
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_170_0.png)

图5.16：界优化算法示意图。改编自[Bis06]的图9.14。由emLogLikelihoodMax.m生成。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_170_1.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_170_2.png)

(a) 过冲。

(b) 寻求错误的根。

图5.17：MM算法的二次下界（实线）与牛顿法的二次近似（虚线）叠加在经验密度估计（点线）上。两种算法的起点均为圆圈。方块表示一次MM更新的结果。菱形表示一次牛顿更新的结果。(a) 牛顿法过冲了全局最大值。(b) 牛顿法导致目标函数下降。摘自[FT05]的图4。经Carlo Tomasi善意许可使用。

如果Q是一个二次下界，则整个方法与牛顿法类似，牛顿法反复拟合然后优化一个二次近似，如图5.8(a)所示。区别在于，优化Q能够保证目标函数得到改进，即使该目标函数不是凸的；而牛顿法可能会过冲或导致目标函数下降，如图5.17所示，因为它是一个二次近似而非一个界。

## 5.7.2 EM算法

在本节中，我们讨论期望最大化（EM）算法 [DLR77; MK97]。该算法旨在为具有缺失数据和/或隐藏变量的概率模型计算MLE或MAP参数估计。令 y_n 为第 n 个样本的可见数据，z_n 为隐藏数据。

EM背后的基本思想是在**E步**（期望步）中估计隐藏变量（或缺失值），然后在**M步**（最大化步）中使用完全观测数据计算MLE，如此交替进行。当然，我们需要迭代这一过程，因为期望值依赖于参数，而参数又依赖于期望值。

在5.7.2.1节中，我们证明EM是一种MM算法，这意味着该迭代过程将收敛到对数似然的局部最大值。收敛速度取决于缺失数据的多少，这会影响界的紧度 [XJ96; MD97; SRG03; KKS20]。

EM在机器学习中有许多应用。在本书中，我们考虑几个例子：

- 在5.7.3节中，我们展示如何使用EM拟合混合模型，如高斯混合模型。
- 在5.7.4节中，我们展示存在缺失数据时如何使用EM拟合多元高斯分布。
- 在11.4.1.1节中，我们展示如何使用EM拟合稳健线性回归模型。

### 5.7.2.1 下界

EM的目标是最大化观测数据的对数似然：

$$\ell(\boldsymbol{\theta}) = \sum_{n=1}^{N} \log p(\mathbf{y}_n|\boldsymbol{\theta}) = \sum_{n=1}^{N} \log \left[ \sum_{\mathbf{z}_n} p(\mathbf{y}_n, \mathbf{z}_n|\boldsymbol{\theta}) \right] \tag{5.145}$$

其中 $\mathbf{y}_n$ 是可见变量，$\mathbf{z}_n$ 是隐藏变量。不幸的是，这很难优化，因为对数不能移到求和号内部。

EM通过如下方式绕开这个问题。首先，考虑一组定义在每个隐藏变量 $\mathbf{z}_n$ 上的任意分布 $q_n(\mathbf{z}_n)$。观测数据的对数似然可以写成如下形式：

$$\ell(\boldsymbol{\theta}) = \sum_{n=1}^{N} \log \left[ \sum_{\mathbf{z}_n} q_n(\mathbf{z}_n) \frac{p(\mathbf{y}_n, \mathbf{z}_n|\boldsymbol{\theta})}{q_n(\mathbf{z}_n)} \right] \tag{5.146}$$

利用Jensen不等式（式(B.60)），我们可以将对数（它是一个凹函数）移入期望内部，从而得到对数似然的如下下界：

$$\begin{aligned}
\ell(\boldsymbol{\theta}) &\ge \sum_n \sum_{\mathbf{z}_n} q_n(\mathbf{z}_n) \log \frac{p(\mathbf{y}_n, \mathbf{z}_n|\boldsymbol{\theta})}{q_n(\mathbf{z}_n)} \tag{5.147}\\
&= \sum_n [\mathbb{E}_{q_n}[\log p(\mathbf{y}_n, \mathbf{z}_n|\boldsymbol{\theta})]] + \mathbb{H}(q_n) \tag{5.148}\\
&\triangleq Q(\boldsymbol{\theta}, \{q_n\}) \tag{5.149}
\end{aligned}$$

其中 $\mathbb{H}(q)$ 是概率分布 $q$ 的熵：$\mathbb{H}(q) \triangleq -\sum_z q(z) \log q(z)$。式(5.149)中的表达式有时称为**证据下界**或**ELBO**，因为它是**证据** $\log p(\mathbf{x}_{1:N}|\boldsymbol{\theta})$ 的下界。（证据是边际对数似然的另一个术语。）

EM算法在关于分布 $q_n$ 和参数 $\boldsymbol{\theta}$ 最大化下界 $Q$ 之间交替进行，下面我们讨论这一点。

### 5.7.2.2 E步

我们看到，下界是N项之和，每一项具有如下形式：

$$Q(\boldsymbol{\theta}, q_n) = \sum_{\mathbf{z}_n} q_n(\mathbf{z}_n) \log \frac{p(\mathbf{y}_n, \mathbf{z}_n | \boldsymbol{\theta})}{q_n(\mathbf{z}_n)}\tag{5.150}$$

$$= \sum_{\mathbf{z}_n} q_n(\mathbf{z}_n) \log \frac{p(\mathbf{z}_n | \mathbf{y}_n, \boldsymbol{\theta}) p(\mathbf{y}_n | \boldsymbol{\theta})}{q_n(\mathbf{z}_n)}\tag{5.151}$$

$$= \sum_{\mathbf{z}_n} q_n(\mathbf{z}_n) \log \frac{p(\mathbf{z}_n | \mathbf{y}_n, \boldsymbol{\theta})}{q_n(\mathbf{z}_n)} + \sum_{\mathbf{z}_n} q_n(\mathbf{z}_n) \log p(\mathbf{y}_n | \boldsymbol{\theta})\tag{5.152}$$

$$= -\mathbb{KL}\big(q_n(\mathbf{z}_n) \| p(\mathbf{z}_n | \mathbf{y}_n, \boldsymbol{\theta})\big) + \log p(\mathbf{y}_n | \boldsymbol{\theta})\tag{5.153}$$

其中 $\mathbb{KL}(q \| p) \triangleq \sum_z q(z) \log \frac{q(z)}{p(z)}$ 是概率分布 $q$ 和 $p$ 之间的Kullback-Leibler散度（简称KL散度）。我们将在6.2节更详细地讨论它，但这里需要的关键性质是 $\mathbb{KL}(q \| p) \ge 0$，且 $\mathbb{KL}(q \| p) = 0$ 当且仅当 $q = p$。因此，我们可以通过将每个 $q_n$ 设为 $q_n^* = p(\mathbf{z}_n | \mathbf{y}_n, \boldsymbol{\theta})$ 来关于 $\{q_n\}$ 最大化下界 $Q(\boldsymbol{\theta}, \{q_n\})$。这称为E步。这使得下界是紧的，即 $Q(\boldsymbol{\theta}, \{q_n^*\}) = \sum_n \log p(\mathbf{y}_n | \boldsymbol{\theta}) = \ell(\boldsymbol{\theta})$。

### 5.7.2.3 M步

在M步中，我们需要关于 $\boldsymbol{\theta}$ 最大化 $Q(\boldsymbol{\theta}, \{q_n^t\})$，其中 $q_n^t$ 是在第 $t$ 次迭代的E步中计算得到的分布。由于熵项 $\mathbb{H}(q_n)$ 关于 $\boldsymbol{\theta}$ 是常数，因此我们可以在M步中忽略它们。于是剩下

$$\ell^t(\boldsymbol{\theta}) = \sum_n \mathbb{E}_{q_n^t(\mathbf{z}_n)}[\log p(\mathbf{y}_n, \mathbf{z}_n | \boldsymbol{\theta})]\tag{5.154}$$

这称为期望完全数据对数似然。如果联合概率属于指数族（12.2节），我们可以将其重写为

$$\ell^t(\boldsymbol{\theta}) = \sum_n \mathbb{E}[\mathbf{t}(\mathbf{y}_n, \mathbf{z}_n)^\top \boldsymbol{\theta} - A(\boldsymbol{\theta})] = \sum_n (\mathbb{E}[\mathbf{t}(\mathbf{y}_n, \mathbf{z}_n)]^\top \boldsymbol{\theta} - A(\boldsymbol{\theta}))\tag{5.155}$$

其中 $\mathbb{E}[\mathbf{t}(\mathbf{y}_n, \mathbf{z}_n)]$ 称为期望充分统计量。

在M步中，我们最大化期望完全数据对数似然，得到

$$\boldsymbol{\theta}^{t+1} = \arg \max_{\boldsymbol{\theta}} \sum_n \mathbb{E}_{q_n^t}[\log p(\mathbf{y}_n, \mathbf{z}_n | \boldsymbol{\theta})]\tag{5.156}$$

对于指数族情形，可以通过匹配期望充分统计量的矩来闭式求解该最大化问题（12.2.4节）。

从上文可以看出，E步实际上不需要返回完整的后验分布集合 $\{q(\mathbf{z}_n) : n = 1 : N\}$，而只需返回期望充分统计量之和 $\sum_n \mathbb{E}_{q(\mathbf{z}_n)}[\mathbf{t}(\mathbf{y}_n, \mathbf{z}_n)]$。这一点在下面的例子中将变得更加清晰。

## 5.7.3 示例：GMM的EM算法

在本节中，我们展示如何使用EM算法计算高斯混合模型（GMM）参数的MLE和MAP估计。

### 5.7.3.1 E步

E步简单地使用当前参数估计 $\boldsymbol{\theta}^{(t)}$ 计算簇 $k$ 对生成数据点 $n$ 的**责任**：

$$r_{nk}^{(t)} = p(z_n = k | \boldsymbol{\theta}^{(t)}) = \frac{\pi_k^{(t)} p(\mathbf{y}_n | \boldsymbol{\theta}_k^{(t)})}{\sum_{k'} \pi_{k'}^{(t)} p(\mathbf{y}_n | \boldsymbol{\theta}_{k'}^{(t)})} \tag{5.157}$$

### 5.7.3.2 M步

M步最大化期望完全数据对数似然，其表达式为

$$\ell^t(\boldsymbol{\theta}) = \mathbb{E}\left[\sum_n \log p(z_n | \boldsymbol{\pi}) + \log p(\mathbf{y}_n | z_n, \boldsymbol{\theta})\right] \tag{5.158}$$

$$= \mathbb{E}\left[\sum_n \log\left(\prod_k \pi_k^{z_{nk}}\right) + \log\left(\prod_k \mathcal{N}(\mathbf{y}_n | \boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)^{z_{nk}}\right)\right] \tag{5.159}$$

$$= \sum_n \sum_k \mathbb{E}[z_{nk}] \log \pi_k + \sum_n \sum_k \mathbb{E}[z_{nk}] \log \mathcal{N}(\mathbf{y}_n | \boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k) \tag{5.160}$$

$$= \sum_n \sum_k r_{nk}^{(t)} \log(\pi_k) - \frac{1}{2} \sum_n \sum_k r_{nk}^{(t)} \left[\log |\boldsymbol{\Sigma}_k| + (\mathbf{y}_n - \boldsymbol{\mu}_k)^\top \boldsymbol{\Sigma}_k^{-1} (\mathbf{y}_n - \boldsymbol{\mu}_k)\right] + \text{const} \tag{5.161}$$

其中 $z_{nk} = \mathbb{I}(z_n = k)$ 是分类值 $z_n$ 的one-hot编码。该目标只是计算MVN的MLE这一标准问题（见4.2.6节）的加权版本。可以证明，新的参数估计为

$$\boldsymbol{\mu}_k^{(t+1)} = \frac{\sum_n r_{nk}^{(t)} \mathbf{y}_n}{r_k^{(t)}} \tag{5.162}$$

$$\boldsymbol{\Sigma}_k^{(t+1)} = \frac{\sum_n r_{nk}^{(t)} (\mathbf{y}_n - \boldsymbol{\mu}_k^{(t+1)})(\mathbf{y}_n - \boldsymbol{\mu}_k^{(t+1)})^\top}{r_k^{(t)}}$$

$$= \frac{\sum_n r_{nk}^{(t)} \mathbf{y}_n \mathbf{y}_n^\top}{r_k^{(t)}} - \boldsymbol{\mu}_k^{(t+1)} (\boldsymbol{\mu}_k^{(t+1)})^\top \tag{5.163}$$

其中 $r_k^{(t)} \triangleq \sum_n r_{nk}^{(t)}$ 是分配给簇 $k$ 的点的加权数量。簇 $k$ 的均值就是分配给簇 $k$ 的所有点的加权平均值，协方差与加权经验散布矩阵成正比。

