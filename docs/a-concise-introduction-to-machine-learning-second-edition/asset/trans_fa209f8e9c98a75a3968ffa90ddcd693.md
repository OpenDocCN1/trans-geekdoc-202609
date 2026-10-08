

![](img/c6c76bf52016db7e78a5e30d4766ef81_125_0.png)

(a)

(b)

(c)

![](img/c6c76bf52016db7e78a5e30d4766ef81_125_1.png)

(d)

(e)

(f)

图 4.6：使用不同特征的分类。

均值

$\mu = \frac{1}{K} \sum_{i=1}^{K} \mu_i.$

**类间散度**定义为

$\Sigma_b = \frac{1}{K} \sum_{i=1}^{K} (\mu_i - \bar{\mu})(\mu_i - \bar{\mu})^T$

在 **w** 方向上的类间间隔为

$s(\mathbf{w}) = \frac{\mathbf{w}^T \Sigma_b \mathbf{w}}{\mathbf{w}^T \Sigma_w \mathbf{w}}$

为了分离 $K$ 个类，我们需要找到方向 $\mathbf{w}_1, \dots, \mathbf{w}_{K-1}$ 使得 $s(\mathbf{w})$ 最大。这等价于最大化

$\mathbf{S}(\mathbf{W}) = \frac{[\mathbf{W}^T \Sigma_b \mathbf{W}]}{[\mathbf{W}^T \Sigma_w \mathbf{W}]}$

其中 $\mathbf{W}$ 表示列为向量 $\mathbf{w}_1, \dots, \mathbf{w}_{K-1}$ 的矩阵，$|\cdot|$ 表示矩阵的行列式。如果特征数 $M$ 大于或等于类别数 $K$，可以证明，当 $\mathbf{w}_1, \dots, \mathbf{w}_{K-1}$ 是对应于广义特征值问题 $K-1$ 个最大广义特征值的广义特征向量，则 $S(\mathbf{W})$ 取最大：

$\Sigma_B \mathbf{w} = \lambda \Sigma_W \mathbf{w}.$

这在 MATLAB 中通过 `ClassificationDiscriminant.fit` 实现。而在 Python 中的实现是 `sklearn.discrimin_analysis.LinearDiscriminantAnalysis`。

如图 4.6 所示，某些特征比其他特征更有用。我们在讨论特征选择时会进一步探讨这一点。当类别重叠时，需要考虑进入另一个类别区域的样本是离群点，还是无法使用这些特征进行分离。

## 4.5 在线学习与感知机

到目前为止，我们考虑的是训练数据预可用的学习任务。这被称为批量学习或离线学习。相反，在在线学习中，训练数据按顺序出现。

回想我们寻找一个方向向量 $\mathbf{w}$ 和间隔阈值 $b$，使得对于样本 $\mathbf{v}$：

- $\mathbf{w}^T\mathbf{v} < b \Rightarrow$ $\mathbf{v} \in C_0$,
- $\mathbf{w}^T\mathbf{v} > b \Rightarrow$ $\mathbf{v} \in C_1$。

通过将向量 $\mathbf{w}$ 扩展为 $\mathbf{\hat{w}}=\mathbf{w}-b$ 以及 $\mathbf{\hat{v}}=(1,\mathbf{v})$，可以重新表述为：

- $\mathbf{\hat{w}}^T\mathbf{\hat{v}} - b < 0 \Rightarrow$ $\mathbf{\hat{v}} \in C_0$，
- $\mathbf{\hat{w}}^T\mathbf{\hat{v}} - b > 0 \Rightarrow$ $\mathbf{\hat{v}} \in C_1$。

这样，偏置 $b$ 就变成了权重向量的一部分。
我们定义函数：

```
sgn(x) = \begin{cases} -1 & \text{if } x < 0 \\ 0 & \text{if } x = 0 \\ 1 & \text{if } x > 0 \end{cases}
```

## 硬限制

| 输入 | | 输出 |
|---|---|---|
| 2 | W, b | 3 |

图 4.7：感知机。

对于样本 $v$

```
$$sgn(w^T v) = -1 \Rightarrow v \in C_0,$$
sgn(w^T v) = 1 \Rightarrow v \in C_1. \quad (4.3)
```

Rosenblatt (1958) 发明了感知机。它是一台用于图像识别的物理机器。它包含 400 个光电池，权重由电位器实现，并通过电动机进行更新。
具体来说，感知机初始化 $w_0 = 0$，并在每个新训练样本 $v_i$ 更新权重 $w_{i-1}$：

```
$$\mathbf{w}_i = \mathbf{w}_{i-1} + (c_i - sgn(\mathbf{w}_{i-1}^T v_i)) \mathbf{v}_i.$$
```

其中 $c_i$ 是 $v_i$ 的类别标签，如果 $v_i \in C_0$ 则 $c_i = -1$，如果 $v_i \in C_1$ 则 $c_i = 1$。
参数 $0 < \alpha \leq 1$ 是学习率，由用户设置。如果学习率选择太大，任何变化将是剧烈的且会发生震荡。
注意 $\mathbf{w}_i$ 与 $\mathbf{w}_{i-1}$ 相关。如果类别标签确定错误，分离线将向某个方向拉，使得样本被正确标记的概率更大。$c_i - sgn(\mathbf{w}_{i-1}^T v_i)$ 的符号决定了分离线拉动的方向。在任何阶段，权重向量 $\mathbf{w}_i$ 都是迄今为止样本的线性组合。

感知机在 MATLAB 的神经网络框架内实现为单层网络（见图 4.7 和列表 4.2）。在考虑非线性分类时，我们会仔细观察神经网络。
感知机需要看到示例来建立分离线。一个 epoch（周期）是指向算法完整展示一次数据。
图 4.8 显示了感知机看到一定数量数据后不同的分离线。未见的数据用 $\times$ 标记。学习率设置为 1。由于这个值很大，在看到 90% 数据和看到完整数据集之间，分离线的位置发生了剧烈变化。
在 100 个 epoch 之后，感知机分类了除一个离群点以外的所有样本。感知机需要几百个 epoch 才能正确分类这个样本。给随机数赋予不同的种子：

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

列表 4.2：MATLAB 中的感知机。Python 请访问 https://github.com/ACoul/Linear-Classification-Python。

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

让学习率 $\alpha$ 成为一个粗略的选择。一切应由数据决定。当所有样本都被正确分类时，即 $c_n = sgn(\mathbf{w}^T\mathbf{v}_n)$，分离线的**间隔**定义为：

```
$\min_{n=1,\dots,N} \frac{\mathbf{w}^T\mathbf{v}_n}{\|\mathbf{w}\|} > 0$
```

支持向量机（SVM）尝试最大类别之间的间隔。

注意间隔与 $\mathbf{w}$ 的缩放无关，因为我们除了 $\mathbf{w}$ 的长度。我们利用缩放 $\mathbf{w}$ 的自由度使得对于 $n=1,\dots,N, c_n\mathbf{w}^T\mathbf{v}_n - 1 \ge 0$，且对于每个样本取等号。在这些约束下，最大化间隔等同于最大化 $|\mathbf{w}\|^{-1}$。这里，等价问题是：**最小化目标函数** $|\mathbf{w}\|^2/2$，受到约束 $c_n\mathbf{w}^T\mathbf{v}_n - 1 \ge 0$（对于所有 $n=1,\dots,N$）。这被称为*二次规划问题*。由于下文将的原因，这被称为*原始优化问题*。

