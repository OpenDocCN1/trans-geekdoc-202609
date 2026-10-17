
##### 注意

你首先在 `第 3 章`，`回归` 中学习了点积。两个向量的点积的计算方法是，将第一个向量的第 `ith` 坐标乘以第二个向量的第 `ith` 坐标（对于每个 `i`）。一旦我们得到了所有的乘积，我们就对这些值求和：

```
np.dot([1, 2, 3], [4, 5, 6]) # 1*4 + 2*5 + 3*6
```

#### 练习 15：计算熵

计算数据集 5.1 中特征的熵。

1. 我们有四个特征：`Employed`（雇佣）、`Income`（收入）、`LoanType`（贷款类型）、`LoanAmount`（贷款金额）。为了简单起见，我们将 `Income` 和 `LoanAmount` 视为离散值。目前 `Employed` 的分布如下：
   * true 4/7 次
   * false 3/7 次
2. 使用熵函数计算 `Employed` 列的熵：
   ```
   H_employed = entropy([4/7, 3/7])
   ```
   输出为 0.9852。
3. `Income` 的分布如下：
   * 25,000 1/7 次
   * 75,000 2/7 次
   * 80,000 1/7 次
   * 100,000 1/7 次
   * 125,000 1/7 次
   计算 `Income` 列的熵：
   ```
   H_income = entropy([1/7, 2/7, 1/7, 1/7, 1/7])
   ```
   输出为 2.2359。
4. `LoanType` 的分布如下：
   * car 3/7 次
   * house 2/7 次
   * other 2/7 次
   计算 `LoanType` 列的熵：
   ```
   H_loanType = entropy([3/7, 2/7, 2/7])
   ```
   输出为 1.557。
5. `LoanAmount` 的分布如下：
   * 15,000 1/7 次
   * 25,000 1/7 次
   * 80,000 3/7 次
   * 100,000 1/7 次
   * 125,000 1/7 次
   * 150,000 1/7 次
   计算 `LoanAmount` 列的熵：
   ```
   H_loanAmount = entropy([1/7, 1/7, 3/7, 1/7, 1/7, 1/7])
   ```
   输出为 2.1281。
6. 如你所示，分布越接近均匀分布，熵就越大。
7. 在这个练习中，我们使用熵来构建树。

除了熵（entropy），还有另一种广泛使用的指标可以衡量分布的随机性：`Gini Impurity`（基尼纯度）。

基尼纯度的定义如下：

![](img/Image00053.jpg)

##### 图 5.5：基尼纯度

对于两个变量，基尼纯度为：

![](img/Image00054.jpg)

##### 图 5.6：两个变量的基尼纯度

由于使用了对数，熵的计算速度可能会慢一些。相反，基尼纯度在衡量随机性方面的精确度较低。

#### 注意事项

构建决策树时，使用熵还是基尼纯度的信息增益更好？

有些人更倾向于使用基尼纯度，因为你不需要计算对数。从计算角度来看，这两种解决方案都不特别复杂，因此都可以使用。在性能方面，以下研究得出结论：这两个指标之间的差异微乎其微：[`www.unine.ch/files/live/sites/imi/files/shared/documents/papers/Gini_index_fulltext.pdf`](https://www.unine.ch/files/live/sites/imi/files/shared/documents/papers/Gini_index_fulltext.pdf)。

我们已经了解到可以基于信息增益或基尼纯度来优化决策树。遗憾的是，这些指标仅适用于离散值。如果标签定义在连续区间上（例如价格范围或工资范围）怎么办？

我们必须使用其他指标。从技术上，你可以理解基于连续标签创建决策树的原理，这涉及到回归。我们可以从本章中复用的指标是均方误差（mean squared error）。我们必须通过最小化均方误差而不是基尼纯度或信息增益来优化决策树。由于这是一本入门书籍，我们将省略这一指标。

#### 退出条件

我们可以根据规则值不断分割数据点，直到决策树的每个叶子节点的熵为零。问题在于，这种终止状态是否理想。

通常，这种状态是不理想的，因为我们面临模型过拟合的风险。当我们模型的规则过于具体且挑剔时，并且做出决策的样本量太小，我们就有可能得出错误的结论，从而在数据集中识别出一种在现实生活中并不存在的模式。

例如，如果我们转了三次轮盘，得到了 `12`、`25`、`12`，得出“每个奇数次旋转的结果都是 `12`”并不是一个明智的策略。通过假设每个奇数次旋转都等于 `12`，我们找到了一个完全由随机噪声引起的规则。

因此，对可以继续分割的数据集的最小大小设置限制，是一个在实践中运行良好的退出条件。例如，如果你在数据集大小小于 `50`、`100`、`200` 或 `500` 时就停止分割，就可以避免对随机噪声得出结论，从而最大限度地降低模型过拟合的风险。

另一个流行的退出条件是对树深度的最大限制。一旦达到固定的树深度，我们就对叶节点中的数据点进行分类。

#### 使用 scikit-learn 构建决策树分类器

我们已经学习了如何从 `.csv` 文件加载数据，如何对数据进行预处理，以及如何将数据分为训练集和测试集。如果你需要复习这些知识，可以回到之前的章节，你在回归和分类的背景下学习过这个过程。

现在我们假设一组训练特征、训练标签、测试特征和测试标签是作为 scikit-learn `train-test-split` 调用的返回值提供的。

注意，在旧版本的 scikit-learn 中，你必须导入 `cross_validation` 而不是 `model_selection`：

```python
features_train, features_test, label_train, label_test = model_selection.train_test_split(
    features,
    label,
    test_size=0.1
)
```

我们不会关注如何获取这些数据点，因为这个过程与回归和分类的情况完全相同。

是时候导入并使用 scikit-learn 的决策树分类器了：

```python
from sklearn.tree import DecisionTreeClassifier

decision_tree = DecisionTreeClassifier(max_depth=6)
decision_tree.fit(features_train, label_train)
```

我们在 `DecisionTreeClassifier` 中设置了一个可选参数 `max_depth`，用于限制决策树的深度。你可以阅读官方文档以获取完整的参数列表：[`scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html`](http://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html)。一些较重要的参数如下：

* `criterion`: Gini 代表基尼纯度（Gini Impurity），而 entropy 代表信息增益。
* `max_depth`: 这是树的最大深度。
* `min_samples_split`: 这是分割内部节点所需的最小样本数。

你也可以对文档列出的所有其他参数进行实验。我们将在本主题中省略它们。

模型构建完成后，我们就可以使用决策树分类器来预测数据：

```python
decision_tree.predict(features_test)
```

你将在本主题结束的活动中构建一个决策树分类器。

#### 评估分类器的性能

在分割训练数据和测试数据之后，决策树模型有一个 `score` 方法来评估测试数据的分类情况。我们已经在第 3 和第 4 章中学习了如何使用 `score` 方法：

```python
decision_tree.score(features_test, label_test)
```

`score` 方法的返回值是一个小于等于 1 的数字。越接近 1，我们的模型就越好。

现在我们将学习另一种评估模型的方法。尽管将此方法应用于你在上一个章节中构建的模型。

假设我们有一个测试特征和一个测试标签：

```python
testLabel 表示测试标签
predicted_label = decision_tree.predict(testFeature)
```

假设我们正在研究一个标签值 `positiveValue`。我们将使用以下定义来定义一些帮助你评估分类器好坏的指标：

* 真正例（True Positive）：`positiveValue == predicted_label == testLabel`
* 真负例（True Negative）：`positiveValue != predicted_label == testLabel`
* 假正例（False Positive）：`positiveValue == predicted_label != testLabel`
* 假负例（False Negative）：`positiveValue != predicted_label != testLabel`

假阳性是指预测等于正值，但测试数据中的实际标签不等于该正值。例如，在技术面试中，假阳性是指一个能力平平的软件开发者因为表现得很有说服力而被录用，隐藏了他完全缺乏能力。

不要将假阳性与假阴性混淆。以技术面试为例，假阴性是指一个能力足以胜任工作的软件开发者，但他没有被录用。

使用上述四个定义，我们可以定义三个描述模型预测现实情况优劣的指标。符号 `#( X)` 表示 `X` 中值的数量。用技术术语来说，`#( X)` 表示 `X` 的基数（cardinality）：

精确率（Precision）：`#( True Positives) / (#( True Positives) + #( False Positives))`

召回率（Recall）：`#( True Positives) / (#( True Positives) + #( False Negatives))`

精确集中在分类器认为为正的值上。这些结果中的一些是真正例，另一些是假正例。高精确率意味着与真正例相比，假正例的结果数量非常少。这意味着一个精确的分类器在寻找正结果时很少出错。

回想，召回率（recall）围绕测试数据中的正值展开。这些正值中的某些被分类器找到了，这些是真正例（true positives）。那些没有被分类器找到的正值是假负例（false negatives）。高召回率的分类器可以找到大多数正值。

#### 练习 16：精确率与召回率

计算以下两个分类器的精确率（precision）和召回率值：

##### 分类器 1

```python
TestLabels1 = [True, True, False, True, True]
PredictedLabels1 = [True, False, False, False, False]
```

##### 分类器 2

```python
TestLabels2 = [True, True, False, True, True]
PredictedLabels = [True, True, True, True, True]
```

1. 根据公式，让我们计算分类器 1 的真正、假正和负的数量：
   ```python
   TruePositives1 = 1 # 预测标签和测试标签均为 true
   FalsePositives1 = 0 # 预测标签为 true，测试标签为 false
   FalseNegatives1 = 3 # 预测标签为 false，测试标签为 true
   Precision1 = TruePositives1 / (TruePositives1 + FalsePositives1)
   Precision1 # 1/1 = 1
   Recall1 = TruePositives1 / (TruePositives1 + FalseNegatives1)
   Recall1 #1/4 = 0.25
   ```

2. 第一个分类器的精确率很高，但召回率很差。让我们为第二个分类器进行相同的计算。
   ```python
   TruePositives2 = 4
   FalsePositives2 = 1
   FalseNegatives2 = 0
   Precision2 = TruePositives2 / (TruePositives2 + FalsePositives2)
   Precision2 #4/5 = 0.8
   Recall2 = TruePositives2 / (TruePositives2 + FalseNegatives2)
   Recall2 # 4/4 = 1
   ```

3. 第二个分类器具有极高的召回率，但其精确率并不完美。

4. F1 分数是精确率和召回率的调和平均数。其取值范围在 0 到 1 之间。F1 分数的优势在于它同时考虑了假正和假负。

#### 练习 17：计算 F1 分数

计算上一个练习中两个分类器的 F1 分数：

1. 计算 F1 分数的公式如下：
   ```python
   2*Precision*Recall / (Precision + Recall)
   ```

2. 第一个分类器的 F1 分数如下：
   ```python
   2 * 1 * 0.25 / (1 + 0.25) # 0.4
   ```

3. 第二个分类器的 F1 分数如下：
   ```python
   2 * 0.8 * 1 / (0.8 + 1) # 0.888888888888889
   ```

现在我们已经知道了精确率、召回率和 F1 分数的含义，让我们使用 scikit-learn 的工具来计算并打印这些值：

```python
from sklearn.metrics import classification_report

print(
    classification_report(
        label_test,
        decision_tree.predict(features_test)
    )
)
```

输出将如下：

```
precision recall f1-score support
0 0.97 0.97 0
1 1.00 1.00 5
2 0.91 0.91 3
3 0.83 0.83 1
```

真阳性 (True Positives) 假阳性 (False Positives)
假阴性 (False Negatives) 真阴性 (True Negatives)

6. 混淆矩阵可以计算精确率、召回率、准确率以及 `f1_score` 指标。计算方法非常直接，且包含在指标的定义中。

7. 可以使用 scikit-learn 计算混淆矩阵：

```python
from sklearn.metrics import confusion_matrix

confusion_matrix(label_test, label_predicted)
```

```
array([[25, 0, 11, 0],
       [5, 0, 0, 0],
       [0, 0, 127, 0],
       [5, 0, 0, 0]])
```

8. 注意，这与我们在上一节使用的示例不同。因此，如果你使用混淆矩阵内部的值，将得到不同的精确率、召回率和 `f1_score` 值。

9. 你也可以使用 `pandas` 来创建混淆矩阵：

```python
import pandas

pandas.crosstab(label_test, label_predicted)
```

```
col_0 0 2
row_0
0 25 11
1 5 0
2 0 127
3 5 0
```

让我们通过计算模型的准确率分数来验证这些值：
- 我们有 127 + 25 = 152 个被分类正确的数据点。
- 数据点的总数为 152 + 11 + 5 + 5 = 173。
- 152/173 等于 0.8786127167630058。

让我们使用之前用过的 scikit-learn 工具函数来计算准确率分数：

```python
from sklearn.metrics import accuracy_score

accuracy_score(label_test, label_predicted)
```
