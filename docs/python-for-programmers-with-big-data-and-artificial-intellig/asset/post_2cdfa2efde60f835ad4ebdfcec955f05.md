
data. For example, in New York City, the monthly average high temperature varies significantly based on the seasons (winter, spring, summer or fall).

- Time series forecasting, which uses past data to predict the future.

We'll perform time series forecasting in this section.

## Simple Linear Regression

Using a technique called *simple linear regression*, we'll make predictions by finding a linear relationship between the months (January of each year) and New York City's average January high temperatures. Given a collection of values representing an **independent variable** (the month/year combination) and a **dependent variable** (the average high temperature for that month/year), simple linear regression describes the relationship between these variables with a straight line, known as the *regression line*.

## Linear Relationships

To understand the general concept of a linear relationship, consider Fahrenheit and Celsius temperatures. Given a Fahrenheit temperature, we can calculate the corresponding Celsius temperature using the following formula:

```
c = 5 / 9 * (f - 32)
```

In this formula, f (the Fahrenheit temperature) is the *independent variable*, and c (the Celsius temperature) is the *dependent variable*—each value of c *depends on* the value of f used in the calculation.

Plotting Fahrenheit temperatures and their corresponding Celsius temperatures produces a straight line. To show this, let's first create a `lambda` for the preceding formula and use it to calculate the Celsius equivalents of the Fahrenheit temperatures 0–100 in 10-degree increments. We store each Fahrenheit/Celsius pair as a tuple in `temps`:

Click here to view code image

```
In [1]: c = lambda f: 5 / 9 * (f - 32)

In [2]: temps = [(f, c(f)) for f in range(0, 101, 10)]
```

Next, let's place the data in a `DataFrame`, then use its **plot method** to display the linear relationship between the Fahrenheit and Celsius temperatures. The `plot` method's `style` keyword argument controls the data's appearance. The period in the string '.-' indicates that each point should appear as a dot, and the dash indicates that lines should connect the dots. We manually set the y-axis label to 'Celsius' because the `plot` method shows 'Celsius' only in the graph's upper-left corner legend, by default.

Click here to view code image

```
In [3]: import pandas as pd

In [4]: temps_df = pd.DataFrame(temps, columns=['Fahrenheit', 'Celsius'])

In [5]: axes = temps_df.plot(x='Fahrenheit', y='Celsius', style='.-')

In [6]: y_label = axes.set_ylabel('Celsius')
```

![](img/34b7fc2f1ee27beb73bca14927d42340_447_0.png)

## Components of the Simple Linear Regression Equation

The points along any straight line (in two dimensions) like those shown in the preceding graph can be calculated with the equation:

```
y = mx + b
```

where

- m is the line’s slope,
- b is the line’s intercept with the y-axis (at x = 0),
- x is the independent variable (the date in this example), and
- y is the dependent variable (the temperature in this example).

In simple linear regression, y is the predicted value for a given x.

## Function linregress from the SciPy's stats Module

Simple linear regression determines the slope (m) and intercept (b) of a straight line that best fits your data. Consider the following diagram, which shows a few of the time-series data points we'll process in this section and a corresponding regression line. We added vertical lines to indicate each data point's distance from the regression line:

![](img/34b7fc2f1ee27beb73bca14927d42340_448_0.png)

The simple linear regression algorithm iteratively adjusts the slope and intercept and, for each adjustment, calculates the square of each point's distance from the line. The “best fit” occurs when the slope and intercept values minimize the sum of those squared distances. This is known as an **ordinary least squares** calculation.

0 https://en.wikipedia.org/wiki/Ordinary_least_squares.

The **SciPy (Scientific Python) library** is widely used for engineering, science and math in Python. This library's *linregress* function (from the **scipy.stats module**) performs simple linear regression for you. After calling *linregress*, you'll plug the resulting slope and intercept into the y = mx + b equation to make predictions.

## Pandas

In the three previous Intro to Data Science sections, you used pandas to work with data. You'll continue using pandas throughout the rest of the book. In this example, we'll load the data for New York City's 1895–2018 average January high temperatures from a CSV file into a **DataFrame**. We'll then format the data for use in this example.

## Seaborn Visualization

We'll use Seaborn to plot the DataFrame's data with a regression line that shows the average high-temperature trend over the period 1895–2018.

## Getting Weather Data from NOAA

Let's get the data for our study. The National Oceanic and Atmospheric Administration (NOAA) 1 offers lots of public historical data including time series for average high temperatures in specific cities over various time intervals.

1 http://www.noaa.gov.

We obtained the January average high temperatures for New York City from 1895 through 2018 from NOAA's “Climate at a Glance” time series at:

```
https://www.ncdc.noaa.gov/cag/
```

On that web page, you can select temperature, precipitation and other data for the entire U.S., regions within the U.S., states, cities and more. Once you've set the area and time frame, click Plot to display a diagram and view a table of the selected data. At the top of that table are links for downloading the data in several formats including CSV, which we discussed in the “Files and Exceptions” chapter. NOAA's maximum date range available at the time of this writing was 1895–2018. For your convenience, we provided the data in the ch10 examples folder in the file ave_hi_nyc_jan_1895-2018.csv. If you download the data on your own, delete the rows above the line containing "Date,Value,Anomaly".

This data contains three columns per observation:

- Date—A value of the form ' YYYYMM' (such as ' 201801 '). MM is always 01 because we downloaded data for only January of each year.

- Value—A floating-point Fahrenheit temperature.

- Anomaly—The difference between the value for the given date and average values for all dates. We do not use the Anomaly value in this example, so we'll ignore it.

## Loading the Average High Temperatures into a DataFrame

Let's load and display the New York City data from ave_hi_nyc_jan_1895-2018.csv:

![](img/34b7fc2f1ee27beb73bca14927d42340_449_0.png)

```
In [7]: nyc = pd.read_csv('ave_hi_nyc_jan_1895-2018.csv')
```

We can look at the DataFrame's head and tail to get a sense of the data:

![](img/34b7fc2f1ee27beb73bca14927d42340_449_1.png)

```
In [8]: nyc.head()
Out[8]:
     Date  Value  Anomaly
0  189501   34.2    -3.2
1  189601   34.7    -2.7
2  189701   35.5    -1.9
3  189801   39.6     2.2
4  189901   36.4    -1.0

In [9]: nyc.tail()
Out[9]:
      Date  Value  Anomaly
119  201401   35.5    -1.9
120  201501   36.1    -1.3
121  201601   40.8     3.4
122  201701   42.8     5.4
123  201801   38.7     1.3
```

## Cleaning the Data

We'll soon use Seaborn to graph the `Date`-`Value` pairs and a regression line. When plotting data from a `DataFrame`, Seaborn labels a graph's axes using the `DataFrame`'s column names. For readability, let's rename the 'Value' column as 'Temperature':

Click here to view code image

```
In [10]: nyc.columns = ['Date', 'Temperature', 'Anomaly']

In [11]: nyc.head(3)
Out[11]:
     Date  Temperature  Anomaly
0  189501          34.2     -3.2
1  189601          34.7     -2.7
2  189701          35.5     -1.9
```

Seaborn labels the tick marks on the x-axis with `Date` values. Since this example processes only January temperatures, the x-axis labels will be more readable if they do not contain `01` (for January), we'll remove it from each `Date`. First, let's check the column's type:

```
In [12]: nyc.Date.dtype
Out[12]: dtype('int64')
```

The values are integers, so we can divide by 100 to truncate the last two digits. Recall that each column in a `DataFrame` is a `Series`. Calling `Series` method `floordiv` performs `integer division` on every element of the `Series`:

Click here to view code image

```
In [13]: nyc.Date = nyc.Date.floordiv(100)

In [14]: nyc.head(3)
```
