

$s(\boldsymbol{x}, N) = 2^{-\frac{1}{B} \sum_{b=1}^B h_b(\boldsymbol{x}) / c(N)},$ (7.9)

其中 \(N\) 是样本大小，\(h_b(\boldsymbol{x})\) 是第 \(b\) 棵树中到 \(\boldsymbol{x}\) 的路径长度，\(c(N)\) 是 *未成功搜索的平均路径长度*；在由 \(N\) 个观测值构建的二叉树中，\(c(N)\) 由以下公式给出

\(c(N) = 2H(N-1) - 2(N-1)/N,\)

其中 \(H(i)\) 是第 \(i\) 个 *调和数* (https://mathworld.wolfram.com/HarmonicNumber.html).

令 \(\bar{h}(\boldsymbol{x}) = \frac{1}{B} \sum_{b=1}^B h_b(\boldsymbol{x})\) 为实例 \(\boldsymbol{x}\) 在森林中所有树上的平均路径长度，并注意 \(0 < s(\boldsymbol{x}, N) \le 1\) 且 \(0 < \bar{h}(\boldsymbol{x}) \le N - 1\)。关于 (7.9) 的一些有用关系值得注意：

- \(s(\boldsymbol{x}, N) \to 0.5\) as \(\bar{h}(\boldsymbol{x}) \to c(N)\);
- \(s(\boldsymbol{x}, N) \to 1\) as \(\bar{h}(\boldsymbol{x}) \to 0\);
- \(s(\boldsymbol{x}, N) \to 0\) as \(\bar{h}(\boldsymbol{x}) \to N - 1\).

由于假设异常点更容易被隔离，因此它们的平均路径长度通常较短。因此，任何 \(s(\boldsymbol{x}, N)\) 值接近 1 的实例 \(\boldsymbol{x}\) 往往是高度异常的。如果 \(s(\boldsymbol{x}, N)\) 远小于 0.5，则可以安全地将 \(\boldsymbol{x}\) 视为“正常”实例。如果所有实例返回的值都接近 0.5，则可以安全地说样本中实际上不包含任何异常。请注意，这些只是指导原则。

隔离森林是检测潜在离群点和异常的一种表现优异的无监督方法 [Domingues et al., 2018]。与其他离群点检测算法相比，隔离森林具有可扩展性（例如，计算和内存需求相对较少），完全非参数化，且不需要类似距离的矩阵。LinkedIn 的反滥用 AI 团队使用隔离森林来帮助检测 LinkedIn 上的滥用行为（例如，虚假账户、账户接管和个人资料抓取）[Verbus, 2019]。

让我们用一个简单的模拟示例来说明总体思路。考虑图 7.17（左）中的数据。这里，点 \(\{(x_{1i}, x_{2i})\}_{i=1}^{2000}\) 独立地从标准正态分布中采样。然而，我将第一个观测值更改为 \((x_{11}, x_{21}) = (5.5, 5.5)\)（紫色点），与样本的其余部分相比，这相当异常。

图 7.17（右）显示了隔离森林中的一棵 IsoTree，以及 \(\boldsymbol{x}\) 所走的路径（紫色）。这里 \(\boldsymbol{x}\) 的路径长度为 2，你可以看到 \(\boldsymbol{x}\) 在树中走的路径相对比大多数其他可用路径都要短。

![](img/2c227bfb3620dc3d159fa5e6598afa30_287_0.png)

图 7.17：隔离树示例。左：来自标准正态分布的两个独立样本的散点图；坐标为 (5.5, 5.5) 的观测值是一个明显的异常。右：隔离树图；隔离紫色点的分支也以紫色突出显示。

### 7.8.5.1 扩展隔离森林

*扩展隔离森林* [Hariiri et al., 2021] 通过使用随机斜分割（在此情况下为具有随机斜率的超平面），而非轴对齐分割，提高了标准隔离森林产生的异常分数的一致性和可靠性——这通常会带来更好的异常分数。图 7.17 中的树来自使用 **eif** 包 [Hariiri et al., 2021] 拟合的扩展隔离森林，该包也可在 R 中使用。

### 7.8.5.2 示例：检测信用卡欺诈

为了说明隔离森林的基本用法，我将使用 Kaggle¹ 上的一个数据集，其中包含匿名的信用卡交易，标记为欺诈或真实，这些交易是在 2013 年 9 月的 48 小时内获得的；数据可以从 Kaggle 下载，网址为

https://www.kaggle.com/mlg-ulb/creditcardfraud.

识别欺诈性信用卡交易是信用卡公司的一项重要任务，以确保客户不会为其未购买的商品付款。由于欺诈交易相对较少（如人们所希望的那样），数据高度不平衡，在 N = 284,807 笔交易中有 492 笔欺诈（0.17%）。

出于保密原因，原始特征已使用 PCA 进行了转换，得到 28 个数值特征，标记为 V1、V2、...、V28。还有两个额外变量可用：Time（每笔交易与数据集中第一笔交易之间经过的秒数）和 Amount（交易金额）。这些是带标签的数据，二元结果 Class 取值为 0 或 1，其中 1 表示欺诈交易。虽然这当然可以被视为一个监督学习问题，但我将仅使用类标签来衡量我们基于隔离森林的异常检测的性能，该检测将是无监督的。我认为，你更可能面临这种性质的未标记数据，因为在大型数据库中准确标记每笔交易相当具有挑战性。

首先，我将把数据分为训练/测试样本，仅使用 N = 10,000 个观测值（3.51%）进行训练；其余 274,807 个观测值（96.49%）将用作测试集。不过，在这样做之前，我将打乱行，以确保它们首先是随机顺序的。（假设我已经将数据读入名为 ccfraud 的数据框中。）

```
# ccfraud <- data.table::fread("some/path/to/ccfraud.csv")

# Randomly permute rows
set.seed(2117) # for reproducibility
ccfraud <- ccfraud[sample(nrow(ccfraud)), ]

# Split data into train/test sets
set.seed(2013) # for reproducibility
trn.id <- sample(nrow(ccfraud), size = 10000, replace = FALSE)
ccfraud.trn <- ccfraud[trn.id, ]
ccfraud.tst <- ccfraud[-trn.id, ]

# Check class distribution in each
proportions(table(ccfraud.trn$Class))
proportions(table(ccfraud.tst$Class))

#>
#> 0 1
#> 0.9982 0.0018
#>
#> 0 1
#> 0.99828 0.00172
```

接下来，我将使用 isotree 包 [Cortes, 2022] 在训练集上拟合默认隔离森林，并为测试集提供异常分数。（注意我如何在构建隔离森林时排除真实类标签（第 31 列）！）

```
library(isotree)

# Fit a default isolation forest
ccfraud.info <- isolation.forest(ccfraud.trn[, -31], nthreads = 1,
                                 seed = 2223)

# Compute anomaly scores for the test observations
head(scores <- predict(ccfraud.info, newdata = ccfraud.tst))

#>   1   2   3   4   5   6
#> 0.320 0.341 0.324 0.325 0.340 0.325
```

虽然这不一定是一个分类问题，但我们可以将异常分数视为概率并构建信息图形。虽然精确率-召回率（PR）曲线$^k$在此可能有用，但我认为简单的累积提升图$^l$会更有信息量。下面我将两者都计算出来；参见图 7.18。

例如，查看提升图时，我们可以看到，如果审计测试集中得分最高的 5% 交易，那么我们将发现大约 87% 的欺诈案例。

PR 曲线看起来不太好，正如你查看提升图后可能预期的那样。例如，尽管我们只查看测试样本的 5% 就能识别大约 87% 的欺诈交易，但这仍然留下了 1300 多笔非欺诈交易也需要审计。在这个示例中，似乎我们无法在不接受大量假阳性的情况下检测出大多数欺诈行为。

```
#cutoff <- sort(unique(scores))
# Compute precision and recall across various cutoffs
cutoff <- seq(from = min(scores), to = max(scores), length = 999)
cutoff <- c(0, cutoff)
precision <- recall <- numeric(length(cutoff))
for (i in seq_along(cutoff)) {
  yhat <- ifelse(scores >= cutoff[i], 1, 0)
  tp <- sum(yhat == 1 & ccfraud.tst$Class == 1) # true positives
  tn <- sum(yhat == 0 & ccfraud.tst$Class == 0) # true negatives
  fp <- sum(yhat == 1 & ccfraud.tst$Class == 0) # false positives
  fn <- sum(yhat == 0 & ccfraud.tst$Class == 1) # false negatives
  precision[i] <- tp / (tp + fp) # precision (or PPV)
  recall[i] <- tp / (tp + fn) # recall (or sensitivity)
}
precision <- c(precision, 0)
recall <- c(recall, 0)
```

$^k$精确率（或阳性预测值）与阳性结果的患病率成正比。PR 曲线不适用于病例对照研究（例如，也包括病例对照采样——如下采样——用于不平衡数据集），并且只有在真实类先验概率在数据中得到反映时才应使用。

$^l$累积增益（或提升）图显示通过针对总案例数的一定百分比而“获得”的给定类别中总案例数的比例。

