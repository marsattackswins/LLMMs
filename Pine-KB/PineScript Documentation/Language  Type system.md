## [Introduction](https://www.tradingview.com/pine-script-docs/language/type-system/#introduction)

The Pine Script™ type system determines the compatibility of a script’s values with various functions and operations. While it’s possible to write simple scripts without knowing anything about the type system, a reasonable understanding of it is necessary to achieve any degree of proficiency with the language, and an in-depth knowledge of its subtleties allows programmers to harness its full potential.

Pine Script™ uses [types](https://www.tradingview.com/pine-script-docs/language/type-system/#types) to classify all values, and it uses [qualifiers](https://www.tradingview.com/pine-script-docs/language/type-system/#qualifiers) to determine whether values and references are constant, established on the first script execution, or dynamic across executions. This system applies to all Pine values and references, including literals, variables, expressions, function returns, and function arguments.

The type system closely intertwines with Pine’s [execution model](https://www.tradingview.com/pine-script-docs/language/execution-model/) and [time series](https://www.tradingview.com/pine-script-docs/language/time-series/) concepts. Understanding all three is essential for making the most of the power of Pine Script™.

## [Qualifiers](https://www.tradingview.com/pine-script-docs/language/type-system/#qualifiers)

Pine Script™ _qualifiers_ identify when values are accessible to a script:

-   Values and references qualified as [const](https://www.tradingview.com/pine-script-docs/language/type-system/#const) are established at compile time (i.e., when saving the script in the Pine Editor or adding it to the chart).
-   Values qualified as [input](https://www.tradingview.com/pine-script-docs/language/type-system/#input) are established at input time (i.e., when confirming values based on user input, primarily from the “Settings/Inputs” tab).
-   Values qualified as [simple](https://www.tradingview.com/pine-script-docs/language/type-system/#simple) are established at bar zero (i.e., the first script execution).
-   Values qualified as [series](https://www.tradingview.com/pine-script-docs/language/type-system/#series) can change throughout the script’s executions.

Pine Script™ bases the dominance of type qualifiers on the following hierarchy: **const < input < simple < series**, where “const” is the _weakest_ qualifier and “series” is the _strongest_. The qualifier hierarchy translates to this rule: whenever a variable, function, or operation is compatible with a specific qualified type, values with _weaker_ qualifiers are also allowed.

Scripts always qualify their expressions’ returned types based on the _dominant qualifier_ in their calculations. For example, evaluating an expression that involves “input” and “series” values will return a value qualified as “series”. Furthermore, scripts **cannot** change a value’s qualifier to one that’s _lower_ on the hierarchy. If a value acquires a _stronger_ qualifier (e.g., a value initially inferred as “simple” becomes “series” later in the script’s executions), that state is irreversible.

It’s important to note that “series” values are the **only** ones that can change across script executions, including those from various built-ins, such as [close](https://www.tradingview.com/pine-script-reference/v6/#var_close) and [volume](https://www.tradingview.com/pine-script-reference/v6/#var_volume), as well as the results of expressions involving “series” values. All values qualified as “const”, “input”, or “simple” remain consistent across all script executions.

### [const](https://www.tradingview.com/pine-script-docs/language/type-system/#const)

Values or references qualified as “const” are established at _compile time_, before the script starts its executions. Compilation initially occurs when saving a script in the Pine Editor, which does not require it to run on a chart. Values or references with the “const” qualifier _never change_ between script executions, not even on the first execution.

All _literal_ values and the results returned by expressions involving only values qualified as “const” automatically adopt the “const” qualifier.

These are some examples of literal values:

-   _literal int_: `1`, `-1`, `42`
-   _literal float_: `1.`, `1.0`, `3.14`, `6.02E-23`, `3e8`
-   _literal bool_: `true`, `false`
-   _literal color_: `#FF55C6`, `#FF55C6ff`
-   _literal string_: `"A text literal"`, `"Embedded single quotes 'text'"`, `'Embedded double quotes "text"'`

Our [Style guide](https://www.tradingview.com/pine-script-docs/writing/style-guide/) recommends using uppercase SNAKE\_CASE to name “const” variables for readability. While not a requirement, one can also use the [var](https://www.tradingview.com/pine-script-reference/v6/#kw_var) keyword when declaring “const” variables so the script only initializes them on the _first bar_ of the dataset. See [this section](https://www.tradingview.com/pine-script-docs/language/variable-declarations/#var) of our User Manual for more information.

Below is an example that uses “const” values within the [indicator()](https://www.tradingview.com/pine-script-reference/v6/#fun_indicator) and [plot()](https://www.tradingview.com/pine-script-reference/v6/#fun_plot) functions, which both require a value of the “const string” qualified type as their `title` argument:

`//@version=6      // The following global variables are all of the "const string" qualified type:      //@variable The title of the indicator.   INDICATOR_TITLE = "const demo"   //@variable The title of the first plot.   var PLOT1_TITLE = "High"   //@variable The title of the second plot.   const string PLOT2_TITLE = "Low"   //@variable The title of the third plot.   PLOT3_TITLE = "Midpoint between " + PLOT1_TITLE + " and " + PLOT2_TITLE      indicator(INDICATOR_TITLE, overlay = true)      plot(high, PLOT1_TITLE)   plot(low, PLOT2_TITLE)   plot(hl2, PLOT3_TITLE)   `

The following example will raise a compilation error since it uses [syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker), which returns a “simple” value because it depends on chart information that’s only accessible after the script’s first execution:

``//@version=6      //@variable The title in the `indicator()` call.   var NAME = "My indicator for " + syminfo.ticker      indicator(NAME, "", true) // Causes an error because `NAME` is qualified as a "simple string".   plot(close)   ``

The [const](https://www.tradingview.com/pine-script-reference/v6/#type_const) keyword allows the declaration of variables and parameters with constant _value assignments_. Declaring a variable with this keyword instructs the script to forbid using _reassignment_ and _compound assignment_ operations on it. For example, this script declares the `myVar` variable with the keyword, then attempts to assign a new “float” value to the variable with the addition assignment operator ([+=](https://www.tradingview.com/pine-script-reference/v6/#op_+=)), resulting in a compilation error:

``//@version=6   indicator("Cannot reassign const demo")      //@variable A "float" variable declared as `const`, preventing reassignment.    const float myVar = 0.0      myVar += 1.0 // Causes an error. Reassignment and compound assignments are not allowed on `const` variables.      plot(myVar)   ``

It’s crucial to note that declaring a variable with the [const](https://www.tradingview.com/pine-script-reference/v6/#type_const) keyword forces it to maintain a constant reference to the value returned by a specific expression, but that _does not_ necessarily define the nature of the assigned value. For example, a script can declare a [const](https://www.tradingview.com/pine-script-reference/v6/#type_const) variable that maintains a constant reference to an expression returning the _ID_ of a _special type_. Although the script cannot _reassign_ the variable, the assigned ID is a “series” value:

``//@version=6   indicator("Constant reference to 'series' ID demo")      //@variable A `label` variable declared as `const`, preventing reassignment.   //          Although the reference is constant, the ID of the `label` is a "series" value.   const label myVar = label.new(bar_index, close)   ``

### [input](https://www.tradingview.com/pine-script-docs/language/type-system/#input)

Most values qualified as “input” are established after initialization via the `input.*()` functions. These functions produce values that users can modify within the “Inputs” tab of the script’s settings. When one changes any of the values in this tab, the script _restarts_ from the beginning of the chart’s history to ensure its inputs are consistent throughout its executions. Some of Pine’s built-in variables, such as [chart.bg\_color](https://www.tradingview.com/pine-script-reference/v6/#var_chart.bg_color) also use the “input” qualifier, even though `input.*()` functions do not return them, since the script receives their values at _input time_.

The following script plots the value of a `sourceInput` from the `symbolInput` and `timeframeInput` context. The [request.security()](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security) call is valid in this script since its `symbol` and `timeframe` parameters allow “series string” arguments by default, meaning they can also accept “input string” values because the “input” qualifier is _lower_ on the hierarchy:

``//@version=6   indicator("input demo", overlay = true)      //@variable The symbol to request data from. Qualified as "input string".   symbolInput = input.symbol("AAPL", "Symbol")   //@variable The timeframe of the data request. Qualified as "input string".   timeframeInput = input.timeframe("D", "Timeframe")   //@variable The source of the calculation. Qualified as "series float".   sourceInput = input.source(close, "Source")      //@variable The `sourceInput` value from the requested context. Qualified as "series float".   requestedSource = request.security(symbolInput, timeframeInput, sourceInput)      plot(requestedSource)   ``

### [simple](https://www.tradingview.com/pine-script-docs/language/type-system/#simple)

Values qualified as “simple” are available on the first script execution, and they remain consistent across subsequent executions.

Users can explicitly define variables and parameters that accept “simple” values by including the `simple` keyword in their declaration.

Many built-in variables return “simple” qualified values because they depend on information that a script can only obtain once it starts running on the chart. Additionally, many built-in functions require “simple” arguments that do not change over time. Wherever a script allows “simple” values, it can also accept values qualified as “input” or “const”.

This script highlights the background to warn users that they’re using a non-standard chart type. It uses the value of [chart.is\_standard](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_standard) to calculate the `isNonStandard` variable, then uses that variable’s value to calculate a `warningColor` that also references a “simple” value. The `color` parameter of [bgcolor()](https://www.tradingview.com/pine-script-reference/v6/#fun_bgcolor) allows a “series color” argument, meaning it can also accept a “simple color” value since “simple” is lower on the hierarchy:

``//@version=6   indicator("simple demo", overlay = true)      //@variable Is `true` when the current chart is non-standard. Qualified as "simple bool".   isNonStandard = not chart.is_standard   //@variable Is orange when the the current chart is non-standard. Qualified as "simple color".   simple color warningColor = isNonStandard ? color.new(color.orange, 70) : na      // Colors the chart's background to warn that it's a non-standard chart type.   bgcolor(warningColor, title = "Non-standard chart color")   ``

### [series](https://www.tradingview.com/pine-script-docs/language/type-system/#series)

Values qualified as “series” provide the most flexibility in scripts since they can change across executions.

Users can explicitly define variables and parameters that accept “series” values by including the `series` keyword in their declarations.

Built-in variables such as [open](https://www.tradingview.com/pine-script-reference/v6/#var_open), [high](https://www.tradingview.com/pine-script-reference/v6/#var_high), [low](https://www.tradingview.com/pine-script-reference/v6/#var_low), [close](https://www.tradingview.com/pine-script-reference/v6/#var_close), [volume](https://www.tradingview.com/pine-script-reference/v6/#var_volume), [time](https://www.tradingview.com/pine-script-reference/v6/#var_time), and [bar\_index](https://www.tradingview.com/pine-script-reference/v6/#var_bar_index), and the result from any expression using such built-ins, are qualified as “series”. The result of any function or operation that returns a dynamic value will always be a “series”, as will the results from using the history-referencing operator [\[\]](https://www.tradingview.com/pine-script-reference/v6/#op_%5B%5D) to access historical values. Wherever a script allows “series” values, it will also accept values with any other qualifier, as “series” is the _highest_ qualifier on the hierarchy.

This script displays the [highest](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.highest) and [lowest](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.lowest) value of a `sourceInput` over `lengthInput` bars. The values assigned to the `highest` and `lowest` variables are of the “series float” qualified type, as they can change throughout the script’s execution:

``//@version=6   indicator("series demo", overlay = true)      //@variable The source value to calculate on. Qualified as "series float".   series float sourceInput = input.source(close, "Source")   //@variable The number of bars in the calculation. Qualified as "input int".   lengthInput = input.int(20, "Length")      //@variable The highest `sourceInput` value over `lengthInput` bars. Qualified as "series float".   series float highest = ta.highest(sourceInput, lengthInput)   //@variable The lowest `sourceInput` value over `lengthInput` bars. Qualified as "series float".   lowest = ta.lowest(sourceInput, lengthInput)      plot(highest, "Highest source", color.green)   plot(lowest, "Lowest source", color.red)   ``

## [Types](https://www.tradingview.com/pine-script-docs/language/type-system/#types)

Pine Script™ _types_ classify values and determine the functions and operations they’re compatible with. They include:

-   The fundamental types: [int](https://www.tradingview.com/pine-script-docs/language/type-system/#int), [float](https://www.tradingview.com/pine-script-docs/language/type-system/#float), [bool](https://www.tradingview.com/pine-script-docs/language/type-system/#bool), [color](https://www.tradingview.com/pine-script-docs/language/type-system/#color), and [string](https://www.tradingview.com/pine-script-docs/language/type-system/#string)
-   The special types: [plot](https://www.tradingview.com/pine-script-docs/language/type-system/#plot-and-hline), [hline](https://www.tradingview.com/pine-script-docs/language/type-system/#plot-and-hline), [line](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types), [linefill](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types), [box](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types), [polyline](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types), [label](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types), [table](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types), [chart.point](https://www.tradingview.com/pine-script-docs/language/type-system/#chart-points), [array](https://www.tradingview.com/pine-script-docs/language/type-system/#collections), [matrix](https://www.tradingview.com/pine-script-docs/language/type-system/#collections), and [map](https://www.tradingview.com/pine-script-docs/language/type-system/#collections)
-   [User-defined types (UDTs)](https://www.tradingview.com/pine-script-docs/language/type-system/#user-defined-types)
-   [Enums](https://www.tradingview.com/pine-script-docs/language/type-system/#enum-types)
-   [void](https://www.tradingview.com/pine-script-docs/language/type-system/#void)

Fundamental types refer to the underlying nature of a value, e.g., a value of 1 is of the “int” type, 1.0 is of the “float” type, “AAPL” is of the “string” type, etc. Special types and user-defined types utilize _IDs_ that refer to objects of a specific type. For example, a value of the “label” type contains an ID that acts as a _pointer_ referring to a “label” object. The “void” type refers to the output from a function or [method](https://www.tradingview.com/pine-script-docs/language/methods/) that does not return a usable value.

Pine Script™ can automatically convert values from some types into others. The auto-casting rules are: **int → float → bool**. See the [Type casting](https://www.tradingview.com/pine-script-docs/language/type-system/#type-casting) section of this page for more information.

In most cases, Pine Script™ can automatically determine a value’s type. However, we can also use type keywords to _explicitly_ specify types for readability and for code that requires explicit definitions (e.g., declaring a variable assigned to [na](https://www.tradingview.com/pine-script-reference/v6/#var_na)). For example:

``//@version=6   indicator("Types demo", overlay = true)      //@variable A value of the "const string" type for the `ma` plot's title.   string MA_TITLE = "MA"      //@variable A value of the "input int" type. Controls the length of the average.   int lengthInput = input.int(100, "Length", minval = 2)      //@variable A "series float" value representing the last `close` that crossed over the `ma`.   var float crossValue = na      //@variable A "series float" value representing the moving average of `close`.   float ma = ta.sma(close, lengthInput)   //@variable A "series bool" value that's `true` when the `close` crosses over the `ma`.   bool crossUp = ta.crossover(close, ma)   //@variable A "series color" value based on whether `close` is above or below its `ma`.   color maColor = close > ma ? color.lime : color.fuchsia      // Update the `crossValue`.   if crossUp       crossValue := close      plot(ma, MA_TITLE, maColor)   plot(crossValue, "Cross value", style = plot.style_circles)   plotchar(crossUp, "Cross Up", "▲", location.belowbar, size = size.small)   ``

### [int](https://www.tradingview.com/pine-script-docs/language/type-system/#int)

Values of the “int” type represent integers, i.e., whole numbers without any fractional quantities.

Integer literals are numeric values written in _decimal_ notation. For example:

Built-in variables such as [bar\_index](https://www.tradingview.com/pine-script-reference/v6/#var_bar_index), [time](https://www.tradingview.com/pine-script-reference/v6/#var_time), [timenow](https://www.tradingview.com/pine-script-reference/v6/#var_timenow), [dayofmonth](https://www.tradingview.com/pine-script-reference/v6/#var_dayofmonth), and [strategy.wintrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.wintrades) all return values of the “int” type.

### [float](https://www.tradingview.com/pine-script-docs/language/type-system/#float)

Values of the “float” type represent floating-point numbers, i.e., numbers that can contain whole and fractional quantities.

Floating-point literals are numeric values written with a `.` delimiter. They may also contain the symbol `e` or `E` (which means “10 raised to the power of X”, where X is the number after the `e` or `E` symbol). For example:

`3.14159    // Rounded value of Pi (π)   - 3.0   6.02e23    // 6.02 * 10^23 (a very large value)   1.6e-19    // 1.6 * 10^-19 (a very small value)   `

The internal precision of “float” values in Pine Script™ is 1e-16.

Built-in variables such as [close](https://www.tradingview.com/pine-script-reference/v6/#var_close), [hlcc4](https://www.tradingview.com/pine-script-reference/v6/#var_hlcc4), [volume](https://www.tradingview.com/pine-script-reference/v6/#var_volume), [ta.vwap](https://www.tradingview.com/pine-script-reference/v6/#var_ta.vwap), and [strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_size) all return values of the “float” type.

### [bool](https://www.tradingview.com/pine-script-docs/language/type-system/#bool)

Values of the “bool” type represent the truth value of a comparison or condition, which scripts can use in [conditional structures](https://www.tradingview.com/pine-script-docs/language/conditional-structures/) and other expressions.

There are only two literals that represent boolean values:

`true    // true value   false   // false value   `

A `bool` variable can never be [na](https://www.tradingview.com/pine-script-reference/v6/#var_na), and any [conditional structure](https://www.tradingview.com/pine-script-docs/language/conditional-structures) that can return `na` will return `false` instead. For example, an [if](https://www.tradingview.com/pine-script-reference/v6/#kw_if) condition returns `bool` values, when the condition is not met and the `else` block is not specified, it will returns `false`.

Built-in variables such as [barstate.isfirst](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isfirst), [chart.is\_heikinashi](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_heikinashi), [session.ismarket](https://www.tradingview.com/pine-script-reference/v6/#var_session.ismarket), and [timeframe.isdaily](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isdaily) all return values of the “bool” type.

### [color](https://www.tradingview.com/pine-script-docs/language/type-system/#color)

Color literals have the following format: `#RRGGBB` or `#RRGGBBAA`. The letter pairs represent _hexadecimal_ values between `00` and `FF` (0 to 255 in decimal) where:

-   `RR`, `GG` and `BB` pairs respectively represent the values for the color’s red, green and blue components.
-   `AA` is an optional value for the color’s opacity (or _alpha_ component) where `00` is invisible and `FF` opaque. When the literal does not include an `AA` pair, the script treats it as fully opaque (the same as using `FF`).
-   The hexadecimal letters in the literals can be uppercase or lowercase.

These are examples of “color” literals:

`#000000      // black color   #FF0000      // red color   #00FF00      // green color   #0000FF      // blue color   #FFFFFF      // white color   #808080      // gray color   #3ff7a0      // some custom color   #FF000080    // 50% transparent red color   #FF0000ff    // same as #FF0000, fully opaque red color   #FF000000    // completely transparent red color   `

Pine Script™ also has [built-in color constants](https://www.tradingview.com/pine-script-docs/concepts/colors/#constant-colors), including [color.green](https://www.tradingview.com/pine-script-reference/v6/#const_color%7Bdot%7Dgreen), [color.red](https://www.tradingview.com/pine-script-reference/v6/#const_color%7Bdot%7Dred), [color.orange](https://www.tradingview.com/pine-script-reference/v6/#const_color%7Bdot%7Dorange), [color.blue](https://www.tradingview.com/pine-script-reference/v6/#const_color%7Bdot%7Dblue) (the default color in `plot*()` functions and many of the default color-related properties in [drawing types](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types)), etc.

When using built-in color constants, it is possible to add transparency information to them via the [color.new()](https://www.tradingview.com/pine-script-reference/v6/#fun_color.new) function.

Note that when specifying red, green or blue components in `color.*()` functions, we use “int” or “float” arguments with values between 0 and 255. When specifying transparency, we use a value between 0 and 100, where 0 means fully opaque and 100 means completely transparent. For example:

``//@version=6   indicator("Shading the chart's background", overlay = true)      //@variable A "const color" value representing the base for each day's color.    color BASE_COLOR = color.rgb(0, 99, 165)      //@variable A "series int" value that modifies the transparency of the `BASE_COLOR` in `color.new()`.   int transparency = 50 + int(40 * dayofweek / 7)      // Color the background using the modified `BASE_COLOR`.   bgcolor(color.new(BASE_COLOR, transparency))   ``

See the User Manual’s page on [colors](https://www.tradingview.com/pine-script-docs/concepts/colors/) for more information on using colors in scripts.

### [string](https://www.tradingview.com/pine-script-docs/language/type-system/#string)

Values of the “string” type represent sequences of letters, numbers, symbols, spaces, and other characters.

String literals in Pine are characters enclosed in single or double quotation marks. For example:

`"This is a string literal using double quotes."   'This is a string literal using single quotes.'   `

Single and double quotation marks are functionally equivalent in Pine Script™. A “string” enclosed within double quotation marks can contain any number of single quotation marks and vice versa:

`"It's an example"   'The "Star" indicator'   `

Scripts can _escape_ the enclosing delimiter in a “string” using the backslash character (`\`). For example:

`'It\'s an example'   "The \"Star\" indicator"   `

We can create “string” values containing the new line escape character (`\n`) for displaying multi-line text with `plot*()` and `log.*()` functions and objects of [drawing types](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types). For example:

`"This\nString\nHas\nOne\nWord\nPer\nLine"   `

We can use the [+](https://www.tradingview.com/pine-script-reference/v6/#op_+) operator to concatenate “string” values:

`"This is a " + "concatenated string."   `

The built-ins in the `str.*()` namespace create “string” values using specialized operations. For instance, this script creates a _formatted string_ to represent “float” price values and displays the result using a label:

``//@version=6   indicator("Formatted string demo", overlay = true)      //@variable A "series string" value representing the bar's OHLC data.   string ohlcString = str.format("Open: {0}\nHigh: {1}\nLow: {2}\nClose: {3}", open, high, low, close)      // Draw a label containing the `ohlcString`.   label.new(bar_index, high, ohlcString, textcolor = color.white)   ``

See our User Manual’s page on [Text and shapes](https://www.tradingview.com/pine-script-docs/concepts/text-and-shapes/) for more information about displaying “string” values from a script.

Built-in variables such as [syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.tickerid), [syminfo.currency](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.currency), and [timeframe.period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.period) return values of the “string” type.

### [plot and hline](https://www.tradingview.com/pine-script-docs/language/type-system/#plot-and-hline)

Pine Script™‘s [plot()](https://www.tradingview.com/pine-script-reference/v6/#fun_plot) and [hline()](https://www.tradingview.com/pine-script-reference/v6/#fun_hline) functions return IDs that respectively reference instances of the “plot” and “hline” types. These types display calculated values and horizontal levels on the chart, and one can assign their IDs to variables for use with the built-in [fill()](https://www.tradingview.com/pine-script-reference/v6/#fun_fill) function.

For example, this script plots two EMAs on the chart and fills the space between them using a [fill()](https://www.tradingview.com/pine-script-reference/v6/#fun_fill) call:

``//@version=6   indicator("plot fill demo", overlay = true)      //@variable A "series float" value representing a 10-bar EMA of `close`.   float emaFast = ta.ema(close, 10)   //@variable A "series float" value representing a 20-bar EMA of `close`.   float emaSlow = ta.ema(close, 20)      //@variable The plot of the `emaFast` value.   emaFastPlot = plot(emaFast, "Fast EMA", color.orange, 3)   //@variable The plot of the `emaSlow` value.   emaSlowPlot = plot(emaSlow, "Slow EMA", color.gray, 3)      // Fill the space between the `emaFastPlot` and `emaSlowPlot`.   fill(emaFastPlot, emaSlowPlot, color.new(color.purple, 50), "EMA Fill")   ``

It’s important to note that unlike other special types, there is no `plot` or `hline` keyword in Pine to explicitly declare a variable’s type as “plot” or “hline”.

Users can control where their scripts’ plots display via the variables in the `display.*` namespace and a `plot*()` function’s `force_overlay` parameter. Additionally, one script can use the values from another script’s plots as _external inputs_ via the [input.source()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.source) function (see our User Manual’s section on [source inputs](https://www.tradingview.com/pine-script-docs/concepts/inputs/#source-input)).

### [Drawing types](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types)

Pine Script™ drawing types allow scripts to create custom drawings on charts. They include the following: [line](https://www.tradingview.com/pine-script-reference/v6/#type_line), [linefill](https://www.tradingview.com/pine-script-reference/v6/#type_linefill), [box](https://www.tradingview.com/pine-script-reference/v6/#type_box), [polyline](https://www.tradingview.com/pine-script-reference/v6/#type_polyline), [label](https://www.tradingview.com/pine-script-reference/v6/#type_label), and [table](https://www.tradingview.com/pine-script-reference/v6/#type_table).

Each type also has a namespace containing all the built-ins that create and manage drawing instances. For example, the following `*.new()` constructors create new objects of these types in a script: [line.new()](https://www.tradingview.com/pine-script-reference/v6/#fun_line.new), [linefill.new()](https://www.tradingview.com/pine-script-reference/v6/#fun_linefill.new), [box.new()](https://www.tradingview.com/pine-script-reference/v6/#fun_box.new), [polyline.new()](https://www.tradingview.com/pine-script-reference/v6/#fun_polyline.new), [label.new()](https://www.tradingview.com/pine-script-reference/v6/#fun_label.new), and [table.new()](https://www.tradingview.com/pine-script-reference/v6/#fun_table.new).

Each of these functions returns an _ID_ which is a reference that uniquely identifies a drawing object. IDs are always qualified as “series”, meaning their qualified types are “series line”, “series label”, etc. Drawing IDs act like pointers, as each ID references a specific instance of a drawing in all the functions from that drawing’s namespace. For instance, the ID of a line returned by a [line.new()](https://www.tradingview.com/pine-script-reference/v6/#fun_line.new) call is used later to refer to that specific object once it’s time to delete it with [line.delete()](https://www.tradingview.com/pine-script-reference/v6/#fun_line.delete).

### [Chart points](https://www.tradingview.com/pine-script-docs/language/type-system/#chart-points)

Chart points are special types that represent coordinates on the chart. Scripts use the information from [chart.point](https://www.tradingview.com/pine-script-reference/v6/#type_chart.point) objects to determine the chart locations of [lines](https://www.tradingview.com/pine-script-docs/concepts/lines-and-boxes/#lines), [boxes](https://www.tradingview.com/pine-script-docs/concepts/lines-and-boxes/#boxes), [polylines](https://www.tradingview.com/pine-script-docs/concepts/lines-and-boxes/#polylines), and [labels](https://www.tradingview.com/pine-script-docs/concepts/text-and-shapes/#labels).

Objects of this type contain three _fields_: `time`, `index`, and `price`. Whether a drawing instance uses the `time` or `price` field from a [chart.point](https://www.tradingview.com/pine-script-reference/v6/#type_chart.point) as an x-coordinate depends on the drawing’s `xloc` property.

We can use any of the following functions to create chart points in a script:

-   [chart.point.new()](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.new) - Creates a new [chart.point](https://www.tradingview.com/pine-script-reference/v6/#type_chart.point) with a specified `time`, `index`, and `price`.
-   [chart.point.now()](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.now) - Creates a new [chart.point](https://www.tradingview.com/pine-script-reference/v6/#type_chart.point) with a specified `price` y-coordinate. The `time` and `index` fields contain the [time](https://www.tradingview.com/pine-script-reference/v6/#var_time) and [bar\_index](https://www.tradingview.com/pine-script-reference/v6/#var_bar_index) of the bar the function executes on.
-   [chart.point\_from\_index()](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.from_index) - Creates a new [chart.point](https://www.tradingview.com/pine-script-reference/v6/#type_chart.point) with an `index` x-coordinate and `price` y-coordinate. The `time` field of the resulting instance is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na), meaning it will not work with drawing objects that use an `xloc` value of [xloc.bar\_time](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_time).
-   [chart.point.from\_time()](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.from_time) - Creates a new [chart.point](https://www.tradingview.com/pine-script-reference/v6/#type_chart.point) with a `time` x-coordinate and `price` y-coordinate. The `index` field of the resulting instance is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na), meaning it will not work with drawing objects that use an `xloc` value of [xloc.bar\_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index).
-   [chart.point.copy()](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.copy) - Creates a new [chart.point](https://www.tradingview.com/pine-script-reference/v6/#type_chart.point) containing the same `time`, `index`, and `price` information as the `id` in the function call.

This example draws lines connecting the previous bar’s [high](https://www.tradingview.com/pine-script-reference/v6/#var_high) to the current bar’s [low](https://www.tradingview.com/pine-script-reference/v6/#var_low) on each chart bar. It also displays labels at both points of each line. The line and labels get their information from the `firstPoint` and `secondPoint` variables, which reference chart points created using [chart.point\_from\_index()](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.from_index) and [chart.point.now()](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.now):

``//@version=6   indicator("Chart points demo", overlay = true)      //@variable A new `chart.point` at the previous `bar_index` and `high`.   firstPoint = chart.point.from_index(bar_index - 1, high[1])   //@variable A new `chart.point` at the current bar's `low`.   secondPoint = chart.point.now(low)      // Draw a new line connecting coordinates from the `firstPoint` and `secondPoint`.   // This line uses the `index` fields from the points as x-coordinates.   line.new(firstPoint, secondPoint, color = color.purple, width = 3)   // Draw a label at the `firstPoint`. Uses the point's `index` field as its x-coordinate.   label.new(        firstPoint, str.tostring(firstPoint.price), color = color.green,         style = label.style_label_down, textcolor = color.white    )   // Draw a label at the `secondPoint`. Uses the point's `index` field as its x-coordinate.   label.new(        secondPoint, str.tostring(secondPoint.price), color = color.red,         style = label.style_label_up, textcolor = color.white    )   ``

### [Collections](https://www.tradingview.com/pine-script-docs/language/type-system/#collections)

Collections in Pine Script™ ([arrays](https://www.tradingview.com/pine-script-docs/language/arrays/), [matrices](https://www.tradingview.com/pine-script-docs/language/matrices/), and [maps](https://www.tradingview.com/pine-script-docs/language/maps/)) utilize reference IDs, much like other special types (e.g., labels). The type of the ID defines the type of _elements_ the collection will contain. In Pine, we specify array, matrix, and map types by appending a [type template](https://www.tradingview.com/pine-script-docs/language/type-system/#type-templates) to the [array](https://www.tradingview.com/pine-script-reference/v6/#type_array), [matrix](https://www.tradingview.com/pine-script-reference/v6/#type_matrix), or [map](https://www.tradingview.com/pine-script-reference/v6/#type_map) keywords:

-   `array<int>` defines an array containing “int” elements.
-   `array<label>` defines an array containing “label” IDs.
-   `array<UDT>` defines an array containing IDs referencing objects of a [user-defined type (UDT)](https://www.tradingview.com/pine-script-docs/language/type-system/#user-defined-types).
-   `matrix<float>` defines a matrix containing “float” elements.
-   `matrix<UDT>` defines a matrix containing IDs referencing objects of a [user-defined type (UDT)](https://www.tradingview.com/pine-script-docs/language/type-system/#user-defined-types).
-   `map<string, float>` defines a map containing “string” keys and “float” values.
-   `map<int, UDT>` defines a map containing “int” keys and IDs of [user-defined type (UDT)](https://www.tradingview.com/pine-script-docs/language/type-system/#user-defined-types) instances as values.

For example, one can declare an “int” array with a single element value of 10 in any of the following, equivalent ways:

`a1 = array.new<int>(1, 10)   array<int> a2 = array.new<int>(1, 10)   a3 = array.from(10)   array<int> a4 = array.from(10)   `

Note that:

-   The `int[]` syntax can also specify an array of “int” elements, but its use is discouraged. No equivalent exists to specify the types of matrices or maps in that way.
-   Type-specific built-ins exist for arrays, such as [array.new\_int()](https://www.tradingview.com/pine-script-reference/v6/#fun_array%7Bdot%7Dnew_int), but the more generic [array.new<type>](https://www.tradingview.com/pine-script-reference/v6/#type_array) form is preferred, which would be `array.new<int>()` to create an array of “int” elements.

### [User-defined types](https://www.tradingview.com/pine-script-docs/language/type-system/#user-defined-types)

The [type](https://www.tradingview.com/pine-script-reference/v6/#kw_type) keyword allows the creation of _user-defined types_ (UDTs) from which scripts can create [objects](https://www.tradingview.com/pine-script-docs/language/objects/). UDTs are composite types; they contain an arbitrary number of _fields_ that can be of any type, including other user-defined types.

The syntax to declare a user-defined type is:

```
[export ]type <UDT_identifier>    <field_type> <field_name>[ = <value>]    ...
```

where:

-   [export](https://www.tradingview.com/pine-script-reference/v6/#kw_export) is the keyword that a [library](https://www.tradingview.com/pine-script-reference/v6/#fun_library) script uses to export the user-defined type. To learn more about exporting UDTs, see our User Manual’s [Libraries](https://www.tradingview.com/pine-script-docs/concepts/libraries/#user-defined-types-and-objects) page.
-   `<UDT_identifier>` is the name of the user-defined type.
-   `<field_type>` is the type of the field.
-   `<field_name>` is the name of the field.
-   `<value>` is an optional default value for the field, which the script will assign to it when creating new objects of that UDT. If one does not provide a value, the field’s default is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na). The same rules as those governing the default values of parameters in function signatures apply to the default values of fields. For example, a UDT’s default values cannot use results from the history-referencing operator [\[\]](https://www.tradingview.com/pine-script-reference/v6/#op_%5B%5D) or expressions.

This example declares a `pivotPoint` UDT with an “int” `pivotTime` field and a “float” `priceLevel` field that will respectively hold time and price information about a calculated pivot:

    `//@type             A user-defined type containing pivot information.       //@field pivotTime  Contains time information about the pivot.       //@field priceLevel Contains price information about the pivot.       type pivotPoint           int   pivotTime           float priceLevel`

User-defined types support _type recursion_, i.e., the fields of a UDT can reference objects of the same UDT. Here, we’ve added a `nextPivot` field to our previous `pivotPoint` type that references another `pivotPoint` instance:

    ``//@type             A user-defined type containing pivot information.       //@field pivotTime  Contains time information about the pivot.       //@field priceLevel Contains price information about the pivot.       //@field nextPivot  A `pivotPoint` instance containing additional pivot information.       type pivotPoint           int        pivotTime           float      priceLevel           pivotPoint nextPivot``

Scripts can use two built-in methods to create and copy UDTs: `new()` and `copy()`. See our User Manual’s page on [Objects](https://www.tradingview.com/pine-script-docs/language/objects/) to learn more about working with UDTs.

### [Enum types](https://www.tradingview.com/pine-script-docs/language/type-system/#enum-types)

The [enum](https://www.tradingview.com/pine-script-reference/v6/#kw_enum) keyword allows the creation of an _enum_, otherwise known as an _enumeration_, _enumerated type_, or _enum type_. An enum is a unique type construct containing distinct, named fields representing _members_ (i.e., possible values) of the type. Enums allow programmers to control the values accepted by variables, conditional expressions, and [collections](https://www.tradingview.com/pine-script-docs/language/type-system/#collections), and they facilitate convenient dropdown [input](https://www.tradingview.com/pine-script-docs/concepts/inputs/#enum-input) creation with the [input.enum()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.enum) function.

The syntax to declare an enum is as follows:

```
[export ]enum <enumName>    <field_1>[ = <title_1>]    <field_2>[ = <title_2>]    ...    <field_N>[ = <title_N>]
```

where:

-   [export](https://www.tradingview.com/pine-script-reference/v6/#kw_export) is the optional keyword allowing a [library](https://www.tradingview.com/pine-script-reference/v6/#fun_library) to export the enum for use in other scripts. See [this section](https://www.tradingview.com/pine-script-docs/concepts/libraries/#enum-types) to learn more about exporting enum types.
-   `<enumName>` is the name of the enum type. Scripts can use the enum’s name as the type keyword in [variable declarations](https://www.tradingview.com/pine-script-docs/language/variable-declarations/) and [type templates](https://www.tradingview.com/pine-script-docs/language/type-system/#type-templates).
-   `<field_*>` is the name of an enum field, representing a named member (value) of the `enumName` type. Each field must have a unique name that does not match the name or title of any other field in the enum. To retrieve an enum member, reference its field name using dot notation syntax (i.e., `enumName.fieldName`).
-   `<title_*>` is a “const string” title assigned to a field. If one does not specify a title, the field’s title is the “string” representation of its name. The [input.enum()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.enum) function displays field titles within its dropdown in the script’s “Settings/Inputs” tab. Users can also retrieve a field’s title with the [str.tostring()](https://www.tradingview.com/pine-script-reference/v6/#fun_str.tostring) function. As with field names, each field’s title must not match the name or title of any other field in the enum.

This example declares an `maChoice` enum. Each field within this declaration represents a distinct member of the `maChoice` enum type:

`//@enum       An enumeration of named values for moving average selection.   //@field sma  Selects a Simple Moving Average.   //@field ema  Selects an Exponential Moving Average.   //@field wma  Selects a Weighted Moving Average.   //@field hma  Selects a Hull Moving Average.   enum maChoice       sma  = "Simple Moving Average"       ema  = "Exponential Moving Average"       wma  = "Weighted Moving Average"       hma  = "Hull Moving Average"   `

Note that:

-   All the enum’s possible values are available upon the _first_ script execution and do not change across subsequent executions. Hence, they automatically adopt the [simple](https://www.tradingview.com/pine-script-docs/language/type-system/#simple) qualifier.

The script below uses the `maChoice` enum within an [input.enum()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.enum) call to create a _dropdown_ input in the “Settings/Inputs” tab that displays all the field titles. The `maInput` value represents the member of the enum that corresponds to the user-selected title. The script uses the selected member within a [switch](https://www.tradingview.com/pine-script-reference/v6/#kw_switch) structure to determine the built-in moving average it calculates:

``//@version=6   indicator("Enum types demo", overlay = true)      //@enum       An enumeration of named values for moving average selection.   //@field sma  Selects a Simple Moving Average.   //@field ema  Selects an Exponential Moving Average.   //@field wma  Selects a Weighted Moving Average.   //@field hma  Selects a Hull Moving Average.   enum maChoice       sma  = "Simple Moving Average"       ema  = "Exponential Moving Average"       wma  = "Weighted Moving Average"       hma  = "Hull Moving Average"      //@variable The `maChoice` member representing a selected moving average name.   maChoice maInput = input.enum(maChoice.sma, "Moving average type")   //@variable The length of the moving average.   int lengthInput = input.int(20, "Length", 1, 4999)      //@variable The moving average selected by the `maInput`.    float selectedMA = switch maInput       maChoice.sma => ta.sma(close, lengthInput)       maChoice.ema => ta.ema(close, lengthInput)       maChoice.wma => ta.wma(close, lengthInput)       maChoice.hma => ta.hma(close, lengthInput)      // Plot the `selectedMA`.   plot(selectedMA, "Selected moving average", color.teal, 3)   ``

See the [Enums](https://www.tradingview.com/pine-script-docs/language/enums/) page and the [Enum input](https://www.tradingview.com/pine-script-docs/concepts/inputs/#enum-input) section of the [Inputs](https://www.tradingview.com/pine-script-docs/concepts/inputs/) page to learn more about using enums and enum inputs.

### [void](https://www.tradingview.com/pine-script-docs/language/type-system/#void)

There is a “void” type in Pine Script™. Functions having only side-effects and returning no usable result return the “void” type. An example of such a function is [alert()](https://www.tradingview.com/pine-script-reference/v6/#fun_alert); it does something (triggers an alert event), but it returns no usable value.

Scripts cannot use “void” results in expressions or assign them to variables. No `void` keyword exists in Pine Script™ since one cannot declare a variable of the “void” type.

## [\`na\` value](https://www.tradingview.com/pine-script-docs/language/type-system/#na-value)

There is a special value in Pine Script™ called [na](https://www.tradingview.com/pine-script-reference/v6/#var_na), which is an acronym for _not available_. We use [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) to represent an undefined value from a variable or expression. It is similar to `null` in Java and `None` in Python.

Scripts can automatically cast [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) values to almost any type. However, in some cases, the compiler cannot infer the type associated with an [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) value because more than one type-casting rule may apply. For example:

`// Compilation error!   myVar = na   `

The above line of code causes a compilation error because the compiler cannot determine the nature of the `myVar` variable, i.e., whether the variable will reference numeric values for plotting, string values for setting text in a label, or other values for some other purpose later in the script’s execution.

To resolve such errors, we must explicitly declare the type associated with the variable. Suppose the `myVar` variable will reference “float” values in subsequent script iterations. We can resolve the error by declaring the variable with the [float](https://www.tradingview.com/pine-script-reference/v6/#type_float) keyword:

or by explicitly casting the [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) value to the “float” type via the [float()](https://www.tradingview.com/pine-script-reference/v6/#fun_float) function:

To test if the value from a variable or expression is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na), we call the [na()](https://www.tradingview.com/pine-script-reference/v6/#fun_na) function, which returns `true` if the value is undefined. For example:

``//@variable Is 0 if the `myVar` is `na`, `close` otherwise.   float myClose = na(myVar) ? 0 : close   ``

Do not use the `==` comparison operator to test for [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) values, as scripts cannot determine the equality of an undefined value:

``//@variable Returns the `close` value. The script cannot compare the equality of `na` values, as they're undefined.   float myClose = myVar == na ? 0 : close   ``

Best coding practices often involve handling [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) values to prevent undefined values in calculations.

We can ensure the expression also returns an actionable value on the first bar by replacing the undefined past value with a value from the current bar. This line of code uses the [nz()](https://www.tradingview.com/pine-script-reference/v6/#fun_nz) function to replace the past bar’s [close](https://www.tradingview.com/pine-script-reference/v6/#var_close) with the current bar’s [open](https://www.tradingview.com/pine-script-reference/v6/#var_open) when the value is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na):

``//@variable Is `true` when the `close` exceeds the last bar's `close` (or the current `open` if the value is `na`).   bool risingClose = close > nz(close[1], open)   ``

Protecting scripts against [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) instances helps to prevent undefined values from propagating in a calculation’s results. For example, this script declares an `allTimeHigh` variable on the first bar. It then uses the [math.max()](https://www.tradingview.com/pine-script-reference/v6/#fun_math.max) between the `allTimeHigh` and the bar’s [high](https://www.tradingview.com/pine-script-reference/v6/#var_high) to update the `allTimeHigh` throughout its execution:

``//@version=6   indicator("na protection demo", overlay = true)      //@variable The result of calculating the all-time high price with an initial value of `na`.   var float allTimeHigh = na      // Reassign the value of the `allTimeHigh`.   // Returns `na` on all bars because `math.max()` can't compare the `high` to an undefined value.   allTimeHigh := math.max(allTimeHigh, high)      plot(allTimeHigh) // Plots `na` on all bars.   ``

This script plots a value of [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) on all bars, as we have not included any [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) protection in the code. To fix the behavior and plot the intended result (i.e., the all-time high of the chart’s prices), we can use [nz()](https://www.tradingview.com/pine-script-reference/v6/#fun_nz) to replace [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) values in the `allTimeHigh` series:

``//@version=6   indicator("na protection demo", overlay = true)      //@variable The result of calculating the all-time high price with an initial value of `na`.   var float allTimeHigh = na      // Reassign the value of the `allTimeHigh`.   // We've used `nz()` to prevent the initial `na` value from persisting throughout the calculation.   allTimeHigh := math.max(nz(allTimeHigh), high)      plot(allTimeHigh)   ``

## [Type templates](https://www.tradingview.com/pine-script-docs/language/type-system/#type-templates)

Type templates specify the data types that collections ([arrays](https://www.tradingview.com/pine-script-docs/language/arrays/), [matrices](https://www.tradingview.com/pine-script-docs/language/matrices/), and [maps](https://www.tradingview.com/pine-script-docs/language/maps/)) can contain.

Templates for [arrays](https://www.tradingview.com/pine-script-docs/language/arrays/) and [matrices](https://www.tradingview.com/pine-script-docs/language/matrices/) consist of a single type identifier surrounded by angle brackets, e.g., `<int>`, `<label>`, and `<PivotPoint>` (where `PivotPoint` is a [user-defined type (UDT)](https://www.tradingview.com/pine-script-docs/language/type-system/#user-defined-types)).

Templates for [maps](https://www.tradingview.com/pine-script-docs/language/maps/) consist of two type identifiers enclosed in angle brackets, where the first specifies the type of _keys_ in each key-value pair, and the second specifies the _value_ type. For example, `<string, float>` is a type template for a map that holds `string` keys and `float` values.

Users can construct type templates from:

-   Fundamental types: [int](https://www.tradingview.com/pine-script-docs/language/type-system/#int), [float](https://www.tradingview.com/pine-script-docs/language/type-system/#float), [bool](https://www.tradingview.com/pine-script-docs/language/type-system/#bool), [color](https://www.tradingview.com/pine-script-docs/language/type-system/#color), and [string](https://www.tradingview.com/pine-script-docs/language/type-system/#string)
-   The following special types: [line](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types), [linefill](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types), [box](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types), [polyline](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types), [label](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types), [table](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types), and [chart.point](https://www.tradingview.com/pine-script-docs/language/type-system/#chart-points)
-   [User-defined types (UDTs)](https://www.tradingview.com/pine-script-docs/language/type-system/#user-defined-types)
-   [Enum types](https://www.tradingview.com/pine-script-docs/language/type-system/#enum-types)

Note that:

-   [Maps](https://www.tradingview.com/pine-script-docs/language/maps/) can use any of these types as _values_, but they can only accept fundamental types or [enum types](https://www.tradingview.com/pine-script-docs/language/type-system/#enum-types) as _keys_.

Scripts use type templates to declare variables that reference collections, and when creating new collection instances. For example:

``//@version=6   indicator("Type templates demo")      //@variable A variable initially assigned to `na` that accepts arrays of "int" values.   array<int> intArray = na   //@variable An empty matrix that holds "float" values.   floatMatrix = matrix.new<float>()   //@variable An empty map that holds "string" keys and "color" values.   stringColorMap = map.new<string, color>()   ``

## [Type casting](https://www.tradingview.com/pine-script-docs/language/type-system/#type-casting)

Pine Script™ includes an automatic type-casting mechanism that _casts_ (converts) **“int”** values to **“float”** when necessary. Variables or expressions requiring “float” values can also use “int” values because any integer can be represented as a floating point number with its fractional part equal to 0.

It’s sometimes necessary to cast one type to another when auto-casting rules do not suffice. For such cases, the following type-casting functions are available: [int()](https://www.tradingview.com/pine-script-reference/v6/#fun_int), [float()](https://www.tradingview.com/pine-script-reference/v6/#fun_float), [bool()](https://www.tradingview.com/pine-script-reference/v6/#fun_bool), [color()](https://www.tradingview.com/pine-script-reference/v6/#fun_color), [string()](https://www.tradingview.com/pine-script-reference/v6/#fun_string), [line()](https://www.tradingview.com/pine-script-reference/v6/#fun_line), [linefill()](https://www.tradingview.com/pine-script-reference/v6/#fun_linefill), [label()](https://www.tradingview.com/pine-script-reference/v6/#fun_label), [box()](https://www.tradingview.com/pine-script-reference/v6/#fun_box), and [table()](https://www.tradingview.com/pine-script-reference/v6/#fun_table).

The example below shows a code that tries to use a “const float” value as the `length` argument in the [ta.sma()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.sma) function call. The script will fail to compile, as it cannot automatically convert the “float” value to the required “int” type:

``//@version=6   indicator("Explicit casting demo", overlay = true)      //@variable The length of the SMA calculation. Qualified as "const float".   float LENGTH = 10.0      float sma = ta.sma(close, LENGTH) // Compilation error. The `length` parameter requires an "int" value.      plot(sma)   ``

The code raises the following error: _“Cannot call ‘ta.sma’ with argument ‘length’=‘LENGTH’. An argument of ‘const float’ type was used but a ‘series int’ is expected.”_

The compiler is telling us that the code is using a “float” value where an “int” is required. There is no auto-casting rule to cast a “float” to an “int”, so we must do the job ourselves. In this version of the code, we’ve used the [int()](https://www.tradingview.com/pine-script-reference/v6/#fun_int) function to explicitly convert our “float” `LENGTH` value to the “int” type within the [ta.sma()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.sma) call:

``//@version=6   indicator("explicit casting demo")      //@variable The length of the SMA calculation. Qualified as "const float".   float LENGTH = 10.0      float sma = ta.sma(close, int(LENGTH)) // Compiles successfully since we've converted the `LENGTH` to "int".      plot(sma)   ``

Explicit type casting is also handy when declaring variables assigned to [na](https://www.tradingview.com/pine-script-reference/v6/#var_na), as explained in the [previous section](https://www.tradingview.com/pine-script-docs/language/type-system/#na-value).

For example, once could explicitly declare a variable with a value of [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) as a “label” type in either of the following, equivalent ways:

``// Explicitly specify that the variable references "label" objects:   label myLabel = na      // Explicitly cast the `na` value to the "label" type:   myLabel = label(na)   ``

## [Tuples](https://www.tradingview.com/pine-script-docs/language/type-system/#tuples)

A _tuple_ is a comma-separated set of expressions enclosed in brackets. When a function, [method](https://www.tradingview.com/pine-script-docs/language/methods/), or other local block returns more than one value, scripts return those values in the form of a tuple.

For example, the following [user-defined function](https://www.tradingview.com/pine-script-docs/language/user-defined-functions/) returns the sum and product of two “float” values:

``//@function Calculates the sum and product of two values.   calcSumAndProduct(float a, float b) =>       //@variable The sum of `a` and `b`.       float sum = a + b       //@variable The product of `a` and `b`.       float product = a * b       // Return a tuple containing the `sum` and `product`.       [sum, product]   ``

When we call this function later in the script, we use a _tuple declaration_ to declare multiple variables corresponding to the values returned by the function call:

``// Declare a tuple containing the sum and product of the `high` and `low`, respectively.   [hlSum, hlProduct] = calcSumAndProduct(high, low)   ``

Keep in mind that unlike declaring single variables, we cannot explicitly define the types the tuple’s variables (`hlSum` and `hlProduct` in this case), will contain. The compiler automatically infers the types associated with the variables in a tuple.

In the above example, the resulting tuple contains values of the same type (“float”). However, it’s important to note that tuples can contain values of _multiple types_. For example, the `chartInfo()` function below returns a tuple containing “int”, “float”, “bool”, “color”, and “string” values:

``//@function Returns information about the current chart.   chartInfo() =>       //@variable The first visible bar's UNIX time value.       int firstVisibleTime = chart.left_visible_bar_time       //@variable The `close` value at the `firstVisibleTime`.       float firstVisibleClose = ta.valuewhen(ta.cross(time, firstVisibleTime), close, 0)       //@variable Is `true` when using a standard chart type, `false` otherwise.       bool isStandard = chart.is_standard       //@variable The foreground color of the chart.       color fgColor = chart.fg_color       //@variable The ticker ID of the current chart.       string symbol = syminfo.tickerid       // Return a tuple containing the values.        [firstVisibleTime, firstVisibleClose, isStandard, fgColor, symbol]   ``

Tuples are especially handy for requesting multiple values in one [request.security()](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security) call.

For instance, this `roundedOHLC()` function returns a tuple containing OHLC values rounded to the nearest prices that are divisible by the symbol’s [minimum tick](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.mintick) value. We call this function as the `expression` argument in [request.security()](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security) to request a tuple containing daily OHLC values:

`//@function Returns a tuple of OHLC values, rounded to the nearest tick.   roundedOHLC() =>       [math.round_to_mintick(open), math.round_to_mintick(high), math.round_to_mintick(low), math.round_to_mintick(close)]      [op, hi, lo, cl] = request.security(syminfo.tickerid, "D", roundedOHLC())   `

We can also achieve the same result by directly passing a tuple of rounded values as the `expression` in the [request.security()](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security) call:

`[op, hi, lo, cl] = request.security(        syminfo.tickerid, "D",         [math.round_to_mintick(open), math.round_to_mintick(high), math.round_to_mintick(low), math.round_to_mintick(close)]    )   `

Local blocks of [conditional structures](https://www.tradingview.com/pine-script-docs/language/conditional-structures/), including [if](https://www.tradingview.com/pine-script-reference/v6/#kw_if) and [switch](https://www.tradingview.com/pine-script-reference/v6/#kw_switch) statements, can return tuples. For example:

`[v1, v2] = if close > open       [high, close]   else       [close, low]   `

and:

`[v1, v2] = switch    close > open => [high, close]   =>              [close, low]   `

However, ternaries cannot contain tuples, as the return values in a ternary statement are not considered local blocks:

`// Not allowed.   [v1, v2] = close > open ? [high, close] : [close, low]   `

Note that all items within a tuple returned from a function are qualified as “simple” or “series”, depending on its contents. If a tuple contains a “series” value, all other elements within the tuple will also adopt the “series” qualifier. For example:

``//@version=6   indicator("Qualified types in tuples demo")      getParameters(float source, simple int length) =>       // The second item in the tuple becomes a "series" if `source` is a "series"        // because all returned tuple elements adopt the strongest qualifier.        [source, length]      // Although the `length` argument is a "const int", the `len` variable is a "series" because `src` is a "series".   [src, len] = getParameters(close, 20)      // Causes a compilation error because `ta.ema()` requires a "simple int" `length` argument.    plot(ta.ema(src, len))   ``