<iframe src="https://www.youtube.com/embed/aG8UIRNzPJQ??si=_YghbKfWoCvpPM1R&amp;wmode=opaque" frameborder="0" allowfullscreen=""></iframe>  

BBTrend is an indicator developed by John Bollinger, the creator of Bollinger Bands. Designed to be used in conjunction with the regular Bollinger Bands, this indicator analyzes the strength and the direction of the trend based on two separate Bollinger Bands calculations, a long one and a short one.

The BBTrend indicator presents the resulting calculation as a histogram. When the BBTrend value is above zero, it indicates a bullish trend, whereas a reading below zero signifies a bearish trend. How far is the value removed from zero reflects the strength or momentum behind the trend.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43482727219/original/9toEo8UQcV8rHaEtxlCfC05USSAl2ugd1A.png?1714486919)

#### Calculation

The BBTrend is calculated based on the bands of two different Bollinger Bands instances, a short one and a long one. The formula is:

```
BBTrend = (math.abs(shortLower - longLower) - math.abs(shortUpper - longUpper)) / shortMiddle * 100
```

Where _shortLower_, _shortMiddle_, and _shortUpper_ are the components of the short Bollinger Bands, while _longLower_ and _longUpper_ are the bands from the long Bollinger Bands calculation. The length of both short and long Bollinger Bands can be changed in the indicator's Inputs.

The intensity of the color of each separate column in the histogram reflects the direction in which the BBTrend moves: a more intense green or red column indicates that the current value of BBTrend is moving away from 0, while a dimmer green or red shows that the BBTrend is trending towards 0, while still being above it (for green columns) or below it (for red ones).

#### Inputs

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43482727208/original/ZqA_l5ewKEsuTTvPUG5VCEKEGWMoxK_HvQ.png?1714486917)

#### Short BB Length

The length of the short Bollinger Bands calculation used while calculating the BBTrend.

#### Long BB Length

The length of the long Bollinger Bands calculation used while calculating the BBTrend.

#### StdDev

The Standard Deviation of both Bollinger Bands calculations used while calculating the BBTrend.