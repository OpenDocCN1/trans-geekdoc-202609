

## 第 8 章 使用深度学习预测行为 257

```r
# Softmax function.
softmax <- function(scores)
  exp(scores) / sum(exp(scores))
}
probabilities <- softmax(scores)
print(probabilities)
# [1] 0.82196136 0.04216934 0.13586930
print(sum(probabilities)) # 总和应为 1。
# [1] 1
```

我们利用向量化能力在同一个函数内计算最终的概率向量，而不需要遍历每个元素。当使用 Keras 时，这些操作是由后端（例如 TensorFlow）高效计算的。

最后，第 3 点指出我们需要需要使用平均交叉熵（average cross-entropy）作为损失函数。现在我们已经将 $y'$ 转换为了概率，就可以计算它与 $y$ 之间的差异。两个概率向量 $(A,B)$ 之间的距离（差异）可以使用交叉熵来计算：

> $CE(A, B) = -\sum B_i log(A_i) \quad (8.17)$

因此，为了获取 $y'$ 和 $y$ 之间的差异，我们首先应用 $y'$（将其转换为概率概率），然后对生成的概率向量和 $y$ 计算交叉熵。

> $CE(softmax(y'), y). \quad (8.18)$

在 R语言中，可以通过以下代码实现：

```r
# Cross-entropy
CE <- function(A,B){
  sum(B * log(A))
}
y <- c(1, 0, 0)
```

```r
print(CE(softmax(scores), y))
# [1] 0.1960619
```

请注意，当使用公式 (8.17) 计算交叉熵时，顺序是重要的。第一个元素应该是预测得分 $y'$，第二个元素应该是真值独热编码（true-one encoded）向量 $y$。我们不希望对值为 0 的向量应用对数函数。在大多数情况下，预测得分 $y'$ 不等于 0，因此我们倾向于对它们应用对数函数。在预测得分出现 0 的极少数情况下，我们可以添加一个很小的数字。在实践中，这通常由后端（例如 TensorFlow）处理。

我们已经知道如何计算每个训练实例的交叉熵。总损失函数就是所有训练点上的平均交叉熵。下一节将展示如何使用 Keras 构建一个用于分类的神经网络。

### 8.3.1 肌电信号的分类

keras_electromyography.R

在这个示例中，我们将使用 Keras 训练一个神经网络，根据肌肉电活动对数据集中的手势进行分类。这里将使用 ELECTROMYOGRAPHY 数据集。电活动是通过作为手带的肌电图（EMG）传感器记录的。这些数据由 Yashunk (2019) 收集并提供。手带上有 8 个放置在皮肤表传感器，以 200 Hz 的采样率测量右前臂的电活动。可以在此处找到设备的视频：https://youtube.be/iu5-G6DPptkk

数据包含 4 种不同的手势：0-石头、1-剪刀、2-布、3-OK，共有 65 列。最后一列是从 0 到 3 的类别。前 64 列是电测量值。8 个传感器中的每个有 8 次连续读取。目标是使用前 64 个变量来预测类别。

脚本 keras_electromyography.R 包含了完整代码。我们首先将数据集划分为训练集（60%）、验证集（10%）和测试集（30%）。我们将验证验证监控每个 epoch 的性能。我们还需要对三个集合进行归一化，但仅从训练集中学习归一化参数。脚本包含的 `normalize()` 函数将完成工作。

我们需要做的之一是格式化数据矩阵并对类别进行独热编码（one-hot encode）。以下代码定义了一个输入数据框和特征、最后一列包含类别数的函数。它假设前几列是特征，最后一列是类别。首先，它将特征转换为矩阵并使用 Keras 的 `to_categorical()` 函数对其进行独热编码。类别存储在 y 中，函数返回一个包含特征和独热编码类别的列表。然后，我们可以对训练集、验证集和测试集调用该函数。

```r
# 定义一个格式化特征并对类别进行独热编码的函数。
format.to.array(data, numclasses = 4){
  x <- as.matrix(data, 1:(ncol(data)-1))
  y <- as.categorical(y, num_classes = numclasses)
  l <- list(x=x, y=y)
  return(l)
}
```

```r
# 格式化数据
trainset <- format.to.array(trainset, numclasses = 4)
valset <- format.to.array(valset, numclasses = 4)
testset <- format.to.array(testset, numclasses = 4)
```

