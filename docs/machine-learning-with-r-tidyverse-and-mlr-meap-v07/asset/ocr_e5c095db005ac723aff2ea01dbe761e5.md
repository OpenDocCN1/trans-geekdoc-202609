![](bbox=[0.131, 0.066, 0.864, 0.402])

Figure 14.6 The effect of changing max_iter (row facets) and eta (column facets) using the default values of theta and perplexity, on the final t-SNE embedding of the swissTib dataset.

So now that we’re a little more clued up about how t-SNE’s hyperparameters affect its performance, let’s run t-SNE on our Swiss banknote dataset. Just like for PCA, I first select all the columns except the categorical variable (t-SNE also cannot handle categorical variables), and pipe this data into the `Rtsne()` function. I manually set the values of the perplexity, theta, and max_iter hyperparameters (honestly, I rarely alter eta), and set the argument `verbose = TRUE` so the algorithm prints a running commentary on what the Kullback–Leibler divergence is at each iteration.

# Listing 14.1 Running t-SNE

```
```r
swissTsne <- select(swissTib, -Status) %>%
  Rtsne(perplexity = 30, theta = 0, max_iter = 5000, verbose = TRUE)
```
```

> **TIP**  By default, the `Rtsne()` function reduces the dataset down to two dimensions. If you want to return another number, you can set this using the `dims` argument.

That didn’t take too long did it? For a small dataset like this, t-SNE takes only a few seconds. But it gets slow quickly (see what I did there?) as the dataset increases in size.