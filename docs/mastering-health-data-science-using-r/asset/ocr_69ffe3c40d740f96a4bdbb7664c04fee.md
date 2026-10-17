Another way to sample from a data frame is to use the `slice_sample()` function from the **tidyverse**. In this function, we can either specify the number of observations to sample `n` or the proportion of observations to sample `prop`. Additionally, we can sample with or without replacement by setting the value of the argument `replace` (with default value `FALSE`). We use this function to randomly sample 20% of observations without replacement.

```
```r
nhanes_sample <- NHANESsample %>%
  slice_sample(prop = 0.2, replace = FALSE)
dim(nhanes_sample)
#> [1] 6253   21
```
```

# ### 10.2.1 Practice Question

Set the random seed to 5 and then sample 50 observations with replacement from the set of integers from 1 to 100. Take the mean of those observations; it should be 56.7.

```
```r
# Insert your solution here:
```
```

Beyond sampling, we can also find the empirical cumulative distribution. That is, we can use a given vector to infer a distribution. In the following case, we draw a random sample from a normal distribution `vec` and then find its empirical cumulative distribution using the `ecdf()` function. This function actually returns a function, which can then be used to find the sample cumulative distribution for different values similar to the `p[dist]()` functions. In our example, we find the sample probability that $X \leq 0$.

```
```r
vec <- rnorm(100)
ecdf_vec <- ecdf(vec)
ecdf_vec(0)
#> [1] 0.63
```
```

We now plot this empirical distribution against the actual cdf using the `pnorm()` function. Note that in order to do so, we create a sequence of possible `x` values to pass to both `pnorm()` and `ecdf_vec()`.

```
```r
df <- data.frame(x = seq(-3, 3, 0.05))
df$ecdf <- ecdf_vec(df$x)
df$distn = pnorm(df$x)
```
```