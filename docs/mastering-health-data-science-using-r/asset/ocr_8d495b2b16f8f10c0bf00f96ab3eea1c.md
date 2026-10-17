```
p_grid <- c(50, 100)
s_grid = c(10)
iter_grid <- 1:5
param_grid <- expand.grid(rho = rho_grid, snr = snr_grid, n = n_grid,
                          p = p_grid, s = s_grid, iter = iter_grid)

# convert to numeric
param_grid <- as.matrix(param_grid)
head(param_grid)
#>   rho snr n p s iter
#> [1,] 0.35 0.1 500 50 10  1
#> [2,] 0.35 0.5 500 50 10  1
#> [3,] 0.35 1.5 500 50 10  1
#> [4,] 0.35 0.1 500 100 10  1
#> [5,] 0.35 0.5 500 100 10  1
#> [6,] 0.35 1.5 500 100 10  1
```

Recall that our main function took in a named vector that contained all needed parameters. This allows us to use an apply() function to run our simulation. In order to summarize by method, we pivot the results to a longer form with a column for method.

```
# Run experiments
results <- apply(param_grid, 1, model_selection) %>% t()

# Convert to long data frame
results <- as.data.frame(results) %>%
  pivot_longer(cols = starts_with(c("lasso", "ridge")),
               names_to = c("method", ".value"), names_sep="_")
```

Finally, we summarize our results. For example, we can create a table with the average time for each method grouped by the data dimensions. We observe that ridge regression was slower on average than lasso.

```
avg_time <- results %>%
  group_by(method, n, p) %>%
  summarize(avg_seconds = round(mean(sec), 3)) %>%
  ungroup()
avg_time
#> # A tibble: 4 x 4
#> method n p avg_seconds
#> <chr> <dbl> <dbl> <dbl>
```