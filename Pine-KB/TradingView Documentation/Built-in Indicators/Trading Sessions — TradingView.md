The Trading Sessions indicator highlights custom trading sessions on the chart. Up to three sessions can be customized to start and end at any time point in any timezone. The default settings represent the commonly used Asian, European, and North American sessions, respectively.

Instruments that are traded in multiple markets in different time zones can experience periodic spikes in volume and volatility. Using the Trading Sessions indicator, you can visually track when different markets open and close.

The Style section in the indicator's settings allows you to change the color of every session, and turn any specific session on or off, while the Inputs section specifies when each session starts and ends.

#### Inputs

The inputs specify when each session starts and ends.

Each session has two inputs: for start and end times, and for time zones.  The inputs work the same way for each session.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43491203135/original/Lbs7H6rvTV_yFmZ1FT3jWLGfUHL_1l1Qxw.png?1718094356)

#### First/Second/Third session

Specifies the starting and ending time of each session. The input dropdown specifies the time in 15-minute intervals. If you want a time that ends in a different number of minutes, click into the minutes field and type the number.

If the second time is before the first, the session is considered an overnight session. For example, "10:00 – 09:00" highlights bars from 10AM on the first day to 9AM on the second day.

#### First/Second/Third session timezone

Specifies the timezone for the session start and end. 

There are two supported formats for a session's timezone:

-   GMT notation with numerical offset from Greenwich Mean Time, e.g., 'GMT-5', 'GMT+0530'.
-   IANA timezone database name, e.g., 'America/New\_York', 'Asia/Tokyo'. Wikipedia provides [a list of timezones in this format](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

If the timezone field is left empty, the indicator uses the IANA timezone from the exchange of the symbol that is open on the chart.

#### Considerations for time zone changes

Using IANA time zone database names is a more robust way to specify a session’s time zone than using GMT notation because it adjusts for changes, such as the switch to Daylight Savings Time.

To demonstrate, let's open a BINANCE:BTCUSD chart, because its exchange timezone is always GMT regardless of the season. Using the Trading Sessions indicator, we add two different sessions based on the US trading session, 09:30-16:00. The first trading session uses "GMT-4" as its timezone and highlights the chart in blue.The second session uses "America/New\_York" and highlights the chart in yellow.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43491203142/original/OW5uGUGAkIprtWQhHgz0oEiB9akkGvuBDw.png?1718094358)

During Daylight Savings Time, both sessions overlap exactly. For the rest of the year, the two sessions are different by one hour. This is because the US switches to GMT-5 in winter, and while the "America/New\_York" timezone adjusts for this automatically, the "GMT-4" timezone does not.

As a result, the "America/New\_York" session always highlights 09:30-16:00 with the proper time offset, while "GMT-4" will be off by one hour in winter.