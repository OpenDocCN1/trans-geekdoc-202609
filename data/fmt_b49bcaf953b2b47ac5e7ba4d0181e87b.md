
```python
import numpy as np
import pandas as pd
import collections
from operator import itemgetter

# 离散化特征
attribute_means = X.mean(axis=0)

def train_feature(X, y, feature_index):
    # 根据阈值计算频率类
    class_counts = collections.defaultdict(int)
    for i in range(len(X)):
        if X[i, feature_index] >= attribute_means[feature_index]:
            class_counts[y[i]] += 1
    
    prediction = max(class_counts, key=class_counts.get)
    
    # 计算误差
    predictions = np.zeros(X.shape[0])
    for i in range(len(X)):
        if X[i, feature_index] >= attribute_means[feature_index]:
            predictions[i] = 1
            
    error = np.sum(predictions != y)
    return prediction, error
```

# 使用 Scikit-learn 估计器进行分类

Scikit-learn 库是一系列用 Python 编写的数据挖掘算法，并使用了通用的编程接口。这允许用户轻松地尝试不同的算法，并利用标准工具进行有效的测试和参数搜索。scikit-learn 中包含了大量的算法和工具。![Image result for Classifying with scikit-learn Estimators](img/image6249.jpg)

在本章中，我们重点关注为运行数据挖掘程序建立一个良好的框架。这将在后续章节中使用，那些章节将都侧重于在特定场景下的应用技术。本章介绍的核心概念如下：

*   **估计器 (Estimators)**：用于分类、聚类和回归。
*   **转换器 (Transformers)**：用于预处理和数据更改。
*   **流水线 (Pipelines)**：用于将你的工作流整合成可复制的 Scikit-learn 估计器格式。（注：根据上下文，可能是“估计器”或“流水线”）。

## 估计器

`Estimators` 是 scikit-learn 的抽象，允许对大量分类算法标准化实现。`Estimators` 用于分类。`Estimators` 有两个主要功能：

*   `fit()`：执行算法训练并设置内部参数。它接受两个输入：训练样本数据集以及这些样本对应的类别。
*   `predict()`：对作为输入的测试样本进行类别预测。该函数返回一个包含每个输入测试样本预测结果的数组。

大多数 Scikit-learn 估计器使用 `NumPy` 数组或相关格式作为输入和输出。Scikit-learn 中有大量的估计器。这些包括支持向量机 (SVM)、随机森林和神经网络。这些算法中的许多将在后面的章节中用到。在本章中，我们将使用 Scikit-learn 的一个不同的估计器：最近邻。为了本章，你需要安装 Matplotlib（如果你还没有安装的话）。最简单的安装方法是使用 `pip3` 安装 Scikit-learn：

```
pip3 install matplotlib
```

如果你在安装 Matplotlib 时遇到任何困难，请访问 `http://matplotlib.org/users/installing.html` 查看官方安装说明。

# 最近邻算法

最近邻算法（Nearest Neighbors）是标准数据挖掘算法中最直观的算法之一。为了预测新样本的类别，我们在训练数据集中查找与新样本最相似的样本。我们选取最相似的样本，并预测这些样本中大多数所属的类别。例如，我们希望根据三角形更接近哪一类来预测三角形的类别（在这里表示为相似的物体距离更近）。我们寻找三个最近的邻居，是两个钻石和一个正方形。钻石比圆圈多，因此三角形预测的类别是钻石。

最近邻算法可以用于任何数据集——然而，计算所有样本对之间的距离在计算上可能非常昂贵。例如，如果数据集中有 10 个样本，就有 45 个唯一的距离需要计算。但是，如果有 1000 个样本，就有将 500,000 个！存在多种方法来提高速度，其中一些将在后面的章节中介绍。它在分类数据上的表现也很糟糕，对于这类数据应该使用其他算法。

## 距离度量

学习中的一个概念是距离。如果我们有两个样本，我们需要知道它们有多近。此外，我们还需要回答诸如“这两个样本比另一个大吗？”。回答这类问题对于案例至关重要。人们所知的常用度量是欧几式距离。如果你在图上绘制点并用直尺测量距离，结果就是欧几式距离。正式一点说，它是每个特征距离平方和的平方根。欧几式距离很直观，但如果某些特征的值较大，它就无法提供准确性。当许多特征值为 0（即稀疏）时，它也能给出结果。其他常用的距离度量是曼哈顿距离。曼哈顿距离（也称为街区距离）是每个特征绝对差（带单位距离）之和。直观地说，它可以被看作如果限制为一次移动一个方格，在点之间移动所需的移动次数（或步数）。虽然曼哈顿距离在某些特征比其他特征大时会受到影响，但在欧几式距离的情况下影响没有那么显著。欧几式距离更适用于某些特征大于其他且数据集中存在零的情况。直观上，我们从原点到每个样本画一条线，并测量这些线之间的角度。

# 加载数据集

我们将使用的数据集称为 Ionosphere（电离层），它是许多高频天线的记录。天线的目的是确定电离层和高层大气中是否存在结构。具有结构的被认为是好的，而没有结构的被认为是坏的。该应用程序的目标是构建一个数据挖掘分类器，能够判断图像是好是坏。它可以从 UCL 机器学习数据库下载，该库包含许多不同数据挖掘应用的数据集。访问 `http://archive.ics.uci.edu/ml/datasets/Ionosphere` 并点击 Data Folder。下载 `ionosphere.data` 和 `ionosphere.names` 文件到你电脑上的一个文件夹。在本例中，我假设数据集位于一个名为 `Data` 的目录中。你的主文件夹位置取决于你的操作系统。对于 Windows，通常是 `C:\Users\Documents`。对于 Mac 或 Linux，通常是 `/home`。你可以运行以下 Python 代码来获取你的主文件夹：

```python
import os
print(os.getcwd())
```

数据集中的每行有 35 个值。前 34 个是来自 17 个天线的特征（每个天线有两个值）。最后一个是 'g' 或 'b'（“good”或“bad”）。启动 IPython Notebook 服务器并为本章创建一个名为 NearestNeighbors 的新 notebook。首先，加载代码所需的 `numpy` 和 `csv` 库：

```python
import numpy as np
import csv
```

加载数据集，从我们的文件夹获取文件：

```python
data_file = os.path.join("Data", "ionosphere")
```

然后创建 `X` 和 `y` 数组来存储数据集。这些数组的大小是从数据已知的。如果你事先不知道大小——我们将使用其他方法来加载数据集：

```python
X = np.zeros((351, 34), dtype='float')
y = np.zeros((351,), dtype='bool')
```

数据集采用逗号分隔值（CSV）格式，这通常用于数据集。我们将使用 `csv` 模块加载此文件。导入它并设置读取器对象：

```python
with open(filename, 'r') as input_file:
    reader = csv.reader(input_file)
```

接下来，我们遍历文件的每一行。每行代表一组新的测量值，即数据集中的一个样本。我们使用 `enumerate` 函数获取行的索引，这样我们就可以将样本添加到数据集 (X)：

```python
for i, row in enumerate(reader):
    # 从此样本中提取前 34 个值，将每个转换为浮点数，并将其保存到数据集中：
    data = [float(datum) for datum in row[:-1]]
    X[i] = data
```

最后，我们取行的最后一个值并设置类别。如果是好样本，将其设置为 1（或 True），否则则设置为 0：

```python
y[i] = row[-1] == 'g'
```

我们现在在 X 中拥有样本和特征的数据集，以及 y 中对应的类别，正如我们在“数据挖掘”中的分类示例中所做的那样。

# 向标准工作流移动

Scikit-learn 中的估计器有两个主要函数：`fit()` 和 `predict()`。我们使用 `fit` 方法和训练集来训练算法。我们在测试集上使用 `predict` 方法对其进行评估。首先，我们需要创建这些训练和测试集。像之前一样，从 `sklearn` 并运行 `train_test_split`：

```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=14)
```

默认情况下，算法选择五个邻居。从 `sklearn.neighbors` 导入 `KNeighborsClassifier`：

```python
from sklearn.neighbors import KNeighborsClassifier
knn = KNeighborsClassifier(n_neighbors=5)
```

在训练数据上拟合算法：

```python
knn.fit(X_train, y_train)
```

然后在测试集上进行评估：

```python
predicted = knn.predict(X_test)
accuracy = np.mean(predicted == y_test) * 100
print(f"The accuracy is {accuracy:.1f}%")
```

*   将整个数据集分为若干部分，称为“折”（folds）。
*   对于数据集中的每一折，执行以下步骤：
    *   将该折单独留出作为当前测试集
    *   在剩余的折上训练算法
    *   在当前测试集上进行评估
    *   报告所有的评估分数，包括平均分。

在此过程中，每个样本仅在测试集中被使用一次。这降低了（但没有完全消除）选择到“幸运”测试集的概率。在整个模块中，代码示例在每个章节内是层层构建的。除非另有说明，每个章节的代码应输入到同一个 IPython Notebook 中。Scikit-learn 库包含了许多交叉折验证方法。它提供了一个执行上述过程的辅助函数。我们现在可以将其导入到 IPython Notebook 中：`from sklearn.cross_validation import cross_val_score`

默认情况下，`cross_val_score` 使用一种名为“分层 K 折”（Stratified K Fold）的特定方法将数据集划分为折。这创建的折在每个类别别的比例上大致相同，再次降低了选择糟糕折的概率。这是一个非常好的默认设置，所以我们现在不打算修改。接下来，我们使用该函数，将其应用于原始（完整）数据集和标签上：

```python
scores = cross_val_score(estimator, X, y, scoring='accuracy')
average = np.mean(scores) * 100
print(f"average accuracy is {average:.1f}")
```

这得到了一个 82.3% 的略高一点的结果，但在我们还没有尝试设置更好的参数之前，它已经足够好了。在下一节中，我们将看到如何通过更改参数来改进

### 参数

几乎所有算法都有由用户设置的参数。这有助于泛化算法，使其能够适用于更广泛的情况。设置这些参数可能是困难的，因为良好的值通常高度依赖数据集的特征。最近邻算法有几个参数，但最重要的参数是用于预测类别时使用的最近邻居数量。在 sklearn 中，这个参数被称为 `n_neighbors`。

在下面的图中，我们展示了当这个数字太低时，随机标记的样本会导致错误。相反，当它太高时，实际的最近邻居对结果的影响就较小：在左侧，我们通常期望测试样本（三角形）被分类为圆形。然而，如果 `n_neighbors` 为 1，该区域中的单个红色菱形（可能是一个噪声样本）会导致该样本被预测为菱形，尽管它看起来位于红色区域。在图 (b) 中，在右侧，我们通常期望测试样本被分类为菱形。然而，如果 `n_neighbors` 为 7，最近邻（全部都是菱形）会被大量的圆形样本所覆盖。如果我们想对 `n_neighbors` 参数测试多个值，例如从 1 到 20 的每一个值，我们可以通过设置 `n_neighbors` 并观察结果来多次重新运行实验：

```python
avg_scores = []
all_scores = []
parameter_values = list(range(1, 21))
# 在 parameter_values 中包含 20 以于 n_neighbors：
estimator = KNeighborsClassifier(n_neighbors=n_neighbors)
scores = cross_val_score(estimator, X, y, scoring='accuracy')
```

在我们的分数列表中计算并存储平均值：`avg_scores.append(np.mean(scores))`。我们还存储了完整集合以便分析：`all_scores.append(scores)`。然后我们可以绘制 `n_neighbors` 和准确率之间的关系图。首先，我们告诉 IPython Notebook 我们想内联显示：`%matplotlib inline` 我们导入 matplotlib 并绘制参数值以及对应的分数。虽然存在很大差异，但图表显示随着邻居数量的增加，呈现下降趋势。

对于一个基于数学的算法来比较这些每一个特征，它们在尺度、范围和单位上的差异可能很难解释。如果我们在许多算法中使用上述特征，权重可能会成为最有影响的特征，这在很大程度上是因为数值较大，而与特征的实际效果没有关系。克服这一问题的方法之一是使用一种称为“预处理”（preprocessing）的过程对特征进行归一化，使它们都具有相同的范围，或者被归类为小、中、大等类别。突然，特征类型之间的巨大差异对算法的影响就会减小，并可能导致准确性的大幅提高。预处理还可以用于仅选择更有效的特征、创建新特征等。Scikit-learn 中的预处理是通过 `Transformer` 对象完成的，这些对象接收一种格式的数据集并在对数据进行某些转换后返回修改后的数据集。这些对象不需要是数值型的，因为 `Transformers` 也用于提取特征——但在在本节中，我们将专注于预处理。

### 示例

我们可以通过破坏鸢尾花（Iris）数据集来展示这个问题。虽然这只是一个例子，但许多真实世界的数据都有此类形式的问题。首先，我们创建一个数组的副本，以便不修改原始数据集：`X_broken = np.array(X)`。接下来，我们通过将每个第二个特征除以 10 来破坏数据集：`X_broken[:,::2] /= 10`。

理论上，这不应该对结果产生巨大影响。毕竟，这些特征的值是非常相似的。主要问题是尺度发生了变化，奇数特征的值现在大于偶数特征。我们可以通过计算准确率来看到这种效果：

```
estimator = KNeighborsClassifier()
original_scores = cross_val_score(estimator, X, y, scoring='accuracy')
print("The original average accuracy for is {0:.1f}%".format(np.mean(original_scores) * 100))
broken_scores = cross_val_score(estimator, X_broken, y, scoring='accuracy')
print("The 'broken' average accuracy for is {0:.1f}%".format(np.mean(broken_scores) * 100))
```

这给原始数据集得到了 82.3% 的分，但在破坏的数据集上下降到了 71.5%。我们可以通过将所有特征缩放到 0 到 1 的范围来解决这个问题。

### 标准预处理

我们将为这次实验进行的预处理称为通过 `MinMaxScaler` 类进行的“基于特征的归一化”。继续本节剩余部分的 IPython notebook；首先，我们导入这个类：`from sklearn.preprocessing import MinMaxScaler`

`MinMaxScaler` 类接收每个特征并将其缩放到 0 到 1 的范围。最小值被替换为 0，最大值替换为 1，中间的其他值相应填充。对于我们的预处理器，我们运行 `transform` 函数。虽然 `MinMaxScaler` 不需要（某些 `Transformers` 需要先训练），但我们也可以通过运行 `fit_transform` 来组合这些步骤：

```python
X_transformed = MinMaxScaler().fit_transform(X)
```

在这里，`X_transformed` 的形状与 `X` 相同。但每列的最大值为 1，最小值为 0。这种方法还有其他形式的归一化，它们对于其他应用和特征是有效的：
