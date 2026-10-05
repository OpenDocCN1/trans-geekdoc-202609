
AUC 值的标准差有所减小。这表明刀法检验（Jackknife test）是最稳健的方法，因为它不依赖于对种群的随机采样。图 3.19 显示了这一比较。

针对种子（seeds）数据还构建了 LR 模型和 GDA 模型。表 3.5 显示了这两个模型的混淆矩阵。它们的性能与 LDA 相似。图 3.20 显示了 LR 和 GDA 模型在种子数据集上的 ROC 曲线。两个模型的性能差异非常显著。

表 3.5. LR 模型和 GDA 模型针对种子数据的混淆矩阵。

| | LR A B % | GDA A B % |
|---|---|---|---|---|---|---|
| A | 63 | 8 | 88.7 | 61 | 10 | 85.9 |
| B | 4 | 61 | 93.8 | 3 | 61 | 93.8 |
| % | 94.0 | 88.4 | 90.0 | 93.8 | 85.9 | 88.5 |

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_128_0.png)

Fig. 3.20. LR 和 GDA 模型针对种子数据的 ROC 曲线。

## 3.6 非线性算法

除了线性判别分析算法外，还有几种非线性判别分析算法，例如多层感知器（或人工神经网络）、基函数神经网络、支持向量机、随机森林算法以及深度神经网络。

## 蛋白酶切割模式发现

### 3.6.1 多层感知器 (MLP)

多层感知器（MLP）或人工神经网络是一类用于模式分析的算法 [Rumelhart, et al., 1986; Bishop, 1996]。MLP 源于大脑研究和现代计算技术。它也被称为信息处理系统，因为它可以用于大规模数据挖掘过程中的知识发现和记忆关联。典型案例是 MLP 可以用于发现数据背后的模式，并在无需先验模式函数形状的情况下对其进行重构。使 MLP 成为卓越智能处理系统最重要的特征是它具有存储从数据集中学习到的知识或智能的能力。由于这种强大性，MLP 已广泛应用于生物和医学等许多领域的模式发现和识别。例如，它已用于基于小鼠模型的炎症性肠病的治疗 [Sabater, et al., 2019]。另一近期使用 MLP 的研究是通过学习复杂多细胞类型样本的非线性基因关系来研究生成单细胞 RNA-seq [Marouf, et al., 2020]。

#### 3.6.1.1 MLP 的结构

图 3.21 显示了 MLP结构的一个示例，其中包含三层称为神经元的计算单元：有一层输入神经元（$x_1$ 和 $x_2$）、一层隐藏神经元（$z_1$ 和 $z_2$）和一层输出神经元（$y$）。假设

```
$z_1 = f_1(x_1, x_2)$
z_2 = f_2(x_1, x_2)$
y = f_3(z_1, z_2)$ $\quad\quad (3.29)
```

因变量 $y$ 随后是自变量 $x_1$ 和 $x_2$ 的复合函数，

```
$y = f_3\{f_1(x_1, x_2), f_1(x_1, x_2)\}$ $\quad\quad (3.30)
```

## 使用 R 进行生物模式发现

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_130_0.png)

Fig. 3.21. 一个具有两个输入神经元、两个隐藏神经元和一个输出神经元的 MLP。

计算节点用于处理信息和信息传输最常用的函数称为 sigmoid 函数。所有三个函数（$f_1, f_2$ 和 $f_3$）都使用这种 sigmoid 函数进行信息的处理、存储和跳过，其中 sigmoid 函数的输入是来自下层神经元的加权信号。图 3.22 显示了 sigmoid 函数。sigmoid 函数将区间 $(-\infty, \infty)$ 转换为区间 $(0, 1)$。例如，$z_1$ 的输入如下所示，其中 $x_1$ 和 $x_2$ 是下层（输入层）神经元（或信号），

$w_{11} \times x_1 + w_{12} \times x_2 \quad\quad (3.31)$

$z_1$ 的输出定义为 sigmoid 函数，如下所示，

$1 + e^{-w_{11}x_1-w_{12}x_2} \quad\quad\quad (3.32)$

$z_2$ 的输出和 $y$ 的输出采用类似的函数。

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_130_1.png)

Fig. 3.22. sigmoid 函数。x坐标是输入，y 坐标是输出。

## 蛋白酶切割模式发现

### 3.6.1.2 MLP 的机制

为了估计 MLP 的参数，简单的方法是

```
$\varepsilon = \frac{1}{N} \sum_{n=1}^{N} (\hat{y}_n - y_n)^2 \quad\quad (3.33)$
```

由于 $\hat{y}_n$ 是线性的，参数估计非常困难。

```
$\frac{\partial \varepsilon}{\partial w} = \frac{2}{N} \sum_{n=1}^{N} (\hat{y}_n - y_n) \frac{\partial \hat{y}_n}{\partial w} \quad\quad (3.34)$
```

导数 $\frac{\partial \hat{y}_n}{\partial w}$ 使用链式法则计算：

```
$\frac{\partial \hat{y}_n}{\partial w} = \frac{\partial \hat{y}_n}{\partial z_j} \frac{\partial z_j}{\partial w} \quad\quad (3.35)$
```

导数 $\frac{\partial \hat{y}_n}{\partial z_j}$ 使用 sigmoid 函数计算：

```
$\frac{\partial \hat{y}_n}{\partial z_j} = \hat{y}_n(1 - \hat{y}_n) \quad\quad (3.36)$
```

导数 $\frac{\partial z_j}{\partial w}$ 使用以下公式计算：

```
$\frac{\partial z_j}{\partial w} = x_i \quad\quad (3.37)$
```

导数 $\frac{\partial \varepsilon}{\partial w}$ 则为：

```
$\frac{\partial \varepsilon}{\partial w} = \frac{2}{N} \sum_{n=1}^{N} (\hat{y}_n - y_n) \hat{y}_n(1 - \hat{y}_n) x_i \quad\quad (3.38)$
```

$w$ 的更新计算为：

```
$w^{t+1} = w^t - \eta \frac{\partial \varepsilon}{\partial w} \quad\quad (3.39)$
```

随后通过引入动量改进了 $w$ 的更新：

```
$w^{t+1} = w^t - \eta \frac{\partial \varepsilon}{\partial w} + \alpha \Delta w^t \quad\quad (3.40)$
```

其中 $\Delta w^t = w^t - w^{t-1}$。这是带有动量的反向传播算法。

