Please note that the information about expected price targets provided by Auto Chart Patterns isn't a recommendation for what you should personally do. Do not take this data as investment advice. It should only be used for education and research. As with any trade, always look first and then leap.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43381130948/original/eMXllBNMI7PtE-uhDQc-11LzptMLv2bsXQ.png?1671727508)

Triple Top is a reversal pattern formed by three consecutive highs that are at the same level (a slight difference in price values is allowed) and two intermediate lows between them. It is expected that after the price reaches the third high and then falls below the level of the intermediate low, then the fall will continue further by about the difference between the highs and lows.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43381131064/original/zDTzdfy9kb7WMlY6Rf20EydIp6IaZAqxFw.png?1671727533)

The indicator searches for patterns on the last 600 bars. The pattern consists of lines indicating price movements (_Price Line_) and neck lines (_Neck Line_). The neck line is drawn along the smallest of the intermediate lows. The start and end points of each price line, except for the last one (point 7), are located in 5/5 pivots. A pivot point is a local extremum (minimum or maximum) to the left and right of which there are no price values that exceed this extremum. Thus, a point will be a 5/5 pivot high if there are no high values 5 bars to the left and 5 bars to the right of it that are higher than this value at this point. Point 7 is located at the intersection of the last price line with the neck line. In the _In Progress_ mode, the indicator looks for not only formed, but also emerging patterns. The third peak of such a pattern may not be in the pivot, and the price lines that form it will be dotted.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43381131122/original/voZfON53u0p1kfcn8ggHzIK3FX5aUm25VQ.png?1671727545)

The pattern is considered formed when, after the appearance of the third peak, the price (close) falls below the neckline. The dotted horizontal line that ends with the _Target_ label indicates the expected price level after the pattern has formed. As new bars appear, the line extends to the right until the last bar, until the pattern status changes from _Awaiting_ to another. The label tooltip shows the price and the current status of the pattern. When the status changes, the color of the label also changes. There are 4 statuses in total:

-   _Awaiting_. The price did not reach the expected level and did not go above the last top.
-   _Reached_. The price reached the expected level.
-   _Failed_. The price did not reach the expected level and went above the last top.
-   _Indefinable._ The indicator cannot unambiguously determine the status of the patterns.

If the indicator finds two intersecting patterns, then preference is given to the one whose status is _Awaiting_. If the status of the intersecting patterns is _Failed_ or _Reached_ or the status of both is _Awaiting_, then the chart will display the pattern whose vertex prices values are most similar, i.e. more accurate. A pattern with the _Indefinable_ status is deleted if it intersects with a pattern that has a different status.

Alerts:

-   __New Pattern.__ It is triggered when a new pattern appears on the chart. A pattern is considered new if it has a different position of the first or second top or one of the intermediate minima.
-   __Pattern Formed.__ It is triggered when, after the appearance of the third top, a bar appears that has closed below the neckline.
-   _Pattern Failed._ Triggers when the pattern status changes to failed. Triggers only if the pattern is fully formed.
-   __Target Reached.__ Triggers when the price reaches the pattern target. Triggers only if the pattern is fully formed.

Inputs:

-   _Patterns_ \- Defines which pattern will be drawn depending on its status. Possible values: All, Awaiting and Reached_,_ Only Awaiting, Last Awaiting. If Last Awaiting is selected, only one pattern with the Awaiting status will be displayed, the first point of which is located to the right of all the others.
-   _Price Targets_ \- Defines which price targets will be drawn depending status of the pattern. Possible values: All, Only Awaiting, Awaiting and Reached, None.
-   _Trend Height_ – Sets the required height of the trend preceding the pattern relative to the height of the pattern itself. The height of the pattern is the difference in price between the maximum of the tops and the minimum of the intermediate lows. Percent value.
-   _In Progress_ – Search for patterns that have not been fully formed yet.
-   _Tops_ – The maximum allowable difference in tops heights. The height of the top is calculated from the minimum of the intermediate lows. Percent value.
-   _Intermediate Minima_ – The maximum allowable difference in the depth of intermediate minima. The depth of the minimum is measured from the highest of the peaks. Percent value.