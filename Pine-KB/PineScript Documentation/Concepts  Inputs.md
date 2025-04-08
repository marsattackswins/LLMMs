## [Introduction](https://www.tradingview.com/pine-script-docs/concepts/inputs/#introduction)

Inputs receive values that users can change from a script’s “Settings/Inputs” tab. By utilizing inputs, programmers can write scripts that users can more easily adapt to their preferences.

The following script plots a 20-period [simple moving average (SMA)](https://www.tradingview.com/support/solutions/43000502589) using [ta.sma(close, 20)](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.sma). While it is straightforward to write, the code is not very _flexible_ because the function call uses specific `source` and `length` arguments that users cannot change without modifying the code:

`//@version=6   indicator("MA", "", true)   plot(ta.sma(close, 20))   `

If we write our script this way instead, it becomes much more flexible, as users can select the `source` and the `length` values they want to use from the “Settings/Inputs” tab without changing the source code:

`//@version=6   indicator("MA", "", true)   sourceInput = input(close, "Source")   lengthInput = input(20, "Length")   plot(ta.sma(sourceInput, lengthInput))   `

Inputs are only accessible while a script runs on a chart. Users can access script inputs from the “Settings” dialog box. To open this dialog, users can:

-   Double-click on the name of an on-chart indicator
-   Right-click on the script’s name and choose the “Settings” item from the dropdown menu
-   Choose the “Settings” item from the “More” menu icon (three dots) that appears when hovering over the indicator’s name on the chart
-   Double-click on the indicator’s name from the Data Window (fourth icon down to the right of the chart)

The “Settings” dialog always contains the “Style” and “Visibility” tabs, which allow users to specify their preferences about the script’s visuals and the chart timeframes that can display its outputs.

When a script contains calls to `input.*()` functions, an “Inputs” tab also appears in the “Settings” dialog box.

![image](https://www.tradingview.com/pine-script-docs/_astro/Inputs-Introduction-1.CNd-sZxz_2qJffB.webp)

Scripts process inputs when users add them to the chart or change the values in the script’s “Settings/Inputs” tab. Any changes to a script’s inputs prompt it to re-execute across all available data using the new specified values.

## [Input functions](https://www.tradingview.com/pine-script-docs/concepts/inputs/#input-functions)

Pine Script™ features the following input functions:

-   [input()](https://www.tradingview.com/pine-script-reference/v6/#fun_input)
-   [input.int()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.int)
-   [input.float()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.float)
-   [input.bool()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.bool)
-   [input.color()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.color)
-   [input.string()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.string)
-   [input.text\_area()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.text_area)
-   [input.timeframe()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.timeframe)
-   [input.symbol()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.symbol)
-   [input.price()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.price)
-   [input.source()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.source)
-   [input.session()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.session)
-   [input.time()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.time)
-   [input.enum()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.enum)

Scripts create input _widgets_ in the “Inputs” tab that accept different types of inputs based on their `input.*()` function calls. By default, each input appears on a new line of the “Inputs” tab in the order of the `input.*()` calls. Programmers can also organize inputs in different ways by using the `input.*()` functions’ `group` and `inline` parameters. See [this section](https://www.tradingview.com/pine-script-docs/concepts/inputs/#input-function-parameters) below for more information.

Our [Style guide](https://www.tradingview.com/pine-script-docs/writing/style-guide/#style-guide) recommends placing `input.*()` calls at the beginning of the script.

Input functions typically contain several parameters that allow programmers to define their default values, value limits, their organization in the “Inputs” tab, and other properties.

Since an `input.*()` call is simply another function call in Pine Script™, programmers can combine them with [arithmetic](https://www.tradingview.com/pine-script-docs/language/operators/#arithmetic-operators), [comparison](https://www.tradingview.com/pine-script-docs/language/operators/#comparison-operators), [logical](https://www.tradingview.com/pine-script-docs/language/operators/#logical-operators), and [ternary](https://www.tradingview.com/pine-script-docs/language/operators/#-ternary-operator) operators to assign expressions to variables. This simple script compares the result from a call to [input.string()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.string) to the “On” string and assigns the result to the `plotDisplayInput` variable. This variable is of the “input bool” type because the [\==](https://www.tradingview.com/pine-script-reference/v6/#op_==) operator returns a “bool” value:

``//@version=6   indicator("Input in an expression`", "", true)   bool plotDisplayInput = input.string("On", "Plot Display", options = ["On", "Off"]) == "On"   plot(plotDisplayInput ? close : na)   ``

All values returned by `input.*()` functions except “source” ones are “input” qualified values. See our User Manual’s section on [type qualifiers](https://www.tradingview.com/pine-script-docs/language/type-system/#qualifiers) for more information.

## [Input function parameters](https://www.tradingview.com/pine-script-docs/concepts/inputs/#input-function-parameters)

The parameters common to all input functions are: `defval`, `title`, `tooltip`, `inline`, `group`, and `display`. Some input functions also include other parameters: `options`, `minval`, `maxval`, `step` and `confirm`.

All these parameters expect “const” arguments. The only exceptions are for the `defval` and `options` parameters of the [source](https://www.tradingview.com/pine-script-docs/concepts/inputs/#source-input) and [enum](https://www.tradingview.com/pine-script-docs/concepts/inputs/#enum-input) inputs, as [input.source()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.source) uses “series float” value, and [input.enum()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.enum) uses _members_ of an [enum type](https://www.tradingview.com/pine-script-docs/language/type-system/#qualifiers).

Since `input.*()` parameters accept “const” arguments in most cases and the “input” and other [qualifiers](https://www.tradingview.com/pine-script-docs/language/type-system/#qualifiers) are stronger than “const”, it follows that one cannot use the result from one `input.*()` call as an argument in another `input.*()` call.

Let’s go over each parameter:

-   `defval` is the first parameter of all input functions. It is the default value that appears in the input widget. It requires an argument of the type of input value that the function applies to.
-   `title` requires a “const string” argument. It is the field’s label.
-   `tooltip` requires a “const string” argument. When the parameter is used, a question mark icon will appear to the right of the field. When users hover over it, the tooltip’s text will appear. Note that if multiple input fields are grouped on one line using `inline`, the tooltip will always appear to the right of the rightmost field, and display the text of the last `tooltip` argument used in the line. Newlines (`\n`) are supported in the argument string.
-   `inline` requires a “const string” argument. Using the same argument for the parameter in multiple `input.*()` calls will group their input widgets on the same line. There is a limit to the width the “Inputs” tab will expand, so a limited quantity of input fields can be fitted on one line. Using one `input.*()` call with a unique argument for `inline` has the effect of bringing the input field left, immediately after the label, foregoing the default left-alignment of all input fields used when no `inline` argument is used.
-   `group` requires a “const string” argument. Use it to group any number of inputs in an organized section. The string used as the `group` argument becomes the section’s heading. All `input.*()` calls to be grouped together must use the same string for their `group` argument.
-   `options` requires a comma-separated list of elements enclosed in square brackets (e.g., `["ON", "OFF"]`, `[1, 2, 3]`, `[myEnum.On, myEnum.Off]`). The input uses the specified elements as menu selections in its resulting dropdown widget. Users can only select one menu item at a time. When supplying an `options` list, the `defval` value must be one of the list’s elements. Inputs that allow `minval`, `maxval`, or `step` parameters cannot use those parameters and the `options` parameter simultaneously.
-   `minval` requires a “const int/float” argument, depending on the type of the `defval` value. It is the minimum valid value for the input field.
-   `maxval` requires a “const int/float” argument, depending on the type of the `defval` value. It is the maximum valid value for the input field.
-   `step` is the increment by which the field’s value will move when the widget’s up/down arrows are used.
-   `confirm` requires a “const bool” (`true` or `false`) argument. This parameter affects the behavior of the script when it is added to a chart. `input.*()` calls using `confirm = true` will cause the “Settings/Inputs” tab to popup when the script is added to the chart. `confirm` is useful to ensure that users configure a particular field.

The `minval`, `maxval` and `step` parameters are only present in the signature of the [input.int()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.int) and [input.float()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.float) functions.

## [Input types](https://www.tradingview.com/pine-script-docs/concepts/inputs/#input-types)

The next sections explain what each input function does. As we proceed, we will explore the different ways you can use input functions and organize their display.

### [Generic input](https://www.tradingview.com/pine-script-docs/concepts/inputs/#generic-input)

[input()](https://www.tradingview.com/pine-script-reference/v6/#fun_input) is a simple, generic function that supports the fundamental Pine Script™ types: “int”, “float”, “bool”, “color” and “string”. It also supports “source” inputs, which are price-related values such as [close](https://www.tradingview.com/pine-script-reference/v6/#var_close), [hl2](https://www.tradingview.com/pine-script-reference/v6/#hl2), [hlc3](https://www.tradingview.com/pine-script-reference/v6/#var_hlc3), and [hlcc4](https://www.tradingview.com/pine-script-reference/v6/#var_hlcc4), or which can be used to receive the output value of another script.

Its signature is:

```
input(defval, title, tooltip, inline, group) → input int/float/bool/color/string | series float
```

The function automatically detects the type of input by analyzing the type of the `defval` argument used in the function call. This script shows all the supported types and the qualified type returned by the function when used with `defval` arguments of different types:

``//@version=6   indicator("`input()`", "", true)   a = input(1, "input int")   b = input(1.0, "input float")   c = input(true, "input bool")   d = input(color.orange, "input color")   e = input("1", "input string")   f = input(close, "series float")   plot(na)   ``

![image](https://www.tradingview.com/pine-script-docs/_astro/Inputs-InputTypes-01.Cq1mAVhd_Z1FJl78.webp)

### [Integer input](https://www.tradingview.com/pine-script-docs/concepts/inputs/#integer-input)

Two signatures exist for the [input.int()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.int) function; one when `options` is not used, the other when it is:

```
input.int(defval, title, minval, maxval, step, tooltip, inline, group, confirm) → input intinput.int(defval, title, options, tooltip, inline, group, confirm) → input int
```

This call uses the `options` parameter to propose a pre-defined list of lengths for the MA:

`//@version=6   indicator("MA", "", true)   maLengthInput = input.int(10, options = [3, 5, 7, 10, 14, 20, 50, 100, 200])   ma = ta.sma(close, maLengthInput)   plot(ma)   `

This one uses the `minval` parameter to limit the length:

`//@version=6   indicator("MA", "", true)   maLengthInput = input.int(10, minval = 2)   ma = ta.sma(close, maLengthInput)   plot(ma)   `

The version with the `options` list uses a dropdown menu for its widget. When the `options` parameter is not used, a simple input widget is used to enter the value:

![image](https://www.tradingview.com/pine-script-docs/_astro/Inputs-InputTypes-02.CZ6pYgBC_2jU4nO.webp)

### [Float input](https://www.tradingview.com/pine-script-docs/concepts/inputs/#float-input)

Two signatures exist for the [input.float()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.float) function; one when `options` is not used, the other when it is:

```
input.float(defval, title, minval, maxval, step, tooltip, inline, group, confirm) → input intinput.float(defval, title, options, tooltip, inline, group, confirm) → input int
```

Here, we use a “float” input for the factor used to multiple the standard deviation, to calculate Bollinger Bands:

`//@version=6   indicator("MA", "", true)   maLengthInput = input.int(10, minval = 1)   bbFactorInput = input.float(1.5, minval = 0, step = 0.5)   ma      = ta.sma(close, maLengthInput)   bbWidth = ta.stdev(ma, maLengthInput) * bbFactorInput   bbHi    = ma + bbWidth   bbLo    = ma - bbWidth   plot(ma)   plot(bbHi, "BB Hi", color.gray)   plot(bbLo, "BB Lo", color.gray)   `

The input widgets for floats are similar to the ones used for integer inputs:

![image](https://www.tradingview.com/pine-script-docs/_astro/Inputs-InputTypes-03.3O4JqasJ_ALMjG.webp)

### [Boolean input](https://www.tradingview.com/pine-script-docs/concepts/inputs/#boolean-input)

Let’s continue to develop our script further, this time by adding a boolean input to allow users to toggle the display of the BBs:

![image](https://www.tradingview.com/pine-script-docs/_astro/Inputs-InputTypes-04.BsSpKR3Q_Za4RlV.webp)

`//@version=6   indicator("MA", "", true)   maLengthInput = input.int(10,    "MA length", minval = 1)   bbFactorInput = input.float(1.5, "BB factor", inline = "01", minval = 0, step = 0.5)   showBBInput   = input.bool(true, "Show BB",   inline = "01")   ma      = ta.sma(close, maLengthInput)   bbWidth = ta.stdev(ma, maLengthInput) * bbFactorInput   bbHi    = ma + bbWidth   bbLo    = ma - bbWidth   plot(ma, "MA", color.aqua)   plot(showBBInput ? bbHi : na, "BB Hi", color.gray)   plot(showBBInput ? bbLo : na, "BB Lo", color.gray)   `

Note that:

-   We have added an input using [input.bool()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.bool) to set the value of `showBBInput`.
-   We use the `inline` parameter in that input and in the one for `bbFactorInput` to bring them on the same line. We use `"01"` for its argument in both cases. That is how the Pine Script™ compiler recognizes that they belong on the same line. The particular string used as an argument is unimportant and does not appear anywhere in the “Inputs” tab; it is only used to identify which inputs go on the same line.
-   We have vertically aligned the `title` arguments of our `input.*()` calls to make them easier to read.
-   We use the `showBBInput` variable in our two [plot()](https://www.tradingview.com/pine-script-reference/v6/#fun_plot) calls to plot conditionally. When the user unchecks the checkbox of the `showBBInput` input, the variable’s value becomes `false`. When that happens, our [plot()](https://www.tradingview.com/pine-script-reference/v6/#fun_plot) calls plot the [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) value, which displays nothing. We use `true` as the default value of the input, so the BBs plot by default.
-   Because we use the `inline` parameter for the `bbFactorInput` variable, its input field in the “Inputs” tab does not align vertically with that of `maLengthInput`, which doesn’t use `inline`.

### [Color input](https://www.tradingview.com/pine-script-docs/concepts/inputs/#color-input)

As explained in [this](https://www.tradingview.com/pine-script-docs/concepts/colors/#maintaining-automatic-color-selectors) section of the [Colors](https://www.tradingview.com/pine-script-docs/concepts/colors/) page, selecting the colors of a script’s outputs via the “Settings/Style” tab is not always possible. In the case where one cannot choose colors from the “Style” tab, programmers can create color inputs with the [input.color()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.color) function to allow color customization from the “Settings/Inputs” tab.

Suppose we wanted to plot our BBs with a ligther transparency when the [high](https://www.tradingview.com/pine-script-reference/v6/#var_high) and [low](https://www.tradingview.com/pine-script-reference/v6/#var_low) values are higher/lower than the BBs. We can use a code like this to create the colors:

`bbHiColor = color.new(color.gray, high > bbHi ? 60 : 0)   bbLoColor = color.new(color.gray, low  < bbLo ? 60 : 0)   `

When using dynamic (“series”) color components like the `transp` arguments in the above code, the color widgets in the “Settings/Style” tab will no longer appear. Let’s create our own input for color selection, which will appear in the “Settings/Inputs” tab:

![image](https://www.tradingview.com/pine-script-docs/_astro/Inputs-InputTypes-05.D_uuADST_ZadKOP.webp)

`//@version=6   indicator("MA", "", true)   maLengthInput = input.int(10,           "MA length", inline = "01", minval = 1)   maColorInput  = input.color(color.aqua, "",          inline = "01")   bbFactorInput = input.float(1.5,        "BB factor", inline = "02", minval = 0, step = 0.5)   bbColorInput  = input.color(color.gray, "",          inline = "02")   showBBInput   = input.bool(true,        "Show BB",   inline = "02")   ma      = ta.sma(close, maLengthInput)   bbWidth = ta.stdev(ma, maLengthInput) * bbFactorInput   bbHi    = ma + bbWidth   bbLo    = ma - bbWidth   bbHiColor = color.new(bbColorInput, high > bbHi ? 60 : 0)   bbLoColor = color.new(bbColorInput, low  < bbLo ? 60 : 0)   plot(ma, "MA", maColorInput)   plot(showBBInput ? bbHi : na, "BB Hi", bbHiColor, 2)   plot(showBBInput ? bbLo : na, "BB Lo", bbLoColor, 2)   `

Note that:

-   We have added two calls to [input.color()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.color) to gather the values of the `maColorInput` and `bbColorInput` variables. We use `maColorInput` directly in the `plot(ma, "MA", maColorInput)` call, and we use `bbColorInput` to build the `bbHiColor` and `bbLoColor` variables, which modulate the transparency using the position of price relative to the BBs. We use a conditional value for the `transp` value we call [color.new()](https://www.tradingview.com/pine-script-reference/v6/#fun_color.new) with, to generate different transparencies of the same base color.
-   We do not use a `title` argument for our new color inputs because they are on the same line as other inputs allowing users to understand to which plots they apply.
-   We have reorganized our `inline` arguments so they reflect the fact we have inputs grouped on two distinct lines.

### [Timeframe input](https://www.tradingview.com/pine-script-docs/concepts/inputs/#timeframe-input)

The [input.timeframe()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.timeframe) function creates a dropdown input containing _timeframe choices_. It returns a “string” value representing the selected timeframe in our [specification format](https://www.tradingview.com/pine-script-docs/concepts/timeframes/#timeframe-string-specifications), which scripts can use in `request.*()` calls to retrieve data from user-selected timeframes.

The following script uses [request.security()](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security) on each bar to fetch the value of a [ta.sma()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.sma) call from a user-specified higher timeframe, then plots the result on the chart:

![image](https://www.tradingview.com/pine-script-docs/_astro/Inputs-InputTypes-06.BvUY6GL6_Z14lcBY.webp)

``//@version=6   indicator("Timeframe input demo", "MA", true)      //@variable The timeframe of the requested data.   string tfInput = input.timeframe("1D", "Timeframe")      // Get the typical number of seconds in the chart's timeframe and the `tfInput` timeframe.    int chartSeconds = timeframe.in_seconds()   int tfSeconds    = timeframe.in_seconds(tfInput)   // Raise an error if the `tfInput` is a lower timeframe.   if tfSeconds < chartSeconds       runtime.error("The 'Timeframe' input must represent a timeframe higher than or equal to the chart's.")      //@variable The offset of the requested expression. 1 when `tfInput` is a higher timeframe, 0 otherwise.    int offset = chartSeconds == tfSeconds ? 0 : 1   //@variable The 20-bar SMA of `close` prices for the current symbol from the `tfInput` timeframe.   float maHTF = request.security(syminfo.tickerid, tfInput, ta.sma(close, 20)[offset], lookahead = barmerge.lookahead_on)      // Plot the `maHTF` value.   plot(maHTF, "MA", color.aqua)   ``

Note that:

-   By default, the [input.timeframe()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.timeframe) call’s dropdown contains options for the chart’s timeframe and all timeframes listed in the chart’s “Time interval” menu. To restrict the available options to specific preset timeframes, pass a [tuple](https://www.tradingview.com/pine-script-docs/language/type-system/#tuples) of timeframe strings to the function’s `options` parameter.
-   This script raises a [runtime error](https://www.tradingview.com/pine-script-reference/v6/#fun_runtime.error) if the estimated [number of seconds](https://www.tradingview.com/pine-script-reference/v6/#fun_timeframe.in_seconds) in the `tfInput` timeframe is _less_ than the number of seconds in the main timeframe, preventing it from requesting lower-timeframe data. See [this section](https://www.tradingview.com/pine-script-docs/concepts/other-timeframes-and-data/#higher-timeframes) of the [Other timeframes and data](https://www.tradingview.com/pine-script-docs/concepts/other-timeframes-and-data/) page to learn more.
-   The [request.security()](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security) call uses [barmerge.lookahead\_on](https://www.tradingview.com/pine-script-reference/v6/#const_barmerge.lookahead_on) as its `lookahead` argument, and it offsets the `expression` argument by one bar when the `tfInput` represents a _higher timeframe_ to [avoid repainting](https://www.tradingview.com/pine-script-docs/concepts/other-timeframes-and-data/#avoiding-repainting).

### [Symbol input](https://www.tradingview.com/pine-script-docs/concepts/inputs/#symbol-input)

The [input.symbol()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.symbol) function creates an input widget that mirrors the chart’s “Symbol Search” widget. It returns a “string” _ticker identifier_ representing the chosen symbol and exchange, which scripts can use in `request.*()` calls to retrieve data from other contexts.

The script below uses [request.security()](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security) to retrieve the value of a [ta.rsi()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.rsi) call evaluated on a user-specified symbol’s prices. It plots the requested result on the chart in a separate pane:

``//@version=6   indicator("Symbol input demo", "RSI")      //@variable The ticker ID of the requested data. By default, it is an empty "string", which specifies the main symbol.    string symbolInput = input.symbol("", "Symbol")      //@variable The 14-bar RSI of `close` prices for the `symbolInput` symbol on the script's main timeframe.    float symbolRSI = request.security(symbolInput, timeframe.period, ta.rsi(close, 14))      // Plot the `symbolRSI` value.   plot(symbolRSI, "RSI", color.aqua)   ``

Note that:

-   The `defval` argument in the [input.symbol()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.symbol) call is an empty “string”. When the [request.security()](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security) call in this example uses this default value as the `symbol` argument, it calculates the RSI using the _chart symbol’s_ data. If the user wants to revert to the chart’s symbol after choosing another symbol, they can select “Reset settings” from the “Defaults” dropdown at the bottom of the “Settings” menu.

### [Session input](https://www.tradingview.com/pine-script-docs/concepts/inputs/#session-input)

Session inputs are useful to gather start-stop values for periods of time. The [input.session()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.session) built-in function creates an input widget allowing users to specify the beginning and end time of a session. Selections can be made using a dropdown menu, or by entering time values in “hh:mm” format.

The value returned by [input.session()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.session) is a valid string in session format. See the manual’s page on [sessions](https://www.tradingview.com/pine-script-docs/concepts/sessions/) for more information.

Session information can also contain information on the days where the session is valid. We use an [input.string()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.string) function call here to input that day information:

`//@version=6   indicator("Session input", "", true)   string sessionInput = input.session("0600-1700", "Session")   string daysInput = input.string("1234567", tooltip = "1 = Sunday, 7 = Saturday")   sessionString = sessionInput + ":" + daysInput   inSession = not na(time(timeframe.period, sessionString))   bgcolor(inSession ? color.silver : na)   `

Note that:

-   This script proposes a default session of “0600-1700”.
-   The [input.string()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.string) call uses a tooltip to provide users with help on the format to use to enter day information.
-   A complete session string is built by concatenating the two strings the script receives as inputs.
-   We explicitly declare the type of our two inputs with the [string](https://www.tradingview.com/pine-script-reference/v6/#type_string) keyword to make it clear those variables will contain a string.
-   We detect if the chart bar is in the user-defined session by calling [time()](https://www.tradingview.com/pine-script-reference/v6/#fun_time) with the session string. If the current bar’s [time](https://www.tradingview.com/pine-script-reference/v6/#var_time) value (the time at the bar’s [open](https://www.tradingview.com/pine-script-reference/v6/#var_open)) is not in the session, [time()](https://www.tradingview.com/pine-script-reference/v6/#fun_time) returns [na](https://www.tradingview.com/pine-script-reference/v6/#var_na), so `inSession` will be `true` whenever [time()](https://www.tradingview.com/pine-script-reference/v6/#fun_time) returns a value that is not [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).

![image](https://www.tradingview.com/pine-script-docs/_astro/Inputs-InputTypes-07.DBQQqMr6_15fqiC.webp)

### [Source input](https://www.tradingview.com/pine-script-docs/concepts/inputs/#source-input)

Source inputs are useful to provide a selection of two types of sources:

-   Price values, namely: [open](https://www.tradingview.com/pine-script-reference/v6/#var_open), [high](https://www.tradingview.com/pine-script-reference/v6/#var_high), [low](https://www.tradingview.com/pine-script-reference/v6/#var_low), [close](https://www.tradingview.com/pine-script-reference/v6/#var_close), [hl2](https://www.tradingview.com/pine-script-reference/v6/#var_hl2), [hlc3](https://www.tradingview.com/pine-script-reference/v6/#var_hlc3), and [ohlc4](https://www.tradingview.com/pine-script-reference/v6/#var_ohlc4).
-   The values plotted by other scripts on the chart. This can be useful to “link” two or more scripts together by sending the output of one as an input to another script.

This script simply plots the user’s selection of source. We propose the [high](https://www.tradingview.com/pine-script-reference/v6/#var_high) as the default value:

`//@version=6   indicator("Source input", "", true)   srcInput = input.source(high, "Source")   plot(srcInput, "Src", color.new(color.purple, 70), 6)   `

This shows a chart where, in addition to our script, we have loaded an “Arnaud Legoux Moving Average” indicator. See here how we use our script’s source input widget to select the output of the ALMA script as an input into our script. Because our script plots that source in a light-purple thick line, you see the plots from the two scripts overlap because they plot the same value:

![image](https://www.tradingview.com/pine-script-docs/_astro/Inputs-InputTypes-08.SH4c1RFT_1XVzNK.webp)

### [Time input](https://www.tradingview.com/pine-script-docs/concepts/inputs/#time-input)

Time inputs use the [input.time()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.time) function. The function returns a Unix time in milliseconds (see the [Time](https://www.tradingview.com/pine-script-docs/concepts/time/) page for more information). This type of data also contains date information, so the [input.time()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.time) function returns a time **and** a date. That is the reason why its widget allows for the selection of both.

Here, we test the bar’s time against an input value, and we plot an arrow when it is greater:

`//@version=6   indicator("Time input", "T", true)   timeAndDateInput = input.time(timestamp("1 Aug 2021 00:00 +0300"), "Date and time")   barIsLater = time > timeAndDateInput   plotchar(barIsLater, "barIsLater", "🠆", location.top, size = size.tiny)   `

Note that the `defval` value we use is a call to the [timestamp()](https://www.tradingview.com/pine-script-reference/v6/#fun_timestamp) function.

### [Enum input](https://www.tradingview.com/pine-script-docs/concepts/inputs/#enum-input)

The [input.enum()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.enum) function creates a dropdown input that displays _field titles_ corresponding to distinct _members_ (possible values) of an [enum type](https://www.tradingview.com/pine-script-docs/language/type-system/#enum-types). The function returns one of the unique, named values from a declared [enum](https://www.tradingview.com/pine-script-docs/language/enums/), which scripts can use in calculations and logic requiring more strict control over allowed values and operations. Supply a list of enum members to the `options` parameter to specify the members users can select from the dropdown. If one does not specify an enum field’s title, its title is the “string” representation of its _name_.

This example declares a `SignalType` enum with four fields representing named signal display modes: `long`, `short`, `both`, and `none`. The script uses a member of this [enum type](https://www.tradingview.com/pine-script-docs/language/type-system/#enum-types) as the `defval` argument in the [input.enum()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.enum) call to generate a dropdown in the “Inputs” tab, allowing users to select one of the enum’s titles to control which signals it displays on the chart:

![image](https://www.tradingview.com/pine-script-docs/_astro/Inputs-Input-types-Enum-input-1.D56ry8Yz_4z6vc.webp)

``//@version=6   indicator("Enum input demo", overlay = true)      //@enum         An enumeration of named values representing signal display modes.   //@field long   Named value to specify that only long signals are allowed.   //@field short  Named value to specify that only short signals are allowed.   //@field both   Named value to specify that either signal type is allowed.   //@field none   Named value to specify that no signals are allowed.    enum SignalType       long  = "Only long signals"       short = "Only short signals"       both  = "Long and short signals"       none       //@variable An enumerator (member) of the `SignalType` enum. Controls the script's signals.    SignalType sigInput = input.enum(SignalType.long, "Signal type")      // Calculate moving averages.   float ma1 = ta.sma(ohlc4, 10)   float ma2 = ta.sma(ohlc4, 200)   // Calculate cross signals.    bool longCross  = ta.crossover(close, math.max(ma1, ma2))   bool shortCross = ta.crossunder(close, math.min(ma1, ma2))   // Calculate long and short signals based on the selected `sigInput` value.   bool longSignal = (sigInput == SignalType.long or sigInput == SignalType.both) and longCross   bool shortSignal = (sigInput == SignalType.short or sigInput == SignalType.both) and shortCross      // Plot shapes for the `longSignal` and `shortSignal`.   plotshape(longSignal, "Long signal", shape.triangleup, location.belowbar, color.teal, size = size.normal)   plotshape(shortSignal, "Short signal", shape.triangledown, location.abovebar, color.maroon, size = size.normal)   // Plot the moving averages.   plot(ma1, "Fast MA")   plot(ma2, "Slow MA")`` 

Note that:

-   The `sigInput` value is the `SignalType` member whose field contains the selected title.
-   Since we did not specify a title for the `none` field of the enum, its title is the “string” representation of its name (“none”), as we see in the above image of the enum input’s dropdown.

By default, an enum input displays the titles of all an enum’s members within its dropdown. If we supply an `options` argument to the [input.enum()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.enum) call, it will only allow users to select the members included in that list, e.g.:

`SignalType sigInput = input.enum(SignalType.long, "Signal type", options = [SignalType.long, SignalType.short])   `

The above `options` argument specifies that users can only view and select the titles of the `long` and `short` fields from the `SignalType` enum. No other options are allowed:

![image](https://www.tradingview.com/pine-script-docs/_astro/Inputs-Input-types-Enum-input-2.DoT-LWc3_nngA2.webp)

## [Other features affecting Inputs](https://www.tradingview.com/pine-script-docs/concepts/inputs/#other-features-affecting-inputs)

Some parameters of the [indicator()](https://www.tradingview.com/pine-script-reference/v6/#fun_indicator) and [strategy()](https://www.tradingview.com/pine-script-reference/v6/#fun_indicator) functions populate a script’s “Settings/Inputs” tab with additional inputs. These parameters are `timeframe`, `timeframe_gaps`, and `calc_bars_count`. For example:

`//@version=6   indicator("MA", "", true, timeframe = "D", timeframe_gaps = false)   plot(ta.vwma(close, 10))   `

![image](https://www.tradingview.com/pine-script-docs/_astro/Inputs-OtherFeaturesAffectingInputs-03.BtNE-F7g_ecT8G.webp)

## [Tips](https://www.tradingview.com/pine-script-docs/concepts/inputs/#tips)

The design of your script’s inputs has an important impact on the usability of your scripts. Well-designed inputs are more intuitively usable and make for a better user experience:

-   Choose clear and concise labels (your input’s `title` argument).
-   Choose your default values carefully.
-   Provide `minval` and `maxval` values that will prevent your code from producing unexpected results, e.g., limit the minimal value of lengths to 1 or 2, depending on the type of MA you are using.
-   Provide a `step` value that is congruent with the value you are capturing. Steps of 5 can be more useful on a 0-200 range, for example, or steps of 0.05 on a 0.0-1.0 scale.
-   Group related inputs on the same line using `inline`; bull and bear colors for example, or the width and color of a line.
-   When you have many inputs, group them into meaningful sections using `group`. Place the most important sections at the top.
-   Do the same for individual inputs **within** sections.

It can be advantageous to vertically align different arguments of multliple `input.*()` calls in your code. When you need to make global changes, this will allow you to use the Editor’s multi-cursor feature to operate on all the lines at once.

Because It is sometimes necessary to use Unicode spaces to In order to achieve optimal alignment in inputs. This is an example:

`//@version=6   indicator("Aligned inputs", "", true)      var GRP1 = "Not aligned"   ma1SourceInput   = input(close, "MA source",     inline = "11", group = GRP1)   ma1LengthInput   = input(close, "Length",        inline = "11", group = GRP1)   long1SourceInput = input(close, "Signal source", inline = "12", group = GRP1)   long1LengthInput = input(close, "Length",        inline = "12", group = GRP1)      var GRP2 = "Aligned"   // The three spaces after "MA source" are Unicode EN spaces (U+2002).   ma2SourceInput   = input(close, "MA source   ",  inline = "21", group = GRP2)   ma2LengthInput   = input(close, "Length",        inline = "21", group = GRP2)   long2SourceInput = input(close, "Signal source", inline = "22", group = GRP2)   long2LengthInput = input(close, "Length",        inline = "22", group = GRP2)      plot(ta.vwma(close, 10))   `

![image](https://www.tradingview.com/pine-script-docs/_astro/Inputs-Tips-1.DU-DannF_Eodj8.webp)

Note that:

-   We use the `group` parameter to distinguish between the two sections of inputs. We use a constant to hold the name of the groups. This way, if we decide to change the name of the group, we only need to change it in one place.
-   The first sections inputs widgets do not align vertically. We are using `inline`, which places the input widgets immediately to the right of the label. Because the labels for the `ma1SourceInput` and `long1SourceInput` inputs are of different lengths the labels are in different _y_ positions.
-   To make up for the misalignment, we pad the `title` argument in the `ma2SourceInput` line with three Unicode EN spaces (U+2002). Unicode spaces are necessary because ordinary spaces would be stripped from the label. You can achieve precise alignment by combining different quantities and types of Unicode spaces. See here for a list of [Unicode spaces](https://jkorpela.fi/chars/spaces.html) of different widths.