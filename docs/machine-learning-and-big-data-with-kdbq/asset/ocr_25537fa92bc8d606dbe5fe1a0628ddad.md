# 204 Implementation

12.3.3.1 The calculation of the t' statistic is rather straightforward:

```
quantQ.stats.tTestOneSample([x1;mean])
// x1 - array to be tested
// mean - mean
// return t-statistics
// (avg[x1]-mean)%dev[x1]% sqrt count x1);
```

The input is the sample and the value of the mean we want to assess under the null hypothesis. The function returns the statistics. The assessment of the test is done using the function which maps statistics to the corresponding p-value for a given test set. In this example, we use the two-sided test for $\mu$ being equal to 0.45. The value of the statistic can be calculated as:

```
quantQ.stats.tTestOneSample[xTest:100?1.0;0.45]
```

1.929509 while make the corresponding p-value is:

```
quantQ.stats.pValueTwoSided abs quantQ.stats.tTestOneSample[xTest;0.45]
```

0.06 The p-value of the test is 6%, which suggests that we may reject the null hypothesis of mean being equal to 0.45 at 6% confidence level. Even though the mean is 0.5, and the value tested 0.45 is smaller by 10%, the size of the sample prevents us from rejecting the null confidently.

# 12.3.4 t-test: Two Samples

In the previous, we tested one sample against a static mean value. In practice, we may want to test two samples that have the same mean. Let us consider independently drawn sample $X_1, ..., X_N$ representing $N$ draws of a random variable $X$, which has a population mean $\mu_1$ and a standard deviation $\sigma_1$, and independently drawn sample $y_1, ..., y_M$ representing $M$ draws of a random variable $Y$, which has a population mean $\mu_2$ and standard deviation $\sigma_2$. The hypothesis to be tested is of the form:

+   - $H_0$: The population means are equal, $\mu_1 = \mu_2$.
- $H_a$: The population means are different.

The test is done by constructing a suitable test. The form of the statistic depends on the assumptions imposed on $N$ and $M$, and $\sigma_1$ and $\sigma_2$, respectively. The stronger the assumptions, the closer to asymptotic behaviour but more prone to model error. In this test, we focus on the least restricted of the two-sample $t$-statistic,