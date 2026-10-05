# Exploratory Data Analysis

It is important to remember that different viewers may perceive the same graph differently. Color is sometimes used as a variable in graphs, where in particular a color map may suggest severity. Some viewers may have certain kinds of color blindness, and the colors may be misleading. For others, they might struggle to understand the interpretation.

Visuals can be a double-edged sword: points of interest can garner attention and to interest, and they can also mislead. In the next example, we plot over them. The viewer will follow the trend and see that the rightmost value fell. There is a bit of a trap here the 2023 value is based on the first half of the year. In fact, 2023 might be the best year. It is important to clarify this point to avoid misleading the viewer; annotation can be added to the plot to call out the half year.

```
year = ['2020', '2021', '2022', '1H2023']
revenue = [5, 8, 10, 7]
sns.barplot(x=year, y=revenue, color='grey')
```

![](bbox=[0.363, 0.435, 0.636, 0.587])

FIGURE 11.15: Bar Plot with Half Year

Adding layers to a plot should only be done if they are helpful in understanding the data. Consider the histogram in Figure 11.16 with an overplotted set of gridlines. The gridlines are so dark that they dominate the plot. Lighter layers as shown in Figure 11.17 allow the data to come forward.

From the examples given above, we see the importance for graphics to be clear and accurate to avoid misleading viewers. As we create graphics to show data, we should challenge them with questions including those listed below. By honestly addressing the questions, we can produce better graphics.

+   * Is this graph necessary?
* Is this clearly communicating the data?
* Is there anything misleading, missing, or incorrect?