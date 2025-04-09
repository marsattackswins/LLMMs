The MTF functionality is a feature that allows you to change any indicator’s timeframe with just two clicks in Inputs, using the _Timeframe_ dropdown.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43406478106/original/J59O0ypNKJNC0cPjfAScAJ2ZRJXd5HY-SA.png?1682512774)

Pine coders can use the same _timeframe_ parameter we use in our built-in indicators in their own scripts. By simply adding it to a script's _[indicator](https://www.tradingview.com/pine-script-reference/v5/#fun_indicator)_ declaration statement, coders now have an easy way to add MTF functionality to scripts and let users decide the timeframe they want the indicator to run on. 

Using the timeframe parameter will automatically add a _Timeframe_ input field to your script's Inputs. The parameter's default value can be any valid timeframe string. If, however, it is not included in the choices available from the field's dropdown menu, the default _Same as symbol_ will appear as the default value in the field. Use the empty string ("") to represent the chart's timeframe. 

Let’s say, for example, that you want to use a chart with a timeframe of 5m, but want it to show a Moving Average based on a timeframe of 1D. Previously, you could do this by using the _[request.security](https://www.tradingview.com/pine-script-reference/v5/#fun_request%7Bdot%7Dsecurity)_ function:

//@version=5  
indicator(title\="Moving Average", shorttitle\="MA with security", overlay\=true)  
len \= input.int(9, minval\=1, title\="Length")  
src \= input.source(close, title\="Source")  
out \= ta.sma(src, len)  
tf \= input.timeframe(title\="Timeframe", defval\="1D")  
s1 \= request.security(syminfo.tickerid, tf, out, gaps\=barmerge.gaps\_on)  
plot(s1, color\=color.red)  

  
Now, however, you’ll just need to add _timeframe="D"_ to your _indicator_ call:

//@version=5  
indicator(title\="Moving Average", shorttitle\="MA with timeframe", overlay\=true, timeframe\="D", timeframe\_gaps\=true)  
len \= input.int(9, minval\=1, title\="Length")  
src \= input.source(close, title\="Source")  
offset \= input.int(title\="Offset", defval\=0, minval\=\-500, maxval\=500)  
out \= ta.sma(src, len)  
plot(out, color\=color.blue, title\="MA", offset\=offset)  

The _timeframe_ parameter provides an easy way to add MTF functionality to relatively simple scripts. The addition of _timeframe\_gaps=true_ is optional and similar in principle to the \`gaps\` parameter in the \`request.security()\` function. More complex Pine scripts will still need _[request.security](https://www.tradingview.com/pine-script-reference/v5/#fun_request%7Bdot%7Dsecurity)_ to implement advanced calculations using higher timeframe information.

Note that the value of _timeframe.\*_ variables will represent the timeframe the script is currently running on as determined by the value of the _Timeframe_ field in the script's Inputs, regardless of the chart's timeframe. Also note that since higher time frame values contain gaps when the _timeframe_ parameter is used in a script (unless timeframe\_gaps is set to _false_), the _timeframe.\*_ variables will also contain _n/a_ values between time transitions. This behavior is expected. You can learn more about it in our [Help Center](https://www.tradingview.com/chart/?solution=43000586466).