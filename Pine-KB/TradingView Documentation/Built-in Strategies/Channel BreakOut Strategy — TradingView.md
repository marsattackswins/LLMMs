#### Definition

The Channel BreakOut Strategy creates a channel with its bands based on the highest and lowest values for the last X bars (X is the value of the 'Length' setting). The strategy enters long if the high of the current bar is higher than the upper channel band of the previous bar. It enters short if the low of the current bar is lower than the lower channel band of the previous bar.

#### Calculations

##### Pine Script 

```
//@version=5
strategy("ChannelBreakOutStrategy", overlay=true)
length = input.int(title="Length", minval=1, maxval=1000, defval=5)
upBound = ta.highest(high, length)
downBound = ta.lowest(low, length)
if (not na(close[length]))
strategy.entry("ChBrkLE", strategy.long, stop=upBound + syminfo.mintick, comment="ChBrkLE")
strategy.entry("ChBrkSE", strategy.short, stop=downBound - syminfo.mintick, comment="ChBrkSE")
//plot(strategy.equity, title="equity", color=color.red, linewidth=2, style=plot.style_areabr)
```

#### Summary

The Channel Breakout Strategy attempts to create a strategy just like its name says - trades based on whether a symbol breaks out from a channel or not. The channel is dependent on the length, which is chosen in the strategy settings. The strategy then enters long if the high of the current bar is higher than the upper channel band of the previous bar. It enters short if the low of the current bar is lower than the lower channel band of the previous bar.