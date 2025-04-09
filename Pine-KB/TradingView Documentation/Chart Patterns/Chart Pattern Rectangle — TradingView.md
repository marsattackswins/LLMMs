Please note that the information about expected price targets provided by Auto Chart Patterns isn't a recommendation for what you should personally do. Do not take this data as investment advice. It should only be used for education and research. As with any trade, always look first and then leap.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43398793751/original/LFBbyEMLmAj_yNGBTtaidCR7MlCqVmCgOQ.jpg?1679314193)

A rectangle is an indefinite pattern that can herald both an increase and a fall in price. The target price level depends on the direction in which the price broke this pattern. It is expected that after the breakout of the pattern, the price will go approximately to the height of the rectangle in the direction of the breakout.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43398793867/original/8YH-_neV36dokhQM-WRKeK2an97g_5_UAQ.jpg?1679314219)

The indicator searches for patterns on the last 600 bars. The pattern consists of lines denoting price movements (_Price Line_) and lines forming a rectangle (_Rectangle_). The start and end points of each price line are in 5/5 pivots. A pivot point is a local extremum (minimum or maximum) to the left and right of which there are no price values that exceed this extremum. Thus, a point will be a 5/5 pivot high if there are no high values 5 bars to the left and 5 bars to the right of it that are higher than this value at this point. The breakout of the pattern is fixed by the close value. The intersection of the horizontal lines of the rectangle with the close value in the interval between points 1 and 4 is not allowed. In the _In Progress_ mode, the indicator looks for not only formed, but also emerging patterns. The last two points of such a pattern may not be in pivots, and the last price line will be dotted.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43398793950/original/0vF_41_gl3jK6rmDkHDDk6Pk3Oa6j0P3nQ.jpg?1679314244)

The dotted horizontal line that ends with the _Target_ label indicates the expected price level after the pattern is completed. If the pattern is not broken, then the indicator will draw 2 such lines – one in each direction. After the breakout, only the line in the direction of the breakout remains. As new bars appear, the line extends to the right until the last bar, until the pattern status changes from _Awaiting_ to another. The label tooltip shows the price and the current status of the pattern. When the status changes, the color of the label also changes. There are 4 statuses in total:

-   _Awaiting._ The rectangle is not broken or is broken and the price has not yet reached the target level in the direction of the breakdown and has not gone beyond the last opposite point of the rectangle.
-   _Reached._ The price broke through one of the horizontal lines of the rectangle and reached the target in the same direction.
-   _Failed._ The price broke through one of the lines of the rectangle and, having not reached the target, went beyond the last point opposite to the direction of the breakdown.
-   _Indefinable._ The indicator cannot unambiguously determine the status of the pattern.

If the indicator finds two intersecting patterns, then preference is given to the one whose status is _Awaiting_. If the status of the intersecting patterns is _Failed_ or _Reached_, or the status of both is _Awaiting_, then the pattern that is larger will be displayed on the chart. A pattern with the _Indefinable_ status is deleted if it intersects with a pattern that has a different status.

Alerts:

-   _New Pattern._ Triggered when a new pattern appears on the chart. The pattern is considered new if the position of the first point has changed.
-   __Pattern Breakout.__ It is triggered when a bar that has closed outside the rectangle appears. If there is a breakout of the same line on which the last point of the pattern is located, then in case of an unsuccessful attempt to rebuild point 4, this alert will trigger on reverse rebuilding if no more than 5 bars have appeared since the breakout.
-   _Pattern Failed._ Triggers when the pattern status changes to failed. Triggers only if the pattern is fully formed.
-   __Target Reached.__ Triggers when the price reaches the pattern target. Triggers only if the pattern is fully formed.

Inputs:

-   _Patterns_ \- Defines which pattern will be drawn depending on its status. Possible values: All, Awaiting and Reached_,_ Only Awaiting, Last Awaiting. If Last Awaiting is selected, only one pattern with the Awaiting status will be displayed, the first point of which is located to the right of all the others.
-   _Price Targets_ \- Defines which price targets will be drawn depending status of the pattern. Possible values: All, Only Awaiting, Awaiting and Reached, None.
-   _Permissible Deviation_ – The maximum allowable deviation of a point from its corresponding line. It is calculated as a percentage of the distance between the lines of the rectangle on the same bar where this point is located.  
    
-   _In Progress_ – Search for emerging patterns.