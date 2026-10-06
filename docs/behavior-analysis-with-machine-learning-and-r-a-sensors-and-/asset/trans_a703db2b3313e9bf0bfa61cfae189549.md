

# 第2章：使用分类模型预测行为

![](img/91c149cc24c3e5af2971580c9dda9d8b_96_0.png)

图 2.24：三角形手势。

图 2.24 显示了三角形手势的原始加速度计数值（虚线）。实线显示了生成的幅值。这还将简化问题，因为我们现在只需通过使用幅值而不是其他 3 个轴，来处理 1 维序列。

手势存储在包含 x、y 和 z 记录的文本文件中。手势辅助 `hand_gestures_auxiliary.R` 脚本包含一些辅助函数用于对数据进行预处理。由于每个手势的序列长度不一，将它们存储为数据框（data frame）可能会出现问题，因为数据框的大小固固定。`gen.instances()` 函数处理文件并将所有手势作为列表返回。该函数还计算了幅值（公式 2.16）。以下代码（来自 `hand_gestures.R`）调用了 `gen.instances()` 函数并将结果存储在列表变量 `instances` 中。然后，我们选择前两个实例作为查询实例和参考实例。

```R
# 从文件格式化实例。
instances <- gen.instances("../data/hand_gestures/")

# 使用第一个实例作为查询。
query <- instances[[1]]

# 使用第二个实例作为参考。
ref <- instances[[2]]
```

`instances` 中的每个元素也是一个列表，存储了每个手势的类型和值（幅值）。

# 第2章：使用分类模型预测行为

```R
# 打印它们各自类别
print(query$type)
> [1] "1"
```

```R
print(ref$type)
> [1] "1"
```

在这里，前两个实例的类型均为 '1'。我们也可以打印幅值。

```R
# 打印值。
print(query$values)
> [1] 9.167477 9.291464 9.901090 ...
```

在这种情况下，两个类别都是 "1"。我们可以使用 `dtw()` 函数计算查询实例和参考实例之间的相似性，并绘制生成的对齐图。

```R
alignment <- dtw(query$values, ref$values, keep = TRUE)
```

```R
# 打印相似性（距离）
alignment$distance
> [1] 68.56493
```

```R
# 绘制结果。
plot(alignment, type="two", off=1, match.lty=2, match.indices=40,
main="DTW resulting alignment",
xlab="time", ylab="magnitude")
```

为了执行实际分类，我们将使用著名的 k = 1 的 k-nn 分类器。要对查询实例进行分类，我们需要计算它到训练集中其他每个实例的 DTW 距离，并根据最近的实例预测标签。我们将使用 10 折交叉验证来测试性能。由于计算所有 DTW 距离需要时间，我们预先计算所有对的距离并将它们存储在矩阵中。辅助函数正是执行此操作的 `matrix.distances()`。由于可能需要几分钟，我们保存了结果，这样就不需要再次等待了。

# DTW 结果对齐

![](img/91c149cc24c3e5af2971580c9dda9d8b_98_0.png)

图 2.25：生成的对齐结果。

```R
D <- matrix.distances(instances)

# 保存结果。
save(D, file="D.RData")
```

`matrix.distances()` 返回一个列表。第一个元素是带有手势类别的数组，第二个元素是实际的距离矩阵。对角线上的元素设置为 Inf（无穷大），以表示我们不想考虑手势与其自身之间的差异。

为了方便起见，该矩阵已经存储在本章代码目录的 `D.RData` 文件中。以下代码执行 10 折交叉验证并计算性能结果。

```R
# 加载 DTW 距离矩阵。
load("D.RData")
set.seed(1234)
k <- 10 # 折数。
```

```R
folds <- sample(k, size = length(D[[1]]), replace = T)
predictions <- NULL
groundTruth <- NULL

# 实现 k=1 的 k-nn。
for(i in 1:k){
  trainSet <- folds != i
  testSet <- folds == i
  train.labels <- D[[1]][trainSet]

  for(query in testSet){
    type <- D[[1]][query]
    distances <- D[[2]][query, trainSet]

    # 返回最近的。
    nn <- sort(distances, index = T)[1]
    pred <- train.labels[nn]
    predictions <- c(predictions, pred)
    groundTruth <- c(groundTruth, type)
  }
}
```
*(注：原文代码块此处似乎不完整，已根据逻辑补全翻译所需的结构，但严格遵循不翻译代码原则)*

由于原文提供的文本在循环结束处中断，以下是基于给定文本的后续翻译：

... `} ` 循环结束。

接下来的：`D[[2]][query, trainSet]` 获取查询与训练集中之间的预计算距离。

```R
# 计算性能。
```

由于在面对新问题时，你可能会被想要使用复杂的模型来尝试解决它。然后，你对你的复杂模型进行训练和评估。结果看起来不错，所以你认为已经完成了。然而，数据中存在底层问题，给出了模型性能良好的假象。此类问题的示例包括不平衡数据集、特征与类别之间没有相关性、特征包含的信息不足。**哑模型（Dummy models）**可以用于发现某些此类问题。哑模型在做出预测时使用或完全不使用信息（我们稍后会说明）。

# 2.6.1 最频繁类别分类器

正如其名，最频繁类别分类器总是预测训练集中出现频率最高的标签。这意味着该模型甚至不需要查看

