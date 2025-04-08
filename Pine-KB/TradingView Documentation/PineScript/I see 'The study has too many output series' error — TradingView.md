This error means that you have exceeded the maximum number of output series. These are the series that have values plotted on the chart. There are several functions you can call to plot series - their names begin with _plot_: [plot](https://www.tradingview.com/study-script-reference/#fun_plot), [plotcandle](https://www.tradingview.com/study-script-reference/#fun_plotcandle), [plotbar](https://www.tradingview.com/study-script-reference/#fun_plotbar), etc.

Please note:

-   plotbar and plotcandle functions actually plot 4 series (OHLC) at once;
-   serial (not constant) color in all plot functions is considered an additional output series;
-   in Pine v4, an alertcondition call generates an additional plot and all such calls are taken into account when we calculate the number of the output series per script.

To avoid this error, reduce the number of plot functions.  

I see "Maximum number of orders (9000) was reached." error

I see 'Calculation takes too long to execute' error