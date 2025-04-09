<iframe src="https://www.youtube.com/embed/q3dtVkMNMBw??si=F60QhQ1tG0H-mVSO&amp;wmode=opaque" frameborder="0" allowfullscreen=""></iframe>  

Range bars allow users to analyze the price movement of financial instruments, while also reducing market noise. Range bars don’t take time into consideration and are therefore able to create the so-called 'clean chart effect.' A new bar is formed when prices reach a certain value set by the user.

#### How are Range bars built?

-   A Range bar has an opening price (_Open_). The price movement is recorded when the bar is being formed. During that time, the size of the bar grows from the _Open_ point either up or down, depending on the price.
-   The difference between the highest (_High_) and the lowest (_Low_) bar value is considered as price movement.
-   Whenever the _High_ — _Low_ point reaches _Range_ interval, the formation of the bar finishes.
-   If the price moves in the \[_Low, High_\] range, the closing point (_Close_) of the bar changes.
-   When the price crosses the \[_Low, High_\] range, the bar closes and the new bar starts to form.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43407525197/original/NVoAFPPBngmyRMFBZPhCabr1a_yKYrbziA.png?1683022373)

#### How do I select Range bars on the chart?

There are two ways.

-   Select Range bars in the chart type menu in the top panel.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43407525397/original/Wlxcj987kiEYBVqfSFZw3ZEoTxBDRYYJpw.png?1683022422)

-   Select Range interval in the interval menu in the top panel.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43407525606/original/uPKclha_Z1TRGJVQzXZQuC5h7J2CA7fN8Q.png?1683022464)

#### What does Range interval mean?

Range interval sets the range in which the price moves, which in turn initiates the formation of a new bar.

1 Range equals one minimum price change. This value can be presented with the following formula.

_1 Range = Tick Size_

The values _Tick Size_ are displayed in the _Symbol Info_ menu (Right click on the chart series -> Symbol Info...).  

Please note that the time parameter does not affect Range bars, therefore when you choose the Range chart type, the interval of the chart will be automatically switch to Range interval by default or to the last used Range interval. 

#### What settings are available for Range charts?

There are two general styles - Bars and Candles. Let's look into the Properties of Bars Range charts:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43407525881/original/KGr0qkV3PCv132ogsdtx96gNoQwGiP-xqA.png?1683022541)

 

_Up bars_ — set the color of the up bar.

_Down bars_ — set the color of the down bar. 

_Projection up bars_ — set the color of the projection up bar.

_Projection down bars_ — set the color of the projection down bar. 

\*Projection bars — bars that are built based on the data of a temporary bar, that is still forming.

_Thin bars -—_ keep bars displaying always thin (otherwise they'll become bold when zoom in).

_Phantom bars_ — the display setting of virtual bars 

\*Phantom bars — bars that are built in price ranges, which were not traded.

_Last_ — the display setting of the line that shows the last price.

_Previous day close_ — the display setting of the line that shows the closing price of the previous trading day.

The settings of Candles Range chart are following:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43407528901/original/qltgCpD4xd6ixe7iZ0v3uYLjBcPJtVG_1A.png?1683023256)

_Body —_ set the color of the up / down candle body.

_Borders —_ set the color of the up / down candle border.

_Wick —_ set the color of the up / down candle wick

_Projection candles —_ set the color of the up / down projection candles

#### Features and limitations of Range bars

-   The set of 1 second interval bar values (_Open_, \[_High, Low_\], _Close_) are source data for Range bars.
-   Customizable intervals, other than predefined intervals, are only available to users on a paid plan, i.e. Pro Plus or higher.
-   The interval needs to be more than 10 Range to be able to publish an idea that is based on Range bars.
-   The Bar Replay is not supported for Range bars.