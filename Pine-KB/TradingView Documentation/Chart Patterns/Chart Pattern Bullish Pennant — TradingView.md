Please note that the information about expected price targets provided by Auto Chart Patterns isn't a recommendation for what you should personally do. Do not take this data as investment advice. It should only be used for education and research. As with any trade, always look first and then leap.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43398802412/original/mAXAXpgKzEsRH4p_RQ_Z2UtwKOkd1B0Gow.jpg?1679316017)

A bullish pennant is a technical analysis figure that implies the continuation of the main trend after the consolidation area. The main trend forms a flagpole, and the consolidation area is a triangle – a pennant. It is expected that after the price breaks the upper line of the pennant, its further growth will continue to approximately the height of the flagpole.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43398802561/original/-s_PA7fjwQXJ9Nv0ndAE-WRDME9lYoxiQQ.jpg?1679316048)

The indicator searches for patterns on the last 600 bars. The pattern consists of lines denoting price movements (_Price Line_) and lines forming a triangle – a pennant. The start and end points of each price line are in 5/5 pivots. A pivot point is a local extremum (minimum or maximum) to the left and right of which there are no price values that exceed this extremum. Thus, a point will be a 5/5 pivot high if there are no high values 5 bars to the left and 5 bars to the right of it that are higher than this value at this point. The breakout of the pattern is fixed by the close value. Crossing the pennant line with the close value in the interval between points 2 and 5 is not allowed. In the _In Progress_ mode, the indicator looks for not only formed, but also emerging patterns. The last two points of such a pattern may not be in pivots, and the last price line will be dotted.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43398802684/original/fpyiQWdwyjpPQY06TxUkzewDAh8XinwdRg.jpg?1679316075)

The dotted horizontal line that ends with the _Target_ label indicates the expected price level after the pattern is completed. As new bars appear, the line extends to the right until the last bar, until the pattern status changes from _Awaiting_ to another. The label tooltip shows the price and the current status of the pattern. When the status changes, the color of the label also changes. There are 4 statuses in total:

-   _Awaiting_. The price did not break through either the upper or lower line of the pennant, or it broke through the upper line, but at the same time did not reach the expected level and did not go below point 5.
-   _Reached_. The price broke the upper line of the pennant and reached the expected level.
-   _Failed_. The price broke through the upper line, did not reach the target level and fell below point 5, or the price broke through the lower line of the pennant without breaking through the upper line.
-   _Indefinable_. The indicator cannot unambiguously determine the status of the pattern.

If the indicator finds two intersecting patterns, then preference is given to the one whose status is _Awaiting_. If the statuses of the intersecting patterns are _Failed_ or _Reached_, or the status of both is _Awaiting_, then the pattern will be displayed on the chart, for which the distance from point 1 to point 5 is greater. A pattern with the _Indefinable_ status is deleted if it intersects with a pattern that has a different status.

Alerts:

-   __New Pattern.__ Triggered when a new pattern appears on the chart. A pattern is considered new if it has a different position of point 1, 2 or 4.
-   __Pattern Breakout.__ It is triggered when a bar that has closed outside the pennant appears. Only the breakout in the direction of the target is registered. A breakout in the opposite direction will not trigger an alert.
-   _Pattern Failed._ Triggers when the pattern status changes to failed. Triggers only if the pattern is fully formed.
-   __Target Reached.__ Triggers when the price reaches the pattern target. Triggers only if the pattern is fully formed.

Inputs:

-   _Patterns_ \- Defines which pattern will be drawn depending on its status. Possible values: All, Awaiting and Reached_,_ Only Awaiting, Last Awaiting. If Last Awaiting is selected, only one pattern with the Awaiting status will be displayed, the first point of which is located to the right of all the others.
-   _Price Targets_ \- Defines which price targets will be drawn depending status of the pattern. Possible values: All, Only Awaiting, Awaiting and Reached, None.
-   _In Progress_ – Search for emerging patterns.