This error means that the strategy placed more orders, or closed more trades, than the maximum number allowed.

To avoid this error, [convert your strategy](https://www.tradingview.com/support/solutions/43000530720-how-can-i-convert-scripts-to-a-newer-pine-version/) to Pine Script v6. In v6, all orders above the limit are trimmed: each new order appears in the List of Trades, and the oldest order above the order limit is removed.

Alternatively, you can limit the dates when a strategy places orders by checking for a time range in the order condition. The following example script establishes a time range for placing orders by checking whether the [time](https://www.tradingview.com/pine-script-reference/v5/#var_time) of the current bar is between two [timestamps](https://www.tradingview.com/pine-script-reference/v5/#fun_timestamp).

//@version=6  
strategy("My strategy", overlay \= true)  
  
enableFilter \= input(true,  "Enable Backtesting Range Filtering")  
fromDate     \= input.time(timestamp("20 Jul 2023 00:00 +0300"), "Start Date")  
toDate       \= input.time(timestamp("20 Jul 2099 00:00 +0300"), "End Date")  
  
tradeDateIsAllowed \= not enableFilter or (time \>= fromDate and time <= toDate)  
  
longCondition \=  ta.crossover(ta.sma(close, 14),  ta.sma(close, 28))  
shortCondition \= ta.crossunder(ta.sma(close, 14), ta.sma(close, 28))  
  
if longCondition and tradeDateIsAllowed  
    strategy.entry("Long", strategy.long)  
  
if shortCondition and tradeDateIsAllowed  
    strategy.entry("Short", strategy.short)