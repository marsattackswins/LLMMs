Please know that information about expected waves that have not yet formed in In-Progress mode is not a recommendation as to what you personally should do. Do not take this data as investment advice. It should be used only for education and scientific research. As with any trade, always look first at the result.

Elliott Waves are a system of repeating patterns discovered by Ralph Nelson Elliott. Elliott discovered 13 patterns in total, but the 5-3 pattern consisting of 8 waves is considered the basic one.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43282992445/original/rBSBOAO7z0NAm11u9j5P0JgRiIDbZ94odQ.png?1640270787)

  
According to Elliott's wave theory, waves are divided into "Motive” and "Corrective”. Motive waves are price movements that coincide with the direction of the main trend, Corrective waves are movements against the main trend. In the screenshot shown above, the motive waves are (1), (3), (5), (a), and (c), and corrective waves are (2), (4), and (b). Also, according to Elliott, any motive wave of the basic model can be represented as five smaller waves, and any corrective wave as a three. Thus, the basic model 5-3 can be represented as 2 waves of a higher wave level and as 34 waves of a lower one.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43282992516/original/jjF-X0MN1G9GF2kvbk3aFJ73tV2C-g03oA.png?1640270802)

The Chart Pattern Elliott Wave indicator is configured to recognize the most common wave patterns, which are built according to the following rules:

_Impulse (Motive wave):_

1.  Wave structure: 5-3-5-3-5
2.  Wave 2 does not retrace more than 100% of the length of wave 1
3.  Wave 3 moves beyond the end of wave 1
4.  Wave 3 cannot be the shortest among waves 1, 3, and 5
5.  Wave 4 does not go beyond the level of wave 1

_ZigZag (Corrective wave):_

1.  Wave structure: 5-3-5
2.  Wave b is shorter than a
3.  Wave c goes beyond the level of wave a

The indicator analyzes the last 600 bars in search of patterns, conditionally dividing them into two levels by nesting (main and sub-waves). The start and end points of the waves in the patterns found are tied to the most suitable pivot points. Then the indicator checks the rules for impulse and zigzag and draws patterns that capture the most amplitude price movements.

The following marking is used to indicate the level that the wave belongs to:

Main Waves: (1), (2), (3), (4), (5), (a), (b), (c)

Sub-waves: 1, 2, 3, 4, 5, a, b, c

This marking does not correspond to the historical levels of the Elliott wave theory; it is conditional. It displays the nesting level of the pattern.

When the pattern is in the _In Progress_ mode, the indicator builds as many waves as possible based on the pivots, and uses a local extremum (highest high or lowest low) to build the last wave. If that last wave does not complete the pattern, the indicator draws possible projections of the next wave using Fibonacci proportions. Depending on the length of wave 3, wave 5 will be projected either from wave 1 or from the height of the movement of the first three waves. The projections of wave C are constructed from the length of wave A. All other projections are calculated based on the wave preceding them. The minimum number of waves in the in-progress pattern is 3.

Alerts:

-   _New Pattern._ It is triggered when a new pattern appears on the chart, or when a previously drawn pattern is rebuilt and at the same time the position of two or more points changes. The rebuilding of the very first point of the pattern is not taken into account.
-   __New Potential Wave.__ It is triggered when a new forming wave is added to a previously found pattern, or when the last formed wave is rebuilt to a new point and becomes forming again.
-   __Wave Formed_._ It is triggered when any of the forming waves of the pattern are formed.

#### Inputs:

-   _Invert Pattern_ - This flag allows you to change the direction of the pattern, to search for impulse in a downtrend, and a zigzag in an uptrend.
-   _In Progress_ \- Enables the search for incomplete patterns that are in the process of being formed.
-   _Length type_ - How the wavelength is calculated when checking the rules of pattern construction:
-   _Absolute_ - the wavelength is calculated as the price difference between the start and end point of the wave.
-   _Percent_ - the wavelength is calculated as the percentage change in price between the start and end points of the wave.
-   _Show Projections_ \- Enables possible projections of future waves when in _In Progress_ mode.

#### Important note:

When new data is received, the indicator updates and clarifies previously found patterns. Changing any settings of the indicator leads to its complete recalculation. The result may differ from the expected one.