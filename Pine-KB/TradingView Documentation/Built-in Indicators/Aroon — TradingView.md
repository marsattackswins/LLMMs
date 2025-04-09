#### Definition

The [Aroon Indicator](https://www.tradingview.com/scripts/aroon/) (often referred to as Aroon Up Down) is a range bound, technical indicator that is actually a set of two separate measurements designed to measure how many periods have passed since price has recorded an n-period high or low low with “n” being a number of periods set at the trader’s discretion. For example a 14 Day Aroon-Up will take the number of days since price last recorded a 14 day high and then calculate a number between 0 and 100. A 14 Day Aroon-Down will do the same thing except is will calculate a number based of the number of days since a 14 day low. This number is intended to quantify the strength of a trend (if there is one). The closer the number is to 100, the stronger the trend. Aroon is not only good at identifying trends, it is also a useful tool for identifying periods of consolidation.

#### History

The Aroon Indicator was developed in 1995 by technical analyst and author Tushar Chande. The fact that he named the indicator “Aroon” which is Sanskrit for “Dawn’s Early Light” demonstrates his belief in his indicator’s trend discovery capabilities.

#### Calculation

The Calculation relies on a user-defined period. For this example we will use a 14 Day Aroon. 

```
Aroon-Up = ((14 - Days Since 14-day High)/14) x 100
Aroon-Down = ((14 - Days Since 14-day Low)/14) x 100
```

#### The basics

The Aroon Indicator is range bound, techncial indicator that produces numbers between 0 and 100. The technical analyst should focus on three areas on that scale.

1.  Close to or at 100 indicates a stronger trend.
2.  Close to or at 0 indicates a weaker trend.
3.  The area right around 50 is middle ground and the trend could go either way.

When Aroon-Up is above 50 and close to 100 and Aroon-Down is below 50, this is a good indication of a strengthening uptrend. Likewise when Aroon-Down is above 50 and close to 100 and Aroon-Up is below 50, a strengthening downtrend may be at hand.

#### What to look for

##### Trend Spotting

Aroon's major function is to identify new trends as they happen. There are three steps to identifying when a new trend could be forming.

1.  The Aroon-Up and the Aroon-Down cross each other.
2.  The Aroon Lines will continue in opposite directions with one going above 50 towards 100 and the other staying below 50.
3.  One of the Aroon Lines will then hit 100.

Based on those three steps, lets use a Bullish Trend as an example. In a Bullish Trend, The Aroon-Up and the Aroon-Down will cross. Then, the Aroon-Up will cross above 50 while the Aroon-Down crosses below 50. Finally the Aroon-Up will hit 100 signifying the emergence of a Bullish Trend.

##### Consolidation Periods

Another good function of the Aroon Indicator is its ability to identify periods of consolidation. This occurs when Both the Aroon-Up and the Aroon-Down have dropped below 50. This shows a period of sideways trading because neither the Bullish Trend nor Bearish Trend has any strength. This is especially true when both the Aroon-Up and the Aroon-Down are moving down in unison. When both drop in a parallel manner, a sideways trading range may be forming.

#### Summary

The Aroon Indicator (Aroon Up Down) is most definitely a very good indicator for identifying both trends as well as periods of consolidation. That being said, it is an indicator best used a complementary piece. Knowing the overall trend is an important part to any trading strategy. Using Aroon as a foundation and combining it with additional indicators which are used to generate signals is probably the most effective way to use Aroon.

#### Inputs

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43080412463/original/KVNklH1n9m-u7HUCT-QOCHJbf8Y9sABOAw.png?1572028228)

##### Length

The look back time period for the Aroon.

#### Style

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43080412492/original/rPY5iO2mnoeECQHxc7b8Imtts4Mmz2QC0A.png?1572028238)

##### Aroon Up

Can toggle the visibility of the Aroon Up as well as the visibility of a price line showing the actual current value of the Aroon Up. Can also select the Aroon Up's color, line thickness and visual type (Line is the default).

##### Aroon Down

Can toggle the visibility of the Aroon Down as well as the visibility of a price line showing the actual current value of the Aroon Down. Can also select the Aroon Down's color, line thickness and visual type (Line is the default).