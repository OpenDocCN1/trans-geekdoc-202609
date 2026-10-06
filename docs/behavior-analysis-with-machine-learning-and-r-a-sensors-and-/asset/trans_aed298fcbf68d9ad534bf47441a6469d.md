

```r
# Get class names.
classes <- names(params$priors)
```

```r
# Get number of features.
features <- nrow(params$list.means.sds[1])
```

```r
# Iterate instances.
for(i in 1:n){
  query <- data[i],

  max.probability <- -Inf

  predicted.class <- ""

  # Find the class with highest probability.
  for(j in 1:nfeatures){

    # Get the prior probability for class c.
    accum.prob <- params$priors[c]

    # Iterate features.
    # Compute P(feature/class)
    tmp <- f(query[j],j],
      params$list.means.sds[[c]][j,1],
      params$list.means.sds[[c]][j,2]

    # Accumulate result.
    accum.prob <- accum.prob * tmp
  }

  if(accum.prob > max.probability){
    max.probability <- accum.prob
    predicted.class <- c
  }
}

```

```r
predictions <- c(predictions, predicted.class)
}
return(predictions)
}
```

该函数遍历每个实例并计算每个类别的后验概率，并将获得最高值的存储为预测。最后，它返回包含所有预测结果的列表。

我们准备好训练朴素贝叶斯分类器了。我们需要做的只是调用 `naive.bayes.train()` 函数并传入训练集。

```r
# Learn Naive Bayes parameters.
b.model <- naive.bayes.train(trainset)
```

学习到的参数存储在 `nb.model` 中，我们可以通过传递 `nb.model` 和测试集使用 `naive.bayes.predict()` 函数进行预测。

```r
# Make predictions.
predictions <- naive.bayes.predict(nb.model, testset)
```

然后，我们通过计算混淆矩阵来评估模型的性能。

```r
# Compute confusion matrix and other performance metrics.
groundTruth <- testset$class

cm <- confusionMatrix(as.factor(predictions), as.factor(groundTruth))
```

```r
# Print accuracy
cm$overall["Accuracy"]
# Accuracy
#> 0.7501538
```

# 第 2 章. 使用分类模型预测行为 73

```r
# Print overall metrics across classes.
colMeans(cm$byClass[,c("Recall", "Specificity", "Precision", "F1")])
```

```r
# Recall Specificity Precision F1
# 0.6621381 0.9423729 0.6468372 0.6433231
```

准确率为 75%。在上一节中，我们通过决策树获得了 78% 的准确率，这并不一定意味着决策树一定更好。此外，在上一节中我们使用了交叉验证，而这里我们使用了留出验证。

需要注意的一个重要点是，计算后验概率可能会导致数值精度的损失，特别是当特征很多时。这是因为需要相乘每个特征的似然概率（公式 2.13），而这些似然概率是非常小的数字。解决此问题的方法是使用对数。在 `naive.bayes.predict()` 中，我们可以将 `accum.prob <- params$priors[c]` 改为 `accum.prob <- log(params$priors[c])`，并将 `accum.prob <- accum.prob * tmp` 改为 `accum.prob <- accum.prob + log(tmp)`。如果你尝试这些更改，应该会得到与之前相同的结果。

![](img/91c149cc24c3e5af2971580c9dda9d8b_85_png)

这里有一个流行的 R 包 `e1071` 用于训练朴素贝叶斯分类器。

```r
#### Naive Bayes implementation from package e1071
library(e1071)
```

```r
# We need to convert the class into a factor.
trainset$class <- as.factor(trainset$class)
```

```r
nb.model2 <- naiveBayes(class ~ ., trainset)
```

```r
predictions2 <- predict(nb.model2, testset)
```

```r
cm2 <- confusionMatrix(as.factor(predictions2), as.factor(groundTruth))
```

# 第 2 章. 使用分类模型预测行为

```r
# Print accuracy
cm2$overall["Accuracy"]
#> Accuracy
#> 0.7501538
```

如你所见，结果与我们的实现是一致的！我们为了演示自己实现了，但建议使用经过测试的包。此外，该包支持分类变量。

## 2.5 动态时间规整 (Dynamic Time Warping)

![](img/91c149cc24c3e5af2971580c9dda9d8b_86_png)

在活动识别示例中，我们使用了提取的特征来训练分类器，而不是原始数据。这会导致时间信息的丢失。在之前的例子中，由于提取的特征能够保留足够的信息，我们可以以合理的准确率进行分类。但在某些情况下，保留时间信息是关重要的。例如，在手写签名识别中，需要检查签名是否匹配数据库中的某个签名。签名需要几乎完全匹配。如果我们将每个签名表示为特征向量，可能会发现两个签名看起来不同，但它们是相似的。例如，图 2.16 显示了四个数据集。它们看起来不同，但相关性为 0.86。为了避免这个潜在问题，我们也可以通过保持数据点的顺序将时间信息包含到模型中。同样，当我们读一个单词时，有时会强调不同的字母。图 2.17 显示了 "very good" 的两个版本。如果我们想比较两个序列，可以使用欧式距离。然而，如果两个序列没有对齐，结果可能是误导性的。

# 第 2 章. 使用分类模型预测行为

![](img/91c149cc24c3e5af2971580c9dda9d8b_87_png)

图 2.16：相关性为 0.86 的四个数据集。

![](img/91c149cc24c3e5af2971580c9dda9d8b_87_1_png)

图 2.17：句子之间的时间偏移。

为了处理时间序列中的“时间偏移”效应，可以使用动态时间规整 (Sakoe 等，1990)。DTW 是一种方法，它可以：

- 找到两个给定时间序列之间的最佳匹配。
- 计算序列之间的差异性。
- 找到一个序列到另一个序列的最优变形。

DTW 的另一个优势是时间序列不需要长度相同。假设我们有两个时间序列，一个查询序列 (*query*) 和一个参考序列 (*reference*) 需要比较：

# 第 2 章. 使用分类模型预测行为

# DTW 结果对齐

![](img/91c149cc24c3e5af2971580c9dda9d8b_88_0_png)

图 2.18：查询序列和参考序列之间的 DTW 对齐（实线为查询）。

> query = (2, 2, 2, 4, 3)
ref = (2, 2, 3, 2)

首先需要注意的是两个序列的长度不同。图 2.18 显示了包含两个序列的图。查询是实线。可以看到查询相对于参考序列似乎向右移动了一个位置。图还显示了应用 DTW 算法后的结果对齐（序列之间的虚线）。序列之间的结果距离为 3。接下来，我们将看到如何形式化该问题以及计算最终距离的步骤。如果你觉得数学符号有点难以理解，请不要担心。后面将有一个逐步逐步的示例，这有助于解释该方法的工作原理。

对齐两个序列的问题可以形式化如下 (Rabiner 和 Juang, 1993)。令 *X* 和 *Y* 为两个序列：

$X = (x_1, x_2, \dots, x_{T_x})$
$Y = (y_1, y_2, \dots, y_{T_y})$

$x_i$ 和 $y_i$ 是向量。在之前的例子中，由于序列是 1 维的，向量只有一个元素，但 DTW 也适用于多维序列。$T_x$ 和 $T_y$ 是序列的长度。

$d(i_x, i_y)$ 是向量 $x_i$ 和 $y_i$ 之间的*差异性*（距离）（例如欧式距离）。然后，$\phi_x$ 和 $\phi_y$ 是将 $i_x$ 和 $i_y$ 映射到公共轴 $k$ 的规整函数：

$i_x = \phi_x(k), k = 1, 2, \dots, T$
$i_y = \phi_y(k), k = 1, 2, \dots, T.$

两个序列之间的总差异性：

$d_{\phi}(X, Y) = \sum_{k=1}^{T} d(\phi_x(k), \phi_y(k))$

目标是找到使总差异最小化的规整函数 $\phi$：

$\min_{\phi} d_{\phi}(X, Y)$

可以通过动态规划高效求解。通常在解决此最小化问题时，会应用一些约束：

- **端点约束**。该约束确保序列的第一个和最后一个元素相互连接。

$\phi_x(1) = 1, \phi_y(1) = 1$
$\phi_x(T) = T_x, \phi_y(T) = T_y$

