#### Definition

The [Price Oscillator indicator (PPO)](https://www.tradingview.com/scripts/priceoscillator/) is a technical analysis tool, used for measuring momentum that is very similar to the MACD. The MACD employs two Moving Averages of varying lengths (which are lagging indicators) to identify trend direction and duration. Then, MACD takes the difference in values between those two Moving Averages (MACD Line) and an EMA of those Moving Averages (Signal Line) and plots that difference between the two lines as a histogram which oscillates above and below a center Zero Line.  
PPO is exactly the same, however it then takes the same values at the MACD and calculates them as a percentage. The purpose of this, is that it makes value comparisons much more simple and straightforward over longer durations of time.

#### Calculation

```
PPO Line: {(12-day EMA - 26-day EMA)/26-day EMA} x 100

Signal Line: 9-day EMA of PPO

PPO Histogram: PPO - Signal Line
```

#### The basics

There are three major components to the Price Oscillator indicator (PPO). In order to fully understand, the indicator, each of these components needs to be understood.

#### The Three Major Components

##### The PPO Line

-   PPO Line is a result of taking a longer term EMA and subtracting it from a shorter term EMA. The result is then divided by the longer term EMA and then multiplied by 100.
-   The most commonly used values are 26 days for the longer term EMA and 12 days for the shorter term EMA, but it is the trader's choice.

##### The Signal Line

-   The Signal Line is an EMA of the PPO Line described in Component 1.
-   The trader can choose what period length EMA to use for the Signal Line however 9 is the most common.

##### The PPO Histogram

-   As time advances, the difference between the PPO Line and Signal Line will continually differ. The PPO histogram takes that difference and plots it into an easily readable histogram. The difference between the two lines oscillates around a Zero Line.
-   When the PPO histogram is above the Zero Line, the PPO is considered positive and when it is below the Zero Line, the PPO is considered negative.

A general interpretation of PPO is that when PPO is positive and the histogram value is increasing, then upside momentum is increasing. When PPO is negative and the histogram value is decreasing, then downside momentum is increasing.

#### What to look for

The PPO indicator is typically good for identifying three types of basic signals; Signal Line Crossovers, Zero Line Crossovers, and Divergence.

##### Signal line crossovers

A Signal Line Crossover is the most common signal produced by the PPO. First one must consider that the Signal Line is essentially an indicator of an indicator. The Signal Line is calculating the Moving Average of the PPO Line. Therefore the Signal Line lags behind the PPO line. That being said, on the occasions where the PPO Line crosses above or below the Signal Line, that can signify a potentially strong move.  
The strength of the move is what determines the duration of Signal Line Crossover. Understanding and being able to analyze move strength, as well as being able to recognize false signals, is a skill that comes with experience.

The first type of Signal Line Crossover to examine is the Bullish Signal Line Crossover. Bullish Signal Line Crossovers occur when the PPO Line crosses above the Signal Line.

The second type of Signal Line Crossover to examine is the Bearish Signal Line Crossover. Bearish Signal Line Crossovers occur when the PPO Line crosses below the Signal Line.

#### Zero line crossovers

Zero Line Crossovers have a very similar premise to Signal Line Crossovers. Instead of crossing the Signal Line, Zero Line Crossovers occur when the PPO Line crossed the Zero Line and either becomes positive (above 0) or negative (below 0).

The first type of Zero Line Crossover to examine is the Bullish Zero Line Crossover. Bullish Zero Line Crossovers occur when the PPO Line crosses above the Zero Line and go from negative to positive.

The second type of Zero Line Crossover to examine is the Bearish Zero Line Crossover. Bearish Zero Line Crossovers occur when the PPO Line crosses below the Zero Line and go from positive to negative.

#### Divergence

Divergence is another signal created by the PPO. Simply put, divergence is when the PPO and actual price are not in agreement.

For example, Bullish Divergence occurs when price records a lower low, but the PPO records a higher low. The movement of price can provide evidence of the current trend, however changes in momentum as evidenced by the PPO can sometimes precede a significant reversal.

Bearish Divergence is, of course, the opposite. Bearish Divergence occurs when price records a higher high while the PPO records a lower high.

#### Summary

#### 

The Price Oscillator indicator (PPO) is a very valuable indicator. Just like the MACD, it takes two lagging indicators and adds the aspect of momentum which is much more predictive. It is important to not lose sight of the similarities between MACD and PPO. They are almost the exact same. The only difference is that PPO's calculation is returned as a percentage.