One of our main goals in developing the Pine language is to provide users with as many useful tools as possible. These tools may have a variety of different uses, and with certain manipulations, some indicators and chart types allow you to extract data from the future bars or trades (relative to the currently processed bar). Since a trader cannot receive this data in real trading, strategies built around it can produce unrealistically profitable results when backtesting, while in real-time trading these trades would be losses. The mistake of using information from the _future_ in the strategies is also called look-ahead bias.

Some TradingView users, out of ignorance or with malicious intent, tend to create ideas and script publications exploiting this feature. TradingView cannot remove the feature itself because it may be useful in some cases, but at the same time, we are committed to warning users of this behavior.

#### Strategies using Japanese-style candles

A very common reason for this behavior is strategy backtesting on Japanese-style charts (Renko, Kagi, etc). The problem arises from the fact that the Strategy Backtesting Engine considers each bar as 4 transactions, with the prices of open, high, low and close (as is the case with a regular candlestick chart). Because of that, on a Renko chart the Strategy Backtesting Engine can enter/exit a position at a price that did not exist in reality. In addition, if you set a Box Size value to be smaller than the mintick, it is possible to check if the next price will be higher or lower than the current one and enter/exit the position in advance, before the Backtesting Engine processes the real price.

//@version=5  
strategy("My Strategy", overlay\=true)  
if close < close\[1\]  
    strategy.entry("ShortEntryId", strategy.short)  
strategy.close("ShortEntryId", when \= close \> close\[1\])  
  
if close \> close\[1\]  
    strategy.entry("LongEntryId", strategy.long)  
strategy.close("LongEntryId", when \= close < close\[1\])  

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43197447218/original/D8i6noYdWq-ORHfWmHqpSfUxbKMJX1Iagw.png?1613458682)

As you can see on the screenshot, this simple strategy can make deals at prices that are very close to the maximum/minimum ones.

#### Strategies using the parameter _calc\_on\_order\_fills = true_

When the parameter calc\_on\_order\_fills = true is specified in the strategy function, the Backtesting Engine performs an additional calculation inside the bar after the order is executed (in contrast to the usual situation when the strategy is calculated only at the close of the bar). At the same time, during the calculation, the strategy gets access to many additional bar parameters, for example, high and low values. This allows you to write a strategy that will show excellent performance while backtesting:

//@version=5  
strategy("CalcOnOrderFillsStrategy", overlay\=true, calc\_on\_order\_fills\=true)  
  
// a variable is used to prevent double entry on the same bar  
var lastTimeEntry \= 0  
  
longCondition \= close \> sma(close, 14)  and lastTimeEntry != time  
if longCondition  
    strategy.entry("LongEntryId", strategy.long)  
  
strategy.exit("exitId", "LongEntryId", limit\=high)  
lastTimeEntry := time  

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43197450508/original/5QhH1E31BKxa0ilELs7-kQng1QB87ZfDaw.png?1613459633)

On the screenshot, you can see that the entry is at the open price of a bar, and the exit happens at the high of the same bar. That is, during the calculation, after the order was executed, we set the strategy.exit limit price equal to the high level of the current bar, which we cannot do in real trading.

#### The _lookahead = barmerge.lookahead\_on_ parameter in security and any security before Pine v3

The security function in Pine allows you to request data from other symbols and/or timeframes. Depending on the implementation, this may allow the strategy to receive data from the future: if one, for example, requests the close or high of a daily bar, while backtesting the strategy could know these values right at the opening of the day. 

Prior to version 3, the security function would return the value from the higher timeframe even before it should have been accessible. In version 3, this behavior was fixed, but for compatibility, the lookahead parameter was added to the security function. It is false by default (i.e., _future vision_ is turned off), but you can enable it by setting the value of the parameter _lookahead_ to _barmerge.lookahead\_on_).

An example of a profitable strategy built using this feature:

//@version=5  
strategy("My Strategy", overlay\=true)  
dayStart \= request.security(syminfo.tickerid, "1D", time, lookahead\=barmerge.lookahead\_on)  
dayHigh \= request.security(syminfo.tickerid, "1D", high, lookahead\=barmerge.lookahead\_on)  
dayLow \= request.security(syminfo.tickerid, "1D", low, lookahead\=barmerge.lookahead\_on)  
  
// entry at first bar of a day  
if time \== dayStart  
    // distance to daily high is further, so we can earn more  
    if math.abs(open \- dayHigh) \> math.abs(open \- dayLow)  
        strategy.entry("LongEntryId", strategy.long)  
        strategy.exit("exitLongId", "LongEntryId", limit\=dayHigh)  
    else  
        strategy.entry("ShortEntryId", strategy.short)  
        strategy.exit("exitShortId", "ShortEntryId", limit\=dayLow)  
          
plot(dayHigh)  
plot(dayLow)  

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43197451291/original/HabBvGFAs5DTnbIK6SS6oNPeLKT0uZb1qw.png?1613459827)

On the first bar, we analyze whether the price will move more up or down relative to the opening price and based on this, we enter a long or short position, and then exit at the maximum or minimum price of the day, respectively. 

Note that not all cases where [_request.security()_](https://www.tradingview.com/pine-script-reference/v5/#fun_request{dot}security) has the _barmerge.lookahead\_on_ argument look into the future: for example, if we were to change the code above by replacing _time/high/low_ inside _[request.security()](https://www.tradingview.com/pine-script-reference/v5/#fun_request{dot}security)_ to _time\[1\]/high\[1\]/low\[1\]_ respectively, we’d receive values for the bars that have already closed. This is often used by experienced coders to get data from _[request.security()](https://www.tradingview.com/pine-script-reference/v5/#fun_request{dot}security)_ without any risk of _lookahead_.

At the moment, these are all known ways for a strategy to look into the future. We hope that this description will allow you to create strategies that do not have these shortcomings, as well as avoid published strategies whose authors exploit these features in their ideas.