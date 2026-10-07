

# 10.6 PCA 详解：第3部分 - 应用 PCA

在本节中，我们将涵盖以下部分：拟合逻辑模型、预测、混淆矩阵以及可视化部分。由于独立变量尚未固定，以下是我们接下来的操作步骤：

- 导入 PCA
- 首次对所有 13 个独立变量应用 PCA：检查所有 13 个变量及其对数据的影响（即方差）。
- 寻找最独立的独立变量，即主成分 - PC。
- 然后我们将对 2 个独立变量进行第二次 PCA 应用。（在找到 PC 的数量后：我们只需要在 PCA 对象中固定该数量。）

```python
# 库导入
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# 数据提取
dataset = pd.read_csv("data.csv")
X = dataset.iloc[:, :13].values
y = dataset.iloc[:, 13].values

# 数据划分
from sklearn.model_selection import train_test_split
# 0.20 test_size 意味着总观测值的 "2/10"
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.20, random_state=0)

# 预处理
from sklearn.preprocessing import StandardScaler
# y 需要进行标准化
st = StandardScaler()
X_train = st.fit_transform(X_train)
X_test = st.transform(X_test)

# 应用 PCA
# 将数据集拟合到逻辑回归
from sklearn.linear_model import LogisticRegression # 导入类
# 我们现在使用 "classifier" 而不是 "regressor"
classifier = LogisticRegression(random_state=0) # 创建对象
classifier.fit(X_train, y_train) # 拟合数据集

# 预测
y_pred = classifier.predict(X_test)
# 使用函数 "confusion_matrix" 生成混淆矩阵
# 类名大写，函数名小写
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_train, y_test, y_pred)
# cm 的参数：y_true: 真实值，y_pred: 预测值

# 可视化训练集结果
from matplotlib.colors import ListedColormap
X_set, y_set = X_train, y_train
X1, X2 = np.meshgrid(np.arange(X_train[:, 0].min(), X_train[:, 0].max() + 1, 0.01), np.arange(X_train[:, 1].min(), X_train[:, 1].max() + 1, 0.01))
plt.contour(X1, X2, np.array(y_train).reshape(X1.shape), alpha=0.03, cmap=ListedColormap(['red', 'green']))
plt.contour(X1, X2, np.array(y_test).reshape(X1.shape), cmap=ListedColormap(['red', 'green', 'orange']))
for i, j in enumerate(np.unique(y_set)):
    plt.scatter(X_set[j,0], X_set[:,1], c=ListedColormap(['red', 'green', 'orange'])(i), Label = j)
plt.title('Logistic Regression (training set)')
plt.legend()
plt.show()

# 可视化测试集结果
from matplotlib.colors import ListedColormap
```

导入 PCA：我们首先导入正确的包以及精确的类来作为 PCA。然后我们创建该类的对象，并分别在训练集和测试集上使用 `fit_transform` 和 `transform` 方法。

```python
from sklearn.decomposition import PCA
decompose_pca = PCA(n_components=None)

X_train = decompose_pca.fit_transform(X_train)
X_test = decompose_pca.transform(X_test)
```

通过对此 `decomposition_pca` 对象应用 `fit_transform` 方法，我们可以看到训练集是如何被**结构化**并转换的。对象被拟合到训练集，然后我们使用 `transform` 方法来转换测试集 **X_test**。

这将同时处理我们的**训练集**并对其进行**转换**，即提取所有的 **PCs**。

**n_components**: int, float 或 None，默认值=None

要保留的成分数量。如果未设置 `n_components`，则保留所有成分。它是你为了解释最大方差而想要获取的**提取特征**的数量。我们根据想要解释多少比例的方差来选择数量。

目前我们使用 `n_components=None`，因为我们想要获得两个**主成分**来可视化结果，但我们不知道这两个成分解释了多少方差。

我们需要确保确保解释方差的前两个主成分（PCs）解释的不是很小的方差。

我们使用 None 是因为我们通过 PCA 属性 `explained_variance_ratio_` 创建了一个向量 `explained_variance`，以查看每个主成分的累积百分比。

**explained_variance_ratio**: 返回我们提取的所有每个主成分所解释的百分比列表。

```python
explained_variance_ratio = decompose_pca.explained_variance_ratio_
```

```python
from sklearn.decomposition import PCA
decompose_pca = PCA(n_components=None)
X_train = decompose_pca.fit_transform(X_train)
X_test = decompose_pca.transform(X_test)
explained_variance = decompose_pca.explained_variance_ratio_
```

现在我们可以查看此返回的、主成分的解释方差 `explained_variance`。

- 在**方差向量**中，由于我们最初有 13 个独立变量，我们提取了 13 个主成分。这些是解释**最多**方差的**提取独立变量**。

- 你可以看到它们的**排序**，从解释**最多****方差**的第一个 ($$0^{th}$) PC 到第 12 个和最后一个第 13 个解释**最少****方差**的 PC。

第一个 PC 将解释 37% 的方差。第二个 PC 将解释 19% 的方差。
所以如果我们取两个 PC，它们将解释 37% + 19% = 56% 的方差。

对于 3D 可视化，如果我们取三个 PC，将解释 37 + 19 + 11 = 67%。

- 我们选择前两个 PC 是因为我们可以获得结果的 2D 可视化。
- 解释 56% 的方差对于分类来说已经不错了。

现在我们编辑上面的 PCA 代码段，并将 n_components 替换为：
n_components = 2

```python
from sklearn.decomposition import PCA
# dcm_pca = PCA(n_components=None)
dcm_pca = PCA(n_components=2)
X_train = dcm_pca.fit_transform(X_train)
X_test = dcm_pca.transform(X_test)
explained_variance_ = dcm_pca.explained_variance_ratio_
```

然后 pca 对象 dcm_pca 将返回 2 个最独立的变量（代表 2 个 PC）。X_train 和 X_test 将从 3D 矩阵转换为 2D 矩阵。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_329_0.png)

- 这两个 PC 是解释最多方差的前两个独立变量。
- 这两个 PC 是前两个独立变量（原始为 13 个）。我们查看 X_train，而 X_test 现在只包含两个独立变量。
- 这两个 PC 是解释最多方差的前两个独立变量。

# 10.7 Python 中的 PCA：第4部分 - 逻辑回归与结果可视化

我们准备好拟合一个逻辑模型来对它们所属的类别进行分类。我们将预测结果并使用混淆矩阵评估性能。

```python
from sklearn.linear_model import LogisticRegression # 导入类
# 我们现在使用 "classifier" 而不是 "regressor"
classifier = LogisticRegression(random_state=0) # 创建对象
classifier.fit(X_train, y_train) # 拟合数据集

# 预测
y_pred = classifier.predict(X_test)

# 使用函数 "confusion_matrix" 生成混淆矩阵
# 类名大写，函数名小写
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_train, y_test, y_pred) # y_true: 真实值，y_pred: 预测值
```

## 混淆矩阵：

在这里我们看到带有两个提取主成分的分类模型。

由于这些 PC 是为了解释方差而选择的，它们解释了大约 60% 的方差。因此我们应该获得很好的准确率，因为我们的两个 PC 实际上是数据集中方差最大的方向。

这是一个带有三个类的混淆矩阵，所以它不会是 2x2 的混淆矩阵，但由于我们有三个类，这将是一个 3x3 的混淆矩阵。

你可以看到我们获得了结果，因为在对角线上我们将获得正确的预测。

- 对第一组客户类别的 14 次正确预测。
- 对第二组客户类别的 15 次正确预测。
- 对第三组客户类别的 6 次正确预测。

使用 PCA 我们得到了非常好的预测。在 36 次总观测值中有 35 次正确预测。即 35/37 = 97.2% 的准确率。

可视化：我们编辑变量的标签。

并使用 3 种颜色来可视化我们的三个 customer_segments。

```python
ListedColormap(['red', 'green', 'orange'])
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_330_0.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_330_1.png)

