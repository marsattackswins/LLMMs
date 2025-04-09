Displays the largest run-up of wins, i.e., the maximum possible win that the strategy could have incurred among all of the trades it has made. This value is calculated separately for every bar that the strategy spends with an open position. To calculate the Max Run-up, which is displayed on the _Performance Summary_ tab in the _Strategy Tester_, we:

1\. For each separate trade, calculate the Equity before the current trade's opening. For the first trade, this value will be equal to Initial Capital.

2\. For each trade, calculate Min Equity the strategy had before that trade opened. To do so, we take the strategy's Initial Capital and all of the Equity values from the trades that were already closed by that moment and find the smallest number among these values.

3\. Calculate the run-up of the strategy for each bar where the strategy was in a market position. For long trades, it is calculated by the following formula:

_Equity\_on\_Entry - Min\_Equity + Numbers\_of\_Contracts \* (Current\_High - Entry\_Price)_

For short trades, the formula will look like this:

_Equity\_on\_Entry - Min\_Equity + Numbers\_of\_Contracts \* (Entry\_Price - Current\_Low)_

Note that if you calculate the run-up for the closing bar of a trade, you should also account for the intrabar price movement, which goes from Open to High or Low (whichever is closest), then to the other value of that pair, and then to Close. So if the trade was closed on the bar's open, Open will be considered both the maximum and the minimum value of that bar.

4\. After finding the run-up for the current bar, find the maximum value among all of the run-up values we have calculated. This will be the Max Run-up for the current position of the strategy.

Let's look at how Max Run-up is calculated at this example:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43377594841/original/9c6LupHuLzZ1bt5l_TGLm88eb-gi-oCNkQ.png?1670335567)

We use the Supertrend Strategy with Initial Capital equal to 10000 USD, and open NYSE:UBER on the 10D timeframe as the symbol.

We are looking at the first trade, so our Max Equity and Equity on Entry will be equal to the Initial Capital. On first trade opened on Nov 13, 2020, the strategy entered long and bought 32 contracts for 47.11 = 1507.52 USD worth of stock. At the same bar after the opening, the price reached a maximum of 52.15. If we sell our stocks at this point, our run-up would be 10000 - 10000 + 32 \* (52.15 - 47.11) = 161.28. This is the only run-up value we have, so for the time being it is also the Max Run-up. At the next bar on Nov 30, 2020, the price rose to 56.02. Now the run-up will be equal to 10000 - 10000 + 32 \* (56.02 - 47.11) = 285.12. This value also becomes the new Max Run-up, since it is greater than the one found on the previous bar. Then the price will reach new highs twice more during the first trade, so we will get a new Max Run-up value twice.

Jan 4, 2021: 10000 - 10000 + 32 \* (60.03 - 47.11) = 413.44,

Feb 2, 2021: 10000 - 10000 + 32 \* (64.05 - 47.11) = 542.08.

At the first trade the price will not rise above 64.05, so we can move on to the second trade.

At the second trade (Feb 15, 2022) we get the signal to reverse the position. To do so, we first need to sell our 32 stocks to close our long. We sell 32 contracts at 35.44 = 1134.08 USD. Our Equity after closing the first trade is 10000 - 1507.52 + 1134.08 = 9626.56 USD. This value will be our new Min Equity. After getting to 0, we also short 73 - 32 = 41 contracts at 35.44, effectively gaining 1453.04 USD (we short the stock, so we loan it and sell it expecting to buy it back later at a better price).

At the current bar, the price will reach a minimum at 29.71. If we buy contracts at this moment, our run-up will be 9626.56 - 9626.56 + 41 \* (35.44 - 29.71) = 234.93. This is the run-up value at the opening bar of the second trade, but it is less than 542.08, so 542.08 remains the Max Run-up at the moment.

Next, the price will reach new lows a few times, but the price value that will allow us to get a new Max Run-up will come only at the bar on May 12, 2022, when the price will reach a minimum at 21.28. The run-up on this bar will be equal to 9626.56 - 9626.56 + 41 \* (35.44 - 21.28) = 580.56. And since this is the largest run-up value found at the moment, it becomes the new Max Run-up.

At the bar for Jun 10, 2022 the price will drop to 20.16 and the new Max Run-up will be 9626.56 - 9626.56 + 41 \* (35.44 - 20.16) = 626.48.

Finally, at the bar on Jun 27, 2022, having reached the minimum price of 19.9, we will get the Max Run-up value equal to 9626.56 - 9626.56 + 41 \* (35.44 - 19.9) = 637.14.