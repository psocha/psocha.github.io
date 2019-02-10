---
layout: single
title: Stochastic Sudoku Solver
permalink: /widgets/sudokusolver
author_profile: true
---

<main>
    <div id="main">
        <script src="https://cdn.jsdelivr.net/gh/psocha/StochasticSudokuSolver/solver.js" type="text/javascript"></script>
        <link rel="stylesheet" type="text/css" href="https://cdn.jsdelivr.net/gh/psocha/StochasticSudokuSolver/solver.css" />
        <div id="stochastic-sudoku-solver" style="margin-bottom:40px;"></div>
        <p>
            This solver uses a simulated annealing algorithm to solve Sudoku grids.
            The grid is first filled in randomly, creating an invalid solution with many errors.
            Each turn, the algorithm randomly picks two open cells in the same 3x3 box and considers swapping them.
            If the grid after the swap would have fewer errors than the old grid, the swap is accepted and performed.
            If the proposed swap makes the grid worse, it is stochastically accepted or rejected.
            The probability of accepting a negative swap depends on the error differential and the distance from the goal of a zero-error solution.
            Simulated annealing sometimes accepts worsening swaps in order to prevent stagnation in the algorithm.
        </p>
        <p>
            Simulated annealing is probabilistic and each run will be different.
            It will not always solve every solvable grid, though it is guaranteed to find a solution if given infinite time (this widget times out after 30,000 swaps).
            Simulated annealing can often find solutions more quickly than deterministic brute-force or backtracking algorithms.
        </p>
    </div>
</main>
