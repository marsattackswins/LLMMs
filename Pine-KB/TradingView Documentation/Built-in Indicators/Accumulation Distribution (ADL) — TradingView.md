#### Definition

Accumulation Distribution Indicator or ADL (Accumulation Distribution Line) is a volume based indicator which was essentially designed to measure underlying supply and demand. It accomplishes this by trying to determine whether traders are actually accumulating (buying) or distributing (selling). This is accomplished by plotting a running total of each period’s Money Flow Volume. ADL can reveal divergences between volume flow and actual price to primarily either affirm a current trend or to anticipate a future reversal.

#### History

The Accumulation Distribution Line was created by famed stock analyst Marc Chaikin. The ADL has become closely related to two of Chaikin’s other famous indicators; the Chaikin Oscillator and the Chaikin Money Flow indicator.

#### Calculation

```
Accumulation/Distribution = ((Close – Low) – (High – Close)) / (High – Low) * Period Volume 
```

In order to fully understand how the indicator actually works, it is necessary to break this formula down into individual parts.

1.   Find the Money Flow Multiplier. 
    
    ```
    ((Close - Low) - (High - Close))/(High - Low) = Money Flow Multiplier
    ```
    
2.  Once you have calculated the Money Flow Multiplier, you can calculate Money Flow Volume. 
    
    ```
    Money Flow Multiplier * Period’s Volume = Money Flow Volume
    ```
    
3.  As previously mentioned The ADL is a running total of each period’s Money Flow Volume. Therefore once you have the Current Money Flow Volume you can plot the ADL. 
    
    ```
    ADL = Previous ADL + Current Money Flow Volume
    ```
    

#### The basics

When breaking down the formula, what ultimately causes the ADL to rise or fall is the Money Flow Multiplier. The Money Flow Multiplier is determined by the relationship between a period’s closing price and the period’s high/low range. The Money Flow Multiplier is always within a range of 1 and -1. When a period closes in the upper half of the high/low range, the Money Flow Multiplier will rise closer to 1. On the other hand, when a period closes in the lower half of the high/low range, the Money Flow Multiplier will fall towards -1. The closer the multiplier is to 1, the higher the buying pressure. So when you combine a highly positive multiplier with strong volume the ADL will rise. When you combine a highly negative multiplier with strong volume, selling pressure will rise and the ADL will fall. Therefore ADL can be seen as a way of measuring the strength of buying and selling (accumulation and distribution) pressure. With this in mind, ADL becomes a valuable tool in both confirming trends as well as anticipating reversal.

#### What to look for

##### Trend Confirmation

This is actually the simplest benefit of using the ADL. During a strong uptrend or a strong downtrend, The ADL will actually move in the same direction as price confirming the current trend.

##### Divergence

Divergences play another huge role in analyzing the ADL. It is believed by many that volume precedes price so any instance in which volume and price are heading in opposite directions should surely be noted. ADL will help the trader identify these instances.

_Bullish ADL Divergence is when the ADL is trending upwards while price is trending down. ADL trending up shows an increase in buying pressure (Accumulation). Assuming volume does precede price, a reversal in price definitely seems possible._

_Bearish ADL Divergence is when the ADL is trending downwards while price is on the rise. In this instance, ADL is signaling an increase in selling pressure (Distribution), and price may soon take a downwards turn._

##### Unreliability

As with any indicator, it is important for whoever is employing the ADL to understand its shortfalls or weaknesses. ADL’s major shortfall is that the Money Flow Multiplier, which plays a major part in determining which direction the Accumulation/Distribution Line will move, does not take into account the change in price range between periods. This means that if there is any type of gap in price, it won’t be picked up by the ADL and therefore the line and price will become out of synch.

#### Summary

Overall, The Accumulation Distribution indicator is a fairly reliable indicator for calculating underlying factors on a security’s chart. This is not something that is easily done, so ADL can indeed be quite valuable. However, knowing the underlying buying and selling (accumulation and distribution) pressures is typically not enough on its own. That is why ADL is best used as a complementary indicator that is just one aspect of any trading program or strategy. Another reason why ADL should not necessarily be used as a stand-alone is the unreliability mentioned in the previous section. Sometimes ADL can become out of sync with price. It is typically best to have other tools in place in order to have a system of checks and balances.

##### Style

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43080413577/original/hX3d1ZSFyWVRuuzR_rBTmG0BMvWjC7jDtw.png?1572028585)

###### Accumulation/Distribution

Can toggle the visibility of the ADL as well as the visibility of a price line showing the actual current value of the ADL. Can also select the ADL's color, line thickness and visual type (Line is the default).

##### Properties

###### Last Value on Price Scale

Toggles the visibility of the Indicator Value on the vertical axis.

###### Arguments in Header

Toggles the visibility of the indicator's name and settings in the upper left hand corner of the chart.

###### Scaling

Scales the indicator to either the Right or to the Left.