---
layout: single
title: "Feeding my Personal Journal into a Sentiment API"
date: 2020-02-17 10:00:00 -0700
categories: coding
---

In early 2019 I began the habit of keeping a personal journal.
Every day I would write about 20-40 sentences of text into a text file (yyyy-MM-dd.txt) outlining the day's events and my immediate reactions to them.
I have found this habit extremely helpful in decluttering my mind, putting the day's events in perspective, remembering things that would otherwise be forgotten, and motivating me to achieve something noteworthy every day.

In all of 2019 I never lapsed and never forgot to write an entry.
As a result, I had a large and well-structured dataset that was just begging to be quantified and analyzed.

One day I got the random idea of feeding my journal into the [Microsoft Azure Text Analytics API](https://azure.microsoft.com/en-us/services/cognitive-services/text-analytics/), specifically its sentiment analysis function.
The sentiment API takes text as input and returns a double between 0 and 1.
Text perceived as negative in tone or content gets a score close to 0, positive text gets a score close to 1, and statements that are completely neutral return a score of exactly 0.5.

```csharp
string key = "YOUR_AZURE_KEY_HERE";
string endpoint = "YOUR_AZURE_ENDPOINT_HERE";

ApiKeyServiceClientCredentials credentials =
    new ApiKeyServiceClientCredentials(key);

var client = new TextAnalyticsClient(credentials)
{
    Endpoint = endpoint
};

string positiveText = "The sentiment API is easy to use " +
    "and can be set up with very little code.";
Console.WriteLine(client.Sentiment(positiveText).Score);  // 0.920177400112152

string negativeText = "The sentiment API has low latency " +
    "but your code should be ready to handle the occasional timeout error.";
Console.WriteLine(client.Sentiment(negativeText).Score);  // 0.152802914381027
```

With some simple client code (above example is in C#), I could input my journal entries and get a numerical positivity or negativity score for every entry.
One complication is that the API's document size limit is 5120 characters, whereas many of my daily journal entries were longer.
To work around this limitation, I inputted my journal entries one paragraph at a time rather than one file at a time, then calculated a score for each day by taking a weighted average of the paragraph scores (longer paragraphs got more weight).

After setting up a free trial Azure subscription, I wrote a standalone app to iterate through my journal entries, feed them into the sentiment API one paragraph at a time, then aggregate the results for each day (source code is on [GitHub](https://github.com/psocha/JournalSentimentAnalyzer)).
After inputting the app's CSV output into Excel and making a time chart, this was the result.

![Journal Sentiment Results](/assets/images/SentimentGraph.png)

Immediate impressions from the above:

- **Negativity rules the day:** My average daily score was 0.4048. Only 72 days had scores at or above 0.500. I attribute this to negativity bias; minor negative things were more likely to be recorded in the journal than minor positive things.
- **Volatility shrank over time:** My journal entries tended to get longer as the year went on, making extreme scores less likely. My highest and lowest scores are concentrated heavily in the first half of the year.
- **Long-term trend is flat:** My average scores consistently hovered around 0.4 for the entire year with no major intra-year trends. Given that I spent the whole year in the same residence and same job and given that 2019 had no giant transitions, triumphs, or tragedies, a flat trend should be expected.
- **Vacations are good for me:** I went out of state four times in 2019 and those time segments are drawn in green. The vast majority of my vacation days scored higher than my non-vacation average.
- **Illness is bad for me:** Days on which I consider myself to have been "sick" are drawn in orange. These days are usually below average, though a few outliers exist.

Here are the most positive days of 2019 accoding to the sentiment API.

| Date | Day's Events | Comments |
|-------|---------|
| Friday May 3 | Attended security training at my day job. Spent the workday watching lectures and eating free catered food. | My journal entry had lots of praise for the lectures and the free food, which no doubt raised its sentiment score. |
| Sunday June 23 | Planned a vacation to Alaska. Booked flights, an Airbnb, and some attractions. | My journal entry had lots of praise for the decent financial deals I got and the feeling of pleasant anticipation I had once everything was booked. |
| Sunday January 13 | Was sick with a cold and didn't leave home all day. Did a binge-read of [In Defense of Food](/book-summaries/in-defense-of-food) and finished it all in one day. | This day doesn't deserve a high score. I'm guessing it got one because I expressed optimism that my health would get better and because I was pleased about finishing a book all in one day. |

Here are the most negative days of 2019 according to the sentiment API.

| Date | Day's Events | Comments |
|-------|---------|
| Thursday May 30 | Fairly ordinary workday. In the evening I watched my hometown Toronto Raptors score an unexpected win over the Golden State Warriors in the first game of the 2019 NBA Finals. | This is not the worst day of 2019 by any means. Its low score is likely because I described in great detail how the Warriors' play was lackluster. |
| Wednesday April 24 | Stressful workday with lots of livesite firefighting. | A much better candidate for worst day of the year than May 30. |
| Tuesday June 25 | Had a long meeting at my day job about how to improve our test coverage. Had a bit of a panic in the evening when I noticed my eyelid was red and swelling. | Lots of negative language in my journal directed at our test coverage and at my eyelid. |

As seen in the tables, a few of my highest and lowest-scoring days probably didn't deserve the extreme scores that they got.
Some traits the extreme days had in common were:
- **Few paragraphs:** A smaller number of paragraphs meant that fewer API calls were made for that particular day. A smaller sample makes an extreme weighted average more likely.
- **Reflective and judgmental language:** Most of my journal text is fairly dry and matter-of-fact. On the occasions when I go out of the way to praise or complain about something, a lopsided paragraph score becomes much more likely.

All in all, working with the sentiment API was an interesting experiment.
The sentiment API is designed mainly for reading business-related texts such as customer reviews; my journal input was definitely not the sort of text the API was optimized for.
Even so, the API did very well at its core job of identifying positive or negative text.
While this experiment gave me some weird results, many of them stemmed from my usage of the API (ie paragraph-weighted daily averaging) and are not the fault of the API itself.
