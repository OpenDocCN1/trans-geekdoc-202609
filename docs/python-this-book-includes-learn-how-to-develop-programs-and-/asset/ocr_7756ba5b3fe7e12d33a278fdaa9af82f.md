used to determine the hypothesis.

![](bbox=[0.134, 0.137, 0.599, 0.335])

For a two-tailed test, when a given percentage of 5% is used, then it's distributed equally on both sides. In this case, it is 2.5% on one side, and 2.5% on the opposite side.
Here's an example to illustrate this. The average score of mathematics exam at a national level is 60 marks, and the standard deviation is 3 marks. The average marks of the class is 53. The null hypothesis refers to the mean marks of the class, similar to the national average. First, let's test the following hypothesis by first finding the z-score 60.

```
>>> zscore = ( 53 - 60 ) / 3.0
>>> zscore
-2.3333333333333335
```

The p-value would be:

```
>>> prob = stats.norm.cdf(zscore)
>>> prob
0.009815328628645336
```

In this case, the p-value is 0.98%. The null hypothesis is to be rejected, and the p-value should be lower than 2.5% in either direction of the bell curve. Because the p-value is less than 2.5%, you can reject the null hypothesis and clearly define what the average marks of the class are different from the national average.