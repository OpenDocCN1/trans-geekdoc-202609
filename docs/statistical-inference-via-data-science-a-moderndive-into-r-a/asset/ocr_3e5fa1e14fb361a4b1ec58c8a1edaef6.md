# 7.3 The Central Limit Theorem

So, the proportion of red balls is 0.375 with a standard deviation of 0.484. The intuition behind the standard deviation can be expressed as follows: if you were to select many balls, with replacement, from the bowl, we would expect the proportion of red balls to be about 0.375 or give over 0.484.

In addition, when dealing with proportions, the formula for the standard deviation can be expressed directly in terms of the population proportion, $p$, using the formula:

```
$SD = \sqrt{p(1 - p)}$
```

Here is the value of the standard deviation using this alternative formula in R:

```
p <- 0.375
sqrt(p * (1 - p))

[1] 0.484
```

The value is the same as using the general formula. Now that we have gained a better understanding of the standard deviation, we can discuss the standard deviation in the context of sampling variation for the sample proportion.

# The standard error

Recall that we want to measure the magnitude of the sampling variation for the distribution of $X$ (the sampling distribution of the sample proportion) and want to use standard deviation for this purpose. We have shown earlier that the center of the distribution of $ar{X}$ is the expected value of $ar{X}$. In our case, this is the population proportion $p = 0.375$. The standard deviation will indicate how far, on average, each possible sample proportion roughly is from the population proportion. If we were to consider using a sample proportion as an estimate of the population proportion, this deviation could be considered the error in estimation. Because of this particular relationship, the standard deviation receives a special name: the **standard error**. Note that all *standard errors* are standard deviations but not all standard deviations are errors.

We work again with simulations and the bowl of red and white balls. We take 10,000 random samples of size $n=100$, find the sample proportion for each sample, and calculate the average and standard deviation for these proportions. This simulation produces a histogram similar to the one presented on the right in Figure 7.13. To produce this data we use the `rep_slice_sample()` function and `mean()` and `sd()` function inside summarize() to produce the desired results:

```
bowl |>
rep_slice_sample(n = 100
```