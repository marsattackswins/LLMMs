<iframe src="https://www.youtube.com/embed/FKICHC0kF3o?&amp;wmode=opaque" frameborder="0" allowfullscreen="" data-identifyelement="466"></iframe>

Strategies are specific scripts, written in [Pine Script language](https://www.tradingview.com/support/solutions/43000561836-what-is-pine-script/), which are able to send, modify, execute, and cancel buy or sell orders and simulate real trading right on your chart.

Backtesting is the process of recreating the work of your strategies on historical data, essentially all of your past strategic work. Forward testing allows for the recreation of your strategy work in real-time, all while your charts refresh their data.

##### How can I get started?

Any user can create a strategy if they know the Pine Script language. The main differences between a strategy and a simple script are the use of the [strategy](https://www.tradingview.com/pine-script-reference/#fun_strategy) function instead of [study](https://www.tradingview.com/pine-script-reference/#fun_study) and special commands that start with the word ‘strategy’, such as [strategy.entry](https://www.tradingview.com/pine-script-reference/#fun_strategy%7Bdot%7Dentry) or [strategy.exit](https://www.tradingview.com/pine-script-reference/#fun_strategy%7Bdot%7Dexit). Pine Script documentation has a [special section](https://www.tradingview.com/pine-script-docs/concepts/strategies/) dedicated to writing and working with strategies.

You can use pre-made strategies from a list of built-in indicators or from our Community Scripts, which users are welcome to add to.

##### How can I analyze strategy results?

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43464141867/original/CZnwCxtO-L68ME67ycEWztxe5tJW6FP0-g.png?1706626098)

When you add a strategy to the chart, additional information will appear in the Strategy Tester tab and can show you a report of your strategies results.

There are three sections available: Overview, Performance Summary and List of Trades. You can learn more about the indicators available in each section via our [Help Center](https://www.tradingview.com/chart/?folder=43000587044).

Executed orders are displayed directly on your chart with arrows, varying in color, depending on the operation.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43464141963/original/hs7Kp6Ii0sE-oC_wC8HxcS1DbesHaU54xw.png?1706626117)

As data is updated on the chart, the report will also be updated. This is forward testing.

Each strategy has parameters, which affect the calculation and result. You can change the parameters in your settings, causing backtesting and forward testing results to change as well.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43464142116/original/b9w_7bhkpthUFZ-RbBrH28uHTAm3aA9j7Q.gif?1706626145)

Strategies can be published just like any script written in Pine. In this case, a report with all indicators will be included in the publication.

##### What do I do if I still have questions?

If you cannot find what you are interested in within our reference materials, you can ask questions in the [Tradingview chat](https://www.tradingview.com/chat/#BfmVowG1TZkKO235) where Pine Script is specifically discussed, or on the [StackOverflow website](https://stackoverflow.com/questions/tagged/pine-script), where we have a separate tag listed.