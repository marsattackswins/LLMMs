## [What does “scope” mean?](https://www.tradingview.com/pine-script-docs/faq/programming/#what-does-scope-mean)

The _scope_ of a variable is the part of a script that defines the variable and in which it can be referenced. There are two main types of scope: _global_ and _local_.

**Global Scope:** The global scope is all of the script that is not inside a [function](https://www.tradingview.com/pine-script-docs/language/user-defined-functions/), [if statement](https://www.tradingview.com/pine-script-reference/v6/#kw_if), or other [conditional structure](https://www.tradingview.com/pine-script-docs/language/conditional-structures/). Code from anywhere in the script can access global variables. There is only one global scope.

**Local Scope:** Code that is inside a function or in any local block (one that is inset by four spaces) defines a local scope. Only code that is in the same local scope can access a local variable. There can be many local scopes.

The following example script gives an “Undeclared identifier” error when we try to access a local variable from the global scope.

//@version=5 indicator("Scope demo") // Global scope int globalValue = close > open ? 1 : -1 if barstate.isconfirmed // Local scope int localValue = close > open ? 1 : -1 plot(localValue, "Local variable", chart.fg\_color, 2)

To fix this error, we can declare the variable in the global scope, thus making it accessible from any scope in the script, and then conditionally modify it within a local block:

//@version=5 indicator("Scope demo") // Global scope int globalValue = close > open ? 1 : -1 int localValue = na if barstate.isconfirmed // Local scope localValue := close > open ? 1 : -1 plot(localValue, "Local variable", chart.fg\_color, 2)

Similarly, the following script gives an “Undeclared identifier” error when we try to access a variable defined in one local scope from another local scope. In this case, local scope 1 _contains_ local scope 2, but the same problem would be present if they were on the same level. When a scope contains another one, the inner scope can access variables declared in the outer one, but not vice versa.

//@version=5 indicator("Scope demo") bool isUpCandleWithLargerUpWick = false if barstate.isconfirmed // Local scope 1 bool upWickIsLarger = (high - math.max(open, close)) > (math.min(open,close) - low) if close > open // Local scope 2 bool isUpCandle = true isUpCandleWithLargerUpWick := upWickIsLarger and isUpCandle ? true : false plot(isUpCandleWithLargerUpWick, "Global variable depending on two local variables", chart.fg\_color, 2)

For more information about scopes, see the [Code](https://www.tradingview.com/pine-script-docs/language/script-structure/#code) section of the User Manual.

## [How can I convert a script to a newer version of Pine Script™?](https://www.tradingview.com/pine-script-docs/faq/programming/#how-can-i-convert-a-script-to-a-newer-version-of-pine-script)

See the [Migration Guides](https://www.tradingview.com/pine-script-docs/migration-guides/overview/) section of the User Manual for instructions about upgrading the version of Pine that a script uses.

## [Can I access the source code of “Invite-Only” or “closed-source” scripts?](https://www.tradingview.com/pine-script-docs/faq/programming/#can-i-access-the-source-code-of-invite-only-or-closed-source-scripts)

No; only _open_ scripts have their source code visible. The source code of _protected_ and _Invite-Only_ scripts is hidden and can only be seen by the script author.

For a definition of the _access types_ of published scripts: open, protected, and Invite-Only, see [this article](https://www.tradingview.com/support/solutions/43000482573-what-are-the-different-types-of-published-scripts/) in the Help Center.

For an explanation on the _visibility_ (public/private) that a script can have, see the [Visibility](https://www.tradingview.com/pine-script-docs/writing/publishing/#visibility) section of the Publishing scripts page in the User Manual.

## [Is Pine Script™ an object-oriented language?](https://www.tradingview.com/pine-script-docs/faq/programming/#is-pine-script-an-object-oriented-language)

Although Pine Script™ is not strictly an object-oriented programming language, it incorporates some object-oriented features, notably [user-defined types](https://www.tradingview.com/pine-script-docs/language/type-system/#user-defined-types) (UDTs). Scripts can create [objects](https://www.tradingview.com/pine-script-docs/language/objects/) as instances of a UDT. These objects have one or more fields, which can store values of various data types.

Here is a simple example of how to use the [type](https://www.tradingview.com/pine-script-reference/v6/#kw_type) keyword to create an object:

//@version=5 indicator("Object demo") // Define a new type named \`pivot\`. type pivot int x float y bool isHigh // Create a new \`pivot\` with specific values. pivot newPivot = pivot.new(bar\_index, close, true) // Plot the \`y\` component of \`newPivot\`. plot(newPivot.y)

In this example, we create an object `newPivot`, which is an instance of the user-defined type `pivot`. The script then plots the `y` field of `newPivot`.

## [How can I access the source code of built-in indicators?](https://www.tradingview.com/pine-script-docs/faq/programming/#how-can-i-access-the-source-code-of-built-in-indicators)

There are two ways to access the source code of built-in indicators that are written in Pine:

**Create a new indicator**

In the Pine Script™ Editor, click the dropdown menu (the arrow in the upper-left corner of the editor pane) and choose the “_Create new_” > “_Built in…_” option. Select the built-in indicator that you want to work with.

**Edit the code**

With the indicator displayed on the chart, click on the curly braces `{}` next to the indicator name to open it in the Pine Editor. To edit the code, click the option to create a working copy.

Some built-in indicators, such as the Volume Profile or chart pattern indicators, are not written in Pine and so the code for these indicators is not accessible. These indicators are not included in the “_Built-in script_” menu, and curly braces are not displayed next to their names on the chart.

## [How can I examine the value of a string in my script?](https://www.tradingview.com/pine-script-docs/faq/programming/#how-can-i-examine-the-value-of-a-string-in-my-script)

Scripts can print strings to Pine Logs on any or every bar, along with messages about the logic of the script at that point. See the [Pine Logs](https://www.tradingview.com/pine-script-docs/writing/debugging/#pine-logs) section of the User Manual for information about logging.

Scripts can also display string in labels or label tooltips. The following example scripts displays a string in a label on the last bar of the chart using a custom function.

//@version=5 indicator("print()", "", true) print(string txt) => // Create a persistent label var label myLabel = label.new(bar\_index, na, txt, xloc.bar\_index, yloc.price, color(na), label.style\_label\_left, chart.fg\_color, size.large, text.align\_left) // Update the label's x and y position, and the text it displays. label.set\_xy(myLabel, bar\_index, open) label.set\_text(myLabel, txt) if barstate.islast print("Timeframe = " + timeframe.period)

For more techniques, see the [debugging strings](https://www.tradingview.com/pine-script-docs/writing/debugging/#strings) section of the User Manual.

## [How can I visualize my script’s conditions?](https://www.tradingview.com/pine-script-docs/faq/programming/#how-can-i-visualize-my-scripts-conditions)

If a script contains complex logical conditions, it can be difficult to debug the output. Visualizing each condition separately can help to debug any problems. See the [Compound and nested conditions](https://www.tradingview.com/pine-script-docs/writing/debugging/#compound-and-nested-conditions) section of the User Manual for an example.

## [How can I make the console appear in the editor?](https://www.tradingview.com/pine-script-docs/faq/programming/#how-can-i-make-the-console-appear-in-the-editor)

To display the console in the editor, either press the keyboard shortcut Ctrl + \` (grave accent), or right-click within the editor and choose the “Toggle Console” option.

## [How can I plot numeric values so that they don’t affect the indicator’s scale?](https://www.tradingview.com/pine-script-docs/faq/programming/#how-can-i-plot-numeric-values-so-that-they-dont-affect-the-indicators-scale)

Plotting numerical values on the main chart pane can distort the price scale if the values differ too much from the price.

One way around this is not to plot the values on the chart, but use the Data Window to inspect them. Add `display = display.data_window` to the [plot()](https://www.tradingview.com/pine-script-reference/v6/#fun_plot) call, and the values are visible in the Data Window for any single historical or realtime bar that the cursor hovers over.

Another option is to set the script to display in a separate pane by using `overlay = false` in the [indicator()](https://www.tradingview.com/pine-script-reference/v6/#fun_indicator) declaration. The user needs to delete and re-add the script to the chart if this parameter is changed. Plot the numeric values to track in the separate pane, and draw the rest of the script visuals on the main chart pane by using the `force_overlay` parameter.

Additionally, right-clicking on the scale on the chart brings out the dropdown menu. The “Scale Price Chart Only” option there makes it so the Auto mode of the chart scale only takes the chart itself into account, without adjusting for plots or other graphics of all indicators that overlay that chart.