#### <iframe src="https://www.youtube.com/embed/u5yKdhdJHy8??si=sgw4yDl3AwIY7Wp0&amp;wmode=opaque" frameborder="0" allowfullscreen=""></iframe>  

#### Definition

Auto Anchored Volume Profile (AAVP) indicator automatically determines the most important price points and volume levels depending on the current chart timeframe and calculates a volume profile for these points. This can help traders simply identify significant support and resistance levels as well as areas of high liquidity.

> _Note: you can read more about traits shared by all Volume Profile indicators in the_ _[Volume Profile Indicators: basic concepts](https://www.tradingview.com/chart/?solution=43000502040)_ _Help Center article. The text below describes features unique to this particular Volume Profile indicator._

#### Calculation

When calculating Auto Anchored Volume Profile, we check a list of timeframes in a sequence until the number of bars in the time interval for which VP is calculated will be fewer than 5000. The sequence of timeframes is: 1, 5, 15, 30, 60, 240, 1D.

> _Note: On Futures and Spread charts, Volume Profiles is calculated not by requesting a timeframe with fewer than 5000 bars, but by using a timeframe one step lower than the current one based on the timeframe list above. The exception is all second-based timeframes, which always use 1S data._

Consider the following example. The AAVP indicator is set to reset the calculation once per week on a symbol that is traded 24x7 (for the sake of the experiment, let's assume there are no gaps where no trades were happening and each minute of every week has a bar associated with it). 

1.  First, the indicator first checks the "1" timeframe, sees that the 1m chart for this symbol has 7D \* 1440m = 10080 bars of 1m data, which is above the 5000 bar limit. It selects the next timeframe in the sequence.
2.  Next, the indicator does the same with the "3" timeframe. The 3m chart for the symbol has 7D \* (1440 / 3) = 3360 bars of data. This is below the 5000 bar limit, so the 3m bars will be used in the AAVP calculation.

#### Inputs

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43412315922/original/2Owkvner9WRNZJMRmfS4QJcb1cVs5o85Xw.png?1684930943)

##### Anchor Period

Anchor Period specifies the anchor of the Volume Profile calculation, i.e. how often Volume Profile recalculates and where it starts. The available options are:

Auto - The starting point of the Volume Profile calculation depends on the timeframe on the chart:

-   "Session" on all intraday timeframes
-   "Month" on the 1D timeframe
-   "Quarter" on all timeframes between 2D and 10D
-   "Year" on all timeframes between 11D and 60D
-   "Decade" on all timeframes above 61D

Highest High - Volume Profile starts on the bar with the highest high among the last X bars, where X is specified in the Length argument.

Lowest Low - Volume Profile starts on the bar with the lowest low among the last X bars, where X is specified in the Length argument.

Highest Volume - Volume Profile starts on the bar with the highest volume among the last X bars, where X is specified in the Length argument.

Session - Volume Profile starts at the beginning of the last daily session.

Week - Volume Profile starts at the beginning of the last week.

Month - Volume Profile starts at the beginning of the last month.

Year - Volume Profile starts at the beginning of the last year.

Quarter - Volume Profile starts at the beginning of the last quarter (three-month period: Jan-Mar, Apr-Jun, Jul-Sep, Oct-Dec).

Decade - Volume Profile starts at the beginning of the last decade.

Century - Volume Profile starts at the beginning of the last century.

Earnings - Volume Profile starts at the bar with the last earnings report for the current symbol.

Dividends - Volume Profile starts at the bar with the last dividends report for the current symbol.

Splits - Volume Profile starts at the bar with the last split for the current symbol.

##### Length

A rolling window that specifies the number of bars that the indicator analyzes when searching for the anchor. Applies only to Highest High, Lowest Low, and Highest Volume anchor periods. E.g. with the Highest High anchor period and the length of 100, the indicator will search the last 100 bars for the bar with the highest ‘high’ value to start the Volume Profile calculation on.

##### Rows Layout / Row Size

These two inputs specify the way the indicator calculates how many rows each histogram will have.

If the "Rows Layout" input is set to "Number of Rows", the "Row Size" input specifies the total number of rows in the histogram, and the number of ticks per each row is calculated automatically, based on the formula: Ticks Per Row = (Histogram Top - Histogram Bottom) / Number of Rows / Tick size. Depending on the span of the histogram, the Ticks Per Row value can be rounded either up or down, and the total number of rows may exceed what is specified in the limit. 

Let's consider a symbol with a tick size of 0.01, and a Volume Profile histogram that spans a price change from 10 to 11, which brings the total number of ticks it spans to 100. If the "Row Size" is set to 25, the height of a single row is (3 - 2) / 25 / 0.01 = 4 ticks. The resulting histogram has 25 rows, with each row spanning 4 ticks.

If the row height calculation results in a floating point number, the indicator rounds the Ticks Per Row calculation to ensure the height is a whole number. It may also create additional rows to ensure all of the data is represented in the histogram. Whether the Ticks Per Row value is rounded up or down depends on which one results in a total number of rows that is closer to the value in the "Row Size" input.

For example, if in the case above the "Row Size" input is changed to 30, the initial row height is (3 - 2) / 30 / 0.01 = 3.333 ticks per each row.

If this number is then rounded to the nearest integer, 3, each row in the the resulting histogram has 3 ticks per row. As a result, the first 30 rows only account for 30 \* 3 = 90 ticks out of a hundred that the histogram spans. This leaves 10 ticks unaccounted for, and for them, four additional rows are created -- the first three with the size of 3, and the last one with the size of 1, increasing the total number of rows to 34.

If it is rounded up instead, each row in the histogram has a height of 4 ticks. In this case, all 100 ticks fit into 25 rows with no remainder. As 34 rows is closer to 30, the requested "Row Size", the indicator uses 3 ticks as the row height. 

If this input is set to “Ticks Per Row”, Row Size indicates the number of ticks in each single row (1 tick being the minimal move the price for this symbol can make: for example, for NASDAQ:AAPL, 1 tick is 0.01 because the price needs to move at least 0.01 USD, i.e. 1 cent). E.g., setting it to 25 will mean that each row has the height of 25 ticks. In that case, the number of rows will be calculated automatically, and the Volume Profile histogram spanning the price from 200 to 300 for a symbol with a tick size of 0.01 will have (300 - 200) / 0.01 / 25 = 400 rows per each histogram.

##### Volume

Toggles between showing total volume for each row (Total), splitting each row into up/down (Up/Down), or showing their difference (Delta).

##### Value Area Volume

Specifies what percentage of all volume for the trading session should be highlighted by Value Area.