Historical data does not include records of intra-bar movements of price; only open, high, low and close (OHLC). This leads to a script sometimes working differently on historical data and in real-time, where only the open price is known and where price will typically move many times before the real-time bar’s final high, low and close values are set after the real-time bar closes.

If we add a script on a chart, wait until it calculates on a number of real-time bars and then reload the page. We will sometimes see a script’s plots change slightly. This behavior is one of a few different types of behaviors commonly referred to as _indicator repainting_. It is the type of repainting we are concerned with here and which we will refer to when using repainting. It is due to the fact that when certain features are used in scripts, they will calculate differently on historical and real-time bars.

Other types of behavior, correctly or incorrectly referred to as repainting, include plotting with a negative offset on past bars and using otherwise unavailable future information received through misunderstood calls to the [request.security](https://www.tradingview.com/pine-script-reference/v5/#fun_request{dot}security) function. This can introduce data unavailable in real-time, into script calculations.

Not all indicators are subject to the type of repainting we discuss here. In most cases, it depends on whether or not certain functions or language constructs are used in the code. Please note that this repainting effect is **not a bug**, rather the result of the inherent differences between historic bars and real-time bar information on TradingView.

We can see repainting in the following cases:

1\. Strategies using _calc\_on\_every\_tick = true_. A strategy with parameter _calc\_on\_every\_tick = false_ may also be prone to repainting, but to a lesser degree.

2\. Using _[request.security](https://www.tradingview.com/pine-script-reference/v5/#fun_request{dot}security)_ to request data from a resolution higher than the resolution of the chart’s main symbol:

// Add this indicator on 1 minute chart  
//@version=5  
indicator("My Script")  
c \= request.security(syminfo.tickerid, "5", close)  
plot(close)  
plot(c, color\=color.red)  

This study will calculate differently on real-time and historical data, regardless of lookahead parameter’s value (see [Understanding lookahead](https://www.tradingview.com/pine-script-docs/en/v4/essential/Context_switching_the_security_function.html#understanding-lookahead)).

3\. Using __[request.security](https://www.tradingview.com/pine-script-reference/v5/#fun_request{dot}security)__ to request data from a timeframe lower than the timeframe of the main chart (more information [here](https://www.tradingview.com/pine-script-docs/en/v4/essential/Context_switching_the_security_function.html#requesting-data-of-a-lower-timeframe)):

// Add this indicator to a 5 minute chart  
//@version=5  
indicator("My Script")  
c \= request.security(syminfo.tickerid, "1", close, lookahead\=barmerge.lookahead\_off)  
plot(close)  
plot(c, color\=color.red)  

If _lookahead=barmerge.lookahead\_off_, repainting will occur. When _lookahead=_barmerge.lookahead\_on__, repainting is less probable. It may still happen when 1 and 5 minute updates outrun each other.

4\. All scripts calculations depend on their _starting point_. Intraday data gets aligned to the beginning of the week, month or year, depending on the resolution. Due to this, the results produced by such scripts can differ from time to time. These are cases where scripts will be relying on a starting point:

-   when they use [valuewhen](https://www.tradingview.com/pine-script-reference/v5/#fun_ta{dot}valuewhen), [barssince](https://www.tradingview.com/pine-script-reference/v5/#fun_ta{dot}barssince) or [ema](https://www.tradingview.com/pine-script-reference/v5/#fun_ta{dot}ema) functions (due to peculiarities in their algorithm)
-   any backtesting strategy (regardless of how the _calc\_on\_every\_tick_ parameter is defined)

There is a dependency between the resolution and the alignment of a starting point:

-   1–14 minutes — aligns to the beginning of a week
-   15–29 minutes — aligns to the beginning of a month
-   from 30 minutes and higher — aligns to the beginning of a year

The following limitations of history lengths are taken into account when processing the data:

-   40000 historical bars for Ultimate plans
-   25000 historical bars for Expert plans
-   20000 historical bars for Premium plans
-   10000 historical bars for Essential and Plus plans
-   5000 historical bars for other plans

5\. Changes in historical data, for example, due to a split.

6\. Presence of the following variables in the script usually leads to repainting:

-   [barstate.isconfirmed](https://www.tradingview.com/pine-script-reference/v5/#var_barstate%7Bdot%7Disconfirmed), [barstate.isfirst](https://www.tradingview.com/pine-script-reference/v5/#var_barstate%7Bdot%7Disfirst), [barstate.ishistory](https://www.tradingview.com/pine-script-reference/v5/#var_barstate%7Bdot%7Dishistory), [barstate.islast](https://www.tradingview.com/pine-script-reference/v5/#var_barstate%7Bdot%7Dislast), [barstate.isnew](https://www.tradingview.com/pine-script-reference/v5/#var_barstate%7Bdot%7Disnew), [barstate.isrealtime](https://www.tradingview.com/pine-script-reference/v5/#var_barstate%7Bdot%7Disrealtime), [barstate.islastconfirmedhistory](https://www.tradingview.com/pine-script-reference/v5/#var_barstate{dot}islastconfirmedhistory)
-   [timenow](https://www.tradingview.com/pine-script-reference/v5/#var_timenow)
-   [bar\_index](https://www.tradingview.com/pine-script-reference/v5/#var_bar_index)