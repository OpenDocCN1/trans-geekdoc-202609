```
series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
groups = series.groupby(Grouper(freq='10YS'))
decades = DataFrame()
for name, group in groups:
    if len(group.values) is 10:
        decades[name.year] = group.values
decades.boxplot()
pyplot.show()
```

Listing 31.10: Create a box and whisker plots of the Baltimore Water Usage dataset.

Running the example creates 6 box and whisker plots side-by-side, one for the 6 decades of selected data. Some observations from reviewing the plot include:

+   The median values for each year (red line) may show an increasing trend that may not be linear.

+   The spread, or middle 50% of the data (blue boxes), does show some variability.

+   There maybe outliers in some decades (crosses outside of the box and whiskers).

+   The second to last decade seems to have a lower average consumption, perhaps related to the first world war.

![](bbox=[0.18, 0.49, 0.81, 0.85])

Figure 31.3: Box and whisker plots of the training set for the Baltimore Water Usage dataset.