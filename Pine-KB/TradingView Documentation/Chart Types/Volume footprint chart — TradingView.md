<iframe src="https://www.youtube.com/embed/0WggFVVsmkM??si=v0DFBI8iZE4Lrwh_&amp;wmode=opaque" frameborder="0" allowfullscreen="" data-identifyelement="488"></iframe>

#### Definition

Volume footprint is a powerful charting tool that visualizes the distribution of trading volume across several price levels for each candle on a specified timeframe, providing traders with additional information to help identify areas of high liquidity or significant trading activity. Users with Premium and higher-tier plans can view volume footprints on their charts by selecting the "Volume footprint" option from the chart type dropdown menu.

By default, this chart type displays the distribution of seller volume to the left of each candle and buyer volume to the right with optional gradient colors that signify the relative intensity of the volume on each level, and it places vertical lines beside levels in the distributions to highlight significant areas of imbalance. In addition, it indicates each bar's Value Area (VA) and Point of Control (POC), and it displays volume delta and total volume information below each candle.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43481035650/original/7jWofOedIHQDMLJ1GC-W6HQL9nUIQ6zy8Q.png?1713798415)

See the "Settings" section below to learn about the different footprint display types and all other chart customization options.

#### Calculation

#### Volume data source

This chart type retrieves a symbol's volume data from several intrabar timeframes, i.e., timeframes lower than the chart's, for its historical calculations. The timeframe gradually increases with the exhaustion of available historical data, starting with the lowest available timeframe. In other words, the deeper into the chart's history, the higher the intrabar timeframe of the volume data. The footprints for the chart's recent candles are the most precise since they use the most granular information in their calculations.

The order by which the chart requests intrabar timeframes for its calculations is 1S, 1, 15, 60, then 1D. The highest intrabar timeframe requested for historical footprints depends on the chart's timeframe.

#### Volume categorization

The Volume footprint chart categorizes volume as "buy" or "sell" based on the direction of intrabar price movements. It uses the following algorithm to determine the category of each volume value:

-   If the intrabar's closing price exceeds its opening price, it assigns the volume to the "buy" category.
-   If the intrabar's closing price is below its opening price, it assigns the volume to the "sell" category.
-   If the closing price equals the opening price:
    -   The volume will belong to the "buy" category if the current intrabar's close exceeds the previous intrabar's close.
    -   The volume will belong to the "sell" category if the current intrabar's close is below the previous intrabar's close.
    -   The volume will belong to the same category as the previous intrabar if their closing prices are equal.

The chart accumulates the categorized volume across the lower timeframes at different price levels to construct the footprint representation.

#### Imbalance detection

A balanced market occurs when there's an equilibrium between supply and demand, typically resulting in relatively stable prices. In contrast, an imbalanced market occurs when there is a significant disparity between supply and demand, often leading to more substantial price movements.

The Volume footprint chart detects a buy imbalance when the "buy" volume at a price level exceeds the "sell" volume at the level below by a specified percentage. Similarly, it detects a sell imbalance when the "sell" volume at a level exceeds the "buy" volume at the above level by that percentage. Users can control the percentage by which the "buy" volume must exceed the "sell" volume, or vice versa, to detect an imbalance via the "Imbalance" input in the chart's settings. By default, its value is 300% (i.e., the volume of one side must be three times larger than the other).

When it detects a "buy" imbalance, the chart will display a vertical line to the right of the corresponding price level. When a "sell" imbalance occurs, a vertical line will appear to the left of the level:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43488069251/original/bGTPGoJI3oRUu3pQnQOozpgjzP5J-Xw9Xg.png?1716812277)

In the given example, a sequential comparison of volumes at different levels is carried out. For each comparison, the assessment determines whether the larger volume of the pair exceeds the specified imbalance threshold, according to the formula: max(buy, sell) ≥ (imbalance percentage / 100) \* min(buy, sell).

The initial calculation is as follows: 506.37 ("buy") ≥ (300 / 100) \* 166.433 ("sell"). This statement holds true, indicating a buy imbalance. Subsequent comparisons adhere to the same logic: "buy" level 3 is compared with "sell" level 2, and "buy" level 4 with "sell" level 3.

Traders often analyze volume footprints to identify balance and imbalance within the market. When a market is in a state of balance, a volume footprint may show evenly distributed trading volume across various price levels, suggesting stability and equilibrium. Conversely, while in an imbalanced state, a volume footprint may reveal clusters of elevated trading activity at specific levels, indicating areas of supply or demand disparity and potential price trends.

#### Interpretation

#### Order flow

During the order execution process, market participants engage in a search for price equilibria that will satisfy both buyers and sellers, thus driving transactions. The directed volume of each transaction determines its contribution to a market's buying or selling pressure. In cases where supply surpasses demand, downward price movement may occur as the market gravitates toward more equitable prices for buyers. Conversely, when the demand for an asset exceeds its supply, prices may ascend until enough participants are willing to sell.

Analyzing the concentration of buying and selling activity across price levels with the Volume footprint chart can provide deeper insight into the dominance of buyers and sellers, the balance or imbalance between supply and demand, and areas of elevated liquidity (i.e., areas with a greater abundance of trading activity). Traders can utilize such insights to gauge market sentiment and identify trading opportunities.

#### Failed auction

In Auction Market Theory, a failed auction is a pattern in which the market fails to establish a new price for an instrument, resulting in a return to previous prices. Traders conventionally analyze failed auctions with tools such as Market Profile, but one can also identify instances of such patterns using footprints.

A failed auction typically occurs when one side of the market, either buyers or sellers, fails to attract enough participation to sustain trading activity at a price level, potentially leading to a rapid price reversal as market participants reassess and adjust their positions. Failed auctions often coincide with heightened volatility, and they can indicate potential key turning points in the market.

Traders and analysts often pay close attention to failed auctions, as they can provide helpful insights into market dynamics and trading opportunities. Identifying failed auction states can help traders identify support and resistance levels and anticipate potential reversal patterns.

The example below demonstrates a case where prices moved successively higher with each bar while buyer volume gradually decreased. On the fourth bar in the image, the imbalance between sellers and buyers reached a point where buyers could not push the price further upward, and the price rebounded downward. One can interpret this area of imbalance as a possible resistance level. If prices break the level in the future, it might suggest a growing trend:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43482198815/original/_XhpfOnvTyvlXYkHrU0DCGxAk60AfX0mOQ.png?1714222051)

#### Delta divergence

Delta divergence in volume footprints refers to a discrepancy or disagreement between price movement and volume delta.

Positive delta divergence occurs when prices successively move downward while the volume delta rises, possibly even turning positive. Conversely, negative delta divergence occurs when prices successively rise while the volume delta falls or even becomes negative. These divergence patterns often suggest that, despite the current price action, the underlying buying or selling pressure is diminishing, potentially signaling the weakening or reversal of the current trend.

The example below shows four falling bars, two of which have a positive delta. In other words, those bars exhibit positive delta divergence:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43481038686/original/WAcJSl-lV9gnOQGQKDNzapNu3cWPtCkcLw.png?1713799027)

Traders often analyze delta divergence in footprint charts to help them anticipate potential reversals or changes in market direction. However, it's essential to consider other factors and utilize additional tools to help validate divergences and make informed trading decisions.

#### Excess trades at extreme price levels

In Auction Market Theory, the market price ascends until the exhaustion of demand and descends until the exhaustion of supply. This exhaustive movement is a complete auction. On a footprint chart, this situation appears as zero or minimal purchases at the low price level or minimal sales at the high price level.

In some cases, a situation referred to as an incomplete auction may arise, where the difference between buying and selling volume at the high or low levels differs slightly relative to the differences on previous levels. This condition may indicate that price exploration is incomplete, and there may still be interested market participants above the current highs or below the current lows. In essence, this pattern might indicate that the market price may continue its directional movement past the current range until the end of the auction.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43481038899/original/NHsY8x8BSfUaPm-ZauEBhRWGGRkMN9fgOg.png?1713799058)

#### Settings

Customization options for the Volume footprint chart are available from the chart settings, which users can access from the "gear" icon in the toolbar above the chart, the icon in the chart's bottom-right corner, or from the "More" menu accessed by clicking the three dots next to the symbol name.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43486059778/original/VeuLsEVdoIOXrqGVNEiQz4JKoKGxICO3Zw.png?1715868092)

#### Candles

The settings in the "Candles" section are identical to those for a regular candlestick chart. From this section, users can configure the appearance of the candlesticks.

#### Volume Footprint

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43486059893/original/V1kmw0p0CywOJi5SR6Sq2QRUOMyfR94r7w.png?1715868116)

#### Row size

Controls how the chart will determine the size of each footprint row (level). There are two options to choose from:

-   The "Auto" option specifies that the chart will calculate the size automatically based on the data's latest normalized Average True Range (ATR) value. It uses the formula: 0.2 \* NormalizedATR / MinimumTick. The chart recalculates the size when selecting the "Volume footprint" chart type or changing the symbol or timeframe. When using this option, the input below specifies the length of the ATR calculation.
-   The "Manual" option specifies that the chart will utilize the number of ticks specified in the "Ticks per row" input below.

#### ATR length

Specifies the smoothing length for the Average True Range used to calculate the number of ticks per footprint row when the "Row size" input uses the "Auto" option.

#### Ticks per row

Specifies the number of ticks per footprint row when the "Row size" input uses the "Manual" option.

#### Type

Defines the display mode of the footprints on the chart. Three options are available:

-   The "Buy and Sell" option (default) displays seller volume across levels to the left of each candle and buyer volume to the right.
-   The "Delta" option will display one column to the right of each bar that shows the volume delta (i.e., the difference between buyer and seller volume) for each level.
-   The "Total" option will display one column to the right of each bar that shows the total volume at each price level.
-   The "Ladder" option will highlight with color the highest volume on each price level.

#### Apply gradient to background

If enabled, the color of the background of each footprint level will differ based on its volume compared to the volume at other levels. The chart uses the following algorithm to calculate the gradient colors:

1.  Determine the maximum and minimum volume.
2.  Calculate the volume range, i.e., the difference between the maximum and minimum volume value.
3.  Subtract the minimum volume from the current level's volume.
4.  Calculate the ratio of the value obtained in step 3 by the volume range obtained in step 2.
5.  Use the ratio from step 4 to select a color from the available options:
    1.  Select the first color if the ratio is less than 0.25.
    2.  Select the second color if the ratio is greater than or equal to 0.25 and less than 0.5.
    3.  Select the third color if the ratio is greater than or equal to 0.5 and less than 0.75.
    4.  Select the fourth color if the ratio is greater than or equal to 0.75.
6.  Repeat steps 3 through 6 for each price level.

When the footprint type is "Buy and sell" or "Delta", the chart calculates the gradients for the buy and sell sides separately.

#### Background

These inputs specify the background colors used by the footprint levels. Users can choose separate colors for buy and sell sides when the footprint type is "Buy and sell" or "Delta". If the "Apply gradient to background" option is enabled, a four-color gradient will be available for each color option. The chart will select colors for each level using the algorithm described in the previous section.

#### Value Area

Enables Value Area (VA) lines and specifies the VA percentage. The Value Area High (VAH) line will appear above all levels included in the Value Area, and the Value Area Low (VAL) line will appear below all levels in the Value Area. The Volume footprint chart's Value Area algorithm is similar to the algorithm used by our [Volume Profile indicators](https://www.tradingview.com/chart/?solution=43000502040).

#### Labels

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43486060012/original/o6Ku99X06Dgi4W7YzRch2o1QGPhvYiPAlw.png?1715868130)

#### POC

Determines whether the chart will display each footprint's Point of Control (POC).

#### Show summary info

Determines whether each footprint will display information about the bar's total volume, the total buy and sell volume, and the overall volume delta.

#### Imbalance

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43486060041/original/hMq-yw8HRFbWYwwyhe-aw7qA18o649Pn0Q.png?1715868136)

Specifies the percentage by which buyer volume must exceed seller volume, or vice versa, to detect a significant imbalance. See the "Imbalance detection" section above to learn how the Volume footprint chart detects imbalances.

#### Highlighting

Determines whether the chart will highlight imbalanced price levels and specifies the colors. When imbalance highlights are enabled, the chart places colored vertical lines to the sides of significantly imbalanced levels. The chart displays buy imbalance markers to the right of the levels and sell imbalance markers to the left.

#### Stacked levels

Controls whether to display stacked imbalances and the number of required consecutive levels with an imbalance on the same side to detect a stacked imbalance. When enabled, the chart projects stacked imbalances until subsequent prices intersect the levels.