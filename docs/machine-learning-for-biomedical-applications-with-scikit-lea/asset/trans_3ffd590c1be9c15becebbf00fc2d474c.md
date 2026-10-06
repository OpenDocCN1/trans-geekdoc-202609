
机器学习基础 61

- 为训练数据拟合多项式模型；
- 使用交叉验证调优超参数多项式次数；
- 在测试集上评估性能。

## 生成数据

首先，我们把真实模型 $y = 2x^2 + 4x + 5$ 定义为一个函数：

```python
def TrueModel(x):
    return 2*x**2+4*x+5
```

接下来，我们从区间为 $[-3, 3]$ 的均匀分布中生成包含 $n = 100$ 个随机特征的数组 $X$。可以使用 `numpy` 函数 `rand` 实现：

```python
import numpy as np
n=100
X = 6*np.random.rand(n)-3
```

为了生成带噪声的目标值，我们首先使用 `numpy` 函数 `randn` 生成 $\sigma = 3$ 的高斯噪声：

```python
noise = 3*np.random.randn(n)
```

通过计算真实目标值并加上噪声即可得到带噪声的目标值 $y$：

```python
y = TrueModel(X) + noise
```

最后，将特征矩阵 $X$ 转换为 2 数组：

```python
X = X.reshape(-1,1)
```

## 训练测试集划分

Scikit-learn 提供了 `train_test_split` 函数来执行数据集的划分。一种模式是保留 80% 的数据用于训练，20% 用于测试。这可以通过选项 `test_size` 进行设置。注意，反斜杠允许将长命令拆分为两行。

```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = \
    train_test_split(X,y,test_size =0.2)
```

如果我们想创建一个具有代表性的测试集，可以使用 `stratify` 参数。在本例中，我们将通过对特征值取舍入将数据分为七个箱（bins），并对测试集进行分层，以确保每个箱的数据比例与训练集相同：

## 生物医学应用中的机器学习

```python
bins = np.round(X)
X_train, X_test, y_train, y_test = \
train_test_split(X,y,test_size =0.2, \
stratify =bins)
```

## 拟合多项式模型

Scikit-learn 没有直接实现多项式回归模型。相反，多项式回归分两个步骤执行：

- 1. 多项式特征转换——转换器对象 `PolynomialFeatures` 将每个特征转换为特征向量 $(1, x, x^2, ..., x^M)$，其中次数 $M$ 通过设置参数 `degree` 来定义；
- 2. 执行多元线性回归——回归器对象 `LinearRegression` 对数据进行拟合模型 $y = x_0 + x_1y_1 + ... + x_My_M$。

如果我们这些这些结合起来，就会有 $x_i = x'$，从而创建一个多项式模型 $y = x_0 + x_1x' + ... + x_Mx'$。这两个步骤的实现方式如下：首先我们进行多项式特征转换：

```python
from sklearn.preprocessing import PolynomialFeatures
poly_features = PolynomialFeatures(degree=M)
x_train_poly = poly_features.transform(X_train)
```

然后我们创建并拟合 `LinearRegression`。注意，在 `LinearRegression` 模型中不需要截距，因为我们已经生成了特征 $x_0 = 1$。因此，在创建 `LinearRegression` 对象时我们将设置 `fit_intercept=False`：

```python
from sklearn.linear_model import LinearRegression
model = LinearRegression(fit_intercept=False)
model.fit(X_train_poly, y_train)
```

## 设置模型流水线

执行模型训练、预测和评估的多个步骤并不总是方便的。如果模型成为另一个 sklearn 对象的输入（例如我们将介绍的交叉验证超参数搜索），则需要将步骤统一到单个对象中。Scikit-learn 使用 `Pipeline` 将多个步骤合并为一个模型。它实现了 `fit`、`predict`、`score` 等方法，与其他 sklearn 对象提供统一的 API。接下来，我们将多项式特征转换和多元线性回归合并到一个流水线中：

```python
from sklearn.pipeline import Pipeline
pipeline = Pipeline(( 
("poly_features", PolynomialFeatures(degree=2)),
("lin_reg", LinearRegression(fit_intercept=False)) ))
```

让我们详细查看创建流水线的语法。它的格式为 `Pipeline(steps)`，其中输入参数 `steps` 是要链的转换器和模型的列表，按照它们调用的顺序排列。每个步骤由元组 `(name, model)` 描述，其中 `name` 是用户使用的字符串，`model` 是一个 sklearn 对象。流水线可以像上面所示那样对数据进行拟合：

```python
pipeline.fit(X_train, y_train)
```

要访问 Pipeline 中的原始对象，我们使用属性 `named_steps`。例如，访问线性回归对象的方式为：

```python
pipeline.named_steps["lin_reg"]
```

线性回归的系数 $w_0, ..., w_k$ 可以通过以下方式访问：

```python
>>> pipeline.named_steps["lin_reg"].coef_
>>> array([4.98164783, 3.7729512, 1.90766111])
```

（注：原文此处存在大量重复段落，已根据要求去重，仅保留核心逻辑翻译）

（此处省略重复的 Pipeline 访问描述...）

（注：由于原始文本包含大量重复的关于 `named_steps` 的访问描述，作为高级文档工程师已对其进行冗余处理。）

## 2.3.6 练习题

- 1. 在第 2 节中，你获得了生成噪声数据集和二阶多项式模型的代码。编写代码来可视化拟合的曲线和原始数据。尝试拟合的多项式次数，并观察模型的变化。
2. 对模拟数据集执行不同次数的多项式拟合交叉验证，并观察 $R^2$ 分数的变化。
3. 使用 pandas 加载 `noisy_data.csv`。该文件包含两列：
   - 第一列包含特征 $X$；
   - 第二列包含目标值 $y$。
* 为数据拟合多项式模型。执行以下步骤：
* 执行分层训练测试集划分；
* 使用 `Pipeline` 创建多项式模型；
* 使用 `GridSearchCV` 找到最优多项式次数，并打印最佳交叉验证分数；
* 计算测试集上的性能；
* 绘制拟合模型图；
* 打印模型的系数。
你能推断出底层的多项式模型是什么吗？（提示：系数是整数。）

