				

# **Pine Script® language reference manual**

			  
			

## **Variables**

### **ask**

The current ask price, which represents the lowest price an active seller will accept for the instrument at its current value. This information is available only on the "1T" timeframe. On other timeframes, the variable's value is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).  
Type  
series float  
See also  
[open](https://www.tradingview.com/pine-script-reference/v6/#var_open)[high](https://www.tradingview.com/pine-script-reference/v6/#var_high)[low](https://www.tradingview.com/pine-script-reference/v6/#var_low)[volume](https://www.tradingview.com/pine-script-reference/v6/#var_volume)[time](https://www.tradingview.com/pine-script-reference/v6/#fun_time)[hl2](https://www.tradingview.com/pine-script-reference/v6/#var_hl2)[hlc3](https://www.tradingview.com/pine-script-reference/v6/#var_hlc3)[hlcc4](https://www.tradingview.com/pine-script-reference/v6/#var_hlcc4)[ohlc4](https://www.tradingview.com/pine-script-reference/v6/#var_ohlc4)[bid](https://www.tradingview.com/pine-script-reference/v6/#var_bid)

### **bar\_index**

Current bar index. Numbering is zero-based, index of the first bar is 0\.  
Type  
series int  
Example  
//@version=6  
indicator("bar\_index")  
plot(bar\_index)  
plot(bar\_index \> 5000 ? close : 0\)  
Remarks  
Note that **bar\_index** has replaced **n** variable in version 4\.  
Note that bar indexing starts from 0 on the first historical bar.  
Please note that using this variable/function can cause [indicator repainting](https://www.tradingview.com/pine-script-docs/concepts/repainting/).  
See also  
[last\_bar\_index](https://www.tradingview.com/pine-script-reference/v6/#var_last_bar_index)[barstate.isfirst](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isfirst)[barstate.islast](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.islast)[barstate.isrealtime](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isrealtime)

### **barstate.isconfirmed**

Returns true if the script is calculating the last (closing) update of the current bar. The next script calculation will be on the new bar data.  
Type  
series bool  
Remarks  
Pine Script® code that uses this variable could calculate differently on history and real-time data.  
It is NOT recommended to use [barstate.isconfirmed](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isconfirmed) in [request.security](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security) expression. Its value requested from [request.security](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security) is unpredictable.  
Please note that using this variable/function can cause [indicator repainting](https://www.tradingview.com/pine-script-docs/concepts/repainting/).  
See also  
[barstate.isfirst](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isfirst)[barstate.islast](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.islast)[barstate.ishistory](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.ishistory)[barstate.isrealtime](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isrealtime)[barstate.isnew](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isnew)[barstate.islastconfirmedhistory](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.islastconfirmedhistory)

### **barstate.isfirst**

Returns true if current bar is first bar in barset, false otherwise.  
Type  
series bool  
Remarks  
Pine Script® code that uses this variable could calculate differently on history and real-time data.  
Please note that using this variable/function can cause [indicator repainting](https://www.tradingview.com/pine-script-docs/concepts/repainting/).  
See also  
[barstate.islast](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.islast)[barstate.ishistory](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.ishistory)[barstate.isrealtime](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isrealtime)[barstate.isnew](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isnew)[barstate.isconfirmed](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isconfirmed)[barstate.islastconfirmedhistory](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.islastconfirmedhistory)

### **barstate.ishistory**

Returns true if current bar is a historical bar, false otherwise.  
Type  
series bool  
Remarks  
Pine Script® code that uses this variable could calculate differently on history and real-time data.  
Please note that using this variable/function can cause [indicator repainting](https://www.tradingview.com/pine-script-docs/concepts/repainting/).  
See also  
[barstate.isfirst](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isfirst)[barstate.islast](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.islast)[barstate.isrealtime](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isrealtime)[barstate.isnew](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isnew)[barstate.isconfirmed](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isconfirmed)[barstate.islastconfirmedhistory](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.islastconfirmedhistory)

### **barstate.islast**

Returns true if current bar is the last bar in barset, false otherwise. This condition is true for all real-time bars in barset.  
Type  
series bool  
Remarks  
Pine Script® code that uses this variable could calculate differently on history and real-time data.  
Please note that using this variable/function can cause [indicator repainting](https://www.tradingview.com/pine-script-docs/concepts/repainting/).  
See also  
[barstate.isfirst](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isfirst)[barstate.ishistory](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.ishistory)[barstate.isrealtime](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isrealtime)[barstate.isnew](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isnew)[barstate.isconfirmed](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isconfirmed)[barstate.islastconfirmedhistory](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.islastconfirmedhistory)

### **barstate.islastconfirmedhistory**

Returns true if script is executing on the dataset's last bar when market is closed, or script is executing on the bar immediately preceding the real-time bar, if market is open. Returns false otherwise.  
Type  
series bool  
Remarks  
Pine Script® code that uses this variable could calculate differently on history and real-time data.  
Please note that using this variable/function can cause [indicator repainting](https://www.tradingview.com/pine-script-docs/concepts/repainting/).  
See also  
[barstate.isfirst](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isfirst)[barstate.islast](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.islast)[barstate.ishistory](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.ishistory)[barstate.isrealtime](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isrealtime)[barstate.isnew](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isnew)

### **barstate.isnew**

Returns true if script is currently calculating on new bar, false otherwise. This variable is true when calculating on historical bars or on first update of a newly generated real-time bar.  
Type  
series bool  
Remarks  
Pine Script® code that uses this variable could calculate differently on history and real-time data.  
Please note that using this variable/function can cause [indicator repainting](https://www.tradingview.com/pine-script-docs/concepts/repainting/).  
See also  
[barstate.isfirst](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isfirst)[barstate.islast](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.islast)[barstate.ishistory](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.ishistory)[barstate.isrealtime](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isrealtime)[barstate.isconfirmed](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isconfirmed)[barstate.islastconfirmedhistory](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.islastconfirmedhistory)

### **barstate.isrealtime**

Returns true if current bar is a real-time bar, false otherwise.  
Type  
series bool  
Remarks  
Pine Script® code that uses this variable could calculate differently on history and real-time data.  
Please note that using this variable/function can cause [indicator repainting](https://www.tradingview.com/pine-script-docs/concepts/repainting/).  
See also  
[barstate.isfirst](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isfirst)[barstate.islast](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.islast)[barstate.ishistory](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.ishistory)[barstate.isnew](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isnew)[barstate.isconfirmed](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isconfirmed)[barstate.islastconfirmedhistory](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.islastconfirmedhistory)

### **bid**

The current bid price, which represents the highest price an active buyer is willing to pay for the instrument at its current value. This information is available only on the "1T" timeframe. On other timeframes, the variable's value is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).  
Type  
series float  
See also  
[open](https://www.tradingview.com/pine-script-reference/v6/#var_open)[high](https://www.tradingview.com/pine-script-reference/v6/#var_high)[low](https://www.tradingview.com/pine-script-reference/v6/#var_low)[volume](https://www.tradingview.com/pine-script-reference/v6/#var_volume)[time](https://www.tradingview.com/pine-script-reference/v6/#fun_time)[hl2](https://www.tradingview.com/pine-script-reference/v6/#var_hl2)[hlc3](https://www.tradingview.com/pine-script-reference/v6/#var_hlc3)[hlcc4](https://www.tradingview.com/pine-script-reference/v6/#var_hlcc4)[ohlc4](https://www.tradingview.com/pine-script-reference/v6/#var_ohlc4)[ask](https://www.tradingview.com/pine-script-reference/v6/#var_ask)

### **box.all**

Returns an array filled with all the current boxes drawn by the script.  
Type  
array\<box\>  
Example  
//@version=6  
indicator("box.all")  
//delete all boxes  
box.new(time, open, time \+ 60 \* 60 \* 24, close, xloc=xloc.bar\_time, border\_style=line.style\_dashed)  
a\_allBoxes \= box.all  
if array.size(a\_allBoxes) \> 0  
    for i \= 0 to array.size(a\_allBoxes) \- 1  
        box.delete(array.get(a\_allBoxes, i))  
Remarks  
The array is read-only. Index zero of the array is the ID of the oldest object on the chart.  
See also  
[box.new](https://www.tradingview.com/pine-script-reference/v6/#fun_box.new)[line.all](https://www.tradingview.com/pine-script-reference/v6/#var_line.all)[label.all](https://www.tradingview.com/pine-script-reference/v6/#var_label.all)[table.all](https://www.tradingview.com/pine-script-reference/v6/#var_table.all)

### **chart.bg\_color**

Returns the color of the chart's background from the "Chart settings/Appearance/Background" field. When a gradient is selected, the middle point of the gradient is returned.  
Type  
input color  
See also  
[chart.fg\_color](https://www.tradingview.com/pine-script-reference/v6/#var_chart.fg_color)

### **chart.fg\_color**

Returns a color providing optimal contrast with [chart.bg\_color](https://www.tradingview.com/pine-script-reference/v6/#var_chart.bg_color).  
Type  
input color  
See also  
[chart.bg\_color](https://www.tradingview.com/pine-script-reference/v6/#var_chart.bg_color)

### **chart.is\_heikinashi**

Type  
simple bool  
Returns  
Returns [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) if the chart type is Heikin Ashi, [false](https://www.tradingview.com/pine-script-reference/v6/#const_false) otherwise.  
See also  
[chart.is\_renko](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_renko)[chart.is\_linebreak](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_linebreak)[chart.is\_kagi](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_kagi)[chart.is\_pnf](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_pnf)[chart.is\_range](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_range)

### **chart.is\_kagi**

Type  
simple bool  
Returns  
Returns [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) if the chart type is Kagi, [false](https://www.tradingview.com/pine-script-reference/v6/#const_false) otherwise.  
See also  
[chart.is\_renko](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_renko)[chart.is\_linebreak](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_linebreak)[chart.is\_heikinashi](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_heikinashi)[chart.is\_pnf](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_pnf)[chart.is\_range](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_range)

### **chart.is\_linebreak**

Type  
simple bool  
Returns  
Returns [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) if the chart type is Line break, [false](https://www.tradingview.com/pine-script-reference/v6/#const_false) otherwise.  
See also  
[chart.is\_renko](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_renko)[chart.is\_heikinashi](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_heikinashi)[chart.is\_kagi](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_kagi)[chart.is\_pnf](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_pnf)[chart.is\_range](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_range)

### **chart.is\_pnf**

Type  
simple bool  
Returns  
Returns [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) if the chart type is Point & figure, [false](https://www.tradingview.com/pine-script-reference/v6/#const_false) otherwise.  
See also  
[chart.is\_renko](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_renko)[chart.is\_linebreak](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_linebreak)[chart.is\_kagi](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_kagi)[chart.is\_heikinashi](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_heikinashi)[chart.is\_range](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_range)

### **chart.is\_range**

Type  
simple bool  
Returns  
Returns [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) if the chart type is Range, [false](https://www.tradingview.com/pine-script-reference/v6/#const_false) otherwise.  
See also  
[chart.is\_renko](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_renko)[chart.is\_linebreak](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_linebreak)[chart.is\_kagi](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_kagi)[chart.is\_pnf](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_pnf)[chart.is\_heikinashi](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_heikinashi)

### **chart.is\_renko**

Type  
simple bool  
Returns  
Returns [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) if the chart type is Renko, [false](https://www.tradingview.com/pine-script-reference/v6/#const_false) otherwise.  
See also  
[chart.is\_heikinashi](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_heikinashi)[chart.is\_linebreak](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_linebreak)[chart.is\_kagi](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_kagi)[chart.is\_pnf](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_pnf)[chart.is\_range](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_range)

### **chart.is\_standard**

Type  
simple bool  
Returns  
Returns [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) if the chart type is not one of the following: Renko, Kagi, Line break, Point & figure, Range, Heikin Ashi; [false](https://www.tradingview.com/pine-script-reference/v6/#const_false) otherwise.  
See also  
[chart.is\_renko](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_renko)[chart.is\_linebreak](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_linebreak)[chart.is\_kagi](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_kagi)[chart.is\_pnf](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_pnf)[chart.is\_range](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_range)[chart.is\_heikinashi](https://www.tradingview.com/pine-script-reference/v6/#var_chart.is_heikinashi)

### **chart.left\_visible\_bar\_time**

The [time](https://www.tradingview.com/pine-script-reference/v6/#var_time) of the leftmost bar currently visible on the chart.  
Type  
input int  
Remarks  
Scripts using this variable will automatically re-execute when its value updates to reflect changes in the chart, which can be caused by users scrolling the chart, or new real-time bars.  
Alerts created on a script that includes this variable will only use the value assigned to the variable at the moment of the alert's creation, regardless of whether the value changes afterward, which may lead to repainting.  
See also  
[chart.right\_visible\_bar\_time](https://www.tradingview.com/pine-script-reference/v6/#var_chart.right_visible_bar_time)

### **chart.right\_visible\_bar\_time**

The [time](https://www.tradingview.com/pine-script-reference/v6/#var_time) of the rightmost bar currently visible on the chart.  
Type  
input int  
Remarks  
Scripts using this variable will automatically re-execute when its value updates to reflect changes in the chart, which can be caused by users scrolling the chart, or new real-time bars.  
Alerts created on a script that includes this variable will only use the value assigned to the variable at the moment of the alert's creation, regardless of whether the value changes afterward, which may lead to repainting.  
See also  
[chart.left\_visible\_bar\_time](https://www.tradingview.com/pine-script-reference/v6/#var_chart.left_visible_bar_time)

### **close**

Close price of the current bar when it has closed, or last traded price of a yet incomplete, realtime bar.  
Type  
series float  
Remarks  
Previous values may be accessed with square brackets operator \[\], e.g. close\[1\], close\[2\].  
See also  
[open](https://www.tradingview.com/pine-script-reference/v6/#var_open)[high](https://www.tradingview.com/pine-script-reference/v6/#var_high)[low](https://www.tradingview.com/pine-script-reference/v6/#var_low)[volume](https://www.tradingview.com/pine-script-reference/v6/#var_volume)[time](https://www.tradingview.com/pine-script-reference/v6/#fun_time)[hl2](https://www.tradingview.com/pine-script-reference/v6/#var_hl2)[hlc3](https://www.tradingview.com/pine-script-reference/v6/#var_hlc3)[hlcc4](https://www.tradingview.com/pine-script-reference/v6/#var_hlcc4)[ohlc4](https://www.tradingview.com/pine-script-reference/v6/#var_ohlc4)[ask](https://www.tradingview.com/pine-script-reference/v6/#var_ask)[bid](https://www.tradingview.com/pine-script-reference/v6/#var_bid)

### **dayofmonth**

Date of current bar time in exchange timezone.  
Type  
series int  
Remarks  
Note that this variable returns the day based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00) this value can be lower by 1 than the day of the trading day.  
See also  
[dayofmonth](https://www.tradingview.com/pine-script-reference/v6/#fun_dayofmonth)[time](https://www.tradingview.com/pine-script-reference/v6/#var_time)[year](https://www.tradingview.com/pine-script-reference/v6/#var_year)[month](https://www.tradingview.com/pine-script-reference/v6/#var_month)[weekofyear](https://www.tradingview.com/pine-script-reference/v6/#var_weekofyear)[dayofweek](https://www.tradingview.com/pine-script-reference/v6/#var_dayofweek)[hour](https://www.tradingview.com/pine-script-reference/v6/#var_hour)[minute](https://www.tradingview.com/pine-script-reference/v6/#var_minute)[second](https://www.tradingview.com/pine-script-reference/v6/#var_second)

### **dayofweek**

Day of week for current bar time in exchange timezone.  
Type  
series int  
Remarks  
Note that this variable returns the day based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00) this value can be lower by 1 than the day of the trading day.  
You can use [dayofweek.sunday](https://www.tradingview.com/pine-script-reference/v6/#const_dayofweek.sunday), [dayofweek.monday](https://www.tradingview.com/pine-script-reference/v6/#const_dayofweek.monday), [dayofweek.tuesday](https://www.tradingview.com/pine-script-reference/v6/#const_dayofweek.tuesday), [dayofweek.wednesday](https://www.tradingview.com/pine-script-reference/v6/#const_dayofweek.wednesday), [dayofweek.thursday](https://www.tradingview.com/pine-script-reference/v6/#const_dayofweek.thursday), [dayofweek.friday](https://www.tradingview.com/pine-script-reference/v6/#const_dayofweek.friday) and [dayofweek.saturday](https://www.tradingview.com/pine-script-reference/v6/#const_dayofweek.saturday) variables for comparisons.  
See also  
[dayofweek](https://www.tradingview.com/pine-script-reference/v6/#fun_dayofweek)[time](https://www.tradingview.com/pine-script-reference/v6/#var_time)[year](https://www.tradingview.com/pine-script-reference/v6/#var_year)[month](https://www.tradingview.com/pine-script-reference/v6/#var_month)[weekofyear](https://www.tradingview.com/pine-script-reference/v6/#var_weekofyear)[dayofmonth](https://www.tradingview.com/pine-script-reference/v6/#var_dayofmonth)[hour](https://www.tradingview.com/pine-script-reference/v6/#var_hour)[minute](https://www.tradingview.com/pine-script-reference/v6/#var_minute)[second](https://www.tradingview.com/pine-script-reference/v6/#var_second)

### **dividends.future\_amount**

Returns the payment amount of the upcoming dividend in the currency of the current instrument, or [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) if this data isn't available.  
Type  
series float  
Remarks  
This value is only fetched once during the script's initial calculation. The variable will return the same value until the script is recalculated, even after the expected Payment date of the next dividend.

### **dividends.future\_ex\_date**

Returns the Ex-dividend date (Ex-date) of the current instrument's next dividend payment, or [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) if this data isn't available. Ex-dividend date signifies when investors are no longer entitled to a payout from the most recent dividend. Only those who purchased shares before this day are entitled to the dividend payment.  
Type  
series int  
Returns  
UNIX time, expressed in milliseconds.  
Remarks  
This value is only fetched once during the script's initial calculation. The variable will return the same value until the script is recalculated, even after the expected Payment date of the next dividend.

### **dividends.future\_pay\_date**

Returns the Payment date (Pay date) of the current instrument's next dividend payment, or [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) if this data isn't available. Payment date signifies the day when eligible investors will receive the dividend payment.  
Type  
series int  
Returns  
UNIX time, expressed in milliseconds.  
Remarks  
This value is only fetched once during the script's initial calculation. The variable will return the same value until the script is recalculated, even after the expected Payment date of the next dividend.

### **earnings.future\_eps**

Returns the estimated Earnings per Share of the next earnings report in the currency of the instrument, or [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) if this data isn't available.  
Type  
series float  
Remarks  
This value is only fetched once during the script's initial calculation. The variable will return the same value until the script is recalculated, even after the expected time of the next earnings report.  
See also  
[request.earnings](https://www.tradingview.com/pine-script-reference/v6/#fun_request.earnings)

### **earnings.future\_period\_end\_time**

Checks the data for the next earnings report and returns the UNIX timestamp of the day when the financial period covered by those earnings ends, or [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) if this data isn't available.  
Type  
series int  
Returns  
UNIX time, expressed in milliseconds.  
Remarks  
This value is only fetched once during the script's initial calculation. The variable will return the same value until the script is recalculated, even after the expected time of the next earnings report.  
See also  
[request.earnings](https://www.tradingview.com/pine-script-reference/v6/#fun_request.earnings)

### **earnings.future\_revenue**

Returns the estimated Revenue of the next earnings report in the currency of the instrument, or [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) if this data isn't available.  
Type  
series float  
Remarks  
This value is only fetched once during the script's initial calculation. The variable will return the same value until the script is recalculated, even after the expected time of the next earnings report.  
See also  
[request.earnings](https://www.tradingview.com/pine-script-reference/v6/#fun_request.earnings)

### **earnings.future\_time**

Returns a UNIX timestamp indicating the expected time of the next earnings report, or [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) if this data isn't available.  
Type  
series int  
Returns  
UNIX time, expressed in milliseconds.  
Remarks  
This value is only fetched once during the script's initial calculation. The variable will return the same value until the script is recalculated, even after the expected time of the next earnings report.  
See also  
[request.earnings](https://www.tradingview.com/pine-script-reference/v6/#fun_request.earnings)

### **high**

Current high price.  
Type  
series float  
Remarks  
Previous values may be accessed with square brackets operator \[\], e.g. high\[1\], high\[2\].  
See also  
[open](https://www.tradingview.com/pine-script-reference/v6/#var_open)[low](https://www.tradingview.com/pine-script-reference/v6/#var_low)[close](https://www.tradingview.com/pine-script-reference/v6/#var_close)[volume](https://www.tradingview.com/pine-script-reference/v6/#var_volume)[time](https://www.tradingview.com/pine-script-reference/v6/#fun_time)[hl2](https://www.tradingview.com/pine-script-reference/v6/#var_hl2)[hlc3](https://www.tradingview.com/pine-script-reference/v6/#var_hlc3)[hlcc4](https://www.tradingview.com/pine-script-reference/v6/#var_hlcc4)[ohlc4](https://www.tradingview.com/pine-script-reference/v6/#var_ohlc4)[ask](https://www.tradingview.com/pine-script-reference/v6/#var_ask)[bid](https://www.tradingview.com/pine-script-reference/v6/#var_bid)

### **hl2**

Is a shortcut for (high \+ low)/2  
Type  
series float  
See also  
[open](https://www.tradingview.com/pine-script-reference/v6/#var_open)[high](https://www.tradingview.com/pine-script-reference/v6/#var_high)[low](https://www.tradingview.com/pine-script-reference/v6/#var_low)[close](https://www.tradingview.com/pine-script-reference/v6/#var_close)[volume](https://www.tradingview.com/pine-script-reference/v6/#var_volume)[time](https://www.tradingview.com/pine-script-reference/v6/#fun_time)[hlc3](https://www.tradingview.com/pine-script-reference/v6/#var_hlc3)[hlcc4](https://www.tradingview.com/pine-script-reference/v6/#var_hlcc4)[ohlc4](https://www.tradingview.com/pine-script-reference/v6/#var_ohlc4)[ask](https://www.tradingview.com/pine-script-reference/v6/#var_ask)[bid](https://www.tradingview.com/pine-script-reference/v6/#var_bid)

### **hlc3**

Is a shortcut for (high \+ low \+ close)/3  
Type  
series float  
See also  
[open](https://www.tradingview.com/pine-script-reference/v6/#var_open)[high](https://www.tradingview.com/pine-script-reference/v6/#var_high)[low](https://www.tradingview.com/pine-script-reference/v6/#var_low)[close](https://www.tradingview.com/pine-script-reference/v6/#var_close)[volume](https://www.tradingview.com/pine-script-reference/v6/#var_volume)[time](https://www.tradingview.com/pine-script-reference/v6/#fun_time)[hl2](https://www.tradingview.com/pine-script-reference/v6/#var_hl2)[hlcc4](https://www.tradingview.com/pine-script-reference/v6/#var_hlcc4)[ohlc4](https://www.tradingview.com/pine-script-reference/v6/#var_ohlc4)[ask](https://www.tradingview.com/pine-script-reference/v6/#var_ask)[bid](https://www.tradingview.com/pine-script-reference/v6/#var_bid)

### **hlcc4**

Is a shortcut for (high \+ low \+ close \+ close)/4  
Type  
series float  
See also  
[open](https://www.tradingview.com/pine-script-reference/v6/#var_open)[high](https://www.tradingview.com/pine-script-reference/v6/#var_high)[low](https://www.tradingview.com/pine-script-reference/v6/#var_low)[close](https://www.tradingview.com/pine-script-reference/v6/#var_close)[volume](https://www.tradingview.com/pine-script-reference/v6/#var_volume)[time](https://www.tradingview.com/pine-script-reference/v6/#fun_time)[hl2](https://www.tradingview.com/pine-script-reference/v6/#var_hl2)[hlc3](https://www.tradingview.com/pine-script-reference/v6/#var_hlc3)[ohlc4](https://www.tradingview.com/pine-script-reference/v6/#var_ohlc4)[ask](https://www.tradingview.com/pine-script-reference/v6/#var_ask)[bid](https://www.tradingview.com/pine-script-reference/v6/#var_bid)

### **hour**

Current bar hour in exchange timezone.  
Type  
series int  
See also  
[hour](https://www.tradingview.com/pine-script-reference/v6/#fun_hour)[time](https://www.tradingview.com/pine-script-reference/v6/#var_time)[year](https://www.tradingview.com/pine-script-reference/v6/#var_year)[month](https://www.tradingview.com/pine-script-reference/v6/#var_month)[weekofyear](https://www.tradingview.com/pine-script-reference/v6/#var_weekofyear)[dayofmonth](https://www.tradingview.com/pine-script-reference/v6/#var_dayofmonth)[dayofweek](https://www.tradingview.com/pine-script-reference/v6/#var_dayofweek)[minute](https://www.tradingview.com/pine-script-reference/v6/#var_minute)[second](https://www.tradingview.com/pine-script-reference/v6/#var_second)

### **label.all**

Returns an array filled with all the current labels drawn by the script.  
Type  
array\<label\>  
Example  
//@version=6  
indicator("label.all")  
//delete all labels  
label.new(bar\_index, close)  
a\_allLabels \= label.all  
if array.size(a\_allLabels) \> 0  
    for i \= 0 to array.size(a\_allLabels) \- 1  
        label.delete(array.get(a\_allLabels, i))  
Remarks  
The array is read-only. Index zero of the array is the ID of the oldest object on the chart.  
See also  
[label.new](https://www.tradingview.com/pine-script-reference/v6/#fun_label.new)[line.all](https://www.tradingview.com/pine-script-reference/v6/#var_line.all)[box.all](https://www.tradingview.com/pine-script-reference/v6/#var_box.all)[table.all](https://www.tradingview.com/pine-script-reference/v6/#var_table.all)

### **last\_bar\_index**

Bar index of the last chart bar. Bar indices begin at zero on the first bar.  
Type  
series int  
Example  
//@version=6  
strategy("Mark Last X Bars For Backtesting", overlay \= true, calc\_on\_every\_tick \= true)  
lastBarsFilterInput \= input.int(100, "Bars Count:")  
// Here, we store the 'last\_bar\_index' value that is known from the beginning of the script's calculation.  
// The 'last\_bar\_index' will change when new real-time bars appear, so we declare 'lastbar' with the 'var' keyword.  
var lastbar \= last\_bar\_index  
// Check if the current bar\_index is 'lastBarsFilterInput' removed from the last bar on the chart, or the chart is traded in real-time.  
allowedToTrade \= (lastbar \- bar\_index \<= lastBarsFilterInput) or barstate.isrealtime  
bgcolor(allowedToTrade ? color.new(color.green, 80\) : na)  
Returns  
Last historical bar index for closed markets, or the real-time bar index for open markets.  
Remarks  
Please note that using this variable can cause [indicator repainting](https://www.tradingview.com/pine-script-docs/concepts/repainting/).  
See also  
[bar\_index](https://www.tradingview.com/pine-script-reference/v6/#var_bar_index)[last\_bar\_time](https://www.tradingview.com/pine-script-reference/v6/#var_last_bar_time)[barstate.ishistory](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.ishistory)[barstate.isrealtime](https://www.tradingview.com/pine-script-reference/v6/#var_barstate.isrealtime)

### **last\_bar\_time**

Time in UNIX format of the last chart bar. It is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970\.  
Type  
series int  
Remarks  
Please note that using this variable/function can cause [indicator repainting](https://www.tradingview.com/pine-script-docs/concepts/repainting/).  
Note that this variable returns the timestamp based on the time of the bar's open.  
See also  
[time](https://www.tradingview.com/pine-script-reference/v6/#var_time)[timenow](https://www.tradingview.com/pine-script-reference/v6/#var_timenow)[timestamp](https://www.tradingview.com/pine-script-reference/v6/#fun_timestamp)[last\_bar\_index](https://www.tradingview.com/pine-script-reference/v6/#var_last_bar_index)

### **line.all**

Returns an array filled with all the current lines drawn by the script.  
Type  
array\<line\>  
Example  
//@version=6  
indicator("line.all")  
//delete all lines  
line.new(bar\_index \- 10, close, bar\_index, close)  
a\_allLines \= line.all  
if array.size(a\_allLines) \> 0  
    for i \= 0 to array.size(a\_allLines) \- 1  
        line.delete(array.get(a\_allLines, i))  
Remarks  
The array is read-only. Index zero of the array is the ID of the oldest object on the chart.  
See also  
[line.new](https://www.tradingview.com/pine-script-reference/v6/#fun_line.new)[label.all](https://www.tradingview.com/pine-script-reference/v6/#var_label.all)[box.all](https://www.tradingview.com/pine-script-reference/v6/#var_box.all)[table.all](https://www.tradingview.com/pine-script-reference/v6/#var_table.all)

### **linefill.all**

Returns an array filled with all the current linefill objects drawn by the script.  
Type  
array\<linefill\>  
Remarks  
The array is read-only. Index zero of the array is the ID of the oldest object on the chart.

### **low**

Current low price.  
Type  
series float  
Remarks  
Previous values may be accessed with square brackets operator \[\], e.g. low\[1\], low\[2\].  
See also  
[open](https://www.tradingview.com/pine-script-reference/v6/#var_open)[high](https://www.tradingview.com/pine-script-reference/v6/#var_high)[close](https://www.tradingview.com/pine-script-reference/v6/#var_close)[volume](https://www.tradingview.com/pine-script-reference/v6/#var_volume)[time](https://www.tradingview.com/pine-script-reference/v6/#fun_time)[hl2](https://www.tradingview.com/pine-script-reference/v6/#var_hl2)[hlc3](https://www.tradingview.com/pine-script-reference/v6/#var_hlc3)[hlcc4](https://www.tradingview.com/pine-script-reference/v6/#var_hlcc4)[ohlc4](https://www.tradingview.com/pine-script-reference/v6/#var_ohlc4)[ask](https://www.tradingview.com/pine-script-reference/v6/#var_ask)[bid](https://www.tradingview.com/pine-script-reference/v6/#var_bid)

### **minute**

Current bar minute in exchange timezone.  
Type  
series int  
See also  
[minute](https://www.tradingview.com/pine-script-reference/v6/#fun_minute)[time](https://www.tradingview.com/pine-script-reference/v6/#var_time)[year](https://www.tradingview.com/pine-script-reference/v6/#var_year)[month](https://www.tradingview.com/pine-script-reference/v6/#var_month)[weekofyear](https://www.tradingview.com/pine-script-reference/v6/#var_weekofyear)[dayofmonth](https://www.tradingview.com/pine-script-reference/v6/#var_dayofmonth)[dayofweek](https://www.tradingview.com/pine-script-reference/v6/#var_dayofweek)[hour](https://www.tradingview.com/pine-script-reference/v6/#var_hour)[second](https://www.tradingview.com/pine-script-reference/v6/#var_second)

### **month**

Current bar month in exchange timezone.  
Type  
series int  
Remarks  
Note that this variable returns the month based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00) this value can be lower by 1 than the month of the trading day.  
See also  
[month](https://www.tradingview.com/pine-script-reference/v6/#fun_month)[time](https://www.tradingview.com/pine-script-reference/v6/#var_time)[year](https://www.tradingview.com/pine-script-reference/v6/#var_year)[weekofyear](https://www.tradingview.com/pine-script-reference/v6/#var_weekofyear)[dayofmonth](https://www.tradingview.com/pine-script-reference/v6/#var_dayofmonth)[dayofweek](https://www.tradingview.com/pine-script-reference/v6/#var_dayofweek)[hour](https://www.tradingview.com/pine-script-reference/v6/#var_hour)[minute](https://www.tradingview.com/pine-script-reference/v6/#var_minute)[second](https://www.tradingview.com/pine-script-reference/v6/#var_second)

### **na**

A keyword signifying "not available", indicating that a variable has no assigned value.  
Type  
simple na  
Example  
//@version=6  
indicator("na")  
// CORRECT  
// Plot no value when on bars zero to nine. Plot \`close\` on other bars.  
plot(bar\_index \< 10 ? na : close)  
// CORRECT ALTERNATIVE  
// Initialize \`a\` to \`na\`. Reassign \`close\` to \`a\` on bars 10 and later.  
float a \= na  
if bar\_index \>= 10  
    a := close  
plot(a)

// INCORRECT  
// Trying to test the preceding bar's \`close\` for \`na\`.  
// The next line, if uncommented, will cause a compilation error, because direct comparison with \`na\` is not allowed.  
// plot(close\[1\] \== na ? close : close\[1\])  
// CORRECT  
// Use the \`na()\` function to test for \`na\`.  
plot(na(close\[1\]) ? close : close\[1\])  
// CORRECT ALTERNATIVE  
// \`nz()\` tests \`close\[1\]\` for \`na\`. It returns \`close\[1\]\` if it is not \`na\`, and \`close\` if it is.  
plot(nz(close\[1\], close))  
Remarks  
Do not use this variable with [comparison operators](https://www.tradingview.com/pine-script-docs/language/operators/#comparison-operators) to test values for `na`, as it might lead to unexpected behavior. Instead, use the [na](https://www.tradingview.com/pine-script-reference/v6/#fun_na) function. Note that `na` can be used to initialize variables when the initialization statement also specifies the variable's type.  
See also  
[na](https://www.tradingview.com/pine-script-reference/v6/#fun_na)[nz](https://www.tradingview.com/pine-script-reference/v6/#fun_nz)[fixnan](https://www.tradingview.com/pine-script-reference/v6/#fun_fixnan)

### **ohlc4**

Is a shortcut for (open \+ high \+ low \+ close)/4  
Type  
series float  
See also  
[open](https://www.tradingview.com/pine-script-reference/v6/#var_open)[high](https://www.tradingview.com/pine-script-reference/v6/#var_high)[low](https://www.tradingview.com/pine-script-reference/v6/#var_low)[close](https://www.tradingview.com/pine-script-reference/v6/#var_close)[volume](https://www.tradingview.com/pine-script-reference/v6/#var_volume)[time](https://www.tradingview.com/pine-script-reference/v6/#fun_time)[hl2](https://www.tradingview.com/pine-script-reference/v6/#var_hl2)[hlc3](https://www.tradingview.com/pine-script-reference/v6/#var_hlc3)[hlcc4](https://www.tradingview.com/pine-script-reference/v6/#var_hlcc4)

### **open**

Current open price.  
Type  
series float  
Remarks  
Previous values may be accessed with square brackets operator \[\], e.g. open\[1\], open\[2\].  
See also  
[high](https://www.tradingview.com/pine-script-reference/v6/#var_high)[low](https://www.tradingview.com/pine-script-reference/v6/#var_low)[close](https://www.tradingview.com/pine-script-reference/v6/#var_close)[volume](https://www.tradingview.com/pine-script-reference/v6/#var_volume)[time](https://www.tradingview.com/pine-script-reference/v6/#fun_time)[hl2](https://www.tradingview.com/pine-script-reference/v6/#var_hl2)[hlc3](https://www.tradingview.com/pine-script-reference/v6/#var_hlc3)[hlcc4](https://www.tradingview.com/pine-script-reference/v6/#var_hlcc4)[ohlc4](https://www.tradingview.com/pine-script-reference/v6/#var_ohlc4)[ask](https://www.tradingview.com/pine-script-reference/v6/#var_ask)[bid](https://www.tradingview.com/pine-script-reference/v6/#var_bid)

### **polyline.all**

Returns an array containing all current [polyline](https://www.tradingview.com/pine-script-reference/v6/#type_polyline) instances drawn by the script.  
Type  
array\<polyline\>  
Remarks  
The array is read-only. Index zero of the array references the ID of the oldest polyline object on the chart.

### **second**

Current bar second in exchange timezone.  
Type  
series int  
See also  
[second](https://www.tradingview.com/pine-script-reference/v6/#fun_second)[time](https://www.tradingview.com/pine-script-reference/v6/#var_time)[year](https://www.tradingview.com/pine-script-reference/v6/#var_year)[month](https://www.tradingview.com/pine-script-reference/v6/#var_month)[weekofyear](https://www.tradingview.com/pine-script-reference/v6/#var_weekofyear)[dayofmonth](https://www.tradingview.com/pine-script-reference/v6/#var_dayofmonth)[dayofweek](https://www.tradingview.com/pine-script-reference/v6/#var_dayofweek)[hour](https://www.tradingview.com/pine-script-reference/v6/#var_hour)[minute](https://www.tradingview.com/pine-script-reference/v6/#var_minute)

### **session.isfirstbar**

Returns [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) if the current bar is the first bar of the day's session, [false](https://www.tradingview.com/pine-script-reference/v6/#const_false) otherwise. If extended session information is used, only returns `true` on the first bar of the pre-market bars.  
Type  
series bool  
Example  
//@version=6  
strategy("\`session.isfirstbar\` Example", overlay \= true)  
longCondition \= year \>= 2022  
// Place a long order at the \`close\` of the trading session's first bar.  
if session.isfirstbar and longCondition   
    strategy.entry("Long", strategy.long)

// Close the long position at the \`close\` of the trading session's last bar.  
if session.islastbar and barstate.isconfirmed  
    strategy.close("Long", immediately \= true)  
See also  
[session.isfirstbar\_regular](https://www.tradingview.com/pine-script-reference/v6/#var_session.isfirstbar_regular)[session.islastbar](https://www.tradingview.com/pine-script-reference/v6/#var_session.islastbar)[session.islastbar\_regular](https://www.tradingview.com/pine-script-reference/v6/#var_session.islastbar_regular)

### **session.isfirstbar\_regular**

Returns [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) on the first regular session bar of the day, [false](https://www.tradingview.com/pine-script-reference/v6/#const_false) otherwise. The result is the same whether extended session information is used or not.  
Type  
series bool  
Example  
//@version=6  
strategy("\`session.isfirstbar\_regular\` Example", overlay \= true)  
longCondition \= year \>= 2022  
// Place a long order at the \`close\` of the trading session's first bar.  
if session.isfirstbar and longCondition  
    strategy.entry("Long", strategy.long)  
// Close the long position at the \`close\` of the trading session's last bar.  
if session.islastbar\_regular and barstate.isconfirmed  
    strategy.close("Long", immediately \= true)  
See also  
[session.isfirstbar](https://www.tradingview.com/pine-script-reference/v6/#var_session.isfirstbar)[session.islastbar](https://www.tradingview.com/pine-script-reference/v6/#var_session.islastbar)

### **session.islastbar**

Returns [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) if the current bar is the last bar of the day's session, [false](https://www.tradingview.com/pine-script-reference/v6/#const_false) otherwise. If extended session information is used, only returns `true` on the last bar of the post-market bars.  
Type  
series bool  
Example  
//@version=6  
strategy("\`session.islastbar\` Example", overlay \= true)  
longCondition \= year \>= 2022  
// Place a long order at the \`close\` of the trading session's last bar.  
// The position will enter on the \`open\` of next session's first bar.  
if session.islastbar and longCondition  
    strategy.entry("Long", strategy.long)  
 // Close 'Long' position at the close of the last bar of the trading session  
if session.islastbar and barstate.isconfirmed  
    strategy.close("Long", immediately \= true)  
Remarks  
This variable is not guaranteed to return [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) once in every session because the last bar of the session might not exist if no trades occur during what should be the session's last bar.  
This variable is not guaranteed to work as expected on non-standard chart types, e.g., Renko.  
See also  
[session.isfirstbar](https://www.tradingview.com/pine-script-reference/v6/#var_session.isfirstbar)[session.islastbar\_regular](https://www.tradingview.com/pine-script-reference/v6/#var_session.islastbar_regular)

### **session.islastbar\_regular**

Returns [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) on the last regular session bar of the day, [false](https://www.tradingview.com/pine-script-reference/v6/#const_false) otherwise. The result is the same whether extended session information is used or not.  
Type  
series bool  
Example  
//@version=6  
strategy("\`session.islastbar\_regular\` Example", overlay \= true)  
longCondition \= year \>= 2022  
// Place a long order at the \`close\` of the trading session's first bar.  
if session.isfirstbar and longCondition  
    strategy.entry("Long", strategy.long)  
// Close the long position at the \`close\` of the trading session's last bar.  
if session.islastbar\_regular and barstate.isconfirmed  
    strategy.close("Long", immediately \= true)  
Remarks  
This variable is not guaranteed to return [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) once in every session because the last bar of the session might not exist if no trades occur during what should be the session's last bar.  
This variable is not guaranteed to work as expected on non-standard chart types, e.g., Renko.  
See also  
[session.isfirstbar](https://www.tradingview.com/pine-script-reference/v6/#var_session.isfirstbar)[session.islastbar](https://www.tradingview.com/pine-script-reference/v6/#var_session.islastbar)[session.isfirstbar\_regular](https://www.tradingview.com/pine-script-reference/v6/#var_session.isfirstbar_regular)

### **session.ismarket**

Returns [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) if the current bar is a part of the regular trading hours (i.e. market hours), [false](https://www.tradingview.com/pine-script-reference/v6/#const_false) otherwise.  
Type  
series bool  
See also  
[session.ispremarket](https://www.tradingview.com/pine-script-reference/v6/#var_session.ispremarket)[session.ispostmarket](https://www.tradingview.com/pine-script-reference/v6/#var_session.ispostmarket)

### **session.ispostmarket**

Returns [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) if the current bar is a part of the post-market, [false](https://www.tradingview.com/pine-script-reference/v6/#const_false) otherwise. On non-intraday charts always returns `false`.  
Type  
series bool  
See also  
[session.ismarket](https://www.tradingview.com/pine-script-reference/v6/#var_session.ismarket)[session.ispremarket](https://www.tradingview.com/pine-script-reference/v6/#var_session.ispremarket)

### **session.ispremarket**

Returns [true](https://www.tradingview.com/pine-script-reference/v6/#const_true) if the current bar is a part of the pre-market, [false](https://www.tradingview.com/pine-script-reference/v6/#const_false) otherwise. On non-intraday charts always returns `false`.  
Type  
series bool  
See also  
[session.ismarket](https://www.tradingview.com/pine-script-reference/v6/#var_session.ismarket)[session.ispostmarket](https://www.tradingview.com/pine-script-reference/v6/#var_session.ispostmarket)

### **strategy.account\_currency**

Returns the currency used to calculate results, which can be set in the strategy's properties.  
Type  
simple string  
See also  
[strategy](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy)[strategy.convert\_to\_account](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.convert_to_account)[strategy.convert\_to\_symbol](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.convert_to_symbol)

### **strategy.avg\_losing\_trade**

Returns the average amount of money lost per losing trade. Calculated as the sum of losses divided by the number of losing trades.  
Type  
series float  
See also  
[strategy.avg\_losing\_trade\_percent](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.avg_losing_trade_percent)

### **strategy.avg\_losing\_trade\_percent**

Returns the average percentage loss per losing trade. Calculated as the sum of loss percentages divided by the number of losing trades.  
Type  
series float  
See also  
[strategy.avg\_losing\_trade](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.avg_losing_trade)

### **strategy.avg\_trade**

Returns the average amount of money gained or lost per trade. Calculated as the sum of all profits and losses divided by the number of closed trades.  
Type  
series float  
See also  
[strategy.avg\_trade\_percent](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.avg_trade_percent)

### **strategy.avg\_trade\_percent**

Returns the average percentage gain or loss per trade. Calculated as the sum of all profit and loss percentages divided by the number of closed trades.  
Type  
series float  
See also  
[strategy.avg\_trade](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.avg_trade)

### **strategy.avg\_winning\_trade**

Returns the average amount of money gained per winning trade. Calculated as the sum of profits divided by the number of winning trades.  
Type  
series float  
See also  
[strategy.avg\_winning\_trade\_percent](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.avg_winning_trade_percent)

### **strategy.avg\_winning\_trade\_percent**

Returns the average percentage gain per winning trade. Calculated as the sum of profit percentages divided by the number of winning trades.  
Type  
series float  
See also  
[strategy.avg\_winning\_trade](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.avg_winning_trade)

### **strategy.closedtrades**

Number of trades, which were closed for the whole trading range.  
Type  
series int  
See also  
[strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_size)[strategy.opentrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.opentrades)[strategy.wintrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.wintrades)[strategy.losstrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.losstrades)[strategy.eventrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.eventrades)

### **strategy.closedtrades.first\_index**

The index, or trade number, of the first (oldest) trade listed in the List of Trades. This number is usually zero. If more trades than the allowed limit have been closed, the oldest trades are removed, and this number is the index of the oldest remaining trade.  
Type  
series int  
See also  
[strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_size)[strategy.opentrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.opentrades)[strategy.wintrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.wintrades)[strategy.losstrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.losstrades)[strategy.eventrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.eventrades)

### **strategy.equity**

Current equity ([strategy.initial\_capital](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.initial_capital) \+ [strategy.netprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.netprofit) \+ [strategy.openprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.openprofit)).  
Type  
series float  
See also  
[strategy.netprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.netprofit)[strategy.openprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.openprofit)[strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_size)

### **strategy.eventrades**

Number of breakeven trades for the whole trading range.  
Type  
series int  
See also  
[strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_size)[strategy.opentrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.opentrades)[strategy.closedtrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.closedtrades)[strategy.wintrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.wintrades)[strategy.losstrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.losstrades)

### **strategy.grossloss**

Total currency value of all completed losing trades.  
Type  
series float  
See also  
[strategy.netprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.netprofit)[strategy.grossprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.grossprofit)

### **strategy.grossloss\_percent**

The total value of all completed losing trades, expressed as a percentage of the initial capital.  
Type  
series float  
See also  
[strategy.grossloss](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.grossloss)

### **strategy.grossprofit**

Total currency value of all completed winning trades.  
Type  
series float  
See also  
[strategy.netprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.netprofit)[strategy.grossloss](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.grossloss)

### **strategy.grossprofit\_percent**

The total currency value of all completed winning trades, expressed as a percentage of the initial capital.  
Type  
series float  
See also  
[strategy.grossprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.grossprofit)

### **strategy.initial\_capital**

The amount of initial capital set in the strategy properties.  
Type  
series float  
See also  
[strategy](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy)

### **strategy.losstrades**

Number of unprofitable trades for the whole trading range.  
Type  
series int  
See also  
[strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_size)[strategy.opentrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.opentrades)[strategy.closedtrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.closedtrades)[strategy.wintrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.wintrades)[strategy.eventrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.eventrades)

### **strategy.margin\_liquidation\_price**

When margin is used in a strategy, returns the price point where a simulated margin call will occur and liquidate enough of the position to meet the margin requirements.  
Type  
series float  
Example  
//@version=6  
strategy("Margin call management", overlay \= true, margin\_long \= 25, margin\_short \= 25,   
  default\_qty\_type \= strategy.percent\_of\_equity, default\_qty\_value \= 395\)

float maFast \= ta.sma(close, 14\)  
float maSlow \= ta.sma(close, 28\)

if ta.crossover(maFast, maSlow)  
    strategy.entry("Long", strategy.long)

if ta.crossunder(maFast, maSlow)  
    strategy.entry("Short", strategy.short)

changePercent(v1, v2) \=\>   
    float result \= (v1 \- v2) \* 100 / math.abs(v2)

// exit when we're 10% away from a margin call, to prevent it.  
if math.abs(changePercent(close, strategy.margin\_liquidation\_price)) \<= 10  
    strategy.close("Long")  
    strategy.close("Short")  
Remarks  
The variable returns [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) if the strategy does not use margin, i.e., the [strategy](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy) declaration statement does not specify an argument for the `margin_long` or `margin_short` parameter.

### **strategy.max\_contracts\_held\_all**

Maximum number of contracts/shares/lots/units in one trade for the whole trading range.  
Type  
series float  
See also  
[strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_size)[strategy.max\_contracts\_held\_long](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.max_contracts_held_long)[strategy.max\_contracts\_held\_short](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.max_contracts_held_short)

### **strategy.max\_contracts\_held\_long**

Maximum number of contracts/shares/lots/units in one long trade for the whole trading range.  
Type  
series float  
See also  
[strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_size)[strategy.max\_contracts\_held\_all](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.max_contracts_held_all)[strategy.max\_contracts\_held\_short](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.max_contracts_held_short)

### **strategy.max\_contracts\_held\_short**

Maximum number of contracts/shares/lots/units in one short trade for the whole trading range.  
Type  
series float  
See also  
[strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_size)[strategy.max\_contracts\_held\_all](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.max_contracts_held_all)[strategy.max\_contracts\_held\_long](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.max_contracts_held_long)

### **strategy.max\_drawdown**

Maximum equity drawdown value for the whole trading range.  
Type  
series float  
See also  
[strategy.netprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.netprofit)[strategy.equity](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.equity)[strategy.max\_runup](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.max_runup)

### **strategy.max\_drawdown\_percent**

The maximum equity drawdown value for the whole trading range, expressed as a percentage and calculated by formula: `Lowest Value During Trade / (Entry Price x Quantity) * 100`.  
Type  
series float  
See also  
[strategy.max\_drawdown](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.max_drawdown)

### **strategy.max\_runup**

Maximum equity run-up value for the whole trading range.  
Type  
series float  
See also  
[strategy.netprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.netprofit)[strategy.equity](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.equity)[strategy.max\_drawdown](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.max_drawdown)

### **strategy.max\_runup\_percent**

The maximum equity run-up value for the whole trading range, expressed as a percentage and calculated by formula: `Highest Value During Trade / (Entry Price x Quantity) * 100`.  
Type  
series float  
See also  
[strategy.max\_runup](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.max_runup)

### **strategy.netprofit**

Total currency value of all completed trades.  
Type  
series float  
See also  
[strategy.openprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.openprofit)[strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_size)[strategy.grossprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.grossprofit)[strategy.grossloss](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.grossloss)

### **strategy.netprofit\_percent**

The total value of all completed trades, expressed as a percentage of the initial capital.  
Type  
series float  
See also  
[strategy.netprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.netprofit)

### **strategy.openprofit**

Current unrealized profit or loss for all open positions.  
Type  
series float  
See also  
[strategy.netprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.netprofit)[strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_size)

### **strategy.openprofit\_percent**

The current unrealized profit or loss for all open positions, expressed as a percentage and calculated by formula: `openPL / realizedEquity * 100`.  
Type  
series float  
See also  
[strategy.openprofit](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.openprofit)

### **strategy.opentrades**

Number of market position entries, which were not closed and remain opened. If there is no open market position, 0 is returned.  
Type  
series int  
See also  
[strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_size)

### **strategy.opentrades.capital\_held**

Returns the capital amount currently held by open trades.  
Type  
series float  
Example  
//@version=6  
strategy(  
   "strategy.opentrades.capital\_held example", overlay=false, margin\_long=50, margin\_short=50,   
   default\_qty\_type \= strategy.percent\_of\_equity, default\_qty\_value \= 100  
 )

// Enter a short position on the first bar.  
if barstate.isfirst  
    strategy.entry("Short", strategy.short)

// Plot the capital held by the short position.  
plot(strategy.opentrades.capital\_held, "Capital held")  
// Highlight the chart background if the position is completely closed by margin calls.  
bgcolor(bar\_index \> 0 and strategy.opentrades.capital\_held \== 0 ? color.new(color.red, 60\) : na)  
Remarks  
This variable returns [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) if the strategy does not simulate funding trades with a portion of the hypothetical account, i.e., if the [strategy](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy) function does not include nonzero `margin_long` or `margin_short` arguments.

### **strategy.position\_avg\_price**

Average entry price of current market position. If the market position is flat, 'NaN' is returned.  
Type  
series float  
See also  
[strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_size)

### **strategy.position\_entry\_name**

Name of the order that initially opened current market position.  
Type  
series string  
See also  
[strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_size)

### **strategy.position\_size**

Direction and size of the current market position. If the value is \> 0, the market position is long. If the value is \< 0, the market position is short. The absolute value is the number of contracts/shares/lots/units in trade (position size).  
Type  
series float  
See also  
[strategy.position\_avg\_price](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_avg_price)

### **strategy.wintrades**

Number of profitable trades for the whole trading range.  
Type  
series int  
See also  
[strategy.position\_size](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.position_size)[strategy.opentrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.opentrades)[strategy.closedtrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.closedtrades)[strategy.losstrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.losstrades)[strategy.eventrades](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.eventrades)

### **syminfo.basecurrency**

Returns a string containing the code representing the symbol's base currency (i.e., the traded currency or coin) if the instrument is a Forex or Crypto pair or a derivative based on such a pair. Otherwise, it returns an empty string. For example, this variable returns "EUR" for "EURJPY", "BTC" for "BTCUSDT", "CAD" for "CME:6C1\!", and "" for "NASDAQ:AAPL".  
Type  
simple string  
See also  
[syminfo.currency](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.currency)[syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker)

### **syminfo.country**

Returns the two-letter code of the country where the symbol is traded, in the [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) format, or [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) if the exchange is not directly tied to a specific country. For example, on "NASDAQ:AAPL" it will return "US", on "LSE:AAPL" it will return "GB", and on "BITSTAMP:BTCUSD it will return [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).  
Type  
simple string

### **syminfo.currency**

Returns a string containing the code representing the currency of the symbol's prices. For example, this variable returns "USD" for "NASDAQ:AAPL" and "JPY" for "EURJPY".  
Type  
simple string  
See also  
[syminfo.basecurrency](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.basecurrency)[syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker)[currency.USD](https://www.tradingview.com/pine-script-reference/v6/#const_currency.USD)[currency.EUR](https://www.tradingview.com/pine-script-reference/v6/#const_currency.EUR)

### **syminfo.description**

Description for the current symbol.  
Type  
simple string  
See also  
[syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker)[syminfo.prefix](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.prefix)

### **syminfo.employees**

The number of employees the company has.  
Type  
simple int  
Example  
//@version=6  
indicator("syminfo simple")  
//@variable A table containing information about a company's employees, shareholders, and shares.  
var result\_table \= table.new(position \= position.top\_right, columns \= 2, rows \= 5, border\_width \= 1\)  
if barstate.islastconfirmedhistory  
    // Add header cells  
    table.cell(table\_id \= result\_table, column \= 0, row \= 0, text \= "name")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 0, text \= "value")  
    // Add employee info cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 1, text \= "employees")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 1, text \= str.tostring(syminfo.employees))  
    // Add shareholder cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 2, text \= "shareholders")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 2, text \= str.tostring(syminfo.shareholders))  
    // Add float shares outstanding cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 3, text \= "shares\_outstanding\_float")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 3, text \= str.tostring(syminfo.shares\_outstanding\_float))  
    // Add total shares outstanding cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 4, text \= "shares\_outstanding\_total")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 4, text \= str.tostring(syminfo.shares\_outstanding\_total))  
See also  
[syminfo.shareholders](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.shareholders)[syminfo.shares\_outstanding\_float](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.shares_outstanding_float)[syminfo.shares\_outstanding\_total](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.shares_outstanding_total)

### **syminfo.expiration\_date**

A UNIX timestamp representing the start of the last day of the current futures contract. This variable is only compatible with non-continuous futures symbols. On other symbols, it returns [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).  
Type  
simple int

### **syminfo.industry**

Returns the industry of the symbol, or [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) if the symbol has no industry. Example: "Internet Software/Services", "Packaged software", "Integrated Oil", "Motor Vehicles", etc. These are the same values one can see in the chart's "Symbol info" window.  
Type  
simple string  
Remarks  
A sector is a broad section of the economy. An industry is a narrower classification. NASDAQ:CAT (Caterpillar, Inc.) for example, belongs to the "Producer Manufacturing" sector and the "Trucks/Construction/Farm Machinery" industry.

### **syminfo.main\_tickerid**

A ticker identifier representing the current chart's symbol. The value contains an exchange prefix and a symbol name, separated by a colon (e.g., "NASDAQ:AAPL"). It can also include information about data modifications such as dividend adjustment, non-standard chart type, currency conversion, etc. Unlike [syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.tickerid), this variable's value does not change when used in the `expression` argument of a `request.*()` function call.  
Type  
simple string  
See also  
[ticker.new](https://www.tradingview.com/pine-script-reference/v6/#fun_ticker.new)[timeframe.main\_period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.main_period)[syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.tickerid)[syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker)[timeframe.period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.period)[timeframe.multiplier](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.multiplier)[syminfo.root](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.root)

### **syminfo.mincontract**

The smallest amount of the current symbol that can be traded. This limit is set by the exchange. For cryptocurrencies, it is often less than 1 token. For most other types of asset, it is often 1\.  
Type  
simple float  
See also  
[syminfo.mintick](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.mintick)[syminfo.pointvalue](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.pointvalue)

### **syminfo.minmove**

Returns a whole number used to calculate the smallest increment between a symbol's price movements ([syminfo.mintick](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.mintick)). It is the numerator in the [syminfo.mintick](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.mintick) formula: `syminfo.minmove / syminfo.pricescale = syminfo.mintick`.  
Type  
simple int  
See also  
[ticker.new](https://www.tradingview.com/pine-script-reference/v6/#fun_ticker.new)[syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker)[timeframe.period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.period)[timeframe.multiplier](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.multiplier)[syminfo.root](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.root)

### **syminfo.mintick**

Min tick value for the current symbol.  
Type  
simple float  
See also  
[syminfo.pointvalue](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.pointvalue)[syminfo.mincontract](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.mincontract)

### **syminfo.pointvalue**

Point value for the current symbol.  
Type  
simple float  
See also  
[syminfo.mintick](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.mintick)[syminfo.mincontract](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.mincontract)

### **syminfo.prefix**

Prefix of current symbol name (i.e. for 'CME\_EOD:TICKER' prefix is 'CME\_EOD').  
Type  
simple string  
Example  
//@version=6  
indicator("syminfo.prefix")

// If current chart symbol is 'BATS:MSFT' then syminfo.prefix is 'BATS'.  
if barstate.islastconfirmedhistory  
    label.new(bar\_index, high, text=syminfo.prefix)  
See also  
[syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker)[syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.tickerid)

### **syminfo.pricescale**

Returns a whole number used to calculate the smallest increment between a symbol's price movements ([syminfo.mintick](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.mintick)). It is the denominator in the [syminfo.mintick](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.mintick) formula: `syminfo.minmove / syminfo.pricescale = syminfo.mintick`.  
Type  
simple int  
See also  
[ticker.new](https://www.tradingview.com/pine-script-reference/v6/#fun_ticker.new)[syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker)[timeframe.period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.period)[timeframe.multiplier](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.multiplier)[syminfo.root](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.root)

### **syminfo.recommendations\_buy**

The number of analysts who gave the current symbol a "Buy" rating.  
Type  
series int  
Example  
//@version=6  
indicator("syminfo recommendations", overlay \= true)  
//@variable A table containing information about analyst recommendations.  
var table ratings \= table.new(position.top\_right, 8, 2, frame\_color \= \#000000)  
if barstate.islastconfirmedhistory  
    //@variable The time value one year from the date of the last analyst recommendations.  
    int YTD \= syminfo.target\_price\_date \+ timeframe.in\_seconds("12M") \* 1000  
    // Add header cells.  
    table.cell(ratings, 0, 0, "Start Date", bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 1, 0, "End Date", bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 2, 0, "Buy", bgcolor \= color.teal, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 3, 0, "Strong Buy", bgcolor \= color.lime, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 4, 0, "Sell", bgcolor \= color.maroon, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 5, 0, "Strong Sell", bgcolor \= color.red, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 6, 0, "Hold", bgcolor \= color.orange, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 7, 0, "Total", bgcolor \= color.silver, text\_color \= \#000000, text\_size \= size.large)  
    // Recommendation strings  
    string startDate         \= str.format\_time(syminfo.recommendations\_date, "yyyy-MM-dd")  
    string endDate           \= str.format\_time(YTD, "yyyy-MM-dd")  
    string buyRatings        \= str.tostring(syminfo.recommendations\_buy)  
    string strongBuyRatings  \= str.tostring(syminfo.recommendations\_buy\_strong)  
    string sellRatings       \= str.tostring(syminfo.recommendations\_sell)  
    string strongSellRatings \= str.tostring(syminfo.recommendations\_sell\_strong)  
    string holdRatings       \= str.tostring(syminfo.recommendations\_hold)  
    string totalRatings      \= str.tostring(syminfo.recommendations\_total)  
    // Add value cells  
    table.cell(ratings, 0, 1, startDate, bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 1, 1, endDate, bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 2, 1, buyRatings, bgcolor \= color.teal, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 3, 1, strongBuyRatings, bgcolor \= color.lime, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 4, 1, sellRatings, bgcolor \= color.maroon, text\_color \= \#000000, text\_size \= size.large)  
See also  
[syminfo.recommendations\_buy\_strong](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_buy_strong)[syminfo.recommendations\_date](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_date)[syminfo.recommendations\_hold](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_hold)[syminfo.recommendations\_total](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_total)[syminfo.recommendations\_sell](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_sell)[syminfo.recommendations\_sell\_strong](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_sell_strong)

### **syminfo.recommendations\_buy\_strong**

The number of analysts who gave the current symbol a "Strong Buy" rating.  
Type  
series int  
Example  
//@version=6  
indicator("syminfo recommendations", overlay \= true)  
//@variable A table containing information about analyst recommendations.  
var table ratings \= table.new(position.top\_right, 8, 2, frame\_color \= \#000000)  
if barstate.islastconfirmedhistory  
    //@variable The time value one year from the date of the last analyst recommendations.  
    int YTD \= syminfo.target\_price\_date \+ timeframe.in\_seconds("12M") \* 1000  
    // Add header cells.  
    table.cell(ratings, 0, 0, "Start Date", bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 1, 0, "End Date", bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 2, 0, "Buy", bgcolor \= color.teal, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 3, 0, "Strong Buy", bgcolor \= color.lime, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 4, 0, "Sell", bgcolor \= color.maroon, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 5, 0, "Strong Sell", bgcolor \= color.red, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 6, 0, "Hold", bgcolor \= color.orange, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 7, 0, "Total", bgcolor \= color.silver, text\_color \= \#000000, text\_size \= size.large)  
    // Recommendation strings  
    string startDate         \= str.format\_time(syminfo.recommendations\_date, "yyyy-MM-dd")  
    string endDate           \= str.format\_time(YTD, "yyyy-MM-dd")  
    string buyRatings        \= str.tostring(syminfo.recommendations\_buy)  
    string strongBuyRatings  \= str.tostring(syminfo.recommendations\_buy\_strong)  
    string sellRatings       \= str.tostring(syminfo.recommendations\_sell)  
    string strongSellRatings \= str.tostring(syminfo.recommendations\_sell\_strong)  
    string holdRatings       \= str.tostring(syminfo.recommendations\_hold)  
    string totalRatings      \= str.tostring(syminfo.recommendations\_total)  
    // Add value cells  
    table.cell(ratings, 0, 1, startDate, bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 1, 1, endDate, bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 2, 1, buyRatings, bgcolor \= color.teal, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 3, 1, strongBuyRatings, bgcolor \= color.lime, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 4, 1, sellRatings, bgcolor \= color.maroon, text\_color \= \#000000, text\_size \= size.large)  
See also  
[syminfo.recommendations\_buy](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_buy)[syminfo.recommendations\_date](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_date)[syminfo.recommendations\_hold](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_hold)[syminfo.recommendations\_total](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_total)[syminfo.recommendations\_sell](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_sell)[syminfo.recommendations\_sell\_strong](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_sell_strong)

### **syminfo.recommendations\_date**

The starting date of the last set of recommendations for the current symbol.  
Type  
series int  
Example  
//@version=6  
indicator("syminfo recommendations", overlay \= true)  
//@variable A table containing information about analyst recommendations.  
var table ratings \= table.new(position.top\_right, 8, 2, frame\_color \= \#000000)  
if barstate.islastconfirmedhistory  
    //@variable The time value one year from the date of the last analyst recommendations.  
    int YTD \= syminfo.target\_price\_date \+ timeframe.in\_seconds("12M") \* 1000  
    // Add header cells.  
    table.cell(ratings, 0, 0, "Start Date", bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 1, 0, "End Date", bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 2, 0, "Buy", bgcolor \= color.teal, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 3, 0, "Strong Buy", bgcolor \= color.lime, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 4, 0, "Sell", bgcolor \= color.maroon, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 5, 0, "Strong Sell", bgcolor \= color.red, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 6, 0, "Hold", bgcolor \= color.orange, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 7, 0, "Total", bgcolor \= color.silver, text\_color \= \#000000, text\_size \= size.large)  
    // Recommendation strings  
    string startDate         \= str.format\_time(syminfo.recommendations\_date, "yyyy-MM-dd")  
    string endDate           \= str.format\_time(YTD, "yyyy-MM-dd")  
    string buyRatings        \= str.tostring(syminfo.recommendations\_buy)  
    string strongBuyRatings  \= str.tostring(syminfo.recommendations\_buy\_strong)  
    string sellRatings       \= str.tostring(syminfo.recommendations\_sell)  
    string strongSellRatings \= str.tostring(syminfo.recommendations\_sell\_strong)  
    string holdRatings       \= str.tostring(syminfo.recommendations\_hold)  
    string totalRatings      \= str.tostring(syminfo.recommendations\_total)  
    // Add value cells  
    table.cell(ratings, 0, 1, startDate, bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 1, 1, endDate, bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 2, 1, buyRatings, bgcolor \= color.teal, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 3, 1, strongBuyRatings, bgcolor \= color.lime, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 4, 1, sellRatings, bgcolor \= color.maroon, text\_color \= \#000000, text\_size \= size.large)  
See also  
[syminfo.recommendations\_buy](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_buy)[syminfo.recommendations\_buy\_strong](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_buy_strong)[syminfo.recommendations\_hold](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_hold)[syminfo.recommendations\_total](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_total)[syminfo.recommendations\_sell](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_sell)[syminfo.recommendations\_sell\_strong](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_sell_strong)

### **syminfo.recommendations\_hold**

The number of analysts who gave the current symbol a "Hold" rating.  
Type  
series int  
Example  
//@version=6  
indicator("syminfo recommendations", overlay \= true)  
//@variable A table containing information about analyst recommendations.  
var table ratings \= table.new(position.top\_right, 8, 2, frame\_color \= \#000000)  
if barstate.islastconfirmedhistory  
    //@variable The time value one year from the date of the last analyst recommendations.  
    int YTD \= syminfo.target\_price\_date \+ timeframe.in\_seconds("12M") \* 1000  
    // Add header cells.  
    table.cell(ratings, 0, 0, "Start Date", bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 1, 0, "End Date", bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 2, 0, "Buy", bgcolor \= color.teal, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 3, 0, "Strong Buy", bgcolor \= color.lime, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 4, 0, "Sell", bgcolor \= color.maroon, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 5, 0, "Strong Sell", bgcolor \= color.red, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 6, 0, "Hold", bgcolor \= color.orange, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 7, 0, "Total", bgcolor \= color.silver, text\_color \= \#000000, text\_size \= size.large)  
    // Recommendation strings  
    string startDate         \= str.format\_time(syminfo.recommendations\_date, "yyyy-MM-dd")  
    string endDate           \= str.format\_time(YTD, "yyyy-MM-dd")  
    string buyRatings        \= str.tostring(syminfo.recommendations\_buy)  
    string strongBuyRatings  \= str.tostring(syminfo.recommendations\_buy\_strong)  
    string sellRatings       \= str.tostring(syminfo.recommendations\_sell)  
    string strongSellRatings \= str.tostring(syminfo.recommendations\_sell\_strong)  
    string holdRatings       \= str.tostring(syminfo.recommendations\_hold)  
    string totalRatings      \= str.tostring(syminfo.recommendations\_total)  
    // Add value cells  
    table.cell(ratings, 0, 1, startDate, bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 1, 1, endDate, bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 2, 1, buyRatings, bgcolor \= color.teal, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 3, 1, strongBuyRatings, bgcolor \= color.lime, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 4, 1, sellRatings, bgcolor \= color.maroon, text\_color \= \#000000, text\_size \= size.large)  
See also  
[syminfo.recommendations\_buy](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_buy)[syminfo.recommendations\_buy\_strong](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_buy_strong)[syminfo.recommendations\_date](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_date)[syminfo.recommendations\_total](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_total)[syminfo.recommendations\_sell](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_sell)[syminfo.recommendations\_sell\_strong](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_sell_strong)

### **syminfo.recommendations\_sell**

The number of analysts who gave the current symbol a "Sell" rating.  
Type  
series int  
Example  
//@version=6  
indicator("syminfo recommendations", overlay \= true)  
//@variable A table containing information about analyst recommendations.  
var table ratings \= table.new(position.top\_right, 8, 2, frame\_color \= \#000000)  
if barstate.islastconfirmedhistory  
    //@variable The time value one year from the date of the last analyst recommendations.  
    int YTD \= syminfo.target\_price\_date \+ timeframe.in\_seconds("12M") \* 1000  
    // Add header cells.  
    table.cell(ratings, 0, 0, "Start Date", bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 1, 0, "End Date", bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 2, 0, "Buy", bgcolor \= color.teal, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 3, 0, "Strong Buy", bgcolor \= color.lime, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 4, 0, "Sell", bgcolor \= color.maroon, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 5, 0, "Strong Sell", bgcolor \= color.red, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 6, 0, "Hold", bgcolor \= color.orange, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 7, 0, "Total", bgcolor \= color.silver, text\_color \= \#000000, text\_size \= size.large)  
    // Recommendation strings  
    string startDate         \= str.format\_time(syminfo.recommendations\_date, "yyyy-MM-dd")  
    string endDate           \= str.format\_time(YTD, "yyyy-MM-dd")  
    string buyRatings        \= str.tostring(syminfo.recommendations\_buy)  
    string strongBuyRatings  \= str.tostring(syminfo.recommendations\_buy\_strong)  
    string sellRatings       \= str.tostring(syminfo.recommendations\_sell)  
    string strongSellRatings \= str.tostring(syminfo.recommendations\_sell\_strong)  
    string holdRatings       \= str.tostring(syminfo.recommendations\_hold)  
    string totalRatings      \= str.tostring(syminfo.recommendations\_total)  
    // Add value cells  
    table.cell(ratings, 0, 1, startDate, bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 1, 1, endDate, bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 2, 1, buyRatings, bgcolor \= color.teal, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 3, 1, strongBuyRatings, bgcolor \= color.lime, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 4, 1, sellRatings, bgcolor \= color.maroon, text\_color \= \#000000, text\_size \= size.large)  
See also  
[syminfo.recommendations\_buy](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_buy)[syminfo.recommendations\_buy\_strong](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_buy_strong)[syminfo.recommendations\_date](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_date)[syminfo.recommendations\_hold](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_hold)[syminfo.recommendations\_total](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_total)[syminfo.recommendations\_sell\_strong](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_sell_strong)

### **syminfo.recommendations\_sell\_strong**

The number of analysts who gave the current symbol a "Strong Sell" rating.  
Type  
series int  
Example  
//@version=6  
indicator("syminfo recommendations", overlay \= true)  
//@variable A table containing information about analyst recommendations.  
var table ratings \= table.new(position.top\_right, 8, 2, frame\_color \= \#000000)  
if barstate.islastconfirmedhistory  
    //@variable The time value one year from the date of the last analyst recommendations.  
    int YTD \= syminfo.target\_price\_date \+ timeframe.in\_seconds("12M") \* 1000  
    // Add header cells.  
    table.cell(ratings, 0, 0, "Start Date", bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 1, 0, "End Date", bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 2, 0, "Buy", bgcolor \= color.teal, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 3, 0, "Strong Buy", bgcolor \= color.lime, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 4, 0, "Sell", bgcolor \= color.maroon, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 5, 0, "Strong Sell", bgcolor \= color.red, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 6, 0, "Hold", bgcolor \= color.orange, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 7, 0, "Total", bgcolor \= color.silver, text\_color \= \#000000, text\_size \= size.large)  
    // Recommendation strings  
    string startDate         \= str.format\_time(syminfo.recommendations\_date, "yyyy-MM-dd")  
    string endDate           \= str.format\_time(YTD, "yyyy-MM-dd")  
    string buyRatings        \= str.tostring(syminfo.recommendations\_buy)  
    string strongBuyRatings  \= str.tostring(syminfo.recommendations\_buy\_strong)  
    string sellRatings       \= str.tostring(syminfo.recommendations\_sell)  
    string strongSellRatings \= str.tostring(syminfo.recommendations\_sell\_strong)  
    string holdRatings       \= str.tostring(syminfo.recommendations\_hold)  
    string totalRatings      \= str.tostring(syminfo.recommendations\_total)  
    // Add value cells  
    table.cell(ratings, 0, 1, startDate, bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 1, 1, endDate, bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 2, 1, buyRatings, bgcolor \= color.teal, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 3, 1, strongBuyRatings, bgcolor \= color.lime, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 4, 1, sellRatings, bgcolor \= color.maroon, text\_color \= \#000000, text\_size \= size.large)  
See also  
[syminfo.recommendations\_buy](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_buy)[syminfo.recommendations\_buy\_strong](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_buy_strong)[syminfo.recommendations\_date](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_date)[syminfo.recommendations\_hold](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_hold)[syminfo.recommendations\_total](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_total)[syminfo.recommendations\_sell](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_sell)

### **syminfo.recommendations\_total**

The total number of recommendations for the current symbol.  
Type  
series int  
Example  
//@version=6  
indicator("syminfo recommendations", overlay \= true)  
//@variable A table containing information about analyst recommendations.  
var table ratings \= table.new(position.top\_right, 8, 2, frame\_color \= \#000000)  
if barstate.islastconfirmedhistory  
    //@variable The time value one year from the date of the last analyst recommendations.  
    int YTD \= syminfo.target\_price\_date \+ timeframe.in\_seconds("12M") \* 1000  
    // Add header cells.  
    table.cell(ratings, 0, 0, "Start Date", bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 1, 0, "End Date", bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 2, 0, "Buy", bgcolor \= color.teal, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 3, 0, "Strong Buy", bgcolor \= color.lime, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 4, 0, "Sell", bgcolor \= color.maroon, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 5, 0, "Strong Sell", bgcolor \= color.red, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 6, 0, "Hold", bgcolor \= color.orange, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 7, 0, "Total", bgcolor \= color.silver, text\_color \= \#000000, text\_size \= size.large)  
    // Recommendation strings  
    string startDate         \= str.format\_time(syminfo.recommendations\_date, "yyyy-MM-dd")  
    string endDate           \= str.format\_time(YTD, "yyyy-MM-dd")  
    string buyRatings        \= str.tostring(syminfo.recommendations\_buy)  
    string strongBuyRatings  \= str.tostring(syminfo.recommendations\_buy\_strong)  
    string sellRatings       \= str.tostring(syminfo.recommendations\_sell)  
    string strongSellRatings \= str.tostring(syminfo.recommendations\_sell\_strong)  
    string holdRatings       \= str.tostring(syminfo.recommendations\_hold)  
    string totalRatings      \= str.tostring(syminfo.recommendations\_total)  
    // Add value cells  
    table.cell(ratings, 0, 1, startDate, bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 1, 1, endDate, bgcolor \= color.gray, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 2, 1, buyRatings, bgcolor \= color.teal, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 3, 1, strongBuyRatings, bgcolor \= color.lime, text\_color \= \#000000, text\_size \= size.large)  
    table.cell(ratings, 4, 1, sellRatings, bgcolor \= color.maroon, text\_color \= \#000000, text\_size \= size.large)  
See also  
[syminfo.recommendations\_buy](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_buy)[syminfo.recommendations\_buy\_strong](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_buy_strong)[syminfo.recommendations\_date](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_date)[syminfo.recommendations\_hold](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_hold)[syminfo.recommendations\_sell](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_sell)[syminfo.recommendations\_sell\_strong](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.recommendations_sell_strong)

### **syminfo.root**

Root for derivatives like futures contract. For other symbols returns the same value as [syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker).  
Type  
simple string  
Example  
//@version=6  
indicator("syminfo.root")

// If the current chart symbol is continuous futures ('ES1\!'), it would display 'ES'.  
if barstate.islastconfirmedhistory  
    label.new(bar\_index, high, syminfo.root)  
See also  
[syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker)[syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.tickerid)

### **syminfo.sector**

Returns the sector of the symbol, or [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) if the symbol has no sector. Example: "Electronic Technology", "Technology services", "Energy Minerals", "Consumer Durables", etc. These are the same values one can see in the chart's "Symbol info" window.  
Type  
simple string  
Remarks  
A sector is a broad section of the economy. An industry is a narrower classification. NASDAQ:CAT (Caterpillar, Inc.) for example, belongs to the "Producer Manufacturing" sector and the "Trucks/Construction/Farm Machinery" industry.

### **syminfo.session**

Session type of the chart main series. Possible values are [session.regular](https://www.tradingview.com/pine-script-reference/v6/#const_session.regular), [session.extended](https://www.tradingview.com/pine-script-reference/v6/#const_session.extended).  
Type  
simple string  
See also  
[session.regular](https://www.tradingview.com/pine-script-reference/v6/#const_session.regular)[session.extended](https://www.tradingview.com/pine-script-reference/v6/#const_session.extended)

### **syminfo.shareholders**

The number of shareholders the company has.  
Type  
simple int  
Example  
//@version=6  
indicator("syminfo simple")  
//@variable A table containing information about a company's employees, shareholders, and shares.  
var result\_table \= table.new(position \= position.top\_right, columns \= 2, rows \= 5, border\_width \= 1\)  
if barstate.islastconfirmedhistory  
    // Add header cells  
    table.cell(table\_id \= result\_table, column \= 0, row \= 0, text \= "name")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 0, text \= "value")  
    // Add employee info cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 1, text \= "employees")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 1, text \= str.tostring(syminfo.employees))  
    // Add shareholder cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 2, text \= "shareholders")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 2, text \= str.tostring(syminfo.shareholders))  
    // Add float shares outstanding cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 3, text \= "shares\_outstanding\_float")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 3, text \= str.tostring(syminfo.shares\_outstanding\_float))  
    // Add total shares outstanding cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 4, text \= "shares\_outstanding\_total")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 4, text \= str.tostring(syminfo.shares\_outstanding\_total))  
See also  
[syminfo.employees](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.employees)[syminfo.shares\_outstanding\_float](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.shares_outstanding_float)[syminfo.shares\_outstanding\_total](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.shares_outstanding_total)

### **syminfo.shares\_outstanding\_float**

The total number of shares outstanding a company has available, excluding any of its restricted shares.  
Type  
simple float  
Example  
//@version=6  
indicator("syminfo simple")  
//@variable A table containing information about a company's employees, shareholders, and shares.  
var result\_table \= table.new(position \= position.top\_right, columns \= 2, rows \= 5, border\_width \= 1\)  
if barstate.islastconfirmedhistory  
    // Add header cells  
    table.cell(table\_id \= result\_table, column \= 0, row \= 0, text \= "name")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 0, text \= "value")  
    // Add employee info cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 1, text \= "employees")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 1, text \= str.tostring(syminfo.employees))  
    // Add shareholder cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 2, text \= "shareholders")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 2, text \= str.tostring(syminfo.shareholders))  
    // Add float shares outstanding cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 3, text \= "shares\_outstanding\_float")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 3, text \= str.tostring(syminfo.shares\_outstanding\_float))  
    // Add total shares outstanding cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 4, text \= "shares\_outstanding\_total")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 4, text \= str.tostring(syminfo.shares\_outstanding\_total))  
See also  
[syminfo.employees](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.employees)[syminfo.shareholders](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.shareholders)[syminfo.shares\_outstanding\_total](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.shares_outstanding_total)

### **syminfo.shares\_outstanding\_total**

The total number of shares outstanding a company has available, including restricted shares held by insiders, major shareholders, and employees.  
Type  
simple int  
Example  
//@version=6  
indicator("syminfo simple")  
//@variable A table containing information about a company's employees, shareholders, and shares.  
var result\_table \= table.new(position \= position.top\_right, columns \= 2, rows \= 5, border\_width \= 1\)  
if barstate.islastconfirmedhistory  
    // Add header cells  
    table.cell(table\_id \= result\_table, column \= 0, row \= 0, text \= "name")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 0, text \= "value")  
    // Add employee info cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 1, text \= "employees")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 1, text \= str.tostring(syminfo.employees))  
    // Add shareholder cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 2, text \= "shareholders")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 2, text \= str.tostring(syminfo.shareholders))  
    // Add float shares outstanding cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 3, text \= "shares\_outstanding\_float")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 3, text \= str.tostring(syminfo.shares\_outstanding\_float))  
    // Add total shares outstanding cells.  
    table.cell(table\_id \= result\_table, column \= 0, row \= 4, text \= "shares\_outstanding\_total")  
    table.cell(table\_id \= result\_table, column \= 1, row \= 4, text \= str.tostring(syminfo.shares\_outstanding\_total))  
See also  
[syminfo.employees](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.employees)[syminfo.shareholders](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.shareholders)[syminfo.shares\_outstanding\_float](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.shares_outstanding_float)

### **syminfo.target\_price\_average**

The average of the last yearly price targets for the symbol predicted by analysts.  
Type  
series float  
Example  
//@version=6  
indicator("syminfo target\_price")  
if barstate.islastconfirmedhistory  
    //@variable The time value one year from the date of the last analyst recommendations.  
    int YTD \= syminfo.target\_price\_date \+ timeframe.in\_seconds("12M") \* 1000  
    //@variable A line connecting the current \`close\` to the highest yearly price estimate.  
    highLine \= line.new(time, close, YTD, syminfo.target\_price\_high, color \= color.green, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the lowest yearly price estimate.  
    lowLine \= line.new(time, close, YTD, syminfo.target\_price\_low, color \= color.red, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the median yearly price estimate.  
    medianLine \= line.new(time, close, YTD, syminfo.target\_price\_median, color \= color.gray, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the average yearly price estimate.  
    averageLine \= line.new(time, close, YTD, syminfo.target\_price\_average, color \= color.orange, xloc \= xloc.bar\_time)  
    // Fill the space between targets  
    linefill.new(lowLine, medianLine, color.new(color.red, 90))  
    linefill.new(medianLine, highLine, color.new(color.green, 90))  
    // Create a label displaying the total number of analyst estimates.  
    string estimatesText \= str.format("Number of estimates: {0}", syminfo.target\_price\_estimates)  
    label.new(bar\_index, close, estimatesText, textcolor \= color.white, size \= size.large)  
Remarks  
If analysts supply the targets when the market is closed, the variable can return [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) until the market opens.  
See also  
[syminfo.target\_price\_date](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_date)[syminfo.target\_price\_estimates](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_estimates)[syminfo.target\_price\_high](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_high)[syminfo.target\_price\_low](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_low)[syminfo.target\_price\_median](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_median)

### **syminfo.target\_price\_date**

The starting date of the last price target prediction for the current symbol.  
Type  
series int  
Example  
//@version=6  
indicator("syminfo target\_price")  
if barstate.islastconfirmedhistory  
    //@variable The time value one year from the date of the last analyst recommendations.  
    int YTD \= syminfo.target\_price\_date \+ timeframe.in\_seconds("12M") \* 1000  
    //@variable A line connecting the current \`close\` to the highest yearly price estimate.  
    highLine \= line.new(time, close, YTD, syminfo.target\_price\_high, color \= color.green, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the lowest yearly price estimate.  
    lowLine \= line.new(time, close, YTD, syminfo.target\_price\_low, color \= color.red, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the median yearly price estimate.  
    medianLine \= line.new(time, close, YTD, syminfo.target\_price\_median, color \= color.gray, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the average yearly price estimate.  
    averageLine \= line.new(time, close, YTD, syminfo.target\_price\_average, color \= color.orange, xloc \= xloc.bar\_time)  
    // Fill the space between targets  
    linefill.new(lowLine, medianLine, color.new(color.red, 90))  
    linefill.new(medianLine, highLine, color.new(color.green, 90))  
    // Create a label displaying the total number of analyst estimates.  
    string estimatesText \= str.format("Number of estimates: {0}", syminfo.target\_price\_estimates)  
    label.new(bar\_index, close, estimatesText, textcolor \= color.white, size \= size.large)  
Remarks  
If analysts supply the targets when the market is closed, the variable can return [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) until the market opens.  
See also  
[syminfo.target\_price\_average](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_average)[syminfo.target\_price\_estimates](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_estimates)[syminfo.target\_price\_high](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_high)[syminfo.target\_price\_low](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_low)[syminfo.target\_price\_median](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_median)

### **syminfo.target\_price\_estimates**

The latest total number of price target predictions for the current symbol.  
Type  
series float  
Example  
//@version=6  
indicator("syminfo target\_price")  
if barstate.islastconfirmedhistory  
    //@variable The time value one year from the date of the last analyst recommendations.  
    int YTD \= syminfo.target\_price\_date \+ timeframe.in\_seconds("12M") \* 1000  
    //@variable A line connecting the current \`close\` to the highest yearly price estimate.  
    highLine \= line.new(time, close, YTD, syminfo.target\_price\_high, color \= color.green, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the lowest yearly price estimate.  
    lowLine \= line.new(time, close, YTD, syminfo.target\_price\_low, color \= color.red, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the median yearly price estimate.  
    medianLine \= line.new(time, close, YTD, syminfo.target\_price\_median, color \= color.gray, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the average yearly price estimate.  
    averageLine \= line.new(time, close, YTD, syminfo.target\_price\_average, color \= color.orange, xloc \= xloc.bar\_time)  
    // Fill the space between targets  
    linefill.new(lowLine, medianLine, color.new(color.red, 90))  
    linefill.new(medianLine, highLine, color.new(color.green, 90))  
    // Create a label displaying the total number of analyst estimates.  
    string estimatesText \= str.format("Number of estimates: {0}", syminfo.target\_price\_estimates)  
    label.new(bar\_index, close, estimatesText, textcolor \= color.white, size \= size.large)  
Remarks  
If analysts supply the targets when the market is closed, the variable can return [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) until the market opens.  
See also  
[syminfo.target\_price\_average](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_average)[syminfo.target\_price\_date](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_date)[syminfo.target\_price\_high](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_high)[syminfo.target\_price\_low](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_low)[syminfo.target\_price\_median](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_median)

### **syminfo.target\_price\_high**

The last highest yearly price target for the symbol predicted by analysts.  
Type  
series float  
Example  
//@version=6  
indicator("syminfo target\_price")  
if barstate.islastconfirmedhistory  
    //@variable The time value one year from the date of the last analyst recommendations.  
    int YTD \= syminfo.target\_price\_date \+ timeframe.in\_seconds("12M") \* 1000  
    //@variable A line connecting the current \`close\` to the highest yearly price estimate.  
    highLine \= line.new(time, close, YTD, syminfo.target\_price\_high, color \= color.green, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the lowest yearly price estimate.  
    lowLine \= line.new(time, close, YTD, syminfo.target\_price\_low, color \= color.red, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the median yearly price estimate.  
    medianLine \= line.new(time, close, YTD, syminfo.target\_price\_median, color \= color.gray, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the average yearly price estimate.  
    averageLine \= line.new(time, close, YTD, syminfo.target\_price\_average, color \= color.orange, xloc \= xloc.bar\_time)  
    // Fill the space between targets  
    linefill.new(lowLine, medianLine, color.new(color.red, 90))  
    linefill.new(medianLine, highLine, color.new(color.green, 90))  
    // Create a label displaying the total number of analyst estimates.  
    string estimatesText \= str.format("Number of estimates: {0}", syminfo.target\_price\_estimates)  
    label.new(bar\_index, close, estimatesText, textcolor \= color.white, size \= size.large)  
Remarks  
If analysts supply the targets when the market is closed, the variable can return [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) until the market opens.  
See also  
[syminfo.target\_price\_average](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_average)[syminfo.target\_price\_date](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_date)[syminfo.target\_price\_estimates](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_estimates)[syminfo.target\_price\_low](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_low)[syminfo.target\_price\_median](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_median)

### **syminfo.target\_price\_low**

The last lowest yearly price target for the symbol predicted by analysts.  
Type  
series float  
Example  
//@version=6  
indicator("syminfo target\_price")  
if barstate.islastconfirmedhistory  
    //@variable The time value one year from the date of the last analyst recommendations.  
    int YTD \= syminfo.target\_price\_date \+ timeframe.in\_seconds("12M") \* 1000  
    //@variable A line connecting the current \`close\` to the highest yearly price estimate.  
    highLine \= line.new(time, close, YTD, syminfo.target\_price\_high, color \= color.green, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the lowest yearly price estimate.  
    lowLine \= line.new(time, close, YTD, syminfo.target\_price\_low, color \= color.red, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the median yearly price estimate.  
    medianLine \= line.new(time, close, YTD, syminfo.target\_price\_median, color \= color.gray, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the average yearly price estimate.  
    averageLine \= line.new(time, close, YTD, syminfo.target\_price\_average, color \= color.orange, xloc \= xloc.bar\_time)  
    // Fill the space between targets  
    linefill.new(lowLine, medianLine, color.new(color.red, 90))  
    linefill.new(medianLine, highLine, color.new(color.green, 90))  
    // Create a label displaying the total number of analyst estimates.  
    string estimatesText \= str.format("Number of estimates: {0}", syminfo.target\_price\_estimates)  
    label.new(bar\_index, close, estimatesText, textcolor \= color.white, size \= size.large)  
Remarks  
If analysts supply the targets when the market is closed, the variable can return [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) until the market opens.  
See also  
[syminfo.target\_price\_average](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_average)[syminfo.target\_price\_date](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_date)[syminfo.target\_price\_estimates](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_estimates)[syminfo.target\_price\_high](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_high)[syminfo.target\_price\_median](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_median)

### **syminfo.target\_price\_median**

The median of the last yearly price targets for the symbol predicted by analysts.  
Type  
series float  
Example  
//@version=6  
indicator("syminfo target\_price")  
if barstate.islastconfirmedhistory  
    //@variable The time value one year from the date of the last analyst recommendations.  
    int YTD \= syminfo.target\_price\_date \+ timeframe.in\_seconds("12M") \* 1000  
    //@variable A line connecting the current \`close\` to the highest yearly price estimate.  
    highLine \= line.new(time, close, YTD, syminfo.target\_price\_high, color \= color.green, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the lowest yearly price estimate.  
    lowLine \= line.new(time, close, YTD, syminfo.target\_price\_low, color \= color.red, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the median yearly price estimate.  
    medianLine \= line.new(time, close, YTD, syminfo.target\_price\_median, color \= color.gray, xloc \= xloc.bar\_time)  
    //@variable A line connecting the current \`close\` to the average yearly price estimate.  
    averageLine \= line.new(time, close, YTD, syminfo.target\_price\_average, color \= color.orange, xloc \= xloc.bar\_time)  
    // Fill the space between targets  
    linefill.new(lowLine, medianLine, color.new(color.red, 90))  
    linefill.new(medianLine, highLine, color.new(color.green, 90))  
    // Create a label displaying the total number of analyst estimates.  
    string estimatesText \= str.format("Number of estimates: {0}", syminfo.target\_price\_estimates)  
    label.new(bar\_index, close, estimatesText, textcolor \= color.white, size \= size.large)  
Remarks  
If analysts supply the targets when the market is closed, the variable can return [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) until the market opens.  
See also  
[syminfo.target\_price\_average](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_average)[syminfo.target\_price\_date](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_date)[syminfo.target\_price\_estimates](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_estimates)[syminfo.target\_price\_high](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_high)[syminfo.target\_price\_low](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.target_price_low)

### **syminfo.ticker**

Symbol name without exchange prefix, e.g. 'MSFT'.  
Type  
simple string  
See also  
[syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.tickerid)[timeframe.period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.period)[timeframe.multiplier](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.multiplier)[syminfo.root](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.root)

### **syminfo.tickerid**

A ticker identifier representing the chart's symbol or a requested symbol, depending on how the script uses it. The variable's value represents a requested dataset's ticker ID when used in the `expression` argument of a `request.*()` function call. Otherwise, it represents the chart's ticker ID. The value contains an exchange prefix and a symbol name, separated by a colon (e.g., "NASDAQ:AAPL"). It can also include information about data modifications such as dividend adjustment, non-standard chart type, currency conversion, etc.  
Type  
simple string  
Remarks  
Because the value of this variable does not always use a simple "prefix:ticker" format, it is a poor candidate for use in boolean comparisons or string manipulation functions. In those contexts, run the variable's result through [ticker.standard](https://www.tradingview.com/pine-script-reference/v6/#fun_ticker.standard) to purify it. This will remove any extraneous information and return a ticker ID consistently formatted using the "prefix:ticker" structure.  
To always access the script's main ticker ID, even within another context, use the [syminfo.main\_tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.main_tickerid) variable.  
See also  
[ticker.new](https://www.tradingview.com/pine-script-reference/v6/#fun_ticker.new)[syminfo.main\_tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.main_tickerid)[timeframe.main\_period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.main_period)[syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker)[timeframe.period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.period)[timeframe.multiplier](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.multiplier)[syminfo.root](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.root)

### **syminfo.timezone**

Timezone of the exchange of the chart main series. Possible values see in [timestamp](https://www.tradingview.com/pine-script-reference/v6/#fun_timestamp).  
Type  
simple string  
See also  
[timestamp](https://www.tradingview.com/pine-script-reference/v6/#fun_timestamp)

### **syminfo.type**

The type of market the symbol belongs to. The values are "stock", "fund", "dr", "right", "bond", "warrant", "structured", "index", "forex", "futures", "spread", "economic", "fundamental", "crypto", "spot", "swap", "option", "commodity".  
Type  
simple string  
See also  
[syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker)

### **syminfo.volumetype**

Volume type of the current symbol. Possible values are: "base" for base currency, "quote" for quote currency, "tick" for the number of transactions, and "n/a" when there is no volume or its type is not specified.  
Type  
simple string  
Remarks  
Only some data feed suppliers provide information qualifying volume. As a result, the variable will return a value on some symbols only, mostly in the crypto sector.  
See also  
[syminfo.type](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.type)

### **ta.accdist**

Accumulation/distribution index.  
Type  
series float

### **ta.iii**

Intraday Intensity Index.  
Type  
series float  
Example  
//@version=6  
indicator("Intraday Intensity Index")  
plot(ta.iii, color=color.yellow)

// the same on pine  
f\_iii() \=\>  
    (2 \* close \- high \- low) / ((high \- low) \* volume)

plot(f\_iii())

### **ta.nvi**

Negative Volume Index.  
Type  
series float  
Example  
//@version=6  
indicator("Negative Volume Index")

plot(ta.nvi, color=color.yellow)

// the same on pine  
f\_nvi() \=\>  
    float ta\_nvi \= 1.0  
    float prevNvi \= (nz(ta\_nvi\[1\], 0.0) \== 0.0) ? 1.0 : ta\_nvi\[1\]  
    if nz(close, 0.0) \== 0.0 or nz(close\[1\], 0.0) \== 0.0  
        ta\_nvi := prevNvi  
    else  
        ta\_nvi := (volume \< nz(volume\[1\], 0.0)) ? prevNvi \+ ((close \- close\[1\]) / close\[1\]) \* prevNvi : prevNvi  
    result \= ta\_nvi

plot(f\_nvi())

### **ta.obv**

On Balance Volume.  
Type  
series float  
Example  
//@version=6  
indicator("On Balance Volume")  
plot(ta.obv, color=color.yellow)

// the same on pine  
f\_obv() \=\>  
    ta.cum(math.sign(ta.change(close)) \* volume)

plot(f\_obv())

### **ta.pvi**

Positive Volume Index.  
Type  
series float  
Example  
//@version=6  
indicator("Positive Volume Index")

plot(ta.pvi, color=color.yellow)

// the same on pine  
f\_pvi() \=\>  
    float ta\_pvi \= 1.0  
    float prevPvi \= (nz(ta\_pvi\[1\], 0.0) \== 0.0) ? 1.0 : ta\_pvi\[1\]  
    if nz(close, 0.0) \== 0.0 or nz(close\[1\], 0.0) \== 0.0  
        ta\_pvi := prevPvi  
    else  
        ta\_pvi := (volume \> nz(volume\[1\], 0.0)) ? prevPvi \+ ((close \- close\[1\]) / close\[1\]) \* prevPvi : prevPvi  
    result \= ta\_pvi

plot(f\_pvi())

### **ta.pvt**

Price-Volume Trend.  
Type  
series float  
Example  
//@version=6  
indicator("Price-Volume Trend")  
plot(ta.pvt, color=color.yellow)

// the same on pine  
f\_pvt() \=\>  
    ta.cum((ta.change(close) / close\[1\]) \* volume)

plot(f\_pvt())

### **ta.tr**

True range, equivalent to `ta.tr(handle_na = false)`. It is calculated as `math.max(high - low, math.abs(high - close[1]), math.abs(low - close[1]))`.  
Type  
series float  
See also  
[ta.tr](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.tr)[ta.atr](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.atr)

### **ta.vwap**

Volume Weighted Average Price. It uses [hlc3](https://www.tradingview.com/pine-script-reference/v6/#var_hlc3) as its source series.  
Type  
series float  
See also  
[ta.vwap](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.vwap)

### **ta.wad**

Williams Accumulation/Distribution.  
Type  
series float  
Example  
//@version=6  
indicator("Williams Accumulation/Distribution")  
plot(ta.wad, color=color.yellow)

// the same on pine  
f\_wad() \=\>  
    trueHigh \= math.max(high, close\[1\])  
    trueLow \= math.min(low, close\[1\])  
    mom \= ta.change(close)  
    gain \= (mom \> 0\) ? close \- trueLow : (mom \< 0\) ? close \- trueHigh : 0  
    ta.cum(gain)

plot(f\_wad())

### **ta.wvad**

Williams Variable Accumulation/Distribution.  
Type  
series float  
Example  
//@version=6  
indicator("Williams Variable Accumulation/Distribution")  
plot(ta.wvad, color=color.yellow)

// the same on pine  
f\_wvad() \=\>  
    (close \- open) / (high \- low) \* volume

plot(f\_wvad())

### **table.all**

Returns an array filled with all the current tables drawn by the script.  
Type  
array\<table\>  
Example  
//@version=6  
indicator("table.all")  
//delete all tables  
table.new(position \= position.top\_right, columns \= 2, rows \= 1, bgcolor \= color.yellow, border\_width \= 1\)  
a\_allTables \= table.all  
if array.size(a\_allTables) \> 0  
    for i \= 0 to array.size(a\_allTables) \- 1  
        table.delete(array.get(a\_allTables, i))  
Remarks  
The array is read-only. Index zero of the array is the ID of the oldest object on the chart.  
See also  
[table.new](https://www.tradingview.com/pine-script-reference/v6/#fun_table.new)[line.all](https://www.tradingview.com/pine-script-reference/v6/#var_line.all)[label.all](https://www.tradingview.com/pine-script-reference/v6/#var_label.all)[box.all](https://www.tradingview.com/pine-script-reference/v6/#var_box.all)

### **time**

Current bar time in UNIX format. It is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970\.  
Type  
series int  
Remarks  
Note that this variable returns the timestamp based on the time of the bar's open. Because of that, for overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00) this variable can return time before the specified date of the trading day. For example, on EURUSD, `dayofmonth(time)` can be lower by 1 than the date of the trading day, because the bar for the current day actually opens one day prior.  
See also  
[time](https://www.tradingview.com/pine-script-reference/v6/#fun_time)[time\_close](https://www.tradingview.com/pine-script-reference/v6/#var_time_close)[timenow](https://www.tradingview.com/pine-script-reference/v6/#var_timenow)[year](https://www.tradingview.com/pine-script-reference/v6/#var_year)[month](https://www.tradingview.com/pine-script-reference/v6/#var_month)[weekofyear](https://www.tradingview.com/pine-script-reference/v6/#var_weekofyear)[dayofmonth](https://www.tradingview.com/pine-script-reference/v6/#var_dayofmonth)[dayofweek](https://www.tradingview.com/pine-script-reference/v6/#var_dayofweek)[hour](https://www.tradingview.com/pine-script-reference/v6/#var_hour)[minute](https://www.tradingview.com/pine-script-reference/v6/#var_minute)[second](https://www.tradingview.com/pine-script-reference/v6/#var_second)

### **time\_close**

The time of the current bar's close in UNIX format. It represents the number of milliseconds elapsed since 00:00:00 UTC, 1 January 1970\. On non-standard price-based chart types (Renko, Line break, Kagi, Point & Figure, and Range), this variable returns [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) on the chart's realtime bars.  
Type  
series int  
See also  
[time](https://www.tradingview.com/pine-script-reference/v6/#var_time)[timenow](https://www.tradingview.com/pine-script-reference/v6/#var_timenow)[year](https://www.tradingview.com/pine-script-reference/v6/#var_year)[month](https://www.tradingview.com/pine-script-reference/v6/#var_month)[weekofyear](https://www.tradingview.com/pine-script-reference/v6/#var_weekofyear)[dayofmonth](https://www.tradingview.com/pine-script-reference/v6/#var_dayofmonth)[dayofweek](https://www.tradingview.com/pine-script-reference/v6/#var_dayofweek)[hour](https://www.tradingview.com/pine-script-reference/v6/#var_hour)[minute](https://www.tradingview.com/pine-script-reference/v6/#var_minute)[second](https://www.tradingview.com/pine-script-reference/v6/#var_second)

### **time\_tradingday**

The beginning time of the trading day the current bar belongs to, in UNIX format (the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970).  
Type  
series int  
Remarks  
The variable is useful for overnight sessions, where the current day's session can start on the previous calendar day (e.g., on FXCM:EURUSD the Monday session will start on Sunday, 17:00 in the exchange timezone). Unlike `time`, which would return the timestamp for Sunday at 17:00 for the Monday daily bar, `time_tradingday` will return the timestamp for Monday, 00:00 UTC.  
When used on timeframes higher than 1D, `time_tradingday` returns the trading day of the last day inside the bar (e.g. on 1W, it will return the last trading day of the week).  
See also  
[time](https://www.tradingview.com/pine-script-reference/v6/#var_time)[time\_close](https://www.tradingview.com/pine-script-reference/v6/#var_time_close)

### **timeframe.isdaily**

Returns true if current resolution is a daily resolution, false otherwise.  
Type  
simple bool  
See also  
[timeframe.isdwm](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isdwm)[timeframe.isintraday](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isintraday)[timeframe.isminutes](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isminutes)[timeframe.isseconds](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isseconds)[timeframe.isticks](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isticks)[timeframe.isweekly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isweekly)[timeframe.ismonthly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.ismonthly)

### **timeframe.isdwm**

Returns true if current resolution is a daily or weekly or monthly resolution, false otherwise.  
Type  
simple bool  
See also  
[timeframe.isintraday](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isintraday)[timeframe.isminutes](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isminutes)[timeframe.isseconds](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isseconds)[timeframe.isticks](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isticks)[timeframe.isdaily](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isdaily)[timeframe.isweekly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isweekly)[timeframe.ismonthly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.ismonthly)

### **timeframe.isintraday**

Returns true if current resolution is an intraday (minutes or seconds) resolution, false otherwise.  
Type  
simple bool  
See also  
[timeframe.isminutes](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isminutes)[timeframe.isseconds](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isseconds)[timeframe.isticks](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isticks)[timeframe.isdwm](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isdwm)[timeframe.isdaily](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isdaily)[timeframe.isweekly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isweekly)[timeframe.ismonthly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.ismonthly)

### **timeframe.isminutes**

Returns true if current resolution is a minutes resolution, false otherwise.  
Type  
simple bool  
See also  
[timeframe.isdwm](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isdwm)[timeframe.isintraday](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isintraday)[timeframe.isseconds](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isseconds)[timeframe.isticks](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isticks)[timeframe.isdaily](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isdaily)[timeframe.isweekly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isweekly)[timeframe.ismonthly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.ismonthly)

### **timeframe.ismonthly**

Returns true if current resolution is a monthly resolution, false otherwise.  
Type  
simple bool  
See also  
[timeframe.isdwm](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isdwm)[timeframe.isintraday](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isintraday)[timeframe.isminutes](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isminutes)[timeframe.isseconds](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isseconds)[timeframe.isticks](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isticks)[timeframe.isdaily](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isdaily)[timeframe.isweekly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isweekly)

### **timeframe.isseconds**

Returns true if current resolution is a seconds resolution, false otherwise.  
Type  
simple bool  
See also  
[timeframe.isdwm](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isdwm)[timeframe.isintraday](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isintraday)[timeframe.isminutes](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isminutes)[timeframe.isticks](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isticks)[timeframe.isdaily](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isdaily)[timeframe.isweekly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isweekly)[timeframe.ismonthly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.ismonthly)

### **timeframe.isticks**

Returns true if current resolution is a ticks resolution, false otherwise.  
Type  
simple bool  
See also  
[timeframe.isdwm](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isdwm)[timeframe.isintraday](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isintraday)[timeframe.isminutes](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isminutes)[timeframe.isseconds](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isseconds)[timeframe.isdaily](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isdaily)[timeframe.isweekly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isweekly)[timeframe.ismonthly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.ismonthly)

### **timeframe.isweekly**

Returns true if current resolution is a weekly resolution, false otherwise.  
Type  
simple bool  
See also  
[timeframe.isdwm](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isdwm)[timeframe.isintraday](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isintraday)[timeframe.isminutes](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isminutes)[timeframe.isseconds](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isseconds)[timeframe.isticks](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isticks)[timeframe.isdaily](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.isdaily)[timeframe.ismonthly](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.ismonthly)

### **timeframe.main\_period**

A string representation of the script's main timeframe. If the script is an [indicator](https://www.tradingview.com/pine-script-reference/v6/#fun_indicator) that specifies a `timeframe` value in its declaration statement, this variable holds that value. Otherwise, its value represents the chart's timeframe. Unlike [timeframe.period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.period), this variable's value does not change when used in the `expression` argument of a `request.*()` function call.  
The string's format is "\<quantity\>\[\<unit\>\]", where \<unit\> is "T" for ticks, "S" for seconds, "D" for days, "W" for weeks, and "M" for months, but is absent for minutes. No \<unit\> exists for hours: hourly timeframes are expressed in minutes.  
The variable's value is: "10S" for 10 seconds, "30" for 30 minutes, "240" for four hours, "1D" for one day, "2W" for two weeks, and "3M" for one quarter.  
Type  
simple string  
See also  
[timeframe.period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.period)[syminfo.main\_tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.main_tickerid)[syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker)[syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.tickerid)[timeframe.multiplier](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.multiplier)

### **timeframe.multiplier**

Multiplier of resolution, e.g. '60' \- 60, 'D' \- 1, '5D' \- 5, '12M' \- 12\.  
Type  
simple int  
See also  
[syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker)[syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.tickerid)[timeframe.period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.period)

### **timeframe.period**

A string representation of the script's main timeframe or a requested timeframe, depending on how the script uses it. The variable's value represents the timeframe of a requested dataset when used in the `expression` argument of a `request.*()` function call. Otherwise, its value represents the script's main timeframe ([timeframe.main\_period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.main_period)), which equals either the `timeframe` argument of the [indicator](https://www.tradingview.com/pine-script-reference/v6/#fun_indicator) declaration statement or the chart's timeframe.  
The string's format is "\<quantity\>\[\<unit\>\]", where \<unit\> is "T" for ticks, "S" for seconds, "D" for days, "W" for weeks, and "M" for months, but is absent for minutes. No \<unit\> exists for hours: hourly timeframes are expressed in minutes.  
The variable's value is: "10S" for 10 seconds, "30" for 30 minutes, "240" for four hours, "1D" for one day, "2W" for two weeks, and "3M" for one quarter.  
Type  
simple string  
Remarks  
To always access the script's main timeframe, even within another context, use the [timeframe.main\_period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.main_period) variable.  
See also  
[timeframe.main\_period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.main_period)[syminfo.main\_tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.main_tickerid)[syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker)[syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.tickerid)[timeframe.multiplier](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.multiplier)

### **timenow**

Current time in UNIX format. It is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970\.  
Type  
series int  
Remarks  
Please note that using this variable/function can cause [indicator repainting](https://www.tradingview.com/pine-script-docs/concepts/repainting/).  
See also  
[timestamp](https://www.tradingview.com/pine-script-reference/v6/#fun_timestamp)[time](https://www.tradingview.com/pine-script-reference/v6/#var_time)[time\_close](https://www.tradingview.com/pine-script-reference/v6/#var_time_close)[year](https://www.tradingview.com/pine-script-reference/v6/#var_year)[month](https://www.tradingview.com/pine-script-reference/v6/#var_month)[weekofyear](https://www.tradingview.com/pine-script-reference/v6/#var_weekofyear)[dayofmonth](https://www.tradingview.com/pine-script-reference/v6/#var_dayofmonth)[dayofweek](https://www.tradingview.com/pine-script-reference/v6/#var_dayofweek)[hour](https://www.tradingview.com/pine-script-reference/v6/#var_hour)[minute](https://www.tradingview.com/pine-script-reference/v6/#var_minute)[second](https://www.tradingview.com/pine-script-reference/v6/#var_second)

### **volume**

Current bar volume.  
Type  
series float  
Remarks  
Previous values may be accessed with square brackets operator \[\], e.g. volume\[1\], volume\[2\].  
See also  
[open](https://www.tradingview.com/pine-script-reference/v6/#var_open)[high](https://www.tradingview.com/pine-script-reference/v6/#var_high)[low](https://www.tradingview.com/pine-script-reference/v6/#var_low)[close](https://www.tradingview.com/pine-script-reference/v6/#var_close)[time](https://www.tradingview.com/pine-script-reference/v6/#fun_time)[hl2](https://www.tradingview.com/pine-script-reference/v6/#var_hl2)[hlc3](https://www.tradingview.com/pine-script-reference/v6/#var_hlc3)[hlcc4](https://www.tradingview.com/pine-script-reference/v6/#var_hlcc4)[ohlc4](https://www.tradingview.com/pine-script-reference/v6/#var_ohlc4)[ask](https://www.tradingview.com/pine-script-reference/v6/#var_ask)[bid](https://www.tradingview.com/pine-script-reference/v6/#var_bid)

### **weekofyear**

Week number of current bar time in exchange timezone.  
Type  
series int  
Remarks  
Note that this variable returns the week based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00) this value can be lower by 1 than the week of the trading day.  
See also  
[weekofyear](https://www.tradingview.com/pine-script-reference/v6/#fun_weekofyear)[time](https://www.tradingview.com/pine-script-reference/v6/#var_time)[year](https://www.tradingview.com/pine-script-reference/v6/#var_year)[month](https://www.tradingview.com/pine-script-reference/v6/#var_month)[dayofmonth](https://www.tradingview.com/pine-script-reference/v6/#var_dayofmonth)[dayofweek](https://www.tradingview.com/pine-script-reference/v6/#var_dayofweek)[hour](https://www.tradingview.com/pine-script-reference/v6/#var_hour)[minute](https://www.tradingview.com/pine-script-reference/v6/#var_minute)[second](https://www.tradingview.com/pine-script-reference/v6/#var_second)

### **year**

Current bar year in exchange timezone.  
Type  
series int  
Remarks  
Note that this variable returns the year based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00) this value can be lower by 1 than the year of the trading day.  
See also  
[year](https://www.tradingview.com/pine-script-reference/v6/#fun_year)[time](https://www.tradingview.com/pine-script-reference/v6/#var_time)[month](https://www.tradingview.com/pine-script-reference/v6/#var_month)[weekofyear](https://www.tradingview.com/pine-script-reference/v6/#var_weekofyear)[dayofmonth](https://www.tradingview.com/pine-script-reference/v6/#var_dayofmonth)[dayofweek](https://www.tradingview.com/pine-script-reference/v6/#var_dayofweek)[hour](https://www.tradingview.com/pine-script-reference/v6/#var_hour)[minute](https://www.tradingview.com/pine-script-reference/v6/#var_minute)[second](https://www.tradingview.com/pine-script-reference/v6/#var_second)  
