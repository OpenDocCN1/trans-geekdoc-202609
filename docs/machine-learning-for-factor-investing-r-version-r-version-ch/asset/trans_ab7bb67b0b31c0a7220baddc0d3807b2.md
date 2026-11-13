
有几种方法可以分割训练数据，从而构建不同的训练样本子集。第一种二分法是在随机分割与确定性分割之间。随机分割很容易，只需固定目标样本大小即可。请注意，只要重叠程度不过大，训练样本可以相互重叠。因此，如果原始训练样本有 $I$ 个实例，而集成需要 $M$ 个模型，那么子样本大小 $\lceil I/M \rceil$ 可能过于保守，尤其是当训练样本不够大时。在这种情况下，$\lceil I/\sqrt{M} \rceil$ 可能是一个更好的替代方案。随机森林是基于随机训练样本构建的集成的一个示例。

确定性分割的一个优点是它们易于复现，且结果不依赖于随机种子。由于基于因子的训练样本的性质，第二种分割二分法是在时间和资产之间。在资产内部的分割很简单：每个模型在不同的股票集合上训练。请注意，集合的选择可以是随机的，也可以由某些基于因子的标准决定：规模、动量、市净率等。

日期分割需要做出其他决定：数据是分成大块（例如年份）且每个模型获得一块（可能代表一种特定的市场条件）？或者训练日期是分得更规律？例如，如果集成中有 12 个模型，每个模型可以在给定月份的数据上训练（例如，第一个模型用一月，第二个模型用二月，等等）。

下面，我们在四个不同年份上训练四个模型，以查看这是否有助于减少模型间的相关性。这个过程有点冗长，因为所有样本和模型都需要重新定义。我们首先创建四个训练样本。第三个模型在较小的特征子集上工作，因此样本较小。

```r
training_sample_2007 <- training_sample %>%
  filter(date > "2006-12-31", date < "2008-01-01")
training_sample_2009 <- training_sample %>%
  filter(date > "2008-12-31", date < "2010-01-01")
training_sample_2011 <- training_sample %>%
  dplyr::select(c("date", "features_short", "$R1M_Usd")) %>%
  filter(date > "2010-12-31", date < "2012-01-01")
training_sample_2013 <- training_sample %>%
  filter(date > "2012-12-31", date < "2014-01-01")
```

然后，我们进行模型训练。语法与前几章中使用的相同，这里没有新内容。我们从惩罚回归开始。在下面的所有预测中，原始测试样本用于所有模型。

```r
y_ens_2007 <- training_sample_2007$R1M_Usd           # Dep. var.
x_ens_2007 <- training_sample_2007 %>%               # Predictors
  dplyr::select(features) %>% as.matrix()
fit_ens_2007 <- glmnet(x_ens_2007, y_ens_2007, alpha = 0.1, lambda = 0.1)   # Model
err_ens_2007 <- predict(fit_ens_2007, x_penalized_test) - testing_sample$R1M_Usd # Pred. errs
```

接下来是随机森林。

```r
fit_ens_2009 <- randomForest(formula,
                             data = training_sample_2009,   # Same formula as for simple trees!
                             sampsize = 4000,              # Data source: 2011 training sample
                             replace = FALSE,              # Size of (random) sample for each tree
                             nodesize = 100,               # Is the sampling done with replacement?
                             ntree = 40,                   # Minimum size of terminal cluster
                             mtry = 30                     # Nb of random trees
                             # Nb of predictive variables for each tree
)
err_ens_2009 <- predict(fit_ens_2009, testing_sample) - testing_sample$R1M_Usd # Pred. errs
```

第三个模型是提升树。

```r
train_features_2011 <- training_sample_2011 %>%
  dplyr::select(features_short) %>% as.matrix()       # Independent variable
train_label_2011 <- training_sample_2011 %>%
  dplyr::select(R1M_Usd) %>% as.matrix()             # Dependent variable
train_matrix_2011 <- xgb.DMatrix(data = train_features_2011,
                                 label = train_label_2011)    # XGB format!
fit_ens_2011 <- xgb.train(data = train_matrix_2011,       # Data source
                          eta = 0.4,                    # Learning rate
                          objective = "reg:linear",     # Objective function
                          max_depth = 4,                # Maximum depth of trees
                          nrounds = 18                  # Number of trees used
                         )
err_ens_2011 <- predict(fit_ens_2011, xgb_test) - testing_sample$R1M_Usd # Prediction errors
```

最后，最后一个模型是一个简单的神经网络。

```r
NN_features_2013 <- dplyr::select(training_sample_2013, features) %>%   # Matrix format is important
                    as.matrix()
NN_labels_2013 <- training_sample_2013$R1M_Usd
model_ens_2013 <- keras_model_sequential()
model_ens_2013 %>%   # This defines the structure of the network, i.e. how layers are organized
  layer_dense(units = 16, activation = 'relu', input_shape = ncol(NN_features_2013)) %>%   #
  layer_dense(units = 8, activation = 'tanh') %>%   #
  layer_dense(units = 1)
model_ens_2013 %>% compile(   # Model specification
  loss = 'mean_squared_error',   # Loss function
  optimizer = optimizer_rmsprop(),   # Optimisation method (weight updating)
  metrics = c('mean_absolute_error')   # Output metric
)
model_ens_2013 %>% fit(NN_features_2013,   # Training features
                       NN_labels_2013,      # Training labels
                       epochs = 9, batch_size = 128   # Training parameters
                      )
err_ens_2013 <- predict(model_ens_2013, NN_test_features) - testing_sample$R1M_Usd
```

有了四个模型的误差，我们可以计算它们的相关性矩阵。

```r
E_subtraining <- tibble(err_ens_2007,
                       err_ens_2009,
                       err_ens_2011,
                       err_ens_2013)
cor(E_subtraining)
```

| | err_ens_2007 | err_ens_2009 | err_ens_2011 | err_ens_2013 |
|---|---|---|---|---|
| err_ens_2007 | 1.0000000 | 0.9610165 | 0.6460091 | 0.9990129 |
| err_ens_2009 | 0.9610165 | 1.0000000 | 0.6340258 | 0.9626267 |
| err_ens_2011 | 0.6460091 | 0.6340258 | 1.0000000 | 0.6457394 |
| err_ens_2013 | 0.9990129 | 0.9626267 | 0.6457394 | 1.0000000 |

结果总体令人失望。只有一个模型能够提取与其他模型有些不同的模式，导致整体相关性为 65%。神经网络（2013 年数据）和惩罚回归（2007 年）仍然高度相关。一个可能的解释是，这些模型主要捕捉噪声而非信号。

## 11.4 练习

构建一个由 3 个完全使用 Keras 训练的神经网络组成的集成模型。每个网络将三分之一的预测变量作为输入。这三个网络输出分类结果（是/否或买入/卖出）。上层网络将三个输出汇总为最终决策。在测试样本上评估其性能。使用函数式 API。

## 投资组合回测

在本节中，我们将介绍分析和比较投资策略时将使用的符号和框架。投资组合回测通常被视为寻找最佳策略（或至少是一个稳健盈利策略）的过程。当彻底进行时，这项可能漫长的努力可能会诱使外行将偶然事件误认为是稳健的策略。连续发表的两篇论文警告提防 **数据窥探的风险**，这与 _p_-hacking 有关。在这两种情况下，研究人员会对数据进行折腾，直到找到所需结果。

Fabozzi 和 de Prado（2018）承认，只有有效的策略才能公之于众，而至少有数千种策略经过测试。挑选令人满意的异常值（似乎唯一有效的策略）在切换到实盘交易时可能会导致失望。同样，Arnott 等人（2019b）提供了一份任何分析师在回测策略时应遵循的原则和保障措施清单，以避免任何类型的错误。最糟糕的类型可以说是 **假阳性**，即策略（通常通过挑选样本）被发现在某个非常特定的环境下优于大盘，但在实际实施中很可能会失败。

除了这些关于投资组合构建的建议外，Arnott 等人（2019a）还警告不要盲目投资与学术因素相关的智能贝塔产品。显然，期望不应设定得过高，否则可能会面临失望的风险。他们文章的另一个要点是：**经济周期**对因子回报有强烈影响：相关性变化迅速，在重大下跌期间回撤可能会被放大。

回测比表面看起来更复杂，很容易犯一些小错误，从而导致 *表面上* 良好的投资组合策略。本章为这项练习提出了一种严谨的方法，讨论了一些注意事项，并提出了一个详细的示例。

### 12.1 设定协议

我们考虑一个具有三个维度的数据集：时间 \(t = 1, ..., T\)、资产 \(n = 1, ..., N\) 和特征 \(k = 1, ..., K\)。这些属性中必须有一个是资产 \(n\) 在时间 \(t\) 的价格，我们将其表示为 \(p_{t,n}\)。由此，算术回报的计算很简单（\(r_{t,n} = p_{t,n}/p_{t-1,n} - 1\)），任何启发式盈利度量也是如此。为简单起见，我们假设时间点是等距或均匀的，即 \(t\) 例如是交易日或月份的索引。如果每个时间点 \(t\) 都有所有资产的数据，那么这就构成了一个包含 \(I = T \times N\) 行的数据集。

数据集首先分为两部分：样本外期间和 **初始缓冲** 期间。缓冲期用于为第一个投资组合构建训练模型。此期间
