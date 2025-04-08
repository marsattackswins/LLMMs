## [Introduction](https://www.tradingview.com/pine-script-docs/language/built-ins/#introduction)

Pine Script™ has hundreds of _built-in_ variables and functions. They provide your scripts with valuable information and make calculations for you, dispensing you from coding them. The better you know the built-ins, the more you will be able to do with your Pine scripts.

On this page, we present an overview of some of Pine’s built-in variables and functions. They will be covered in more detail in the pages of this manual covering specific themes.

All built-in variables and functions are defined in the Pine Script™ [v6 Reference Manual](https://www.tradingview.com/pine-script-reference/v6/). It is called a “Reference Manual” because it is the definitive reference on the Pine Script™ language. It is an essential tool that will accompany you anytime you code in Pine, whether you are a beginner or an expert. If you are learning your first programming language, make the [Reference Manual](https://www.tradingview.com/pine-script-reference/v6/) your friend. Ignoring it will make your programming experience with Pine Script™ difficult and frustrating — as it would with any other programming language.

Variables and functions in the same family share the same _namespace_, which is a prefix to the function’s name. The [ta.sma()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta%7Bdot%7Dsma) function, for example, is in the `ta` namespace, which stands for “technical analysis”. A namespace can contain both variables and functions.

Some variables have function versions as well, e.g.:

-   The [ta.tr](https://www.tradingview.com/pine-script-reference/v6/#fun_ta%7Bdot%7Dtr) variable returns the “True Range” of the current bar. The [ta.tr(true)](https://www.tradingview.com/pine-script-reference/v6/#fun_ta%7Bdot%7Dtr) function call also returns the “True Range”, but when the previous [close](https://www.tradingview.com/pine-script-reference/v6/#var_close) value which is normally needed to calculate it is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na), it calculates using `high - low` instead.
-   The [time](https://www.tradingview.com/pine-script-reference/v6/#var_time) variable gives the time at the [open](https://www.tradingview.com/pine-script-reference/v6/#var_open) of the current bar. The [time(timeframe)](https://www.tradingview.com/pine-script-reference/v6/#fun_time) function returns the time of the bar’s [open](https://www.tradingview.com/pine-script-reference/v6/#var_open) from the `timeframe` specified, even if the chart’s timeframe is different. The [time(timeframe, session)](https://www.tradingview.com/pine-script-reference/v6/#fun_time) function returns the time of the bar’s [open](https://www.tradingview.com/pine-script-reference/v6/#var_open) from the `timeframe` specified, but only if it is within the `session` time. The [time(timeframe, session, timezone)](https://www.tradingview.com/pine-script-reference/v6/#fun_time) function returns the time of the bar’s [open](https://www.tradingview.com/pine-script-reference/v6/#var_open) from the `timeframe` specified, but only if it is within the `session` time in the specified `timezone`.

## [Built-in variables](https://www.tradingview.com/pine-script-docs/language/built-ins/#built-in-variables)

Built-in variables exist for different purposes. These are a few examples:

-   Price- and volume-related variables: [open](https://www.tradingview.com/pine-script-reference/v6/#var_open), [high](https://www.tradingview.com/pine-script-reference/v6/#var_high), [low](https://www.tradingview.com/pine-script-reference/v6/#var_low), [close](https://www.tradingview.com/pine-script-reference/v6/#var_close), [hl2](https://www.tradingview.com/pine-script-reference/v6/#var_hl2), [hlc3](https://www.tradingview.com/pine-script-reference/v6/#var_hlc3), [ohlc4](https://www.tradingview.com/pine-script-reference/v6/#var_ohlc4), and [volume](https://www.tradingview.com/pine-script-reference/v6/#var_volume).
-   Symbol-related information in the `syminfo` namespace: [syminfo.basecurrency](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo%7Bdot%7Dbasecurrency), [syminfo.currency](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo%7Bdot%7Dcurrency), [syminfo.description](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo%7Bdot%7Ddescription), [syminfo.main\_tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.main_tickerid), [syminfo.mincontract](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.mincontract), [syminfo.mintick](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo%7Bdot%7Dmintick), [syminfo.pointvalue](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo%7Bdot%7Dpointvalue), [syminfo.prefix](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo%7Bdot%7Dprefix), [syminfo.root](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo%7Bdot%7Droot), [syminfo.session](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo%7Bdot%7Dsession), [syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo%7Bdot%7Dticker), [syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo%7Bdot%7Dtickerid), [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo%7Bdot%7Dtimezone), and [syminfo.type](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo%7Bdot%7Dtype).
-   Timeframe (a.k.a. “interval” or “resolution”, e.g., 15sec, 30min, 60min, 1D, 3M) variables in the `timeframe` namespace: [timeframe.isseconds](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe%7Bdot%7Disseconds), [timeframe.isminutes](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe%7Bdot%7Disminutes), [timeframe.isintraday](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe%7Bdot%7Disintraday), [timeframe.isdaily](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe%7Bdot%7Disdaily), [timeframe.isweekly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe%7Bdot%7Disweekly), [timeframe.ismonthly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe%7Bdot%7Dismonthly), [timeframe.isdwm](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe%7Bdot%7Disdwm), [timeframe.multiplier](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe%7Bdot%7Dmultiplier), [timeframe.main\_period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.main_period), and [timeframe.period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe%7Bdot%7Dperiod).
-   Bar states in the `barstate` namespace (see the [Bar states](https://www.tradingview.com/pine-script-docs/concepts/bar-states/) page): [barstate.isconfirmed](https://www.tradingview.com/pine-script-reference/v6/#var_barstate%7Bdot%7Disconfirmed), [barstate.isfirst](https://www.tradingview.com/pine-script-reference/v6/#var_barstate%7Bdot%7Disfirst), [barstate.ishistory](https://www.tradingview.com/pine-script-reference/v6/#var_barstate%7Bdot%7Dishistory), [barstate.islast](https://www.tradingview.com/pine-script-reference/v6/#var_barstate%7Bdot%7Dislast), [barstate.islastconfirmedhistory](https://www.tradingview.com/pine-script-reference/v6/#var_barstate%7Bdot%7Dislastconfirmedhistory), [barstate.isnew](https://www.tradingview.com/pine-script-reference/v6/#var_barstate%7Bdot%7Disnew), and [barstate.isrealtime](https://www.tradingview.com/pine-script-reference/v6/#var_barstate%7Bdot%7Disrealtime).
-   Strategy-related information in the `strategy` namespace: [strategy.equity](https://www.tradingview.com/pine-script-reference/v6/#var_strategy%7Bdot%7Dequity), [strategy.initial\_capital](https://www.tradingview.com/pine-script-reference/v6/#var_strategy%7Bdot%7Dinitial_capital), [strategy.grossloss](https://www.tradingview.com/pine-script-reference/v6/#var_strategy%7Bdot%7Dgrossloss), [strategy.grossprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy%7Bdot%7Dgrossprofit), [strategy.wintrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy%7Bdot%7Dwintrades), [strategy.losstrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy%7Bdot%7Dlosstrades), [strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy%7Bdot%7Dposition_size), [strategy.position\_avg\_price](https://www.tradingview.com/pine-script-reference/v6/#var_strategy%7Bdot%7Dposition_avg_price), [strategy.wintrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy%7Bdot%7Dwintrades), etc.

## [Built-in functions](https://www.tradingview.com/pine-script-docs/language/built-ins/#built-in-functions)

Many functions are used for the result(s) they return. These are a few examples:

-   Math-related functions in the `math` namespace: [math.abs()](https://www.tradingview.com/pine-script-reference/v6/#fun_math%7Bdot%7Dabs), [math.log()](https://www.tradingview.com/pine-script-reference/v6/#fun_math%7Bdot%7Dlog), [math.max()](https://www.tradingview.com/pine-script-reference/v6/#fun_math%7Bdot%7Dmax), [math.random()](https://www.tradingview.com/pine-script-reference/v6/#fun_math%7Bdot%7Drandom), [math.round\_to\_mintick()](https://www.tradingview.com/pine-script-reference/v6/#fun_math%7Bdot%7Dround_to_mintick), etc.
-   Technical indicators in the `ta` namespace: [ta.sma()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta%7Bdot%7Dsma), [ta.ema()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta%7Bdot%7Dema), [ta.macd()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta%7Bdot%7Dmacd), [ta.rsi()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta%7Bdot%7Drsi), [ta.supertrend()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta%7Bdot%7Dsupertrend), etc.
-   Support functions often used to calculate technical indicators in the `ta` namespace: [ta.barssince()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta%7Bdot%7Dbarssince), [ta.crossover()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta%7Bdot%7Dcrossover), [ta.highest()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta%7Bdot%7Dhighest), etc.
-   Functions to request data from other symbols or timeframes in the `request` namespace: [request.dividends()](https://www.tradingview.com/pine-script-reference/v6/#fun_request%7Bdot%7Ddividends), [request.earnings()](https://www.tradingview.com/pine-script-reference/v6/#fun_request%7Bdot%7Dearnings), [request.financial()](https://www.tradingview.com/pine-script-reference/v6/#fun_request%7Bdot%7Dfinancial), [request.quandl()](https://www.tradingview.com/pine-script-reference/v6/#fun_request%7Bdot%7Dquandl), [request.security()](https://www.tradingview.com/pine-script-reference/v6/#fun_request%7Bdot%7Dsecurity), [request.splits()](https://www.tradingview.com/pine-script-reference/v6/#fun_request%7Bdot%7Dsplits).
-   Functions to manipulate strings in the `str` namespace: [str.format()](https://www.tradingview.com/pine-script-reference/v6/#fun_str%7Bdot%7Dformat), [str.length()](https://www.tradingview.com/pine-script-reference/v6/#fun_str%7Bdot%7Dlength), [str.tonumber()](https://www.tradingview.com/pine-script-reference/v6/#fun_str%7Bdot%7Dtonumber), [str.tostring()](https://www.tradingview.com/pine-script-reference/v6/#fun_str%7Bdot%7Dtostring), etc.
-   Functions used to define the input values that script users can modify in the script’s “Settings/Inputs” tab, in the `input` namespace: [input()](https://www.tradingview.com/pine-script-reference/v6/#fun_input), [input.color()](https://www.tradingview.com/pine-script-reference/v6/#fun_input%7Bdot%7Dcolor), [input.int()](https://www.tradingview.com/pine-script-reference/v6/#fun_input%7Bdot%7Dint), [input.session()](https://www.tradingview.com/pine-script-reference/v6/#fun_input%7Bdot%7Dsession), [input.symbol()](https://www.tradingview.com/pine-script-reference/v6/#fun_input%7Bdot%7Dsymbol), etc.
-   Functions used to manipulate colors in the `color` namespace: [color.from\_gradient()](https://www.tradingview.com/pine-script-reference/v6/#fun_color%7Bdot%7Dfrom_gradient), [color.new()](https://www.tradingview.com/pine-script-reference/v6/#fun_color%7Bdot%7Drgb), [color.rgb()](https://www.tradingview.com/pine-script-reference/v6/#fun_color%7Bdot%7Dnew), etc.

Some functions do not return a result but are used for their side effects, which means they do something, even if they don’t return a result:

-   Functions used as a declaration statement defining one of three types of Pine scripts, and its properties. Each script must begin with a call to one of these functions: [indicator()](https://www.tradingview.com/pine-script-reference/v6/#fun_indicator), [strategy()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy) or [library()](https://www.tradingview.com/pine-script-reference/v6/#fun_library).
-   Plotting or coloring functions: [bgcolor()](https://www.tradingview.com/pine-script-reference/v6/#fun_bgcolor), [plotbar()](https://www.tradingview.com/pine-script-reference/v6/#fun_plotbar), [plotcandle()](https://www.tradingview.com/pine-script-reference/v6/#fun_plotcandle), [plotchar()](https://www.tradingview.com/pine-script-reference/v6/#fun_plotchar), [plotshape()](https://www.tradingview.com/pine-script-reference/v6/#fun_plotshape), [fill()](https://www.tradingview.com/pine-script-reference/v6/#fun_fill).
-   Strategy functions placing orders, in the `strategy` namespace: [strategy.cancel()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy%7Bdot%7Dcancel), [strategy.close()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy%7Bdot%7Dclose), [strategy.entry()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy%7Bdot%7Dentry), [strategy.exit()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy%7Bdot%7Dexit), [strategy.order()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy%7Bdot%7Dorder), etc.
-   Strategy functions returning information on indivdual past trades, in the `strategy` namespace: [strategy.closedtrades.entry\_bar\_index()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy%7Bdot%7Dclosedtrades%7Bdot%7Dentry_bar_index), [strategy.closedtrades.entry\_price()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy%7Bdot%7Dclosedtrades%7Bdot%7Dentry_price), [strategy.closedtrades.entry\_time()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy%7Bdot%7Dclosedtrades%7Bdot%7Dentry_time), [strategy.closedtrades.exit\_bar\_index()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy%7Bdot%7Dclosedtrades%7Bdot%7Dexit_bar_index), [strategy.closedtrades.max\_drawdown()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy%7Bdot%7Dclosedtrades%7Bdot%7Dmax_drawdown), [strategy.closedtrades.max\_runup()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy%7Bdot%7Dclosedtrades%7Bdot%7Dmax_runup), [strategy.closedtrades.profit()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy%7Bdot%7Dclosedtrades%7Bdot%7Dprofit), etc.
-   Functions to generate alert events: [alert()](https://www.tradingview.com/pine-script-reference/v6/#fun_alert) and [alertcondition()](https://www.tradingview.com/pine-script-reference/v6/#fun_alertcondition).

Other functions return a result, but we don’t always use it, e.g.: [hline()](https://www.tradingview.com/pine-script-reference/v6/#fun_hline), [plot()](https://www.tradingview.com/pine-script-reference/v6/#fun_plot), [array.pop()](https://www.tradingview.com/pine-script-reference/v6/#fun_array%7Bdot%7Dpop), [label.new()](https://www.tradingview.com/pine-script-reference/v6/#fun_label%7Bdot%7Dnew), etc.

All built-in functions are defined in the Pine Script™ [v6 Reference Manual](https://www.tradingview.com/pine-script-reference/v6/). You can click on any of the function names listed here to go to its entry in the Reference Manual, which documents the function’s signature, i.e., the list of _parameters_ it accepts and the qualified type of the value(s) it returns (a function can return more than one result). The Reference Manual entry will also list, for each parameter:

-   Its name.
-   The qualified type of the value it requires (we use _argument_ to name the values passed to a function when calling it).
-   If the parameter is required or not.

All built-in functions have one or more parameters defined in their signature. Not all parameters are required for every function.

Let’s look at the [ta.vwma()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta%7Bdot%7Dvwma) function, which returns the volume-weighted moving average of a source value. This is its entry in the Reference Manual:

![image](https://www.tradingview.com/pine-script-docs/_astro/BuiltIns-BuiltInFunctions.Csw66lto_Z11CbGU.webp)

The entry gives us the information we need to use it:

-   What the function does.
-   Its signature (or definition):

```
ta.vwma(source, length) → series float
```

-   The parameters it includes: `source` and `length`
-   The qualified type of the result it returns: “series float”.
-   An example showing it in use: `plot(ta.vwma(close, 15))`.
-   An example showing what it does, but in long form, so you can better understand its calculations. Note that this is meant to explain --- not as usable code, because it is more complicated and takes longer to execute. There are only disadvantages to using the long form.
-   The “RETURNS” section explains exacty what value the function returns.
-   The “ARGUMENTS” section lists each parameter and gives the critical information concerning what qualified type is required for arguments used when calling the function.
-   The “SEE ALSO” section refers you to related Reference Manual entries.

This is a call to the function in a line of code that declares a `myVwma` variable and assigns the result of `ta.vwma(close, 20)` to it:

`myVwma = ta.vwma(close, 20)   `

Note that:

-   We use the built-in variable [close](https://www.tradingview.com/pine-script-reference/v6/#var_close) as the argument for the `source` parameter.
-   We use `20` as the argument for the `length` parameter.
-   If placed in the global scope (i.e., starting in a line’s first position), it will be executed by the Pine Script™ runtime on each bar of the chart.

We can also use the parameter names when calling the function. Parameter names are called _keyword arguments_ when used in a function call:

`myVwma = ta.vwma(source = close, length = 20)   `

You can change the position of arguments when using keyword arguments, but only if you use them for all your arguments. When calling functions with many parameters such as [indicator()](https://www.tradingview.com/pine-script-reference/v6/#fun_indicator), you can also forego keyword arguments for the first arguments, as long as you don’t skip any. If you skip some, you must then use keyword arguments so the Pine Script™ compiler can figure out which parameter they correspond to, e.g.:

`indicator("Example", "Ex", true, max_bars_back = 100)   `

Mixing things up this way is not allowed:

`indicator(precision = 3, "Example") // Compilation error!   `

**When calling built-ins, it is critical to ensure that the arguments you use are of the required qualified type, which will vary for each parameter.**

To learn how to do this, one needs to understand Pine Script™‘s [type system](https://www.tradingview.com/pine-script-docs/language/type-system/). The Reference Manual entry for each built-in function includes an “ARGUMENTS” section which lists the qualified type required for the argument supplied to each of the function’s parameters.