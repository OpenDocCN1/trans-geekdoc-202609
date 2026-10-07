

## 主成分

PCA 识别出训练集中解释最大方差的轴。在图 8-7 中，它是实线。它还会找到与第一轴正交的第二个轴，该轴解释了最大的方差。在这个 2D 示例中没有选择：如果是高维数据集，PCA 还会找到与之前的轴正交的第三条轴，以及第四条、第五条，直到达到数据集的维度数量。

定义第 $i$ 个轴的单位向量被称为第 $i$ 个主成分（PC）。在图 8-7 中，第 1 个 PC 是 $c_1$，第 2 个 PC 是 $c_2$。在图 8-2 中前两个 PC 由平面上的正交箭头表示，而第 3 个 PC 将垂直于平面（向上或向下）。

主成分的方向是不稳定的：如果我们对集合进行轻微扰动并再次运行 PCA，某些新的 PC 可能会指向原始 PC 相反的方向。然而，它们仍然位于相同的轴上。在某些情况下，一对 PC 甚至可能会旋转或交换，但它们定义的平面将保持不变。

![](img/0684d2da98e09085c0a622d4fd69aaad_248_0.png)

如何找到训练集的主成分？幸运的是，有一种标准的矩阵分解技术称为奇异值分解（SVD），它可以将训练集 $X$ 分解为三个矩阵的乘法乘积 $U \Sigma^T V$，其中 $V$ 包含了我们寻找的所有主成分，如方程 8-1 所示。

方程 8-1. 主成分矩阵

```
V = | c_1 c_2 ... c_n |

```

接后的 Python 代码使用 NumPy 的 `svd()` 函数获取训练集的所有主成分，并提取前两个 PC：

```python
X_centered = X - X.mean(axis=0)
U, s, Vt = np.linalg.svd(X_centered)
c1 = Vt.T[:, 0]
c2 = Vt.T[:, 1]
```

PCA 假设数据集是以原点为中心化的。正如我们将看到的，Scikit-Learn 的 PCA 类会替你处理数据的中心化工作。然而，如果你自己实现 PCA（如前面的示例所示），或者使用其他库，请忘记先对数据进行中心化。

## 投影到 d 维

一旦确定了所有主成分，你就可以通过投影到由前 $d$ 个主成分定义的超平面，将数据集的维度降低到 $d$ 维。选择这个超平面可以确保投影尽可能地保留方差。例如，在图 8-2 中，3D 数据集投影到由前主成分定义的 2D 平面上，保留了数据集的大部分方差。结果2D 投影看起来非常像原始 3D 数据集。

要将训练集投影到超平面，你只需计算训练集 $X$ 与矩阵 $W_d$ 的矩阵乘法，其中 $W_d$ 是包含前 $d$ 个主成分的矩阵（即由 $V$ 的前 $d$ 列组成的矩阵），如方程 8-2 所示。

方程 8-2. 将训练集投影到 d 维

```
X_{d-proj} = XW_d
```

下面的 Python 代码将训练集投影到由前主成分定义的平面上：

```python
W2 = Vt.T[:2]
XD = X_centered.dot(W2)
```

大功告！你现在知道如何将任何数据集的维度降低到任意维数，同时尽可能地保留方差。

## 使用 Scikit-Learn

Scikit-Learn 的 PCA 类使用 SVD 分解来实现 PCA，就像我们之前做一样。下面的代码应用 PCA 将数据集的维度降低到两个维度（它会自动处理数据的中心化）：

```python
from sklearn.decomposition import PCA

pca = PCA(n_components=2)
XD = pca.fit_transform(X)
```

在对数据集拟合 PCA 转换器后，你可以使用 `components_` 变量访问主成分（注意它以水平向量的形式包含 PC，因此例如，第一个主成分等于 `pca.components_.T[:, 0]`）。

### 解释方差率

另一个非常有用的信息是每个主成分的解释方差率，可以通过 `explained_variance_ratio_` 变量获取。它表示数据集的方差沿每个主成分轴分布的比例。例如，让我们看看图 8-2 所示 3D 数据集前两个组件的解释方差：

```python
>>> pca.explained_variance_ratio_
array([0.84248607, 0.14631839])
```

这告诉你数据集 84.2% 的方差沿第一轴分布，14.6% 沿第二轴分布。这为第三条轴留下了少于 10% 的空间。

### 选择维度

与其任意选择维度，不如选择能保留 95% 方差的维度。下面的代码计算了保留 95% 方差所需的最小维度数：

```python
pca = PCA()
pca.fit(X)
cumsum = np.cumsum(pca.explained_variance_ratio_)
d = np.argmax(cumsum >= 0.95) + 1
print(f"Number of dimensions: {d}")
```

另一个选项是将解释方差绘制为维度的函数图。你可以看到重建误差中有一个“肘部”：

```python
pca = PCA(n_components=d)
X_reduced = pca.fit_transform(X)
X_recovered = pca.inverse_transform(X_reduced)
error = np.mean((X - X_recovered)**2)
print(f"Reconstruction error: {error}")
```

