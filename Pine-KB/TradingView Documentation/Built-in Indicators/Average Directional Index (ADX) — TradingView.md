#### Definition

The Average Directional Index (ADX) is a specific indicator used by technical analysts and traders in order to determine the strength of a trend. The trend can be going either up or down, which is shown by two indicators which often accompany ADX, the Positive Directional Indicator, commonly known as +DI, and the Negative Directional Indicator, also known as -DI. It is for this reason that the average directional index is presented with three separate lines, symbolizing each indicator. Each line is used to help assess a trade and whether or not it should taken long or short, if at all. The ADX indicator on TradingView does not display the +DI and -DI lines by itself, but you can use the Directional Movement Index (DMI) indicator to see all three at the same time.

#### History 

The Average Directional Index was initially designed by Welles Wilder for commodity daily charts, but was then modified so that it could be used in other markets and for various timeframes. These modifications allowed for ADX to become what it is today - an indicator to track the strength of market trends and analyzing said trends with the aid of additional, directional indicators.

#### Calculations

Due to the fact that the Average Directional Index includes multiple lines, the indicator requires a sequence of calculations, which are laid out below. 

1.  Start off by calculating the +DM, -DM, and True Range (TR) for each period you are analyzing. Note:
    1.  +DM = Current High - Previous High
    2.  \-DM = Previous Low - Current Low
2.  You can use +DM when the Current High - Previous High > Previous Low - Current Low.
3.  Use -DM when the Previous Low - Current Low > Current High - Previous High.
4.  The TR is the greater of the Current High - Current Low, the Current High - Previous Close, or the Current Low - Previous Close.
5.  Go ahead and smooth your period averages of +DM, -DM, and TR. Then, insert the -DM and +DM values to calculate the smoothed averages of those.
6.  First xTR = Sum of first x TR readings (x = number of…)
7.  Next xTR value = First xTR - (Prior xTR/14) + Current TR
8.  Then divide the smoothed +DM value by the smoothed TR value to get your +DI value. Multiply this value by 100.
9.  Divide the smoothed -DM value by the smoothed TR value to get your -DI value. Multiply this value by 100.
10.  The formula for the Directional Movement Index (DX) is +DI minus -DI, then divided by the sum of +DI and -DI (all of these are absolute values). Multiply this value by 100.
11.  In order to get the ADX, you’ll need to continue calculating the DX values for x periods. Smooth the results of the periods in order to get your ADX value.
12.  First ADX = the sum of x periods of DX / x
13.  Finally, ADX = ((Prior ADX \* 13) + Current DX) / x

#### Takeaways and what to look for

The Average Directional Index (ADX), as well as the Negative (-DI) / Positive (+DI) Directional Indicators, are momentum indicators and help investors determine the strength of a trend and trend direction.. 

The Average Directional Index projects market price and it is clearly seen when prices move up (when +DI is above -DI), and when the prices move down (when -DI is above +DI). When there are crosses between both +DI and -DI lines, it can signify potential trading signals, as a bearish or bullish market emerges.

A trend shows the most strength when the Average Directional Index is above 25 (potential signal to buy), and a trend is weak or the price is considered trendless if the ADX reaches below 20 - according to the concept creator, Wilder. Keep in mind, if ADX is below 20, it might not be the most ideal time to enter a trade.

If the market presents itself as not following a specific trend, this does not mean that the price isn’t moving, rather that it could be making a change or the direction is not currently present. 

#### Limitations

Crossovers between indicator lines can occur quite often. In the case that this occurs too frequently, there will most likely be confusion among traders and the potential for money loss can be high. These moments in question are known as “false signals” and are most common when ADX is calculated below 25. 

The Average Directional Index should be combined with other indicators that examine price and others that can help filter signals and control risk to get the most out of the tool. Like most indicators, it works best when paired with highly functioning data processors and other analytical tools.

#### Summary

To sum up, the Average Directional Index is a great tool for technical analysis and determining the strength of a trend, whether it be going up or down. Pair it with other indicators to analyze trends and find when it is a good time to place a trade, given market status.