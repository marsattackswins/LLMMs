To display the value of a numeric variable, you can plot it using the [plot()](https://qa-backend-2.xstaging.tv/pine-script-reference/v5/#fun_plot) function:

```
plot(variable_name)
```

This allows you to inspect the variable's value on each chart bar and follow its progression if it changes.  
If you want to display the value of a string variable, use the [label.new()](https://qa-backend-2.xstaging.tv/pine-script-reference/v5/#fun_label{dot}new) function:

```
label.new(bar_index, high, text=syminfo.ticker)
```

You can also use [label.new()](https://qa-backend-2.xstaging.tv/pine-script-reference/v5/#fun_label{dot}new) to display the value of a numeric variable by first converting it to a string using the [str.tostring()](https://qa-backend-2.xstaging.tv/pine-script-reference/v5/#fun_str{dot}tostring) function:

```
label.new(bar_index, high, text=str.tostring(high))
```

The [label.new()](https://qa-backend-2.xstaging.tv/pine-script-reference/v5/#fun_label{dot}new) function will only display the last ~50 values of the variable by default.

A more detailed tutorial on debugging in Pine can be found in [this article in Pine User Manual](https://www.tradingview.com/pine-script-docs/writing/debugging/).