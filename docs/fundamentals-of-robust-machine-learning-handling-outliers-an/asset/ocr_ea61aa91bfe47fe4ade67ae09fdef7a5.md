Here, the upper value $x_{(\frac{n}{2}+1)}$ and lower value $x_{(\frac{n}{2})}$ are averaged to obtain the median, but technically *any value between the upper and lower values* can serve as the median which implies an infinite number of possible values.

We can already see a problem in that the median seems a little complicated, requires several steps, along with a caveat when $n$ is even, while the mean is easy to understand in one simple equation. This provides insight into why the median has not been embraced as readily as the mean. Furthermore, the mean is always unique, whereas the median may or may not be unique. In fact, it can either be unique or any one of an **infinite number of values** in a bounded region. However, the median is more important when it comes to finding the essence of a dataset with outliers, as we will see shortly. It is for good reason that we hear phrases like “the median house price” or “the median household income.”

Table 1.2 compares and contrasts these two statistics for some trivial cases. The first set {3, 1, 4, 2, 5, 3} produces 3 for both the mean and median. This is consistent with a visual examination of the values in the set. However, if we change one of the values from 3 to 100 to produce the second set, {100, 1, 4, 2, 5, 3}, the mean increases significantly to 19.2, while the median is 3.5, which is close to the previous value. In this case, the value of 100 would be considered an *outlier* because it is far away from the rest of the data. The mean is greatly affected by one outlier which makes it unstable. On the other hand, the median seems rather stable in the presence of one outlier.

Continuing the exercise, if we examine Set 3 listed as {100, 100, 1, 4, 2, 5, 3} in the final column of Table 1.2, we now have two outliers and the mean shifts further beyond the range of the original elements of Set 1 from 3.0 to 30.7. On the other hand, the median maintains relative stability at 4.0. We refer to the median as having the *robustness property* for this reason.

Returning to Set 2 for a moment, if we let $x_{(n)}$ represent the outlier value and set $x_{(n)} = 100$ initially, what happens as $x_{(n)} \to \infty$? The mean tends to $\infty$ while the median remains stable at 3.5. This is fundamentally why robust methods are needed in ML. If outliers are present, the model cannot be trusted using traditional methods.

# 1.4.2 Effect on Standard Deviation

The standard deviation is also greatly affected by outliers. Let $\mu$ be the population mean, and let $\bar{x}$ of Eq. (1.4.1) be an estimate of $\mu$. Further, let the population variance, $\sigma^2$, be defined by

```
\sigma^2 = \frac{1}{n} \sum_{i=1}^n (x_i - \mu)^2,
```

Table 1.2 Comparison of mean and median, and standard deviation (SD), and the normalized median absolute deviation (MADN) on three small datasets.

| Measure | Set 1 {3,1,4,2,5,3} | Set 2 {100,1,4,2,5,3} | Set 3 {100,100,1,4,2,5,3} |
|---|---|---|---|
| Mean | 3.0 | 19.2 | 30.7 |
| Median | 3.0 | 3.5 | 4.0 |
| SD | 1.41 | 36.9 | 47.3 |
| MADN | 1.48 | 2.22 | 3.0 |