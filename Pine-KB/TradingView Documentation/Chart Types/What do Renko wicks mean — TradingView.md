On a Renko chart, wicks show major price moves inside a Renko box, if they happened.

A new Renko brick is built based on a value specified in the Renko chart's Box Size (either directly, when the Box Size Assignment method is set to Traditional, or indirectly, when it's set to ATR). The conditions for a new brick to appear are based on the direction of the last created Renko brick: to create a new brick that moves in the same direction as the last one, the price needs to move 1x Box Size in that direction. But to reverse and create a move in the opposite direction, the price needs to move 2x Box Size: first to get to the level of the open of the last brick, and then to move one Box Size beyond it.

Sometimes, the price moves more than one Box Size but less than two in the direction opposite of the direction of the last brick. This indicates an obvious price swing that wasn't enough to turn the Renko chart, but came close to it. These moments are highlighted on the Renko chart with wicks. Consequently, High wicks will only appear on bricks that move down, and Low wicks will only appear on bricks that move up.

Wicks are enabled by default on Renko charts. You can adjust wick color & enable/disable them in the Symbol tab of the Chart settings dialog.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43329508829/original/V9fqHHPI5_mZFM9UFjaKroPaevzsJEGrxw.png?1654272736)

Renko wicks are based on actual prices present on the regular, non-Renko chart, unlike Renko bricks' Open and Close which are synthetic and are always divisible by the chart's Box Size. The source for these values depends on the source for the whole Renko chart (also specified in Chart settings): if the Renko chart is based solely on Close, wicks will represent highest/lowest Close values; if OHLC is chosen, highest and lowest wicks will be based on High and Low values respectively.

Let's examine a specific case: 

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43329508892/original/YOR5FWjpM5qSw6uEEFgbkNtscD-Ra8UWMw.png?1654272751)

On the screenshot above, we have a Renko chart of AAPL with 1D timeframe. Source is set to OHLC, and the Box Size is 3. 

There is a sequence of two downward-moving bricks, with the second one formed on 11 Apr '22. The next brick is also going down and was formed on 18 Apr '22. It has a High wick of 171.27.

On the chart below that, we open the same symbol and timeframe, but on a regular candlestick chart, and check what candles the 18 Apr '22 brick is based on. As the previous brick formed on 11 Apr '22, everything after that date and up to and including 18 Apr '22 is used to build the next brick.

In this case, before the price moved down to 165, where a new down brick could be formed, it first moved up to 171.21. This was above the open of the previous brick (171), but not enough to turn the direction of the Renko chart up. After that level was reached, the price fell, which caused another down brick to form. The swing in the Up direction is reflected with a High wick on a resulting Renko brick.