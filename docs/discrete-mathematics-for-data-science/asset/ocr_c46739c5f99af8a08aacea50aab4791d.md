While there are other measures of correlation, use of Pearson correlation is common. For that reason, when referring to the Pearson correlation coefficient, we may plainly state “correlation coefficient” or just use it's symbol, r or R.

Correlation coefficient values range from $-1$ to $+1$, that is, $-1 \le r \le +1$. When $r$ is close to $1$, we have positive linear correlation. When $r$ is close to $-1$, we have negative linear correlation. And when $r$ is close to zero, we have no linear correlation.

Suppose that we have two sets of data, X and Y, and values from set X are somehow paired with values from set Y. Suppose we obtain a sample of size $n$ of these pairs, such as:

```
$(x_1, y_1), (x_2, y_2), \dots, (x_n, y_n)$
```

Before computing bivariate statistics of X and Y, we need to determine some component parameters, namely each set's mean, variance, and standard deviation.

As we have seen before, the sample mean and standard deviation for each set are defined as:

```
$$ar{x} = \frac{1}{n} \sum_{i=1}^n x_i \quad s_x = \sqrt{\frac{1}{n-1} \sum_{i=1}^n (x_i - \bar{x})^2}$$
```

```
$$ar{y} = \frac{1}{n} \sum_{i=1}^n y_i \quad s_y = \sqrt{\frac{1}{n-1} \sum_{i=1}^n (y_i - \bar{y})^2}$$
```

Now use $\bar{x}$ and $\bar{y}$ to construct the sample covariance between X and Y, which itself will be a component of the correlation coefficient. The covariance equation is:

```
$$s_{xy} = \frac{1}{n-1} \sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})$$
```