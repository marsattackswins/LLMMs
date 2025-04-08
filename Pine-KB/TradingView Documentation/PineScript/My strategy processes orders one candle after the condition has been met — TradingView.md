By default, a strategy is calculated once per bar, on the bar close. During that calculation, the strategy is able to generate new orders or update existing ones. But when the bar has already closed, it cannot be traded anymore, so the earliest moment that a strategy order can be filled is at the open of the next bar. Because of this, by default, the strategy will open a position one bar after the entry condition has been met.

That behavior can be changed with the _process\_orders\_on\_close_ argument. This allows the strategy to fill orders on the close of the bar. To do this, a _process\_orders\_on\_close_ argument should be added to the [_strategy()_](https://www.tradingview.com/pine-script-reference/v5/#fun_strategy) function declaration and set to true, like this:

//@version=5  
strategy(..., process\_orders\_on\_close\=true, ...)  

This is how strategy works without the _process\_orders\_on\_close_ argument:

//@version=5  
strategy("process\_orders\_on\_close example")  
strategy.entry("EN", strategy.long, when \= bar\_index \== 20650)  
strategy.close("EN", when \= bar\_index \== 20655)  

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43207126155/original/bVdxomHDMqjXiohPxobWbJy-WIGbq1HHIw.png?1616507070)

This is how strategy works with the _process\_orders\_on\_close_ argument:

//@version=4  
strategy("process\_orders\_on\_close example", process\_orders\_on\_close \= true)  
strategy.entry("EN", strategy.long, when \= bar\_index \== 20650)  
strategy.close("EN", when \= bar\_index \== 20655)  

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43207126552/original/_LsgDBUSqZm-srBCZGdtBpqEVnORjZ99KA.png?1616507140)

The entry _EN_ is tied to a condition that will be true at the bar 20650, but the actual entry occurs one bar after that, at bar 20651. The same happens with its close: the condition is true at bar 20655, but the entry is only closed on the next bar. By adding the _process\_orders\_on\_close_ argument and setting it to true, the strategy can now fill orders on the close of the bars, so the market order _EN_ now fills one bar sooner.