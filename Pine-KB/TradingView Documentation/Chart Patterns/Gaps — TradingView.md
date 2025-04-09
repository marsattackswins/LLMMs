#### <iframe src="https://www.youtube.com/embed/uAuisQGLRVA?&amp;wmode=opaque" frameborder="0" allowfullscreen=""></iframe>

#### Definition

A gap is an area on a chart where the price between two bars changes significantly without any trades happening between them. Such gaps often occur when a strong shift in sentiment happens during the hours when markets are usually closed. This indicator highlights these gaps on the chart and extends them further until they have been covered (i.e., when a newer bar has crossed that gap).

The gaps highlighted by the indicator have two main variations: if the low of the current bar is greater than the high of the previous one, that is an Up Gap and it will be colored green by default. If the high of the current bar is lower than the low of the previous one, such a gap (Down Gap) will be colored red by default. If no gaps that fit the specified settings were found on the current symbol, a corresponding message will be displayed.

By default, the indicator filters the gaps based on their width and only displays the gaps when they are at least 30% as wide as the average bar range (high - low) for the last 14 bars. The deviation % can be changed in the Inputs section.

Additionally, the indicator extends the gaps indefinitely, until they get covered by new price movement. This can also be changed in the settings by enabling the Max Gap Trail Length limit. When enabled, gaps will be closed if they extend past the specified number of bars (300 by default).

#### Summary

Gaps mark periods when there was a sharp change in prices during the period when the exchange was inactive. This information can be used by traders to profit from the current situation of sudden price changes.

#### Inputs

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43409272834/original/B-gb6M4ndrkvkz1VlXiHBo8EIzwULOXW5A.png?1683702062)

##### Close Gaps Partially

Changes the logic based on which the gaps are closed. By default, this setting is turned off, and a gap is fully closed as soon as a bar enters it, even if that bar only touches a small part of the gap. When the setting is on, whenever a bar enters the gap zone but does not fully cover it, the gap closes partially, and the part that has not been covered by the price movement is extended further (and can be covered by the future bars).

On the screenshot below, the top chart features Gaps with the Close Gaps Partially turned off. The big down gap that starts at the beginning of February is closed almost instantly because its bottom part is slightly covered by a following bar. In contrast, on the bottom chart, where the Close Gaps Partially setting is turned on, only the small part on the bottom of the gap is closed, and the big uncovered part is extended further right, and is then eventually closed by future price action.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43409276324/original/IlPJyry0Zp5bvynzS_iKsw-lIPkTo-FhoA.png?1683702933)

##### Max Number of Gaps

Limits the maximum number of gaps displayed.

##### Minimal Deviation (%)

Sets the minimum size of detected gaps as a percentage of the average range of highs and lows over the last 14 bars. I.e., if this setting is set to 30, a gap would need to be at least 30% as high as the range of an average candle to be highlighted by the indicator.

##### Limit Max Gap Trail Length (bars)

If true, sets the maximum length of gaps from their beginning (left edge) in bars. Gaps that exceed the specified length will be cut off.