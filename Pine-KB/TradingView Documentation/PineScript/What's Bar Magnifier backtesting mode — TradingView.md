[Premium account](https://www.tradingview.com/gopro/) holders can obtain more realistic order fills in their strategy backtests by using The Bar Magnifier option. This tool uses intrabar inspection to obtain deeper granularity on price movement within a bar, allowing for more precise order fills. When selected, Bar Magnifier mode replaces the [assumptions](https://www.tradingview.com/pine-script-docs/concepts/strategies/) the broker emulator must make on price movement with only OHLC values for historical bars.

The intrabar timeframe used with the Bar Magnifier dynamically adjusts with the chart’s timeframe. This table lists the intrabar timeframe used for progressively higher chart timeframes:

<table><colgroup></colgroup><tbody><tr><td><p dir="ltr">Chart timeframe, higher than or equals to (T &gt;=)</p></td><td><p dir="ltr">Intrabar timeframe used</p></td></tr><tr><td><p dir="ltr">1S</p></td><td><p dir="ltr">1S</p></td></tr><tr><td><p dir="ltr">30S</p></td><td><p dir="ltr">5S</p></td></tr><tr><td><p dir="ltr">1</p></td><td><p dir="ltr">10S</p></td></tr><tr><td><p dir="ltr">5</p></td><td><p dir="ltr">30S</p></td></tr><tr><td><p dir="ltr">10</p></td><td><p dir="ltr">1</p></td></tr><tr><td><p dir="ltr">15</p></td><td><p dir="ltr">2</p></td></tr><tr><td><p dir="ltr">30</p></td><td><p dir="ltr">5</p></td></tr><tr><td><p dir="ltr">60</p></td><td><p dir="ltr">10</p></td></tr><tr><td><p dir="ltr">240</p></td><td><p dir="ltr">30</p></td></tr><tr><td dir="ltr">1D</td><td dir="ltr">60</td></tr><tr><td dir="ltr">3D</td><td dir="ltr">240</td></tr><tr><td dir="ltr">W</td><td dir="ltr">D</td></tr></tbody></table>

Table 1. Intrabar timeframes used

Here’s an example of a strategy that uses a stop order without using the Bar Magnifier option:

//@version=5  
strategy("bar\_magnifier\_demo", overlay \= true, use\_bar\_magnifier \= false)  
  
if bar\_index  \== 10381  
    strategy.entry("Long", strategy.long, stop \= 157.0)  
    strategy.exit("Exit", stop \= 156.0)  

The broker emulator places a stop order on bar #10381 and fills an order with a price of 157.0 on the next bar as soon as the stop = 157.0 condition is met. The broker emulator estimates that inside the bar itself, the price goes from “open” to “low”, then to “high” (triggering the entry), then to “close”. After a few bars (11 days for the current timeframe), the condition for exiting the position with the stop price = 156.0 is triggered:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43326690338/original/XuukAw-5XEu76fNzo18Ckgf01c77hvg2Cg.png?1653467457)

When the Bar magnifier is enabled (parameter use\_bar\_magnifier = true), exit and entry prices are unchanged; however, the exit from the position occurs inside the same bar in which the entry happened:

//@version=5  
strategy("bar\_magnifier\_demo", overlay \= true, use\_bar\_magnifier \= true)  
  
if bar\_index  \== 10381  
    strategy.entry("Long", strategy.long, stop \= 157.0)  
    strategy.exit("Exit", stop \= 156.0)  

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43326690339/original/Hp_G1sSnFbhtEkgzQvMj8lOt5jSAWzzZmg.png?1653467458)

If we check the lower timeframe chart for the same symbol (a 60-minute chart, according to the intrabar timeframe table) and find the time range corresponding to bar 10382, we can see that on the hourly timeframe, after reaching 157.0 and triggering the entry, the price goes down below 156.0, satisfying the stop = 156.0 condition:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43326690335/original/ckREF_lfJcTbIcUhuuluXD50Tk8kq_uxnw.png?1653467457)

With Bar Magnifier on, the broker emulator gets access to price changes from lower timeframes during backtesting, making its behavior more similar to what would happen during forward testing the strategy for the same time period.

The Bar magnifier option can be switched by toggling corresponding input in strategy’s “Settings/Properties” window:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43326738096/original/3urMUSN3IFmoRBQZsX_riJd0AdLgnJu1eQ.png?1653475472)

Note that this option has a limitation: the strategy can request no more than 200,000 bars from the lower timeframe. This can be for symbols with a lot of historical data (where _Num of Bars on the Chart_ \* _Num of Lower Timeframe Bars per Chart Bar_ > 200000), first trades on the chart might not be affected by the bar magnifier. The number of bars, starting from the end of the chart, that can be affected by the Bar Magnifier can be roughly calculated as:

```
last_bar_index - (200000 / ( 1 / Num of Lower Timeframe Bars per Chart Bar)
```

The resulting value will be a rough approximation, because the number of lower timeframe bars can differ from one bar to another.