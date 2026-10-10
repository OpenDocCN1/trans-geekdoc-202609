
```matlab
load fisheriris;
# meas 包含第 1 到 50 行的第一种物种，第 51 到 100 行的第二物种，
# 以及 101 到 150 行的第三种物种，而
# 列分别给出花萼长度、花萼宽度、
# 花瓣长度和花瓣宽度的测量。
# 提取两个物种和两个属性。
m = meas(1:100,1:2);
s = species(1:100);
# 绘制数据。
figure;
scatter(m(1,:),m(2,:),'rg','s','cs');
hold on;
# 生成属于类别 0 的二值真/假样本，接 50 个属于类别 1
s = zeros(100)+ones(50);
# 生成随机排列矩阵，以便使得
P = randperm(100);
# 创建随机流。
st = randn(100);
# 打乱数据。
m = m(P);
PerceptronModel = perceptron;
# 使用所有样本划分
s = s(P);
# 设置学习率为 1。
PerceptronModel.trainLr = 1;
# 指定最大 epoch 数。
PerceptronModel.train.epochs = 1000;
# 训练感知机。
PerceptronModel = train(PerceptronModel,m,s);
# 绘制分离线。
w = PerceptronModel.w(1);
b = PerceptronModel.b(1);
h = plot(w,b);\set(h,'Color','k');
# 标记图例。
legend('Versicolor','Location','Northeast');
xlabel('花萼长度');
ylabel('花萼宽度');
axis({4 7 1.5});
```

列表 4.2：MATLAB 中的感知机。Python 请访问 `https://github.com/ACoul/Linear-Classification-Python`。

![](img/c6c76bf52016db7e78a5e30d4766ef81_129_0.png)

(a) 看到 70% 的数据。

(b) 看到 80% 的数据。

(c) 看到 90% 的数据。

(d) 看到完整数据集。

(e) 完整看到一百次。

(f) 收敛。

> 图 4.8：感知机分类（未见数据标记为 ×）。

生成器改变数据的展示顺序会导致不同的分离线。

## 4.6 支持向量机

让学习率 `α` 成为一个粗略的选择。一切应由数据决定。当所有样本都被正确分类时，即 `c_n = sgn(w^T v_n)`，分离线的**间隔**定义为：

```
$\min_{n=1,\dots,N} \frac{\mathbf{w}^T\mathbf{v}_n}{\|\mathbf{w}\|} > 0$
```

支持向量机（SVM）尝试最大类别之间的间隔。

注意间隔与 `w` 的缩放无关，因为我们除了 `w` 的长度。我们利用缩放 `w` 的自由度使得对于 `n=1,\dots,N, c_n w^T v_n - 1 >= 0`，且对于每个样本取等号。在这些约束下，最大化间隔等同于最大化 `|w|^{-1}`。这里，等价问题是：**最小化目标函数** `|w|^2/2`，受到约束 `c_n w^T v_n - 1 >= 0`（对于所有 `n=1,\dots,N`）。这被称为*二次规划问题*。由于下文将的原因，这被称为*原始优化问题*。

![](img/c6c76bf52016db7e78a5e30d4766ef81_130_0.png)

图 4.9：目标函数、约束条件和梯度。

**图 4.9** 描述了二次规划问题。圆圈是 `||w||^2/2` 的等值线，即函数取值为常数的直线。在白色区域，不满足任何约束条件；在浅灰色区域，满足一个约束条件；在中灰色区域，满足两个约束条件；在深灰色区域，所有约束条件都得到了满足。这被称为**可行**（feasible）集合。在约束条件下的最小值位于可行集梯度距离圆圈最近的点。在该点处，`||w||^2/2` 的梯度是激活约束条件梯度的线性组合。在**图 4.9** 的插图中，这些约束中是激活的，而其中一个是非激活的。

**拉格朗日函数**（Lagrangian function）将目标函数和约束条件合并为一个。其形式如下：

```
L(\mathbf{w}, \alpha) = \frac{1}{2}\|\mathbf{w}\|^2 - \sum_{n} \alpha_n (c_n\mathbf{w}^T\mathbf{v}_n - 1),
```

其中 `α = (α_1, ..., α_n)^T` 是**拉格朗日乘子**（Lagrange multipliers），它们需要非负。对于特定的 `w`，如果约束 `c_n w^T v_n - 1 >= 0` 以严格不等式满足，则它为零且不对总和产生贡献。如果它以严格不等式满足，我们从目标函数中减去它；如果不满足，则将其加上。因此，如果 `w` 位于可行集合之外，将通过增加需要被最小化的目标函数来对其进行惩罚。

在**图 4.9** 中，垂直于约束条件的箭头是约束梯度乘以 `α_n` 的结果。虚线说明了这些向量相加形成了约束最小值处目标函数的梯度向量。

![](img/c6c76bf52016db7e78a5e30d4766ef81_131_0.png)

图 4.10：训练样本与新样本之间关系的加权。

函数

`L(α)=min_w L(w, α)`

是原优化问题的*对偶*（dual）函数。请注意，在可行集合中，`L(α)` 始终是 `||w||^2/2` 的下界。我们通过关于 `α` 最大化最小化问题来找到最大的下界。

当乘子 `α_n` 在约束非激活时为零，否则为正时，我们恢复原始的最小化问题。形式上，这写为：

`α_n(c_n^T v_n - 1) = 0`。

这一性质被称为*互补性*（complementarity）。如果情况如此，则最大下界和约束最小值是相同的。解是 `L(w, α)` 的一个驻点，其导数为零。利用 A.2.1 和 A.2.2，`L(w, α)` 相对于 `w` 的导数为：

```
$$\frac{d}{d\mathbf{w}}L(\mathbf{w}, \boldsymbol{\alpha}) = \sum_{n=1}^N \alpha_n c_n\mathbf{v}_n.$$
```

将其置为零等同于目标函数的梯度是约束梯度的线性组合。

代入

```
$$\mathbf{w} = \sum_{n=1}^N \alpha_n c_n\mathbf{v}_n,\quad(4.4)$$
```

![](img/c6c76bf52016db7e78a5e30d4766ef81_132_0.png)

图 4.11：支持向量机分类。

代入拉格朗日函数，我们寻找 `α` 使得对偶函数最大化：

`L(α) = sum_{n=1}^N α_n - 1/2 sum_{i=1}^N sum_{j=1}^N α_i α_j c_i v_i^T v_j,` 受到约束 `α_n >= 0` 和 `α_n (w^T v_n - 1) = 0, n = 1, ..., N`。这是最大化间隔问题的**对偶表示**（dual representation）。在形成权重向量 `w` 的线性组合中，`α_n != 0` 的样本被称为支持向量。如果是这种情况，最大下界和约束最小值是相同的。解是 `L(w, α)` 的驻点，其导数为零。使用 A.2.1 和 A.2.2，`L(w, α)` 相对于 `w` 的导数为：

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn import datasets
from sklearn import svm

n = datasets.load_iris()
# 创建一个实例
s = svm.SVC(kernel="linear", tol=1e-3)
# 在数据上训练
s.fit(n.data[:100], n.target[:100])

# 支持向量:
v = s.support_vectors
# 拉格朗日乘子:
lm = s.dual_coef_
# 计算权重
w = s.coef_

print("Weight vector:", w)
```

在 Python 中实现支持向量机。参考 `https://github.com/ACFaul/Linear-Classification-Matlab`。对于 MATLAB。

## 参考文献

Fisher, R. A. (1936), ‘The Use of Multiple Measurements in Taxonomic Problems’, *Annals of Eugenics* **7**(2), 179–188.

Rosenblatt, F. (1958), ‘The Perceptron: A Probabilistic Model for Information Storage and Organization in the Brain.', *Psychological Review* **65**(6), 386–408.

Vapnik, V. & Lerner, A. (1963), ‘Pattern Recognition using Generalized Portrait Method’, *Automation and Remote Control* **24**, 774–780.

# 非线性分类

到目前，我们假设数据可以用直线分开。然而，这种为线性分类所作的假设具有很强的限制性。在在此之前，我们需要回顾两个关键概念之间的细微差别：*概率*（probability）与*似然*（likelihood）。概率回答的问题是：一个属于类别 `C_i` 的样本具有这些特征的概率有多大？而似然回答的问题是：具有这些特征的样本属于类别 `C_i` 的可能性有多大？

有 `M` 个特征。假设类别 `C_i` 中样本的特征服从均值为 `μ_i`、方差为 `Σ_i` 的正态分布，`i=0, 1`。令 `v` 为特征向量。在给定 `v` 属于类别 `C_i` 的情况下，其概率密度为：

```
$p(\mathbf{v} \in C_i) = \frac{1}{\sqrt{(2\pi)^M|\Sigma_i|}} \exp\left(-\frac{1}{2}(\mathbf{v}-\mu_i)^T\Sigma_i^{-1}(\mathbf{v}-\mu_i)\right)$
```

在给定 `v` 的特征的情况下，其似然为：

```
$L(\mathbf{v} \in C_i) = \frac{1}{\sqrt{(2\pi)^M|\Sigma_i|}} \exp\left(-\frac{1}{2}(\mathbf{v}-\mu_i)^T\Sigma_i^{-1}(\mathbf{v}-\mu_i)\right)$
```

公式是相同的，但解释不同。

如果属于 `C_0` 的似然大于属于 `C_1` 的似然，则可以通过将 `v` 分配到类别 `C_0` 来构建分类器。类别之间的边界由：

`L(v ∈ C_0) = L(v ∈ C_1)`

这表示为似然比：

`L(v ∈ C_0)/L(v ∈ C_1) = sqrt((2π)^M|Σ_1|)/sqrt((2π)^M|Σ_0|) exp(-1/2 (v-μ_0)^T Σ_0^{-1} (v-μ_0)) / exp(-1/2 (v-μ_1)^T Σ_1^{-1} (v-μ_1)) = 1.`

![](img/c6c76bf52016db7e78a5e30d4766ef81_137_0.png)

图 5.1：二次判别分析。

取对数后，我们得到：

```
$$\mathcal{L}(v \in C_0(v)) = \frac{1}{2}\log|\Sigma_0|-\frac{1}{2}(v-\mu_0)^T\Sigma_0^{-1}(v-\mu_0)$$
$\mathcal{L}(v \in C_1(v)) = \frac{1}{2}(v-\mu_1)^T\Sigma_1^{-1}(v-\mu_1) +\frac{1}{2}(\log|\Sigma_1| + \mu_1^T\Sigma_1^{-1}\mu_1 - \mu_0^T\Sigma_0^{-1}\mu_0)$$
+v^T(\Sigma_0^{-1}-\Sigma_1^{-1}) + \frac{1}{2}v^T(\Sigma_1^{-1}-\Sigma_0^{-1})v = 0.$
```

因此，类别之间的边界由以下二次型给出：

```
$$\mathbf{A} = \frac{1}{2}(\Sigma_1^{-1}-\Sigma_0^{-1})$$$
$\mathbf{b} = \Sigma_0^{-1}\mu_0-\Sigma_1^{-1}\mu_1$
$c = \frac{1}{2}\log|\Sigma_0| + \mu_1^T\Sigma_1^{-1}\mu_1 - \mu_0^T\Sigma_0^{-1}\mu_0$$
```

```
$$\mathbf{v}^T\mathbf{A}\mathbf{v} + \mathbf{b}^T\mathbf{v} + c = 0.$$
```

这就是*二次判别分析*（QDA）。在两个特征的特殊情况下，边界是圆锥曲线，即直线、圆、椭圆、抛物线或双曲线。列表 5.1 展示了将二次判别分析应用于 Fisher 的鸢尾花数据，结果见图 5.1。

```matlab
load fisher;
% 提取属性
pl = mean(iris,:3); % 花瓣长度
pw = mean(iris,:4); % 花瓣宽度
```

## 5.2 核技巧

在二次情况下，矩阵 `A` 是对称的，因为 `A` 是协方差矩阵的差。假设 `M=2` 并写入：

```
$$\mathbf{A} = \begin{pmatrix} A_{11} & A_{12} \\ A_{12} & A_{22} \end{pmatrix}, \mathbf{b} = \begin{pmatrix} b_1 \\ b_2 \end{pmatrix}$$
```

边界方程可以写为：

`A11 v1^2 + 2 A12 v1 v2 + A22 v2^2 + b1 v1 + b2 v2 + c = 0`

现在我们可以将其重组为：

`(A11 A12 A22 b1 b2) (v1^2 v2^2) + c = 0`

令 `w^T = (A11 A12 A22 b1 b2)` 且 `v = (v1^2 v2^2 v1 v2)`，这描述了五维特征空间中的线性边界。

`w^T v + c = 0`

换句话说，我们通过三个人工特征扩展了特征空间：

`v1^2, v2^2, v1`

我们看到，映射 `φ` 永远不需要求值，只需要最大化目标函数的核 `k` 即可：

`L(α) = sum_{n=1}^{N} α_n - 1/2 sum_{i=1}^{N} sum_{j=1}^{N} α_i α_j c_{ij} (1 + k(v_i, v_j))`

受限于 `α_i >= 0, i = 1, ..., N`。分类根据以下内容的符号进行：

`-b + sum_{n=1}^{N} α_n c_n φ(v_n)^T v = -b + sum_{n=1}^{N} α_n c_n k(v_n, v)`

核技巧可以应用于所有的线性分类方法，以分离非线性可的数据。所有方法都减少了核函数 `k` 的计算。

核函数推导自高维内积。在上一章中，我们将内积视为样本之间关系的度量。例如，一个新样本的分类取决于它与一组支持向量的加权内积的相关性是否比另一组更高。核函数提供了一个描述两个样本之间关系的数值。
