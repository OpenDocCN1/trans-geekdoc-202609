

## 5.1.5 软件

装袋法直接实现相当简单，如本章所示。尽管如此，存在多个可用于实现算法5.1的R包。R包ipred [Peters and Hothorn, 2021]（代表改进预测器）使用rpart包实现装袋决策树，并支持分类、回归和生存问题。R包adabag [Alfaro et al., 2018]也通过rpart实现装袋法，但仅支持分类问题。在Python中，装袋法在scikit-learn的sklearn.ensemble模块中实现，并可应用于任何基估计器（即，不仅限于决策树）。

一般来说，我认为使用随机森林软件来实现装袋法更高效，尤其是在R中。这是因为随机森林软件通常使用高效的编译代码构建整个集成模型，而例如ipred则利用现有的树软件，并以类似于我们在电子邮件垃圾邮件示例中所做的方式构建集成模型。第5.5节给出了使用随机森林软件实现装袋法的回归示例。随机森林是第7章的主题。

## 5.2 提升法

回顾一下，装袋法通过对多个不稳定学习器进行平均来降低方差。另一方面，提升法最初是为二元分类问题而设计的，作为提升弱学习器性能的一种方法——弱学习器是指仅比多数投票分类器好一点点的模型（即，始终预测学习样本中多数类的模型）。那么，提升法如何改善弱学习器的性能呢？基本思想非常直观：按顺序拟合模型，序列中的每个模型都在重新采样的训练数据上拟合，该数据对先前被误分类的观测赋予更多权重，从而“提升”先前模型的性能。提升序列中的每个后续模型实际上都会聚焦于先前模型出现最大错误的数据行。

存在多种不同的提升法变体，该过程自最初为二元分类而设计以来已有相当大的演变。在下一节中，我将讨论用于二元分类的最早和最流行的提升法变体之一：AdaBoost.M1 [Freund and Schapire, 1996]。需要指出的是，AdaBoost.M1及其许多变体假设基学习器（在我们的例子中，二元分类树）可以纳入案例权重。第8章将介绍一种更通用（且更灵活）的提升策略。

### 5.2.1 用于二元结果的AdaBoost.M1

AdaBoost.M1——在Friedman et al. [2000]中也被称为*离散AdaBoost*，因为基学习器各自返回一个离散类标签——拟合如下形式的加法模型

```
C(\boldsymbol{x}) = \text{sign} \left( \sum_{b=1}^B \alpha_b C_b(\boldsymbol{x}) \right)
```

其中，\(\{\alpha_b\}_{b=1}^B\) 是为每个相应基学习器 \(C_b(\boldsymbol{x})\) 的贡献加权的系数，以及

```
\text{sign}(x) = \begin{cases} +1 & \text{if } x > 0 \\ -1 & \text{if } x < 0 \\ 0 & \text{otherwise} \end{cases}
```

本质上，序列中准确率更高的分类器获得更多权重，因此对最终分类 \(C(\boldsymbol{x})\) 有更大影响。

AdaBoost.M1的详细内容见算法5.2。该思想的核心如下：首先使用等权重案例 \(\{w_i = 1/N\}_{i=1}^N\) 从训练数据构建初始分类器，然后增加那些最常被误分类的案例的 \(w_i\)。该过程重复固定次数（\(B\)）。

与装袋法一样，提升法是一种*元算法*，可应用于任何类型的模型，但它通常最成功地应用于浅层决策树（即，分割/终端节点相对较少的决策树）。虽然装袋法依赖于聚合多个不稳定学习器的结果，但提升法往往受益于按顺序改进弱学习器（如简单的决策树桩）的性能。在下一节中，我将编写算法5.2的代码，并将其应用于电子邮件垃圾邮件数据，以与先前获得的装袋树集成模型进行比较。

尽管AdaBoost.M1在当时是最准确的分类器之一\(^c\)，但它仅产生分类这一事实是一个严重的局限性。为此，Friedman et al. [2000]将AdaBoost.M1算法推广，使弱学习器返回类概率估计，而不是离散类标签；对最终分类器的贡献是该概率估计的logit变换的一半。他们将此过程称为Real AdaBoost。其他推广（例如，针对多类结果）也存在。在第8章中，我将讨论一种更灵活的提升变体，称为随机梯度树提升，它可以自然地处理一般结果类型（例如，连续型、二元型、泊松计数、删失等）。

\(^c\)事实上，在AdaBoost推出后不久，Leo Breiman就将其称为“……世界上最好的现成分类器。”

### 算法5.2 用于二元分类的基础版AdaBoost.M1算法。

- 1) 初始化案例权重 \(\{w_i = 1/N\}_{i=1}^N\)。
- 2) 对 \(b = 1, 2, \dots, B\)：
  - a) 使用案例权重 \(w_i\) 将分类器 \(C_b(\boldsymbol{x})\) 拟合到训练观测值。
  - b) 计算加权误分类错误
    \[
    err_b = \frac{\sum_{i=1}^N w_i I(y_i \neq C_b(\boldsymbol{x}))}{\sum_{i=1}^N}.
    \]
  - c) 计算 \(\alpha_b = \log(1/err_b - 1)\)。
  - d) 更新案例权重：\(\{w_i \leftarrow \exp[\alpha_b I(y_i \neq C_b(\boldsymbol{x}))]\}_{i=1}^N\)。
- 3) 返回加权多数投票：\(C(\boldsymbol{x}) = \text{sign}\left(\sum_{b=1}^B \alpha_b C_b(\boldsymbol{x})\right)\)

### 5.2.2 从零开始提升：对电子邮件垃圾邮件进行分类

为了说明，让我们将AdaBoost.M1（算法5.2）应用于电子邮件垃圾邮件数据，并展示它如何“提升”单个rpart树的性能；我将继续使用第5.1.2节中先前示例的相同训练/测试划分。对于本示例，我将使用 \(B = 500\) 个深度为10的决策树。由于AdaBoost.M1要求 \(y \in \{-1, +1\}\)，我将重新编码响应（type），使得 type = "spam" 对应于 \(y = +1\)：

```
spam.trn$type <- ifelse(spam.trn$type == "spam", 1, -1)
spam.tst$type <- ifelse(spam.tst$type == "spam", 1, -1)
spam.xtrn <- subset(spam.trn, select = -type)  # feature columns only
spam.xtst <- subset(spam.tst, select = -type)  # feature columns only
```

遵循之前关于装袋法的示例，我将使用简单的for循环和list()依次构建和存储拟合的树。

对于AdaBoost.M1，我们还需要收集和存储 \(\{\alpha_b\}_{b=1}^B\) 系数，以便稍后进行预测。请注意，`predict.rpart()` 返回一个因子——在此情况下，因子水平为 "-1" 和 "1"——在进一步处理之前需要将其强制转换为数值；下面代码中的 `fac2num()` 辅助函数正是为此目的⁴：

```
library(rpart)

# Helper function to coerce factors to numeric
fac2num <- function(x) as.numeric(as.character(x))

# Apply AdaBoost.M1 algorithm
B <- 500 # number of trees in ensemble
ctrl <- rpart.control(maxdepth = 10, xval = 0)
N <- nrow(spam.trn) # number of training observations
w <- rep(1 / N, times = N) # initialize weights
spam.ada <- vector("list", length = B) # to store sequence of trees
alpha <- numeric(B) # hold coefficients
for (i in seq_len(B)) { # for b = 1, 2, ..., B
  spam.ada[[i]] <- rpart(type ~ ., data = spam.trn, weights = w,
                         control = ctrl, method = "class")

  # Compute predictions and coerce factor output to +1/-1
  pred <- fac2num(predict(spam.ada[[i]], type = "class"))
  err <- sum(w * pred != spam.trn$type) / sum(w) # weighted error
  if (err == 0 | err == 1) { # to avoid log(0) and dividing by 0
    err <- (1 - err) * 1e-06 + err * 0.999999
  }
  alpha[i] <- log((1 / err) - 1) # coefficient from step 2) (c)
  w <- w * exp(alpha[i] * (pred != spam.trn$type)) # update weights
}
```

接下来，我将使用前 \(b\) 棵树（其中 \(b\) 将在范围 \(1, 2, \dots, B\) 上变化）对测试数据（`spam.tst`）生成预测，并计算每个的误分类错误；请注意，我使用的是之前装袋法示例中定义的相同 `err()` 函数：

```
spam.ada.preds <- sapply(seq_len(B), FUN = function(i) {
  class.labels <- predict(spam.ada[[i]], newdata = spam.tst,
                          type = "class")
  alpha[i] * fac2num(class.labels)
}) # (N x B) matrix of un-aggregated predictions

# Compute test error as a function of number of trees
spam.ada.err <- sapply(seq_len(B), FUN = function(b) {
  agg.pred <- apply(spam.ada.preds[, seq_len(b), drop = FALSE],
                    MARGIN = 1, FUN = function(x) sign(sum(x)))
  err(agg.pred, obs = spam.tst$type)
}
```

⁴根据[R FAQ指南](https://cran.r-project.org/doc/FAQ/)，一种更高效但更难记住的解决方案是使用 `as.numeric(levels(x))[as.integer(x)]`。

