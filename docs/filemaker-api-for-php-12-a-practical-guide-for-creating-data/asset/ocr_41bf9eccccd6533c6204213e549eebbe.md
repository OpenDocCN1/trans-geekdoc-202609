Define the chart scaling from 0 to the $sum of the data we defined above.

$chds= 'chds=0,' . $sum '&';

Add the chart labels that we retrieved from the database above.

$chl= 'ch1' . $labels '&';

Create a random ID number for the chart. This isn't really required, but it is highly recommended. It will force the Google Chart server to refresh the chart each time it is requested.

$chid= 'chid' . md5(uniqid(rand(), true)) . '&';

# Optional Elements

The following chart elements are optional. The nice thing with the way I set up the code for you is that all the elements are present even they may not be utilized. You just need to decide if you want to use them or by including them in the image source. The first is the title content and formatting. I might actually suggest that this should be a required element

```
$chtt= 'chtt' . ' Sales-By-Region ' . . date('m/d/Y') . '&';
$chs= 'chs' . '#FF0000,12,c' . '&';
```

You can display a legend in any location in the chart. I might suggest that a legend isn't very useful for a pie chart. It is a feature that is available to every chart.

```
$chdl= 'chdl' . $labels '&';
$chdlp= 'chdlp' . 'l';
```

You can define the color of the slices. By default you'll receive an orange gradient. You can specify a single color, a gradient, or custom colors for each slice. I might suggest that the default colors are best because it requires less code and doesn't waste you the 2K character limit. After that, a gradient of complementary colors is always nice. I can't imagine trying to dynamically create custom colors for an unknown number of slices. This could be a messy function.

```
$chco= 'chco' . '0000FF' . '&';
```

```
$chma= 'chma' . '20,20,20,20|50,50' . '&';
```

Chart and legend margins are like cell padding for tables. The values will force the labels and the chart to scale properly fit within the size of the chart

```
$chcf= 'chcf' . 'bg,EFEFEFE' . '&';
?
```

Finally, you can fill the background of the chart with a custom color, and even transparency settings. That will give the chart custom visual appearance.

There are other optional elements and data functions available. I encourage you to at least look them over if they are of any interest to you. I prefer to keep my charts simple and to the point so the data stands out and not necessarily the design de.

Now that you have all the variables defined in the PHP code you can assemble the NVPs We'll be using the simplest GET method to retrieve the image. We'll use an image tag with the source pointed to the Google Chart URL. If some reason your string is more than 2K you can utilize the POST method to retrieve the image. Google has instructions for implementing this code. Now we will display the chart using the following image tag and PHP code:

```
<img src="https://chart.googleapis.com/chart?<?php echo $chft $chs $chcd $chds
$chl $chtt $chid;?"/>
```

291 * With Neolithic