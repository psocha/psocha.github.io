---
layout: single
title: "Lessons Learned from Writing a Chess Engine"
date: 2018-09-30 10:00:00 -0700
categories: coding
---

My [chess engine](https://github.com/psocha/ChessEngine) is my favorite on-again-off-again programming side project.

![Chess Engine](/assets/images/chessengine.png){:class="img-responsive"}

In its current iteration, the engine is still relatively straightforward.
Its position evaluation function is a simple mix of material counting and piece-square tables.
Its min-max search tree is limited to a depth of only 6 plies (3 moves per side).
Despite its crudeness, the engine plays surprisingly well.
It is capable of outperforming established chess engines like Stockfish on the lowest difficulty settings.

Here are some lessons I learned as I built and iterated on this project.

**Standardization makes the world go round.**
Writing a chess AI is a surprisingly simple undertaking.
It is not necessary for you to write any user interface code.
There is a standard command-line format called the Universal Chess Interface (UCI) which is widely implemented across chess-playing GUIs.
A UCI-compliant GUI may send your engine application an input like `position startpos moves e2e4 e7e5`.
All your engine needs to do is read the input, build up an internal representation of the board, determine the best move, and output something like `bestmove g1f3`.
Thanks to the UCI standard's high adoption, a chess engine can be little more than a command-line application.

**The profiler is your friend.**
Past a certain point, it is almost impossible to make informed hunches about the performance of a complicated program.
A chess engine is extremely hard to reason about because of its recursive and exponentially-growing tree searches.

You can only get the objective truth by taking rigorous measurements.
In my case, I used the open-source `gprof` profiler to track my engine's performance at runtime on a representative data set.
A profiler can tell you authoritatively how many times each function is called and what fraction of the total runtime it consumes.
The output of `gprof` is verbose, but there are tools out there to convert it to a more readable format, such as [this gprof-to-graph converter](https://github.com/jrfonseca/gprof2dot).
Once you have mathematical performance data, you can make informed decisions about what parts of your code most urgently need optimization.
A profiler's conclusions are often surprising, but they are empirical and you should trust them.

**The C++ Standard Library is slow.**
The standard library offers lots of convenient and easily-resizable data structures.
However, this flexibility inevitably comes with increased overhead, even if you don't take advantage of it.
A chess board, for instance, has constant and static dimensions.
A chessboard data structure needs fast reads and writes, but it doesn't need a fast resizing function.
I originally wrote my chessboard as a `vector<vector<SquareContents>>`, then as a `SquareContents[][]`, then finally as a one-dimensional `SquareContents[]` that used modulo math.
With each change, the engine's all-around performance improved noticeably.
A simple and low-level data structure was the right tool for the job.

**Strings are slow.**
Compared to numbers, strings are a heavy-duty data type.
Frequent string operations and string-centered computations are bad for performance.

One time when I was lazy, I defined my equality operators for my `Move` and `Square` classes as `a.ToString() == b.ToString()`.
It may look like a simple one-liner at this level, but my `ToString()` implementations were non-trivial functions that made multiple expensive string concatenation operations.
Although comparing multiple integer-typed public fields made for a longer comparison function, it was noticeably better for performance.

**Corollary: serialization is extremely slow.**
If string-building is slow, it follows that the full serialization of complex objects is even slower.
I once tried to improve performance by storing my position evaluation calculation results in a cache.
With each position, I would serialize the board position into FEN notation, check the cache for the position, and skip the chess calculations if I got a cache hit.
The engine would never make a redundant calculation.
Sounds promising, right?

The caching experiment ended up being a performance-ruining disaster.
According to `gprof`, the engine was spending over three-quarters of its time inside of `Position::Serialize()`.
Even though the cache hit rate was good, serialization was dominating the total runtime.
The high cost of serialization meant that caching was not a worthwhile optimization.

**AI performance can be drastically improved with little effort.**
For an AI to have acceptable speed, its search space must be kept at a manageable size.
The search tree grows exponentially with increasing depth.
The biggest performance gains will happen when you reduce the number of nodes that need to be processed.

After you write a min-max tree search, the next step is to implement alpha-beta pruning.
As soon as you know that a certain path down the search tree has no chance of being the winning path, don't search it any deeper.

Once alpha-beta pruning is in place, you can use simple heuristics to place promising moves at the front of your processing list.
For example, after generating the list of legal moves, my engine sorts them so that all capture moves appear at the front of the list.
Capture moves are often the best move in a position, often by a wide margin.
If an optimal move is found early, the non-optimal moves will quickly be competing against a high benchmark and alpha-beta pruning will quickly eliminate them.
You may be adding some extra linear-time processing, but it's all worth it if you can remove some exponential-time tree-searching.

**If it's not in the search tree, it doesn't exist.**
The position below is from one of my engine's test games.
The engine is playing white and [my brother](https://m-socha.github.io) is playing black.

Black has an advanced passed pawn that is threatening to advance to `a1`.
Queening the a-pawn would give black an overwhelming material advantage.

![Blunder](/assets/images/chessengine_blunder_position.png){:class="img-responsive"}

The pawn on `a4` is currently a solvable threat.
White can play `Rf5-f1` and cover the queening square, leading to a position that Stockfish evaluates as being roughly even.
In the actual game, instead of playing the sensible move `Rf5-f1`, my engine instantly threw the game away with the greedy move `Rf5-e5`.
After `Rf5-e5`, black can queen the a-pawn and there is nothing white can do to prevent it.
My brother won the game easily at this point.

My engine was searching to a depth of six plies.
In the position above, black can theoretically queen the pawn six plies from now if the a-pawn is the only piece he moves.
My engine was fully aware that black could promote the pawn if white played a move like `Rf5-e5`.
Why did it play that move anyway?

My engine found a "solution" to the promotion problem that wasn't a solution at all.
After `Rf5-e5 a4-a3 Re5-e4 a3-a2`, white has gained a pawn but black's promotion is now a certainty.
White was aware of the promotion, but it knew that it could avoid it by checking the black king with `Re4-e6+`.
A check forces black to move his king instead of promote his pawn.
The eventual pawn promotion move `a2-a1Q` is now outside the six-ply search range.
While black is _able to_ promote the pawn within six plies, he cannot _force_ a promotion within six plies because white can make delays with check moves.
Faced with the threat of promotion, white found a way to kick the can down the road until it was no longer visible in the search tree.
As far as the algorithm was concerned, a threat that can be delayed is not a threat at all.

It is very difficult to force a limited-depth AI to think about the long-term strategic consequences of its actions.
The engine's short-term greed for the `e4` pawn was simply too great.

**Conclusion:**
A chess engine is an interesting case study in performance-oriented programming and basic AI.
There is still much to improve and hopefully I'll revisit the codebase again soon.
