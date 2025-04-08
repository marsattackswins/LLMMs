<iframe src="https://www.youtube.com/embed/XL5KiP2mBUQ??si=UiQNu_6pAGuw9S5b&amp;wmode=opaque" frameborder="0" allowfullscreen=""></iframe>  

The Volume Delta indicator uses intrabar volume and price fluctuations to estimate the difference (delta) between buying and selling pressure within each chart bar, providing insight into an instrument's sentiment and market dynamics. 

The indicator analyzes each chart bar from an intrabar timeframe (i.e., a timeframe lower than the chart's), categorizing each intrabar's volume as positive or negative. It gradually accumulates the polarized volume values throughout a chart bar to calculate the volume delta, and it keeps track of the highest and lowest volume delta values achieved over the bar's duration. 

After performing this analysis on a bar, the indicator plots a candle to represent the results:

-   The candle's open value is always 0.
-   The candle's close signifies the bar's final volume delta value.
-   The high reflects the highest volume delta calculated throughout the bar's duration.
-   The low reflects the lowest volume delta calculated throughout the bar's duration.  

#### Calculation

The Volume Delta indicator scans volume and price action across lower-timeframe bars within each chart bar to calculate volume delta values. To do this, it must first determine the intrabar timeframe to analyze. 

Users can decide the lower timeframe manually or let the indicator determine the timeframe. By default, it selects the timeframe automatically based on the chart's timeframe using the following rules:

<table><colgroup></colgroup><tbody><tr><td><p dir="ltr">Chart timeframe</p></td><td><p dir="ltr">Timeframe used for the calculation</p></td></tr><tr><td><p dir="ltr">Seconds</p></td><td><p dir="ltr">1S</p></td></tr><tr><td><p dir="ltr">Minutes or Hours</p></td><td><p dir="ltr">1</p></td></tr><tr><td><p dir="ltr">Daily</p></td><td><p dir="ltr">5</p></td></tr><tr><td><p dir="ltr">Others</p></td><td><p dir="ltr">60</p><br></td></tr></tbody></table>

When selecting an intrabar timeframe manually, it's important to note that lower timeframes provide higher precision at the cost of less chart bar coverage. Higher timeframes provide more historical data, but the volume delta values will be less precise. 

After timeframe selection, the indicator analyzes the direction of the available intrabars to categorize their volume and calculate the delta on each bar.

If the intrabar's opening price is not equal to the closing price:

-   It considers the intrabar's volume positive and adds the value to the chart bar's total if the closing price exceeds the opening price. 
-   It considers the intrabar's volume negative and subtracts it from the chart bar's total if the closing price is below the opening price.  

If the intrabar's opening and closing prices are equal:

-   It considers the intrabar's volume positive and adds the value to the chart bar's total if the closing price exceeds the close of the previous intrabar.
-   It considers the intrabar's volume negative and subtracts it from the chart bar's total if the closing price is below the previous intrabar's close.  
-   If the closing price equals that of the previous intrabar, the indicator assigns the previous intrabar's positive/negative status to the current intrabar. 

#### Inputs

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43476940584/original/8ZGOOHHspcTBLozitcxgF906tOdIE5iXLw.png?1712056667)

#### Use custom timeframe

Determines whether the user manually chooses the lower timeframe. If unchecked (default), the indicator selects the timeframe automatically. Otherwise, it uses the value specified in the "Timeframe" input below. 

#### Timeframe

Specifies the intrabar timeframe used for volume delta calculation when "Use custom timeframe" is enabled. Higher timeframes provide more historical data at the cost of reduced precision. Lower timeframes cover fewer chart bars but offer higher precision.