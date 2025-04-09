#### Each Pine strategy has a number of properties that determine its behavior: 

1.  Initial Capital
2.  Base Currency
3.  Order Size
4.  Pyramiding
5.  Commission
6.  Verify Price For Limit Orders
7.  Slippage
8.  Margin
9.  Recalculate
10.  Fill orders

 They are available in the strategy settings, in the Properties tab:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43440948202/original/A48Sj20JJTTUvZXQEiiMeKYTVEUCo74YwQ.png?1696585775)

Each of the parameters specified in the properties of the strategy can be changed by editing the arguments of the [strategy()](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy) function call in the corresponding Pine script:

_strategy(title, initial\_capital, currency, default\_qty\_value, default\_qty\_type, pyramiding, commission\_type, commission\_value, backtest\_fill\_limits\_assumption, slippage, process\_orders\_on\_close, margin\_long, margin\_short, calc\_on\_order\_fills, calc\_on\_every\_tick, _process\_orders\_on\_close_, _use\_bar\_magnifier_)_

Let's take a look at each input parameter in the Properties menu and its corresponding parameter in the Pine language:

1 - _Initial Capital_ (parameter: _initial\_capital_) represents the amount of funds initially available for the strategy to trade, in the currency defined in _Base Currency_. By default, this value is equal to 1,000,000. You may need to increase this value for trades to occur on certain symbols.

2 - _Base Currency_ (parameter: _currency_) specifies the currency used for calculations. Results appearing in the Strategy Tester tab (profit, loss, drawdown, etc) are expressed in this currency. Available choices are:

_Default, USD, EUR, AUD, GBP, NZD, CAD, CHF, HKD, JPY, NOK, SEK, SGD, TRY, ZAR_. If the _Default_ choice is selected, the strategy will use the default currency for this symbol and there is no currency conversion.

3 - _Order Size_ (parameters: _default\_qty\_value_, _default\_qty\_type_). This requires a value and a calculation mode. Note that the calculated values can be subject to constraints due to the minimum tradable quantities for the symbol:

-   _Contracts_ (argument: _strategy.fixed_) - the strategy will enter with the specified number of contracts/shares/lots.
-   _Amount in currency_ (argument: _strategy.cash_) - the strategy will enter the amount specified in base currency.
-   _Percentage of equity_ (argument: _strategy.percent\_of\_equity_) - position sizes will be calculated as a percentage of the available equity when the trade opens.

4 - _Pyramiding_ (parameter: _pyramiding_) specifies the maximum number of successive entries allowed in the same direction. When pyramiding is disabled, the strategy can only open one long or short position, even if entry conditions are met. Pyramiding only affects entries made using the strategy.entry() function. It has no effect on orders created using strategy.order().

5 - _Commission_ (parameters: _commission\_type_, _commission\_value_). It is the amount paid in trading fees for each trade. A value and calculation mode must be supplied. Note that commission is applied on both entries and exits, and that when a percentage is used, the calculated commission will vary with the value of the transaction:

-   _Percentage of the transacted value_ (argument: _strategy.commission.percent__)_ - imposes a commission on each order equal to the specified percentage.
-   _Currency per contract_ (argument: _strategy.commission.cash\_per\_contract_) - imposes a commission on each contract.
-   _Currency per order_ (argument: _strategy.commission.cash\_per\_order_) - imposes a commission on each order.

6 - _Verify Price For Limit Orders_ (parameter: _backtest\_fill\_limits\_assumption_) makes the conditions for entering a position using limit orders more strict. By default, this value is 0, i.e. limit orders are filled on historical data as soon as the price indicated in the order is reached. If the parameter is not zero, then limit orders can enter a position within the bar only if the market price has exceeded the level of the limit order by the specified number of ticks.

7 - _Slippage_ (parameter: _slippage_) specifies the value in ticks to be added to the fill price of market or stop orders. It can be used to account for the spread.

8 - _Margin for Long/Short positions (parameters: _margin\_long_, _margin\_short_)_ specifies the margin for each trade, i.e., the percent of the position that the trader must fund. For example, if the _Margin for long positions_ is set to 25%, the trader has to have enough funds to cover 25% of the open trade and can potentially spend up to 400% of their equity on every trade. If a trade has been opened and it starts losing money to the extent where the trader's funds are not enough to cover their portion of the trade, a Margin Call occurs and forcibly liquidates a part of the original position. You can learn more about this feature and how it's calculated in [this Help Center article](https://www.tradingview.com/chart/?solution=43000717375).

9 - _Recalculate_ options specify how often the strategy should be recalculated. By default, the strategy is recalculated at the close of each bar, but using the options below, it can also be recalculated:

-   _After Order is Filled_ (parameter: _calc\_on\_order\_fills_) - allows the strategy to perform an additional intra-bar order calculation immediately after an order fills. That extra calculation happens on both historical and realtime bars.
-   _On Every Tick_ (parameter: _calc\_on\_every\_tick_). By default, strategies only calculate on the close of realtime bars. This parameter allows the strategy to calculate on each update of realtime bars, like an indicator would. Note that tick data is lost when the chart is refreshed, so strategies using this option will [repaint](https://www.tradingview.com/chart/?solution=43000478429). This parameter does not affect the behavior of strategies on historical bars. Also note that strategies using this feature will not show realistic results on historical bars, as they contain no tick data.

10 - _Fill orders__:_

-   _Using bar magnifier_ (parameter: _use\_bar\_magnifier_) - directs the Broker Emulator to use more precise, lower timeframe prices during history backtesting in order to achieve more realistic results. Read more about this feature in [Help Center](https://www.tradingview.com/chart/?solution=43000669285).  
    
-   _On bar close_ (parameter: _process\_orders\_on\_close_). If true, the strategy generates an additional attempt to execute orders after a bar closes and strategy calculations are completed. If the orders are market orders, the broker emulator executes them before the next bar's open. If the orders are price-dependent, they will only be filled if the price conditions are met. This option is useful if you wish to execute orders at the same time that they are created: by default, the orders are created on the Close of the current bar and executed on the Open of the next one; with this setting turned on, they will be executed on the same Close that the order is created on. Note that entering the position on the same tick that the order is created can be misleading because that would not be possible to accomplish in real trading.
-   _Using standard OHLC (parameter: fill\_orders\_on\_standard\_ohlc)_ forces strategies running on [Heikin Ashi](https://www.tradingview.com/chart/?solution=43000619436) charts to fill orders using actual OHLC prices, for more realistic results. By default, strategy scripts fill orders using the chart's prices, regardless of chart type. For Heikin Ashi charts, this setting prevents the use of synthetic prices which may not align with reality. For example, this strategy we've applied to the daily NASDAQ:AAPL Heikin Ashi chart filled an order on 2023-09-25 at a synthetic price of 175.61 USD. However, after enabling the "Using standard OHLC" option, the same order filled at the standard chart price of 174.20 USD.
    
    ![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43464057585/original/gDgMVgavKi5w6cSDhker6qZwSq-nG_qGXA.png?1706608014)
    
    ![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43464057618/original/zld30QSTituf8vRB1LSZ1ELo_L1wbbA-2g.png?1706608028)