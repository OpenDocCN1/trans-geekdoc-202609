

\(\lambda\) 的最优值可通过交叉验证或独立测试集来选择。

请注意，并非所有集成模型在后处理后都能表现良好。如 Hastie et al. [2009, 第 16.3.1 节] 所述，单个树模型应在需要时覆盖预测变量空间，并且彼此之间应足够不同，以使后处理器发挥作用。Friedman and Popescu [2003] 为不同的树集成模型提供了策略（例如，在不放回抽样时使用较小的子样本，如 5–10%，以及用于装袋树集成模型的较浅树）。下一个示例展示了如何使用 Ames 房价数据（第 1.4.7 节）将此后处理策略应用于装袋树集成模型。

### 5.5.1 示例：对装袋树集成模型进行后处理

为示例说明，让我们回到 Ames 房价示例。下面，我将把数据加载到 R 中，并应用与前一个示例相同的 70/30 划分。请注意，我继续通过除以 1000 来重新缩放 Sale_Price；这仅用于绘图目的。

```r
ames <- as.data.frame(AmesHousing::make_ames())
ames$Sale_Price <- ames$Sale_Price / 1000 # rescale response
set.seed(2101) # for reproducibility
id <- sample.int(nrow(ames), size = floor(0.7 * nrow(ames)))
ames.trn <- ames[id, ] # training data/learning sample
ames.tst <- ames[-id, ] # test data
ames.tst <- subset(ames.tst, select = -Sale_Price) # features only
```

接下来，我将使用 **randomForest** 包 [Breiman et al., 2018] 拟合一个装袋树集成模型（这样做的计算原因在第 5.1.5 节中讨论）。随机森林及其开源实现将在第 7 章中讨论。目前，只需注意，**randomForest** 包等可以通过调整一个特殊参数（通常称为 \(m_{try}\)，将在第 7.2 节中讨论）来实现装袋树集成模型，并将该参数设置为预测变量总数，即可得到普通装袋树集成模型。这比依赖 **ipred** 包要高效得多，并且还允许我们从单个树模型中获得预测，而不仅仅是聚合预测。对 RF 和提升树集成模型进行后处理的示例分别载于第 7.9.2 节和第 8.9.3 节。

这里，我将拟合两个模型，每个模型包含 \(B = 500\) 棵树：

- 一个标准装袋树集成模型，其中每棵树都完全生长到大小为 \(N\) 的自助样本（**ames.bag**）；
- 一个由浅层六节点树组成的装袋树集成模型，每棵树仅使用训练数据的 5% 随机样本（不放回）生长（ames.bag.6.5）。

两个模型均在下面的代码块中训练。请注意，我使用 system.time() 记录了每次拟合的训练时间，这将提供关于此后处理方法可能带来的计算节省的一些洞察。虽然准确性显著较低（参见图 5.6），但请注意训练 ames.bag.6.5 快得多：

```r
library(randomForest)
```

```r
# Fit a typical bagged tree ensemble
system.time({
set.seed(942) # for reproducibility
ames.bag <-
randomForest(Sale_Price ~ ., data = ames.trn, mtry = 80,
ntree = 500, xtest = ames.xtst,
test = ames.tst$Sale_Price, keep.forest = TRUE)
})
```

```
#> user system elapsed
#> 120.407 0.788 123.070
```

```r
# Print results
print(ames.bag)
```

```
#>
#> Call:
#> randomForest(formula = Sale_Price ~ ., data = ames.trn, mtry = 80...
#> Type of random forest: regression
#> Number of trees: 500
#>
#> No. of variables tried at each split: 80
#>
#> Mean of squared residuals: 690
#> % Var explained: 89
#> Test set MSE: 628
#> % Var explained: 90.6
```

```r
# Fit a bagged tree ensemble using six-node trees on 5% samples
system.time({
set.seed(1021)
ames.bag.6.5 <-
randomForest(Sale_Price ~ ., data = ames.trn, mtry = 80,
ntree = 500, maxnodes = 6,
sampsize = floor(0.05 * nrow(ames.trn)),
replace = FALSE, keep.forest = TRUE,
test = ames.xtst, ytest = ames.tst$Sale_Price)
})
```

请注意，在 R 中对表达式进行基准测试和计时有更好的方法；例如，参见 microbenchmark 包 [Mersmann, 2021]。

```
#> user system elapsed
#> 0.395 0.003 0.402
# Print results
print(ames.bag.6.5)
#>
#> Call:
#> randomForest(formula = Sale_Price ~ ., data = ames.trn, mtry = 80...
#> Type of random forest: regression
#> Number of trees: 500
#> No. of variables tried at each split: 80
#>
#> Mean of squared residuals: 1489
#> % Var explained: 76.2
#> Test set MSE: 1450
#> % Var explained: 78.2
```

接下来，我将使用 `glmnet` 对每个集成模型使用 LASSO 进行后处理。以下步骤由 `treemisc` 的 `isle_post()` 函数方便地处理，我将使用它来对 `ames.bag.6.5` 集成模型进行后处理。但首先，我认为使用 `ames.bag` 集成模型展示各个步骤是明智的。

首先，我将计算训练集和测试集的单个树模型预测，并将它们存储在一个矩阵中

```r
preds.trn <- predict(ames.bag, newdata = ames.trn,
                     predict.all = TRUE)$individual
preds.tst <- predict(ames.bag, newdata = ames.tst,
                     predict.all = TRUE)$individual
```

接下来，我将使用 `glmnet()` 函数使用 \(B = 500\) 棵单个树模型的训练预测来拟合整个正则化路径：

```r
library(glmnet)
```

```r
# Fit the LASSO regularization path
lasso.ames.bag <- glmnet(
  x = preds.trn, # individual tree predictions are the predictors
  y = ames.trn$Sale_Price, # same response variable
  lower.limits = 0, # coefficients should be strictly positive
  standardize = FALSE, # no need to standardize
  family = "gaussian" # least squares regression
)
```

关于上面的代码块，有几点需要说明。由于这是一个回归问题，我在调用 `glmnet()` 时设置了 `family = "gaussian"`（用于最小二乘法）。其次，由于单个树模型的预测都在同一尺度上，无需对输入进行标准化（`standardize = FALSE`）。最后，我们可以认为估计系数（每棵树一个）应该是非负的（`lower.limits = 0`）。

图 5.5 显示了估计系数的正则化路径。具体来说，\(\lambda\) 值（在对数尺度上）绘制在 \(x\)-轴上，\(y\)-轴对应估计系数值（每个系数/树一条曲线）。顶部轴突出显示了惩罚参数 \(\lambda\) 的每个特定值处的非零系数数量：

![](img/2c227bfb3620dc3d159fa5e6598afa30_216_0.png)

图 5.5：`ames.bag.6.5` 集成模型的 LASSO 系数剖面，随正则化参数 \(\lambda\) 的变化而变化。顶部轴指示特定 \(\lambda\) 值（在对数尺度上绘制）处的非零系数数量。

从这里开始，我们使用交叉验证或独立测试集来选择惩罚参数 \(\lambda\) 的合理值。这可以使用 `glmnet` 的 `assess.glmnet()` 函数轻松完成，使用测试集预测，如下所示（详情见 `?glmnet::assess.glmnet`）：

```r
# Assess performance of fit using an independent test set
perf <- assess.glmnet(
  object = lasso.ames.bag, # fitted LASSO model
  newx = preds.tst, # test predictions from individual trees
  newy = ames.tst$Sale_Price, #same response variable (test set)
  family = "gaussian" # for MSE and MAE metrics
)
perf <- do.call(cbind, args = perf) # bind results into matrix
```

```r
# List of results
ames.bag.post <- as.data.frame(cbind(
  "ntree" = lasso.ames.bag$df, perf,
  "lambda" = lasso.ames.bag$lambda)
)
```

```r
# Sort in ascending order of number of trees
head(ames.bag.post <- ames.bag.post[order(ames.bag.post$ntree), ])
```

```
#>   ntree mse mae lambda
#> s0   0 6658 59.6 6164
#> s1   4 5672 55.0 5616
#> s2   5 4851 50.7 5117
#> s3   8 4163 46.8 4663
#> s4   9 3592 43.3 4248
#> s5  10 3114 40.1 3871
```

```r
# Print results corresponding to smallest test MSE
ames.bag.post[which.min(ames.bag.post$mse), ]
```

```
#>   ntree mse mae lambda
#> s93  97 612 15.9 1.08
```

根据测试 MSE，惩罚参数 \(\lambda\) 的最优值为 1.077，对应 LASSO 模型中的 97 棵树或非零系数（相比原始的 500 棵有显著减少）。

在下一个代码块中，我将对 `ames.bag.6.5` 集成模型遵循完全相同的过程，但改用 `isle_post()` 函数：

```r
library(treemisc)
```

```r
# Post-process ames.bag.6.5 ensemble
preds.trn.6.5 <- predict(ames.bag.6.5, newdata = ames.trn,
  predict.all = TRUE)$individual
preds.tst.6.5 <- predict(ames.bag.6.5, newdata = ames.tst,
  predict.all = TRUE)$individual
ames.bag.6.5.post <-
  isle_post(preds.trn.6.5, y = ames.trn$Sale_Price,
            family = "gaussian", newX = preds.tst.6.5,
            newy = ames.tst$Sale_Price)
```

每个集成模型的总体结果如图 5.6 所示。这里，我展示了 MSE 作为每个模型树木数量（或 LASSO 中非零系数数量）的函数。在此示例中，更简单的 `ames.bag.6.5` 集成模型从后处理中获益显著，在 MSE 方面似乎与普通装袋树集成模型（`ames.bag`）不相上下，而只需要少量树木，训练速度快几个数量级！原始集成模型（`ames.bag`）从后处理中获得的改进远不如此。

