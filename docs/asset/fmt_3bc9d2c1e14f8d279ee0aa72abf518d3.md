
# 第 9 章. 多用户验证

| user | label | meanDist | meanDist2 | meanDist4 | meanDist5 |
|---|---|---|---|---|---|
| s1 | a1 | 0.6097688 | 0.3756211 | 0.1198043 | 0.4278449 |
| s1 | a1 | 0.6020220 | 0.3818757 | 0.1202754 | 0.4331604 |
| s1 | a1 | 0.6090497 | 0.3734572 | 0.1172473 | 0.4357061 |
| s1 | a1 | 0.6019118 | 0.3750044 | 0.1221976 | 0.4263992 |
| s2 | a1 | 0.5957769 | 0.3899177 | 0.1235468 | 0.4069602 |
| s2 | a1 | 0.5754769 | 0.3830953 | 0.1176922 | 0.4044389 |
| s2 | a1 | 0.5700144 | 0.3820956 | 0.1184156 | 0.4044889 |
| s3 | a1 | 0.5668930 | 0.3813664 | 0.1164518 | 0.4046452 |
| s3 | a1 | 0.5387300 | 0.3526935 | 0.0968490 | 0.4042495 |
| s3 | a1 | 0.5326996 | 0.3523692 | 0.0961034 | 0.4118078 |
| s3 | a1 | 0.5321588 | 0.3512221 | 0.1005066 | 0.4014457 |
| s3 | a1 | 0.5329170 | 0.3534518 | 0.1085026 | 0.4023599 |
| s4 | a1 | 0.5383501 | 0.3546611 | 0.1070678 | 0.3988599 |
| s4 | a1 | 0.5402464 | 0.3554707 | 0.1090228 | 0.3996810 |
| s4 | a1 | 0.5394108 | 0.3533431 | 0.1019983 | 0.3996607 |

图 9.3: 特征提取后骨架的前几行显示了前 4 个特征。

我们将每个动作（文件）表示为特征向量。同一个脚本还显示了从每个动作中提取特征向量的代码。为了提取特征，选择了骨架中的一个参考点，在本例中是脊柱（关节 3）。然后，对于每一帧，计算所有关节（排除参考点）与参考点之间的距离。最后，对于每个关节，计算所有时间帧的*平均值*、*最小值*和*最大值*。由于有 19 个关节（不包括脊柱），我们最终得到了 $19*3=57$ 个特征。图 9.3 显示了最终数据集的样子。仅显示了 57 个特征中的前 4 个特征以及用户 ID 和标签。

> 下述示例假设 `skeleton_actions/` 目录下已存在包含提取特征的 `dataset.csv`。要生成此文件，请运行脚本 `preprocess_skeleton_actions.R` 中的特征提取代码。

如果数据集处于合适的格式，我们就可以**训练我们的混合模型**。包含训练不同类型模型完整代码的脚本是 `classify_skeleton_actions.R`。该脚本使用了 `dataset.csv` 文件。

首先加载辅助函数，因为我们将使用 `normalize()` 函数对数据进行归一化。我们将使用随机森林进行分类，并使用 `caret` 包计算性能指标。

```r
source(file.path("."))
```

```r
# 包含提取提取特征的 csv 文件路径。
# preprocess_skeleton_actions.R 包含了
# 用于提取特征的代码。
filepath <- file.path(datasets_path,
    "skeleton_actions",
    "dataset.csv")
```

```r
# 加载数据集。
dataset <- read.csv(filepath, stringsAsFactors = T)
```

```r
# 提取唯一标签。
unique.actions <- as.character(dataset$label)
```

```r
# 打印唯一标签。
print(unique.actions)
# [1] "a1" "a10" "a11" "a12" "a13" "a14" "a15" "a16" "a17"
# [10] "a18" "a19" "a20" "a21" "a22" "a23" "a24" "a25"
# [19] "a26" "a27" "a23" "a4" "a5" "a6" "a8" "a9"
```

`unique.actions` 变量存储了所有动作的名称。我们需要定义因子对象的水平。我们生成了 10 折（folds）并定义了一些变量来存储性能指标，包括准确率、召回率和精确率。在每次迭代交叉验证中，我们将计算并存储这些性能指标。

```r
k <- 10 # 折数。
set.seed(1234)
folds <- sample(k,
```

## 用户无关模型

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

```r
mean(accuracies)
# [1] 0.5807805
mean(recalls)
# [1] 0.5798611
mean(precisions)
# [1] 0.6539715
```

这些数字太令人惊讶了！在上一节中，我们的混合模型准确率为 92.7%，而现在用户无关的模型准确率仅为 58%！这是因为后者对目标用户一无所知。由于每个人都是不同的，用户无关模型无法捕捉新用户的模式，这对性能产生了巨大影响。

### 什么时候应该使用用户无关模型来验证系统？

- 1. 当你期望新用户可以直接开箱即用该系统，且该系统没有任何来自新用户的数据时。

用户无关模型的主要优势是它不需要目标用户的训练数据，因此他们可以立即开始使用，代价是准确率较低。

相反的情况是针对目标用户专门训练模型。这种模型被称为用户依赖模型，将在下一节介绍。

## 9.3 用户依赖模型

用户依赖模型使用仅属于目标用户的数据进行训练。通常情况下，与混合模型和用户无关模型相比，这类模型的性能更好。这是因为模型捕捉了特定用户的特殊性。评估用户依赖模型的方法是遍历每个用户，并为每个用户仅用其自己的数据构建并测试模型。例如，每个用户的评估可以使用 k 折交叉验证完成。对于骨骼数据库，每个动作有 4 个实例。与每个动作的实例数量相比，唯一类别的数量（27）也很大。如果我们执行例如 10 折交叉验证，训练集很可能不包含某些可能动作的示例。为了避免这种情况，我们将在每个用户内部进行留一验证（leave-one-out validation）。这意味着遍历每一个实例。在每次迭代中，该实例被用测试集，其余实例用于训练集。

```r
unique.users <- as.character(unique(dataset$userid))
accuracies <- NULL; recalls <- NULL; precisions <- NULL
set.seed(1234)
```

### 遍历每个用户。

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

## 自适应模型

主要目标是利用目标用户的少量训练数据构建一个自适应模型。我们首先要做的是构建一个与用户无关的模型。也就是说，我们将选择其中一个用户作为目标用户。我们将使用其余用户（不包括目标用户）的数据训练一个用户无关的模型。然后，我们将对该模型应用迁移学习，使其自适应目标用户。

目标用户的数据将分为测试集和自适应集。测试集将用于评估模型的性能，自适应集将用于微调模型。自适应集用于模拟我们从目标用户那里获取了新数据。

完整代码位于脚本 `keras/adaptive_cnn.R` 中。首先，我们开始读取图像文件。每行对应一种活动。最后两列是用户 ID (`userid`) 和类别 (`class`)。前 300 列对应图像像素。每张图像的大小为 10 x 10 x 3（高、宽、深）。

```r
# 图像格式的智能手机活动路径。
filepath <- file.path(datasets_path,
"smartphone_activities",
"images.txt")
```

```r
# 读取数据。
df <- read.csv(filepath, stringsAsFactors = F)
```

```r
# 打乱行顺序。
set.seed(1234)
df <- df[sample(nrow(df)),]
```
