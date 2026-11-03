
Before we proceed with other plots, we will understand the use of `theme()` function which gives more control over plot annotations. The following code snippet uses `theme()` to change the text colour of the title, x-axis andy-axis, as well as centre align the title.

![](images/page62-01.png)![](images/page62-02.png)

**[Figure 3.4](#11_Chapter03.xhtml#fig3.4)** shows the scatter plot with changes in the default plot theme of ggplot2. However, the background colour of the graph as well as major and minor axis are present. We can further customize the graph. **[Figure 3.5](#11_Chapter03.xhtml#fig3.5)** shows the outcome using the following code snippet.

![](images/page62-03.png)![](images/page63-01.png)![](images/page63-02.png)

In the above code snippet, the arguments which can be used in `element_text` are as follows:

**1.** `family`: font family

**2.** `face`: font face. Possible values are ‘plain, ‘italic’, ‘bold’, and ‘bold.italic’

**3.** `colour`: text colour

**4.** `size`: text size in pts

**5.** `hjust`: horizontal justification (between 0 and 1. 0 = left aligned, 0.5 = centre aligned, 1 = right aligned)

**6.** `vjust`: vertical justification (between 0 and 1. 0 = left aligned, 0.5 = centre aligned, 1 = right aligned)

**7.** `lineheight`: line height. In multi-line text, the line height argument is used to change the spacing between lines

Get the help on `?ggplot2::theme` and `?ggplot2::element_text`, which works in conjunction with `theme`.

We can remove the title and axis labels by using `element_blank()` within the `theme()`. There are in-built themes such as `theme_bw()`, `theme_classic()`, `theme_dark()`, `theme_grey()`, `theme_light()`, `theme_minimal()`, etc., which can be directly applied to the plots. The below code snippet is being used to set a custom theme to be used in all code snippets in this chapter.

![](images/page63-03.png)![](images/page64-01.png)

### 3.5.2 Bar Chart

Bar chart is a frequency chart for qualitative variable (or categorical variable). Histograms (discussed in [Section 3.5.3](#11_Chapter03.xhtml#sec3.5.3)) cannot be used when the variable is qualitative. Bar chart can be used to assess the most-occurring and least-occurring categories within a dataset (Kumar, 2017; Roshan, 2020). To draw a bar chart, we can:

**1.** Use `geom_bar()` which makes the height of the bar proportional to the number of cases in each category or group (if the `weight` aesthetic is supplied, it sums up the weights).

**2.** Use `geom_col`, in case we want the height of the bar to represent actual values. The dataframe should be passed in the parameter `data`. **[Figure 3.6](#11_Chapter03.xhtml#fig3.6)** shows a bar plot created for the count of players for each age category.

`geom_bar()` uses `stat_count()` by default and thus counts the number of records at each horizonal (`x`) position. `geom_col()` uses `stat_identity()` which plots the actual values from the data.

Since `AGE` is being read as an integer variable by `data.table`, we will typecast it as a `factor` variable before proceeding with a plot of bar charts. To get a count of players by age, we can use the following codes:

![](images/page64-02.png)

From **[Figure 3.6](#11_Chapter03.xhtml#fig3.6)**, we can observe that a majority of the players are in the age group of 25-35 (`AGE` 2). To plot the sum of `SOLD_PRICE` for different `AGE` groups and display the total sold price by each age category, we should pass `SOLD PRICE` as `weight` parameter and `AGE` as `x` parameter (horizontal axis).

Note that to show the vertical axis values in dollars, we have passed `labels` argument in `scale_y_continuous` function. It can take three values, that is, `scales::percent`, `scales::dollar` and `scales::comma`.

![](images/page64-03.png)![](images/page65-01.png)![](images/page65-02.png)

We can create **[Figure 3.7](#11_Chapter03.xhtml#fig3.7)** by using `geom_col` as shown below.

![](images/page65-03.png)

We can also create bar charts which can be grouped by a third variable. In **[Figure 3.8](#11_Chapter03.xhtml#fig3.8)**, we show the total sold price by each age category but grouped by playing roles. The parameter `fill` takes the third variable as a groupby parameter. In this case, we pass `PLAYING ROLE` as the `fill` parameter.

![](images/page66-01.png)![](images/page66-02.png)

In case we want to show the relative proportions at each `AGE` group, we can use `position = position_fill()` which stacks the bars and then standardizes each of them to have the same height.

![](images/page66-03.png)

In **[Figure 3.9](#11_Chapter03.xhtml#fig3.9)**, we can compare the sold price for batsmen in three different age groups and conclude that batsmen were sold for maximum value in `AGE` group 1, followed by `AGE` group 3 and `AGE` group 2. By default, the `geom_bar` or `geom_col` will give a stacked bar chart. **[Figure 3.10](#11_Chapter03.xhtml#fig3.10)** shows the bars in dodged position. We set the `position` argument as `position = position_dodge()`.

![](images/page66-04.png)![](images/page67-01.png)![](images/page67-02.png)

If we want to show the average sold price for each `AGE` group, we will first create a `data.table` with this statistic using the following codes. The average sold price across various age group is shown in **[Table 3.4](#11_Chapter03.xhtml#tab3.4).**

**TABLE 3.4** | Mean sold price by age

| `AGE` || `AVG_SOLD_PRICE` |

| --- | --- |

| 1 || 720,250.0 |

| --- | --- |

| 2 || 484,534.9 |

| 3 || 520,178.6 |

![](images/page67-03.png)![](images/page68-01.png)

The following code chunk can be used for creating **[Figure 3.11](#11_Chapter03.xhtml#fig3.11):**

![](images/page68-02.png)

From **[Figure 3.11](#11_Chapter03.xhtml#fig3.11)**, we can note that the average sold price is higher for age category 1. Also note that the `fill` is passed as an aesthetic outside the `mapping` argument as we wanted to fill the same colour across all age groups.

We can create bar charts which can be grouped by a third variable. In the example below **([Figure 3.12](#11_Chapter03.xhtml#fig3.12))**, we show average sold price by each age category but grouped by playing roles **([Table 3.5](#11_Chapter03.xhtml#tab3.5)).**

![](images/page68-03.png)

The parameter `fill` takes the third variable as group by variable. In this case, we pass `PLAYING ROLE` as `hue` parameter.

![](images/page69-01.png)![](images/page69-02.png)![](images/page69-03.png)

From **[Figure 3.12](#11_Chapter03.xhtml#fig3.12)**, we can see that in age categories 1 and 2, batsmen are paid the most, whereas allrounders attract most money in age category 3.

### 3.5.3 Histogram

A histogram is a plot that shows the frequency distribution of a set of continuous variables. It gives an insight into the underlying distribution (e.g. normal distribution) of the variables, outliers, skewness, etc. To draw a histogram, we use `geom_histogram()` function of ggplot2. The following is an example of how to draw a histogram for `SOLD PRICE` and understand its distribution **([Figure 3.13](#11_Chapter03.xhtml#fig3.13)).**

![](images/page69-04.png)![](images/page70-01.png)![](images/page70-02.png)

The histogram in **[Figure 3.13](#11_Chapter03.xhtml#fig3.13)** shows `SOLD PRICE` is right skewed. Most players are auctioned at low price range of 250,000 and 500,000, whereas there are a few players paid very highly, upwards of 1 million dollars. By default, it tries to estimate the bins which cover the range of the data. To create more bins, the `bins` parameter can be set in the `geom_histogram()` method, as shown in **[Figure 3.14](#11_Chapter03.xhtml#fig3.14).**

![](images/page70-03.png)![](images/page71-01.png)![](images/page71-02.png)

We can use the `fill` aesthetic to show a histogram plot of sold price of players with different playing roles. **[Figure 3.15](#11_Chapter03.xhtml#fig3.15)** represents the same.

![](images/page71-03.png)
