#### <iframe src="https://www.youtube.com/embed/I1XhA8QC-8M?&amp;wmode=opaque" frameborder="0" allowfullscreen="" data-identifyelement="461"></iframe>

#### Definition

Technical Ratings is a technical analysis tool that combines the ratings of several [technical indicators](https://www.tradingview.com/scripts/indicator/) to make it easier for traders and investors to find profitable trades.

#### Calculations

These are the criteria used to determine the rating of the individual indicators used. Note that changes from the last bar are used to determine falling or rising states:

##### All Moving Averages

-   Buy — MA value < price
-   Sell — MA value > price
-   Neutral — MA value = price

##### Ichimoku Cloud

-   Buy — lead line 1 > lead line 2 and base line > lead line 1 and conversion line > base line and price > conversion line
-   Sell — lead line 1 < lead line 2 and base line < lead line 1 and conversion line < base line and price < conversion line
-   Neutral — neither Buy nor Sell

##### Relative Strength Index

-   Buy — indicator < 30 and rising
-   Sell — indicator > 70 and falling
-   Neutral — neither Buy nor Sell

##### Stochastic

-   Buy — main and signal lines < 20 and main line > signal line
-   Sell — main and signal lines > 80 and main line < signal line
-   Neutral — neither Buy nor Sell

##### Commodity Channel Index

-   Buy — indicator < -100 and rising
-   Sell — indicator > 100 and falling
-   Neutral — neither Buy nor Sell

##### Average Directional Index

-   Buy — +DI line > -DI line and indicator > 20 and rising
-   Sell — +DI line < -DI line and indicator > 20 and rising
-   Neutral — neither Buy nor Sell

##### Awesome Oscillator

-   Buy — saucer and values are greater than 0, or cross over the zero line
-   Sell — saucer and values are lower than 0, or cross under the zero line
-   Neutral — neither Buy nor Sell

##### Momentum

-   Buy — indicator values are rising
-   Sell — indicator values are falling
-   Neutral — neither Buy nor Sell

##### MACD

-   Buy — main line values > signal line values
-   Sell — main line values < signal line values
-   Neutral — neither Buy nor Sell

##### Stochastic RSI

-   Buy — downtrend and K and D lines < 20 and K line > D line
-   Sell — uptrend and K and D lines > 80 and K line < D line
-   Neutral — neither Buy nor Sell

##### Williams Percent Range

-   Buy — indicator < lower band and rising
-   Sell — indicator > upper band and falling
-   Neutral — neither Buy nor Sell

##### Bulls and Bears Power

-   Buy — uptrend and BearPower < zero and BearPower is rising
-   Sell — downtrend and BullPower > zero and BullPower is falling
-   Neutral — neither Buy nor Sell

##### Ultimate Oscillator

-   Buy — UO > 70
-   Sell — UO < 30
-   Neutral — neither Buy nor Sell

The numerical value of the _Sell_ rating is -1, _Neutral_ is 0 and _Buy_ is 1. The group and overall ratings are calculated as the average of the ratings of the individual indicators.

Recommendations for the group or overall ratings are based on this numerical rating value and determined according to the following criteria:

-   \[-1.0 ≥ value < -0.5\] — Strong Sell
-   \[-0.5 ≥ value < -0.1\] — Sell
-   \[-0.1 ≥ value ≤ 0.1\] — Neutral
-   \[0.1 > value ≤ 0.5\] — Buy
-   \[0.5 > value ≤ 1.0\] — Strong Buy

#### The basics

The recommendations given by the indicator are based on the ratings calculated for the various indicators included in it.

The overall rating of the indicator includes two large groups of indicators. The first consists of SMAs and EMAs with different lengths (MA lengths are 10, 20, 30, 50, 100 and 200), the Ichimoku Cloud (9, 26, 52), VWMA (20) and HullMA (9). The second one is calculated on the following oscillators: RSI (14), Stochastic (14, 3, 3), CCI (20), ADX (14, 14), AO, Momentum (10), MACD (12, 26, 9), Stochastic RSI (3, 3, 14, 14), Williams %R (14), Bulls and Bears Power and UO (7,14,28). Each group's rating is calculated separately, so you can select the group in the indicator settings and its respective rating calculation will be displayed on the chart.

#### What to look for

The Technical Ratings tool is designed to have values that fluctuate above and below a zero line. Its values are plotted as a histogram of red, blue and gray bars, and depend on your selection in the _Rating is based on_ field of the script's inputs, where you can choose to view the value of the MAs rating, the oscillators rating, or the average of both.

Columns are gray when the value of the indicator is between 0.1 and -0.1. Progressively more saturated blue columns indicate rising values above 0.1, and more saturated red columns indicate progressively falling values below -0.1.

The label at the end of the histogram displays the state of the MAs, oscillators, and the overall rating. Its color is determined by the value of the rating selected in the _Rating is based on_ field: gray for neutral, blue for _Buy_ or _Strong Buy_, red for _Sell_ or _Strong Sell_.

#### Summary

Technical Ratings can be a valuable technical analysis tool for many analysts or traders. Many traders use a selection of complementary indicators to make better decisions. Technical Ratings simplifies this task by combining the most popular indicators and their signals.

**Note:** TradingView does not recommend that anyone buy or sell any financial instrument based solely on the recommendations of the Technical Ratings indicator. Recommendations merely indicate the fulfillment of certain conditions of a set of individual indicators that may help the user to spot potentially favorable conditions for a transaction, if this is consistent with his/her strategy.