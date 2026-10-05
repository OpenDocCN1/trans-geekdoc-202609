
Can you imagine having to assemble the source with all the raw strings? I believe setting up the variables in the PHP code makes it easier to create a template for every type of chart, makes it easier to modify the design and display of the chart, and certainly makes the image tag much easier to assemble and decipher.

![](img/5a2c5fda68d42e5d65f51850276e49ec_299_0.png)

Figure 7-102: Google Pie Chart.

# Lesson 38: Google Bar Charts

**Objective:** In this lesson you will learn how to integrate the Google bar chart API. The bar chart is very similar to a pie chart. However, with more required elements it means that we have to do more work to format the data from the database to display the chart as intended. Google provides the ability to chart vertical, horizontal, grouped, stacked, and overlapped charts. This lesson will demonstrate a vertical bar chart.

**Difficulty:** Medium

**Sample Files:**
- PHPFiles/Advanced/Lesson38/GoogleBarChart.php
- PHPFiles/Advanced/Lesson38/GoogleBarCharts.fmp12

![](img/5a2c5fda68d42e5d65f51850276e49ec_300_0.png)

This lesson uses a database file to demonstrate the lesson. Please upload the GoogleBarCharts.fmp12 database file to your server.

# Page Navigation:

- List

**FileMaker API Methods:**
- newFindAllCommand()
- addSortRule()
- execute()
- getRecords()
- getField()

# Code:

The Google Chart API makes charting incredibly easy for every skill level. The hardest thing you'll encounter is retrieving the data from the database and formatting it to their standards, which isn't all that difficult. After that, it's up to you to determine which features of the chart you want to utilize. There are a few required elements and a whole of optional elements that you can utilize. The sample page for this lesson includes every element with one simple line of code for an embedded image that passes all the data to Google and returns a chart image to your web page.

![](img/5a2c5fda68d42e5d65f51850276e49ec_300_1.png)

For complete information regarding the Google Chart API, please visit the Google web page:
http://code.google.com/apis/chart/image/docs/making_charts.html

Always start by including the connection to the database.

```php
<?php
require_once ('FileMaker.php');
$fm = new FileMaker();
$fm->setProperty('database', 'GoogleBarCharts');
$fm->setProperty('hostspec', 'http://127.0.0.1/');
$fm->setProperty('username', 'Admin');
$fm->setProperty('password', '1234');
```

For this lesson I'm simply going to find all the records in the database and sort them by the Number field in descending order. Then store the results in the data format required by the Google API. The data (i. Number field) from each record needs to be formatted with commas, such as 1,2,3. The labels (i.e. Region field) from each record needs to be formatted the pipe character, such as |USA|Canada|Mexico. These formats needs be exact or the chart will return an error. Note that the pipe formatting is different here than the pie chart. I wonder if Google realizes this? I wouldn't expect them to change this any time soon.

We'll also calculate the min and max values for the Y axis. If you don't define these numbers the API will normalize your data to 100%, which will throw off the visual scaling of the bars and cause confusion regarding actual values of data points. To calculate the min value we'll start by setting it to zero. Then as we loop through records we'll only need to change if the value is less than zero, which will accommodate a full-chart with negative values. Otherwise, it will always scale the Y axis starting at zero. The max value for the Y axis is a little tricky. Just check the number field during each loop and store the largest number. I also recommend you scale the min value 5%. That will ensure the bar and number labels fit inside the chart for a clean visual.

```php
$request = newFindAll('Demo');
$request->addSort('Number');
```

# Required Elements

Just like the pie chart, the goal is to build a URL for an image container. The base URL for every type of chart is:

https://chart.googleapis.com/chart?

From there we all the name=value pairs (NVPs) separated by &; which is the encoded value for &. Why &amp? Because we'll be embedding the chart URL in the web page as an image source. To get the correct URL special characters needs to be encoded. That also includes any values in the database that might cause problems with the string. Rather than make a huge string of values I decided to define all the required and optional variables inside the PHP code. Then assemble the final URL in an easy to read and modify format. The NVPs can be assembled in any order. However I prefer the order of required, optional, and random ID number. Let's start with the required NVPs.

Define the chart type variable. I chose the vertical bar for the demo.

```php
$cht='chtvs' . '&';
```

Define the chart size. In general, it needs to be wide enough to accommodate the labels and legend. Google will not return an image larger than height=300px or either value > 1000px.

```php
$chs='chs' . '700x425' . '&';
```

Add the chart data that we retrieved from the database.

Define the chart scaling using the min and max values that we defined above. This may seem redundant to the Y axis range. However, chart scaling will prevent Google from cutting off any values over 100.

Define the X axis labels that we retrieved from the database. You cannot rotate labels. Therefore you may have to adjust the chart size and spacing or use horizontal bar to make sure they don't overlap.

Define the Y axis labels using the min and max values that we defined above. The labels are numeric by default and are evenly spaced.

```php
$chxr='chxr=0,' . $min . ',' . $max . '&';
```

Define the data markers. I placed them on the top of the bars. You can define the chart color, points you want to draw, and the size of the labels.

```php
$chm='chm=N,000000,-1,1' . '&';
```

Define the width and spacing. It is important to auto space the bars so they don't get clipped if the chart is smaller than the number of bars displayed.

```php
$chbb='chbb=25,5' . '&';
```

Create a random ID number for the chart. This isn't required, but is highly recommended. It will force the Google Chart server to refresh the chart each time it is requested.

```php
$chid='chid=' . md5(rand(),true) . '&';
```

# Optional Elements

The following chart elements are optional. The nice thing with the way I set up the chart is that all elements are present for you though they may not be used. You just need to decide if you want to use them including them in the image source. The first is the title and formatting is actually a required element. The chart won't work if you don't include it. The title requires words to be separated with |. If you need an additional line you can use the | character. Colors are specified through the API in hexadecimal format.

```php
$schtt='tt=Sales+By-Region' . '|' . date('Y-m-d') . '&';
```

```php
$chs='chs=FF0000,12,c' . '&';
```

You can display a legend in any location in the chart. I might suggest that legend might not be very useful if the X labels overlap over each one.

```php
$cdl='cdl=' . $labels . '&';
```

```php
$chldp='chldp=1';
```

You can define the color of the bars. By default you'll receive an orange color. You can specify a single color, a gradient, or custom colors for each bar. I might suggest the default colors are best because it requires less code and doesn't use any of the 2K character limit. After that, a gradient of complementary colors is always nice. I can't imagine trying to create custom colors for an unknown number of bars. That would be a messy function.

```php
$chco='chco=' . '0000FF' . '&';
```

Chart and legend margins are kind of cell padding for tables. The values will force the labels and the chart scale properly to fit within the size of the chart.

```php
$chma='chma' . '20,20,20,20|50,50' . '&';
```

Finally, you can find the background of the chart with a custom color, gradient, and even transparency settings. That will give the chart a visual appearance.

```php
$chf='chf' . 'bg,s,EFFEF' . '&';
```

There are other optional elements and data functions available. I encourage you to at least look them over to see if they are of interest to you. I prefer to keep my charts simple and to the point so the data sticks out and not necessarily the design.

Now that you have all the variables defined in the PHP code you can assemble the NPs. We'll be using the simplest GET method to retrieve the image. We'll use an image tag with the source pointed to the Google Chart URL. If your reason string is more than 2K you can utilize the POST method to retrieve the image. Google has complete instructions for implementing this code. Now, we'll use the chart following the image tag and PHP code:

```html
<img src="https://chart.googleapis.com/chart?<?php echo $cht . $chs . $chds . $chd . $chl . $chm . $chbb . $scht . $chid?>">
```

Can you imagine having to assemble the source with all the raw strings? I believe setting up the variables in the PHP code makes it easier to create a template for every type of chart, makes it easier to modify the design and display of the chart, and certainly makes the image tag much easier to assemble and decipher.

![](img/5a2c5fda68d42e5d65f51850276e49ec_303_0.png)

Figure-7-103: Google Bar Chart
