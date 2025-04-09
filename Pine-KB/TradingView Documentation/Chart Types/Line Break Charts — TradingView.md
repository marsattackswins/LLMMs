#### <iframe src="https://www.youtube.com/embed/NCC0CalSzUQ??si=ebWEtxXgEkShZZYj&amp;wmode=opaque" frameborder="0" allowfullscreen=""></iframe>  

#### Definition

Line Break is a Japanese chart style that disregards time intervals and only focuses on price movements, similar to the Kagi and Renko chart styles. Line Break charts form a series of up and down bars (referred to as lines). Up lines represent rising prices, and down lines represent falling prices. New confirmed lines only form on the chart when closing prices break the range covered by previous lines. Users can control the number of past lines used in the calculation via the "Number of Lines" input in the chart settings. The typical "Number of Lines" setting is 3, meaning the chart forms a new up line when the closing price is above the high prices of the last three lines, and it forms a new down line when the closing price is below the past three lines' low prices. If the current price is higher, it is an up line and if it is lower, it is a down line. If the current closing price is the same or the move in the opposite direction is not large enough to warrant a reversal, l then no new line is drawn.

#### Line types

There are only four types of lines

1.  _Up Lines_ — Form during an uptrend.
2.  _Down Lines_ — Form during a downtrend.
3.  _Projected Up Lines_ — During an intraday timeframe, a potential up line that would form based on current price (before actual closing price is set).
4.  _Projected Down Lines_ — During an intraday timeframe, a potential down line that would form based on current price (before actual closing price is set).

#### Line calculation method

Each new closing price has three possible outcomes

1.  _New Line, Same Color_ — When price extends in the same direction.
2.  _New Line, Different Color_ — When the price change is large enough to warrant a reversal.
3.  _No New Line_ — When price does not change or the reversal is not large enough to warrant a new line.

The user defines the "Number of Lines" value. The chart compares the current close to the high and low values from the "Number of Lines" previous lines. If the input's value is 3, the calculation compares the current close to the highs and lows of the latest three confirmed lines, forming a new up or down line only when the close is above the highs or below the lows. The appropriate line is then drawn (or not drawn) based on the above guidelines.

#### Uses of line break charts

Very much like Kagi Charts and Renko Charts, Line Break Charts are popular because of the way that they filter out noise and make price movements easy to digest and understand. Some of the typical uses of Line Break Charts are finding support and resistance, spotting breakouts, and discovering classic chart patterns.

_Support and Resistance_ — Oftentimes, Line Break Charts reveal areas of support and resistance.

_Breakouts_ — Breakouts occur when bars begin to generate in a defined direction after a period of trading within a support and resistance bound trading range.

_Classic Chart Patterns_ — with charts that filter out time and only focus on price, such as Line Break Charts, classical chart patterns can often be spotted.

#### Line break charts specific options in TradingView

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43081060000/original/OG68ohpdkTP6Zr9DYOjeUlWipgthBc0ITw.png?1572359290)

_Up Bars_ — Change the Color and Outline of Up Bars.

_Down Bars_ — Change the Color and Outline of Down Bars.

_Projected Up Bars_ — Change the Color and Outline of Projected Up Bars.

Projected Down Bars — Change the Color and Outline of Projected Down Bars.