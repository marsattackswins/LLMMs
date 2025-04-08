#### Definition

Volume is the total amount of assets traded in a specific period of time. The 24-hour Volume indicator is used to measure the total volume of a symbol traded in the last 24 hours, expressed as in currency. It can be used to measure the market's interest in a particular symbol.

#### Calculation

To calculate the 24-hour volume, the indicator uses data from different timeframes; the timeframes chosen depend on the timeframe on the main chart:

<table><tbody><tr data-identifyelement="502"><td data-identifyelement="503"><p dir="ltr">Chart timeframe</p></td><td data-identifyelement="505" dir="ltr"><p dir="ltr">Timeframe used for the calculation</p></td></tr><tr data-identifyelement="502"><td data-identifyelement="503"><p dir="ltr">less than 1D</p></td><td data-identifyelement="505" dir="ltr"><p dir="ltr">1</p></td></tr><tr data-identifyelement="502"><td data-identifyelement="503"><p dir="ltr">1D - 1W</p></td><td data-identifyelement="505" dir="ltr"><p dir="ltr">5</p></td></tr><tr data-identifyelement="502"><td data-identifyelement="503"><p dir="ltr">greater than 1W</p></td><td data-identifyelement="505" dir="ltr"><p dir="ltr">60</p></td></tr></tbody></table>

The indicator calculates the sum of the volume for the last X bars of the lower timeframe, where X is the number of bars that opened in the last 24 hours. The indicator works with calendar hours regardless of the symbol session, so if there has been no past trades for 24 hours or more (e.g., on the first Monday bar on a symbol that is only traded on business days), 24-hour volume can be equal to the regular volume data.

The indicator always displays the 24-hour volume converted to the currency selected in the indicator's inputs. This means that, if the exchange presents its volume data in base currency (e.g., when for BTCUSD, the volume represents the number of BTC traded), the _24-hour Volume_ indicator converts the base volume into currency volume by multiplying the volume by the price on the chart. The 'Price Source' input can be used to select which specific chart value will be used for this conversion.

The volume can be additionally converted into a currency different from the one on the chart. This can be done by switching the 'Target Currency' input from Default to a different currency.

#### What to look for

The 24-hour volume is a metric used to track the total value of all cryptocurrency transactions within a 24-hour period. It can be used to measure the market's interest in a particular symbol and gauge its overall health. A high 24-hour volume means that there is high demand for the symbol and that it is healthy and viable. A low 24-hour volume may indicate that the symbol is not as popular as others.

#### Inputs

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43325082062/original/Zhtk8ZzBTbSwtDxcAIhUd0wTQ65rFZP2Gg.png?1652958952)

  

##### Price Source

Specifies the price source used to convert base volume into currency volume, if necessary.

##### Target Currency

Sets the currency that the 24-hour volume will be presented in. Available options: Default, USD, EUR, CAD, JPY, GBP, HKD, CNY, NZD, RUB.