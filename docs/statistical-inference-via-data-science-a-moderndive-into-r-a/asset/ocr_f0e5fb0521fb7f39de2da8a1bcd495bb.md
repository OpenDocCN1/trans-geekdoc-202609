| | | | | |
|---|---|---|---|
| 3 | 1 | 1899 | 3.9 |
| 4 | 1 | 1912 | 3.8 |
| 5 | 1 | 4637 | 3.3 |
| 6 | 1 | 511 | 3.5 |
| 7 | 1 | 127 | 4 |
| 8 | 1 | 4419 | 3.5 |
| 9 | 1 | 4729 | 4.2 |
| 10 | 1 | 2574 | 4.1 |

# i 90 more rows

We can use it to calculate the sample mean weight:

```
almonds_sample_100 |>
summarize(sample_mean = mean(weight))
```

```
# A tibble: 1 x 2
replicate sample_mean
<int>dbl
1 3.682
```

Then $\bar{F}= 3.682$ is an estimate of the population mean weight. In summary, the **estimator** is the procedure, equation, or method that will be used on a sample to estimate a parameter before the sample has been retrieved and have useful properties discussed in Chapter 7. The moment a sample is taken and the equation of a sample mean is applied to this sample, the resulting number is an **estimate**.

The sample mean, as an estimator or estimate of the population mean, will be a central component of the material developed in this chapter. But, note that it is not only the quantity of interest. For example, the population standard deviation of the almonds' weight, denoted by the Greek letter $\sigma$, is a parameter and the sample standard deviation can be an **estimator** or **estimate** of this parameter.

Furthermore, we have shown in Chapter 7 that the expected value of the sample mean is equal to the population mean. When this happens, the sample mean will be an **unbiased** estimator of the population mean; some sample means will be greater while others will be smaller, on average, they will be equal to the population mean. In general, when the expected value of an estimator is equal to the parameter it is trying to estimate, we call the estimator **unbiased**. If it is not, the estimator is **biased**.

We now revisit the almond study and how the sampling distribution of the sample mean can help us build interval estimates for the population mean.