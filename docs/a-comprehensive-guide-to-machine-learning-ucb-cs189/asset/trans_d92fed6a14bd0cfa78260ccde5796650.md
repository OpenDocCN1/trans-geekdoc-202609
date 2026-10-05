

# 第 3 章. 低秩近似

![](img/99defe26aebed215976e83d281581f33_49_0.png)

# 构建 PCA 公式

令 $X \in \mathbb{R}^{n \times d}$ 为我们的矩阵，其中每一行是一个 $d$ 维数据点。我们假设数据点的均值为零；否则，我们减去均值使其成为零均值：

```
$X - \frac{1}{n}\mathbf{1}_n\mathbf{1}_n^T X, \quad \mathbf{1}_n = \begin{bmatrix} 1 \\ \vdots \\ 1 \end{bmatrix}$
```

此处的动机是我们要找到数据中方差最大的方向，而方差是相对于数据的均值定义的。如果我们不对数据进行零中心化处理，找到的方向将受到数据相对于原点位置的影响很大，而不是它们与其他数据之间的相对位置（后者更有用）。例如，如果不进行中心化，通过某个固定向量平移所有数据可能会完全改变主成分。

回想任何随机变量 $Z$，

```
$Var(Z) = \mathbb{E}[(Z - \mathbb{E}[Z])^2]$
```

如果 $\mathbb{E}[Z] = 0$，则 $Var(Z) = \mathbb{E}[Z]^2$。

因此，一旦 $X$ 是零均值的，投影的方差由给出

```
$\epsilon_{PCA,var}(u) = \sum_{i=1}^n (x_i^T u)^2 = \|Xu\|^2$
```

其中 $u$ 被限制为单位范数。为了最大化方差，目标变为：

```
$\max_{\|u\|=1} \epsilon_{PCA,var}(u) = \max_{\|u\|=1} \|Xu\|^2 = \max_{u\neq 0} \frac{\|Xu\|^2}{\|u\|^2} = \max_{u\neq 0} \frac{u^T X^T Xu}{u^T u}$
```

这个比值被称为*瑞利商*（Rayleigh quotient）。我们将看到瑞利商与特征值有密切的相关，因此每当你使用它时，其特征向量意义将显而易见。

# 瑞利商

假设 $M \in \mathbb{R}^{d \times d}$ 是一个实对称矩阵（$M = M^T$）。$M$ 的瑞利商定义为

```
$R(u; M) = \frac{u^T Mu}{u^T u}$
```

$M$ 的特征值为 $\lambda_1 \geq \lambda_2 \geq \dots \geq \lambda_d$，对应的特征向量为 $v_1, \dots, v_d$。即对于 $j = 1, \dots, d$，$M_j = \lambda_j v_j$。我们将 $v_j$ 堆叠为矩阵 $V$ 的列：

```
$V = [v_1 \quad \dots \quad v_d]$
```

# 3.2. 主成分分析

那么特征向量方程可以同时写为

$MV = V\Lambda$

其中

$$\Lambda = diag(\lambda_1, \dots, \lambda_d) = V^T$$

那么 $V$ 是一个正交矩阵，它是可逆的且 $V^{-1} = V^T$，所以

$V^T MV = \Lambda$

令 $u$ 为一个单位长度向量。由于 $\{v_j\}$ 构成了一个基，我们可以写成

$$u = \sum_{j=1}^d \alpha_j v_j = V\alpha$$

那么 $V$ 是正交矩阵。$|u| = 1$ 也是。现在

$$R(u;M) = \frac{u^T Mu}{u^T u} = \alpha^T MV\alpha = \alpha^T \Lambda\alpha = \sum_{j=1}^d \lambda_j \alpha_j^2$$

由于我们有约束 $\alpha_1^2 + \dots + \alpha_d^2=1$，最大的表达式是特征值的加权平均，因此受限于这些值中的最小和最大：

$$\lambda_d \le R(u;M) \le \lambda_1$$

下界通过令 $\alpha_1=\pm1, \alpha_{j\neq 1}=0$ 获得。最大值可以通过以下方式恢复：

$$\sum_{j=1}^d \alpha_j v_j = \pm v_1$$

即，它是对应于最大特征值的特征向量：因此

$$\lambda_d = R(v_d;M) \le R(v_1;M) \le \lambda_1$$

最后注意，瑞利商是尺度不变的，即对于任何 $\gamma \neq 0$，$R(\gamma u;M) = R(u;M)$，该不等式适用于向量的所有缩放，而不只是单位长度向量。

# 计算第一个主成分

利用我们瑞利商的知识，PCA 问题的求解显而易见：

$$\max_{\|u\|=1} PCA.var(u) = \max_{u\neq 0} \frac{u^T X u}{u^T u} = \lambda_1(X^T X)$$

其中最大化器 $u^*$ 是对应于该特征值的单位特征向量。写入 $X=U\Sigma V^T$，

$$X^T X = V\Sigma^T U^T U\Sigma V^T$$

右侧表达式是 $X^T X$ 的特征分解，所以

$$\lambda_1(X^T X) = \sigma_1^2$$

对应的特征向量为 $v_1$，即第一个主成分。

# 寻找多个成分

我们已经看到如何推导出使方差最大的第一个主成分。但通常我们需要多个方向，因为一个方向很难很好捕捉数据。这里的主意是减去已计算主成分的贡献，然后对剩余部分应用相同的规则。u_{(1)},\dots,u_{(k-1)}$ 表示已计算的主成分，这种减法通过完成

$$\hat{X} = X - \sum_{j=1}^{k-1} u_j u_j^T = X(I - \sum_{j=1}^{k-1} u_j u_j^T)$$

该表达式应该对数据的每一行应用相同的变换：

$$\hat{x}_i = (I - \sum_{j=1}^{k-1} u_j u_j^T)x_i = x_i - \sum_{j=1}^{k-1} u_j u_j^T x_i$$

向量 $\hat{x}_i$ 应识别为 $x_i$ 在由 $u_{(j)}$ 跨越的子空间上的正交投影。这里 $\hat{x}_i$ 是从 $x_i$ 开始移除所有属于由 $u_{(j)}$ 跨越的空间的部分。我们想要找到满足与所有已计算方向正交的最大方差方向。我们有一个如下形式的问题：

$$u_k = \arg\max_{\forall j < k, u^T u_{(j)}=0} \frac{u^T X^T u}{u^T u}$$

但我们不想计算 $\hat{X}$！考虑如果 $u$ 与 $u_{(1)},\dots,u_{(k-1)}$ 正交（约束），那么

$$\hat{X}u = (X - \sum_{j=1}^{k-1} u_j u_j^T)u = Xu - \sum_{j=1}^{k-1} u_j u_j^T u = Xu$$

因此我们可以将上述优化问题写为

$$u_k = \arg\max_{\forall j < k, u^T u_{(j)}=0} \frac{u^T X^T u}{u^T u}$$

消除了计算 $\hat{X}$ 的需要。意料之中，该问题的解由 $v_k$ 给出，它是 $X^T X$ 的第 $k$ 大特征值。与其迭代计算每个 $u_j$，我们可以将寻找 $k$ 个主成分的问题看是对所有 $k$ 个方向的联合优化。这等同于最大化投影到 $k$ 维子空间上的方差

$$U = \arg\max_{U^TU=I} \text{tr}(U^T X^T U) (U^T X^T U)$$

- 为了看到这一点，对两边取投影并利用 $I - \sum_j u_j u_j^T$ 的对称性。
- 这与 Gram-Schmidt 方法的思想完全相同。

# 3.2. 主成分分析

对于具有正交列的矩阵 $U$，我们可以定义

```
$R(U; M) = R([u_1, \dots, u_k]; M) = \sum_{j=1}^k R(u_j; M)$
```

与之前一样，该表达式的边界由最小和最大特征值给出，我们知道它们是：

```
$\lambda_1 + \lambda_2 + \dots + \lambda_k = R([v_1, \dots, v_k]; M)$
```

因此，投影到前 $k$ 个领先特征向量跨越的子空间使投影数据的方差最大。我们可以通过计算 SVD，$X = U\Sigma V^T$，然后取矩阵 $V$ 的前 $k$ 列来找到 $k$ 个主成分。

# 投影到 PCA 坐标系

一旦有了主成分，就可以将其作为新的坐标系。为了这样做，我们必须将数据投影到这个坐标系，可以通过上述相同的方法（取内积）来实现。每个数据点 $x_i \in \mathbb{R}^d$ 变成一个新的向量 $\tilde{x}_i \in \mathbb{R}^k$，其中 $k$ 是主成分的数量。投影的成分写为

```
$\tilde{x}_ij = x_i^T u_j$
```

我们可以使用矩阵乘法高效地一次性计算所有向量：

```
$\tilde{X} = U^T X$
```

其中 $U \in \mathbb{R}^{d\times k}$ 是一个列为主成分的矩阵。

下面我们绘制了在 $d=k=2$ 情况下此类投影的结果

![](img/99defe26aebed215976e83d281581f33_52_0.png)

图 3.1：左：数据点；右：数据点的 PCA 投影

观察到数据在投影空间中是不相关的。同样请注意，这个例子没有显示出 PCA 的全部威力，因为我们完全没有降低数据的维度——该图仅用于展示 PCA 坐标变换。

