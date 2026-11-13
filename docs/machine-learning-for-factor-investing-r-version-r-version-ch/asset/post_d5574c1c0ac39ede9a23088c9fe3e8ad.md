

```r
gather(key = strat, value = value, -date) %>%
ggplot(aes(x = date, y = value, color = strat)) + geom_line() + theme_grey()
g2 <- tibble(year = lubridate::year(t_oos),
benchmark = portf_returns[,1],
ml_based = portf_returns[,2]) %>%
gather(key = strat, value = value, -year) %>%
group_by(year, strat) %>%
summarise(avg_return = mean(value)) %>%
ggplot(aes(x = year, y = avg_return, fill = strat)) +
geom_col(position = "dodge") + theme_grey()
plot_grid(g1,g2, nrow = 2)
```

Out of the 12 years of the backtest, the advanced strategy outperforms the benchmark during 10 years. It is less hurtful in two of the four years of aggregate losses (2015 and 2018). This is a satisfactory improvement because the EW benchmark is tough to beat!

## 12.7 Second example: backtest overfitting

To end this chapter, we quantify the concepts of Section 12.4.2. First, we build a function that is able to generate performance metrics for simple strategies that can be evaluated in batches. The strategies are pure factor bets and depend on three inputs: the chosen characteristic (e.g., market capitalization), a threshold level (quantile of the characteristic) and a direction (long position in the top or bottom of the distribution).

![](img/8861a37f775d09b4ba7a5151f604d9f5_213_0.png)

FIGURE 12.3: Graphical representation of the performance of the portfolios.

```r
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

```r
strat(data_ml, "Pb", 0.3, 1)  # Large cap
```

| avg | sd | SR |
|-----|----|-----|
| 0.0102 | 0.0496 | 0.207 |

The output keeps three quantities that will be useful to compute the statistic (12.5). We must now generate these indicators for many strategies. We start by creating the grid of parameters.

```r
feature <- c("Div_Yld", "Ebit_Bv", "Mkt_Cap_6M_Usd", "Mom_11M_Usd", "Pb", "Vol1Y_Usd")
thresh <- seq(0.2, 0.8, by = 0.1)   # Threshold values
direction <- c(1, -1)               # Decision direction
pars <- expand.grid(feature, thresh, direction)  # The grid
feature <- pars[,1] %>% as.character()          # re-features
thresh <- pars[,2]                               # re-thresholds
direction <- pars[,3]                            # re-directions
```

This makes 84 strategies in total. We can proceed to see how they fare. We plot the corresponding Sharpe ratios below in Figure 12.4. The top plot shows the strategies that invest in the bottoms of the distributions of characteristics while the bottom plot pertains to the portfolios that are long in the lower parts of these distributions.

```r
grd <- pmap(list(feature, thresh, direction),    # Parameters for the grid search
            strat,                              # Function on which to apply the grid search
            data = data_ml                      # Data source/input
) %>%
  unlist() %>%
  matrix(ncol = 3, byrow = T)
grd <- data.frame(feature, thresh, direction, grd)  # Gather & reformat results
colnames(grd)[4:6] <- c("mean", "sd", "SR")        # Change colnames
grd <- grd %>% mutate_at(vars(direction), as.factor) # Change type: factor (for plot)
grd %>% ggplot(aes(x = thresh, y = SR, color = feature)) + # Plot!
  geom_point() + geom_line() + facet_grid(direction ~.)
```

![](img/8861a37f775d09b4ba7a5151f604d9f5_215_0.png)

**FIGURE 12.4:** Sharpe ratios of all backtested strategies.

The last step is to compute the statistic (12.5). We code it here:

```r
DSR <- function(SR, Tt, M, g3, g4, SR_m, SR_v){ # First, we build the function
  gamma <- -digamma(1) # Euler-Mascheroni constant
  SR_star <- SR_m + sqrt(SR_v)*(((1-gamma)*qnorm(1-1/M) + gamma*qnorm(1-1/M/exp(1)))) # SR*
  num <- (SR-SR_star) * sqrt(Tt-1) # Numerator
  den <- sqrt(1 - g3*SR + (g4-1)/4*SR^-2) # Denominator
  return(pnorm(num/den))
}
```

All that remains to do is to evaluate the arguments of the function. The “best” strategy is the one on the top left corner of Figure 12.4 and it is based on market capitalization.

```r
M <- nrow(pars)                                # Number of strategies we tested
SR <- max(grd$SR)                              # The SR we want to test
SR_m <- mean(grd$SR)                           # Average SR across all strategies
SR_v <- var(grd$SR)                            # Std dev of SR
# Below, we compute the returns of the strategy by recycling the code of the strat() function
data_tmp <- dplyr::select(data_ml, "Mkt_Cap_6M_Usd", date, R1M_Usd) # feature = Mkt_Cap
colnames(data_tmp)[1] <- "feature"
returns_DSR <- data_tmp %>%
  mutate(decision = feature < 0.2) %>% # Investment decision: 0.2 is the best threshold
  group_by(date) %>%                         # Date-by-date computations
  mutate(nb = sum(decision),                 # Nb assets in portfolio
         w = decision / nb,                  # Portfolio weights
         return = w * R1M_Usd) %>%           # Asset contribution to return
  summarise(p_return = sum(return))            # Portfolio return
g3 <- skewness(returns_DSR$p_return)         # Function from the e1071 package
g4 <- kurtosis(returns_DSR$p_return) + 3     # Function from the e1071 package
Tt <- nrow(returns_DSR)                      # Number of dates
DSR(SR, Tt, M, g3, g4, SR_m, SR_v)           # The sought value!
```

## [1] 0.6676416

The value 0.6676416 is not high enough (it does not reach the 90% or 95% threshold) to make the strategy significantly superior to the other ones that were considered in the batch of tests.

## 12.8 Coding exercises

- 1. Code the returns of the EW portfolio with tidyverse functions only (no loop).
- 2. Code the advanced weighting function defined in Equation (12.3).
- 3. Test it in a small backtest and check its sensitivity to the parameters.
- 4. Using the functional programming package purrr, avoid the loop in the backtest.

## Part IV

## Further important topics

![](img/8861a37f775d09b4ba7a5151f604d9f5_218_0.png)

## Taylor & Francis

Taylor & Francis Group

http://taylorandfrancis.com

This chapter is dedicated to the techniques that help understand the way models process inputs into outputs. A recent book (Molnar (2019) available at https://christophm.github.io/interpretable-ml-book/) is entirely devoted to this topic and we highly recommend to have a look at it. Another more introductory and less technical reference is Hall and Gill (2019). Obviously, in this chapter, we will adopt a tone which is factor-investing orientated and discuss examples related to ML models trained on a financial dataset.

Quantitative tools that aim for interpretability of ML models are required to satisfy two simple conditions:

- 1. That they provide information about the model.
- 2. That they are highly comprehensible.

Often, these tools generate graphical outputs which are easy to read and yield immediate conclusions.

In attempts to white-box complex machine learning models, one dichotomy stands out:

- **Global models** seek to determine the relative role of features in the construction of the predictions once the model has been trained. This is done at the global level, so that the patterns that are shown in the interpretation hold *on average* over the whole training set.
- **Local models** aim to characterize how the model behaves around one particular instance by considering small variations around this instance. The way these variations are processed by the original model allows to simplify it by approximating it, e.g., in a linear fashion. This approximation can for example determine the sign and magnitude of the impact of each relevant feature in the vicinity of the original instance.

Molnar (2019) proposes another classification of interpretability solutions by splitting interpretations that depend on one particular model (e.g., linear regression or decision tree) versus the interpretations that can be obtained for any kind of model. In the sequel, we present the methods according to the global versus local dichotomy.

