#### Definition

The MovingAvg Cross strategy is based on a Moving Average with any specific length defined by you the user. The entries are based on whether the close of the bar is higher or lower than the moving average. The strategy goes long when close is greater than the moving average and switches to short when the close is less than the moving average. 

The length of the moving average, for example 20-day or 50-day moving average, can be changed in the strategy settings. By default the length is set to 9. The ConfirmBars setting defines the number of bars that the condition should be true before a new entry can appear. For example, with ConfirmBars=3, the close should be higher than the moving average for 3 consecutive bars before a new entry can be created.

#### Summary

The MovingAvg Cross strategy has elements of swing trading and reversal trading wrapped into it. The strategy looks for crosses in specific moving averages. The strategy goes long when close is greater than the moving average and switches to short when the close is less than the moving average.