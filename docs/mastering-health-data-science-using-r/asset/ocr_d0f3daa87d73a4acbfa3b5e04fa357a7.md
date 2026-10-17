# 19.3 Results

```
```text
#> 1 lasso    500     50      0.019
#> 2 lasso    500    100      0.03
#> 3 ridge    500     50      0.022
#> 4 ridge    500    100      0.045
```
```

We can also create summary plots of our evaluation metrics similar to Hastie, Tibshirani, and Tibshirani (2020). To do so, we create one last function that will create a plot of the relative test error and percentage of variance explained across different signal-to-noise ratios. This allows us to regenerate this plot for different parameter settings.

```
```r
#' Generate RTE and PVE plots for a given set of parameters
#'
#' @param results Data frame with simulation results
#' @param n_input Number of observations
#' @param p_input Number of variables
#' @param s_input Sparsity level
#' @return ggplot object
generate_plot <- function(results, n_input, p_input, s_input) {

  setting <- results %>%
    filter(n == n_input, p == p_input, s == s_input) %>%
    group_by(method, snr) %>%
    summarize(mean_RTE = mean(RTE, na.rm = TRUE),
              sd_RTE = sd(RTE, na.rm = TRUE),
              mean_PVE = mean(PVE, na.rm = TRUE),
              sd_PVE = sd(PVE, na.rm = TRUE))

  rte_plot <- ggplot(setting) +
    geom_point(aes(x = snr, y = mean_RTE, color = method)) +
    geom_errorbar(aes(x = snr, ymin = mean_RTE - sd_RTE,
                      ymax = mean_RTE + sd_RTE, color = method),
                  alpha = 0.8, width = 0.2) +
    geom_line(aes(x = snr, y = mean_RTE, color = method)) +
    theme_bw() +
    theme(legend.position = "bottom") +
    labs(x = "SNR", y = "RTE", color = "")

  pve_plot <- ggplot(setting) +
    geom_point(aes(x = snr, y = mean_PVE, color = method)) +
    geom_errorbar(aes(x = snr, ymin = mean_PVE - sd_PVE,
                      ymax = mean_PVE + sd_PVE, color = method),
```
```