#### Definition

[Moving Average (MA)](https://www.tradingview.com/scripts/movingaverage/) is a price based, lagging (or reactive) indicator that displays the average price of a security over a set period of time. A Moving Average is a good way to gauge momentum as well as to confirm trends, and define areas of support and resistance. Essentially, Moving Averages smooth out the “noise” when trying to interpret charts. Noise is made up of fluctuations of both price and volume. Because a Moving Average is a lagging indicator and reacts to events that have already happened, it is not used as a predictive indicator but rather an interpretive one, used for confirmations and analysis.

Simple Moving Average is an unweighted Moving Average. This means that each day in the data set has equal importance and is weighted equally. As each new day ends, the oldest data point is dropped and the newest one is added to the beginning.

It must be taken into account that, while SMA helps filter out the noise and see the general direction in which the symbol has been moving, it is also slow to react to newer changes. The higher the SMA length is, the longer it will take for a major price change to be notably reflected in it.

#### CALCULATION

A Simple Moving Average with the length of X is a sum of last X values divided by X. Here is an example calculation of an SMA with the length of 3:

```
Sum of Period Values / Number of PeriodsClosing Prices to be used: 5, 6, 7, 8, 9First Day of 3 Period SMA: (5 + 6 + 7) / 3 = 6Second Day of 3 Period SMA: (6 + 7 + 8) / 3 = 7Third Day of 3 Period SMA: (7 + 8 + 9) /3 = 8
```

#### Inputs

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43396051190/original/QJdRCRMuDfk2zDZQjuCtQzD3gsKkFUXBbw.png?1678187257)

##### Timeframe

Specifies the timeframe that the indicator is calculated on. This option allows calculating SMA based on a data from another timeframe, e.g. having SMA calculated on 1H chart be displayed on a 5m chart.

##### Length

The time period to be used in calculating the Simple Moving Average. 9 days is the default.

##### Source

Determines what data from each bar will be used in calculations. Close is the default.

##### Offset

Changing this number will move the Simple Moving Average either Forwards or Backwards relative to the current market. 0 is the default.

##### Smoothing

An additional Moving Average to be calculated based on the data from the main SMA. The type and length of that additional Moving Average can be selected in the Method and Length inputs, respectively. To see the additional Moving Average on the chart, it should be enabled in the Style section first.