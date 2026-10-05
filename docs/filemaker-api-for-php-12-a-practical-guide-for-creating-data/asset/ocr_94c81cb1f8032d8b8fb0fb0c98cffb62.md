Add the chart data that we retrieved from the database above.

Define the chart scaling using the min and max values that we defined above. This may seem redundant to the Y axis range below. However, this chart scaling will prevent Google from cutting off any values over 100.

Define the chart X axis labels that we retrieved from the database above. You cannot rotate the labels. Therefore, you may have to adjust the chart size and spacing/or use a horizontal bar chart to make sure they don't overlap.

Define the Y axis labels using the min and max values that we defined above. The labels are numeric by default and are evenly spaced.

```
$chxr='chrxr=1,' . $min . '.' . $max . '&';
```

Define the data value markers. I placed them on the top of the bars. You can define the chart color, which data index you want to use, points to draw, and the size of the labels.

```
$chm='cht=N,000000,0,-1,11' . '&';
```

Define the width and spacing. It is important to auto space the bars so they don't get clipped if the chart is smaller than the number of bars being displayed.

```
$chbh='chbb=25,5' . '&';
```

Create a random ID number for the chart. This isn't required, but it is highly recommended. It will force the Google Chart server to refresh the chart each time it is requested.

```
$chid='chid=' . md5(uniqid(rand(),true)) . '&';
```

# Optional Elements

The following chart elements are optional. The nice thing with the way I set up the chart is that all the elements are present for you even though they may not be used. You just need to decide if you want to use or not including them in the image source. The first is the title content and formatting. I actually suggest that this should be a required element. The chart won't work if you don't include it. The title requires words to be separated with a '|'. If you need an additional line you can use the pipe '|' character. Colors are specified through the API in hexadecimal format.

```
$schtt='cht=Sales+By-Region' . '| . date(m/d/Y)' . '&';
```

```
$chs='chs=FF0000,12,c' . '&';
```

You can display a legend in any location in the chart. I might suggest that a legend might not be very useful if the X axis labels overlap over each one.

```
$cdl='chdl=' . $labels . '&';
```

```
$chldp='chldp=1' .';
```

You can define the color of the bars. By default you'll receive an orange color. You can specify a single color, a gradient, or custom colors for each bar. I might suggest that the default colors are best because it requires less code and doesn't use any of the 2K character limit. After that, a gradient of complementary colors is always nice. I can't imagine trying to dynamically create custom colors for an unknown number of bars. That would be a messy function.

```
$chco='chco=' . '0000FF' . '&';
```