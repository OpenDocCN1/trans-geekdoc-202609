```
count    3.000000
mean     93.666667
std      6.506407
min      87.000000
25%      90.500000
50%      94.000000
75%      97.000000
max     100.000000
dtype: float64
```

The 25%, 50% and 75% are quartiles:

+   - 50% represents the median of the sorted values.
+   - 25% represents the median of the first half of the sorted values.
+   - 75% represents the median of the second half of the sorted values.

For the quartiles, if there are two middle elements, then their average is that quartile’s median. We have only three values in our Series, so the 25% quartile is the average of 87 and 94, and the 75% quartile is the average of 94 and 100. Together, the interquartile range is the 75% quartile minus the 25% quartile, which is another measure of dispersion, like standard deviation and variance. Of course, quartiles and interquartile range are more useful in larger datasets.

# Creating a Series with Custom Indices

You can specify custom indices with the index keyword argument:

lick here to view code image

```
In [12]: grades = pd.Series([87,      100,   94], index=['Wally', 'Eva',   'Sam']

  n [13]: grades
Out[13]:
Wally      87
Eva       100
Sam        94
dtype: int64
```

In this case, we used string indices, but you can use other immutable types, including integers not beginning at o and nonconsecutive integers. Again, notice how nicely and concisely pandas formats a Series for display.