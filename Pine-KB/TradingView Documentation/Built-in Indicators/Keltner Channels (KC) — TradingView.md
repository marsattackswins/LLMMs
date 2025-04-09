#### Definition

The [Keltner Channels (KC) indicator](https://www.tradingview.com/scripts/keltnerchannels/) is a banded indicator similar to Bollinger Bands and Moving Average Envelopes. They consist of an Upper Envelope above a Middle Line as well as a Lower Envelope below the Middle Line. The Middle Line is a moving average of price over a user-defined time period. Either a simple moving average or an exponential moving average are typically used. The Upper and Lower Envelopes are set a (user-defined multiple) of a range away from the Middle Line. This can be a multiple of the daily high/low range, or more commonly a multiple of the Average True Range.

#### History

The basic idea behind the Keltner Channels indicator was introduced by Chester Keltner in his 1960 book _How to Make Money in Commodities_. Since then, his ideas have been expanded upon and simplified, most notably by Linda Bradford Raschke. Raschke popularized using an exponential moving average for the middle line and using Average True Range for the envelopes.

#### Calculation

For this example we will use a 20 Period EMA with Envelopes using Average True Range and a multiplier of 2:

```
Basis = 20 Period EMA
Upper Envelope = 20 Period EMA + (2 X ATR)
Lower Envelope = 20 Period EMA - (2 X ATR)
```

#### The basics

Much like any indicator that is based around a moving average, The Keltner Channels (KC) indicator is a lagging indicator. Moving averages inherently lag behind price and therefore so do any bands or envelopes that are calculated using a moving average. The main occurrences to look for when using Keltner Channels are breakthroughs above the Upper Envelope or below the Lower Envelope. A breakthrough above the Upper Envelope signifies overbought conditions. A breakthrough below the Lower Envelope signifies oversold conditions.

Keep in mind however when using Keltner Channels, that overbought and oversold conditions are oftentimes a sign of strength. During a clearly defined trend, overbought and oversold conditions can signify strength. In this case, the current trend would strengthen and ultimately continue. It works a little bit different in a sideways market. When the market is trending sideways, overbought and oversold readings are frequently followed by price moving back towards the moving average (Middle Line).

#### What to look for

##### Trend Confirmation

As previously mentioned, during a clearly defined trend, breakthrough above or below the envelopes can be a sign of underlying strength of the trend.

During a Bullish Trend, a breakthrough above the upper envelope can be seen as a sign of strength and the uptrend is likely to continue.

During a Bearish Trend, a breakthrough below the lower envelope can be seen as a sign of strength and the downtrend is likely to continue.

##### Overbought and Oversold

When a market is choppy or trading sideways, Keltner Channels can be useful for identifying overbought and oversold conditions. These conditions can typically lead to price corrections where price moves back towards the moving average (Middle Line).

#### Summary

In terms of trend identification and determining overbought and oversold levels, the Keltner Channels indicator does this effectively. It is one of a number of banded indicators that accomplishes this task, just in its own way. While Keltner Channels can be used independently, it is best to use them with additional technical analysis tools. Historical analysis may also be helpful when trying to determine the correct parameters when setting up the indicator. Different securities may require a different multiplier to adjust the width of the bands or envelopes.

#### Inputs

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43267796142/original/YBSy5ucStDCHAXmphxTyO6tD0x4y9QBxQg.png?1635767114)

##### Indicator Timeframe

Specifies the timeframe that the indicator is calculated on. This option allows calculating KC based on a data from another timeframe, e.g. having KC calculated on 1H chart be displayed on a 5m chart.

##### Length

The time period to be used in calculating the MA which creates the base for the Upper and Lower Envelopes (20 is the default).

##### Multiplier

The multiplier to be applied to the bands.

##### Source

Determines what data from each bar will be used in calculations. Close is the default.

##### Use Exponential MA

Determines if a simple or exponential moving average will be used for the basis.

##### Bands Style

Determines if high/low range or average true range will be used for the bands.

##### ATR Length

The time period to be used in calculating the Average True Range.

#### Style

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43267793571/original/E4zPAkEOAEAAOq4Bs6g2urtOLs2togSlxw.png?1635766567)

##### Upper

Can toggle the visibility of the Upper Band as well as the visibility of a price line showing the actual current value of the Upper Band. Can also select the Upper Band's color, line thickness and line style.

##### Basis

Can toggle the visibility of the Basis as well as the visibility of a price line showing the actual current value of the Basis. Can also select the Basis' color, line thickness and line style.

##### Lower

Can toggle the visibility of the Lower Band as well as the visibility of a price line showing the actual current value of the Lower Band. Can also select the Lower Band's color, line thickness and line style.

##### Background

Toggles the visibility of a Background color within the Bands. Can also change the Color itself as well as the opacity.