## **Types**

### **array**

Keyword used to explicitly declare the "array" type of a variable or a parameter. Array objects (or IDs) can be created with the [array.new\<type\>](https://www.tradingview.com/pine-script-reference/v6/#fun_array.new\<type\>), [array.from](https://www.tradingview.com/pine-script-reference/v6/#fun_array.from) function.  
Example  
//@version=6  
indicator("array", overlay=true)  
array\<float\> a \= na  
a := array.new\<float\>(1, close)  
plot(array.get(a, 0))  
Remarks  
Array objects are always of "series" form.  
See also  
[var](https://www.tradingview.com/pine-script-reference/v6/#kw_var)[line](https://www.tradingview.com/pine-script-reference/v6/#type_line)[label](https://www.tradingview.com/pine-script-reference/v6/#type_label)[table](https://www.tradingview.com/pine-script-reference/v6/#type_table)[box](https://www.tradingview.com/pine-script-reference/v6/#type_box)[array.new\<type\>](https://www.tradingview.com/pine-script-reference/v6/#fun_array.new\<type\>)[array.from](https://www.tradingview.com/pine-script-reference/v6/#fun_array.from)

### **bool**

Keyword used to explicitly declare the "bool" (boolean) type of a variable or a parameter. "Bool" variables can have values [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) or [false](https://www.tradingview.com/pine-script-reference/v6/#const_false).  
Example  
//@version=6  
indicator("bool")  
bool b \= true    // Same as \`b \= true\`  
plot(b ? open : close)  
Remarks  
Explicitly mentioning the type in a variable declaration is optional. Learn more about Pine Script® types in the User Manual page on the [Type System](https://www.tradingview.com/pine-script-docs/language/type-system/).  
See also  
[var](https://www.tradingview.com/pine-script-reference/v6/#kw_var)[varip](https://www.tradingview.com/pine-script-reference/v6/#kw_varip)[int](https://www.tradingview.com/pine-script-reference/v6/#type_int)[float](https://www.tradingview.com/pine-script-reference/v6/#type_float)[color](https://www.tradingview.com/pine-script-reference/v6/#type_color)[string](https://www.tradingview.com/pine-script-reference/v6/#type_string)[true](https://www.tradingview.com/pine-script-reference/v6/#const_true)[false](https://www.tradingview.com/pine-script-reference/v6/#const_false)

### **box**

Keyword used to explicitly declare the "box" type of a variable or a parameter. Box objects (or IDs) can be created with the [box.new](https://www.tradingview.com/pine-script-reference/v6/#fun_box.new) function.  
Example  
//@version=6  
indicator("box")  
// Empty \`box1\` box ID.  
var box box1 \= na  
// \`box\` type is unnecessary because \`box.new()\` returns a "box" type.  
var box2 \= box.new(na, na, na, na)  
box3 \= box.new(time, open, time \+ 60 \* 60 \* 24, close, xloc=xloc.bar\_time)  
Remarks  
Box objects are always of "series" form.  
See also  
[var](https://www.tradingview.com/pine-script-reference/v6/#kw_var)[line](https://www.tradingview.com/pine-script-reference/v6/#type_line)[label](https://www.tradingview.com/pine-script-reference/v6/#type_label)[table](https://www.tradingview.com/pine-script-reference/v6/#type_table)[box.new](https://www.tradingview.com/pine-script-reference/v6/#fun_box.new)

### **chart.point**

Keyword to explicitly declare the type of a variable or parameter as `chart.point`. Scripts can produce `chart.point` instances using the [chart.point.from\_time](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.from_time), [chart.point.from\_index](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.from_index), [chart.point.now](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.now), and [chart.point.new](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.new) functions.  
Fields  
index (series int) The x-coordinate of the point, expressed as a bar index value.  
time (series int) The x-coordinate of the point, expressed as a UNIX time value, in milliseconds.  
price (series float) The y-coordinate of the point.  
See also  
[polyline](https://www.tradingview.com/pine-script-reference/v6/#type_polyline)

### **color**

Keyword used to explicitly declare the "color" type of a variable or a parameter.  
Example  
//@version=6  
indicator("color", overlay \= true)

color textColor \= color.green  
color labelColor \= \#FF000080 // Red color (FF0000) with 50% transparency (80 which is half of FF).  
if barstate.islastconfirmedhistory  
    label.new(bar\_index, high, text \= "Label", color \= labelColor, textcolor \= textColor)

// When declaring variables with color literals, built-in constants(color.green) or functions (color.new(), color.rgb()), the "color" keyword for the type can be omitted.  
c \= color.rgb(0,255,0,0)  
plot(close, color \= c)  
Remarks  
Color literals have the following format: \#RRGGBB or \#RRGGBBAA. The letter pairs represent 00 to FF hexadecimal values (0 to 255 in decimal) where RR, GG and BB pairs are the values for the color's red, green and blue components. AA is an optional value for the color's transparency (or alpha component) where 00 is invisible and FF opaque. When no AA pair is supplied, FF is used. The hexadecimal letters can be upper or lower case.  
Explicitly mentioning the type in a variable declaration is optional, except when it is initialized with [na](https://www.tradingview.com/pine-script-reference/v6/#var_na). Learn more about Pine Script® types in the User Manual page on the [Type System](https://www.tradingview.com/pine-script-docs/language/type-system/).  
See also  
[var](https://www.tradingview.com/pine-script-reference/v6/#kw_var)[varip](https://www.tradingview.com/pine-script-reference/v6/#kw_varip)[int](https://www.tradingview.com/pine-script-reference/v6/#type_int)[float](https://www.tradingview.com/pine-script-reference/v6/#type_float)[string](https://www.tradingview.com/pine-script-reference/v6/#type_string)[color.rgb](https://www.tradingview.com/pine-script-reference/v6/#fun_color.rgb)[color.new](https://www.tradingview.com/pine-script-reference/v6/#fun_color.new)

### **const**

The `const` keyword explicitly assigns the "const" type qualifier to variables and the parameters of non-exported functions. Variables and parameters with the "const" qualifier reference values established at compile time that never change in the script's execution.  
In variable declarations, the compiler can usually infer the qualified type automatically based on the values assigned to a variable, and it can automatically change a variable's qualifier to a stronger one when necessary. The type qualifier hierarchy is "const" \< "input" \< "simple" \< "series", where "const" is the weakest.  
Explicitly declaring a variable with the `const` keyword restricts the type qualifier to "const", meaning the variable cannot accept a value with a stronger qualifier (e.g., "input"), nor can the value assigned to the variable change at any point in the script's execution.  
When using this keyword to specify the type qualifier, one must also use a type keyword to declare the allowed type.  
Syntax  
\[method \]\<functionName\>(\[const \<paramType\> \]\<paramName\>\[ \= \<defaultValue\>\])

\[var/varip \]const \<variableType\> \<variableName\> \= \<variableValue\>  
Example  
//@version=6  
indicator("custom plot title")

//@function Concatenates two "const string" values.  
concatStrings(const string x, const string y) \=\>  
    const string result \= x \+ y

//@variable The title of the plot.  
const string myTitle \= concatStrings("My ", "Plot")

plot(close, myTitle)  
Example  
//@version=6  
indicator("can't assign input to const")

//@variable A variable declared as "const float" that attempts to assign the result of \`input.float()\` as its value.  
//          This declaration causes an error. The "input float" qualified type is stronger than "const float".  
const float myVar \= input.float(2.0)

plot(myVar)  
Remarks  
To learn more, see our User Manual's section on [type qualifiers](https://www.tradingview.com/pine-script-docs/language/type-system/#qualifiers).  
See also  
[simple](https://www.tradingview.com/pine-script-reference/v6/#type_simple)[series](https://www.tradingview.com/pine-script-reference/v6/#type_series)

### **float**

Keyword used to explicitly declare the "float" (floating point) type of a variable or a parameter.  
Example  
//@version=6  
indicator("float")  
float f \= 3.14    // Same as \`f \= 3.14\`  
f := na  
plot(f)  
Remarks  
Explicitly mentioning the type in a variable declaration is optional, except when it is initialized with [na](https://www.tradingview.com/pine-script-reference/v6/#var_na). Learn more about Pine Script® types in the User Manual page on the [Type System](https://www.tradingview.com/pine-script-docs/language/type-system/).  
See also  
[var](https://www.tradingview.com/pine-script-reference/v6/#kw_var)[varip](https://www.tradingview.com/pine-script-reference/v6/#kw_varip)[int](https://www.tradingview.com/pine-script-reference/v6/#type_int)[bool](https://www.tradingview.com/pine-script-reference/v6/#type_bool)[color](https://www.tradingview.com/pine-script-reference/v6/#type_color)[string](https://www.tradingview.com/pine-script-reference/v6/#type_string)

### **int**

Keyword used to explicitly declare the "int" (integer) type of a variable or a parameter.  
Example  
//@version=6  
indicator("int")  
int i \= 14    // Same as \`i \= 14\`  
i := na  
plot(i)  
Remarks  
Explicitly mentioning the type in a variable declaration is optional, except when it is initialized with [na](https://www.tradingview.com/pine-script-reference/v6/#var_na). Learn more about Pine Script® types in the User Manual page on the [Type System](https://www.tradingview.com/pine-script-docs/language/type-system/).  
See also  
[var](https://www.tradingview.com/pine-script-reference/v6/#kw_var)[varip](https://www.tradingview.com/pine-script-reference/v6/#kw_varip)[float](https://www.tradingview.com/pine-script-reference/v6/#type_float)[bool](https://www.tradingview.com/pine-script-reference/v6/#type_bool)[color](https://www.tradingview.com/pine-script-reference/v6/#type_color)[string](https://www.tradingview.com/pine-script-reference/v6/#type_string)

### **label**

Keyword used to explicitly declare the "label" type of a variable or a parameter. Label objects (or IDs) can be created with the [label.new](https://www.tradingview.com/pine-script-reference/v6/#fun_label.new) function.  
Example  
//@version=6  
indicator("label")  
// Empty \`label1\` label ID.  
var label label1 \= na  
// \`label\` type is unnecessary because \`label.new()\` returns "label" type.  
var label2 \= label.new(na, na, na)  
if barstate.islastconfirmedhistory  
    label3 \= label.new(bar\_index, high, text \= "label3 text")  
Remarks  
Label objects are always of "series" form.  
See also  
[var](https://www.tradingview.com/pine-script-reference/v6/#kw_var)[line](https://www.tradingview.com/pine-script-reference/v6/#type_line)[box](https://www.tradingview.com/pine-script-reference/v6/#type_box)[label.new](https://www.tradingview.com/pine-script-reference/v6/#fun_label.new)

### **line**

Keyword used to explicitly declare the "line" type of a variable or a parameter. Line objects (or IDs) can be created with the [line.new](https://www.tradingview.com/pine-script-reference/v6/#fun_line.new) function.  
Example  
//@version=6  
indicator("line")  
// Empty \`line1\` line ID.  
var line line1 \= na  
// \`line\` type is unnecessary because \`line.new()\` returns "line" type.  
var line2 \= line.new(na, na, na, na)  
line3 \= line.new(bar\_index \- 1, high, bar\_index, high, extend \= extend.right)  
Remarks  
Line objects are always of "series" form.  
See also  
[var](https://www.tradingview.com/pine-script-reference/v6/#kw_var)[label](https://www.tradingview.com/pine-script-reference/v6/#type_label)[box](https://www.tradingview.com/pine-script-reference/v6/#type_box)[line.new](https://www.tradingview.com/pine-script-reference/v6/#fun_line.new)

### **linefill**

Keyword used to explicitly declare the "linefill" type of a variable or a parameter. Linefill objects (or IDs) can be created with the [linefill.new](https://www.tradingview.com/pine-script-reference/v6/#fun_linefill.new) function.  
Example  
//@version=6  
indicator("linefill", overlay=true)  
// Empty \`linefill1\` line ID.  
var linefill linefill1 \= na  
// \`linefill\` type is unnecessary because \`linefill.new()\` returns "linefill" type.  
var linefill2 \= linefill.new(na, na, na)

if barstate.islastconfirmedhistory  
    line1 \= line.new(bar\_index \- 10, high+1, bar\_index, high+1, extend \= extend.right)  
    line2 \= line.new(bar\_index \- 10, low+1, bar\_index, low+1, extend \= extend.right)  
    linefill3 \= linefill.new(line1, line2, color \= color.new(color.green, 80))  
Remarks  
Linefill objects are always of "series" form.  
See also  
[var](https://www.tradingview.com/pine-script-reference/v6/#kw_var)[line](https://www.tradingview.com/pine-script-reference/v6/#type_line)[label](https://www.tradingview.com/pine-script-reference/v6/#type_label)[table](https://www.tradingview.com/pine-script-reference/v6/#type_table)[box](https://www.tradingview.com/pine-script-reference/v6/#type_box)[linefill.new](https://www.tradingview.com/pine-script-reference/v6/#fun_linefill.new)

### **map**

Keyword used to explicitly declare the "map" type of a variable or a parameter. Map objects (or IDs) can be created with the [map.new\<type,type\>](https://www.tradingview.com/pine-script-reference/v6/#fun_map.new\<type,type\>) function.  
Example  
//@version=6  
indicator("map", overlay=true)  
map\<int, float\> a \= na  
a := map.new\<int, float\>()  
a.put(bar\_index, close)  
label.new(bar\_index, a.get(bar\_index), "Current close")  
Remarks  
Map objects are always of [series](https://www.tradingview.com/pine-script-docs/language/type-system/#series) form.  
See also  
[map.new\<type,type\>](https://www.tradingview.com/pine-script-reference/v6/#fun_map.new\<type,type\>)

### **matrix**

Keyword used to explicitly declare the "matrix" type of a variable or a parameter. Matrix objects (or IDs) can be created with the [matrix.new\<type\>](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.new\<type\>) function.  
Example  
//@version=6  
indicator("matrix example")

// Create \`m1\` matrix of \`int\` type.  
matrix\<int\> m1 \= matrix.new\<int\>(2, 3, 0\)

// \`matrix\<int\>\` is unnecessary because the \`matrix.new\<int\>()\` function returns an \`int\` type matrix object.  
m2 \= matrix.new\<int\>(2, 3, 0\)

// Display matrix using a label.  
if barstate.islastconfirmedhistory  
    label.new(bar\_index, high, str.tostring(m2))  
Remarks  
Matrix objects are always of "series" form.  
See also  
[var](https://www.tradingview.com/pine-script-reference/v6/#kw_var)[matrix.new\<type\>](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.new\<type\>)[array](https://www.tradingview.com/pine-script-reference/v6/#type_array)

### **polyline**

Keyword to explicitly declare the type of a variable or parameter as `polyline`. Scripts can produce `polyline` instances using the [polyline.new](https://www.tradingview.com/pine-script-reference/v6/#fun_polyline.new) function.  
See also  
[chart.point](https://www.tradingview.com/pine-script-reference/v6/#type_chart.point)

### **series**

The `series` keyword explicitly assigns the "series" type qualifier to variables and function parameters. Variables and parameters that use the "series" qualifier can reference values that change throughout a script's execution.  
Explicit use of the `series` keyword when declaring the parameters of a library's exported functions is typically unnecessary, as the compiler can usually automatically detect whether a parameter is compatible with "series" or "simple" qualified values. By default, all exported function parameters are qualified as "series" wherever possible.  
In variable declarations, the compiler can usually infer the qualified type automatically based on the values assigned to a variable, and it can automatically change a variable's qualifier to a stronger one when necessary. The type qualifier hierarchy is "const" \< "input" \< "simple" \< "series", where "series" is the strongest.  
Explicitly declaring a variable with the `series` keyword restricts the type qualifier to "series", meaning the script cannot pass its value to any variable or function parameter that requires a value with a weaker qualifier ("const", "input", or "simple").  
When using this keyword to specify the type qualifier, one must also use a type keyword to declare the allowed type.  
Syntax  
export \[method \]\<functionName\>(\[\[series \]\<paramType\>\] \<paramName\>\[ \= \<defaultValue\>\])

\[method \]\<functionName\>(\[series \<paramType\> \]\<paramName\>\[ \= \<defaultValue\>\])

\[var/varip \]series \<variableType\> \<variableName\> \= \<variableValue\>  
Example  
//@version=6  
//@description A library with custom functions.  
library("CustomFunctions", overlay \= true)

//@function Finds the highest \`source\` value over \`length\` bars, filtered by the \`cond\` condition.  
export conditionalHighest(series float source, series bool cond, series int length) \=\>  
    //@variable The highest \`source\` value from when the \`cond\` was \`true\` over \`length\` bars.  
    series float result \= na  
    // Loop to find the highest value.  
    for i \= 0 to length \- 1  
        if cond\[i\]  
            value   \= source\[i\]  
            result := math.max(nz(result, value), value)  
    // Return the \`result\`.  
    result

//@variable Is \`true\` once every five bars.  
series bool condition \= bar\_index % 5 \== 0

//@variable The highest \`close\` value from every fifth bar over the last 100 bars.  
series float hiValue \= conditionalHighest(close, condition, 100\)

plot(hiValue)  
bgcolor(condition ? color.new(color.teal, 80\) : na)  
Example  
//@version=6  
indicator("series variable not allowed")

//@variable A variable declared as "series int" with a value of 5\.  
series int myVar \= 5

// This call causes an error.  
// The \`histbase\` accepts "input int/float". It can't accept the stronger "series int" qualified type.  
plot(close, style \= plot.style\_histogram, histbase \= myVar)  
Remarks  
To learn more, see our User Manual's section on [type qualifiers](https://www.tradingview.com/pine-script-docs/language/type-system/#qualifiers).  
See also  
[simple](https://www.tradingview.com/pine-script-reference/v6/#type_simple)[const](https://www.tradingview.com/pine-script-reference/v6/#type_const)

### **simple**

The `simple` keyword explicitly assigns the "simple" type qualifier to variables and function parameters. Variables and parameters that use the "simple" qualifier can reference values established at the beginning of a script's execution that do not change later.  
To restrict the parameters in a library's exported functions to only allow values with a "simple" or weaker type qualifier, using the `simple` keyword when declaring parameters is often necessary, as libraries automatically qualify all parameters as "series" wherever possible by default. Explicitly restricting functions to accept "simple" arguments also allows them to return "simple" values in some cases, depending on the operations they execute, making them usable with the parameters of built-in functions that do not allow "series" arguments.  
In variable declarations, the compiler can usually infer the qualified type automatically based on the values assigned to a variable, and it can automatically change a variable's qualifier to a stronger one when necessary. The type qualifier hierarchy is "const" \< "input" \< "simple" \< "series", where "simple" is stronger than "input" and "const".  
Explicitly declaring a variable with the `simple` keyword restricts the type qualifier to "simple", meaning the script cannot pass its value to any variable or function parameter that requires a value with a weaker qualifier ("const" or "input"). Additionally, one cannot assign a "series" value to a variable explicitly declared with the `simple` keyword.  
When using this keyword to specify the type qualifier, one must also use a type keyword to declare the allowed type.  
Syntax  
export \[method \]\<functionName\>(\[\[simple \]\<paramType\>\] \<paramName\>\[ \= \<defaultValue\>\])

\[method \]\<functionName\>(\[simple \<paramType\> \]\<paramName\>\[ \= \<defaultValue\>\])

\[var/varip \]simple \<variableType\> \<variableName\> \= \<variableValue\>\</variableValue\>  
Example  
//@version=6  
//@description A library with custom functions.  
library("CustomFunctions", overlay \= true)

//@function         Calculates the length values for a ribbon of four EMAs by multiplying the \`baseLength\`.  
//@param baseLength The initial EMA length. Requires "simple int" because you can't use "series int" in \`ta.ema()\`.  
//@returns          A tuple of length values.  
export ribbonLengths(simple int baseLength) \=\>  
    simple int length1 \= baseLength  
    simple int length2 \= baseLength \* 2  
    simple int length3 \= baseLength \* 3  
    simple int length4 \= baseLength \* 4  
    \[length1, length2, length3, length4\]

// Get a tuple of "simple int" length values.  
\[len1, len2, len3, len4\] \= ribbonLengths(14)

// Plot four EMAs using the values from the tuple.  
plot(ta.ema(close, len1), "EMA 1", color \= color.red)  
plot(ta.ema(close, len2), "EMA 1", color \= color.orange)  
plot(ta.ema(close, len3), "EMA 1", color \= color.green)  
plot(ta.ema(close, len4), "EMA 1", color \= color.blue)  
Example  
//@version=6  
indicator("can't change simple to series")

//@variable A variable declared as "simple float" with a value of 5.0.  
simple float myVar \= 5.0

// This reassignment causes an error.  
// The \`close\` variable returns a "series float" value. Since \`myVar\` is restricted to "simple" values, it cannot  
// change its qualifier to "series".  
myVar := close

plot(myVar)  
Remarks  
To learn more, see our User Manual's section on [type qualifiers](https://www.tradingview.com/pine-script-docs/language/type-system/#qualifiers).  
See also  
[series](https://www.tradingview.com/pine-script-reference/v6/#type_series)[const](https://www.tradingview.com/pine-script-reference/v6/#type_const)

### **string**

Keyword used to explicitly declare the "string" type of a variable or a parameter.  
Example  
//@version=6  
indicator("string")  
string s \= "Hello World\!"    // Same as \`s \= "Hello world\!"\`  
// string s \= na // same as ""   
plot(na, title=s)  
Remarks  
Explicitly mentioning the type in a variable declaration is optional, except when it is initialized with [na](https://www.tradingview.com/pine-script-reference/v6/#var_na). Learn more about Pine Script® types in the User Manual page on the [Type System](https://www.tradingview.com/pine-script-docs/language/type-system/).  
See also  
[var](https://www.tradingview.com/pine-script-reference/v6/#kw_var)[varip](https://www.tradingview.com/pine-script-reference/v6/#kw_varip)[int](https://www.tradingview.com/pine-script-reference/v6/#type_int)[float](https://www.tradingview.com/pine-script-reference/v6/#type_float)[bool](https://www.tradingview.com/pine-script-reference/v6/#type_bool)[str.tostring](https://www.tradingview.com/pine-script-reference/v6/#fun_str.tostring)[str.format](https://www.tradingview.com/pine-script-reference/v6/#fun_str.format)

### **table**

Keyword used to explicitly declare the "table" type of a variable or a parameter. Table objects (or IDs) can be created with the [table.new](https://www.tradingview.com/pine-script-reference/v6/#fun_table.new) function.  
Example  
//@version=6  
indicator("table")  
// Empty \`table1\` table ID.  
var table table1 \= na  
// \`table\` type is unnecessary because \`table.new()\` returns "table" type.  
var table2 \= table.new(position.top\_left, na, na)

if barstate.islastconfirmedhistory  
    var table3 \= table.new(position \= position.top\_right, columns \= 1, rows \= 1, bgcolor \= color.yellow, border\_width \= 1\)  
    table.cell(table\_id \= table3, column \= 0, row \= 0, text \= "table3 text")  
Remarks  
Table objects are always of "series" form.  
See also  
[var](https://www.tradingview.com/pine-script-reference/v6/#kw_var)[line](https://www.tradingview.com/pine-script-reference/v6/#type_line)[label](https://www.tradingview.com/pine-script-reference/v6/#type_label)[box](https://www.tradingview.com/pine-script-reference/v6/#type_box)[table.new](https://www.tradingview.com/pine-script-reference/v6/#fun_table.new)  
