

```r
weights_xgb <- function(train_data, test_data, features){
train_features <- train_data %>% dplyr::select(features) %>% as.matrix() # Indep. variable
train_label <- train_data$R12M_Usd / exp(train_data$Vol1Y_Usd) # Dep. variable
ind <- which(train_label < quantile(train_label,0.2)| # Filter
             train_label > quantile(train_label, 0.8))
train_features <- train_features[ind, ] # Filtered features
train_label <- train_label[ind] # Filtered label
train_matrix <- xgb.DMatrix(data = train_features, label = train_label) # XGB format
fit <- train_matrix %>% # Data source (pipe input)
xgb.train(data = .,
        eta = 0.3, # Learning rate
        objective = "reg:linear", # Number of random trees
        max_depth = 4, # Maximum depth of trees
        nrounds = 80 # Number of trees used
        )
xgb_test <- test_data %>% # Test sample => XGB format
dplyr::select(features) %>% as.matrix() %>%
xgb.DMatrix()
pred <- predict(fit, xgb_test) # Single prediction
w <- pred > median(pred) # Keep only the 50% best predictions
w$weights <- w / sum(w)
w$names <- unique(test_data$stock_id) # Best predictions, equally-weighted
return(w)
}
```

与第 6.4.6 节提出的结构相比，区别在于标签不仅基于长期回报，还依赖于波动率分量。尽管标签分母中的波动率指数分位数，似乎可以说它受到夏普比率的启发，并且模型试图解释和预测风险调整后的回报，而不是原始回报。波动率非常低的股票在标签中其回报将保持不变，而波动率非常高的股票将看到其回报被除以接近三的因子（exp(1)=2.718）。

然后将此函数嵌入全局加权函数中，该函数仅包含两种方案：EW基准和基于ML的策略。

```r
portf_compo <- function(train_data, test_data, features, j){
if(j == 1){ # This is the benchmark
  N <- test_data$stock_id %>% # Test data dictates allocation
    factor() %>% nlevels()
  w <- 1/N # EW portfolio
  w$weights <- rep(w,N)
  w$names <- unique(test_data$stock_id) # Asset names
  return(w)
}
if(j == 2){ # This is the ML strategy.
  return(weights_xgb(train_data, test_data, features))
}
}
```

有了这个函数，我们可以转向主回测循环。鉴于我们使用大规模模型，循环的计算时间较长（在慢速CPU机器上可能需要几小时）。采用函数式编程可以加快循环速度（参见本章末尾的练习）。此外，一个简单的等权基准组合可以仅使用 tidyverse 函数来编写。

```
m_offset <- 12 # Offset in months for buffer period
train_size <- 5 # Size of training set in years
for(t in 1: (length(t_oos)-1)){ # Stop before last date: no fwd ret.!
  if(t%%12==0){print(t_oos[t])} # Just checking the date status
  train_data <- data_ml %>% filter(date < t_oos[t] - m_offset * 30, # Roll window w. buffer
                                   date > t_oos[t] - m_offset * 30 - 365 * train_size)
  test_data <- data_ml %>% filter(date == t_oos[t]) # Test sample
  realized_returns <- test_data %>% # Computing returns via:
    dplyr::select(R1M_Usd) # 1M holding period!
  for(j in 1:nb_port){
    temp_weights <- portf_compo(train_data, test_data, features, j) # Weights
    ind <- match(temp_weights$names, ticks) %>% na.omit() # Index: test vs all
    portf_weights[t,j,ind] <- temp_weights$weights # Allocate weights
    portf_returns[t,j] <- sum(temp_weights$weights * realized_returns) # Compute returns
  }
}
```

## [1] "2007-12-31"
## [1] "2008-12-31"
## [1] "2009-12-31"
## [1] "2010-12-31"
## [1] "2011-12-31"
## [1] "2012-12-31"
## [1] "2013-12-31"
## [1] "2014-12-31"
## [1] "2015-12-31"
## [1] "2016-12-31"
## [1] "2017-12-31"

对上述代码有两点重要评论。第一条评论涉及在开头定义的两个参数。它们分别指训练样本的大小（5年）和图 12.2 所示的缓冲期长度。这个**缓冲期是强制性的**，因为标签基于长期（12个月）回报。这种滞后是避免回测中任何前瞻性偏差的必要条件。

下面，我们创建一个计算周转率（权重变化）的函数。它需要权重值以及所有资产的回报率，因为再平衡前的权重取决于前一期分配的权重，以及持有期间改变这些原始权重的资产回报率。

```
turnover <- function(weights, asset_returns, t_oos){
  turn <- 0
  for(t in 2:length(t_oos)){
    realised_returns <- asset_returns %>% filter(date == t_oos[t]) %>% dplyr::select(-date)
    prior_weights <- weights[t-1,] * (1 + realised_returns) # Before rebalancing
    turn <- turn + apply(abs(weights[t,] - prior_weights/sum(prior_weights)),1,sum)
  }
  return(turn/(length(t_oos)-1))
}
```

定义周转率后，我们将其嵌入一个计算几个关键指标的函数中。

```
perf_met <- function(portf_returns, weights, asset_returns, t_oos){
  avg_ret <- mean(portf_returns, na.rm = T) # Arithmetic mean
  vol <- sd(portf_returns, na.rm = T) # Volatility
  Sharpe_ratio <- avg_ret / vol # Sharpe ratio
  VaR_5 <- quantile(portf_returns, 0.05) # Value-at-risk
  turn <- 0 # Initialisation of turnover
  for(t in 2:dim(weights)[1]){
    realized_returns <- asset_returns %>% filter(date == t_oos[t]) %>% dplyr::select(-date)
    prior_weights <- weights[t-1, ] * (1 + realized_returns)
    turn <- turn + apply(abs(weights[t, ] - prior_weights/sum(prior_weights)),1,sum)
  }
  turn <- turn/(length(t_oos)-1) # Average over time
  met <- data.frame(avg_ret, vol, Sharpe_ratio, VaR_5, turn) # Aggregation of all of this
  rownames(met) <- "metrics"
  return(met)
}
```

最后，我们构建一个循环处理各种策略的函数。

```
perf_met_multi <- function(portf_returns, weights, asset_returns, t_oos, strat_name){
J <- dim(weights)[2] # Number of strategies
met <- c() # Initialization of metrics
for(j in 1:J){ # One very ugly loop
  temp_met <- perf_met(portf_returns[, j], weights[, j, ], asset_returns, t_oos)
  met <- rbind(met, temp_met)
}
row.names(met) <- strat_name # Stores the name of the strat
return(met)
}
```

鉴于投资组合的权重和回报，还剩下计算资产回报，以将其插入汇总指标函数中。

```
asset_returns <- data_ml %>% # Compute return matrix: start from data
dplyr::select(date, stock_id, R1M_Usd) %>% # Keep 3 attributes
spread(key = stock_id, value = R1M_Usd) # Shape in matrix format
asset_returns[is.na(asset_returns)] <- 0 # Zero returns for missing points

met <- perf_met_multi(portf_returns = portf_returns, # Computes performance metrics
weights = portf_weights,
asset_returns = asset_returns,
t_oos = t_oos,
strat_name = c("EW", "XGB_SR"))
met # Displays perf metrics
```

| | 平均回报 | 波动率 | 夏普比率 | VaR_5 | 周转率 |
|---|---|---|---|---|---|
| EW | 0.009697248 | 0.05642917 | 0.1718481 | -0.07712509 | 0.0714512 |
| XGB_SR | 0.012602882 | 0.06376845 | 0.1976351 | -0.08335864 | 0.5679932 |

基于机器学习的策略最终表现良好！收益主要来自平均回报，而波动率高于基准。净效果是与基准相比夏普比率有所提高。提升幅度并不惊人，但（因此？）看起来合理。值得注意的是，复杂策略的周转率显著较高。在分子中扣除成本（例如，周转率的0.005倍，如Goto and Xu (2015)所示，这是一个保守数字）只会轻微降低基于机器学习的策略在夏普比率上的优势。

最后，绘制相应的投资组合价值总是很诱人，我们在图 12.3 中显示了两个相关图表。

```
library(lubridate) # Date management
library(cowplot) # Plot grid management
g1 <- tibble(date = t_oos,
benchmark = cumprod(1+portf_returns[,1]),
ml_based = cumprod(1+portf_returns[,2])) %>%
```

