On TradingView, strategies can be applied to any type of chart, including non-standard ones like Heikin Ashi (HA), Renko, Kagi, Point and Figure and Range. Because of the inherently synthetic nature of price levels on non-standard charts, backtesting results calculated on them will typically not produce results representing real market conditions.

Strategy orders are filled using the chart's OHLC values, as is documented in the [Pine User Manual](https://www.tradingview.com/pine-script-docs/v4/essential/strategies/#strategies). A strategy running on a Renko chart, for example, will use the price levels from the Renko bricks rather than from real market prices. Our Help Center pages explain their [features](https://www.tradingview.com/?solution=43000502284) and [calculations](https://www.tradingview.com/?solution=43000480330). Renko brick levels, being disconnected from actual market prices at any given moment, will fill orders using their own prices and therefore, will not produce reliable strategy results. This is because the formation of boxes in real-time is different from recorded historical data.

Consider this simple strategy:

//@version=5   
strategy("My Strategy", overlay\=true)   
longCondition \= open<close   
if (longCondition)   
    strategy.entry("My Long Entry Id", strategy.long)   
shortCondition \= open\>close   
if (shortCondition)   
    strategy.entry("My Short Entry Id", strategy.short)  

On a standard chart using normal candles, it produces results that are quite ordinary. It will also produce the exact same results on any other standard chart type: Bars, Hollow candles, Line, Area or Baseline.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43081279484/original/ero7GnPQTPUFNAsJcV79Erad8qeQYnO9lQ.png?1572427956)

If, however, you run that same strategy on any non-standard chart type, you will obtain different results that cannot be reproduced in real markets. On a Renko chart, for example, we obtain this:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43081279557/original/fsli77teO1Qo_mYd9ml839GRpA_H9QezJw.png?1572427973)

These results are calculated using the Renko chart's synthetic prices, which most likely do not reflect the actual order fills you would get if you were trading for real.

##### Why do we allow strategies to run on non-standard charts?

The different methods used to interpret price action in building non-standard charts can provide traders with an original perspective when analyzing markets. Traders who understand their advantages and limitations may find them useful. We provide tools and believe it's up to traders to select the ones they want to use to trade. However, we still consider it our duty to warn our community: exercise caution when using strategies on non-standard chart types. Use them privately if you wish, but in order to protect the community we will moderate script publications using strategies on non-standard charts.