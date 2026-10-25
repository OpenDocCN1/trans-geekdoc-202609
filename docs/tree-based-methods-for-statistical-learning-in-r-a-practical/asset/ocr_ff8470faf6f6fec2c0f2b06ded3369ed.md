# 3.4.1.1 Example: New York air quality measurements

To illustrate, let's write a simple function, called `gi.test()`, that uses the conditional inference procedure described in Section 3.3 to test the null hypothesis of general independence between two variables X and Y. To keep it simple, this function applies only to univariate continuous variables, and computes an approximate p-value assuming an asymptotic $\chi^2(1)$ distribution (see Section 3.3.1 for details)—although, it would not be too difficult to modify `gi.test()` to return approximate p-values using the permutation distribution instead. The arguments g and h allow for suitable transformations of the variables x and y, respectively; for example, if the relationship between X and Y is monotonic, but not necessarily linear, or if we suspect outliers, then we might consider converting X and/or Y to ranks (e.g., g = rank)—converting both X and Y to ranks is similar in spirit to conducting a correlation test based on Spearman's $\rho$. Both arguments default to R's built-in `identity()` function, which has no effect on the given values.

```
gi.test <- function(x, y, g = identity, h = identity) {
  xy <- na.omit(cbind(x, y)) # only retain complete cases
  gx <- g(xy[, 1L]) # transformation function applied to x
  hy <- h(xy[, 2L]) # influence function applied to y
  lin <- sum(gx * hy) # linear statistic
  mu <- sum(gx) * mean(hy) # conditional expectation
  sigma <- var(hy) * sum(gx ^ 2) # conditional covariance
  var(hy) * sum(gx) ^ 2 / length(hy)
  c.quad <- ((lin - mu) / sqrt(sigma)) ^ 2 # quadratic test statistic
  pval <- 1 - pchisq(c.quad, df = 1) # p-value
  c("chisq" = c.quad, "pval" = pval) # return results
}
```

Continuing with the New York air quality example, let's see which variable, if any, is selected to split the root node. Following convention, I'll use $\alpha = 0.05$ as the set threshold for failing to reject the global null hypothesis in step 1) of Algorithm 3.1.

The following code chunk applies the previously defined `gi.test()` function to test the null hypothesis of general independence between each of the five features and the response—if you skipped Section 3.3, then you can think of this as a simple test of association that defaults to using a test statistic whose asymptotic distribution (i.e., the approximate distribution for sufficiently large N) is $\chi^2(1)$. Note that the `p.adjust()` function mentioned earlier is used to adjust the resulting p-values to account for multiple tests using a simple Bonferroni adjustment: