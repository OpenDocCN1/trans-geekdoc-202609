
生存预测概率
特征贡献

![](img/2c227bfb3620dc3d159fa5e6598afa30_310_0.png)

图 7.25: 所有插补数据集中 Jack 的生存预测概率（左）及其相应的基于 Shapley 的特征贡献（右）。

## 7.9.4 示例：类别不平衡（好、坏、丑）

如第 7.2.1 节所讨论，我们通常不想预测类别标签，而是想要属于某个特定类别的概率——后者的好处是能提供一定的不确定性指示（例如，如果我们预测 Jack 在泰坦尼克号航行中生存的概率为 15%，那么我们也估计他不生存的概率为 85%）。然而，有些模型对类别概率的估计可能很差。*校准*通过允许你更好地校准已拟合模型的概率，或为那些本身无法自然生成概率的模型提供估计概率（例如支持向量机）来解决这个问题。

校准是指观测概率与预测概率之间的一致程度，其效用在统计文献中已有充分讨论（即使不常被实践）；参见，例如，Rufibach [2010]、Austin and Steyerberg [2014] 以及 Niculescu-Mizil and Caruana [2005]——后者在更广泛的背景下讨论了校准，并包含关于校准随机森林（RFs）的一些讨论。一个校准良好的（二元）概率模型应产生准确的类别概率，例如，在接近 0.7 的概率估计中，大约 70% 实际上属于正类，以此类推。

除非树被生长到纯净，否则随机森林通常能产生一致且校准良好的概率 [Malley et al., 2012, Niculescu-Mizil and Caruana, 2005]，而提升树（第 8 章）则不能*。不过，我们很快就会看到，情况并非总是如此。此外，校准曲线在比较已拟合概率模型的性能时也很有用。

现实中的二元数据通常不平衡。例如，在建模贷款违约时，目标类别（贷款违约）往往代表性不足。这是可以预料的，因为我们希望大多数人在还清贷款过程中不会违约。然而，许多从业者将类别不平衡视为影响“准确性”的问题。实际上，问题通常在于数据是平衡的 [Matloff, 2017, p. 193]。

在本示例中，我将模拟一些不平衡数据。具体来说，我将使用隐变量模型将 Friedman 1 基准回归数据（第 1.4.3 节）转换为二元分类问题。基本上，我将观测响应值视为逻辑回归模型的线性预测器并将其转换为概率。然后，我们可以使用二项随机数生成器来模拟观测类别标签。关于这项模拟研究需要记住的重要一点是，我们可以获取真实的基础类别概率！

下面给出了一个简单函数，用于如上所述将 Friedman 1 回归问题转换为二元分类问题。（请注意，行 d$y <- d$y - 23 移动截距项并有效控制生成的 0/1 结果的平衡——此处选择它是为了获得大约 0.95/0.05 的 0/1 类别平衡。）

```
gen_binary <- function(...) {
  d <- treemisc::gen_friedman1(...) # regression data
  d$y <- d$y - 23 # shift intercept
  d$prob <- plogis(d$y) # inverse logit to obtain class probabilities
  #d$prob <- exp(d$y) / (1 + exp(d$y)) # same as above
  d$y <- rbinom(nrow(d), size = 1, prob = d$prob) # 0/1 outcomes
  d
}

# Generate samples
set.seed(1921) # for reproducibility
trn <- gen_binary(100000) # training data
tst <- gen_binary(100000) # test data
```

令 \(N = N_0 + N_1\) 为学习样本中的观测数量，其中 \(N_0\) 和 \(N_1\) 分别表示属于类别 0 和类别 1 的观测数量。如果学习样本是来自感兴趣总体的随机（即具有代表性）样本，那么我们可以使用 \(\pi_i = N_i/N\)（\(i = 1, 2\)）从数据中估计真实类别先验概率；这在 CART 类决策树的第 2.2.4 节中已讨论。有三种情景需要考虑：

- a) 数据构成具有代表性的样本，且观测类别频率反映了总体中的真实类别先验概率（**好**）；
- b) 类别频率已被人为平衡，但真实类别频率/先验概率已知（**坏**）；
- c) 类别频率已被人为平衡，且真实类别频率/先验概率未知（**丑**）。

在下面的代码块中，我使用大小为 \(N = 10^6\) 的独立样本来估计 \(\pi_1\)（即总体中类别 1 观测的*患病率*）：

```
(pi1 <- proportions(table(gen_binary(1000000)$y))["1"])
```

```
#> 1
#> 0.0498
```

接下来，我将定义一个简单的校准函数，可用于*等渗校准*；关于不同校准方法的简要概述，参见 Niculescu-Mizil and Caruana [2005]、Kull et al. [2017]。请注意，有许多 R 和 Python 库可用于校准；例如，R 包 **rms** [Harrell, Jr., 2021] 中的 `val.prob()` 以及 **sklearn.calibration** 模块。

```
isocal <- function(prob, y) { # isotonic calibration function
  ord <- order(prob)
  prob <- prob[ord] # put probabilities in increasing order
  y <- y[ord]
  prob.cal <- isoreg(prob, y)$yf # fitted values
  data.frame("original" = prob, "calibrated" = prob.cal)
}
```

首先，让我们在原始（即不平衡）学习样本上拟合一个默认随机森林。请注意，在指定模型公式时，我排除了 prob 列。

```
library(ranger)
# Fit a probability forest (omitting the prob column)
set.seed(1446) # for reproducibility
(rfo1 <- ranger(y ~ . - prob, data = trn, probability = TRUE,
                verbose = FALSE))
```

```
#> Ranger result
#>
#>
#> Call:
#> ranger(y ~ . - prob, data = trn, probability = TRUE, verbose = FA...
#>
#> Type:                         Probability estimation
#> Number of trees:             500
#> Sample size:                 100000
#> Number of independent variables: 10
#> Mtry:                          3
#> Target node size:              10
#> Variable importance mode:    none
#> Splitrule:                   gini
#> OOB prediction error (Brier score): 0.0256
```

OOB 预测误差（在此例中为 Brier 分数）为 0.026。测试数据上的 Brier 分数也可以计算，但既然我可以获取真实概率，不妨也将其与预测进行比较（为此，我将计算预测概率与真实概率之间的 MSE）。在此例中，我们看到测试集上的 Brier 分数与 OOB Brier 分数相当。

```
prob1 <- predict(rf01, data = tst)$predictions[, 2]
```

```
mean((prob1 - tst$y) ^ 2) # Brier score
```

```
#> [1] 0.0255
```

```
mean((prob1 - tst$prob) ^ 2) # MSE between predicted and true probs
```

```
#> [1] 0.00319
```

仅查看单一指标（或多个指标）无法呈现全貌，因此查看特定的可视化（如校准曲线）有助于进一步评估模型预测概率的准确性（提升图也可能有用）。图 7.26 中最左侧的图显示了测试集的实际 vs. 预测概率，以及上述随机森林的基于等渗的校准曲线。在此例中，随机森林在准确性方面似乎做得不错。该模型在 0.5 以下的概率上似乎校准良好，但在 0.5 以上的概率上似乎存在轻微负偏差，这是合理的，因为大部分概率质量集中在零附近（考虑到真实类别频率，我们本可能预料到这一点）。

为了天真地应对被认为的类别标签不平衡问题，学习样本通常会被人为重新平衡（例如，使用下采样），以便类别结果具有大致相同的分布。一般来说，这是一个糟糕的主意，对于概率模型，并且可能导致预测概率出现严重偏差——事实上，任何要求你删除好数据以优化性能的算法都是可疑的。尽管如此，有时数据在我们无法控制的预处理步骤中已被人为重新平衡，或者你可能决定下采样数据以减少计算时间（在这种情况下，你应该尝试保留原始类别频率，或至少将其存储以供以后调整）。无论如何，让我们看看当我们对多数类进行下采样时，我们的预测会发生什么变化。
