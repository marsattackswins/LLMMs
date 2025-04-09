<iframe src="https://www.youtube.com/embed/MvUHkmOzmaw??si=ib5SfKHI6zCkvy0x&amp;wmode=opaque" frameborder="0" allowfullscreen=""></iframe>  

Please note that the information about expected price targets provided by Auto Chart Patterns is not a recommendation for what you should personally do. Do not take this data as investment advice. It should only be used for education and research. As with any trade, always look first and then leap.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43498869803/original/7IeAqLG3J4ORzu1DjkKoT1mEZOQpmFfgXw.png?1721292721)

Cup and Handle is an indicator that highlights a continuation pattern: a U-shaped correction of the main trend - the cup - and another small corrective movement after the cup, which can also have a U-shape or be represented as a trend line with a downward slope - the handle. The edges of the cup should be approximately at the same level. It is expected that after the breakout of the trend line, the price will go further up by a distance equal to the height of the bowl.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43498870039/original/dFITxa3IS4OTyPncmREG2KbUH4QcZInnCA.png?1721292790)

The indicator searches for patterns on the last 600 bars. The pattern consists of a line outlining a cup and a line indicating a handle (_Price Line_). Points 1, 3 and 4, as marked in the screenshot, are located on 5/5 pivot points. A pivot point is a local extremum (minimum or maximum) to the left and right of which there are no price values that exceed this extremum. Thus, a point will be a 5/5 pivot high if there are no high values 5 bars to the left and 5 bars to the right of it that are higher than this value at this point. Point 2 is located in the center of the cup and at the price of a lowest low of the 5/5 pivot point, which is located in a small range to the left and right of the center of the cup. The minimum width of the cup is 20 bars, and the handle cannot be longer than the cup. 

In the _In_ _Progress mode_, the indicator searches not only for formed patterns, but also for patterns that are still being formed. The last point of such a pattern (point 4) may not be in the pivot point, in this case the handle line will be dotted. When forming the handle, the lowest low values between points 3 and 4 and between point 4 and the end of the handle are taken into account. The low between points 3 and 4 should be higher than the low between point 4 and the end of the handle line. The breakout of the pattern is based on the close value of the symbol.

The dotted line that ends with the _Target_  label indicates the expected price level after the pattern is fully formed. As new bars appear, the line extends to the right to the latest bar until the status of the pattern changes from _Awaiting_ to any other. The label's tooltip shows the price and the current status of the pattern. When the status changes, the color of the label changes as well. There are 4 statuses in total:

-   _Awaiting_ - the handle is not broken through, or it is broken through and at the same time the price has not gone below the threshold value (determined by the _Handle Max Rollback_ input) and has not reached the target yet.
-   _Reached_ - the price broke through the handle and reached the target.
-   _Failed_ \- the price did not reach the target and went below the threshold value, or the handle became longer than the cup.
-   _Indefinable_ \- the indicator cannot uniquely determine the status of the pattern.

If the indicator finds two overlapping patterns, then preference is given to the one with the _Awaiting_ status. If the statuses of the overlapping patterns are _Failed_ or _Reached_ or the status of both is _Awaiting_, then the chart will display the pattern whose cup shape is closer to the U-shaped one. A pattern with the _Indefinable_ status is deleted if it intersects with a pattern with a different status.

Alerts:

-   _New Pattern_. It is triggered when a new pattern appears on the chart. A pattern is considered new if it has a different position of point 1, 2 or 3.
-   _Pattern Breakout_. It is triggered when a bar appears that has closed above the handle line.

-   _Pattern Failed._ Triggers when the pattern status changes to failed. Triggers only if the pattern is fully formed.
-   __Target Reached.__ Triggers when the price reaches the pattern target. Triggers only if the pattern is fully formed.

Inputs:

-   _Patterns_ - determines which patterns will be displayed on the chart depending on their status. Possible values: All, Awaiting and Reached, Only Awaiting, Last Awaiting.
-   _Price Targets_ - determines which price targets will be displayed on the chart depending on the status of the pattern. Possible values: All, Only Awaiting, Awaiting and Reached, None.
-   _Permissible Deviation_ - determines the maximum allowable price difference along the edges of the cup. It is calculated as a percentage of the height of the cup.
-   _Handle Max Rollback_ - determines the maximum allowable price reduction in the handle, calculated as a percentage of the height of the cup.
-   _Cup Max Rollback_ - determines the maximum allowable decrease in the price in the cup relative to the previous trend. It is calculated as a percentage of the height of the previous trend. The checkbox enables/disables parameter check and trend search before the pattern. The option is disabled by default.
-   _In Progress_ - searching for the patterns which are being formed.