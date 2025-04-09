#### <iframe src="https://www.youtube.com/embed/kQw-BDuF5bw??si=uWutzMHYjpTn43uw&amp;wmode=opaque" frameborder="0" allowfullscreen=""></iframe>  

#### Definition

Periodic Volume Profile (PVP) indicator calculates a sequence of volume profiles that provide an indication of the distribution of volume across various price levels within specific periods. The periods are dictated by the indicator's inputs.

> _Note: you can read more about traits shared by all Volume Profile indicators in the_ _[Volume Profile Indicators: basic concepts](https://www.tradingview.com/chart/?solution=43000502040)_ _Help Center article. The text below describes features unique to this particular Volume Profile indicator._

#### Calculation

To calculate Periodic Volume Profile, the indicator uses a table that selects a lower timeframe based on the timeframe currently selected on the chart: 

<table><tbody><tr><td><p>Chart resolution</p></td><td><p>Lower timeframe used for the VP calculation</p></td><td><p>Depth ratio</p></td></tr><tr><td><p>1S, 5S, 10S</p></td><td><p>1S</p></td><td><p>1</p></td></tr><tr><td><p>15S</p></td><td><p>5S</p></td><td><p>3</p></td></tr><tr><td><p>30S</p></td><td><p>15S</p></td><td><p>2</p></td></tr><tr><td><p>1 - 4</p></td><td><p>1</p></td><td><p>1</p></td></tr><tr><td><p>5 - 15</p></td><td><p>1</p></td><td><p>3</p></td></tr><tr><td><p>16 - 30</p></td><td><p>5</p></td><td><p>3</p></td></tr><tr><td><p>31 - 60</p></td><td><p>10</p></td><td><p>3</p></td></tr><tr><td><p>61 - 120</p></td><td><p>15</p></td><td><p>4</p></td></tr><tr><td><p>121 - 240</p></td><td><p>30</p></td><td><p>4</p></td></tr><tr><td><p>241 and more</p></td><td><p>60</p></td><td><p>4</p></td></tr></tbody></table>

The following logic is used to calculate how far in the past the volume profiles will be drawn:

1\. From the table above, select the lower timeframe based on the timeframe on the chart. Data from this lower timeframe will be used to calculate Volume Profile.

2\. Use the number of historical bars available for calculation based on your subscription level and multiply it by the appropriate depth ratio.

3\. The resulting number shows you how many lower timeframe bars will be available for the indicator. 

For example, a Premium user has a limit of historical 20000 bars shown on the chart at the same time. If the chart is open on a "60" timeframe, the indicator will load 20000 \* 3 (depth ratio) = 60000 10-minute bars. As there are six 10-minute bars in one 60-m bar, the indicator will be able to build volume profiles for the last 10000 bars on the 60m chart. As you go deeper into the past of the symbol, you might eventually hit a point where there are no more lower timeframe bars, and the indicator will stop calculating.

Note that:

-   The total limit of histogram rows is always under 6,000. So if each profile has 100 rows, the indicator will not draw more than 60 of these, even if there is still data available on lower timeframes.
-   Profiles are aligned by the beginning of the year. Each Volume Profile will stop calculating at the end of the year, and will start over again from the new year, even if the Period setting is set to work otherwise. This is necessary to maintain consistency when building profiles on different timeframes. 

#### Inputs

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43411995135/original/74Dn_p0_V6KMl64FtX-qTOIjG5PCbINNZA.png?1684837373)

##### Period

Sets the period for which the indicator builds the volume profile, one profile for each new period. The period multiplier is set in the first field, and the period itself, which can take the values "Bar", "Minute", "Hour", "Day", "Week" or "Month", is set in the second field.

##### Volume

Toggles between showing total volume for each row (Total), splitting each row into up/down (Up/Down), or showing their difference (Delta).

##### Value Area Volume

Specifies what percentage of all volume for the trading session should be highlighted by Value Area.

##### Rows Layout / Row Size

These two inputs specify the way the indicator calculates how many rows each histogram will have.

If the "Rows Layout" input is set to "Number of Rows", the "Row Size" input specifies the total number of rows in the histogram, and the number of ticks per each row is calculated automatically, based on the formula: Ticks Per Row = (Histogram Top - Histogram Bottom) / Number of Rows / Tick size. Depending on the span of the histogram, the Ticks Per Row value can be rounded either up or down, and the total number of rows may exceed what is specified in the limit. 

Let's consider a symbol with a tick size of 0.01, and a Volume Profile histogram that spans a price change from 10 to 11, which brings the total number of ticks it spans to 100. If the "Row Size" is set to 25, the height of a single row is (3 - 2) / 25 / 0.01 = 4 ticks. The resulting histogram has 25 rows, with each row spanning 4 ticks.

If the row height calculation results in a floating point number, the indicator rounds the Ticks Per Row calculation to ensure the height is a whole number. It may also create additional rows to ensure all of the data is represented in the histogram. Whether the Ticks Per Row value is rounded up or down depends on which one results in a total number of rows that is closer to the value in the "Row Size" input.

For example, if in the case above the "Row Size" input is changed to 30, the initial row height is (3 - 2) / 30 / 0.01 = 3.333 ticks per each row.

If this number is then rounded to the nearest integer, 3, each row in the the resulting histogram has 3 ticks per row. As a result, the first 30 rows only account for 30 \* 3 = 90 ticks out of a hundred that the histogram spans. This leaves 10 ticks unaccounted for, and for them, four additional rows are created -- the first three with the size of 3, and the last one with the size of 1, increasing the total number of rows to 34.

If it is rounded up instead, each row in the histogram has a height of 4 ticks. In this case, all 100 ticks fit into 25 rows with no remainder. As 34 rows is closer to 30, the requested "Row Size", the indicator uses 3 ticks as the row height. 

If this input is set to “Ticks Per Row”, Row Size indicates the number of ticks in each single row (1 tick being the minimal move the price for this symbol can make: for example, for NASDAQ:AAPL, 1 tick is 0.01 because the price needs to move at least 0.01 USD, i.e. 1 cent). E.g., setting it to 25 will mean that each row has the height of 25 ticks. In that case, the number of rows will be calculated automatically, and the Volume Profile histogram spanning the price from 200 to 300 for a symbol with a tick size of 0.01 will have (300 - 200) / 0.01 / 25 = 400 rows per each histogram.

##### Extend POC Right

Extends the Point of Control line until it crosses any bar.

##### Extend VAH Right

Extends the Value Area High line until it crosses any bar.

##### Extend VAL Right

Extends the Value Area Low line until it crosses any bar.