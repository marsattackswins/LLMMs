**Note:** This feature has been deprecated due to the API change from NASDAQ Data Link. Requests for "QUANDL" symbols are no longer valid and requests for them return a runtime error. The information below is preserved for historical context, but the \`request.quandl()\` function can no longer access any NASDAQ Data Link data.

Nasdaq Data Link (formerly known as Quandl)  is a marketplace for financial, economic, and alternative data. In order to get parameters for the \`[request.quandl()](https://www.tradingview.com/pine-script-reference/v5/#fun_request{dot}quandl)\` function, let’s first break down the different parts of this built-in function.

_request.quandl__(ticker, gaps, index)_

_ticker_ \- a string, the name of the Nasdaq Data Link symbol in the form “QUANDL:{QUANDL\_CODE}”.

_gaps_ \- a parameter, similar to the _gaps_ parameter in the [request.security()](https://www.tradingview.com/pine-script-reference/v5/#fun_request{dot}security) function. If the parameter has the value barmerge.gaps\_on, then values are displayed only on bars corresponding to the date of data publication.

_index_ \- the number of the data series of the symbol.

The _ticker_ and _index_ parameter values can be found on the [Nasdaq Data Link](https://data.nasdaq.com/) website.

Let’s say, for example, that you want to get data on the Consumer Sentiment Index from the University of Michigan. In order to do this, you would need to search for it on the [Nasdaq Data Link website](https://data.nasdaq.com/) and go to the [symbol page](https://data.nasdaq.com/data/UMICH/SOC3-university-of-michigan-consumer-surveyindex-of-consumer-sentiment-within-age-subgroups).

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43318606989/original/g05_lZLoQP_dpESClrwQMOdyV6K5oWSrSA.png?1651150923)

In the upper - right hand corner of the page, you can find the _ticker_, _EOD/AAPL_ parameter.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43318606920/original/3xlFYGUG2KeF89ycCOoT_6rrOp2CRKN6fg.png?1651150915)

To access the _index_ parameter, you will need a [quandl](http://quandl.com/) account. After registering and logging in, you can find the _index_ parameter from the available list:

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43318607345/original/4MQ-_LJtZXBFKGzm8dTRt8x7drdC9x5_Eg.png?1651150965)

  
Note that the numbering starts from 0. In other words, if you need to get data for the Consumer Sentiment Index for the age group 55+, the _index_ parameter needs a value set at 2. Keep this in mind when you are looking to access specific parameter data.