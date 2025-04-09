To ensure the continued availability of computing resources to all TradingView users, indicators and strategies must complete their calculations within the following limits: 

-   20 seconds (for Basic plan)
-   40 seconds (for Essential, Plus and Premium plans)
-   60 seconds (for Expert plan)
-   100 seconds (for Ultimate plan)

See [this page](https://www.tradingview.com/pricing/) to learn more about each plan's features and limitations.

If a script can't complete its calculations during this allotted time, the "Calculation takes too long to execute." error will appear. Here's what you can do to prevent it:

-   Split the script into multiple scripts so that each one calculates faster.
-   Limit the number of bars the script runs on using [date/time filtering](https://www.pinecoders.com/faq_and_code/#how-do-i-implement-date-range-filtering-in-strategies).
-   Optimize the script's code. Pine code can be optimized in many different ways. [These suggestions](https://www.pinecoders.com/faq_and_code/#how-can-i-optimize-pine-code) will help you identify optimization opportunities.

I see 'The study has too many output series' error

I see 'Pine cannot determine the referencing length of a series. Try using max\_bars\_back' error