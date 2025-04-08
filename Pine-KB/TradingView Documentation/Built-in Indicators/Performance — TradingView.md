The Performance indicator shows the percentage change in prices of one or more symbols at set times. The prices display in a table under the chart. The list of symbols and the list of timeframes are defined by inputs.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43510002386/original/CCh6XnwmRfAgWTqiYnuYWXVjC_E67frfvw.png?1726041260)

#### Calculation

The indicator calculates the changes for each symbol in the order in which they are specified. For each timeframe, the indicator selects an anchor bar that is removed from the last bar on the chart by a specified timeframe. For example, if the chart's last bar is May 15, 2024, its 3M anchor is Feb 15, 2024, and its 1Y anchor is May 15, 2023. If there is no bar at the anchor time, the very next bar is used as the anchor.

The indicator calculates the performance value using the following formula:

_(Current value - Past value) / Past value \* 100_

Where:

_Current value_ is the most recent close on the chart, historical or realtime.

_Past value_ is the close of the bar preceding the anchor bar.

For example, if today is May 15, 2024, the timeframe of 1M uses the bar of April 15, 2024 as its anchor and the close of the preceding bar – April 14, 2024 – as the Past Value for the performance calculation. If the current realtime closing price is 215.00 and the closing price on April 14 is 193.00, the resulting performance value is (215 - 193) / 193 \* 100 = 11.40%, indicating that the price has increased by eleven percent in the period of one month.

The logic that the indicator uses to find anchors differs depending on the type of the anchor:

-   For day-based and week-based timeframes, an anchor bar is calculated by subtracting the specified number of 24-hour periods or 7-day periods, respectively, from the last candle's open.
-   For monthly timeframes, the indicator subtracts the months but selects the same day. For example, if today is April 15, 2024, 3M before that will be Jan 15, 2024, and 6M offset is Oct 15, 2023. 
-   For each yearly-based timeframe, the past bar is the bar with the same day and month of its respective year. For example, if the last bar on the chart is July 14, 2024, the 2Y timeframe selects July 14, 2022.
-   For “year to date” (YTD), January 1st of the current year is used as the anchor.

To see the anchor date for a specific symbol and timeframe combination, hover over a percentage value in the Performance table where the two intersect.

Note: The script defines the anchors once, when the script is loaded. The anchors do not change after that unless the page is reloaded, the symbol is changed, or the indicator's settings are changed. This means that over time, the anchor becomes out of sync with the timeframe input. For example, if the script is loaded on Sept 1, with a timeframe of 1M, after two days the current (updated) close as of Sept 3 is still being compared to the close from Aug 1, but that date is now 1M + 2 days ago.

#### Inputs

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43510002136/original/9yTMvdMalr9Bzvj2h0KyZn2heU67fE9PDQ.png?1726041224)

  

#### Include Chart Symbol

When this option is selected, the indicator adds the current symbol to the top of the symbols table if it's not already included in the Symbol List input.

#### Symbol List

A list of symbols or ticker IDs, separated by commas, with optional spaces. A ticker ID can specify an exchange prefix (e.g. "NASDAQ:AAPL") or just the ticker ("AAPL"), in which case the most popular exchange for this symbol is selected automatically.

#### Timeframe List

A list of timeframes, separated by commas, with optional spaces. A valid timeframe consists of a number followed by D, W, M, or Y, e.g., "7D", "1W", "3M", "5Y". Additionally, "YTD" – which stands for "year to date" – is supported.

#### 

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43510002245/original/xu7mVlEUGiJJ0c-eC7XqyhChWY9mjxW6Iw.png?1726041242)

#### Positive Color

The color of table cells that contain positive values. 

#### Negative Color

The color of table cells that contain negative values.

#### Color Intensity Cutoff

Specifies the maximum absolute percentage for the color intensity calculation. Absolute values at or above this level will have the highest intensity (opacity) in the heatmap display. For example, a cutoff value of 10% means colors become more opaque as the corresponding values approach 10%, but all values above 10% will share the same opacity. 

#### Table Position

Specifies the position of the Heatmap table relative to the pane where it is drawn. By default the position is set to "Center" and the Heatmap is anchored to the center of its pane. Changing this setting to "Left" or "Right" anchors the table to the left or the right corner of the pane, respectively.

#### Table Width (%)

The table width as a percentage of the pane where the table is located. The default value is 100, which means that the table is as wide as the pane. If this value is 0, the width fits the contents of the table, and the table can be wider than the pane.

#### Table Height (%)

The table height as a percentage of the pane where the table is located. The default value is 95, which means that the table is slightly shorter than the height of the pane. If this value is 0, the height fits the contents of the table, and the table can be taller than the pane.