at the \(\alpha = 0.05\) level. The results are plotted in Figure 3.4. Clearly, using ranks provides a more powerful test across the range of sample sizes in this example.

```
set.seed(2142) # for reproducibility
N <- seq(from = 5, to = 100, by = 5) # range of sample sizes
res <- sapply(N, FUN = function(n) {
  pvals <- replicate(1000, expr = {
    x <- rnorm(n, mean = 0) # from each test
    y <- x + rnorm(length(x), mean = 0, sd = 0.1)
    y[1:3] <- 10 # insert outliers
    test1 <- gi.test(x, y) # no transformations
    test2 <- gi.test(x, y, g = rank, h = rank) # convert to ranks
    c(test1["pval"], test2["pval"]) # extract p-values
  })
})
apply(pvals, MARGIN = 1, FUN = function(x) mean(x < 0.05))
})
# Plot the results (Figure 3.4)
plot(N, res[2L, ], xlab = "Sample size", ylab = "Power", type = "l",
  ylim = c(0, 1), las = 1)
lines(N, res[1L, ], col = 2, lty = 2)
legend("bottomright",
  legend = c("Rank transformation", "No transformation"),
  lty = c(1, 2), col = c(1, 2), inset = 0.01,
  box.col = "transparent")
```

Remember, in recursive partitioning, the sample size decreases as you proceed further down the tree. Consequently, the tests become less powerful the further down the tree they are. Similar to CART-like decision trees, the more accurate splits tend to occur at the top.

Hothorn et al. [2006c] suggest that increasing \(\alpha\) can help assure that any type of dependence structure is detected. However, increasing \(\alpha\) will result in more splits and therefore a more complex tree. To avoid overfitting in this situation, pruning can be applied in a variety of ways, for example, collapsing terminal nodes that don't meet a second threshold \(\alpha' < \alpha\).

Similar to the cost-complexity parameter (\(cp\)) in CART (Section 2.5.1), you can also think of \(\alpha\) as a tuning parameter controlling the overall complexity of the tree (i.e., the number of terminal nodes)—with smaller values of \(\alpha\) leading to shallower trees. Hence, \(\alpha\) can be optimized using cross-validation or similar techniques, in which case, the former definition related to the type I error rate no longer applies.