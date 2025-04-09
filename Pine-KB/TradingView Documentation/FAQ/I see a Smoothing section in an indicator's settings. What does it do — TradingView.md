Several of our built-in indicators such as [RSI](https://www.tradingview.com/support/solutions/43000502338-relative-strength-index-rsi/) have a "Smoothing" option that can add a moving average plot to the indicator. This feature draws a new line alongside the indicator's calculated output, displaying a smoothed (averaged) version of that same data. The "Smoothing" section is in the script's "Settings/Inputs" tab.

A moving average is a technical analysis tool that calculates a series of averages, each using a successive subset of the chart data, thereby creating a dynamic average line. Traders often use moving averages to smooth a chart's price fluctuations and help identify the general trend direction.

There are different types of moving averages, which vary in their calculations. For example, some use equal weighting for each data point, while others multiply each point by a weighting factor to give more weight to specific data (e.g., weighting the points based on recency, symmetry, or volume, linearly or exponentially). The length of the moving average, which is the number of data points used in calculating the average, also influences the final plot. All together, these variations affect how quickly a moving average responds to price changes and how significantly it moves. 

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43541996707/original/CeomZNLacHD1t28-JsxDBv8mRnZOX72GQw.png?1740044754)

The "Smoothing" section includes three settings: 'Type', 'Length', and 'BB StdDev'. 

The types of moving averages available for built-in indicators are: "[SMA](https://www.tradingview.com/support/solutions/43000696841/)", "SMA + Bollinger Bands", "[EMA](https://www.tradingview.com/support/solutions/43000592270/)", "[SMMA](https://www.tradingview.com/support/solutions/43000591343/) (RMA)", "[WMA](https://www.tradingview.com/support/solutions/43000594680/)", and "[VWMA](https://www.tradingview.com/support/solutions/43000592293/)". To learn more about moving averages and how to interpret their plots, see [this Help center article](https://www.tradingview.com/support/solutions/43000502589-moving-averages/). 

Alternatively, users can select "None" for the 'Type' setting to display the indicator without a moving average plot. Depending on the indicator, the default moving average type is either "SMA" or "None".

The "SMA + Bollinger Bands" option for the 'Type' setting displays the same moving average line as the "SMA" option and plots two additional [Bollinger Bands](https://www.tradingview.com/support/solutions/43000501840/) around the SMA line. 

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43527536219/original/xTdSEizJTIgwWq17ulfuW-RQYWB9O2nqRQ.png?1733321235)

The 'BB StdDev' setting is only applicable when the 'Type' input is set to "SMA + Bollinger Bands". It specifies the standard deviations of the upper and lower Bollinger Bands from the SMA line. By default, the bands are 2 standard deviations above and below the SMA line. 

The 'Length' setting determines the number of data points used in calculating the moving average. Its default value is 14. Using a smaller length creates a faster moving average that is more responsive to short-term price changes, while using a larger length creates a slower moving average that shows more long-term changes.