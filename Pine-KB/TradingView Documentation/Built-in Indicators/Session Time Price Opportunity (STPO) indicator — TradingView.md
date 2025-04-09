#### Definition

The Session Time Price Opportunity (STPO) indicator creates TPO profiles for each day based on the sessions specified in the settings, allowing traders to analyze price distributions over specific periods within each day.

Using multiple instances of the STPO indicator on a chart also allows traders to divide a trading day into several custom periods and independently inspect each period's TPO profile.

> _NOTE: This page describes features unique to the STPO indicator. To learn more about the general traits of all Time Price Opportunity indicators, see our Help Center's [Time Price Opportunity](https://www.tradingview.com/chart/?solution=43000713306) article._

#### Calculation

The calculation of the Session TPO indicator almost entirely matches the Periodic TPO's calculation, which you can learn more about by reading the article noted above.

The primary difference in STPO's calculation is the definition of periods. It calculates TPO profiles over each trading day within the sessions specified in the indicator's settings. The data each profile will contain depends on the indicator's "Sessions" and "Block Size" settings.

The "Block Size" input determines the timeframe of the data the indicator uses to construct the profiles. If the beginning of a specified session occurs after the start of a bar on the "Block Size" timeframe, the session's profile will not include that bar's data. Conversely, when the end of a session occurs after the start of a "Block Size" bar, the indicator will use all that bar's data when constructing the profile, even if it closes after the session ends.

For example, suppose the indicator uses a custom session from 8:00 to 12:30, and its block size is "4h". If the data on the 4-hour timeframe has a bar that starts at 12:00, the profile will include the entire bar's data, even though the session only covers the first 30 minutes (12:00 to 12:30).

#### Inputs

##### Sessions

This input determines the sessions that the STPO considers in its calculation. Enabling "Extended trading hours" in the chart's settings will impact the results for most session options.

-   _All:_ The "All" (default) option specifies that the indicator will consider the entire day's period, including pre-market and post-market sessions, as a single session in the calculation.
-   _Each:_ The "Each (pre-market, market, post-market)" option specifies that the indicator will construct up to three profiles for each trading day: one for pre-market hours, one for primary market hours, and one for post-market hours. Pre-market and post-market profiles will only show if the symbol has extended hours data and the chart displays that data.
-   _Pre-market, Market, or Post-market:_ The dedicated "Pre-market", "Market", and "Post-market" options allow the indicator to construct a single profile for each day over the specified session. The "Pre-market" and "Post-market" options only work for symbols with extended hours data when the chart has "Extended trading hours" enabled.
-   _Custom:_ With the "Custom" option, traders can configure the start and end of the daily period and its timezone, allowing one to inspect TPOs for specific time regions within each day.

See our Help Center's [Time Price Opportunity](https://www.tradingview.com/chart/?solution=43000713306) article to learn about the other inputs and style settings available for this indicator.