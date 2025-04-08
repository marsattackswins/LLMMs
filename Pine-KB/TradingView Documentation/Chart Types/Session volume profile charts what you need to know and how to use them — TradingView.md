<iframe src="https://www.youtube.com/embed/-N9sql9Zkss?&amp;wmode=opaque" frameborder="0" allowfullscreen=""></iframe>  

Session volume profile (SVP) chart shows volume histograms for the specified sessions, sub-sessions, or time intervals set in the settings. It calculates volume data, allowing traders to analyze the intraday volume activity of one specific part of the session.

#### 

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43539691728/original/AgETxojlaM5A4jlndzEXu-uAk2GHmDknAw.png?1739015694)

#### Enabling the chart type

Once you are on the Supercharts, open the chart type menu on the upper toolbar, and select Session volume profile.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43539691730/original/yzRtsoYYPJDhbFI4PahlMynWuA0PRCIH5Q.png?1739015694)

#### Settings

To adjust your session volume profile chart, choose Settings on the upper toolbar, and go to the Symbol tab.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43539691729/original/D0ZPHUiitQXB5HqHDtDT-5xt8g-mOwLaFQ.png?1739015694)

There are several sections with settings specific to the SVP chart.

#### Volume Profile

In the Volume profile section, you can enable the display of values on histogram columns, adjust the columns' width, and the colors of the histogram.

1.  Values. Toggle visibility and set color for the values seen on the chart’s left side.
2.  Width. Alter the width of the columns in the histogram. 
3.  Placement. Flip the bars to the left or right of the trading session area.
4.  Up Volume. Determine the color as well as opacity for the Up Volume (Buys).
5.  Down Volume. Determine the color as well as opacity for the Down Volume (Sells).
6.  Value area up. Determine the color as well as opacity for the Value Area Up.
7.  Value area down. Determine the color as well as opacity for the Value Area Down.
8.  Histogram box. Determine the background color as well as opacity for the Volume Profile area.

#### Lines

In the Lines section, you can activate lines such as POC (Point of Control), VAH (Value Area High), VAL (Value Area Low), developing POC, and developing VA.

1.  VAH. Toggle the visibility of the Value Area High.
    1.  Extend VAH Right. Extends the Value Area High line until it crosses any bar.
2.  VAL. Toggle the visibility of the Value Area Low
    1.  Extend VAL Right. Extends the Value Area Low line until it crosses any bar.
3.  POC. Toggle the visibility of the Point of Control.
    1.  Extend POC Right. Extends the Point of Control line until it crosses any bar.
4.  Developing POC. Toggle the visibility of the Developing Point of Control, showing you how POC was changing when the market was in session.
5.  Developing VA. Toggle the visibility of the Developing Value Area, showing you how VA was changing when the market was in session.

#### Inputs

You can set up a session in the Inputs section where the volume, line placement, and level size will be displayed.

1.  Sessions. Determines how the session volume profile chart is built.

-   All. If set to "All" (default), the indicator will consider the pre-market, main trading session and post-market as one session. One profile will be built for each trading day and it will include the volume for all transactions, starting from the first pre-market candle and ending with the last post-market candle. 
-   Each. The "Each (pre-market, market, post-market)" option allows you to build a separate volume profile for each part of the trading day session, taking into account only deals made during that period. If the symbol has extended hours with pre-market, main session and post-market, the chart will build three separate profiles for each trading day. 
-   Pre-market only, Market only, Post-market only. With the dedicated "Pre-market only," "Market only," and "Post-market only" options, the chart will only build one volume profile per trading day, based on the trades for the specified session period.
-   Custom. The "Custom" option gives you the opportunity to configure the beginning and end of the period for which the profile will be built. You can also choose a time zone.

2.  Volume. Toggle between showing total volume for each row (Total), splitting each row into up/down (Up/Down), or showing their difference (Delta).
3.  Value Area Volume. Specify what percentage of all volume for the trading session should be highlighted by Value Area.
4.  Rows Layout / Row Size. Specify the way the chart calculates how many rows each histogram will have.

You can read more on how the values are calculated in our [article on the Session Volume Profile indicator](https://www.tradingview.com/support/solutions/43000703072/).