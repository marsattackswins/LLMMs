//@version=5  
indicator("Drawing max\_bars\_back")  
// max\_bars\_back(time, 5000)  
var int pastBar \= na  
if barstate.islastconfirmedhistory  
    pastBar := bar\_index \- 300  
if barstate.islast  
    label.new(pastBar, 1, text \= "Label text")  

When a Pine script is calculated, it creates a historical buffer of a certain size for each variable or function in the code. That buffer contains information about previous values of the variable/function and is used when the code refers to the past values using the _\[\]_ history-referencing operator. The size of the buffer specifies how far into the history this value can be requested. 

Pine automatically determines the required buffer size for all variables and functions by analyzing past references made while calculating the script on the first 244 bars. If no past references are detected, a default buffer size is assigned to the variable or function. For variables, the default buffer size is 300 bars, for functions it is one bar. 

In some cases, Pine is not able to assign a proper buffer size for that function and the default buffer size is used instead. This can happen: 

-   In branches of conditional statements (_if_, _iff_, or _?_) when past references to a variable or function inside the conditional statement are first executed when the 244th bar has already passed.
-   In functions that support dynamic length, when the length value passed to the function after the 244th bar is greater than any value that was passed to it before (when the buffer was being calculated).

Take a look at the code below. It will return the aforementioned error because:

-   The _var1_ variable value is not known at the time of compilation
-   The _test_ variable does not request any past data on the first 244 bars of the chart

Due to this, the _test_ variable gets assigned a default buffer of 300 bars. When the script requests the value of the 301st bar in the past, which is outside of the variable's buffer, an error occurs. 

//@version=4  
study("max\_bars\_back var", overlay\=true)  
var1 \= input(301)  
test \= 0.0  
//max\_bars\_back(test, 301)  
if bar\_index \> 244  
    test := test\[var1\]  
plot(test)  

The _max\_bars\_back_ parameter and the _max\_bars\_back()_ function exist to work around this. They allow you to specify the correct buffer size for variables and functions when the default buffer doesn’t suffice. Uncomment the _max\_bars\_back()_ function call in the code above. A buffer of 301 will be assigned to the test variable and as a result, the script will calculate properly.

Here is an example of a function call to which the default one-bar buffer size is attributed because it is not invoked in the first 244 bars. While no explicit reference to past values using the _\[\]_ operator is used, the function nonetheless requires the past 20 values to calculate. The script will thus return the _max\_bars\_back_ error:

//@version=4  
study("Requires max\_bars\_back")  
test \= 0.0  
if bar\_index \> 1000  
    test := vwma(close, 20)  
plot(test)  

 The _max\_bars\_back()_ function cannot be used to assign a specific buffer size to a function. When you need to do so, or when you want to set the default buffer size for all variables and functions in a script, add the _max\_bars\_back_ parameter to the script’s _study_ or _s__trategy_ declaration statement. Note that using the parameter will increase the script's resource usage, so this method should only be used when needed:

//@version=4  
study("Requires max\_bars\_back", max\_bars\_back\=20)  
test \= 0.0  
if bar\_index \> 1000  
    test := vwma(close, 20)  
plot(test)  

You may also resolve the issue by taking the problematic expression out of the conditional branch, in which case the _max\_bars\_back_ parameter is not required:

//@version=4  
study("Requires max\_bars\_back")  
test \= 0.0  
vwma20 \= vwma(close, 20)  
if bar\_index \> 1000  
    test := vwma20  
plot(test)  

The error may also arise when using functions allowing dynamic lengths, i.e., series values. The following script will throw the max\_bars\_back error because during the first 300 bars, _sma()_ is calculated with a length of 50, and thus only requested 50 bars of historical data, limiting its buffer to 50. After the 300th bar, however, the length changed to 100, which is out of bounds of its established buffer:

//@version=4  
study("Out of bounds")  
series\_length \= bar\_index \> 300 ? 100 : 50  
plot(sma(close, series\_length))  

To work around this issue, you can generate a larger buffer in the beginning of the indicator’s calculations by using an intentionally large length value. In the following code, we request 1000 bars of historical data on the first bar of our indicator’s calculations. This creates a permanent 1000-bar buffer for our _sma()_, and as a result we never go out of bounds:

//@version=4  
study("Not out of bounds")  
series\_length \= bar\_index \> 300 ? 100 : 50  
passed\_length \= bar\_index \== 0 ? 1000 : series\_length   
plot(sma(close, passed\_length))  

Another case where this error may appear is when the script uses drawings that are placed on the chart based on the _bar\_index_ variable. The built-in variable _bar\_index_ uses the _time_ series in its inner workings. Before a drawing is displayed on the chart, its coordinates are converted from _bar\_index_ to UNIX time. Accessing the value of the bar index X bars back requires the history buffer size of the _time_ series to be of size X or more. This value is automatically detected based on how the script is calculated on the historical data. If after getting to the real-time calculation the script refers to a _bar\_index_ beyond than _time_ series buffer, it cannot be converted to UNIX time, which will cause the error to appear. 

The script below demonstrates this behavior: initially, it will compile and calculate properly, but as soon as a new bar appears, it will return a runtime error. When the script is applied on the chart, it first saves the _bar\_index_ of a bar 300 bars before the last one to the _pastBar_ variable. The value kept in that variable is then used as an X-coordinate to draw a label on. This causes the script to create a 300-value buffer for the time series. As soon as a new bar appears, that same index now refers to a bar 301 bars before the last one. The _time_ series buffer is only 300, so the _bar\_index_ can no longer be converted, which causes the error to appear.

To work around this issue, you can use the _max\_bars\_back()_ function to create a buffer for the time series. Uncomment the function in the code below to see the fix in action:

//@version=4  
study("Drawing max\_bars\_back")  
//max\_bars\_back(time, 5000)  
var int pastBar \= na  
if barstate.islastconfirmedhistory  
    pastBar := bar\_index \- 300  
if barstate.islast  
    label.new(pastBar, 1, text \= "Label text")  

You can learn more about _max\_bars\_back_ and the related error [in our User Manual.](https://www.tradingview.com/pine-script-docs/v4/appendix/pine-compilation-errors/)