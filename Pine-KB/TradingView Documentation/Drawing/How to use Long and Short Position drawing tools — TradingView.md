<iframe src="https://www.youtube.com/embed/OGF0K1UIUcs??si=nB6FbYxiSJcX3yeE&amp;wmode=opaque" frameborder="0" allowfullscreen="" data-identifyelement="465"></iframe>  

This feature lets you estimate how an order will go if you go long or short, shows the Profit & Loss (PnL) and estimates risk and closing account balance when price reaches your profit target or stop loss levels.

You can practice placing orders and seeing results without actually having to place the orders — get confident and knowledgeable before risking real money in the markets.

#### Calculate your Position Size and Account Balance

1\. Create a Long Position or Short Position drawing.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43523916375/original/Xk68Q9sgqm5Ld49jV0tc6uSum-Y1fxlZDw.png?1731920695)

2\. In properties dialog of the instrument enter your initial account size and risk amount (either in absolute numbers or as a % of your account size) in default or selected currency. You can also enter the Lot Size. Click OK to accept.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43531382260/original/ysVfCjR7BW_RZ6jG8ds4JIxZfpgk4tAJRA.png?1735049498)

3\. Drawing tool tags will show you position size (1) and account balance when positions are closed after reaching either the Take Profit (2) or the Stop Loss (3) level.

#### 

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43523916420/original/uqx1vJo9ctGI-84vD0efyQqtbnos8H8p6Q.png?1731920714)

#### How are the Position Size and Account Balance calculated?

##### Long Position:

<table data-identifyelement="540"><tbody data-identifyelement="541"><tr data-identifyelement="542"><td data-identifyelement="543"><span>Position Size</span></td><td data-identifyelement="547"><span>Qty = (RiskSize / ((EntryPrice – StopPrice) * Point value)) / Lot Size<br data-identifyelement="551"></span></td></tr><tr data-identifyelement="552"><td data-identifyelement="553"><span>Account Balance when position is closed after reaching the Take Profit level<br data-identifyelement="557"></span></td><td data-identifyelement="558"><span>Amount = AccountSize + (ProfitLevel – EntryPrice) * Qty * Point value * Lot Size<br data-identifyelement="562"></span></td></tr><tr data-identifyelement="563"><td data-identifyelement="564"><span>Account Balance when position is closed after reaching the Stop Loss level<br data-identifyelement="568"></span></td><td data-identifyelement="569"><span>Amount = AccountSize — (EntryPrice – StopLevel) * Qty * &nbsp;Point value * Lot Size<br data-identifyelement="573"></span></td></tr></tbody></table>

##### Short Position:

<table data-identifyelement="575"><tbody data-identifyelement="576"><tr data-identifyelement="577"><td data-identifyelement="578"><span>Position Size</span></td><td data-identifyelement="583"><span>Qty = (RiskSize / ((StopPrice – EntryPrice) * Point Value))&nbsp;/ Lot Size</span></td></tr><tr data-identifyelement="591"><td data-identifyelement="592"><span>Account Balance when position is closed after reaching the Take Profit level<br data-identifyelement="596"></span></td><td data-identifyelement="597"><span>Amount = AccountSize + (EntryPrice – ProfitLevel) * Qty * &nbsp;Point value * Lot Size</span></td></tr><tr data-identifyelement="605"><td data-identifyelement="606"><span>Account Balance when position is closed after reaching the Stop Loss level<br data-identifyelement="610"></span></td><td data-identifyelement="611"><span>Amount = AccountSize — (StopLevel – EntryPrice) * Qty * Point value * Lot Size<br data-identifyelement="615"></span></td></tr></tbody></table>

-   AccountSize — initial account size specified in the settings
-   RiskSize =
    -   Risk, if risk is selected in absolute numbers,
    -   Risk / 100 \* AccountSize, if risk is selected as a percentage of account size.

#### Display performance in the Compact mode

Try using the Compact stats mode if you want the position performance tags to consume less space on the chart. You can enable it by choosing the Compact stats mode checkbox in Settings.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43523916461/original/a8MVlg7DcMxISwXPG8FgiD4e_hEDehgWKw.png?1731920726)