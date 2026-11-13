characteristic (e.g., market capitalization), a threshold level (quantile of the characteristic) and a direction (long position in the top or bottom of the distribution).

```
strat <- function(data, feature, thresh, direction){
  data_tmp <- dplyr::select(data, feature, date, R1M_Usd)  # Data
  colnames(data_tmp)[1] <- "feature"                     # Colname
  data_tmp %>%
    mutate(decision = direction * feature > direction * thresh) %>%  # Investment decision
    group_by(date) %>%                                    # Date-by-date analysis
    mutate(nb = sum(decision),                            # Nb assets in portfolio
           w = decision / nb,                             # Weights of assets
           return = w * R1M_Usd) %>%                      # Asset contribution
    summarise(p_return = sum(return)) %>%                  # Portfolio return
    summarise(avg = mean(p_return), sd = sd(p_return), SR = avg/sd) %>% # Perf. metrics
  return()
}
```

Then, we test the function on a triplet of arguments. We pick the price-to-book (Pb) ratio. The position is positive and the threshold is 0.3, which means that the strategy buys the stocks that have a Pb value above the 0.3 quantile of the distribution.

```
strat(data_ml, "Pb", 0.3, 1)  # Large cap
```

```
## # A tibble: 1 x 3
##   avg   sd    SR
##   <dbl> <dbl> <dbl>
## 1 0.0102 0.0496 0.207
```

The output keeps three quantities that will be useful to compute the statistic (12.5). We must now generate these indicators for many strategies. We start by creating the grid of parameters.

```
feature <- c("Div_Yld", "Ebit_Bv", "Mkt_Cap_6M_Usd", "Mom_11M_Usd", "Pb", "Vol1Y_Usd")
thresh <- seq(0.2, 0.8, by = 0.1)   # Threshold values values
direction <- c(1, -1)               # Decision direction
pars <- expand.grid(feature, thresh, direction)  # The grid
feature <- pars[,1] %>% as.character()          # re-features
thresh <- pars[,2]                               # re-thresholds
direction <- pars[,3]                            # re-directions
```

This makes 84 strategies in total. We can proceed to see how they fare. We plot the corresponding Sharpe ratios below in Figure 12.4. The top plot shows the strategies that invest in the bottoms of the distributions of characteristics while the bottom plot pertains to the portfolios that are long in the lower parts of these distributions.

```
grd <- pmap(list(feature, thresh, direction),    # Parameters for the grid search
            strat,                              # Function on which to apply the grid search
            data = data_ml                      # Data source/input
) %>%
  unlist() %>%
  matrix(ncol = 3, byrow = T)
grd <- data.frame(feature, thresh, direction, grd)  # Gather & reformat results
colnames(grd) [4:6] <- c("mean", "sd", "SR")        # Change colnames
grd <- grid %>% mutate_at(vars(direction), as.factor) # Change type: factor (for plot)
grd %>% ggplot(aes(x = thresh, y = SR, color = feature)) + # Plot!
  geom_point() + geom_line() + facet_grid(direction ~.)
```