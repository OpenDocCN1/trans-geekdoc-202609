
The first appropriate step is to assess this dataset by means of a simple statistical analysis. In this analysis, we are trying to describe the properties of the data. Here is a list of such properties.<sup>45</sup> The formulas/commands for these properties in Excel, Python, and R are shown in the companion table.

- Range: shows the spread of data.
- Min/max values: lists the smallest and largest value.
- Mean: the average of values and is calculated as \(\mu = \frac{1}{n} \sum_{i=1}^{n} x_i\)
- Variance: <sup>46</sup> measures the spread of data and is calculated as \(\sigma^2 = \frac{1}{n} \sum_{i=1}^{n} (x_i - \mu)^2\)
- Standard deviation: <sup>47</sup> measures the dispersion of a dataset relative to its mean and is calculated as \(\sigma = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (x_i - \mu)^2}\)
- Median: identifies the middle number of the data by ordering all data points.<sup>48</sup>
- Mode: the most common data value.
- Skewness: <sup>49</sup> describes the degree of asymmetry and is calculated as \(\mu_3 = \frac{\sum_{i=1}^{n} (x_i - \mu)^3}{(n)\sigma^3}\)
- Kurtosis: describes the tailedness<sup>50</sup> of the data and is calculated as \(\mu_4 = \frac{\sum_{i=1}^{n} (x_i - \mu)^4}{(n)\sigma^4}\)
- Percentiles: values indicating the percent of a distribution that is equal to or below it.<sup>51</sup>

Companion table for formulas and commands.

| Property | Excel | Python | R |
| :--- | :--- | :--- | :--- |
| Range | =MAX(Cells)-MIN(Cells) | – | range() |
| Min | =MIN(Cells) | min() | min() |
| Max | =MAX(Cells) | max() | max() |
| Mean | =AVERAGE(Cells) | `from statistics import mean` | mean() |
| Variance | =VAR(Cells) or =VARP(Cells) | `from statistics import variance` | var() |
| Standard deviation | =STDEV.P(Cells) or =STDEV.S(Cells) | `from statistics import stdev` | sd() |
| Median | =MEDIAN(Cells) | `from statistics import median` | median() |
| Mode | =MODE(Cells) | `from statistics import mode` | – |
| Skewness | =SKEW(Cells) | `from scipy.stats import skew` | skewness() |
| Kurtosis | =KURT(Cells) | `from scipy.stats import kurtosis` | kurtosis() |

45 Side note, you might have seen some of the following formulas using *n-1* as opposed to *n* as the divisor. This goes back to a more in-depth discussion on unbiased estimators – a talk for a different day. I advise you to review [23].
46 Tells us how data points differ from the mean. This is also referred to as the second standardized moment.
47 Tells us, *on average*, how far each score lies from the mean.
48 In the event that there are two middle numbers, the median would be the mean of those two numbers.
49 Skewness >1.0 or < -1.0 indicates a high skewedness. A value between 0.5 and 1 or -0.5 and -1.0 indicates moderate skewedness. A value between -0.5 and 0.5 indicates light skewedness or fairly symmetrical. Skewness is also referred to as the third standardized moment.
50 If the data is heavily or lightly tailed. The kurtosis for a normal distribution is 3 (the distribution for a kurtosis greater than +1.0 describes the peakiness while for –1.0 indicates flatness). In other words, this property measures the deviation from the peak in a Gaussian distribution due to outliers. Kurtosis is also referred to as the fourth standardized moment.
51 For example, 25<sup>th</sup>, 50<sup>th</sup>, and 75<sup>th</sup> percentile (interquartile range (IQR)).

| Property | Diameter (mm) | Tube thickness (mm) | Effective length (mm) | Yield strength (MPa) | Compressive strength of concrete (MPa) | Axial capacity (kN) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Min | 44.45 | 0.52 | 152.35 | 178.28 | 9.17 | 45.20 |
| Max | 1020.00 | 16.54 | 5560.00 | 853.00 | 193.30 | 46,000.00 |
| Mean | 158.52 | 4.31 | 1060.07 | 336.53 | 50.21 | 2349.58 |
| Standard deviation | 105.42 | 2.45 | 1005.28 | 90.89 | 31.57 | 4042.29 |
| Median | 127.30 | 4.00 | 662.00 | 325.00 | 41.00 | 1244.60 |
| Skew | 3.71 | 1.59 | 1.98 | 2.19 | 2.07 | 5.40 |
| Kurtosis | 20.46 | 3.69 | 3.84 | 8.47 | 5.17 | 38.63 |

Allow me to demonstrate some of the above properties on a more realistic dataset. In this example, data on concrete-filled steel tubes are collected into a dataset. If we apply some of the above properties to this dataset, we will arrive at Table 3.2 which will help us visualize this dataset. This table also indicates the range of applicability we expect our to-be-developed ML model to be applied to.

While Table 3.2 is indeed helpful, perhaps we can visualize our dataset via other means. For example, we can plot our dataset. There are many, many ways to do so. Let us go over a few.

### Histograms

Display the frequency distribution for a numerical feature. By default, a histogram also shows the range of a feature as well as intervals of equal length (or bins). For example, a look in Figure 3.2a shows the distribution of the tube thickness in our dataset as plotted in Microsoft Excel. As you can see, this distribution is a bit skewed to the left and seems to have a good number of observations on its skewed side. On the other hand, the number of observations heavily drops on the right side. This reflects the presence of a limited number of tubes (or columns) with large thicknesses. Figures 3.2b and 3.2c plot different styles of histograms for other features using Python and R. Histograms are a great tool to show individual features.

### Boxplots

Display a summary of the main characteristics of numerical features through the mean, median, IQR, and possible outliers. These plots can be used to display one or multiple features. As you can see, Figure 3.3 shows a boxplot for two features (yield strength of tube and compressive strength of concrete filling). This boxplot marks the mean with an x and the median with a line that crosses the box. The lines of this box represent the 25th and 75th percentile. The farthest horizontal lines from the box are calculated as 1.5 × IQR. Possible outliers are also plotted as dots.

### (a) Using Excel

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_61_0.png)

### (b) Using Python

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_61_1.png)

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3 [Examples].xlsx")
sns.set(rc = {'figure.figsize':(6,6)})
df
sns.distplot(df['Compressive strength of concrete (MPa)'], bins=15, kde=False)
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_61_2.png)

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3 [Examples].xlsx")
sns.set(rc = {'figure.figsize':(6,6)})
df
sns.histplot(data = df, x = "Yield strength (MPa)", kde = True)
```

### (c) Using R

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_62_0.png)

```
library(tidyverse)
library(ggplot2)
data=read.csv('C:/Chapter 3.csv')
data
str(data)
hist(data$Compressive.strength.of.concrete.MPa.,
     main = " Compressive strength of concrete Mpa",
     xlab = " Compressive strength of concrete Mpa",
     ylab = "count")
```

**Figure 3.2 (Cont'd)** Demonstration of histograms.

Up to this point, we were interested in visualizing features by themselves or via comparison against other features. While such insights are helpful, we are also interested in the relationships between features and, more importantly, between features and the target of interest. Here is where we go toward visualization tools that can accommodate more than one variable.

### Scatter plot

This plot depicts the relationship between two variables – often a feature and the target. The target is plotted on the vertical axis, and the feature is plotted on the horizontal axis. Figure 3.4 shows such a plot for the case of tube diameter and axial capacity.<sup>62</sup> As you can see, there seems to be some form of a relationship between these two variables, where columns with larger diameters tend to have larger axial capacity. If we focus our attention on the bottom two left of Figure 3.4a, we can clearly note the presence of a dense group of data (as compared to the top right corner of the same plot). This effectively implies that the dataset contains plenty of examples on columns of relatively smaller diameter.

The bottom of Figure 3.4a also shows a similar scatter plot but for the case of tube thickness. This plot has some similarities with the plot on tube diameter. For example, there seems to be some form of a weaker rising relationship between the tube diameter and the axial capacity. In addition, if we look at data points for columns with a tube thickness varying between 8 and 14 mm, we will notice that the axial capacity drastically changes for such columns. This is a sign of the presence of possible outliers.<sup>63</sup>

Figure 3.4 shows that the data clutters and it becomes hard to visualize individual points. Thus, proper formatting is important to ensure that we gain the most of this plot. For example, filling the markers with a light tone can significantly enhance the quality of this plot.<sup>64</sup> Similar observations can be made from the different scatter plots as seen in Python and R.

62 This makes sense since larger columns may have larger thicknesses and hence require larger loads to fail. Also, larger columns can contain larger amounts of concrete.
63 This is a visual inspection. To ensure that such possible outliers are indeed outliers, a proper analysis is to be carried out. You will see in the next few chapters that we do have methods and algorithms that can help us!
64 Side note: aim to design the plots to be as simple and informative as possible. Over formatting plots can be distracting. Remember your audience!
