#### Definition

There are several moving average types, many of which you surely have come across, such as the Simple Moving Average (SMA) and the Exponential Moving Average (EMA). The latter of the two, along with the Weighted Moving Average (WMA), were introduced to analyze price lag by putting more of an emphasis on more recent data. The Hull Moving Average (HMA) is a quick and smooth moving average that is distinct in its own nature. The HMA attempts to remove lag in its entirety, while simultaneously improving upon smoothing.

#### History

The Hull Moving Average was developed and first introduced by Alan Hull as a new moving average that focuses on smoothness, efficiency, and lag elimination. 

#### Calculations

To calculate the Hull Moving Average, follow the steps below.

1.  Begin by calculating a Weighted Moving Average with period n / 2 and then multiply this value by 2.
2.  Next, go ahead and calculate another Weighted Moving Average for period n and then subtract this value from the result in Step 1.
3.  Finally, calculate a Weighted Moving Average with period sqrt(n)by using the data you’ve collected from the results of Step 2.

Another version of this calculation can be found below.

HMA = WMA(2\*WMA(n/2) − WMA(n)),sqrt(n))

#### Takeaways and what to look for

A Hull Moving Average (HMA) used to analyze a longer period may be best suited to identify a market trend. To further analyze, it can be determined that if the HMA value is rising and the trend is rising as well, then it would be ideal to enter long positions for your trade. In contrast, if the HMA is falling and the trend is also falling, it would then be ideal to consider entering short positions.

#### Summary

The Hull Moving Average (HMA) is quick and smooth, setting it apart from its moving average counterparts. The HMA seeks to eliminate lag, while providing smooth results at the same time. The HMA follows the movement of the market trend and is calculated quite differently from its counterparts and widely used moving averages like the SMA and EMA.