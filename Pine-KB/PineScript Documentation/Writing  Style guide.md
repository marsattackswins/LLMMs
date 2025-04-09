## [Introduction](https://www.tradingview.com/pine-script-docs/writing/style-guide/#introduction)

This style guide provides recommendations on how to name variables and organize your Pine scripts in a standard way that works well. Scripts that follow our best practices will be easier to read, understand and maintain.

You can see scripts using these guidelines published from the [TradingView](https://www.tradingview.com/u/TradingView/#published-scripts) and [PineCoders](https://www.tradingview.com/u/PineCoders/#published-scripts) accounts on the platform.

## [Naming Conventions](https://www.tradingview.com/pine-script-docs/writing/style-guide/#naming-conventions)

We recommend the use of:

-   `camelCase` for all identifiers, i.e., variable or function names: `ma`, `maFast`, `maLengthInput`, `maColor`, `roundedOHLC()`, `pivotHi()`.
-   All caps `SNAKE_CASE` for constants: `BULL_COLOR`, `BEAR_COLOR`, `MAX_LOOKBACK`.
-   The use of qualifying suffixes when it provides valuable clues about the type or provenance of a variable: `maShowInput`, `bearColor`, `bearColorInput`, `volumesArray`, `maPlotID`, `resultsTable`, `levelsColorArray`.

## [Script organization](https://www.tradingview.com/pine-script-docs/writing/style-guide/#script-organization)

The Pine Script™ compiler is quite forgiving of the positioning of specific statements or the version [compiler annotation](https://www.tradingview.com/pine-script-docs/language/script-structure/#compiler-annotations) in the script. While other arrangements are syntactically correct, this is how we recommend organizing scripts:

```
<license><version><declaration_statement><import_statements><constant_declarations><inputs><function_declarations><calculations><strategy_calls><visuals><alerts>
```

### [<license>](https://www.tradingview.com/pine-script-docs/writing/style-guide/#license)

If you publish your open-source scripts publicly on TradingView (scripts can also be published privately), your open-source code is by default protected by the Mozilla license. You may choose any other license you prefer.

The reuse of code from those scripts is governed by our [House Rules on Script Publishing](https://www.tradingview.com/support/solutions/43000590599) which preempt the author’s license.

The standard license comments appearing at the beginning of scripts are:

// This source code is subject to the terms of the Mozilla Public License 2.0 at https://mozilla.org/MPL/2.0/ // © username

### [<version>](https://www.tradingview.com/pine-script-docs/writing/style-guide/#version)

This is the [compiler annotation](https://www.tradingview.com/pine-script-docs/language/script-structure/#compiler-annotations) defining the version of Pine Script™ the script will use. If none is present, v1 is used. For v6, use:

//@version=6

### [<declaration\_statement>](https://www.tradingview.com/pine-script-docs/writing/style-guide/#declaration_statement)

This is the mandatory declaration statement which defines the type of your script. It must be a call to either [indicator()](https://www.tradingview.com/pine-script-reference/v6/#fun_indicator), [strategy()](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy), or [library()](https://www.tradingview.com/pine-script-reference/v6/#fun_library).

### [<import\_statements>](https://www.tradingview.com/pine-script-docs/writing/style-guide/#import_statements)

If your script uses one or more Pine Script™ [libraries](https://www.tradingview.com/pine-script-docs/concepts/libraries/), your [import](https://www.tradingview.com/pine-script-reference/v6/#kw_import) statements belong here.

### [<constant\_declarations>](https://www.tradingview.com/pine-script-docs/writing/style-guide/#constant_declarations)

Scripts can declare variables qualified as “const”, i.e., ones referencing a constant value.

We refer to variables as “constants” when they meet these criteria:

-   Their declaration uses the optional `const` keyword (see our User Manual’s section on [type qualifiers](https://www.tradingview.com/pine-script-docs/language/type-system/#qualifiers) for more information).
-   They are initialized using a literal (e.g., `100` or `"AAPL"`) or a built-in qualified as “const” (e.g., `color.green`).
-   Their value does not change during the script’s execution.

We use `SNAKE_CASE` to name these variables and group their declaration near the top of the script. For example:

// ————— Constants int MS\_IN\_MIN = 60 \* 1000 int MS\_IN\_HOUR = MS\_IN\_MIN \* 60 int MS\_IN\_DAY = MS\_IN\_HOUR \* 24 color GRAY = #808080ff color LIME = #00FF00ff color MAROON = #800000ff color ORANGE = #FF8000ff color PINK = #FF0080ff color TEAL = #008080ff color BG\_DIV = color.new(ORANGE, 90) color BG\_RESETS = color.new(GRAY, 90) string RST1 = "No reset; cumulate since the beginning of the chart" string RST2 = "On a stepped higher timeframe (HTF)" string RST3 = "On a fixed HTF" string RST4 = "At a fixed time" string RST5 = "At the beginning of the regular session" string RST6 = "At the first visible chart bar" string RST7 = "Fixed rolling period" string LTF1 = "Least precise, covering many chart bars" string LTF2 = "Less precise, covering some chart bars" string LTF3 = "More precise, covering less chart bars" string LTF4 = "Most precise, 1min intrabars" string TT\_TOTVOL = "The 'Bodies' value is the transparency of the total volume candle bodies. Zero is opaque, 100 is transparent." string TT\_RST\_HTF = "This value is used when '" + RST3 +"' is selected." string TT\_RST\_TIME = "These values are used when '" + RST4 +"' is selected. A reset will occur when the time is greater or equal to the bar's open time, and less than its close time.\\nHour: 0-23\\nMinute: 0-59" string TT\_RST\_PERIOD = "This value is used when '" + RST7 +"' is selected."

In this example:

-   The `RST*` and `LTF*` constants will be used as tuple elements in the `options` argument of `input.*()` calls.
-   The `TT_*` constants will be used as `tooltip` arguments in `input.*()` calls. Note how we use a line continuation for long string literals.
-   We do not use [var](https://www.tradingview.com/pine-script-reference/v6/#kw_var) to initialize constants. The Pine Script™ runtime is optimized to handle declarations on each bar, but using [var](https://www.tradingview.com/pine-script-reference/v6/#kw_var) to initialize a variable only the first time it is declared incurs a minor penalty on script performance because of the maintenance that [var](https://www.tradingview.com/pine-script-reference/v6/#kw_var) variables require on further bars.

Note that:

-   Literals used in more than one place in a script should always be declared as a constant. Using the constant rather than the literal makes it more readable if it is given a meaningful name, and the practice makes code easier to maintain. Even though the quantity of milliseconds in a day is unlikely to change in the future, `MS_IN_DAY` is more meaningful than `1000 * 60 * 60 * 24`.
-   Constants only used in the local block of a function or [if](https://www.tradingview.com/pine-script-reference/v6/#kw_if), [while](https://www.tradingview.com/pine-script-reference/v6/#kw_while), etc., statement for example, can be declared in that local block.

### [<inputs>](https://www.tradingview.com/pine-script-docs/writing/style-guide/#inputs)

It is **much** easier to read scripts when all their inputs are in the same code section. Placing that section at the beginning of the script also reflects how they are processed at runtime, i.e., before the rest of the script is executed.

Suffixing input variable names with `input` makes them more readily identifiable when they are used later in the script: `maLengthInput`, `bearColorInput`, `showAvgInput`, etc.

// ————— Inputs string resetInput = input.string(RST2, "CVD Resets", inline = "00", options = \[RST1, RST2, RST3, RST4, RST5, RST6, RST7\]) string fixedTfInput = input.timeframe("D", "  Fixed HTF:  ", tooltip = TT\_RST\_HTF) int hourInput = input.int(9, "  Fixed time hour:  ", inline = "01", minval = 0, maxval = 23) int minuteInput = input.int(30, "minute", inline = "01", minval = 0, maxval = 59, tooltip = TT\_RST\_TIME) int fixedPeriodInput = input.int(20, "  Fixed period:  ", inline = "02", minval = 1, tooltip = TT\_RST\_PERIOD) string ltfModeInput = input.string(LTF3, "Intrabar precision", inline = "03", options = \[LTF1, LTF2, LTF3, LTF4\])

### [<function\_declarations>](https://www.tradingview.com/pine-script-docs/writing/style-guide/#function_declarations)

All user-defined functions must be defined in the script’s global scope; nested function definitions are not allowed in Pine Script™.

Optimal function design should minimize the use of global variables in the function’s scope, as they undermine function portability. When it can’t be avoided, those functions must follow the global variable declarations in the code, which entails they can’t always be placed in the <function\_declarations> section. Such dependencies on global variables should ideally be documented in the function’s comments.

It will also help readers if you document the function’s objective, parameters and result. The same syntax used in [libraries](https://www.tradingview.com/pine-script-docs/concepts/libraries/) can be used to document your functions. This can make it easier to port your functions to a library should you ever decide to do so:

//@version=6 indicator("<function\_declarations>", "", true) string SIZE\_LARGE = "Large" string SIZE\_NORMAL = "Normal" string SIZE\_SMALL = "Small" string sizeInput = input.string(SIZE\_NORMAL, "Size", options = \[SIZE\_LARGE, SIZE\_NORMAL, SIZE\_SMALL\]) // @function Used to produce an argument for the \`size\` parameter in built-in functions. // @param userSize (simple string) User-selected size. // @returns One of the \`size.\*\` built-in constants. // Dependencies SIZE\_LARGE, SIZE\_NORMAL, SIZE\_SMALL getSize(simple string userSize) => result = switch userSize SIZE\_LARGE => size.large SIZE\_NORMAL => size.normal SIZE\_SMALL => size.small => size.auto if ta.rising(close, 3) label.new(bar\_index, na, yloc = yloc.abovebar, style = label.style\_arrowup, size = getSize(sizeInput))

### [<calculations>](https://www.tradingview.com/pine-script-docs/writing/style-guide/#calculations)

This is where the script’s core calculations and logic should be placed. Code can be easier to read when variable declarations are placed near the code segment using the variables. Some programmers prefer to place all their non-constant variable declarations at the beginning of this section, which is not always possible for all variables, as some may require some calculations to have been executed before their declaration.

### [<strategy\_calls>](https://www.tradingview.com/pine-script-docs/writing/style-guide/#strategy_calls)

Strategies are easier to read when strategy calls are grouped in the same section of the script.

### [<visuals>](https://www.tradingview.com/pine-script-docs/writing/style-guide/#visuals)

This section should ideally include all the statements producing the script’s visuals, whether they be plots, drawings, background colors, candle-plotting, etc. See the Pine Script™ user manual’s section on [here](https://www.tradingview.com/pine-script-docs/concepts/colors/#z-index) for more information on how the relative depth of visuals is determined.

### [<alerts>](https://www.tradingview.com/pine-script-docs/writing/style-guide/#alerts)

Alert code will usually require the script’s calculations to have executed before it, so it makes sense to put it at the end of the script.

## [Spacing](https://www.tradingview.com/pine-script-docs/writing/style-guide/#spacing)

A space should be used on both sides of all operators, except unary operators (`-1`). A space is also recommended after all commas and when using named function arguments, as in `plot(series = close)`:

int a = close > open ? 1 : -1 var int newLen = 2 newLen := min(20, newlen + 1) float a = -b float c = d > e ? d - e : d int index = bar\_index % 2 == 0 ? 1 : 2 plot(close, color = color.red)

## [Line wrapping](https://www.tradingview.com/pine-script-docs/writing/style-guide/#line-wrapping)

Line wrapping can make long lines easier to read. Line wraps are defined by using an indentation level that is not a multiple of four, as four spaces or a tab are used to define local blocks. Here we use two spaces:

plot( series = close, title = "Close", color = color.blue, show\_last = 10 )

## [Vertical alignment](https://www.tradingview.com/pine-script-docs/writing/style-guide/#vertical-alignment)

Vertical alignment using tabs or spaces can be useful in code sections containing many similar lines such as constant declarations or inputs. They can make mass edits much easier using the Pine Editor’s multi-cursor feature (`ctrl` + `alt` + `🠅`):

// Colors used as defaults in inputs. color COLOR\_AQUA = #0080FFff color COLOR\_BLACK = #000000ff color COLOR\_BLUE = #013BCAff color COLOR\_CORAL = #FF8080ff color COLOR\_GOLD = #CCCC00ff

## [Explicit typing](https://www.tradingview.com/pine-script-docs/writing/style-guide/#explicit-typing)

Including the type of variables when declaring them is not required. However, it helps make scripts easier to read, navigate, and understand. It can help clarify the expected types at each point in a script’s execution and distinguish a variable’s declaration (using `=`) from its reassignments (using `:=`). Using explicit typing can also make scripts easier to [debug](https://www.tradingview.com/pine-script-docs/writing/debugging/).