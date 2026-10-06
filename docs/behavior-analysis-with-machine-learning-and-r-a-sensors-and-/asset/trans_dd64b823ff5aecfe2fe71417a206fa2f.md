

# 第 1 章 引言

```r
# 用于存储 newdata 中
# 每个实例预测结果的变量。
predictions <- NULL

# 遍历 newdata 中的实例
for(i in 1:nrow(newdata)){
  instance <- newdata[i,]

  # 预测与中心性度量距离
  # 最近的类别的名称。
  pred <- names(which.min(abs(instance$speed - params)))

  predictions <- c(predictions, pred)

  return(predictions)
}
```

该函数遍历每一行，计算到每个中心性度量的距离，并返回最近的类别的名称。距离的计算通过以下行代码完成：

```r
pred <- names(which.min(abs(instance$speed - params)))
```

首先，它计算速度与存储在 `params` 中的的每个中心性度量之间的绝对差，并返回最小值项的名称。现在我们已经定义了训练和预测程序，可以准备好测试我们的分类器了！

在第 1.5 节中，介绍了两种评估方法。**留法（Hold-out）和 k 折交叉验证（k-fold cross-validation）。** 这些方法允许你估算模型在新数据上的表现。让我们先从**留法验证**开始。

首先，我们需要将数据划分为两个独立的集合。我们将使用 70% 的数据来训练分类器，剩余 30% 用于测试。以下代码将 `dataset` 划分为 `trainset` 和 `testset`。

```r
# 用作训练数据的百分比。
pctTrain <- 0.7
```

```r
# 设置种子以保证可复现性。
set.seed(123)
```

```r
idxs <- sample(dataset,
      size = nrow(dataset) * pctTrain,
      replace = FALSE)
```

```r
trainset <- dataset[idxs,]

testset <- dataset[-idxs]
```

`sample()` 函数用于从 1 到 n 随机选择整数，其中 n 是 `dataset` 中数据点的总数。这些随机选择的数据点将进入训练集。因此，通过 `size` 参数，我们告诉函数返回 70 个数字，对应于总数的 70%，因为 `dataset` 有 100 个实例。

> 最后一个参数 `replace` 设置为 `FALSE` 是因为我们不希望出现重复数字。这确保了任何实例只属于训练集或测试集。我们不希望一个实例被复制到两个集合中。

现在是时候测试我们的函数了。我们可以通过调用之前定义的函数 `simple.model.train()` 使用 `trainset` 来训练模型。

```r
# 使用 trainset 训练模型。
params <- simple.model.train(trainset, mean)
```

```r
# 打印学习到的参数。
#> tiger leopard
#> 48.88246 54.58369
```

训练模型后，我们打印学习到的参数。在这种情况下，老虎的平均值为 48.88，豹子为 54.58。有了这些参数，我们就可以在测试集上开始进行预测了！我们将测试集和新学习到的参数传递给函数 `simple.classifier.predict()`。

```r
# 在测试集上进行类别预测。
test.predictions <- simple.classifier.predict(testset, params)
```

```r
# 显示前几个预测结果。
head(test.predictions)
#> [1] "tiger" "tiger" "leopard" "tiger" "tiger" "leopard"
```

我们的 `predict` 函数返回测试集中每个实例的预测结果。我们可以使用 `head()` 函数打印前几个预测结果。前两个实例被归类为老虎，第三个归类为豹子，依此类推。

但这些预测结果如何？由于我们知道测试集中的真实类别（也称为地面值，ground truth），我们可以计算性能。在这种情况下，我们将计算准确率（accuracy），即正确分类的百分比。请注意，我们在进行预测时没有使用类别信息，只使用了速度。我们假装不知道真实类别。我们将使用使用真实类别来评估模型的性能。

```r
# 计算测试准确率。
sum(test.predictions == as.character(testset$class)) /
length(testset)
#> [1] 0.833333333
```

我们可以通过统计有多少个预测结果与真实类别相等，并将其除以测试集中数据点的总数来计算准确率。在这种情况下，测试准确率为 83.0%。恭喜你！你已经训练并评估了你的第一个分类器。在用于训练模型的同一个训练集上计算性能也是一个好主意。

```r
# 计算训练准确率。
train.predictions <- simple.classifier.predict(trainset, params)
sum(train.predictions == as.character(trainset$class)) /
length(trainset)
# [1] 0.8571429
```

训练准确率为 85.7%。如预期的，这比测试准确率高。通常，当你报告测试集上的性能时，可以使用训练集上的性能来寻找过拟合/欠拟合问题，这将在后续章节中介绍。

## 1.6 k 折交叉验证

现在让我们如何实现 k 折交叉验证来测试我们的分类器。我选择 k=5。这意味着将生成 5 个独立的集合并运行 5 次迭代。

```r
# 折数
k <- 5

# 设置随机种子
set.seed(123)

# 生成折数
folds <- sample(1:k, size = nrow(dataset), replace = TRUE)

# 打印每个折的样本数量。
table(folds)
)
```
*(注：原文此处代码块在输入时似乎不完整或存在截断，翻译根据上下文进行了逻辑对齐，但保持了 Markdown 结构)*

由于提供的原文在结尾处有截断或格式不全，我已根据逻辑翻译了所有可读部分。

