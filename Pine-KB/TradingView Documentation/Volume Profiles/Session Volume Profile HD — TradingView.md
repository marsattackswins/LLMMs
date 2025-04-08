#### <iframe src="https://www.youtube.com/embed/sLOmfOjOM_c??si=DQkXQsXLR7BwOxcO&amp;wmode=opaque" frameborder="0" allowfullscreen=""></iframe>  

#### Definition 

Session Volume Profile HD (SVP HD) indicator calculates volume data within a specified session or a sub-session, allowing traders to analyze the intraday volume activity of one specific part of the session. Additionally, unlike the regular Session Volume Profile, it automatically adjusts the level of detail as you zoom the chart. When fewer bars appear on the chart, more levels are displayed. 

> _Note: you can read more about traits shared by all Volume Profile indicators in the_ _[Volume Profile Indicators: basic concepts](https://www.tradingview.com/chart/?solution=43000502040)_ _Help Center article. The text below describes features unique to this particular Volume Profile indicator._

#### Calculation

Session Volume HD consists of two different calculations: a rough one and a detailed one. The detailed calculation applies to the visible part of the chart and adjusts the number of rows in all visible Volume Profiles automatically. For this calculation, the lower timeframe data is selected based on the same logic as with [Visible Range](https://www.tradingview.com/chart/eufRBV30/?solution=43000703076) (with the exception of all second-based timeframes, which use 1S data).

The rough part is shown while the detailed part is still being calculated, and its timeframe selection is equivalent to the one in the regular [Session Volume Profile](https://www.tradingview.com/chart/eufRBV30/?solution=43000703072) indicator.

#### Alignment by the end of the year 

if the volume profile should include a yearly milestone, then at the end of the year such a profile will be completed and will start over again from the new year. This is necessary to maintain consistency when building profiles on different timeframes. 

#### Why is Rows Layout and Row Size not available for SVP HD?

Session Volume HD will automatically adjust the level of detail as you zoom the chart's scale. When you zoom in on a chart, the level of detail increases.

#### Inputs

##### 

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43412004779/original/r8zlmYun-dKidyr8hhG3FA2WS7dVWExUGw.png?1684839437)

##### Sessions

Determines how the SVP HD indicator will be built when the extended hours display is turned on. 

-   All.  If set to "All" (default), the indicator will consider the pre-market, main trading session and post-market as one session. One profile will be built for each trading day and it will include the volume for all transactions, starting from the first pre-market candle and ending with the last post-market candle. 
-   Each. The "Each (pre-market, market, post-market)" option allows you to build a separate volume profile for each part of the trading day session, taking into account only deals made during that period. If the symbol has extended hours with pre-market, main session and post-market, the indicator will build three separate profiles for each trading day. 
-   Pre-market, Market, Post-market.With the dedicated "Pre-market", "Market" and "Post-market" options, the indicator will only build one volume profile per trading day, based on the trades for the specified session period. These settings should be used only on charts with extended hours. If there is no extended hours data on the chart or if the Extended Hours display is turned off, the indicator will not be able to build a volume profile for pre- or post-market. 
-   Custom. The "Custom" option gives you the opportunity to configure the beginning and end of the period for which the profile will be built. You can also choose a time zone.

##### Volume

Toggles between showing total volume for each row (Total), splitting each row into up/down (Up/Down), or showing their difference (Delta).

##### Value Area Volume

Specifies what percentage of all volume for the trading session should be highlighted by Value Area.

##### Extend POC Right

Extends the Point of Control line until it crosses any bar.

##### Extend VAH Right

Extends the Value Area High line until it crosses any bar.

##### Extend VAL Right

Extends the Value Area Low line until it crosses any bar.