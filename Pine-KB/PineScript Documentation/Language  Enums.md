## [Introduction](https://www.tradingview.com/pine-script-docs/language/enums/#introduction)

Pine Script™ Enums, otherwise known as _enumerations_, _enumerated types_, or [enum types](https://www.tradingview.com/pine-script-docs/language/type-system/#enum-types), are unique data types with all possible values (_members_) explicitly defined by the programmer. They provide a human-readable, expressive way to declare distinct sets of _predefined values_ that variables, conditional expressions, and [collections](https://www.tradingview.com/pine-script-docs/language/type-system/#collections) can accept, allowing more strict control over the values used in a script’s logic.

## [Declaring an enum](https://www.tradingview.com/pine-script-docs/language/enums/#declaring-an-enum)

To declare an enum, use the [enum](https://www.tradingview.com/pine-script-reference/v6/#kw_enum) keyword with the following syntax:

```
[export ]enum <enumName>    <field_1>[ = <title_1>]    <field_2>[ = <title_2>]    ...    <field_N>[ = <title_N>]
```

Each **field** in the enum represents a unique, _named member_ (value) of the [enum type](https://www.tradingview.com/pine-script-docs/language/type-system/#enum-types). Users can specify optional “const string” **titles** for enum fields to add extra information about what their values represent. If the programmer does not specify a field’s title, its title is the “string” representation of its name. [Enum inputs](https://www.tradingview.com/pine-script-docs/concepts/inputs/#enum-input) display enum field titles within their dropdown menus in a script’s “Settings/Inputs” tab. Scripts can also retrieve enum field titles using the [str.tostring()](https://www.tradingview.com/pine-script-reference/v6/#fun_str.tostring) function, allowing their use in additional calculations. See [this section](https://www.tradingview.com/pine-script-docs/language/enums/#utilizing-field-titles) below for more information.

While the above syntax may look similar to the syntax for declaring [user-defined types (UDTs)](https://www.tradingview.com/pine-script-docs/language/type-system/#user-defined-types), it’s crucial to understand that [enum types](https://www.tradingview.com/pine-script-docs/language/type-system/#enum-types) and [UDTs](https://www.tradingview.com/pine-script-docs/language/type-system/#user-defined-types) serve different purposes. Scripts use [UDTs](https://www.tradingview.com/pine-script-docs/language/type-system/#user-defined-types) to create [objects](https://www.tradingview.com/pine-script-docs/language/objects/) with “series” fields that can hold values of _any_ specified type. In contrast, enums are distinct groups of “simple” fields representing the specific, _predefined values_ of the same _unique_ type that variables, expressions, and [collections](https://www.tradingview.com/pine-script-docs/language/type-system/#collections) can accept.

For example, this code block declares a `Signal` enum with three fields: `buy`, `sell`, and `neutral`. Each field represents a distinct member (possible value) of the `Signal` [enum type](https://www.tradingview.com/pine-script-docs/language/type-system/#enum-types):

//@enum An enumeration of named values representing buy, sell, and neutral signal states. //@field buy Represents a "Buy signal" state. //@field sell Represents a "Sell signal" state. //@field neutral Represents a "neutral" state. enum Signal buy = "Buy signal" sell = "Sell signal" neutral

Note that:

-   The `Signal` identifier represents the enum’s name, which signifies the _unique type_ the fields belong to.
-   We used the `//@enum` and `//@field` [annotations](https://www.tradingview.com/pine-script-docs/language/script-structure/#compiler-annotations) to document the meaning of the enum and its fields.
-   Unlike the `buy` and `sell` fields, the `neutral` field does not include a specified title. As such, its title is the “string” representation of its _name_ (“neutral”).

To retrieve a member of an enum, reference its field name using _dot notation_ syntax, i.e.:

enumName.fieldName

As with other types, scripts can assign enum members to variables, function parameters, and [UDT](https://www.tradingview.com/pine-script-docs/language/type-system/#user-defined-types) fields, allowing strict control over their allowed values.

For instance, this line of code declares a `mySignal` variable whose value is the `neutral` member of the `Signal` enum. Any value assigned to this variable later must also be of the same [enum type](https://www.tradingview.com/pine-script-docs/language/type-system/#enum-types):

mySignal = Signal.neutral

Note that the above line does not require declaring the variable’s _type_ as `Signal` because the compiler can automatically infer that information from the assigned value. If we use [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) as the initial value instead, we must use `Signal` as the type keyword to specify that `mySignal` will accept a `Signal` member:

Signal mySignal = na

## [Using enums](https://www.tradingview.com/pine-script-docs/language/enums/#using-enums)

Scripts can compare enum members with the [\==](https://www.tradingview.com/pine-script-reference/v6/#op_==) and [!=](https://www.tradingview.com/pine-script-reference/v6/#op_!=) operators and use them in [conditional structures](https://www.tradingview.com/pine-script-docs/language/conditional-structures/), allowing the convenient creation of logical patterns with a reduced risk of unintended values or operations.

The following example declares an `OscType` enum with three fields representing different oscillator choices: `rsi`, `mfi`, and `cci`. The `calcOscillator()` function uses `OscType` members within a [switch](https://www.tradingview.com/pine-script-reference/v6/#kw_switch) structure to determine which oscillator it calculates. The script calls this function using the value from an [enum input](https://www.tradingview.com/pine-script-docs/concepts/inputs/#enum-input) as the `selection` argument and plots the resulting oscillator:

![image](https://www.tradingview.com/pine-script-docs/_astro/Enums-Using-enums-1.nGh65GZL_1UbRFt.webp)

//@version=6 indicator("Using enums demo") //@enum An enumeration of oscillator choices. enum OscType rsi = "Relative Strength Index" mfi = "Money Flow Index" cci = "Commodity Channel Index" //@variable An enumerator (member) of the \`OscType\` enum. OscType oscInput = input.enum(OscType.rsi, "Oscillator type") //@function Calculates one of three oscillators based on a specified \`selection\`. //@param source The series of values to process. //@param length The number of bars in the calculation. //@param selection Determines which oscillator to calculate. calcOscillator(float source, simple int length, OscType selection) => result = switch selection OscType.rsi => ta.rsi(source, length) OscType.mfi => ta.mfi(source, length) OscType.cci => ta.cci(source, length) // Plot the value of a \`calcOscillator()\` call with \`oscInput\` as the \`selection\`. plot(calcOscillator(close, 20, oscInput))

Note that:

-   The `selection` parameter of the `calcOscillator()` function can only take on one of _four_ values: `OscType.rsi`, `OscType.mfi`, `OscType.cci`, or [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).
-   The “Oscillator type” input in the script’s “Settings/Inputs” tab displays all `OscType` field titles in its dropdown. See [this section](https://www.tradingview.com/pine-script-docs/concepts/inputs/#enum-input) to learn more about enum inputs.

It’s crucial to note that each declared enum represents a _unique_ type. Scripts **cannot** compare members of different enums or use such members in expressions requiring a specific [enum type](https://www.tradingview.com/pine-script-docs/language/type-system/#enum-types), even if the fields have identical names and titles.

In this example, we added an `OscType2` enum to the above script and changed the `oscInput` variable to use a member of that enum. The script now raises a _compilation error_ because it can’t use a member of the `OscType2` enum as the `selection` argument in the `calcOscillator()` call:

//@version=6 indicator("Incompatible enums demo") //@enum An enumeration of oscillator choices. enum OscType rsi = "Relative Strength Index" mfi = "Money Flow Index" cci = "Commodity Channel Index" //@enum An enumeration of oscillator choices. Its fields DO NOT represent the same values those in the \`OscType\` enum. enum OscType2 rsi = "Relative Strength Index" mfi = "Money Flow Index" cci = "Commodity Channel Index" //@variable An enumerator (member) of the \`OscType2\` enum. OscType2 oscInput = input.enum(OscType2.rsi, "Oscillator type") //@function Calculates one of three oscillators based on a specified \`selection\`. //@param source The series of values to process. //@param length The number of bars in the calculation. //@param selection Determines which oscillator to calculate. calcOscillator(float source, simple int length, OscType selection) => result = switch selection OscType.rsi => ta.rsi(source, length) OscType.mfi => ta.mfi(source, length) OscType.cci => ta.cci(source, length) // Plot the value of a \`calcOscillator()\` call with \`oscInput\` as the \`selection\`. // Raises a compilation error because only members of \`OscType\` are allowed. plot(calcOscillator(close, 20, oscInput))

### [Utilizing field titles](https://www.tradingview.com/pine-script-docs/language/enums/#utilizing-field-titles)

The “string” titles of an enum’s fields allow programmers to add extra information to each member. These field titles appear within a dropdown in the script’s “Settings/Inputs” tab when calling the [input.enum()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.enum) function.

Scripts can also utilize enum field titles in their calculations and logic. Use the string conversion function ([str.tostring()](https://www.tradingview.com/pine-script-reference/v6/#fun_str.tostring)) on an enum field to access its title.

The following example combines different enum field titles to construct a ticker ID for requesting data from [another context](https://www.tradingview.com/pine-script-docs/concepts/other-timeframes-and-data/). The script declares two enums, `Exchange` and `Pair`, whose respective fields represent _exchange_ and _currency pair_ names. It uses [input.enum()](https://www.tradingview.com/pine-script-reference/v6/#fun_input.enum) to assign user-specified enum members to the `exchangeInput` and `pairInput` variables, then retrieves the “string” titles from those variables with [str.tostring()](https://www.tradingview.com/pine-script-reference/v6/#fun_str.tostring) and concatenates them to form an “Exchange:Symbol” pair for use in a [request.security()](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security) call:

![image](https://www.tradingview.com/pine-script-docs/_astro/Enums-Using-enums-Utilizing-field-titles-1.AzP84EB1_1aSLkU.webp)

//@version=6 indicator("Utilizing field titles demo") //@enum An enumeration of cryptocurrency exchanges. All field titles are the same as the field names. enum Exchange BINANCE BITSTAMP BITFINEX COINBASE KRAKEN //@enum An enumeration of cryptocurrency pairs. All the field titles are the same as the field names. enum Pair BTCUSD ETHUSD SOLUSD XRPUSD //@variable An enumerator (member) of the \`Exchange\` enum. Exchange exchangeInput = input.enum(Exchange.BINANCE, "Exchange") //@variable An enumerator (member) of the \`Pair\` enum. Pair pairInput = input.enum(Pair.BTCUSD, "Pair") //@variable The exchange-symbol pair for the data request. simple string symbol = str.tostring(exchangeInput) + ":" + str.tostring(pairInput) // Plot the \`close\` value requested from the \`symbol\` context. plot(request.security(symbol, timeframe.period, close), "Requested close", color.purple, 3)

Note that:

-   None of the members of the `Exchange` or `Pair` enums have specified titles. Therefore, each field’s title is the “string” representation of its name, as shown by the script’s [enum inputs](https://www.tradingview.com/pine-script-docs/concepts/inputs/#enum-input).
-   Calling the [str.tostring()](https://www.tradingview.com/pine-script-reference/v6/#fun_str.tostring) function on an enum field is the **only** way to retrieve its title for additional calculations. The [str.format()](https://www.tradingview.com/pine-script-reference/v6/#fun_str.format) and `log.*()` functions _cannot_ accept enum members. To use a field’s title in a string formatting function, call [str.tostring()](https://www.tradingview.com/pine-script-reference/v6/#fun_str.tostring) on the field first, then pass the resulting “string” to the function.

## [Collecting enum members](https://www.tradingview.com/pine-script-docs/language/enums/#collecting-enum-members)

Pine Script™ [collections](https://www.tradingview.com/pine-script-docs/language/type-system/#collections) ([arrays](https://www.tradingview.com/pine-script-docs/language/arrays/), [matrices](https://www.tradingview.com/pine-script-docs/language/matrices/), and [maps](https://www.tradingview.com/pine-script-docs/language/maps/)) can store enum members, allowing strict control over the values they can contain. To declare a collection of enum members, include the enum’s _name_ in the collection’s [type template](https://www.tradingview.com/pine-script-docs/language/type-system/#type-templates).

For example, this code block creates an empty [array](https://www.tradingview.com/pine-script-reference/v6/#type_array) to hold members of the `FooBar` enum. The only values this array can allow as elements are `FooBar.foo`, `FooBar.bar`, `FooBar.baz`, and [na](https://www.tradingview.com/pine-script-reference/v6/#var_na):

//@variable An enumeration of miscellaneous named members. enum FooBar foo bar baz //@variable An array that can only contain the following values: \`FooBar.foo\`, \`FooBar.bar\`, \`FooBar.baz\`, \`na\`. array<FooBar> fooBarArray = array.new<FooBar>()

Enums are particularly helpful when working with [maps](https://www.tradingview.com/pine-script-docs/language/maps/), as unlike other _non-fundamental_ [types](https://www.tradingview.com/pine-script-docs/language/type-system/#types), scripts can declare [maps](https://www.tradingview.com/pine-script-docs/language/maps/) with _keys_ of an [enum type](https://www.tradingview.com/pine-script-docs/language/type-system/#enum-types), enabling strict control over all possible keys allowed in their key-value pairs.

The following example uses a [map](https://www.tradingview.com/pine-script-reference/v6/#type_map) with enum keys and “int” values to track and count signal states across chart bars. The script’s `Signal` enum contains five fields representing specific named states. The `signalCounters` [map](https://www.tradingview.com/pine-script-reference/v6/#type_map) uses the `Signal` name as the _first keyword_ in its [type template](https://www.tradingview.com/pine-script-docs/language/type-system/#type-templates) to specify that it can only accept `Signal` members as keys.

The script uses a [switch](https://www.tradingview.com/pine-script-reference/v6/#kw_switch) structure to calculate a `signalState` variable whose value is a member of the `Signal` enum, which it uses to determine the counter value to update in the `signalCounters` map. It constructs a “string” to represent the key-value pairs of the [map](https://www.tradingview.com/pine-script-reference/v6/#type_map) and displays the result in a single-cell [table](https://www.tradingview.com/pine-script-reference/v6/#type_table) on the last chart bar:

![image](https://www.tradingview.com/pine-script-docs/_astro/Enums-Collecting-enums-1.ZTw8lVuz_1tEOAf.webp)

//@version=6 indicator("Collecting enum members demo", overlay = true) //@enum An enumeration of named signal states. enum Signal strongBuy = "Strong buy" buy = "Buy" neutral = "Neutral" sell = "Sell" strongSell = "Strong sell" //@variable The number of bars in the signal calculation. int lengthInput = input.int(50, "Length", 2) //@variable A map of \`Signal.\*\` keys and "int" values counting the number of bars with each signal state. // Allowed keys: \`Signal.strongBuy\`, \`Signal.buy\`, \`Signal.neutral\`, \`Signal.sell\`, \`Signal.strongSell\`, \`na\`. var map<Signal, float> signalCounters = map.new<Signal, float>() //@variable A single-cell table displaying the key-value pairs of the \`signalCounters\` map. var table infoTable = table.new(position.top\_right, 1, 1, chart.fg\_color) if barstate.isfirst // Put \`Signal.\*\`-"int" pairs into the \`signalCounters\` map to establish insertion order. signalCounters.put(Signal.strongBuy, 0) signalCounters.put(Signal.buy, 0) signalCounters.put(Signal.neutral, 0) signalCounters.put(Signal.sell, 0) signalCounters.put(Signal.strongSell, 0) // Initialize the \`infoTable\` cell. infoTable.cell(0, 0, text\_color = chart.bg\_color, text\_halign = text.align\_left, text\_size = size.large) // Calculate the EMA and Percent rank of \`source\` data over \`length\` bars. float ema = ta.ema(close, lengthInput) float rank = ta.percentrank(close, lengthInput) //@variable A \`Signal\` member representing the current signal state based on \`ema\` and \`rank\` values. Signal signalState = switch close > ema => rank > 70 ? Signal.strongBuy : rank > 50 ? Signal.buy : Signal.neutral close < ema => rank < 30 ? Signal.strongSell : rank < 50 ? Signal.sell : Signal.neutral => Signal.neutral // Add 1 to the value in the \`signalCounters\` map associated with the \`signalState\` key. signalCounters.put(signalState, signalCounters.get(signalState) + 1) // Update the \`infoTable\` cell's text using the keys and values from the \`signalCounters\` map on the last bar. if barstate.islast string tableText = "" for \[state, count\] in signalCounters tableText += str.tostring(state) + ": " + str.tostring(count) + "\\n" infoTable.cell\_set\_text(0, 0, str.trim(tableText))

Note that:

-   The `signalCounters` map can contain up to _six_ key-value pairs, as the `Signal` enum has _five_ predefined values, plus a possible value of [na](https://www.tradingview.com/pine-script-reference/v6/#var_na), and [maps](https://www.tradingview.com/pine-script-docs/language/maps/) cannot contain _repetitive_ keys.
-   The script declares the `signalCounters` variable using the [var](https://www.tradingview.com/pine-script-reference/v6/#kw_var) keyword, signifying that the assigned [map](https://www.tradingview.com/pine-script-reference/v6/#type_map) instance persists across executions.
-   On the first chart bar, the script uses five [map.put()](https://www.tradingview.com/pine-script-reference/v6/#fun_map.put) calls to establish the _insertion order_ of keys in the `signalCounters` map. See [this section](https://www.tradingview.com/pine-script-docs/language/maps/#mapkeys-and-mapvalues) of the [Maps](https://www.tradingview.com/pine-script-docs/language/maps/) page for more information.
-   To minimize _resource usage_, the script declares the `infoTable` and initializes its cell on the _first bar_, then updates the cell’s text on the _latest bar_. See [this section](https://www.tradingview.com/pine-script-docs/writing/profiling-and-optimization/#reducing-drawing-updates) of the [Profiling and optimization](https://www.tradingview.com/pine-script-docs/writing/profiling-and-optimization/) page to learn more.

## [Shadowing](https://www.tradingview.com/pine-script-docs/language/enums/#shadowing)

In contrast to [user-defined types (UDTs)](https://www.tradingview.com/pine-script-docs/language/type-system/#user-defined-types), which can have names that _shadow_ some built-in types or namespaces, enum types require _unique_ names that do **not** match any built-in types or namespaces.

For example, this code declares four enums named `Syminfo`, `syminfo`, `polyline`, and `ta`. The last three all cause a compilation error because their names match built-in namespaces:

//@version=6 indicator("Shadowing demo") // Naming an enum "Syminfo" with a capital "S" works without an issue. enum Syminfo abcd // In contrast, the names "syminfo", "polyline", "ta", etc. cause a compilation error because they match // built-in namespaces: enum syminfo abcd enum polyline abcd enum ta abcd