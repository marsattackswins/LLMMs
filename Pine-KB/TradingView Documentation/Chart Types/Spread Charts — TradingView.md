#### <iframe src="https://www.youtube.com/embed/MfiI_0Jk-PI?&amp;wmode=opaque" frameborder="0" allowfullscreen=""></iframe>  

#### Definition

The most basic definition of a spread chart is that it is a comparison between a financial instrument (such as a stock) and an additional variable (such as another financial instrument or a numerical value). Trading by using spreads has been gaining popularity because they provide a new perspective of financial instrument value and can also help to alleviate some risk. There are a few different ways of utilizing spread charts. Some of the more popular ways include price inversions, currency conversions, financial instrument comparisons and pairs trading.

#### Operators and setup

To create your own custom spread chart in TradingView, follow these steps:

1.  Enter the first variable (symbol, number etc.) in the symbol entry window in the upper left hand corner and follow it with a space.
2.  Enter one of four operators; (-) for subtraction, (+) for addition, (\*) for multiplication or (/) for division and follow it with a space.
3.  Enter the second variable (symbol, number etc.) in the symbol entry window in the upper left hand corner and press the enter key.

For Example: Entering _AAPL / XAUUSD_ will create a comparison of Apple vs. Gold by dividing Apple prices by Gold prices.

Spreads for intraday charts are calculated by taking the Open, High, Low, and Close of each 1-minute bar and then recompiling them into the selected interval. This approach is the only method that results in correct spread charts. We handle all necessary calculations on our servers and display the finished spread chart.

**Note:** a single spread can include no more than 10 unique symbols.

#### Repainting Spread charts 

Please note that spread charts can get repainted. The reason for this is that real-time bars are built on tick data, whereas historical bars are built based on minute data. The tick data of price movements within a bar is not included in historical bars. The sequence of price movements intra-bar plays a crucial role in building spread bars in real-time, therefore real-time and historical data in a spread chart may be different. Everytime you refresh a chart, the data can be calculated on different servers each time, and every server can either use historical data, real-time data, or the combination of both. As a result, the bars built on different servers can mismatch and you may see slightly different bars after refreshing the spread chart. This peculiarity also affects alerts set on spread charts because an alert server processes data received only in real-time, thus the bars built on the alert server and chart server may sometimes mismatch.

#### Common spread types

#### Chart Inversions

Inverting a chart is a good way to visually chart the correlation between two instruments. For example, with two instruments with very low correlation, inverting one of the instruments with this method will make them viewable moving in the same direction.

_For example, an inversion on the EURUSD: 1/EURUSD_

#### Currency Conversions

Multiplying or dividing an instrument by a currency pair will allow you to view the price of the instrument in a different currency.

_For Example, Best Buy shown in Euros: BBY/EURUSD_

Instrument Comparisons

A common way to utilize spreads is to divide one instrument by another. This will give you spread value that can be tracked like a single instrument.

_For Example, Apple vs. Gold: AAPL/XAUUSD_

Exchange Arbitrage

Spreads can also be used to view the difference in price between the same instrument traded on two different exchanges. You will need to subtract the symbol for one exchange from the symbol from another exchange.

_For Example: BATS:FB-NASDAQ:FB_

#### Bitcoin Arbitrage

With Bitcoin's rise in popularity, arbitrage between BTC (Bitcoin) trading in different currencies has also become a popular trading opportunity.

_For Example: BTCUSD-BTCEUR\*EURUSD_

#### Pairs Trading

Pairs trading involves trading two separate instruments simultaneously in order to execute a single trade. Pairs trading is a popular way to alleviate some of the risk of trading. The idea is that you find two highly correlated symbols (or two very lowly correlated symbols) and enter a position in both symbols. If the pair is highly [correlated](https://www.tradingview.com/ideas/correlation/ "Correlation"), they should move in the same direction. Typically, an opportunity presents itself when the pair ratio breaks through a threshold that is a certain number of standard deviations away from their average standard deviation. You would then go long in the symbol that is under-performing and short in the symbol that is over-performing. When the pair moves back towards its average deviation, you would then close out both positions. Many technical analysts use the Bollinger Bands indicator to spot pairs trading opportunities. As in the example below, Bollinger Bands are set to be 2.2 Standard Deviations away from the average.

It is important to note a number things in regards to pairs trading.

1.  A pairs trade is designed to be market neutral. This means that because of the positions that you take in two separate instruments, the direction of the market will not effect the position. The trade is designed to profit from the relationship between the two instruments, not the direction of the market itself.
2.  Correlation moves along a scale of -1 to 1 with 1 meaning the instruments are perfectly correlated. Keep in mind that pairs trades can also work with pairs that are extremely negatively correlated (close to -1). When setting up a pairs trade with negatively correlated instruments, you typically want to enter the positions when the two contracts are closer together than usual, with the anticipation that they will move apart in opposite directions. In this case, you would enter positions in the same direction for both, instead of going long in one and short in the other.
3.  Another important piece of the puzzle is position size. The whole idea is to be market neutral. Therefore, you would not simply enter the same number of shares or contracts for each instrument. You would want to create the same actual dollar value in both positions. If you strictly use an equal number of shares on both sides and the dollar value of the two instruments are wildly different, then the side with the higher dollar value will have way too much weight in the trade.  
    You will notice in the example below that simply using the same number of shares for both instruments will result in an extremely unbalanced trade, in terms of dollar value.  
    [
    
    ![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43040511348/original/dGr7-CWeePMZnsfc0OsIMFvtgjN-8rH2KA.png?1556114339)
    
    
    
    ](https://www.tradingview.com/wiki/File:Trade_Size_1.PNG)  
    The number of shares should be modified in order to get the dollar values as close as possible. It will rarely, if ever, be exact, but getting as close as possible is important.  
    [
    
    ![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43040511349/original/AqkcV9XL8bRF3FWM66jiUOfowV0pFeVJ8g.png?1556114339)
    
    
    
    ](https://www.tradingview.com/wiki/File:Trade_Size_2.PNG)
4.  The key to pairs trading is the correlation between the two instruments. One thing that many traders fail to realize is that the correlation between instruments is ever-changing. Even during the course of a trade, their correlation can change. This is why it is important to constantly monitor correlation when in a pairs trade. Be observant and diligent. The trader should be prepared to exit any trades, which have drastic changes in correlation.