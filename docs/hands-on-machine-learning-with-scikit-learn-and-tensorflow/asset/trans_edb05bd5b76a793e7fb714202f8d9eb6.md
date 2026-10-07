
3 和 5 之间的主要区别在于连接顶部直线和底部圆弧的小线的位置。如果你在画 3 的时候将连接处略微向左偏移，分类器可能会将其分类为 5，反之亦然。换句话说，这个分类器对平移和旋转非常敏感。因此，减少 3/5 混淆的一种方法是对图像进行预处理，以确保它们位于居中且没有旋转过大。这可能有助于减少其他错误。

## 多标签分类 (Multilabel Classification)

到目前为止，每个实例始终被分配给一个类。在某些情况下，你可能希望分类器为每个实例输出多个类。例如，考虑一个人脸识别器：如果它在同一张照片上识别出几个人，该怎么办？当然，它应该为识别出的每一个人标记一个标签。分类器已经训练为识别三个脸：Alice、Bob 和 Charlie；那么当给它一张 Alice 和 Charlie 的照片时，它应该输出 [1, 0, 1]（意味着“Alice，Bob 没有，Charlie”）。输出多个二值标签的分类系统被称为多标签分类系统。

我们不会深入讨论人脸识别，但让我们来看一个更简单的例子，仅用于说明：

```python
from sklearn.neighbors import KNeighborsClassifier

y_train_large = (y_train >= 7)
y_train_odd = (y_train % 2 == 1)
y_multilabel = np.c_[y_train_large, y_train_odd]

knn_clf = KNeighborsClassifier()
knn_clf.fit(X_train, y_multilabel)
```

这段代码创建了一个多标签数组，其中每个数字包含两个标签：第一个表示该数字是否大数字（7、8 或 0），第二个表示它是否为奇数。接下来的几行创建了一个 `KNeighborsClassifier` 实例（它支持多标签分类，但并不是所有的分类器都支持），并使用多目标数组对其进行训练。现在我们进行预测，注意到它输出了两个：

```
>>> knn_clf.predict([some_digit])
array([False, True])
```

结果是正确的！数字 5 不大（False）且是奇数（True）。
评估多标签分类器有很多方法，选择合适的指标实际上取决于你的项目。例如，一种方法是为每个单独标签测量 F1 分数（或之前过的任何其他分类器指标），然后简单地计算平均分。这段代码计算所有标签的平均 F1 分数：

```
>>> y_train_knn_pred = cross_val_predict(knn_clf, X_train, y_multilabel, cv=3)
>>> f1_score(y_multilabel, y_train_knn_pred, average="macro")
0.976410265506065
```

这假设所有标签同样重要，但可能并非如此。特别是如果你关于 Alice 的照片比 Bob 或 Charlie 多，你可能希望给分类器对 Alice 的评分更高的权重。一个简单的选项是给每个标签一个与其支持度（即具有目标标签的实例数量）相等的权重。这样做只需在前面的代码中设置 `average="weighted"` ⁴。

## 多输出分类 (Multioutput Classification)

我们将讨论的最后一种分类任务被称为多输出多类分类（或简单的多输出分类）。它是多标签分类的推广，其中每个标签都可以是多类的（即它可以有两个以上的可能值）。

为了说明这一点，让我们构建一个从图像去除噪声的系统。它将接受一个带噪声的数字图像作为输入，并（希望）输出一个干净的数字图像，用像素强度数组表示，就像 MNIST 图像一样。注意分类器的输出是多标签的（每个像素一个标签），每个标签可以有多个值（像素强度范围从 0 到 255）。那么这就是多输出分类系统的示例。

> 分类和回归之间的界限有时是模糊的，在这个例子中如此。可以说，预测像素强度更接近回归而非分类。此外，多输出系统不仅限于分类任务；你甚至可以有一个每个实例输出多个标签的系统，包括类别值和标签值。

让我们先通过使用 NumPy 的 `randInt()` 函数向这些像素图像添加噪声来创建训练集和测试集。目标图像将是原始图像：

```python
noise = np.random.randint(0, 100, (len(X_train), 784))
X_train_mod = X_train + noise
noise = np.random.randint(0, 100, (len(X_test), 784))
X_test_mod = X_test + noise
y_train_mod = X_train
y_test_mod = X_test
```

⁴ Scikit-Learn 提供了其他几种平均选项和多标签分类器指标；更多信息请参阅文档。

让我们看看测试集中的一张图像（是的，我们正在偷测试数据，所以你现在应该皱眉了）：

![](img/0684d2da98e09085c0a622d4fd69aaad_135_0.png)

左侧是带噪声的输入图像，右侧是干净的目标图像。现在让我们训练分类器并让它清理这张图像：

```python
knn_clf.fit(X_train_mod, y_train_mod)
clean_digit = knn_clf.predict(X_test_mod)
plot(clean_digit)
```

![](img/0684d2da98e09085c0a622d4fd69aaad_135_0.png)

看起来足够了！我们对分类的介绍结束了。

练习

1. 尝试在 MNIST 数据集上构建一个准确率达到 97% 的分类器。提示：KNeighbors 效果良好。
2. 写一个函数，可以向任何方向（左、右、上、下）移动一个像素。⁵ 你可以使用 `scipy.ndimage.shift`。然后，对于每个图像，`shift(image, [2, 1])` 会向下移动 2 像素并向右移动 1 像素。
3. 挑战泰坦尼克数据集。从 Kaggle 开始是一个很好的起点：
- 从 ApacheAssassin 的公共数据下载垃圾示例。
- 解压数据集并熟悉格式。
- 将数据集分成训练集和测试集。
- 编写数据流水线，将每封邮件转换为（稀疏）向量。
- 你可以为准备流水线添加超参数，以控制是否删除头部、转换为小写、删除标点符号、将所有 URL 替换为 "URL"将所有数字替换为 "NUMBER"，甚至进行词干提取（即修剪结尾；有相应的 Python 库可以实现这一点）。
- 然后尝试几种分类器，看看你是否能建立高召回率和高精确率的优秀分类器。

这些练习的解答可在在线笔记本中找到：https://github.com/ageron/handson-ml2。

