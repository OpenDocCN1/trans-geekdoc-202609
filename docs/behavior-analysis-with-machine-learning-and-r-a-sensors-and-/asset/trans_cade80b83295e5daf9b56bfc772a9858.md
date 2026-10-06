

## 第 9 章 多用户验证

```r
testset <- dataset[which(dataset$userid == user)],
trainset <- dataset[which(dataset$userid != user)],
```

```r
# 归化。其实不需要，因为 RF
# 不受不同特征尺度的影响。
res <- normalize(testset, testset)
testset <- res$train
testset <- res$test
```

```r
preds.rf <- as.character(rf, newdata = testset[-1])
groundTruth <- as.character(testset$label)
```

```r
cm.rf <- confusionMatrix(factor(preds.rf,
    levels = unique.actions),
    factor(groundTruth,
    levels = unique.actions))
```

```r
accuracies <- c(accuracies, cm.rf$overall["Accuracy"])
metrics <- colMeans(cm.rf$byClass,c("Recall",
    "Specificity",
    "Precision",
    "F1",
    na.rm = TRUE)
```

```r
recalls <- c(recalls, metrics["Recall"])
precisions <- c(precisions, metrics["Precision"])
}
```

现在我们打印跨用户的用户的平均性能指标。

## 第 9 章 多用户验证

```r
mean(accuracies)
# [1] 0.5807805
mean(recalls)
# [1] 0.5798611
mean(precisions)
# [1] 0.6539715
```

这些数字太令人惊讶了！在上一节中，我们的混合模型准确率为 92.7%，而现在用户无关的模型准确率仅为 58%！这是因为后者对目标用户一无所知。由于每个人都是不同的，用户无关模型无法捕捉新用户的模式，这对性能产生了巨大影响。

## 什么时候应该使用用户无关模型来验证系统？

- 1. 当你期望新用户可以直接开箱即用该系统，且该系统没有任何来自新用户的数据时。

用户无关模型的主要优势是它不需要目标用户的训练数据，因此他们可以立即开始使用，代价是准确率较低。

相反的情况是针对目标用户专门训练模型。这种模型被称为用户依赖模型，将在下一节介绍。

## 9.3 用户依赖模型

用户依赖模型使用仅属于目标用户的数据进行训练。通常情况下，与混合模型和用户无关模型相比，这类模型的性能更好。这是因为模型捕捉了特定用户的特殊性。评估用户依赖模型的方法是遍历每个用户，并为每个用户仅用其自己的数据构建并测试模型。例如，每个用户的评估可以使用 k 折交叉验证完成。对于骨骼数据库，每个动作有 4 个实例。与每个动作的实例数量相比，唯一类别的数量（27）也很大。如果我们执行例如 10 折交叉验证，训练集很可能不包含某些可能动作的示例。为了避免这种情况，我们将在每个用户内部进行留一验证（leave-one-out validation）。这意味着遍历每一个实例。在每次迭代中，该实例被用测试集，其余实例用于训练集。

## 第 9 章 多用户验证

unique.users <- as.character(unique(dataset$userid))

accuracies <- NULL; recalls <- NULL; precisions <- NULL

```r
set.seed(1234)
```

## 遍历每个用户。

```r
for(user in unique.users){
  print(paste0("Evaluating user ", user))
  user.data <- dataset[which(dataset$userid == user), -1]

  # 在每个用户内部进行留一交叉验证。

  predictions.rf <- NULL; GroundTruth <- NULL

  for(i in 1:nrow(user.data)){
    # 归化。其实不需要，因为 RF
    # 不受不同特征尺度的影响。
    testset <- user.data[i,]
    trainset <- user.data[-i,]
    res <- res$test
  }

  testset <- res$train
  trainset <- res$train

  rf <- RandomForest(label ~ ., trainset = trainset)
  preds.rf <- as.character(predict(rf, newdata = testset))

  predictions.rf <- c(predictions.rf, preds.rf)

  GroundTruth <- c(GroundTruth, as.character(testset$label))
}
```

```r
cm.rf <- confusionMatrix(factor(predictions.rf,
               levels = unique.actions),
               factor(groundTruth,
               levels = unique.actions))
```

```r
accuracies <- c(cm.rf$overall["Accuracy"])
metrics <- colMeans(cm.rf$byClass,c("Recall",
                               "Specificity",
                               "Precision",
                               "F1"),
                               na.rm = TRUE)
```

```r
recalls <- c(recalls, metrics["Recall"])

precisions <- c(precisions, metrics["Precision"])
} # 用户迭代结束
```

我们遍历了每个用户，并对每个用户执行了独立于其他的留一验证。我们现在可以计算平均性能。

```r
# 打印跨用户的平均值。
mean(accuracies)
# [1] 0.9431142
mean(recalls)
# [1] 0.9425154
mean(precisions)
# [1] 0.9500772
```

准确率、召回率和精确率高于用户无关模型。这是因为用户依赖模型能够捕捉特定用户的特殊性。

## 什么时候应该使用用户无关模型来验证系统？

## 第 9 章 多用户验证

- 1. 当你期望新用户可以直接开箱即用该系统，且该系统没有任何来自新用户的数据时。

用户无关模型的主要优势是它不需要目标用户的训练数据，因此他们可以立即开始使用，代价是准确率较低。

相反的情况是针对目标用户专门训练模型。这种模型被称为用户依赖模型，将在下一节介绍。

## 9.3 用户依赖模型

用户依赖模型使用仅属于目标用户的数据进行训练。通常情况下，与混合模型和用户无关模型相比，这类模型的性能更好。这是因为模型捕捉了特定用户的特殊性。评估用户依赖模型的方法是遍历每个用户，并为每个用户仅用其自己的数据构建并测试模型。例如，每个用户的评估可以使用 k 折交叉验证完成。对于骨骼数据库，每个动作有 4 个实例。与每个动作的实例数量相比，唯一类别的数量（27）也很大。如果我们执行例如 10 折交叉验证，训练集很可能不包含某些可能动作的示例。为了避免这种情况，我们将在每个用户内部进行留一验证。这意味着遍历每一个实例。在每次迭代中，该实例被用测试集，其余实例用于训练集。

