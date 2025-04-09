Please note that the information about expected price targets provided by Auto Chart Patterns isn't a recommendation for what you should personally do. Do not take this data as investment advice. It should only be used for education and research. As with any trade, always look first and then leap.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43381153718/original/PKDxtBIajILJiA2hd4-fygoNcBXYWkeIew.png?1671734520)

Double bottom is a reversal pattern formed by two consecutive lows that are at the same level (a slight difference in values is allowed) and an intermediate high between them. It is expected that after the price again reaches the level of the first low and then turns around and goes above the intermediate high level, further price growth is expected to continue further by about the difference between the lows and the high.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43381153750/original/D5os7N4ESVWPkTwhzhmJWAwszik5PdwBQw.png?1671734532)

The indicator searches for patterns on the last 600 bars. The pattern consists of lines indicating price movements (_Price Line_) and neck lines (_Neck Line_). The neckline is a horizontal line drawn through the intermediate maximum. The start and end points of each price line, except for the last one (point 5), are located in 5/5 pivots. A pivot point is a local extremum (minimum or maximum) to the left and right of which there are no price values that exceed this extremum. Thus, a point will be a 5/5 pivot high if there are no high values 5 bars to the left and 5 bars to the right of it that are higher than this value at this point. Point 5 is located at the intersection of the last price line with the neck line. In the _In Progress_ mode, the indicator looks for not only formed, but also emerging patterns. The second bottom of such a pattern may not be in the pivot and the price lines forming it will be dotted.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43381153813/original/kKnEIyP-Jf4TMg1mUCANmXbzKWifv3eR-Q.png?1671734543)

The pattern is considered formed when, after the appearance of the second bottom, the price (close) rises above the neck line. The dotted horizontal line that ends with the label _Target_ indicates the expected price level after the pattern is formed. As new bars appear, the line extends to the right until the last bar, until the status of the pattern changes from _Awating_ to another. The label tooltip shows the price and the current status of the pattern. When the status changes, the color of the label also changes. There are 4 statuses in total:

-   _Awaiting_. The price did not reach the expected level and did not go below the second bottom.
-   _Reached_. The price reached the expected level.
-   _Failed_. The price did not reach the expected level and went below the second bottom.
-   _Indefinable_. The indicator cannot unambiguously determine the status of the patterns.

If the indicator finds two intersecting patterns, then preference is given to the one whose status is _Awaiting_. If the status of the intersecting patterns is _Failed_ or _Reached_ or the status of both is _Awaiting,_ then the pattern will be displayed on the chart, in which the price values of the bottoms are the most similar, i.e., more accurate. A pattern with the _Indefinable_ status is deleted if it intersects with a pattern that has a different status.

Alerts:

-   _New Pattern._ It is triggered when a new pattern appears on the chart. A pattern is considered new if it has a different position of the first bottom or intermediate maximum.
-   __Pattern Formed.__ It is triggered when, after the appearance of the second bottom, a bar appears that has closed above the neckline.
-   _Pattern Failed._ Triggers when the pattern status changes to failed. Triggers only if the pattern is fully formed.
-   __Target Reached.__ Triggers when the price reaches the pattern target. Triggers only if the pattern is fully formed.

Inputs:

-   _Patterns_ \- Defines which pattern will be drawn depending on its status. Possible values: All, Awaiting and Reached_,_ Only Awaiting, Last Awaiting. If Last Awaiting is selected, only one pattern with the Awaiting status will be displayed, the first point of which is located to the right of all the others.
-   _Price Targets_ \- Defines which price targets will be drawn depending status of the pattern. Possible values: All, Only Awaiting, Awaiting and Reached, None.
-   _Trend Height_ – Sets the required height of the trend preceding the pattern relative to the height of the pattern itself. The height of the pattern is considered to be the difference in the price of the minimum of the bottoms and the intermediate maximum. Percentage value.
-   _Second Bottom_ – Determines which patterns to display with respect to whether the second bottom of the first bottom is above _Higher_ or below _Lower_. If _Both_ is selected, all patterns will be displayed.
-   _Permissible Deviation_ – The maximum allowable difference in vertex depth. The depth of the low is calculated from the intermediate maximum. Percent value.
-   _In Progress_ – Search for patterns that have not been fully formed yet.