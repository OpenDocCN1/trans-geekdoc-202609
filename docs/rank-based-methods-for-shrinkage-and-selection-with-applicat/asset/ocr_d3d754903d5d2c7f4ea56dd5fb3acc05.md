of the slope and intercept for a given set of data points. More generally, it is the maximum likelihood estimate under the normality assumptions for the error.

# 1.3.2 Theil's Estimator

We can also estimate the parameters using the median by way of Theil's estimator (Theil, 1950). For a given set of points, $\{(x_i, y_i)\}_{i=1}^n$, Theil's estimators of $\beta$ and $\theta$ can be obtained by finding the median of the pairwise slopes of all points in the data set, denoted by $\hat{\beta}_n^{\text{Theil}}$, and the median of partial residuals, $(y_i - \hat{\beta}_n^{\text{Theil}} x_i)$, which we denote by $\hat{\theta}_n^{\text{Theil}}$. The actual residuals are $(y_i - (\hat{\theta}_n^{\text{Theil}} + \hat{\beta}_n^{\text{Theil}} x_i))$ which are obtained after estimation. See Hallander and Wolfe (1999) for more details. Hence, we have that

\(\hat{\beta}_n^{\text{Theil}} = \text{median}_{1 \le i < j \le n, i \neq j} \left( \frac{y_j - y_i}{x_j - x_i} \right),\) (1.3.5)

and

\(\hat{\theta}_n^{\text{Theil}} = \text{median}_{1 \le i \le n} (y_i - \hat{\beta}_n^{\text{Theil}} x_i).\) (1.3.6)

Theil's method is an unbiased estimator. Its breakdown point is known to be 29.3%. While this is not as high as 50%, it can tolerate outliers to a higher degree than LSE making it a more robust estimator.

# 1.3.3 Belgium Telephone Data Set

It is instructive to qualitatively compare the mean versus median approaches using a very simple data set. For this purpose, we will use the Belgium telephone data set (Kloke and McKean, 2012). This data set is provided in Table 1.3 and contains the number of calls (in units of tens of millions) made in Belgium in the years between 1950 and 1973. It has 24 data points, with 6 outliers. The outliers are due to a change in measurement technique without re-calibration for 6 years, as is often cited.

Table 1.3 Belgium telephone data set.

| x | 1950 | 1951 | 1952 | 1953 | 1954 | 1955 | 1956 | 1957 | 1958 | 1959 | 1960 | 1961 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| y | 0.44 | 0.47 | 0.47 | 0.59 | 0.66 | 9.73 | 0.81 | 0.88 | 1.06 | 1.2 | 1.35 | 1.49 |

| x | 1962 | 1963 | 1964 | 1965 | 1966 | 1967 | 1968 | 1969 | 1970 | 1971 | 1972 | 1973 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| y | 1.61 | 2.12 | 11.9 | 12.4 | 14.2 | 15.9 | 18.2 | 21.2 | 4.3 | 2.4 | 2.7 | 2.9 |