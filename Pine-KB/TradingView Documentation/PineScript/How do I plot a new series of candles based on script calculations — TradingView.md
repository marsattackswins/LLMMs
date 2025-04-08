To plot a new series of bars or candles, where OHLC values are based on your calculations, use [plotcandle()](https://www.tradingview.com/pine-script-reference/v5/#fun_plotcandle) or [plotbar()](https://www.tradingview.com/pine-script-reference/v5/#fun_plotbar) functions. After adding them to the chart, a script with such functions will plot a series of bars or a series of candles with specified parameters. For example, this script will plot a series of red and green candles with OHLC values twice as much, when compared to values of the main series. 

//@version=5  
indicator("My Script")  
plotcandle(open \* 2, high \* 2, low \* 2, close \* 2, title \= 'Title', color \= open < close ? color.green : color.red, wickcolor \= color.black)