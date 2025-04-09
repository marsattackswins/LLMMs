If the "List of Trades" and "Overview" tabs of the Strategy Tester display "No data" after you've added a strategy to the chart, it's likely that it doesn't simulate any orders, which results in no data to populate the tabs. If your script is not generating orders, it may be due to any of the following reasons:

#### The script is not classified as a strategy or does not use commands that create orders

Backtesting with the Strategy Tester only works with Pine Script™ strategies, which use the \`[strategy()](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy)\` function for their declaration statement. Scripts declared with \`[indicator()](https://www.tradingview.com/pine-script-reference/v5/#fun_indicator)\` or \`[library()](https://www.tradingview.com/pine-script-reference/v5/#fun_library)\` cannot interact with the Strategy Tester module.

Scripts declared as strategies must use \`strategy.\*\` order placement commands (e.g., \`[strategy.order()](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy%7Bdot%7Dorder)\` or \`[strategy.entry()](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy%7Bdot%7Dentry)\`) to simulate orders and display data in the Strategy Tester, regardless of any other buy/sell signals that a script's author may have included in the code.

#### The strategy does not have enough capital to open a position

For a strategy to enter a position, it must have enough money to purchase the specified number of contracts/lots/shares/units. It will not enter a trade if it does not have sufficient capital to cover the cost. For example, if a strategy's initial capital is 1000 USD and the order size is one contract, it cannot enter the position unless the asset's price falls below 1000 USD since it can't afford the entire trade. Strategies will always try to purchase the specified number of contracts/shares/lots/units and nothing less.

Important note on backtesting futures: 

Futures symbols commonly have what's known as a Contract Unit (represented as the Point Value on TradingView and accessible in Pine via the \`[syminfo.pointvalue](https://www.tradingview.com/pine-script-reference/v5/#var_syminfo%7Bdot%7Dpointvalue)\` variable). Like other symbols, the raw price on the chart represents the price of one unit of the traded commodity. However, futures contracts have a set quantity that each represents, so a single-unit purchase is not typically possible. To calculate the capital required for a contract, multiply the chart price by the Point Value.

To demonstrate the effects of Point Value on strategies that operate on futures symbols, let's look at the symbol CME\_MINI:ES1!, which represents the ES futures contract with the best liquidity and has a Point Value of 50:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43398081923/original/it05WOZW6FsefVDpJanJRE2X4dz1_lo2aw.png?1678951909)

In the example below, the strategy we've added to the chart entered a position at precisely 4000 USD and exited at 4500 USD. The actual amount of money spent on the contract at the entry price was 4000 USD times the Point Value of 50, which is 200,000 USD. When the strategy closed its position at the exit price, the amount received was 4500 USD \* 50 = 225,000 USD, resulting in a profit of 25,000 USD, which we can confirm by viewing the "Profit" column of the "List of Trades" tab in the Strategy Tester:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43398081922/original/8ZTqwM8AAUc0bmIeLwlO97bIxaujc5y_hg.png?1678951909)

If the strategy had an Initial Capital value under 200,000 USD in this case, it wouldn't have been able to place the order since it could not afford the entry price, which was 50 times the price shown on the chart. To simulate the position, we must increase the Initial Capital or lower the Margin Long/Short values to allow the strategy to afford it.

#### The strategy returns a runtime error

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43398081921/original/Y6i8OjIj3di31BJ6dXyK0zOHuX1RReGEnA.png?1678951908)

If a strategy encounters an issue during its calculations, it will raise a runtime error and display a red exclamation mark in the top-left corner of the chart pane that contains the strategy. Runtime errors stop the script from continuing calculations, so it cannot simulate orders. The different runtime errors in Pine have various causes and potential fixes. Clicking on the exclamation mark will show the script's error message.

#### The conditions required for placing the strategy's orders were not satisfied

One possible cause for a strategy not showing any data is that no condition triggered an order throughout the testing range. In this case, there would be no entries on the chart because there were no orders to fill. Users can fix this by changing the conditions in a strategy's source code. It can often be helpful to visually inspect the history of a strategy's order conditions by plotting them on the chart.

The script below uses Pine's \`[plotshape()](https://www.tradingview.com/pine-script-reference/v5/#fun_plotshape)\` function to plot blue and red crosses above bars upon the occurrence of the long and short conditions, allowing us to inspect their history on the chart:

//@version=5  
strategy('My Strategy', overlay \= true)  
  
longCondition \= ta.crossover(ta.sma(close, 14), ta.sma(close, 28))  
  
if longCondition  
    strategy.entry('Long', strategy.long)  
  
plotshape(longCondition, color\=color.new(color.blue, 0))  
  
shortCondition \= ta.crossunder(ta.sma(close, 14), ta.sma(close, 28))  
  
if shortCondition  
    strategy.entry('Short', strategy.short)  
  
plotshape(shortCondition, color\=color.new(color.red, 0))  

For additional information on this topic, see our [User Manual's page on Debugging](https://www.tradingview.com/pine-script-docs/writing/debugging/).

#### The strategy's Properties are incorrect

Every strategy has several parameters that govern its rules for opening orders. Authors can set these parameters from a strategy's source code, and users can override them with the inputs in the "Properties" tab of the strategy's settings.

NOTE: There are several places in a strategy's source code where users can set the number of contracts/shares/lots/units for its orders:

-   Parameters in the \`[strategy()](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy)\` function allow users to set the default trade quantity and type, which sets the default values in the "Properties" tab. Users can override these values by adjusting the "Order size" inputs.
-   Order placement commands that produce entry orders, such as \`[strategy.entry()](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy%7Bdot%7Dentry)\`, can set the trade quantity on an order-by-order basis. In this case, changes to the input in the "Properties" tab will not affect the strategy's order size. 

Users must ensure they specify the sizes of their strategies' orders correctly. To add to the "The strategy does not have enough capital to open a position" section above, you should note that:

-   If a strategy's "Order type" is set to "Contracts" (equivalent to \`[strategy.fixed](https://www.tradingview.com/pine-script-reference/v5/#var_strategy%7Bdot%7Dfixed)\` as the default\_qty\_type in the source code), the order size must be greater than 1 for most symbols. Some cryptocurrencies facilitate fractional sizes. For example, an order size of 0.1 is valid for BTCUSD but not for AAPL or EURUSD.
-   The order size must be positive; negative numbers will cause runtime errors, and a value of 0 will have no effect.
-   The total position size (number of contracts) cannot exceed 1e12. Strategies will not simulate new orders if the position size exceeds this number.