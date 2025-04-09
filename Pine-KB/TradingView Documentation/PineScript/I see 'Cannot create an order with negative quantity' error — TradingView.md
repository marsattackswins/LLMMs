This error appears if the strategy equity becomes negative and the total number of contracts calculated for the [strategy.entry()](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy%7Bdot%7Dentry) or [strategy.order()](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy%7Bdot%7Dorder) functions is a negative integer value (qty <0). It can be avoided by tweaking the strategy settings from the Properties menu or by directly changing the logic of the strategy.

#### Source of the error

Let’s take a look at the script where the order quantity is calculated as a percentage of equity, either through the Order Size setting in the strategy settings, or via the [strategy\_percent\_of\_equity](https://www.tradingview.com/pine-script-reference/v5/#var_strategy%7Bdot%7Dpercent_of_equity) constant in the Pine source of the strategy. On each bar, the _[strategy.entry()](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy%7Bdot%7Dentry)_ function is called to enter the position:

//@version=5  
strategy("negative\_qty", default\_qty\_type \= strategy.percent\_of\_equity)  
  
strategy.entry("Short", strategy.short)  
plot(strategy.equity)  

When adding the script to a _NASDAQ:AAPL_ chart for _1D_ timeframe, the script crashes with a runtime error:

```
Cannot create an order with negative quantity. Current qty_type is percent_of_equity and equity is less than 0
```

To understand the reason for this error, you should plot the capital using the _[strategy.equity](https://www.tradingview.com/pine-script-reference/v5/#var_strategy%7Bdot%7Dequity)_ variable and add a constraint on the call to the [_strategy.equity()_](https://www.tradingview.com/pine-script-reference/v5/#var_strategy%7Bdot%7Dequity) function using any condition operator. That way, the function for entering a position will not be called on each bar (and will not cause additional recalculation of parameters, including the _qty_ value) and the script will be calculated successfully:

//@version=5  
strategy("negative\_qty", default\_qty\_type \= strategy.percent\_of\_equity)  
  
if strategy.equity \> 0   
    strategy.entry("Short", strategy.short)  
  
hline(0, "zero line", color \= color.black, linestyle \= hline.style\_dashed)   
plot(strategy.equity, color \= color.black, linewidth \= 3)  

At the opening of the second bar ([_bar\_index_](https://www.tradingview.com/pine-script-reference/v5/#var_bar_index) _= 1_), the strategy enters a short position. But with the growth of the AAPL value, the profit (the value of the _[strategy.openprofit](https://www.tradingview.com/pine-script-reference/v5/#var_strategy{dot}openprofit)_ variable) from the open short position _Short_ plummets, and in the end the capital of the strategy (__[strategy.equity](https://www.tradingview.com/pine-script-reference/v5/#var_strategy%7Bdot%7Dequity)_ = __[strategy.initial\_capital](https://www.tradingview.com/pine-script-reference/v5/#var_strategy{dot}initial_capital)__ + ___[strategy.netprofit](https://www.tradingview.com/pine-script-reference/v5/#var_strategy{dot}netprofit)___ +_ ____[strategy.openprofit](https://www.tradingview.com/pine-script-reference/v5/#var_strategy{dot}openprofit)____) becomes negative.

The number of contracts calculated by the strategy engine is calculated as _qty = (order size \* equity / 100) / close_. The area where the strategy capital turns into negative values can be displayed as follows:

//@version=5  
strategy("negative\_qty", default\_qty\_type \= strategy.percent\_of\_equity)  
  
if strategy.equity \> 0   
    strategy.entry("Short", strategy.short)  
  
hline(0, "zero line", color \= color.black, linestyle \= hline.style\_dashed)   
plot(strategy.equity, color \= color.black, linewidth \= 3)   
  
equity\_p \= 1  // percents of equity  order size value (1% is default)  
qty \= (equity\_p \* strategy.equity / 100) / close   
  
if qty <= \-1   
    var l1  \= label.new(bar\_index, strategy.equity, text \= "Negative qty\_value at \\n bar index: " + str.tostring(bar\_index) + ".\\n" +  "Order size: " + str.tostring(math.round(qty)), color \= color.white)   
    var l2 \= label.new(bar\_index \- 1, strategy.equity\[1\], text \= "Order size : " + str.tostring(math.round(qty\[1\])), color \= color.white)  
    var l3 \= label.new(bar\_index \- 2, strategy.equity\[2\], text \= "Order size: " + str.tostring(math.round(qty\[2\])), color \= color.white)  
  
bgcolor(qty \> \-1 ? color.green : color.red)  

The screenshot shows the label located on the negative equity section, where the resulting number of contracts is - 2. The number of contracts on the green section is >= 0:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43280114573/original/kc7qeFUdYT6kUcxv8Y6IGRCsuN9TTRoWWQ.png?1639464661)

If, when calculating a strategy, __[strategy.entry()](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy%7Bdot%7Dentry)__ is called on a bar with negative equity (and on which the number of contracts is negative), the calculation of the strategy stops with an error.

#### How do I fix this?

As a rule, this error does not appear in a correctly implemented strategy. To avoid mistakes, the strategy should use conditions for entering and exiting a position, stops, and margin.

If an error occurs, the correct methods for debugging the strategy are:

1\. Using margin leverage (Margin For Long/Short positions in the [Properties](https://www.tradingview.com/chart/?solution=43000628599) of the strategy or _margin\_long_ and _margin\_short_ parameters in the [strategy()](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy) function). If specified, a part of a position will be automatically liquidated if the strategy does not have enough equity to maintain it. You can find out more about this functionality in the article in our [User Manual](https://www.tradingview.com/pine-script-docs/concepts/strategies/) or in a [blog post](https://www.tradingview.com/blog/en/strategy-leverage-24638/).

//@version=5  
strategy("", default\_qty\_type \= strategy.percent\_of\_equity, default\_qty\_value \= 10, margin\_long \= 100, margin\_short \= 100)  
  
longCondition \= ta.crossover(ta.sma(close, 14), ta.sma(close, 28))  
if (longCondition)  
    strategy.entry("Long", strategy.long)  
  
shortCondition \= ta.crossunder(ta.sma(close, 14), ta.sma(close, 28))  
if (shortCondition)  
    strategy.entry("Short", strategy.short)  

2\. Checking the equity value to see if it’s above zero before calling __[strategy.entry()](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy%7Bdot%7Dentry)__ or _[strategy.order()](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy%7Bdot%7Dorder)_ functions or additionally redefining the number of entry contracts.

//@version=5  
strategy("", default\_qty\_type \= strategy.percent\_of\_equity, default\_qty\_value \= 10)  
  
if strategy.equity \> 0   
    strategy.entry("Short", strategy.short)  // enter at 10 % of currently available equity  
else   
    strategy.entry("Long", strategy.long, qty \= 1) // Reverse position with fixed contract size  

  
3\. Using variables of the _strategy.risk_ category for risk management. You can read more about these in our [User Manual](https://www.tradingview.com/pine-script-docs/concepts/strategies/).