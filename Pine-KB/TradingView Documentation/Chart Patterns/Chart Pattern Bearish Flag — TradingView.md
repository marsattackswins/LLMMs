Please note that the information about expected price targets provided by Auto Chart Patterns isn't a recommendation for what you should personally do. Do not take this data as investment advice. It should only be used for education and research. As with any trade, always look first and then leap.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43398806553/original/KrInJYjt4mKSps-RiyZCiKha_0CyEuGG6Q.jpg?1679316811)

A bearish flag is a technical analysis figure that implies a continuation of the main trend after some correction. The main trend forms a flagpole, and the correction forms a parallel flag channel. The price in the channel should not rise above the middle of the flagpole. It is expected that after the price breaks the flag's parallel channel down, further price decline is expected to be approximately equal to the size of the flagpole.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43398806621/original/CReQrf5a271yDeyaEqipfHzp1RA9kymX_g.jpg?1679316829)

The indicator searches for patterns on the last 600 bars. The pattern consists of lines indicating price movements (_Price Line_) and lines of the parallel flag channel (_Flag_). The start and end points of each price line are in 5/5 pivots. A pivot point is a local extremum (minimum or maximum) to the left and right of which there are no price values that exceed this extremum. Thus, a point will be a 5/5 pivot high if there are no high values 5 bars to the left and 5 bars to the right of it that are higher than this value at this point. The breakout of the pattern is fixed by the close value. Crossing the flag line with the close value in the interval between points 2 and 5 is not allowed. In the _In Progress_ mode, the indicator looks for not only formed, but also emerging patterns. The last two points of such a pattern may not be in pivots, and the last price line will be dotted.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43398806732/original/_yHCdgJgK7csUnAOx6iOoKeN1epXonLkYg.jpg?1679316854)

The dotted horizontal line that ends with the _Target_ label indicates the expected price level after the pattern is completed. As new bars appear, the line extends to the right until the last bar, until the pattern status changes from _Awaiting_ to another. The label tooltip shows the price and the current status of the pattern. When the status changes, the color of the label also changes. There are 4 statuses in total:

-   _Awaiting._ The price did not reach the expected level, while there is no high value in the channel above the middle of the flagpole. If the price has broken through the lower line of the flag, then the condition must be met that after that it has not risen above the maximum of all the high flag channels.
-   _Reached._ The price broke the lower line of the flag and reached the expected level.
-   _Failed._ The price broke the lower line, did not reach the target level and rose above the maximum of all the highs of the channel, either the price broke the upper line, or a high appeared in the flag channel above the middle of the flagpole.
-   _Indefinable._ The indicator cannot unambiguously determine the status of the pattern.

If the indicator finds two intersecting patterns, then preference is given to the one whose status is _Awaiting_. If the statuses of the intersecting patterns are _Failed_ or _Reached_, or the status of both is _Awaiting_, then the chart will display the pattern in which points 3 and 5 are located closer to the lower line of the flag channel. A pattern with the _Indefinable_ status is deleted if it intersects with a pattern that has a different status.

Alerts:

-   _New Pattern._ Triggered when a new pattern appears on the chart. A pattern is considered new if it has a different position of point 1, 2 or 4.
-   __Pattern Breakout.__ It is triggered when a bar that has closed outside the flag appears. Only the breakout in the direction of the target is registered. A breakout in the opposite direction will not trigger an alert.
-   _Pattern Failed._ Triggers when the pattern status changes to failed. Triggers only if the pattern is fully formed.
-   __Target Reached.__ Triggers when the price reaches the pattern target. Triggers only if the pattern is fully formed.

Inputs:

-   _Patterns_ \- Defines which pattern will be drawn depending on its status. Possible values: All, Awaiting and Reached_,_ Only Awaiting, Last Awaiting. If Last Awaiting is selected, only one pattern with the Awaiting status will be displayed, the first point of which is located to the right of all the others.
-   _Price Targets_ \- Defines which price targets will be drawn depending status of the pattern. Possible values: All, Only Awaiting, Awaiting and Reached, None.
-   _Permissible Deviation_ – The maximum allowable deviation of points in the flag from the lines of the parallel channel. Calculated as a percentage of the channel height.
-   _In Progress_ – Search for emerging patterns.