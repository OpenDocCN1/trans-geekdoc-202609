
![](img/4.1.png)

**图 4.1：逻辑回归（Sigmoid 函数）**

逻辑函数呈 S 形曲线，确保预测概率始终在 0 和 1 之间。逻辑回归模型使用该函数预测给定输入属于两个类别（0 或 1）之一的概率。分类阈值通常设为 0.5，即如果 `p(Y=1|X)` 大于或等于 0.5，则实例分类为 1；否则分类为 0。代码 4.1 展示了如何使用流行的 scikit-learn 库在 Python 中执行逻辑回归。我们将使用一个简单的合成数据集进行二分类。

### 代码 4.1：逻辑回归的 Python 代码

```python
import numpy as np

from sklearn.datasets import make_classification
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, confusion_matrix, classification_report
import matplotlib.pyplot as plt

#### 创建用于二分类的合成数据集
X, y = make_classification(n_samples=100, n_features=2, n_informative=2, n_redundant=0, random_state=42)

#### 将数据集划分为训练集和测试集
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

#### 创建逻辑回归模型
model = LogisticRegression()

#### 使用训练数据拟合模型
model.fit(X_train, y_train)

#### 在测试数据上进行预测
y_pred = model.predict(X_test)

#### 计算准确率和其他性能指标
accuracy = accuracy_score(y_test, y_pred)
conf_matrix = confusion_matrix(y_test, y_pred)
class_report = classification_report(y_test, y_pred)

#### 可视化决策边界
plt.scatter(X[:, 0], X[:, 1], c=y, cmap=plt.cm.Paired)

ax = plt.gca()
xlim = ax.get_xlim()
ylim = ax.get_ylim()

xx, yy = np.meshgrid(np.linspace(xlim[0], xlim[1], 50), np.linspace(ylim[0], ylim[1], 50))
Z = model.decision_function(np.c_[xx.ravel(), yy.ravel()])
Z = Z.reshape(xx.shape)

plt.contour(xx, yy, Z, colors='k', levels=[0], linestyles=['--'])
plt.title("Logistic Regression Decision Boundary")
plt.xlabel("Feature 1")
plt.ylabel("Feature 2")
plt.show()

#### 打印性能指标
print(f"Accuracy: {accuracy}")
print("Confusion Matrix:\n", conf_matrix)
print("Classification Report:\n", class_report)
```

请参考图 4.2 查看代码输出：

![](img/4.2.png)

**图 4.2：代码 4.1 的输出**

在该代码中，我们使用 scikit-learn 的 `make_classification` 创建了一个合成数据集。该数据集包含两个特征，适用于二分类。我们使用 `train_test_split` 将数据集划分为训练集和测试集。我们使用 scikit-learn 的 `LogisticRegression()` 创建逻辑回归模型。我们使用 `fit()` 方法利用训练数据拟合模型。我们使用 `predict()` 方法在测试数据上进行预测。我们计算准确率、混淆矩阵和分类报告以评估模型性能。我们可视化了逻辑回归模型的决策边界，以查看它是如何分离类别的。

## K 近邻

**K 近邻（KNN）** 是一种简单直观的机器学习算法，既可用于分类任务，也可用于回归任务。它是一种非参数化和基于实例的学习方法。KNN 基于特征空间中 K 个最近数据点的多数类别进行预测。KNN 的关键概念和特征包括：

*   **基于实例的学习**：KNN 是一种基于实例的学习算法。它将整个数据集存储在内存中，进行预测时，它会寻找距离新数据点最近的 K 个邻居来确定其类别或数值。

*   **K 个最近邻居**：K 表示进行预测时考虑的最近邻居数量。K 的选择是一个超参数，会显著影响算法性能。较小的 K 可能导致过拟合，而较大的 K 可能导致欠拟合。

*   **距离度量**：KNN 依赖距离度量（例如欧氏距离）来衡量数据点之间的相似性。距离度量有助于确定哪些数据点是最近邻居。

*   **分类与回归**：KNN 既可用于分类也可用于回归任务。在分类中，它根据 K 个最近邻居中的多数类别分配类别标签。在回归中，它计算 K 个最近邻居数值的平均值或加权平均值来预测连续结果。

*   **无训练阶段**：KNN 没有显式的训练阶段。它仅记忆训练数据，所有学习都发生在预测期间。

*   **惰性学习**：KNN 常被称为惰性学习器，因为它在训练期间不构建模型。相反，它将大部分工作推迟到预测时刻。

*   **对异常值鲁棒**：KNN 对异常值具有鲁棒性，因为它考虑的是数据点的局部邻域，而非依赖全局模型。

*   **超参数**：除了 K 之外，其他超参数（如距离度量的选择和加权方案——均匀权重或基于距离的权重）也会影响算法性能。

KNN 易于理解和实现，使其成为简单分类和回归任务的良好选择。然而，它的计算开销可能很大，尤其是在大型数据集上，并且在高维空间中可能表现不佳。适当调整超参数（包括 K 值）对于使用 KNN 获得良好结果至关重要。从数学上表示，KNN 如下：

*   **初始化**：给定一个带有标签示例的数据集：

    ![](img/eq-21.jpg)

    其中  表示第 i 个数据点的特征向量，  是对应的类别标签（用于分类）或数值（用于回归）。

*   **距离度量**：选择一种距离度量，通常为欧氏距离：

    ![](img/eq-3.png)

*   **预测**：按如下方式执行：

    *   对于新数据点 `x_new`，计算 `x_new` 与 D 中所有数据点之间的距离。

    *   选择距离 `x_new` 最近的 K 个数据点（距离最小）。

    *   对于分类，将 `x_new` 的类别标签预测为 K 个最近邻居中的多数类别。

    *   对于回归，将 `x_new` 的数值预测为 K 个最近邻居数值的平均值（或加权平均值）。

KNN 的典型示意图见图 4.3：

![](img/4.3.png)

**图 4.3：KNN 示意图**

在该图中：

*   图中的点代表带有关联类别标签（类别 0 或类别 1）的数据点。

*   新数据点是我们要对其进行预测的点。

*   KNN 计算新数据点与所有现有数据点之间的距离。

*   它根据这些距离选择 K 个最近邻居。本例中使用 K=3。

*   对于分类，K 个邻居中的多数类别决定了新数据点的预测类别。

### 代码 4.2

**代码 4.2：KNN 的 Python 代码**

```python
from sklearn.neighbors import KNeighborsClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, classification_report
from sklearn.datasets import load_iris

#### 加载鸢尾花数据集（scikit-learn 内置数据集）
data = load_iris()
X = data.data  # 特征
y = data.target  # 目标（类别标签）

#### 将数据划分为训练集和测试集
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

#### 创建具有指定邻居数量 (K) 的 KNN 分类器
k = 3
knn_classifier = KNeighborsClassifier(n_neighbors=k)

#### 使用训练数据拟合模型
knn_classifier.fit(X_train, y_train)

#### 在测试数据上进行预测
y_pred = knn_classifier.predict(X_test)

#### 计算准确率并打印分类报告
accuracy = accuracy_score(y_test, y_pred)
report = classification_report(y_test, y_pred, target_names=data.target_names)

print("Accuracy:", accuracy)
print("\nClassification Report:\n", report)
```

请参考图 4.4 查看代码输出：

![](img/4.4.png)

**图 4.4：代码 4.2 的输出**

在这段代码中，我们导入了必要的库，包括 `scikit-learn`，它提供了用于 KNN 分类的 `KNeighborsClassifier`。我们加载了鸢尾花数据集，这是一个著名的分类数据集，包含特征（萼片长度、萼片宽度、花瓣长度、花瓣宽度）和类别标签（山鸢尾、变色鸢尾、维吉尼亚鸢尾）。我们使用 `train_test_split` 将数据集划分为训练集和测试集。我们创建了一个具有指定邻居数量 (K) 的 KNN 分类器，此处为 `k = 3`。我们使用 `fit()` 方法将 KNN 分类器拟合到训练数据上。我们使用 `predict()` 方法对测试数据进行预测。我们计算模型的准确率，并使用 `scikit-learn` 的 `accuracy_score` 和 `classification_report` 函数生成分类报告。

## 决策树

决策树是一种流行的监督机器学习算法，既可用于分类任务，也可用于回归任务。它是一种树状结构，根据输入特征的值做出决策。树的每个内部节点代表基于特定特征的决策，每个叶节点代表类别标签（在分类中）或预测值（在回归中）。决策树易于理解、解释和可视化，使其成为预测建模和数据探索的宝贵工具。

### 决策树的关键特征

决策树的关键特征如下：

*   **节点**：决策树由节点组成，包括内部节点和叶节点。

*   **根节点**：最顶层的节点称为根节点，代表第一个决策或特征。

*   **内部节点**：内部节点代表基于特征值的决策。

*   **叶节点**：叶节点代表结果或预测。

*   **边**：边连接节点，代表从一个节点到另一个节点的路径。

*   **分裂**：每个内部节点代表基于特征值的数据分裂。

*   **分支**：分支是从根节点到叶节点的路径。

### 决策树的工作原理

决策树的工作步骤描述如下：

1.  树的根节点代表用于对数据做决策的最重要或信息量最大的特征。

2.  内部节点代表基于特定特征值的决策。

3.  算法在每个内部节点根据特定准则（例如基尼不纯度、熵）选择最能分离数据的特征。

4.  该过程持续进行，创建更多节点和分支，直到满足停止准则，例如达到最大深度或叶节点中的最小数据点数量。

5.  叶节点包含预测的类别标签（在分类中）或预测值（在回归中）。

### 决策树的优势

决策树的优势如下：

*   易于解释和可视化。

*   适用于分类和回归。

*   可处理数值型和分类型数据。

*   不需要大量的数据预处理。

*   可处理特征选择和变量重要性。

*   对异常值具有鲁棒性。

### 决策树的劣势

决策树的劣势如下：

*   容易过拟合（可通过剪枝等技术缓解）。

*   可能不如其他某些算法那样很好地捕捉复杂关系。

*   对数据的微小变化敏感。

请参考下图以便更好地理解：

![](img/4.5.png)

**图 4.5：决策树表示**

决策树是一组用于分类或预测结果的决策规则的图形表示。虽然决策树结构是可视化的，但没有直接与树结构本身相关联的特定数学方程。图 4.3 表示决策树的典型图示。然而，决策树是通过算法构建的，这些算法使用各种数学概念在每个节点做出决策。以下是决策树构建中涉及的关键组件：

*   **分裂准则（不纯度度量）**：决策树通过基于输入特征值递归地划分数据来构建。选择用于分裂的特征及分裂点，是使用分裂准则来决定的，该准则度量数据点的不纯度或无序程度。常见的不纯度度量包括：

    *   **基尼不纯度**：用于分类任务。它度量随机选择的数据点被错误分类的概率。具有 `K` 个类别的节点 `t` 的公式：

        ![](img/eq-41.jpg)

    *   **熵**：也用于分类任务。它度量节点中无序或不确定性的程度。具有 `K` 个类别的节点 `t` 的公式：

        ![](img/eq-51.jpg)

    *   **MSE（均方误差）**：用于回归任务。它度量节点中数据点的方差。具有数据点的节点 `t` 的公式：

        ![](img/eq-61.jpg)

*   **分裂算法**：决策树算法根据选定的分裂准则选择最佳特征和分裂点。可使用多种算法，包括 `ID3`、`C4.5`、`CART` 和随机森林，它们具有确定分裂的特定公式。

*   **剪枝**：树构建完成后，可能会进行剪枝以防止过拟合。剪枝涉及移除不能提高树预测性能的分支。剪枝决策通常使用统计度量，如卡方检验。

虽然决策树结构没有直接的数学方程，但数学主要体现在在每个节点选择最佳特征和分裂点上。不纯度度量和分裂算法的选择是决策树构建中的关键数学组件。树的结构本身是决策规则的可视化表示。代码 4.3 展示了如何使用 Python 和 `scikit-learn` 实现决策树分类器：

**代码 4.3：决策树的 Python 代码**

```python
from sklearn.tree import DecisionTreeClassifier
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

#### 加载鸢尾花数据集
data = load_iris()
X = data.data  # 特征
y = data.target  # 目标（类别标签）

#### 将数据划分为训练集和测试集
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

### 创建决策树分类器
dt_classifier = DecisionTreeClassifier()

### 在训练数据上拟合模型
dt_classifier.fit(X_train, y_train)

### 对测试数据进行预测
y_pred = dt_classifier.predict(X_test)

### 计算准确率
accuracy = accuracy_score(y_test, y_pred)
print("Accuracy:", accuracy)
```

请参考图 4.6 查看代码输出：

![](img/4.6.png)

**图 4.6：代码 4.3 的输出**

在这段代码中，我们加载鸢尾花数据集，这是一个经典的分类数据集。数据集被划分为训练集和测试集。我们使用 `scikit-learn` 中的 `DecisionTreeClassifier` 创建一个决策树分类器。模型在训练数据上进行训练（`fit`）。我们对测试数据进行预测并计算模型的准确率。

### 树诱导算法

树诱导算法用于从数据集构建决策树。这些算法决定如何在树的每个节点处分割数据集，最终创建一个可用于分类或回归的树结构。最流行的树诱导算法之一是分类与回归树（`CART`）算法。

### 分类与回归树

#### 分类与回归树 (CART)

分类与回归树 (CART) 是一种广泛用于构建决策树的算法。它既可应用于分类任务，也可应用于回归任务。CART 算法的核心思想是根据输入特征的值，将数据集递归地分割成子集，使得生成的子集尽可能“纯净”。在分类中，纯度是指子集中大多数数据点属于单一类别；在回归中，则是指子集具有相似的目标值。该算法的工作流程如下：

1.  **特征选择**：CART 选择最佳特征和最佳分割点，以最大化生成子集的纯度。它使用基尼不纯度作为分类标准，使用均方误差 (MSE) 作为回归标准。

2.  **分割**：根据选定的特征和分割点，将数据集分割成两个子集。

3.  **递归**：算法对每个子集递归地应用相同的过程，直到满足停止条件。这可能是最大树深度、节点中最小数据点数量或预定义的纯度水平。

4.  **叶节点预测**：当达到停止条件时，创建一个叶节点。在分类任务中，将节点中的多数类别指定为预测类别。在回归任务中，将节点中目标值的平均值指定为预测值。

5.  **剪枝**：树构建完成后，可能会进行剪枝以避免过拟合。剪枝涉及移除那些不能显著提升树性能的分支。
