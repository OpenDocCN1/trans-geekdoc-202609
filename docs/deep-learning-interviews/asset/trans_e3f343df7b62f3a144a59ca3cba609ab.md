

## SOL-78 CH.SOL- 4.12.

熵的一组重要性质源于其凹性，而凹性又源于对数函数的凹性。假设我们无法确定“正面”的实际概率是 $p_{1}$ 还是 $p_{2}$。我们可以决定将概率 $q$ 分配给第一种可能性，将概率 $1-q$ 分配给第二种可能性。此时，“正面”的实际概率是混合概率 $qp_{1}+(1-q)p_{2}$。相应的熵满足不等式：

$$S(qp_{1}+(1-q)p_{2}) \geq q S(p_{1})+(1-q) S(p_{2}) \tag{4.16}$$

当处于极端情况时等号成立，即 $p_{1}=p_{2}$，或 $q=0$，或 $q=1$。

## SOL-79 CH.SOL- 4.13.

给定 $(X, Y)$，我们可以确定 $X$ 和 $Z=Y-X$。反过来，给定 $(X, Z)$，我们可以确定 $X$ 和 $Y=X+Z$。因此，由于存在这种双射关系，$H(X, Y)=H(X, Z)$。

## SOL-80 CH.SOL- 4.14.

解决方案和数值计算均使用 $\log _{2}$。

- 我们可以以 $p(x_{h})=98\%$ 的准确率预测每次抛硬币的“正面”。
- 根据图 (4.9)，如果硬币抛掷的结果是“正面”，获得的香农信息量为 $\log _{2}(1/0.98)$ [比特]。

```python
import math
import numpy
print(math.log2(1.0 / 0.98))  # Binary log (base 2)
# 0.02914634565951651
print(numpy.log2(1.0 / 0.02))  # Binary log (base 2)
# 5.643856189774724
```

图 4.9：偏置硬币抛掷的香农信息增益。

- 同样地，如果硬币抛掷的结果是“反面”，获得的香农信息量为 $\log_{2}(1/0.02)$ [比特]。
- 结果所关联的信息量**越多**，该结果就越**令人惊讶**。
- **平均惊讶度**的公式为：

$$H(x) = p(x_h) \log \frac{1}{p(x_h)} + p(x_t) \log \frac{1}{p(x_t)} . \tag{4.17}$$

- **平均惊讶度**以比特为单位的数值由 $(4.10)$ 给出：

$$
\begin{aligned}
H(x) &= [0.98 \times 0.0291] + [0.02 \times 5.643] \tag{4.18} \\
&= 0.1414\ [\text{bits}].
\end{aligned}
$$

```python
import autograd.numpy as np

def binaryEntropy(p):
    return -p * np.log2(p) - (1 - p) * np.log2(1 - p)

print("binaryEntropy(p) is: {} bits".format(binaryEntropy(0.98)))
# binaryEntropy(p) is: 0.1414 bits
```

![](img/574135cb1d7125b50cf484d943cdd676_129_0.png)

## 4.3.3 库拉-莱布勒散度

### SOL-81 CH.SOL- 4.15.

对于离散概率分布 $P$ 和 $Q$，**从** $P$ **到** $Q$ 的库拉-莱布勒散度（KLD）定义为：

$$
\begin{align}
D(P \| Q) &= \sum_x P(x) \log \frac{P(x)}{Q(x)} \tag{4.19} \\
&= \mathbb{E}_P \left[ \log \frac{1}{Q(x)} - \log \frac{1}{P(x)} \right] \\
&= \underbrace{H_P(Q)}_{\text{Cross Entropy}} - \underbrace{H(P)}_{\text{Entropy}}.
\end{align}
$$

### SOL-82 CH.SOL- 4.16.

一种解释如下：KL散度表明，在传输服从 $P(x)$ 分布的值 $x \in X$ 时，若错误地按照分布 $Q(x)$ 进行编码，所需的**额外比特数**的平均值。这是合理的，因为你必须为不知道真实分布而支付额外的比特代价，从而使用了根据其他分布优化的编码方案。这也是KL散度也被称为相对熵的原因之一。从形式上看，交叉熵具有信息论解释，量化了使用错误编码所浪费的比特数：

$$H_P(Q) = \sum_x \underbrace{P(x)}_{\text{Sending } P} \overbrace{\log \frac{1}{Q(x)}}^{\text{code for } Q} . \tag{4.20}$$

### SOL-83 CH.SOL- 4.17.

- 1. 正确。KLD是一种非对称度量，即 $D(P \| Q) \neq D(Q \| P)$。
- 2. 错误。KLD不满足三角不等式。
- 3. 正确。KLD不是一种距离度量。
- 4. 正确。KLD被视为信息增益的度量。但需注意，KLD实际上衡量的是信息损失量。
- 5. 正确。KL散度的单位是信息单位（比特、纳特等）。
- 6. 正确。KLD是一个非负度量。
- 7. 正确。基于高度信息量的事件进行分割通常会导致模型泛化能力较低，准确性也会下降。

### SOL-84 CH.SOL- 4.18.

从形式上看，互信息试图衡量两个变量之间的相关性：

$$
\begin{aligned}
I(X;Y) &= \sum_{x,y} P(x,y) \log \frac{P(x,y)}{P(x)P(y)} \tag{4.21} \\
&= \mathbb{E} \left[ \log \frac{1}{P(x)} + \log \frac{1}{P(y)} - \log \frac{1}{P(x,y)} \right] \\
&= H(X) + H(Y) - H(X,Y).
\end{aligned}
$$

针对所讨论的问题，给定两个分布 $f_1$ 和 $f_2$ 及其联合分布 $f$，$f_1$ 和 $f_2$ 的互信息定义为 $I(f_1, f_2) = H(f, f_1, f_2)$。如果两个分布相互独立，即 $f=f_1 \cdot f_2$，则互信息为零。这一概念在图像分析中被广泛用作相似度度量。

### SOL-85 CH.SOL- 4.19.

$$KL_{p\|q} = \frac{1}{3}(-1 + 0 + 1 + 1) = \frac{1}{4} \tag{4.22}$$

## 4.3.4 分类与信息增益

### SOL-86 CH.SOL- 4.20.

最常用的三种方法是：

1. $$\textit{Entropy}(t)=-\sum_{i=0}^{c-1} p(i|t) \log _{2} p(i|t). \tag{4.23}$$

2. $$\text{Gini}(t)=1-\sum_{i=0}^{c-1}[p(i|t)]. \tag{4.24}$$

3. $$\textit{Classification error}(t)=1-\max _{i}\left[p(i|t)\right]. \tag{4.25}$$

### SOL-87 CH.SOL- 4.21.

在决策树中，我们选择用于分裂的属性是信息增益 **[最大]** 的那个。

### SOL-88 CH.SOL- 4.22.

待定

### SOL-89 CH.SOL- 4.23.

- 信息增益是由根据给定属性对数据集中的值进行划分所导致的熵的期望减少量。
- 决策树学习算法通过首先计算基于熵的信息增益作为分裂准则，来选择下一个用于划分当前选中节点（例如）的属性。
- 有3个正例对应收缩= +，2个负例对应收缩= -。使用以下公式：

$$H(Y) = - \sum_{i=1}^{k} P(Y=y_i) \log_{2} P(Y=y_i) \qquad (4.26)$$

以及概率：

$$P(\gamma = +) = \frac{3}{5} , \qquad (4.27)$$

$$P(\gamma = -) = \frac{2}{5} , \qquad (4.28)$$

分裂前的总熵为 $(4.11)$：

$$
\begin{gathered}
E_{\text {orig }} = -(3 / 5) \log (3 / 5)-(2 / 5) \log (2 / 5) \\
= H(\gamma) \approx 0.97095[\text { bits } / \text { symbol }]
\end{gathered} \qquad (4.29)
$$

```python
import autograd.numpy as np

def binaryEntropy(p):
    return p*np.log2(p) + (1-p)*np.log2(1-p)

print("binaryEntropy(p) is: {} bits".format(binaryEntropy(4/7)))
# binaryEntropy(p) is: 0.97095 bits
```

![](img/574135cb1d7125b50cf484d943cdd676_133_0.png)

- 如果我们在 $\theta_{1}$ 上分裂，(4.5) 相对收缩频率为：

|  | 总数 | $\theta_{1} = T$ | $\theta_{1} = F$ |
|---|:---:|:---:|:---:|
| \oplus | 3 | 0 | 3 |
| \ominus | 2 | 1 | 1 |

**表 4.5：** 在 $\theta_{1}$ 上的分裂。

要计算基于特征 $\theta_1$ 的信息增益（IG），我们必须首先计算基于 $\theta_1$ 分裂后 $\gamma$ 的熵，$H(\gamma \mid \theta_1)$：

$$
\begin{aligned}
H(\gamma | \theta_1) &= - \sum_{j=1}^{v} \left[ \sum_{i=1}^{k} P(\gamma = \gamma_i | \theta_1 = \theta_j) \log_2 P(\gamma = \gamma_i | \theta_1 = \theta_j) \right] P(\theta_1 = \theta_j).
\end{aligned}
$$

因此，使用相对收缩频率数据 (4.5)，在 $\theta_1$ 上分裂后的信息增益为：

$$
\begin{aligned}
E_{\theta_1=T} &= - \frac{3}{4} \log \frac{3}{4} - \frac{1}{4} \log \frac{1}{4} = 0.8112, \\
E_{\theta_1=F} &= - \frac{0}{1} \log \frac{0}{1} - \frac{1}{1} \log \frac{1}{1} = 0.0.
\end{aligned} \qquad (4.30)
$$

现在我们知道 $P(\theta_1 = T) = [4/5]$ 且 $P(\theta_1 = F) = [1/5]$，因此：

$$
\begin{aligned}
\Delta &= E_{orig} - (4/5) E_{\theta_1=T} - (1/5) E_{\theta_1=F} \\
&= 0.97095 - (4/5) * 0.8112 - (1/5) * (0.0) \\
&\approx 0.32198 \; [\text{bits/symbol}].
\end{aligned} \qquad (4.31)
$$

### SOL-90 CH.SOL- 4.24.

有4个正例对应扩张=+，3个负例对应扩张=-。

1. 分裂前的总熵为 $(4.12)$：

$$
\begin{aligned}
E_{orig} &= - (4/7) \log (4/7) - (3/7) \log (3/7) \\
&= 0.9852281 \; [\text{bits/symbol}].
\end{aligned} \qquad (4.32)
$$

```python
import autograd.numpy as np

def binaryEntropy(p):
    return -p * np.log2(p) - (1-p) * np.log2(1-p)
```

