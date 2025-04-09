<iframe src="https://www.youtube.com/embed/UwxZ_JCrt0o?&amp;wmode=opaque" frameborder="0" allowfullscreen="" data-identifyelement="455"></iframe>

The Time Price Opportunity (TPO) indicator, also known as "Market Profile", analyzes market activity by price level as it develops over time. It provides traders with a unique perspective on market dynamics and the distribution of prices by visualizing the blocks of time spent at each of the profile's price levels and the sequence of level traversals within the profile's period. Traders often use TPO to identify significant price levels and market patterns that may not be obvious from inspecting raw price data.

J. Peter Steidlmayer formulated the concept of Time Price Opportunity at the Chicago Board of Trade (CBOT) in the 1980s. TPO Profiles gained prominence in futures and commodities markets and are now widely used across all sectors.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43441004049/original/h6B1ll16-wVTrzMAWIHQJp8ZT_NPQVB45g.png?1696599653)

As a popular and helpful indicator, TPO also made a useful chart type — with the [TPO chart](https://www.tradingview.com/support/solutions/43000725590-time-price-opportunity-tpo-chart/), traders can determine price targets that help predict future price movements in the market. Make use of the chart or dive deeper into the indicator calculations below.

#### Calculation

#### TPO

The indicator displays the TPO Profile on the left of each period and an optional Volume Profile to the right.

The following process constructs the TPO Profile:

-   The user specifies the number of days, weeks, or months the profile's period will cover.
-   The indicator divides the period into equal blocks of time based on the user-specified "Block Size" (5min, 10min, 15min, 30min, 1H, 2H, or 4H). Each successive time block corresponds to a letter. The sequence starts with uppercase letters \[A-Z\], then uses lowercase letters \[a-z\] if more are required. The indicator repeats this sequence if the period contains enough time blocks to exhaust all the available letters.
-   The indicator creates price levels (rows) for each period based on its specified row size. It can calculate the row size automatically, or the user can manually define the number of ticks per row. The profile displays a block at a price level for every time segment in which prices traversed it. For example, a leading "A" block on a row means the market price reached that level during the first time block.

#### TPO Value Area (VA)

The Value Area is the price range that contains a significant concentration of TPO blocks over a period. It suggests the price range where market participants showed the most interest. Traders often use it to identify potential support and resistance levels.

The indicator uses the following algorithm to determine the Value Area of a TPO profile:

1.  Determine the total number of blocks in the profile.
2.  Calculate the target number of blocks in the VA using this formula:  
    `VA Target = Total Blocks * Value Area Percent / 100`
3.  Start the VA block counter at the row with the highest number of blocks (Point of Control - POC). The POC is the first row added to the VA.
4.  Count the blocks in the row above the highest VA row.
5.  Count the blocks in the row below the lowest VA row.
6.  Determine the row with the highest block count from steps 4 and 5 and add its count to the VA block count. That row becomes part of the VA. If both rows have an identical block count, add the row closest to the POC. If they are also equidistant from the POC, add the highest row.
7.  Repeat steps 4-6 until the total number of VA blocks reaches the target calculated in step 2.
8.  Use the highest and lowest levels in the VA as the Value Area High (VAH) and Value Area Low (VAL).

#### Row size

When the "Row Size" input uses the "Auto" option, the indicator calculates the row size based on the latest 300 bars as of the rightmost visible bar. It first divides the difference between the highest high and lowest low across those bars by the symbol's minimum tick value:

`MinTickRange = (HighValue - LowValue) / MinimumTick`

Then, it divides this value by 80, i.e., the number of rows that must fit on the chart:

`RowTicks = MinTickRange / RowsRequired`

Lastly, it rounds the result to calculate the final ticks per row value:

`TicksPerRow = round(RowTicks / Increment) * Increment`

The increment it rounds to depends on the scale of the calculated value:

`If 1 <= RowTicks <= 100, Increment = 5 If 100 <= RowTicks <= 1000, Increment = 50 If 1000 <= RowTicks <= 10000, Increment = 500 If 10000 <= RowTicks <= 100000, Increment = 5000 etc...`

The indicator recalculates the row size when adding it to a chart, resetting its settings, or changing the symbol or timeframe.

#### Volume Profile

The optional [Volume Profile](https://www.tradingview.com/chart/?solution=43000502040) uses the data from the "Block Size" timeframe for its calculations. Comparing the Volume Profile to the TPO Profile can help corroborate the significance of price levels. 

#### Interpretation

#### Balance and imbalance

One can postulate that a market is always in a state of either balance or imbalance. A state of balance in this context means an instrument has an approximately equal number of buyers and sellers. In such a case, the supply and demand for the instrument roughly align, and prices concentrate around a fair price value.

If the number of buyers exceeds the number of sellers or vice versa, one can consider the market imbalanced. When in a state of imbalance, the market price starts a directional movement in search of a new fair value. Prices may rise when the buyers outweigh the sellers, and prices may fall when the sellers outweigh the buyers. In either scenario, the directional movement may persist until the number of buyers and sellers equalizes, resulting in a balanced state at a new fair price.

#### Initial Balance Range (IBR)

The Initial Balance Range is the range of prices visited during the first time blocks in the profile's period. Markets may experience elevated trading activity during the beginning parts of a session. As such, traders often use IBR to identify initial significant levels, which can serve as a reference point when evaluating further price movements. The TPO indicator displays the IBR as a vertical line at the left of the period's starting point. Users can enable the IBR line and the number of time blocks in its calculation from the "Style" tab of the script's "Settings".

#### TPO Midpoint

The TPO midpoint refers to the median price value between the lowest and highest prices within a Time Price Opportunity profile, calculated using the following formula:

`TPO Midpoint = (Highest TPO Price + Lowest TPO Price) / 2`

#### Support and Resistance Levels

Support and resistance levels are key price regions where the market historically experienced concentrated buying (support) or selling (resistance) activity. Traders often use such levels as reference points for identifying potential price reversal or continuation areas. In TPO analysis, such levels can include the Point of Control (POC), Value Area High (VAH), and Value Area Low (VAL), among other significant price levels.

The Point of Control (POC) is the level at which the market price spent the most time in the profile's period. It indicates the value where trading activity had the highest concentration, offering insights into market equilibrium and consensus. Traders often consider the POC a potential reference for future price movements, as the market price might gravitate toward areas with a higher concentration of historical activity. Repeated price interaction with a POC level across subsequent profiles enhances its speculative significance as a support or resistance level.

The Value Area High (VAH) and Value Area Low (VAL) signify the upper and lower boundaries of the price region where most of the market activity occurred throughout the profile's period. VAH and VAL can serve as potential support and resistance levels over subsequent periods.

#### Distributions

Another interpretation path for TPO is to consider two categories of investors according to their goals and decision-making timeframes: short-term and long-term traders.

Short-term traders predominantly place intraday trades. In other words, their typical decision-making timeframe is within the current trading day. Therefore, they tend to gravitate toward the day's fair prices and make most of their trades within the Value Area. These traders play a significant role in forming the Value Area itself, the conditions necessary to facilitate trade execution, and the fair market price for the trading session.

Long-term traders do not limit the window in which they make trade decisions to a single session or trading day. Consequently, they may seek more advantageous prices for their trades, such as those outside the Value Area, i.e., below the VAL for buyers and above the VAH for sellers. Such traders may contribute to price movement outside the Value Area. When long-term traders dominate the market volume, an asset's price may make more significant upward or downward movements, depending on the concentration of buyers and sellers.

This interpretation can help explain some common range development patterns, or distributions, in TPO Profiles. Here are a few of them:

#### Normal day distribution

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43441004396/original/W9-8XH8YwHpdChWCYXTiKqK9zCfyFndXIg.png?1696599721)

A Normal Day distribution occurs when most of the period's price range (about 85%) lies within the Initial Balance Range, implying that activity outside the IBR is insignificant or nonexistent. One might perceive the market as balanced in such a case since most of the period's trading activity occurred within the Value Area (i.e., the fair price area). This pattern suggests that the main market drivers during the period are short-term traders, and the influence of long-term traders is minimal.

#### Normal variation day distribution

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43441004418/original/4KZv_-Tnm2lAygxjT_1g-Zvsh_z3OiVgyA.png?1696599730)

A Normal Variation Day occurs when longer-term traders are more active. The price range extends beyond the Initial Balance Range, which short-term traders are less likely to hold. The range extension beyond the IBR can be anywhere from a few ticks to double the IBR's size.

#### Trend day distribution

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43441004459/original/05id6d9vU5AB5aFJq6N5cT0R-ANz-nKe6A.png?1696599739)

A Trend Day occurs when the longer-term traders push the price range successively further, forming a range extension that is more than double the size of the IBR, and the market closes with a price near the extension's extremity. This distribution suggests long-term traders maintain a heavier influence over the direction as the market searches for a new fair price.

#### Neutral day distribution

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43441004502/original/_CoqnTBonjy4V33DkddpawrP8pcEGTvoNA.png?1696599746)

A Neutral Day occurs when traders temporarily extend the price range beyond the IBR. The market price then reverses, and a similar pattern may appear at the opposite end of the IBR. This distribution suggests uncertainty in the market. It generally occurs when the market tests for continuation or changes in underlying trends.

#### Single prints

Single prints are non-extreme levels that contain only one TPO block, meaning the market price traversed them only once in the profile's period. Traders consider these levels as indicators of potential market interest or imbalance. As such, single prints might attract future trading activity since buying or selling was potentially limited or unexpected around those values. Traders often monitor them as potential levels that price might revisit and as possible areas of support or resistance. Enable the "Single prints" option in the "Style" tab of the indicator's "Settings" to highlight single prints on the chart.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43468449984/original/r6kxnkK7yf8XjM8VMbV8z9KMJsTX5nguCg.png?1708449201)

Note that the indicator will highlight the first single print established in the event of consecutive occurrences.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43468450170/original/iEAz2vwCZu9eqPM7Wbpt5-qbkkpClkBzBw.png?1708449242)

#### Poor high and Poor low

Poor highs and lows are extreme levels with more than one TPO block. In TPO analysis, these levels signify where directional movement halts without clear rejection, revealing flat, narrow tops or bottoms on the chart. This pattern suggests the market might have yet to fully explore prices beyond the profile's high/low, potentially leaving room for further extended movement. Poor highs and lows lack the characteristic tapering indicative of a strong reversal. They pique the interest of market participants seeking further range exploration. Although they are not necessarily strong support/resistance points, these levels can indicate where the market's momentum paused, offering unique insights for trading strategies.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43468450355/original/2ykwbupa_X8mXX1vviepciOvAbrqCMWdeA.png?1708449291)

#### Splitting and merging profiles

Users can split or merge individual profiles displayed on the chart to inspect activity across specific regions on the chart with different levels of detail. To use this functionality, right-click a displayed profile and select the appropriate option at the bottom of the contextual menu.

The "Split profile at this letter" option will split a selected profile spanning two or more time blocks into two separate profiles at the TPO block the user clicked:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43479867670/original/CILL3qOrQv55RneoLYUCMqTcNuKmcIbk6g.gif?1713280752)

The "Merge with previous profile" option will combine the selected profile with the previous profile displayed on the chart. This option is only available if the selected profile is not the first on the chart:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43479867732/original/_ARu9wGbp64vWSvMmmi3gETe_qmm3rDF4Q.gif?1713280766)

The "Reset all merges and splits" option reverts all profile split and merge actions. Note that splits and merges also reset when changing the "Period" or the "Block size" values in the indicator's inputs.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43468450355/original/2ykwbupa_X8mXX1vviepciOvAbrqCMWdeA.png?1708449291)

#### Indicator inputs

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43440920186/original/AK-WF7ST0Zpc4H0TPTVSSESRVRfGKdP_KQ.png?1696578606)

#### Period

The number of days, weeks, or months that each profile covers. The default is one day.

#### Block size

The size of the time blocks that divide the profile's period. Smaller block sizes produce more granular results. The possible values are 5m, 10m, 15m, 30m, 1h, 2h, or 4h. The default is 30m. This value affects the calculation of the TPO and Volume profiles.

#### Row size

The mode used to determine the size of the profile's rows. In the default setting ("Auto"), the indicator displays its calculated row size in the "Ticks per row" field. In "Manual" mode, the user specifies the number of ticks per row.

#### Tick per row

The number of ticks in each profile row, which affects the number of rows each profile will contain. Users can only enter a value into this field if the "Row size" mode is "Manual". If the value is too small, the indicator will raise an error.

#### Value area percentage

The percentage of total TPO blocks used in the Value Area calculation. The default value is 70.

#### Style

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43468401764/original/PPxLMwLbItlcQWaO4AF7-AuP6ghUvlhzEg.png?1708439252)

#### Gradient colors

These are the colors used for the TPO blocks' color gradients. The first two colors define the from/to range for the A-Z blocks. The last two colors specify the color range for a-z blocks.

#### Blocks

Toggles the display of colored TPO blocks. This setting has no effect if "Letters" are enabled but cannot show on the chart due to a lack of space.

#### Letters

Toggles the display of TPO letters. When enabled, the indicator only shows letters if the chart has sufficient space. Otherwise, it will show colored blocks instead.

#### Opacity outside VA

Sets the opacity value for levels outside the Value Area boundaries.

#### Split by blocks

When enabled, the indicator distributes the display of TPO blocks across successive intervals in the period rather than consolidating them at the left of the period. This feature can help traders understand the calculation of the profile's constituent blocks and provide additional insight into the flow of price activity over time.

#### POC

The checkbox toggles the POC label and row highlight, and the dropdown determines whether the indicator extends the row highlights past each profile's period until price intersects the level again. When POC display is enabled, the indicator colors the POC row and label using the chart's foreground color.

#### Poor high

The checkbox toggles the Poor high label and line, and the dropdown determines whether the indicator extends the line past the profile's period until price intersects it.

#### Poor low

The checkbox toggles the Poor low label and line, and the dropdown determines whether the indicator extends the line past the profile's period until price intersects it.

#### Single prints

The checkbox toggles the Single print highlight, and the dropdown determines whether the indicator extends the highlight past the profile's period until price intersects it.

#### VAH

Toggles the Value Area High label and line.

#### VAL

Toggles the Value Area Low label and line.

#### TPO midpoint

Toggles the visibility of the profile's median price label.

#### Open price

Toggles the visibility of the profile's opening price label.

#### Close price

Toggles the visibility of the profile's closing price label.

#### Initial Balance Range

The checkbox toggles the display of the Initial Balance Range as a vertical line to the left of the profile, and the text field defines the number of blocks in the IBR calculation.

#### Volume profile

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43531788605/original/GlrH4cAd0XQbxnnipXYWkWz2G8tN-xqSrA.png?1735379763)

#### Show volume profile

Toggles the display of the Volume Profile to the right of the TPO Profile.

#### Values

The checkbox toggles labels that display volume values at each row and the period's total volume below the profile. The color selector specifies the color of the labels. The indicator only shows these labels when the chart has sufficient space.

#### VAH

Toggles the Volume Profile's Value Area High line, and specifies the color and line style.

#### VAL

Toggles the Volume Profile's Value Area Low line, and specifies the color and line style.

#### POC

Toggles the Volume Profile's Point of Control line, and specifies the color and line style.

#### Volume

Determines the color of levels outside the Value Area.

#### Value Area

Determines the color of levels inside the Value Area.

#### Alignment

Determines whether the volume profile aligns to the left or right.