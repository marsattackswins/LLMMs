<iframe src="https://www.youtube.com/embed/Gb1tBvW2FHM??si=VWwQbs603SNWVy-Z&amp;wmode=opaque" frameborder="0" allowfullscreen="" data-identifyelement="463"></iframe>  

The Time Price Opportunity (TPO) chart type, also known as _Market Profile_, helps traders visualize price dynamics as the profile period develops and the concentration of prices at certain levels during a specific period. Traders use TPO to identify price levels with the most or most minor activity, giving them guidelines to determine future price movements.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43517099131/original/AopLbpPO-G5Jejbqq26ZM3KmmPaku077_A.png?1728995347)

TPO is based on a concept developed by J. Peter Steidlmayer in the 1980s. It has gained widespread acceptance in the futures and commodity markets and is now widely used across all sectors.

#### Main elements

The main element of the graph is the TPO profile. It is displayed on the left side.

#### Construction principles:

-   Each profile covers a period, which can be specified in days, weeks, or months.
-   Each letter represents one block of time within a profile, dividing the profile period into equal periods (5 minutes, 10 minutes, 15 minutes, 30 minutes, 1 hour, 2 hours, or 4 hours). The sequence of letters begins with uppercase \[A-Z\], followed by lowercase \[a-z\], and repeats as necessary.
-   A block of one letter appears at each price level where market activity occurred during the time segment corresponding to one letter. For example, all levels at which block "A" appears were visited during the first time segment of the profile period.
-   Each profile line represents the price range that covers the chart.

For more detailed information on how the TPO profile is calculated, read our article on the [TPO indicator](https://www.tradingview.com/support/solutions/43000713306-time-price-opportunity-tpo/).

On the right side of the TPO is the [volume profile](https://www.tradingview.com/support/solutions/43000502040-volume-profile-indicators-basic-concepts/) — it is calculated using data for the period specified in the _Block Size_ parameter.

Additionally, a price chart is displayed as a line.

#### Settings

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43517099210/original/Paw8rIid0aeIE84qO0haJO8NrdXaHHm_fA.png?1728995363)

Line

-   _Price source_ - allows you to select based on which values the line chart is built.
-   _Line_ - sets the color and thickness of the chart line.

Time Price Opportunity

-   _Periods_ - determines the duration of each profile, set by the number of days, weeks, or months. The default is one day.
-   _Block size_ - Defines the sub-period of time represented by each letter used to name the blocks. Smaller block size allows for more detail. Values: 5 minutes, 10 minutes, 15 minutes, 30 minutes, 1 hour, 2 or 4 hours, default is 30 minutes. Affects the calculation of TPO and Volume profiles.
-   _Row size_ - determines how many lines the profile will contain. Select the optimal value for the "Ticks per row" setting in automatic mode. The number of ticks you specified in the "Ticks per row" field is used manually.
-   _Ticks per row_ - this value is used only if the manual Row size setting mode is used.
-   _Value area_ - Sets the percentage of blocks used to calculate the cost zone. The default value is 70%.
-   _Gradient colors_ - These colors are used to display TPO blocks. The first two colors define the color range for the A-Z blocks; the last two colors are for blocks a-z.
-   _Blocks_ - controls the display of TPO-colored blocks. Disabling the settings will not work if the Letters setting is enabled, but they cannot be displayed due to the lack of space.
-   _Letters_ \- controls the display of TPO letters. If this feature is enabled, letters will only be displayed if there is enough space for them; otherwise, colored blocks will be displayed.
-   _Opacity outside the VA_ \- sets the transparency value outside the Value Zone.
-   _Split by blocks_ - distributes blocks into each time block throughout the entire profile period.

Lines and marks

-   _POC_ \- Toggles the visibility of the line and Point of Control mark for the TPO period.
-   _Poor high_ - Toggles the visibility of the line and the Weak High label for the TPO period.
-   _Poor low_ - toggles the visibility of the line and the Weak Low label for the TPO period.
-   _Single prints_ - Toggles the visibility of the single print line and label for the TPO period.
-   _VAH_ \- toggles the line's visibility and the Value Area High label for the TPO period.
-   _VAL_ \- toggles the line's visibility and the Value Area Low label for the TPO period.
-   _TPO Midpoint_ - Toggles the visibility of the average level label for the TPO period.
-   _Open Price_ - Toggles the visibility of the Open Price label for the TPO period.
-   _Closing Price_ - Toggles the visibility of the closing price label for the TPO period.
-   _Initial balance range_ - Displays the initial balance line as a vertical line to the left of the TPO profile and determines the number of blocks used to form the range.

Volume profile

-   _Show volume profile_ - toggles the visibility of the volume profile to the right of the TPO profile.
-   _Values_ - Toggles the visibility of volume values if there is enough space for them.
-   _VAH_ \- switches the visibility of the Value Area High line for the volume profile.
-   _VAL_ \- switches the visibility of the Value Area Low line for the volume profile.
-   _POC_ \- toggles the visibility of the Point of Control line for the volume profile.
-   _Volume_ \- determines the color of levels outside the Value Zone.
-   _Value area_ - determines the color of the levels inside the cost zone.
-   _Placement_ \- determines whether the volume profile is aligned left or right.

#### Splitting and merging profiles

You can split or merge individual profiles: this is especially useful when you need to look at specific areas of the graph at different levels of detail. To use this feature, right-click on the profile blocks and select the appropriate action from the context menu. 

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43517099424/original/AMo5qED5m-U4C8YnNp7jwWJv1ILuj58jjQ.png?1728995402)