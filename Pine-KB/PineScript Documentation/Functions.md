## [Can I use a variable length in functions?](https://www.tradingview.com/pine-script-docs/faq/functions/#can-i-use-a-variable-length-in-functions)

Many [built-in](https://www.tradingview.com/pine-script-docs/language/built-ins#built-in-functions) technical analysis (TA) functions have a `length` parameter, such as `ta.sma(source, length)`. A majority of these functions can process “[series](https://www.tradingview.com/pine-script-docs/language/type-system/#series)” lengths, i.e., lengths that can change from bar to bar. Some functions, however, only accept “[simple](https://www.tradingview.com/pine-script-docs/language/type-system/#simple)” integer lengths, which must be known on bar zero and not change during the execution of the script.

Check the Reference Manual entry for a function to see what type of values a function can process.

**Additional resources**

For more advanced versions of functions that support “series” lengths, or for extra technical analysis tools explore the [ta library](https://www.tradingview.com/script/BICzyhq0-ta/) on the TradingView profile. This library offers a range of extended TA-related capabilities and custom implementations.

**User-defined functions**

For built-in functions that do not accept “series” lengths and for which the functionality is not available in the [ta library](https://www.tradingview.com/script/BICzyhq0-ta/), consider creating a [user-defined function](https://www.tradingview.com/pine-script-docs/language/user-defined-functions/).

## [How can I calculate values depending on variable lengths that reset on a condition?](https://www.tradingview.com/pine-script-docs/faq/functions/#how-can-i-calculate-values-depending-on-variable-lengths-that-reset-on-a-condition)

To calculate certain values that are dependent on varying lengths, which also reset under specific conditions, the [ta.barssince()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.barssince) function can be useful. This function counts the number of bars since the last occurrence of a specified condition, automatically resetting the count each time this condition is met. There are, however, some considerations to take into account when using this function for this purpose.

Firstly, before the condition is met for the first time in a chart’s history, [ta.barssince()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.barssince) returns [na](https://www.tradingview.com/pine-script-reference/v6/#var_na). This value is not usable as a length for functions and can cause errors, especially during execution on a chart’s early bars. For a more robust version, use [nz()](https://www.tradingview.com/pine-script-reference/v6/#fun_nz) to replace the [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) return of [ta.barssince()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.barssince) with zero for early bars.

Secondly, when the condition is met, [ta.barssince()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.barssince) returns zero for that bar, since zero bars have elapsed since the condition was last true.

Since lengths cannot be zero, it is necessary to add one to a returned value of zero, ensuring that the length is always at least one.

Here’s an example of how to use these principles for a practical purpose. The following example script calculates the highest and lowest price points since the start of a new day. We use [timeframe.change()](https://www.tradingview.com/pine-script-reference/v6/#fun_timeframe.change) to detect the start of a new day, which is our condition. The [ta.barssince()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.barssince) function calculates the number of bars that elapsed since this condition was last met. The script passes this number, or “lookback”, to the [ta.lowest()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.lowest) and [ta.highest()](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.highest) functions, which determine the highest and lowest points since the start of the new day:

![image](https://www.tradingview.com/pine-script-docs/_astro/Functions-How-can-i-calculate-values-depending-on-variable-lengths-that-reset-on-a-condition-1.BG9cnL10_Z2jJ0Tt.webp)

//@version=6 indicator("Highest/lowest since new day", "", true) // Identify the start of a new day and calculate the number of bars since then. bool newDay = timeframe.change("D") int lookback = nz(ta.barssince(newDay)) + 1 // Calculate the highest and lowest point since the new day began. float lowestSinceNewDay = ta.lowest(lookback) float highestSinceNewDay = ta.highest(lookback) // Plot the high/low level since the start of a new day. plot(lowestSinceNewDay, "High today", color.orange) plot(highestSinceNewDay, "Low today", color.aqua) // Change the background color to indicate the start of a new day. bgcolor(newDay ? color.new(color.gray, 80) : na) // Display the varying lookback period in Data Window. plot(lookback, "Lookback", display = display.data\_window)

## [How can I round a number to x increments?](https://www.tradingview.com/pine-script-docs/faq/functions/#how-can-i-round-a-number-to-x-increments)

Rounding numbers to specific increments is useful for tasks like calculating levels for grid trading, dealing with fractional shares, or aligning trading parameters to specific pip values.

In this example, the `roundToIncrement()` function accepts a value and an increment as parameters. It divides the value by the increment, rounds the result, then multiplies it by the increment to give the rounded value. To demonstrate the function, the closing price is rounded to the nearest increment defined in the user menu:

//@version=6 indicator("Round to x increment demo", overlay = true) float incrementInput = input.float(0.75, "Increment", step = 0.25) // @function Rounds a value to the nearest multiple of a specified increment. // @param value The value to round. // @param increment The increment to round the value to. // @returns The rounded value. roundToIncrement(value, increment) => math.round(value / increment) \* increment plot(series = roundToIncrement(close, incrementInput), color = chart.fg\_color)

## [How can I control the precision of values my script displays?](https://www.tradingview.com/pine-script-docs/faq/functions/#how-can-i-control-the-precision-of-values-my-script-displays)

The `precision` and `format` arguments in the [indicator()](https://www.tradingview.com/pine-script-reference/v6/#fun_indicator) or [strategy()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy) declaration statement control the number of decimals in the values that a script displays.

By default, scripts use the precision of the price scale. To display more decimal places, specify a `precision` argument that exceeds the value of the current price scale.

## [How can I control the precision of values used in my calculations?](https://www.tradingview.com/pine-script-docs/faq/functions/#how-can-i-control-the-precision-of-values-used-in-my-calculations)

The `math.round(number, precision)` variation of the [math.round()](https://www.tradingview.com/pine-script-reference/v6/#fun_math.round) function rounds values according to a specified precision. Alternatively, the [math.round\_to\_mintick()](https://www.tradingview.com/pine-script-reference/v6/#fun_math.round_to_mintick) function rounds values to the nearest tick precision of the chart’s symbol.

## [How can I round to ticks?](https://www.tradingview.com/pine-script-docs/faq/functions/#how-can-i-round-to-ticks)

To round values to the tick precision of a chart’s symbol, use the function [math.round\_to\_mintick()](https://www.tradingview.com/pine-script-reference/v6/#fun_math.round_to_mintick). To convert the resulting number to a string, use `str.tostring(myValue, format.mintick)` to first round the number to tick precision and then return its string representation, where `myValue` is the number to convert into a rounded string.

## [How can I abbreviate large values?](https://www.tradingview.com/pine-script-docs/faq/functions/#how-can-i-abbreviate-large-values)

There are different ways to abbreviate large numerical values, such as volume. For instance, the number 1,222,333.0 can be simplified to 1.222M. Here are some methods to accomplish this:

**Apply a global setting**

Use the argument `format = format.volume` within either the [indicator()](https://www.tradingview.com/pine-script-reference/v6/#fun_indicator) or [strategy()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy) statements. Using this setting, displays all values in the script in their abbreviated forms.

**Abbreviate specific values**

To abbreviate only certain values for string display, use the `str.tostring(value, format.volume)` function.

**Use a custom function**

To specify a custom precision or abbreviate values up to trillions, use a custom function. In the following example script, the [user-defined function](https://www.tradingview.com/pine-script-docs/language/user-defined-functions/) `abbreviateValue()` divides the `value` by a power of ten based on its magnitude, and adds an abbreviation letter (K, M, B, or T) to represent the magnitude of the original value. The function also adds a subtle space between the value and the magnitude letter. The `print()` function displays the value on the chart for visualization.

//@version=6 indicator("Value abbreviation example") // @function Converts a numeric value into a readable string representation featuring the appropriate order // of magnitude abbreviation (K, M, B, T). // @param value (float) The value to format. // @param precision (string) The numerical precision of the result. ("" for none, ".00" for two digits, etc.) // @returns (string) The formatted value as a string with the appropriate abbreviation suffix. abbreviateValue(float value, string precision) => float digitsAmt = math.log10(math.abs(value)) string formatPrecision = "#" + precision string result = switch digitsAmt > 12 => str.tostring(value / 1e12, formatPrecision + "  T") digitsAmt > 9 => str.tostring(value / 1e9, formatPrecision + "  B") digitsAmt > 6 => str.tostring(value / 1e6, formatPrecision + "  M") digitsAmt > 3 => str.tostring(value / 1e3, formatPrecision + "  K") => str.tostring(value, "#" + formatPrecision) print(formattedString) => var table t = table.new(position.middle\_right, 1, 1) table.cell(t, 0, 0, formattedString, bgcolor = color.yellow) print(abbreviateValue(volume, ".00"))

## [How can I calculate using pips?](https://www.tradingview.com/pine-script-docs/faq/functions/#how-can-i-calculate-using-pips)

Use the custom function `calcBaseUnit()` in the following example script to return the correct pip value for Forex symbols, or the base unit of change for non-forex symbols:

//@version=6 indicator("Pip calculation example") // @function Calculates the chart symbol's base unit of change in asset prices. // @returns (float) A ticks or pips value of base units of change. calcBaseUnit() => bool isForexSymbol = syminfo.type == "forex" bool isYenQuote = syminfo.currency == "JPY" bool isYenBase = syminfo.basecurrency == "JPY" float result = isForexSymbol ? isYenQuote ? 0.01 : isYenBase ? 0.00001 : 0.0001 : syminfo.mintick // Call the function and plot the result in a label var label baseUnitLabel = na if barstate.islast baseUnitLabel := label.new(x=bar\_index + 1, y=open, text="Base Unit: " + str.tostring(calcBaseUnit(), "#.######"), style=label.style\_label\_left, color=color.new(color.blue, 0), textcolor=color.white) label.delete(baseUnitLabel\[1\])

## [How do I calculate averages?](https://www.tradingview.com/pine-script-docs/faq/functions/#how-do-i-calculate-averages)

The method of calculating averages depends on the type of values to average.

**Distinct variables**

To find the average of a small number of discrete variables, use the function [math.avg(number0, number1, …)](https://www.tradingview.com/pine-script-reference/v6/#fun_math.avg). Simply pass each of the variables as an argument to this function.

**Bar prices**

To find the average price of a single bar, use the built-in variables [hl2](https://www.tradingview.com/pine-script-reference/v6/#var_hl2), [hlc3](https://www.tradingview.com/pine-script-reference/v6/#var_hlc3), and [ohlc4](https://www.tradingview.com/pine-script-reference/v6/#var_ohlc4).

**Series values**

To compute the average of the last _n_ values in a series, use the function [ta.sma(series,n)](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.sma).

**Custom datasets**

To average a custom set of values, organize them into an [array](https://www.tradingview.com/pine-script-docs/language/arrays/) and use [array.avg()](https://www.tradingview.com/pine-script-reference/v6/#fun_array.avg). For complex datasets, programmers can use the [matrix.avg()](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.avg) function to average the contents of a matrix. For a deeper understanding of averaging custom datasets, refer to this [conditional averages](https://www.tradingview.com/script/9l0ZpuQU-ConditionalAverages/) publication.

## [How can I calculate an average only when a certain condition is true?](https://www.tradingview.com/pine-script-docs/faq/functions/#how-can-i-calculate-an-average-only-when-a-certain-condition-is-true)

The usual methods of calculating averages, which were discussed in the [calculating averages section](https://www.tradingview.com/pine-script-docs/faq/functions#how-do-i-calculate-averages) above, apply across _all_ data points in a range. To calculate averages of only those values that occur under specific conditions, calculate _conditional averages_ using custom functions.

The example script below imports a [library](https://www.tradingview.com/pine-script-docs/concepts/libraries/) called [ConditionalAverages](https://www.tradingview.com/script/9l0ZpuQU-ConditionalAverages/) and uses two of its functions:

-   The `avgWhen()` function calculates the average volume of session opening bars across the entire dataset.
-   The `avgWhenLast()` function averages the opening volumes for the last five session opening bars.

The condition for these conditional averages is _session opening bars_, which we determine using the [session.isfirstbar\_regular](https://www.tradingview.com/pine-script-reference/v6/#var_session.isfirstbar_regular) variable.

![image](https://www.tradingview.com/pine-script-docs/_astro/Functions-How-can-i-calculate-an-average-only-when-a-certain-condition-is-true-1.zmzMnsL2_2dPpkK.webp)

//@version=6 indicator("Average session opening volume") import PineCoders/ConditionalAverages/1 as PCca // Color aqua for the session's opening bar, otherwise distinct colors for up/down volume columns. color volumeColor = switch session.isfirstbar\_regular => color.aqua close > open => color.new(#D1D4DC, 65) => color.new(#787B86, 65) // Plot the volume columns. plot(volume, "volume", volumeColor, 4, plot.style\_histogram) // Average volume over \*all\* session opening bars in the dataset. plot(PCca.avgWhen(src = volume, cond = session.isfirstbar\_regular), "avg. When", #FF00FF) // Average volume over the last five opening bars. plot(PCca.avgWhenLast(src = volume, cond = session.isfirstbar\_regular, cnt = 5), "avgWhenInLast()", #00FF00)

## [How can I generate a random number?](https://www.tradingview.com/pine-script-docs/faq/functions/#how-can-i-generate-a-random-number)

Use the [math.random()](https://www.tradingview.com/pine-script-reference/v6/#fun_math.random) function to generate random numbers. This example script creates a circle plot with random RGB color values and a random y value between 0 and 1:

//@version=6 indicator("Random demo", overlay = false) // Generate a random price value (the default range is 0 to 1). float y = math.random() // Generate a color with red, green, and blue values as separate random values between 0 and 255. color plotColor = color.rgb(math.random(0, 255), math.random(0, 255), math.random(0, 255)) plot(series = y, title = "Random number", color = plotColor, linewidth = 2, style = plot.style\_circles)

## [How can I evaluate a filter I am planning to use?](https://www.tradingview.com/pine-script-docs/faq/functions/#how-can-i-evaluate-a-filter-i-am-planning-to-use)

To evaluate a filter, insert your filter code into the [Filter Information Box - PineCoders FAQ](https://www.tradingview.com/script/oTEP9DJF-Filter-Information-Box-PineCoders-FAQ/) script. This script conducts an impulse response analysis and shows the filter’s characteristics in a label on the chart.

For further details and a guide on integrating your filter into the code, refer to the publication’s description.

## [What does nz() do?](https://www.tradingview.com/pine-script-docs/faq/functions/#what-does-nz-do)

The [nz()](https://www.tradingview.com/pine-script-reference/v6/#fun_nz) function replaces any [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) values with zero, or with a user-defined value if the `replacement` argument is specified. This function helps to prevent [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) values from interfering with calculations.

The following example script shows an exaggerated failure as a result of a single [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) value. The `barRangeRaw` variable is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) only once, on the first bar, because it references a bar that does not exist, using the history-referencing operator. The alternative variable `barRangeWithNz` uses [nz()](https://www.tradingview.com/pine-script-reference/v6/#fun_nz) to prevent an [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) value from ever occurring.

The `dependentCalculation` variable takes one of these values and uses it to calculate a crude average of the bar range. If the input to this calculation is ever [na](https://www.tradingview.com/pine-script-reference/v6/#var_na), the series will be [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) forever after that.

Choose between the two values for bar range using the input setting, and the range either displays or not. In the latter case, the Data Window shows that the value of `dependentCalculation` is `ϴ`, meaning [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).

//@version=6 indicator("\`na\` values on first bar demo") bool useNzInput = input.bool(true, "Use \`nz\` to ensure value is never na") // This variable is na on the first bar. float barRangeRaw = close - close\[1\] // This variable is never na. float barRangeWithNz = close - nz(close\[1\], open) // Choose the value to use based on the input float barRange = useNzInput ? barRangeWithNz : barRangeRaw // Perform a calculation that depends on the barRange var float dependentCalculation = 0 dependentCalculation := ((dependentCalculation + barRange)/2) // Plot the results plot(dependentCalculation, title="Average Bar Range")

The [nz()](https://www.tradingview.com/pine-script-reference/v6/#fun_nz) function is also useful to protect against any potential divide-by-zero errors. It guarantees a return value even when an equation unintentionally features a zero in the denominator. Consider the following code snippet that intentionally creates a divide-by-zero scenario by setting the denominator to zero. Without the [nz()](https://www.tradingview.com/pine-script-reference/v6/#fun_nz) function, this expression would return [na](https://www.tradingview.com/pine-script-reference/v6/#var_na), instead of zero:

float dbzTest = nz(close / (close - close))