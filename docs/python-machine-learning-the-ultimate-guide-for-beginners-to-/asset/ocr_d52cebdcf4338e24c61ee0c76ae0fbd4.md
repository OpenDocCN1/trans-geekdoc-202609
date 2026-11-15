When you work with real data instead of nice, clean examples such as the iris datasets, you will sometimes have to also deal with time series. In machine learning, or data science, time series refer to certain data points that are marked on a graph or list by following a chronological order. In simpler terms, it's a series of points in time with an equal distance between each other. This sequence of time data has a wide application anywhere between statistical analysis and counting dark spots on the sun. Take note that datasets with time series are often quite messy. Therefore you have to clean up the data points. The easiest way to do this is to use a mean function, like this:

```
In: smooth_time_series = pd.rolling_mean(time_series, 5)
```

Keep in mind that you can also use the median operation instead. Furthermore, you can use a Pandas-specific function called “apply” in order to find out how many non-null values we have in every row:

```
In: iris.apply(np.count_nonzero, axis=1).head()
Out: 0   5
1   5
2   5
3   5
4   5
dtype: int64
```

Keep in mind that this function has a number of applications. Make sure to check the Pandas’ documentation for more information. Now, the final step is to use the “applymap” function in order to go deeper at the basic element level. For the sake of this demonstration, we are going to assume that the length of each cell’s string representation is something we will later need to process:

```
In: iris.applymap(lambda el:len(str(el))).head()
```

That’s it, but not quite. Data preprocessing is a vital step that ensures we are dealing with high quality data. We require useful information because it will certainly affect the way our machine