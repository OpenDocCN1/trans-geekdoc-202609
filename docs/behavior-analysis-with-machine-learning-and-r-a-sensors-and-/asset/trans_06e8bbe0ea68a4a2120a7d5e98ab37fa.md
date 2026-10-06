

# 第 3 章：使用集成学习预测行为

新的训练集 D'

![](img/91c149cc24c3e5af2971580c9dda9d8b_122_0.png)

图 3.5：通过对第一层学习器的预测进行列绑定并添加真实标签，为元学习器生成新训练集 D' 的过程。

在下一节中，我将介绍多视图堆叠（Multi-view Stacking），它与泛化堆叠（Generalized Stacking）相同，但每个第一层学习器使用来自不同视图的特征进行训练。

## 3.4 用于家庭任务识别的多视图堆叠

```
stacking_algorithms.R stacking_activities.R
```

多视图学习指的是实例可以通过两个或多个独立的“视图”来表征的情况。例如，可以从网页的文本提取网页分类的特征，也可以从指向该网页的链接中提取。通常，假设这些视图是独立的，且每个视图都足以解决问题。那么，为什么要将它们结合起来呢？在许多情况下，每个视图都提供了额外且互补的信息，从而允许训练更好的模型。

人们可以做的最简单是从每个视图中提取特征，将它们聚合并训练单个模型。这种方法通常有效，但它也有一些局限性。每个视图可能具有不同的统计属性，因此每个视图可能需要不同类型的模型。在聚合所有视图的特征时，可能会引入变量相关性，这可能会影响性能。另一个局限性是特征需要相同的格式（特征向量、图像等）以便进行聚合。

对于视频分类，我们可以有两个视图。一个由图像序列表示，另一个由相应的音频表示。对于视频部分，我们可以将特征编码为图像本身，即指标。然后，可以直接从这些图像训练卷积神经网络（在第 8 章中介绍）。对于音频部分，可以提取统计特征并将其存储在普通特征向量中。在这种情况下，这两种表示方法（视图）是不同的。一个是矩阵，另一个是一维特征向量。鉴于视图的本质性以及它们不同的编码格式，将它们结合起来训练单个分类器可能会出现问题。相反，我们可以为每个视图分别训练两个模型并合并结果。这正是多视图堆叠的理念（Garcia-Ceja et al., 2018a）：为每个视图训练一个不同的模型并像 Stacking 一样组合输出。

这里，将使用 HOME TASKS 数据集演示多视图堆叠。该数据集从两个源收集：加速度和音频。加速度是用手环手表记录的，音频是用手机记录的。该数据集包含 7 种常见任务：“拖地”、“扫地”、“在电脑键盘上打字”、“刷牙”、“洗手”、“吃薯片”和“看电视”。三名志愿者对每项活动执行了大约 3 分钟。

加速度和音频信号被分割成 3 秒窗口。从每个窗口中提取了不同的特征。从加速度中提取 3 轴（x,y,z）的均值、标准差、最大值、平均幅、曲线下面积等。从音频信号中提取了 12 个特征，梅尔频率倒谱系数（MFCC）。为了保护志愿者的隐私，未发布原始音频。数据集已经包含了加速度和音频的特征。第一列是标签。

为了实现多视图堆叠，将训练两个随机森林，每个对应一个视图（加速度和音频）。预测输出将堆叠形成新的训练集 D'，使用 D' 的随机森林将作为元学习器。

来自 stacking_algorithms.R 的后续代码片段显示了 R 中实现的多视图堆叠。

```
mvstackacking <- function(D, v1cols, v2cols, k = 10){

# 生成内部交叉验证的折
folds <- sample(1:k, size = nrow(D), replace = T)

trueLabels <- NULL
predicted.v1 <- NULL # 视图 1 的预测标签
predicted.v2 <- NULL # 视图 2 的预测标签
probs.v1 <- NULL # 视图 1 的预测概率
probs.v2 <- NULL # 视图 2 的预测概率

# 执行内部交叉验证。

```
for(i in 1:k){
  train <- D[folds != i
```

```
((probs.v1 + probs.v2) / 2),
pred1 = predicted.v1,
pred2 = predicted.v2)
```

```
#训练元学习器
metalearner <- randomForest(label ~,
metaFeatures, nt = 100)
```

```
res <- structure(list(metalearner=metalearner,
learnerV1=learnerV1,
learnerV2=learnerV2,
v1cols = v1cols,
v2cols = v2cols,
class = "mvstacking")
```

```
return(res)
}
```

第一个参数 D 是一个包含训练数据的数据框。v1cols 和 v2cols 是两个视图的列名。最后，参数 k 指定了内部交叉验证的折数以避免过拟合（如泛化堆叠程序中的第 2 和第 3 步）。

该函数遍历每一折，并使用训练数据为每个视图训练随机森林。在每次迭代中，使用训练好的模型预测内部测试集上的标签和概率，并将所有折的预测连接起来（predicted.v1, predicted.v2）。

交叉验证后，通过创建一个包含每个视图预测结果的数据框生成元特征（meta-features）。此外，类别概率的平均值作为元特征添加。真实标签也被添加。交叉验证的目的是避免过拟合，但在最后，我们不希望浪费数据，因此使用所有数据重新训练两个学习器。

最后，使用元特征数据框训练同样是随机森林的元学习器。创建一个包含进行预测所需所有信息的列表。这包括第一层学习器、元学习器以及每个视图的列名，我们知道在预测时如何将数据框划分为两个视图。

以下代码片段显示了使用训练过的堆叠模型进行预测的实现。

```
mvstackacking <- function(D, v1cols, v2cols, k = 10){

# 生成内部交叉验证的折
folds <- sample(1:k, size = nrow(D), replace = T)

trueLabels <- NULL
predicted.v1 <- NULL # 视图 1 的预测标签
predicted.v2 <- NULL # 视图 2 的预测标签
probs.v1 <- NULL # 视图 1 的预测概率
probs.v2 <- NULL # 视图 2 的预测概率

# 执行内部交叉验证。

```
for(i in 1:k){
  train <- D[folds != i
```

```
((probs.v1 + probs.v2) / 2),
pred1 = predicted.v1,
pred2 = predicted.v2)
```

```
#训练元学习器
metalearner <- randomForest(label ~,
metaFeatures, nt = 100)
```

```
res <- structure(list(metalearner=metalearner,
learnerV1=learnerV1,
learnerV2=learnerV2,
v1cols = v1cols,
v2cols = v2cols,
class = "mvstacking")
```

```
return(res)
}
```

第一个参数 D 是包含训练数据的数据框。v1cols 和 v2cols 是两个视图的列名。最后，参数 k 指定了内部交叉验证的折数以避免过拟合（如泛化堆叠程序）。该函数遍历每一折，并使用训练数据为每个视图训练随机森林。在每次迭代中，使用训练好的模型预测内部测试集上的标签和概率，并将所有折的预测连接起来（predicted.v1, predicted.v2）。交叉验证后，通过创建一个包含每个视图预测结果的数据框生成元特征。此外，类别概率的平均值作为元特征添加。真实标签也被添加。交叉验证的目的是避免过拟合，但在最后，我们不希望浪费数据，因此使用所有数据重新训练两个学习器。最后，使用元特征数据框训练同样是随机森林的元学习器。创建一个包含进行预测所需所有信息的列表。这包括第一层学习器、元学习器以及每个视图的列名，我们知道在预测时如何将数据框划分为两个视图。以下代码片段显示了使用训练过的堆叠模型进行预测的实现。

```
mvstackacking <- function(D, v1cols, v2cols, k = 10){

# 生成内部交叉验证的折
folds <- sample(1:k, size = nrow(D), replace = T)

trueLabels <- NULL
predicted.v1 <- NULL # 视图 1 的预测标签
predicted.v2 <- NULL # 视图 2 的预测标签
probs.v1 <- NULL # 视图 1 的预测概率
probs.v2 <- NULL # 视图 2 的预测概率

# 执行内部交叉验证。

```
for(i in 1:k){
  train <- D[folds != i
```

```
((probs.v1 + probs.v2) / 2),
pred1 = predicted.v1,
pred2 = predicted.v2)
```

```
#训练元学习器
metalearner <- randomForest(label ~,
metaFeatures, nt = 100)
```

```
res <- structure(list(metalearner=metalearner,
learnerV1=learnerV1,
learnerV2=learnerV2,
v1cols = v1cols,
v2cols = v2cols,
class = "mvstacking")
```

```
return(res)
}
```

第一个参数 D 是包含训练数据的数据框。v1cols 和 v2cols 是两个视图的列名。最后，参数 k 指定了内部交叉验证的折数以避免过拟合（如泛化堆叠程序）。该函数遍历每一折，并使用训练数据为每个视图训练随机森林。在每次迭代中，使用训练好的模型预测内部测试集上的标签和概率，并将所有折的预测连接起来（predicted.v1, predicted.v2）。交叉验证后，通过创建一个包含每个视图预测结果的数据框生成元特征。此外，类别概率的平均值作为元特征添加。真实标签也被添加。交叉验证的目的是避免过拟合，但在最后，我们不希望浪费数据，因此使用所有数据重新训练两个学习器。最后，使用元特征数据框训练同样是随机森林的元学习器。创建一个包含进行预测所需所有信息的列表。这包括第一层学习器、元学习器以及每个视图的列名，我们知道在预测时如何将数据框划分为两个视图。

# 第 3 章：使用集成学习预测行为

表 3.1：堆叠结果。
| | 准确率 | 召回率 | 特异性 | 精确率 | F1 |
|---|---|---|---|---|---|
| 音频 | 0.8463203 | 0.8413690 | 0.9741266 | 0.8487849 | 0.8438718 |
| 加速度计 | 0.8585559 | 0.8493635 | 0.9764988 | 0.8548481 | 0.8511572 |
| 多视图堆叠 | 0.9393939 | 0.9349011 | 0.9989275 | 0.9371645 | 0.9358082 |

**object** 参数是训练好的模型，**newdata** 是我们想要从中进行预测的数据框。首先，使用两个视图预测标签和概率。然后，将预测标签和平均概率组合成包含元特征的数据框。最后，使用元学习器利用元特征预测最终类别。脚本 *stacking_activities.R* 显示了如何使用我们的 *mystacking()* 函数。通过以下几行我们可以进行训练和预测。

```
m.stacking <- mystacking(trainset, v1cols, v2cols, k = 10)
pred.stacking <- predict(m.stacking, newdata = testset[-1])
```

