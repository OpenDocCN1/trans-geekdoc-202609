
![](img/c6c76bf52016db7e78a5e30d4766ef81_112_0.png)

(a) $\mathbf{x}_1 = \mu, \sigma = \sigma_{min}$

![](img/c6c76bf52016db7e78a5e30d4766ef81_112_1.png)

(b) $\mathbf{x}_1 = (0,0)^T, \sigma = \sigma_{min}$.

![](img/c6c76bf52016db7e78a5e30d4766ef81_112_2.png)

(c) $\mathbf{x}_1 = \mu, \sigma = \sigma_{min}/2$.

![](img/c6c76bf52016db7e78a5e30d4766ef81_112_3.png)

(d) $\mathbf{x}_1 = \mu, \sigma = 2 * \sigma$.

图 3.6：针对不同初始化和 $\sigma$ 选择的 Metropolis 算法。

## Metropolis-Hastings 算法

Metropolis-Hastings 算法扩展了 Metropolis 方法，使其可以使用非对称的提议分布。在这种情况下，候选者 $\mathbf{x}^*$ 的接受概率计算为

$$\min \left(1, \frac{f(\mathbf{x}^*)g(\mathbf{x}_n, \mathbf{x}^*)}{f(\mathbf{x}_n)g(\mathbf{x}^*, \mathbf{x}_n)}\right) = \min \left(1, \frac{f(\mathbf{x}^*)g(x, x^*)}{f(x)g(x^*, x)}\rightright)$$

从 $\mathbf{x}$ 到 $\tilde{\mathbf{x}}$ 的转移概率由下给出

$$T(\mathbf{x}, \tilde{\mathbf{x}}) = \min \left(1, \frac{f(\tilde{\mathbf{x}})g(\tilde{\mathbf{x}}, \mathbf{x})}{f(\mathbf{x})g(\mathbf{x}, \tilde{\mathbf{x}})}\right)$$

我们现在检查 $f$ 是否满足详细平衡。为此，

$$f(\mathbf{x})T(\mathbf{x}, \mathbf{x}') = \begin{aligned} &\hat{f}(\mathbf{x})g(\mathbf{x}, \mathbf{x}') \min \left(1, \frac{\hat{f}(\mathbf{x}')g(\mathbf{x}', \mathbf{x})}{f(\mathbf{x})g(\mathbf{x}, \mathbf{x}')}\right) &=\frac{1}{c_f} \min(f(\mathbf{x})g(\mathbf{x}, \mathbf{x}'), \hat{f}(\mathbf{x}')g(\mathbf{x}', \mathbf{x}')) \&=\frac{1}{c_f} \min(f(\mathbf{x})g(\mathbf{x}, \mathbf{x}'), \hat{f}(\mathbf{x}')g(\mathbf{x}', \mathbf{x}')) \&=\frac{1}{c_{f'}} g(\mathbf{x}, \mathbf{x}') \min \left(1, \frac{f(\mathbf{x})g(\mathbf{x}, \mathbf{x}')}{\hat{f}(\mathbf{x}')g(\mathbf{x}', \mathbf{x})}\right) &= \hat{f}(\mathbf{x})T(\mathbf{x}, \mathbf{x}').\end{aligned}$$

因此，满足了生成 $f$ 所描述分布的近似样本所需的详细平衡。

Metropolis-Hastings 算法是一类马尔可夫链蒙特卡洛（MCMC）算法的示例。通常，蒙特卡洛方法依赖于重复采样来执行计算，而在这些情况下解析解是不可能的或者成本很高。它们最初开发于洛斯阿拉莫国家实验室。由于这些工作是机密的，“蒙特卡洛”（指赌场）成为了该名称。当从条件分布采样比从联合分布容易时，使用 Gibbs 采样。Metropolis-Hastings 算法是提议分布是对称时的特例。

[img/c6c76bf52016db7e78a5e30d4766ef81_114_0.png]

图 3.7：由 Gibbs 采样生成的随机游走。为了近似样本间的独立性，可以使用稀释（thinning）。另一种技术是分块（blocking）；即使用的不是单个组件的条件概率，而是多个组件集合的条件概率，这些集合可以是重叠的。

## 习题

**练习 3.1.** 证明对于等式 3.5 给出的转移矩阵，如果 $\alpha, \beta$ 和 $\gamma$ 中任意两个均为零，则存在吸收态（如果有的话），但马尔可夫链本身不是吸收态的。

**练习 3.2.** 给定如下状态图，其中 $\alpha, \beta \in [0, 1]$。如果 $\alpha = 0$ 或 $\beta = 0$ 或两者均为零，会发生什么？找到一个平稳分布。

![](img/c6c76bf52016db7e78a5e30d4766ef81_115_0.png)

**练习 3.3.** 下述描述了一个系统，其状态为正整数。除了状态 1 只能转移到 2 或留在原位外，状态只能转移到下一个整数向上或向下或保持不变。向上的转移概率为 $\alpha$，向下的转移概率为 $\beta$。平稳概率为 $1-\beta$，但在状态 1 处，平稳概率为 $1-\alpha$。条件 $0 < \alpha < \beta$ 和 $\alpha + \beta < 1$ 成立。画出状态图并证明 $\mathbf{p} = (p_1, p_2, p_3, \dots)$

```
$p_k = \left( \frac{1-\beta}{\alpha+\beta} \right) \left( \frac{\alpha}{\alpha+\beta} \right)^{k-1}$
```

是一个概率分布且是平稳分布。

**练习 3.4.** 针对二元正态目标分布的 Gibbs 采样。

## 参考文献

Devroye, L. (1986), *Non-Uniform Random Variate Generation*, 1 edn, Springer.

Montgomery, D. (2020), *Introduction to Statistical Quality Control*, 8 edn, John Wiley & Sons.

Norris, J. (1998), *Markov Chains*, Cambridge University Press.

## 线性分类

区分对象之间的区别被称为*分类*（classification）。在我们出生之前，我们已经在子宫中学习区分不同的声音，此后我们继续学习并轻松地区分不同的物体、不同的情况和不同的概念。事实上，我们与其他人的差异或相似性是我们自我感产生的基础。人类在分类领域拥有惊人的能力。例如，尽管犬的品种繁多，但家猫在视觉上非常相似。我们识别出狗就是狗。孩子并不理解猫狗的区别在哪里。它是一只猫，那是一只狗。最多只是，这只狗喵喵，那只狗汪汪。通过这些例子，如何区分它们是显而易见的。什么是特征？什么是狗的特征？

更正式地说，特征有三类。*布尔*（Boolean）或*二值*（binary）特征只有两个值。它们与回答为“是”或“否”的问题有关。它是红色的吗？人高吗？我们有暴风雨吗？*离散*（Discrete）特征具有类别性，也称为*序数值*（ordinal values）。是什么颜色的？人是矮个、中等身材还是高个？蒲福风级上的风力是多少？最后是*连续*（continuous）特征，即*实值*（real-valued）特征。在这里，问题的答案例如：颜色的波长是多少？人的身高是多少？风速是多少？

生活中有很多分类的例子。垃圾邮件过滤是文本分类的应用。图像人脸检测和光学字符识别是机器视觉领域的示例。对于企业来说，市场细分至关重要，而我们都希望信用卡公司的欺诈检测算法是有效的。

分类并不新奇。最常用的例子之一可以追溯到1936年，Fisher (1936) 测量了三种不同品种鸢尾花的花瓣长度和宽度以及花片的长度和宽度，分别是 iris setosa、iris versicolor 和 iris virginica，每种植物有50个样本。因此，存在连续特征。

![](img/c6c76bf52016db7e78a5e30d4766ef81_117_0.png)

图 4.1：花片长度对比花片宽度的散点图。

在下文中，我们首先对两个物种进行分类，即标记为 $C_0$ 和 $C_1$ 的类。这也被称为二分类分类。设 $N_0$ 为类 $C_0$ 中的样本数，$N_1$ 为类 $C_1$ 中的样本数。因此，样本总数为 $N = N_1 + N_2$（注：原文此处为 $N_2$，应为 $N_0$）。查看如图 4.1 所示的数据的可视化是有帮助的，其中我们选择了两个特征进行相互展示：花片长度和花片宽度。这被称为散点图。

一旦我们开发出基于特征区分类别的规则，就可以用它对未来的特征进行分类。然而，需要注意，不一定属于某一类的特征可能会随着时间的推移而变化。因此，需要监控规则是否仍然适用。离群值（Outliers），也称为异常值，是指远离某类大多数样本的特征。只要发生的概率不为零，这些就会出现。比预期越多的离群值可能表明规则需要更新。如果采用在线学习技术，规则会随着新样本的到来进行迭代开发，这很直观，因为可以使用相同的技术。对于考虑所有样本进行更新的离线技术，规则可以通过重新运行算法（包括新样本）而变得更加复杂。

## 4.2 投影到子空间

每个样本都有两个特征，我们可以将它们写为向量，

$$\mathbf{v}_1 = \begin{pmatrix} v_{11} \\ v_{12} \end{pmatrix} \quad \quad \mathbf{v}_2 = \begin{pmatrix} v_{21} \\ v_{22} \end{pmatrix}.$$

*向量长度*（length of a vector）是坐标平方和的平方根。

$$|\mathbf{v}|| = \sqrt{v_{11}^2 + v_{22}^2}.$$

这也被称为欧几里得范数或 $L_2$ 范数。两个向量之间的定义*内积*（inner product），也称为*标量积*（scalar product）或*点积*（dot product）：

$$\mathbf{v}_1 \cdot \mathbf{v}_2 = (\mathbf{v}_1, \mathbf{v}_2) = v_{11}v_{21} + v_{12}v_{22}.$$

更一般的，这可以被视为第一个向量的*转置*（transpose）与第二个向量之间的*矩阵乘积*（matrix product）。

$$\mathbf{v}_1 \cdot \mathbf{v}_2 = \mathbf{v}_1^T \mathbf{v}_2 = \begin{pmatrix} v_{11} & v_{12} \end{pmatrix} \begin{pmatrix} v_{21} \\ v_{22} \end{pmatrix} = v_{11}v_{21} + v_{12}v_{22}.$$
