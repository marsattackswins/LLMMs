## [The if statement is too long](https://www.tradingview.com/pine-script-docs/error-messages/#the-if-statement-is-too-long)

This error occurs when the indented code inside an [if statement](https://www.tradingview.com/pine-script-reference/v6/#kw_if) is too large for the compiler. Because of how the compiler works, you won’t receive a message telling you exactly how many lines of code you are over the limit. The only solution now is to break up your [if statement](https://www.tradingview.com/pine-script-reference/v6/#kw_if) into smaller parts (functions or smaller [if statements](https://www.tradingview.com/pine-script-reference/v6/#kw_if)). The example below shows a reasonably lengthy [if statement](https://www.tradingview.com/pine-script-reference/v6/#kw_if); theoretically, this would throw `line 4: if statement is too long`:

//@version=6 indicator("My script") var e = 0 if barstate.islast a = 1 b = 2 c = 3 d = 4 e := a + b + c + d plot(e)

To fix this code, you could move these lines into their own function:

//@version=6 indicator("My script") var e = 0 doSomeWork() => a = 1 b = 2 c = 3 d = 4 result = a + b + c + d if barstate.islast e := doSomeWork() plot(e)

## [Script requesting too many securities](https://www.tradingview.com/pine-script-docs/error-messages/#script-requesting-too-many-securities)

The maximum number of securities in script is limited to 40. If you declare a variable as a `request.security` function call and then use that variable as input for other variables and calculations, it will not result in multiple `request.security` calls. But if you will declare a function that calls `request.security` --- every call to this function will count as a `request.security` call.

It is not easy to say how many securities will be called looking at the source code. Following example have exactly 3 calls to `request.security` after compilation:

//@version=6 indicator("Securities count") a = request.security(syminfo.tickerid, '42', close) // (1) first unique security call b = request.security(syminfo.tickerid, '42', close) // same call as above, will not produce new security call after optimizations plot(a) plot(a + 2) plot(b) sym(p) => // no security call on this line request.security(syminfo.tickerid, p, close) plot(sym('D')) // (2) one indirect call to security plot(sym('W')) // (3) another indirect call to security c = request.security(syminfo.tickerid, timeframe.period, open) // result of this line is never used, and will be optimized out

## [Script could not be translated from: null](https://www.tradingview.com/pine-script-docs/error-messages/#script-could-not-be-translated-from-null)

study($)

Usually this error occurs in version 1 Pine scripts, and means that code is incorrect. Pine Script™ of version 2 (and higher) is better at explaining errors of this kind. So you can try to switch to version 2 by adding a [special attribute](https://www.tradingview.com/pine-script-docs/language/script-structure/#version) in the first line. You’ll get `line 2: no viable alternative at character '$'`:

// @version=2 study($)

## [line 2: no viable alternative at character ’$’](https://www.tradingview.com/pine-script-docs/error-messages/#line-2-no-viable-alternative-at-character-)

This error message gives a hint on what is wrong. `$` stands in place of string with script title. For example:

// @version=2 study("title")

## [Mismatched input <…> expecting <???>](https://www.tradingview.com/pine-script-docs/error-messages/#mismatched-input--expecting-)

Same as `no viable alternative`, but it is known what should be at that place. Example:

//@version=6 indicator("My Script") plot(1)

`line 3: mismatched input 'plot' expecting 'end of line without line continuation'`

To fix this you should start line with `plot` on a new line without an indent:

//@version=6 indicator("My Script") plot(1)

## [Loop is too long (> 500 ms)](https://www.tradingview.com/pine-script-docs/error-messages/#loop-is-too-long--500-ms)

We limit the computation time of loop on every historical bar and realtime tick to protect our servers from infinite or very long loops. This limit also fail-fast indicators that will take too long to compute. For example, if you’ll have 5000 bars, and indicator takes 500 milliseconds to compute on each of bars, it would have result in more than 16 minutes of loading:

//@version=6 indicator("Loop is too long", max\_bars\_back = 101) s = 0 for i = 1 to 1e3 // to make it longer for j = 0 to 100 if timestamp(2017, 02, 23, 00, 00) <= time\[j\] and time\[j\] < timestamp(2017, 02, 23, 23, 59) s := s + 1 plot(s)

It might be possible to optimize algorithm to overcome this error. In this case, algorithm may be optimized like this:

//@version=6 indicator("Loop is too long", max\_bars\_back = 101) bar\_back\_at(t) => i = 0 step = 51 for j = 1 to 100 if i < 0 i := 0 break if step == 0 break if time\[i\] >= t i := i + step i else i := i - step i step := step / 2 step i s = 0 for i = 1 to 1e3 // to make it longer s := s - bar\_back\_at(timestamp(2017, 02, 23, 23, 59)) + bar\_back\_at(timestamp(2017, 02, 23, 00, 00)) s plot(s)

## [Script has too many local variables](https://www.tradingview.com/pine-script-docs/error-messages/#script-has-too-many-local-variables)

This error appears if the script is too large to be compiled. A statement `var=expression` creates a local variable for `var`. Apart from this, it is important to note, that auxiliary variables can be implicitly created during the process of a script compilation. The limit applies to variables created both explicitly and implicitly. The limitation of 1000 variables is applied to each function individually. In fact, the code placed in a _global_ scope of a script also implicitly wrapped up into the main function and the limit of 1000 variables becomes applicable to it. There are few refactorings you can try to avoid this issue:

var1 = expr1 var2 = expr2 var3 = var1 + var2

can be converted into:

var3 = expr1 + expr2

## [Pine Script™ cannot determine the referencing length of a series. Try using max\_bars\_back in the indicator or strategy function](https://www.tradingview.com/pine-script-docs/error-messages/#pine-script-cannot-determine-the-referencing-length-of-a-series-try-using-max_bars_back-in-the-indicator-or-strategy-function)

The error appears in cases where Pine Script™ wrongly autodetects the required maximum length of series used in a script. This happens when a script’s flow of execution does not allow Pine Script™ to inspect the use of series in branches of conditional statements (`if`, `iff` or `?`), and Pine Script™ cannot automatically detect how far back the series is referenced. Here is an example of a script causing this problem:

//@version=6 indicator("Requires max\_bars\_back") test = 0.0 if bar\_index > 1000 test := ta.roc(close, 20) plot(test)

In order to help Pine Script™ with detection, you should add the `max_bars_back` parameter to the script’s `indicator` or `strategy` function:

//@version=6 indicator("Requires max\_bars\_back", max\_bars\_back = 20) test = 0.0 if bar\_index > 1000 test := ta.roc(close, 20) plot(test)

You may also resolve the issue by taking the problematic expression out of the conditional branch, in which case the `max_bars_back` parameter is not required:

//@version=6 indicator("My Script") test = 0.0 roc20 = ta.roc(close, 20) if bar\_index > 1000 test := roc20 plot(test)

In cases where the problem is caused by a **variable** rather than a built-in **function** (`vwma` in our example), you may use the `max_bars_back` function to explicitly define the referencing length for that variable only. This has the advantage of requiring less runtime resources, but entails that you identify the problematic variable, e.g., variable `s` in the following example:

//@version=6 indicator("My Script") f(off) => t = 0.0 s = close if bar\_index > 242 t := s\[off\] t plot(f(301))

This situation can be resolved using the `max_bars_back` **function** to define the referencing length of variable `s` only, rather than for all the script’s variables:

//@version=6 indicator("My Script") f(off) => t = 0.0 s = close max\_bars\_back(s, 301) if bar\_index > 242 t := s\[off\] t plot(f(301))

When using drawings that refer to previous bars through `bar_index[n]` and `xloc = xloc.bar_index`, the time series received from this bar will be used to position the drawings on the time axis. Therefore, if it is impossible to determine the correct size of the buffer, this error may occur. To avoid this, you need to use `max_bars_back(time, n)`. This behavior is described in more detail in the section about [drawings](https://www.tradingview.com/pine-script-docs/concepts/lines-and-boxes/#historical-buffer-and-max_bars_back).

## [Memory limits exceeded. The study allocates X times more than allowed](https://www.tradingview.com/pine-script-docs/error-messages/#memory-limits-exceeded-the-study-allocates-x-times-more-than-allowed)

The most common cause for this error is returning [objects](https://www.tradingview.com/pine-script-docs/language/objects/#objects) and [collections](https://www.tradingview.com/pine-script-docs/language/type-system/#collections) from [request.\*()](https://www.tradingview.com/pine-script-docs/concepts/other-timeframes-and-data/) functions. Other possible causes include unnecessary drawing updates, excess historical buffer capacity, or inefficient use of [max\_bars\_back](https://www.tradingview.com/pine-script-reference/v6/#fun_max_bars_back).

### [**Returning collections from `request.*()` functions**](https://www.tradingview.com/pine-script-docs/error-messages/#returning-collections-from-request-functions)

A common source of the “_Memory limits exceeded_” error is returning [objects](https://www.tradingview.com/pine-script-docs/language/objects/#objects) or [collections](https://www.tradingview.com/pine-script-docs/language/type-system/#collections) from another chart symbol or timeframe using [request.\*()](https://www.tradingview.com/pine-script-docs/concepts/other-timeframes-and-data/) functions.

When requesting data from other contexts, the data for _each bar_ is copied and stored in memory to allow the script to reference it later in the main context. This can use a lot of memory, depending on the data. Requesting large collections can easily lead to excessive memory consumption.

Let’s look at an example script where we [request](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security) data to calculate the [balance of power (BOP)](https://www.tradingview.com/support/solutions/43000589100-balance-of-power-bop/) for the symbol at a higher timeframe. Here, the _request expression_ is a [custom function](https://www.tradingview.com/pine-script-docs/language/user-defined-functions/) that populates a [persistent array](https://www.tradingview.com/pine-script-docs/language/arrays/#using-var-and-varip-keywords) with our calculated BOP values, returning the _full array_ to the main context on _each_ bar. We intend to use these stored array values to calculate and plot the [average](https://www.tradingview.com/pine-script-reference/v6/#fun_array.avg) BOP in the main context. However, returning every array instance consumes a lot of memory, and so this script can throw a memory error on charts with a sufficiently long history:

//@version=5 indicator("BOP array in higher timeframe context", "Memory limit demo") //@variable User-input length for calculating average of BOP values. int avgLength = input.int(5, "Average BOP Length", minval = 1) //Returns a copy of the \`dataArray\` on every bar, which uses a lot of memory. dataFunction() => //@variable Persistent array containing the "balance of power" (BOP) values for all bars from the higher timeframe. var array<float> dataArray = array.new\_float(0) //@variable The "balance of power" percentage calculated for the current bar. float bop = (close - open) / (high - low) \* 100 dataArray.push(bop) //Return the full collection. dataArray // Request the full BOP array from the 1D timeframe. array<float> reqData = request.security(syminfo.tickerid, "1D", dataFunction()) // Plot zero line. hline(0, "Zero line", color.gray, hline.style\_dotted) // Latest BOP value and average BOP are calculated in the main context if \`reqData\` is not \`na\`. //@variable The latest BOP value from the \`reqData\` array. float latestValue = na //@variable The average of the last \`avgLength\` BOP values. float avgBOP = na if not na(reqData) // Retrieve BOP value for the current main context bar. latestValue := reqData.last() // Calculate the average BOP for the most-recent values from the higher timeframe array. //@variable Size of the \`reqData\` array returned from the higher timeframe. int dataSize = reqData.size() //@variable A subset of the latest values from the \`reqData\` array. Its size is determined by the \`avgLength\` set. array<float> lastValues = dataSize >= avgLength ? reqData.slice(dataSize - avgLength, dataSize): reqData avgBOP := lastValues.avg() // Plot the BOP value and average line. color plotColor = latestValue >= 0 ? color.aqua : color.orange plot(latestValue, "BOP", plotColor, style = plot.style\_columns) plot(avgBOP, "Avg", color.purple, linewidth = 3)

### [How do I fix this?](https://www.tradingview.com/pine-script-docs/error-messages/#how-do-i-fix-this)

Optimize requests and limit the data returned to the main context to ensure that only the _minimum necessary_ data is stored in memory.

If possible, try to return _calculated results_ directly rather than returning the collections themselves, or only return collections _conditionally_, when they are necessary in the main context.

Let’s consider a few common scenarios where scripts need specific data in the main context.

#### [Return last state only](https://www.tradingview.com/pine-script-docs/error-messages/#return-last-state-only)

If a script needs only the _last state_ of a requested collection in the main context: use an [if](https://www.tradingview.com/pine-script-reference/v6/#kw_if) [barstate.islast](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.islast) condition to return a copy of the _last bar’s collection_ only.

Here, we modified our script to display only the _latest_ average BOP (a single value), rather than plotting an average line. The updated request function now returns the calculated BOP values directly for each bar, and returns the higher timeframe’s array only on the last bar:

![image](https://www.tradingview.com/pine-script-docs/_astro/Errors-Return-last-state-only.B7DlHDxT_1Srw3K.webp)

//@version=5 indicator("BOP array on last bar", "Memory limit demo") //@variable User-input length for calculating average of BOP values. int avgLength = input.int(5, "Average BOP Length", minval = 1) // Returns the calculated \`bop\` each bar, and a copy of the \`dataArray\` on the last bar or \`na\` otherwise. dataFunction() => //@variable Persistent array containing the "balance of power" (BOP) values for all higher timeframe bars. var array<float> dataArray = array.new\_float(0) //@variable The "balance of power" percentage calculated for the current higher timeframe bar. float bop = (close - open) / (high - low) \* 100 dataArray.push(bop) // Return the collection on the last bar only. if barstate.islast \[bop, dataArray\] else \[bop, na\] // Request calculated BOP value, and BOPs array if on last bar, from the higher timeframe. \[reqValue, reqData\] = request.security(syminfo.tickerid, "1D", dataFunction()) // Plot zero line. hline(0, "Zero line", color.gray, hline.style\_dotted) // Plot the BOP value for each main context bar. color plotColor = reqValue >= 0 ? color.aqua : color.orange plot(reqValue, "BOP", plotColor, style = plot.style\_columns) // Calculate the average BOP for most-recent values from the higher timeframe array, and display result in a table cell. if not na(reqData) //@variable Size of the \`reqData\` array returned from the higher timeframe. int dataSize = reqData.size() //@variable A subset of the latest values from the \`reqData\` array. Its size is determined by the \`avgLength\` set. array<float> lastValues = dataSize >= avgLength ? reqData.slice(dataSize - avgLength, dataSize): reqData //@variable The average of the last \`avgLength\` BOP values. float avgBOP = lastValues.avg() // Display latest average value in a single-cell table. var table displayTable = table.new(position.bottom\_right, 1, 1, color.purple) displayTable.cell(0, 0, "Avg of last " + str.tostring(avgLength) + " BOPs: " + str.tostring(avgBOP, "##.##") + "%", text\_color = color.white)

#### [Return calculated results](https://www.tradingview.com/pine-script-docs/error-messages/#return-calculated-results)

If a script needs the _result_ of a calculation on a collection, but does not need the collection itself in the main context, use a [user-defined function](https://www.tradingview.com/pine-script-docs/language/user-defined-functions/) as the request expression. The function can calculate on the collection in the _requested_ context and return only the result to the main context.

For example, we can calculate the average BOP directly within our request function. Therefore, only the calculated values are stored in memory, and the request expression returns a tuple (current BOP and average BOP) to plot the results in the main context:

![image](https://www.tradingview.com/pine-script-docs/_astro/Errors-Return-calculated-results.Do61vtAy_Z1MO38Y.webp)

//@version=5 indicator("Return BOP results only", "Memory limit demo") //@variable User-input length for calculating average of BOP values. int avgLength = input.int(5, "Average BOP Length", minval = 1) // Returns the calculated \`bop\` and \`avgBOP\` values directly. dataFunction() => //@variable Persistent array containing the "balance of power" (BOP) values for all higher timeframe bars. var array<float> dataArray = array.new\_float(0) //@variable The "balance of power" percentage calculated for the current higher timeframe bar. float bop = (close - open) / (high - low) \* 100 dataArray.push(bop) // Calculate the average BOP for the \`avgLength\` most-recent values. //@variable Size of the \`dataArray\`. int dataSize = dataArray.size() //@variable A subset of the latest values from the \`dataArray\`. Its size is determined by the \`avgLength\` set. array<float> lastValues = dataSize >= avgLength ? dataArray.slice(dataSize - avgLength, dataSize): dataArray //@variable The average of the last \`avgLength\` BOP values. float avgBOP = lastValues.avg() //Return the calculated results. \[bop, avgBOP\] // Request BOP and average BOP values from the higher timeframe. \[reqValue, reqAverage\] = request.security(syminfo.tickerid, "1D", dataFunction()) // Plot zero line. hline(0, "Zero line", color.gray, hline.style\_dotted) // Plot the BOP value and average line. color plotColor = reqValue >= 0 ? color.aqua : color.orange plot(reqValue, "BOP", plotColor, style = plot.style\_columns) plot(reqAverage, "Avg", color.purple, linewidth = 3)

#### [Return the collection on some bars](https://www.tradingview.com/pine-script-docs/error-messages/#return-the-collection-on-some-bars)

If a script needs the _collection itself_ in the main context, but _not for_ _every bar_, use [conditional expressions](https://www.tradingview.com/pine-script-reference/v6/#kw_if) to return only the necessary collections to the main context, returning [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) otherwise. The logic in the main context can then address the [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) gaps in the series and perform its desired actions on the reduced collections.

For example, if we want to calculate the average BOP across each _month_ instead of using a user-input length, we can return the array from the requested context only when there is a change to a new month, returning [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) otherwise. We then maintain the previous month’s values in the main context to keep a valid array for all intra-month bars:

![image](https://www.tradingview.com/pine-script-docs/_astro/Errors-Return-the-collection-on-some-bars.CQvTHovc_iqEih.webp)

//@version=5 indicator("Monthly BOP array", "Memory limit demo") // Returns the calculated \`bop\`, and a copy of the \`dataArray\` on a month's first trading day only, or \`na\` otherwise. dataFunction() => //@variable Persistent array containing the "balance of power" (BOP) values for all higher timeframe bars. var array<float> dataArray = array.new\_float(0) // When a new month starts, return monthly data array to calculate average BOP for completed month. //@variable Array is \`na\` except on first trading day of each month, when it contains completed month's BOP values. array<float> returnArray = na //@variable Is \`true\` on the first bar of each month, \`false\` otherwise. bool isNewMonth = timeframe.change("1M") if isNewMonth returnArray := dataArray //Clear persistent array to start storing new month's data. if isNewMonth\[1\] dataArray.clear() //@variable The "balance of power" percentage calculated for the current higher timeframe bar. float bop = (close - open) / (high - low) \* 100 dataArray.push(bop) //Return the calculated result and the \`returnArray\`. \[bop, returnArray\] // Request BOP data from the higher timeframe. (Returns calculated BOP and array of BOP values if new month starts) \[reqValue, reqData\] = request.security(syminfo.tickerid, "1D", dataFunction()) // Calculate the average BOP for the most-recent completed month. //@variable Persistent array that holds the BOP values for the most-recent completed month. var array<float> completedMonthBOPs = array.new\_float(0) // If new month starts (i.e., \`reqData\` is not returned as \`na\`), then \`completedMonthBOPs\` is updated with new values. // Otherwise, it persists the last valid values for the rest of the month to adjust for \`na\` gaps. completedMonthBOPs := na(reqData) ? completedMonthBOPs : reqData //@variable The average BOP for the most-recent completed month. float avgBOP = completedMonthBOPs.avg() // Plot the BOP value and average line. color plotColor = reqValue >= 0 ? color.aqua : color.orange plot(reqValue, "BOP", plotColor, style = plot.style\_columns) plot(avgBOP, "Avg", color.purple, linewidth = 3)

### [Other possible error sources and their fixes](https://www.tradingview.com/pine-script-docs/error-messages/#other-possible-error-sources-and-their-fixes)

There are a few other ways to optimize scripts to consume less memory.

#### [**Minimize `request.*()` calls**](https://www.tradingview.com/pine-script-docs/error-messages/#minimize-request-calls)

The [request.\*()](https://www.tradingview.com/pine-script-docs/concepts/other-timeframes-and-data/) function calls can be computationally expensive, because they retrieve data from other contexts, which can often require significant resource usage. Excessive or inefficient requests can easily cause scripts to reach the memory limit.

This memory consumption is especially substantial for scripts requesting data from [_lower timeframes_](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security_lower_tf), where the request function returns an [array](https://www.tradingview.com/pine-script-reference/v6/#type_array) of multiple lower timeframe bars for _each_ main context bar. For example, requesting “1” data on a “1D” chart returns hundreds of “1” bars for each “1D” bar that executes the request. In the process, the script must allocate memory to store all the requested data arrays so that it can access them later in the main context, which quickly increases the memory consumption.

Programmers can reduce the number of requested expressions by:

-   Removing unnecessary `request.*()` function calls.
-   Changing the requested timeframe to a higher resolution.
-   Condensing multiple requests to the _same_ context into a single `request.*()` call.
-   Adjusting the `request.*()` function’s [calc\_bars\_count](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security) parameter to restrict the historical data points in the requested context.

See [this section](https://www.tradingview.com/pine-script-docs/writing/profiling-and-optimization/#minimizing-request-calls) in the User Manual for more information on optimizing `request.*()` calls.

#### [**Refrain from using `max_bars_back` unless necessary**](https://www.tradingview.com/pine-script-docs/error-messages/#refrain-from-using-max_bars_back-unless-necessary)

The `max_bars_back` parameter of an [indicator](https://www.tradingview.com/pine-script-reference/v6/#fun_indicator) or [strategy](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy) sets the size of the _history buffer_ for all series variables in a script. The history buffer determines the number of historical references _stored in memory_ for the script’s built-in and user-defined variables.

By default, the Pine Script™ runtime automatically allocates an appropriate buffer for each variable. Therefore, the `max_bars_back` parameter and [function](https://www.tradingview.com/pine-script-reference/v6/#fun_max_bars_back) are only necessary when Pine [cannot determine the referencing length of a series](https://www.tradingview.com/support/solutions/43000587849-i-see-pine-cannot-determine-the-referencing-length-of-a-series-try-using-max-bars-back-error/).

If you encounter this referencing length error, ensure that you set the `max_bars_back` value appropriately to your script’s needs. Setting a value that’s too large can lead to excessive memory consumption, as it stores unnecessary historical data that the script ultimately doesn’t use. Read up on how to optimize using `max_bars_back` [in our Help Center](https://www.tradingview.com/chart/?solution=43000587849).

#### [Minimize historical buffer calculations](https://www.tradingview.com/pine-script-docs/error-messages/#minimize-historical-buffer-calculations)

The Pine Script™ runtime automatically creates historical buffers for all variables and function calls in a script. It determines the size of a buffer based on the _historical references_ needed in the code (the references made using the [\[\]](https://www.tradingview.com/pine-script-docs/language/operators/#--history-referencing-operator) history-referencing operator).

As the script runs across the dataset, referencing distant points in bar history can cause the script to restart its execution on previous bars to adjust its historical buffer size (see this [User Manual article](https://www.tradingview.com/pine-script-docs/writing/profiling-and-optimization/#minimizing-historical-buffer-calculations) to learn more). Larger buffers in turn lead to an increase in memory consumption and can result in a runtime error. Ensure that scripts are referencing _necessary_ historical values only, and avoid referencing very distant points in history when possible.

You can use the [indicator()](https://www.tradingview.com/pine-script-reference/v6/#fun_indicator) function’s `calc_bars_count` parameter or the [max\_bars\_back()](https://www.tradingview.com/pine-script-reference/v6/#fun_max_bars_back) function to _manually restrict_ the historical data capacity on a script-wide or variable-specific scale. However, be aware that these methods can also cause memory consumption issues of their own if used improperly.

#### [Reduce drawing updates for tables](https://www.tradingview.com/pine-script-docs/error-messages/#reduce-drawing-updates-for-tables)

[Tables](https://www.tradingview.com/pine-script-docs/concepts/tables/) only display their _last state_ on a chart. Any updates to a table on historical bars are redundant, because they are not visible. To use the least memory, draw the table _once_, and fill it on the last bar.

Use the [var](https://www.tradingview.com/pine-script-reference/v6/#kw_var) keyword to declare table objects once. Enclose all other setter function calls in a conditional [if](https://www.tradingview.com/pine-script-reference/v6/#kw_if) [barstate.islast](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.islast) block for better performance. For more about tables, see this [User Manual article](https://www.tradingview.com/pine-script-docs/concepts/tables/).

#### [Do not update drawings on historical bars](https://www.tradingview.com/pine-script-docs/error-messages/#do-not-update-drawings-on-historical-bars)

Similar to tables, any updates to drawing objects such as [lines](https://www.tradingview.com/pine-script-docs/concepts/lines-and-boxes/#lines) and [labels](https://www.tradingview.com/pine-script-docs/concepts/text-and-shapes/#labels) that are made on historical bars are never seen by the user. The user only sees updates on _realtime_ bars.

Eliminate updates to historical drawings during historical bars wherever possible. For more information, see [this User Manual section](https://www.tradingview.com/pine-script-docs/writing/profiling-and-optimization/#reducing-drawing-updates).

#### [Minimize total drawings stored for a chart](https://www.tradingview.com/pine-script-docs/error-messages/#minimize-total-drawings-stored-for-a-chart)

[Drawing objects](https://www.tradingview.com/pine-script-docs/language/type-system/#drawing-types) such as [lines](https://www.tradingview.com/pine-script-docs/concepts/lines-and-boxes/#lines) and [labels](https://www.tradingview.com/pine-script-docs/concepts/text-and-shapes/#labels) can consume a lot of memory, especially if a script _recreates_ drawings unnecessarily.

For example, if a script draws a line from point `x1` to `x2`, then needs to update the line’s endpoint (`x2`), it’s more computationally expensive to delete the existing line and redraw a new line from `x1` to `x3`. Instead, using the _setter_ function [line.set\_x2()](https://www.tradingview.com/pine-script-reference/v6/#fun_line.set_x2) to update the existing line’s endpoint is more efficient.

Look for ways to optimize drawing objects in a script:

-   Reduce the number of redrawn objects by initializing drawing object _identifiers_ and using their setter functions to modify properties.
    
-   Remove unnecessary chart drawings using the `delete()` functions (e.g., [line.delete()](https://www.tradingview.com/pine-script-reference/v6/#fun_line.delete) and [label.delete()](https://www.tradingview.com/pine-script-reference/v6/#fun_label.delete)).
    
-   Reduce an indicator’s maximum drawings limit using the `max_lines_count` or `max_labels_count` [parameters](https://www.tradingview.com/pine-script-reference/v6/#fun_indicator).
    

#### [Filter dates in strategies](https://www.tradingview.com/pine-script-docs/error-messages/#filter-dates-in-strategies)

The total number of trades or orders in a [strategy](https://www.tradingview.com/pine-script-docs/concepts/strategies/) can impact the memory consumption of a script. For large datasets, reduce the number of unnecessary historical orders stored in memory by limiting the _starting point_ of your strategy.

You can filter the strategy’s date by adding a [conditional expression](https://www.tradingview.com/pine-script-reference/v6/#kw_if) that compares the bar time to a specified timestamp to only place entry/exit orders beyond a certain date.

See an example of date filtering in strategies [here](https://www.pinecoders.com/faq_and_code/#how-do-i-implement-date-range-filtering-in-strategies).