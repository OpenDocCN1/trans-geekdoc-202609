

## 梯度下降方程的推导

梯度下降的更新方程由损失函数的一阶导数推导得出：

```
$$\hat{w}^{(n+1)} = \hat{w}^{(n)} - \eta \frac{\partial L(\hat{w}^{(n)})}{\partial \hat{w}^{(n)}} (3.8)$$
```

我们已经推导出了平方误差损失的一阶导数 $\frac{\partial L(w)}{\partial w}= -X^T(\mathbf{y}-X\mathbf{w})$，其结果为方程 (3.7)。

## 3.1.3 衡量多元回归的性能

回归模型性能最直观的衡量标准是**均方根误差 (RMSE)**，定义如下：

```
$RMSE = \sqrt{\frac{1}{N} \sum_{i=1}^{N} (y_i - \hat{y}_i)^2}.$ (3.9)$$
```

它与平方误差 **L(w)** 密切相关：$RMSE = \sqrt{\frac{2}{N}} L(w)$。由于它经过了样本数 $N$ 的归一化并进行了开根处理，因此它以目标值的单位提供了误差的有意义衡量。例如，如果目标值代表婴儿以周为单位的 GA，RMSE 也是以周为单位的平均误差。为了获得模型的最佳性能，我们需要最小化 RMSE，理想的 RMSE 为零。这与 $R^2$ 分数相反，$R^2$ 衡量模型对数据方差的解释比例（见 2.2.1 节），我们希望将其最大化，而最佳值为 1。在 scikit-learn 中，我们可以使用 `mean_squared_error` 函数计算回归模型的 RMSE：

```
from sklearn.metrics import mean_squared_error
from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X_train,y_train)
y_pred_train = model.predict(X_train)
RMSE_train = np.sqrt(mean_squared_error(y_train,y_pred_train))
```

这段代码计算了模型对训练数据的拟合程度，因此它衡量了偏差（bias）。为了识别过拟合，我们可以使用交叉验证，但这次我们定义了一个评分函数 `scoring=-neg_mean_squared_error`：

```
from sklearn.model_selection import cross_val_score
model = LinearRegression()
scores = cross_val_score(model,X_train,y_train,
  scoring='neg_mean_squared_error')
```

```
RMSE_CV = np.sqrt(-np.mean(scores))
```

## 回归 73

另一种方法是通过计算排除在训练集之外的测试集上的 RMSE 来发现过拟合：

```
model.fit(X_train,y_train)
y_pred_test = model.predict(X_test)
RMSE_test = np.sqrt(mean_squared_error(y_test, y_pred_test))
```

直观上，我们可能会认为特征越多预测效果越好，但情况真的是如此吗？让我们重新审视基于 164 次 MRI 扫描计算出的脑结构数据集（图 3.1）。第一个数据集有一个特征，第二个数据集有六个，第三个数据集有 86 个特征。表 3.1 给出了这三个数据集的 RMSE_train 和 RMSE_CV（单位为周）。

表 3.1 通过对整个训练集拟合回归模型得到的 RMSE (RMSE_train) 和使用交叉验证得到的 RMSE (RMSE_CV)。

| 特征数量 (周) | 1 | 6 | 86 |
|---|---|---|---|
| RMSE_train (周) | 1.56 | 1.12 | 0.68 |
| RMSE_CV (周) | 1.6 | 1.27 | 2.08 |

我们可以看到，训练集上的 RMSE (RMSE_train) 随着特征的增加而减小。然而，通过交叉验证的 RMSE_CV 并非如此。拟合到具有单个特征（全脑体积）六个体积的模型，我们通过较小的误差 (RMSE_train) 但较大的交叉验证误差 (RMSE_CV) 来判断这一点，这表明模型无法泛化到未见过的数据。事实上，具有 86 个特征的模型显然对数据中的噪声过度过拟合了。特征越多，模型的灵活性就越大，因为模型的参数数量（权重 w）随特征数量增加而增长。因此，具有大量特征的多元线性回归容易发生过拟合。

我们如何决定多少特征 D 对我们的模型是最优的？这取决于训练样本数 N。正规方程（方程 3.6）中最容易出错的部分是矩阵 $X^TX$ 的求逆。该矩阵的尺寸 $D+1 \times D+1$ 与特征数量有关。它的秩也取决于样本数 N，最大为 $\min(N, D+1)$，因为矩阵 $X$ 的尺寸为 $N \times (D+1)$。因此，如果样本数于于特征，即 $N < D+1$，矩阵 $X^TX$ 是不可逆的，存在许多能够精确拟合训练数据的解。在这种情况下，scikit-learn 的 `LinearRegression` 对象将选择 $[w]$ 最小的解。如果样本数 N 与特征数 D 相似且 $N \ge D+1$，则极有可能对噪声过拟合。如果 $N$ 远大于 $D$，则模型病态良好，且预测泛化良好。

## 3.1.4 练习

- 1. 使用 RMSE 和 $R^2$ 分数衡量回归算法的性能。描述这两个指标代表什么。
- 2. 表 3.2 给出了三个回归模型的性能。判断哪个模型具有最高偏差、最高方差以及最佳的偏差-方差平衡。

表 3.2 三个回归模型的性能。
| | 模型 1 | 模型 2 | 模型 3 |
|---|---|---|---|
| 训练集 $R^2$ 分数 | 0.97 | 0.85 | 0.92 |
| 交叉验证 $R^2$ 分数 | 0.68 | 0.81 | 0.89

- 3. 逗号分隔值 (CSV) 文件 'GA-brain-volumes-6-features.csv' 第一列包含 GA，第二列包含脑体积。执行以下任务：
    - 使用 Pandas 加载文件并提取特征矩阵和目标向量。打印特征和样本的数量。
    - 对数据拟合 `LinearRegression` 模型并计算 RMSE。
    - 创建函数 `RMSE(model,X)` 在整个数据集上拟合。
    - 创建函数 `RMSE_CV(model,X)` 通过交叉验证计算。
    - 使用 NumPy 实现梯度下降。
    - 4. 使用 NumPy 实现以下步骤：
        - 将数据集划分为训练和测试集。
        - 根据方程 (3.6) 在 NumPy 中拟合模型。
        - 根据方程 (3.3) 在测试集上预测。
    - 5. 从 'GA-brain-volumes-1-feature.csv' 和 'GA-brain-volumes-86-features.csv' 加载单特征和 86 个特征的数据集。

