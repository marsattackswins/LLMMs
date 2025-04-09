#### Definition

The Greedy Strategy opens an initial order if there is a gap between current open and the high or low of the previous bar. If open is greater than previous high, strategy goes long, if open is below the low of the previous bar, it opens a short position. After a position is opened, it will continue filling orders in the same direction as long as the color of the candle is consistent with the open position. If the current position is long, new long orders will be created for every consequent green candle and vice versa. This will proceed until the candle of a different color or until the limit of filled orders for a day is reached. 

The limit can be changed in the settings by editing the Max Intraday Filled Orders value. The Tp and Sl settings allow you to set the Stop Loss and Take Profit. The value represents the number of minticks above/below the position price where the TP and SL will be located.

#### Calculations

##### Pine Script

```
//@version=5
strategy("Greedy Strategy", pyramiding = 100, calc_on_order_fills=false, overlay=true)
tp = input(10)
sl = input(10)
maxidf = input(title="Max Intraday Filled Orders", defval=5)
strategy.risk.max_intraday_filled_orders(maxidf)
upGap = open > high[1]
dnGap = open < low[1]
dn = strategy.position_size < 0 and open > close
up = strategy.position_size > 0 and open < close
strategy.entry("GapUp", strategy.long, stop = high[1], when = upGap)
strategy.entry("Dn", strategy.short, stop = close,  when =  dn)
strategy.entry("GapDn", strategy.short, stop = low[1], when = dnGap)
strategy.entry("Up", strategy.long, stop = close,  when =  up)
strategy.cancel("GapUp", not upGap)
strategy.cancel("GapDn", not dnGap)
strategy.cancel("Up", not up)
strategy.cancel("Dn", not dn)
XQty = strategy.position_size < 0 ? -strategy.position_size : strategy.position_size
dir = strategy.position_size < 0 ? -1 : 1
lmP = strategy.position_avg_price + dir*tp*syminfo.mintick
slP = strategy.position_avg_price - dir*sl*syminfo.mintick
float nav = na
revCond = strategy.position_size > 0 ? dnGap : (strategy.position_size < 0 ? upGap : false),
strategy.order("TP", strategy.position_size < 0 ? strategy.long : strategy.short, XQty, lmP, nav, "TPSL",  strategy.oca.reduce, "TPSL", when=  not revCond and XQty > 0)
strategy.order("SL", strategy.position_size < 0 ? strategy.long : strategy.short, XQty, nav, slP, "TPSL",  strategy.oca.reduce, "TPSL", when= not revCond and XQty > 0)
strategy.cancel("TP", XQty == 0 or revCond)
strategy.cancel("SL", XQty == 0 or revCond)
//plot(strategy.equity, title="equity", color=color.red, linewidth=2, style=plot.style_areabr)
```

#### Summary

The Greedy Strategy was created to take advantage of gaps in either direction. It then accelerates into those gaps by playing momentum to the upside or downside. The strategy opens an initial order if there is a gap between the current open and the high or low of the previous bar. If open is greater than previous high, strategy goes long and if open is below the low of the previous bar, it opens a short position. After a position is opened, it will continue filling orders in the same direction as long as the color of the candle is consistent with the open position.