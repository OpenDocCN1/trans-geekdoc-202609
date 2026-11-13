
layer_dense(units = 2, activation = 'softmax')        # Softmax for categ. output
main_output <- layer_concatenate(c(first_network,
                                   second_network,
                                   third_network))  %>%   # Combination
   layer_dense(units = 2, activation = 'softmax', name = 'main_output')
model_ens <- keras_model(
   inputs = c(first_input, second_input, third_input),
   outputs = c(main_output)
)

最后，我们可以训练和评估（参见图 18.12）。

```
summary(model_ens)                    # See model details / architecture
```

| 层 (类型) | 输出形状 | 参数数量 | 连接到 |
|---|---|---|---|
| first_input (InputLayer) | (None, 31) | 0 | |
| second_input (InputLayer) | (None, 31) | 0 | |
| third_input (InputLayer) | (None, 31) | 0 | |
| layer_1 (Dense) | (None, 8) | 256 | first_input[0][0] |
| layer_2 (Dense) | (None, 8) | 256 | second_input[0][0] |
| layer_3 (Dense) | (None, 8) | 256 | third_input[0][0] |
| dense_69 (Dense) | (None, 2) | 18 | layer_1[0][0] |
| dense_70 (Dense) | (None, 2) | 18 | layer_2[0][0] |
| dense_71 (Dense) | (None, 2) | 18 | layer_3[0][0] |
| concatenate_2 (Concatenate) | (None, 6) | 0 | dense_69[0][0]<br>dense_70[0][0]<br>dense_71[0][0] |
| main_output (Dense) | (None, 2) | 14 | concatenate_2[0][0] |

总参数: 836  
可训练参数: 836  
不可训练参数: 0

```
model_ens %>% compile(         # Learning parameters
   optimizer = optimizer_adam(),
   loss = "binary_crossentropy",
   metrics = "categorical_accuracy"
)
fit_NN_ens <- model_ens %>% fit(   # Learning function
   x = list(first_input = feat_train_1,
            second_input = feat_train_2,
            third_input = feat_train_3),
   y = list(main_output = NN_train_labels_C),  # Recycled from NN Chapter
   epochs = 12,                    # Nb rounds
   batch_size = 512,               # Nb obs. per round
   validation_data = list(list(feat_test_1, feat_test_2, feat_test_3),
                        NN_test_labels_C)
)
plot(fit_NN_ens)
```

![](img/8861a37f775d09b4ba7a5151f604d9f5_301_0.png)

图 18.12: 学习集成模型。

## 18.8 第 13 章

### 18.8.1 使用 tidyverse 的等权重投资组合

这个非常简单；它更简单、更紧凑，但在精神上与生成图 3.1 的代码相近。收益在图 18.13 中绘制。

```
data_ml %>%
  group_by(date) %>%  
  summarize(return = mean(R1M_Usd)) %>%  
  ggplot(aes(x = date, y = return)) + geom_point() + geom_line()
```

![](img/8861a37f775d09b4ba7a5151f604d9f5_302_0.png)

图 18.13: 收益时间序列。

### 18.8.2 高级加权函数

首先，我们使用所有输入来编写该函数。

```r
weights <- function(Sigma, mu, Lambda, lambda, k_D, k_R, w_old){
  N <- nrow(Sigma)
  M <- solve(Lambda*Sigma + 2*k_R*Lambda + 2*k_D*diag(N)) # Inverse matrix
  num <- 1-sum(M %*% (mu + 2*k_R*Lambda %*% w_old)) # eta numerator
  den <- sum(M %*% rep(1,N)) # eta denominator
  eta <- num / den # eta
  vec <- mu + eta * rep(1,N) + 2*k_R*Lambda %*% w_old # Vector in weight
  return(M %*% vec)
}
```

其次，我们在一些随机数据集上对其进行测试。我们使用第 1 章末尾创建并在第 5.2.2 节中用于 Lasso 分配的收益。对于 \mu，我们使用样本平均值，这在实践中很少是个好主意。这仅用于说明。

```r
Sigma <- returns %>% dplyr::select(-date) %>% as.matrix() %>% cov() # Covariance matrix
mu <- returns %>% dplyr::select(-date) %>% apply(2,mean) # Vector of exp. returns
Lambda <- diag(nrow(Sigma)) # Trans. Cost matrix
lambda <- 1 # Risk aversion
k_D <- 1
k_R <- 1
w_old <- rep(1, nrow(Sigma)) / nrow(Sigma) # Prev. weights: EW
weights(Sigma, mu, Lambda, lambda, k_D, k_R, w_old) %>% head() # First weights
```

```
## [,1]
## 1 0.0031339308
## 3 -0.0003243527
## 4 0.0011944677
## 7 0.0014194215
## 9 0.0015086240
## 11 -0.0005015207
```

某些权重当然可以为负。最后，我们使用 map2() 函数来测试一些敏感性。我们考察 3 个关键指标：

- **多样化**，我们通过加权平方和的倒数来衡量它（逆赫什曼-赫芬德尔指数）；
- **杠杆**，我们通过负权重的绝对值之和来评估它；
- **样本内波动率**，我们将其计算为 w'Σx

为此，我们在下面创建一个专用函数。

```
sensi <- function(lambda, k_D, Sigma, mu, Lambda, k_R, w_old){
  w <- weights(Sigma, mu, Lambda, lambda, k_D, k_R, w_old)
  out <- c()
  out$div <- 1/sum(w^2) # Diversification
  out$lev <- sum(abs(w[w<0])) # Leverage
  out$vol <- t(w) %*% Sigma %*% w # In-sample vol
  return(out)
}
```

我们不使用基准 map2 函数，而是依赖其一个版本，该版本将结果直接连接到数据框中。

```
lambda <- 10^(-3:2) # parameter values
k_D <- 2^10^(-3:2) # parameter values
pars <- expand.grid(lambda, k_D) # parameter grid
lambda <- pars$lambda
k_D <- pars$k_D

res <- map2_dfr(lambda, k_D, sensi,
                Sigma = Sigma, mu = mu, Lambda = Lambda, k_R = k_R, w_old = w_old)
bind_cols(lambda = as.factor(lambda), k_D = as.factor(k_D), res) %>%
  gather(key = indicator, value = value, -lambda, -k_D) %>%
  ggplot(aes(x = lambda, y = value, fill = k_D)) + geom_col(position = "dodge") +
  facet_grid(indicator ~ ., scales = "free")
```

在图 18.14 中，每个面板显示一个指标。在第一个面板中，我们看到多样化随着 k_D 的增加而增加：确实，随着该数值的增加，投资组合收敛到均匀（等权重）值。参数 λ 的影响较小。第二个面板自然显示了杠杆的逆效应：随着多样化随 k_D 的增加而增加，杠杆（即总负仓位—卖空）会减少。最后，最后一个面板显示样本内波动率主要由风险厌恶参数驱动。随着 λ 的增加，波动率逻辑上会降低。对于较小的 λ 值，k_D 与波动率呈负相关，但对于较大的 λ 值，模式会反转。这是因为等权重投资组合比高度杠杆化的均值-方差策略风险更低，但比最小方差投资组合风险更高。

### 18.8.3 回测中的函数式编程

通常，程序员更喜欢避免使用循环。为了在回测中避免循环，我们需要编写给定日期发生的情况。这在以下函数中被封装。为简单起见，我们仅针对一种策略对其进行编码。此外，该函数假设数据结构已知，但列（特征和标签）也可以作为参数传递。我们回收第 12 章中的函数 **weights_xgb**。

```
portf_map <- function(t, data_ml, ticks, t_oos, m_offset, train_size, weight_func){
  train_data <- data_ml %>% filter(date < t_oos[t] - m_offset * 30, # Roll. window w. buffer
                                   date > t_oos[t] - m_offset * 30 - 365 * train_size)
  test_data <- data_ml %>% filter(date == t_oos[t])   # Test set
  realized_returns <- test_data %>%                   # Computing returns via:
    dplyr::select(R1M_Usd)    # 1M holding period!
  temp_weights <- weight_fun(train_data, test_data, features)  # Weights = recycled!
  ind <- match(temp_weights$names, ticks) %>% na.omit() # Index of test assets
  x <- c()
  x$weights <- rep(0, length(ticks))                 # Empty weights
  x$weights[ind] <- temp_weights$weights             # Locate weights correctly
  x$Returns <- sum(temp_weights$weights * realized_returns) # Compute returns
  return(x)
}
```

接下来，我们将此函数与 map() 结合使用。我们只测试前 6 个日期：这可以减少计算时间。

```
back_test <- 1:3 %>%   # Test on the first 100 out-of-sample dates
  map(portf_map, data_ml = data_ml, ticks = ticks, t_oos = t_oos,
      m_offset = 1, train_size = 5, weight_fun = weights_xgb)
head(back_test[[1]]$weights)   # Sample weights
```

```
## [1] 0.001675042 0.000000000 0.000000000 0.001675042 0.000000000 0.001675042
```

```
back_test[[1]]$returns   # Return of first period
```

```
## [1] 0.0189129
```

backtest 的每个元素都是一个带有两个组件的列表：投资组合权重和收益。为了轻松访问数据，来自 reshape2 包的 melt 等函数很有用。

![](img/8861a37f775d09b4ba7a5151f604d9f5_304_0.png)
