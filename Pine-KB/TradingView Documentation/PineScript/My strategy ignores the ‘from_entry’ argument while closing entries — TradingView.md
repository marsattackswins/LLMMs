The _strategy.exit()_ function allows you to exit a specific entry using the _from\_entry_ parameter.

If the strategy has more than one entry (_pyramiding_), the order in which the market positions are closed in the trade list of the strategy tester may be unclear. 

By default, the first exit order sent by a strategy closes the oldest entry order. Then the next exit order closes the next oldest entry, and so on. Essentially, the strategy closes trades based on the _first in, first out_  (_FIFO_) principle.

In the following example we try using the _from\_entry_ argument to connect _strategy.exit_ calls to specific entries:

//@version=5  
strategy("close\_entries\_rule\_example", overlay\=true, pyramiding \= 2)  
   
strategy.entry("EN2", strategy.short, when \= bar\_index \== last\_bar\_index \- 20)  
strategy.entry("EN1", strategy.short, when \= bar\_index \== last\_bar\_index \- 15)  
   
if bar\_index \== last\_bar\_index \- 10  
    strategy.exit(id \= "EX1", from\_entry \= "EN1", profit \= 1, loss \= 1)  
  
if bar\_index \== last\_bar\_index \- 5  
    strategy.exit(id \= "EX2", from\_entry \= "EN2", profit \= 1, loss \= 1)  

First, [strategy.entry](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy{dot}entry) opens a short position _EN2_, and _EN1_ enters five bars after that.

Once five bars pass, a corresponding [strategy.exit()](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy{dot}exit) function with _id = EX1_ is going to exit entry _EN1_, and _EX2_ should exit _EN2_ another five bars after that.

But the actual strategy tester results look like this:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43325971947/original/83JWZO9Mbav6nmVBGVxMF4PBEPwV4EtUZw.png?1653303921)

The first trade with the id _EN2_ is closed by the exit order _EX1_, and _EN1_ is closed by _EX2_, even though it was coded that _EN2_ should be closed by _EX2_. So the first exit order has closed the first entry order, and the second exit order has closed the second entry. That's classic _FIFO_ behavior.

To make it possible for the strategy to close orders in any sequence, the _close\_entries\_rule_ argument of the [_strategy()_](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy) function should be set to "_ANY_" (instead of the default “_FIFO_”), e.g: 

//@version=5  
strategy(..., close\_entries\_rule\="ANY", ...)  

With this "_ANY_" value the strategy can determine which exit order closes which specific position. (Note that "_FIFO_" is implicitly set as default even when _close\_entries\_rule_ argument is not specified).

With the _[strategy()](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy)_ call changed to

```
strategy("close_entries_rule_example", close_entries_rule="ANY",  overlay=true, pyramiding = 2)
```

the strategy tester results will be different:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43325973338/original/Je_C-WiwnD48sNOZqERzk49WFKGFVV5aAA.png?1653304140)

In this case, the (chronologically) first exit order _EX1_ closed the second entry _EN1_, and the second exit closed the first entry.