#### <iframe src="https://www.youtube.com/embed/J6Cte-D9Gxk??si=PR4HHzQ6v_RGih0l&amp;wmode=opaque" frameborder="0" allowfullscreen=""></iframe>  

#### Definition

Volume Profile is an advanced charting indicator that displays trading activity over a specified time period at specified price levels. The indicator takes into account user-defined parameters such as number of rows and time period and plots a histogram on the chart meant to reveal dominant and/or significant price levels based on volume. Essentially, Volume Profile takes the total volume traded at a specific price level during the specified time period and divides the total volume into either up volume (trades that moved the price up) or down volume (trades that moved the price down) and then makes that information easily visible to the trader.

You can use the following Volume Profile types:

1.  [Auto Anchored Volume Profile](https://www.tradingview.com/chart/?solution=43000703077)
2.  [Fixed Range Volume Profile](https://www.tradingview.com/chart/?solution=43000480324)
3.  [Periodic Volume Profile](https://www.tradingview.com/chart/?solution=43000703071)
4.  [Session Volume Profile](https://www.tradingview.com/chart/?solution=43000703072)
5.  [Session Volume Profile HD](https://www.tradingview.com/chart/?solution=43000557450)
6.  [Visible Range Volume Profile](https://www.tradingview.com/chart/?solution=43000703076)

#### Basic concepts

##### Calculation algorithm

Volume Profile indicators are calculated using the data for the same symbol from the lower timeframes. For example, to calculate the Volume Profile for one daily session, we load all 1m bars that were traded in that daily session, analyze the price levels where they were traded and the direction that the price moved in – if the bar closes above or equal to its open, this counts as an Up bar, otherwise it's a Down bar. Once analyzed, this data is added to the Volume Profile histogram.

The particular logic used to decide which lower timeframe should be used for the calculation differs on an indicator-by-indicator basis.

##### Volume uses in the calculations

Volume Profile uses the following types of volume:

-   trade volume - for stocks.
-   tick volume\*  - for indices/forex and crypto cfd
-   base or quote volume - for crypto 

_\* tick volume indicates the amount of price updates__._We use up/down volume instead of buy/sell volume and calculate VP based on a price direction inside bars: if close >= open, we take it as an Up Volume, if close < open, it's Down Volume.

##### Typical levels of significance

Point of Control (POC) – The price level for the time period with the highest traded volume.

Profile High – The highest reached price level during the specified time period.

Profile Low – The lowest reached price level during the specified time period.

Value Area (VA) – The range of price levels in which the specified percentage of all volume was traded during the time period. Typically, this percentage is set to 70%, however, it is up to the trader’s discretion.

Value Area High (VAH) – The highest price level within the value area.

Value Area Low (VAL) – The lowest price level within the value area.

##### Calculating Value Area (VA)

1.  Determine the total volume traded in the profile (total buys and sells).
2.  Take the number of total buys and sells and multiply it by .7 to determine what number is 70 percent of the total buys and sells. (70% is the default; however, any percentage can be used by the trader).
3.  Start at the Point of Control (POC), The row in the profile with the greatest total volume, and record its total volume number. The POC will be the first profile row added to the Value Area.
4.  Now look at the two rows above the POC (the initial value area) and add the total volume of both.
5.  Now look at the two rows beneath the POC (the initial value area) and add the total volume of both.
6.  Determine which of the total volume numbers is larger and add it to the total volume number of the POC found in step 3.
7.  Repeat steps 4 and 5 adding the larger of the next two numbers to the Value Area.
8.  Once the total volume of your Value Area matches or slightly surpasses the number found in step 2, the Value Area has been determined.
9.  The highest row within the Value Area will be your Value Area High (VAH) and the lowest row within the Value Area will be your Value Area Low (VAL).

##### Сalculation on non-standard chart types (Heikin Ashi, Renko, etc.) 

If you're using the volume profile indicators on this kind of chart, it's important to consider that the data on the chart is synthetic (i.e., does not represent actual prices) and the volume data is also affected by that. For example, a single daily candle that closes above its open can become N separate Renko bricks rising in a sequence, and the daily volume for that candle will be divided by N and the resulting value will be given to every brick in the sequence. Failing to account for this can result in inaccurate predictions and hinder the effectiveness of your trading strategy.

#### Style

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43517104427/original/yH52fedSy3WpXYOhs8978n0Rrs-jPZY4yA.png?1728996382)

##### Volume Profile

Toggles the visibility of the volume histogram.

##### Values

Toggles whether the numerical values should be displayed on the volume histogram itself and adjusts the color of the text. What these values signify depends on the Volume input in the indicator's Inputs tab: with "Total" selected, it shows the total volume for this row, "Up/Down" shows both Up and Down volume in a sequence, and "Delta" shows only the delta, i.e., the difference between the Up and Down volume for the level.

##### Width (% of the box)

Alters the width of the rows in the histogram. The longest row is scaled according to this setting, and all other rows are based on its scaling: e.g., if the indicator displays 3 rows with volumes of 20K, 40K and 100K and Width is set to 40, the 100K row will extend 40% of the width of the histogram, the 40K will extend 40% of 40% (16% of total), and 20K will extend 20% of the 40% (8% of total).

##### Placement

Place rows either left or right.

##### Up Volume

Determines the color as well as opacity for the Up Volume (Buys).

##### Down Volume

Determines the color as well as opacity for the Down Volume (Sells).

##### Value Area Up

Determines the color as well as opacity for the Value Area Up.

##### Value Area Down

Determines the color as well as opacity for the Value Area Down.

##### VAH

Toggles the visibility of the Value Area High.

##### VAL

Toggles the visibility of the Value Area Low.

##### POC

Toggles the visibility of the Point of Control.

##### Developing POC

Toggles the visibility of the Developing Point of Control, showing you how POC was changing when the market was in session.

##### Developing VA

Toggles the visibility of the Developing Value Area, showing you how VA was changing when the market was in session.

##### Histogram Box (unavailable for Visible Range Volume Profile)

Determines the background color as well as opacity for the Volume Profile area.

#### What to look for

##### Support and Resistance Levels

The first thing that most traders will use volume profile for is identifying basic support and resistance levels. It is important to note that using Volume Profile as an identifier for support and resistance levels is a reactive method. This means that unlike proactive methods (such as trend lines and moving averages) which are based on current price action and analysis to predict future price movements, reactive methods rely on past price movements and volume behavior. Reactive methods can be useful in applying meaning or significance to price levels where the market has already visited. Basic technical analysis has shown that a support level is a price level which will support a price on its way down and a resistance level is a price level which will resist price on its way up. Therefore, one can conclude that a price level near the bottom of the profile which heavily favors the buy side in terms of volume is a good indication of a support level. The opposite is also true. A price level near the top of the profile which heavily favors sell side volume is a good indication of a resistance level.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43517104578/original/2YyfokkdVVy2uw0jDOW9YPV27SDH3wiOEw.png?1728996409)

##### Volume Nodes

High Volume Nodes (HVN) are peaks in volume at or around a price level. HVN can be seen as an indicator of a period of consolidation. Usually there is a great deal of activity on both the buy and sell side and the market stays at that price level for a great deal of time compared to other levels in the profile. This can imply a “fair value area” for the asset. When price approaches a previous HVN (or fair value area) a sustained period of sideways movement is expected. The market is less likely to immediately break through that price.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43517104637/original/AJF2hsUH0W1ggN8CFnDuuTUdfKXQ7S4rLA.png?1728996426)

Low Volume Nodes (LVN) are the opposite. They are valleys (or significant drops) in volume at or around a price level. Low Volume Nodes are usually a result of a breakout rally or a breakdown. During a rally or a breakdown, there will typically be an initial burst of volume and then a significant drop off. The drop off can imply an “unfair value area” for the asset. When price approaches a previous LVN (or unfair value area), the market is much more likely to rally through or bounce off of that price level. Because it is seen as an unfair value area, the market will not spend as much time there compared to some other levels in the profile.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43517104683/original/0b0cAOwYlSPOhFD5u-oKAKuAYhEnPt_57Q.png?1728996438)

#### Example strategy

Just like with most other tools or studies, Volume Profile has a number of uses. There are many trading strategies out there using Volume Profile as a key component. Below are the basics of one such strategy which is based on comparing the current day’s opening price to the previous day’s Volume Profile:

-   If the current day opens above the previous day’s value area (but still below the Profile High) look for price to retrace back towards the Point of Control and then proceed to rise (the direction of the day’s open). Therefore during the retracement to the Point of Control, there is a buying opportunity.
-   If the current day opens below the previous day’s value area (but still above the Profile Low) look for price to retrace back towards the Point of Control and then proceed to fall (the direction of the day’s open). Therefore during the retracement to the Point of Control, there is a selling opportunity.
-   If the current day’s opening price is completely outside of the previous day’s profile (above the Profile High or below the Profile Low) this can be seen as a possible runner in the direction of the opening price relative to the previous day’s profile range.

#### Summary

Volume Profile is an extremely valuable technical analysis tool that is used by traders everywhere. The key to Volume Profile’s continued relevance is its versatility. It is a charting tool that truly does have a wide array of uses. Unlike many other studies, there is little to no debate about Volume Profile’s usefulness. The data that is provided by Volume Profile is indisputable, leaving it to the trader to find new and creative ways to use it. Even though in its simplest form, it is a great reactive method for discovering traditional support and resistance areas, traders are still coming up with ways to chart the indicator in predicative or proactive ways. Consider the trading strategy example given earlier in the article. Being able to compare a real-time event (the current day’s open) with historical events (the previous day’s volume profile) and make a trading decision based on the relationship is a great example of this.