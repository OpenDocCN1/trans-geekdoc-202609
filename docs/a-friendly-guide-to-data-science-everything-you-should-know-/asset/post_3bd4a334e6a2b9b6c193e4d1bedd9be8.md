
![](img/df37a23523ff92247f9125691b1edea2_679_0.png)

**Figure 18-28.** A Pareto chart including cumulative percentage

The cumulative line doesn't radically change the look of the chart, it's easy to see how it emphasizes the fact that the growth slows down the end because there are more values to the left side of the chart.

## Boxplot

Another chart we saw in Chapter 2 was the boxplot, which gives us the distribution of each group among several. Boxplots rely on certain points in the distribution to show the spread of the data. They're more intuitive than some statistically based charts and can be explained rather quickly to people who haven't seen them before. They also show outliers well. See Figure 18-29 for an example.

![](img/df37a23523ff92247f9125691b1edea2_680_0.png)

Figure 18-29. Boxplot

Figure 18-29 shows a two-group boxplot with the second group with values that are both higher and more spread out than the first. In this plot, the colored area represents the interquartile range (IQR); between Q1 and Q3), with the central line representing the median. In this version, the “x” represents the mean, which is noticeably higher than the median in the second group, which means the distribution is skewed. The horizontal lines (“whiskers”) at the top and bottom of each group represent the min and max, with the exception of outliers. The min and max use 1.5 times the IQR, with min being Q1 minus that value and the max being Q3 plus the value. Outliers here are defined as anything greater than the calculated max or lower than the calculated min. Extreme outliers can also be included and are anything lower than Q1 minus 3 times the IQR or greater than Q3 plus 3 times the IQR.

We can look at some student credit data, this time showing first-, second-, and third-year students. See Figure 18-30.

## CHAPTER 18: A NEW KIND OF STORYTELLING: DATA VISUALIZATION AND PRESENTATION

![](img/df37a23523ff92247f9125691b1edea2_681_0.png)

**Figure 18-30.** A subplot showing total credits completed by year of student

The figure looks overall like we would expect, with increasing medians, mins, and maxes for each year, but also a decent spread for each year. Some students are part-time and others overload themselves or receive college credit through other methods, so not all students are going to look the same. There are a couple of overachieving second-year students, but those are the only outliers. First- and second-year students have the mean and median close together, indicating little skew, but the mean is lower than the median in the third-year group.

This chart comes up a lot in EDA and less often in charts for stakeholders, but it can still be valuable with the right data and stakeholders.

659

## CHAPTER 18: A NEW KIND OF STORYTELLING: DATA VISUALIZATION AND PRESENTATION

## Heatmaps

A heatmap is an enhancement on a table where the range of values are represented by different colors and gradients, usually light to dark for small to large numbers. It can be very helpful in conveying information quickly because of the visual aspect, but still with the detail of a table. See Figure 18-31 for an example of a heatmap showing average grades of middle and high school students in a range of general subjects.

| Grade | English | Science | Social Studies | Art | Music | Band | Foreign Language |
|---|---|---|---|---|---|---|---|
| 6th grade | 85 | 91 | 88 | 87 | 94 | 93 | 89 |
| 7th grade | 83 | 90 | 89 | 88 | 91 | 96 | 89 | 90 |
| 8th grade | 82 | 89 | 86 | 87 | 89 | 91 | 85 |
| 9th grade | 79 | 86 | 82 | 85 | 90 | 88 | 86 |
| 10th grade | 75 | 80 | 79 | 91 | 91 | 96 | 81 |
| 11th grade | 73 | 85 | 79 | 82 | 88 | 87 | 77 |
| 12th grade | 73 | 85 | 80 | 90 | 93 | 95 | 81 |

Figure 18-31. A heatmap of grades of students in 6th-12th grade

This heatmap makes it clear that as the grades progress, some subject average grades go down, but others don't have the same trajectory. The core subjects tend to follow this trend, whereas the electives don't. Without the grayscale coloring, we wouldn't see this so quickly.

One of the many benefits of heatmaps is that you can show a lot of data while keeping it more readable than some other visualizations. This is one reason it's common when using EDA to make correlation matrix heatmaps, especially because you can use two different colors and represent positive and negative values in different colors and different intensities.

It's all worth checking any time you are working with tabular data to see if a heatmap would be appropriate. Stakeholders tend to like them, too.

## CHAPTER 18: A NEW KIND OF STORYTELLING: DATA VISUALIZATION AND PRESENTATION

## Treemaps

I mentioned treemaps above because they can serve as an alternative to a pie chart that's appropriate when there are too many categories to make a readable pie chart, and they also allow grouping. See Figure 18-32 for an example of a treemap showing the population of US states grouped by region. The size of the rectangle represents the population of the state.

![](img/df37a23523ff92247f9125691b1edea2_683_0.png)

Figure 18-32. A treemap showing US state populations grouped by region

The grouping is a nice bonus, but despite the fact that there are 51 data points, we can still read most of them. The bottom right is Hawaii and Alaska, grouped as “Pacific.” Compare with the pie chart in Figure 18-33,

661

## CHAPTER 18: A NEW KIND OF STORYTELLING: DATA VISUALIZATION AND PRESENTATION

![](img/df37a23523ff92247f9125691b1edea2_684_0.png)

- Alabama
- Alaska
- Arizona
- Arkansas
- California
- Colorado
- Connecticut
- Delaware
- District of Columbia
- Georgia
- Hawaii
- Idaho
- Illinois
- Indiana
- Kansas
- Kentucky
- Louisiana
- Maine
- Maryland
- Massachusetts
- Michigan
- Minnesota
- Mississippi
- Missouri
- Montana
- Nebraska
- Nevada
- New Hampshire
- New York
- New Mexico
- North Carolina
- North Dakota
- Other
- Oklahoma
- Oregon
- Pennsylvania
- Rhode Island
- South Carolina
- South Dakota
- Tennessee
- Texas
- Utah
- Vermont
- Virginia
- Virginia (repeated)
- Washington
- West Virginia
- Wisconsin
- Wyoming

Figure 18-33. A terrible pie chart showing state populations

This pie chart is obviously ridiculous, but the treemap is actually quite readable and intuitive and has the added bonus of grouping. When you have numeric data with one or two levels, consider a treemap. Stakeholders don't see them too often, but you'll have no trouble explaining it to them.

## CHAPTER 18: A NEW KIND OF STORYTELLING: DATA VISUALIZATION AND PRESENTATION

## Choropleth Map

Everyone has seen a choropleth map, but almost no one knows the name. It's simply a geographical map of voting with different areas colored to some values. The maps all the news stations create of the United States around elections, with states colored blue or red, are all choropleth maps. See the 2008 US election map in Figure 18-34, showing county- and state-level voting.

Figure 18-34. A map showing the results of the 2008 presidential election

In this map, blue means the state's electoral college votes went to the Democratic candidate and red went to the Republican candidate. It's also really common to place colors on a gradient based on values, as was done here at the county level. This can be done on a true gradient, where the lowest value has the lightest color and the highest value has the darkest color, with everything proportional. Alternatively, it's possible to bin the values to have a finite number of colors or shades. There are advantages and disadvantages to each. Figure 18-35 shows a map of US state populations with the shades binned.

662

![](img/df37a23523ff92247f9125691b1edea2_685_0.png)
