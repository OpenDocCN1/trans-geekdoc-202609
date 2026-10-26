
关于改进训练的文献可以从这个算子预处理的角度来看待。

## 7.1 损失函数的全局最小值是 PDE 解的良好近似

我们证明，只要能够找到物理信息损失函数 (2.69) 的全局最小值，前面各节的结果就可以用来证明物理信息学习的*先验误差估计*。

我们重新审视第 3 节中提出的误差分解 (3.7)。其中表明，如果能够对问题 2 作出肯定回答，那么对于任意 $\theta^*,\hat{\theta}\in\Theta$，

$$
\mathcal{E}(\theta^*) \le C\mathcal{E}_G(\theta^*)^\alpha
$$

$$
\le C\left(\mathcal{E}_G(\hat{\theta}) + 2\sup_{\theta\in\Theta}|\mathcal{E}_T(\theta,\mathcal{S}) - \mathcal{E}_G(\theta)| + \mathcal{E}_T(\theta^*,\mathcal{S}) - \mathcal{E}_T(\hat{\theta},\mathcal{S})\right)^\alpha. \tag{7.1}
$$

对于任意 $\varepsilon>0$，我们可以令 $\hat{\theta}$ 为与问题 1 中模型对应的参数，因此如果模型类具有足够的表达能力，我们会发现 $\mathcal{E}_G(\hat{\theta})<\varepsilon$。接下来，我们可以使用第 6 节的结果推断训练集 $\mathcal{S}$ 大小的一个下界（用 $\varepsilon$ 表示），使得也有 $\sup_{\theta\in\Theta}|\mathcal{E}_T(\theta,\mathcal{S}) - \mathcal{E}_G(\theta)|<\varepsilon$。最后，如果我们假设 $\theta^*=\theta^*(\mathcal{S})$ 是损失函数 $\theta\mapsto \mathcal{J}(\theta,\mathcal{S}) = \mathcal{E}_T(\theta,\mathcal{S})$ (2.69) 的全局最小值点，那么必然有 $\mathcal{E}_T(\theta^*,\mathcal{S}) \le \mathcal{E}_T(\hat{\theta},\mathcal{S})$，从而 $\mathcal{E}_T(\theta^*,\mathcal{S}) - \mathcal{E}_T(\hat{\theta},\mathcal{S}) \le 0$。因此，我们可从 (7.1) 推出

$$
\mathcal{E}^* \le C(3\varepsilon)^\alpha. \tag{7.2}
$$

另外，我们注意到第 6 节中的许多*后验误差界*具有如下形式

$$
\mathcal{E}(\theta^*) \le C(\mathcal{E}_T(\theta^*,\mathcal{S})+\varepsilon)^\alpha \tag{7.3}
$$

如果训练集足够大（取决于 $\varepsilon$）。如前所述，

$$
\mathcal{E}_T(\theta^*,\mathcal{S}) \le \mathcal{E}_T(\hat{\theta},\mathcal{S}) \le \mathcal{E}_G(\hat{\theta}) + \sup_{\theta\in\Theta}|\mathcal{E}_T(\theta,\mathcal{S}) - \mathcal{E}_G(\theta)| \le 2\varepsilon, \tag{7.4}
$$

因此，总体上我们再次得到 $\mathcal{E}^* \le C(3\varepsilon)^\alpha$，这与 (7.2) 一致。

我们首先对 Navier–Stokes 方程论证这一结论，然后展示一个类似的、克服了维数灾难的 Poisson 方程结果。

### 示例 7.1（Navier–Stokes 方程）

在第 4、5 和 6 节中，我们对问题 Q1–Q3 给出了肯定回答，因此在能够找到损失函数的精确全局最小值点的假设下，我们应该可以应用上述论证。

### 推论 7.2

设 $\varepsilon>0$，$T>0$，$d\in\mathbb{N}$，$k>6(3d+8)=:\gamma$，令 $(u,p)\in H^k(\mathbb{T}^d\times[0,T])$ 为 Navier–Stokes 方程 (2.8) 的经典解，设假设空间由这样的 PINN 组成：其权重上界至少为 $R\ge \varepsilon^{-1/(k-\gamma)}\ln(1/\varepsilon)$，宽度至少为 $W\ge \varepsilon^{-(d+1)/(k-\gamma)}$，深度至少为 $L\ge 3$，令 $(u_{\theta^*(\mathcal{S})},p_{\theta^*(\mathcal{S})})$ 为求解 (2.69) 的 PINN，并设训练集 $\mathcal{S}$ 满足 $N_t\ge \varepsilon^{-d(1+\gamma/(k-\gamma))}$、$N_{\mathrm{int}}\ge \varepsilon^{-2(d+1)(1+\gamma/(k-\gamma))}$ 和 $N_s\ge \varepsilon^{-2d(1+\gamma/(k-\gamma))}$。则有

$$
\|u-u_{\theta^*(\mathcal{S})}\|_{L^2(D\times[0,T])} = O(\varepsilon). \tag{7.5}
$$

*证明.* 这些结果由近似误差（定理 4.9）、稳定性（定理 5.7）和泛化误差（定理 6.5）的结果组合得出。

### 示例 7.3（Poisson 方程）

我们重新审视带变分残差的 Poisson 方程，此前已在示例 4.30（问题 1）和示例 5.11（问题 2）中考虑过。回顾一下，如果 $f\in\mathcal{B}^0(\Omega)$（见定义 4.28）满足 $\int_\Omega f(x)\,dx=0$，那么具有零 Neumann 边界条件的 Poisson 方程 $-\Delta u=f$ 的相应唯一解 $u$ 属于 $\mathcal{B}^2(\Omega)$。

现在，假设训练集 $\mathcal{S}$ 由 $\Omega$ 中 $N$ 个独立同分布（i.i.d.）随机生成的点组成，并且我们在宽度为 $m$ 的浅层 softplus 神经网络的一个子集上进行优化，该子集对应于参数空间 $\Theta^*\subset\Theta$；更精确的定义可参见 Lu 等人 (2021c, 式 (2.13))。和通常一样，我们将 $u_{\theta^*(\mathcal{S})}$ 定义为离散能量残差 $\mathcal{J}(\theta,\mathcal{S})$ 的最小值点。在此设定下，可以证明如下的*先验*泛化结果（Lu 等人 2021c, 注记 2.1）。

### 定理 7.4

假设上述设定成立。如果我们令 $m=N^{1/3}$，那么存在一个常数 $C>0$（与 $m$ 和 $N$ 无关），使得

$$
\mathbb{E}\left[\|u-u_{\theta^*(\mathcal{S})}\|_{H^1(\Omega)}^2\right] \le C\frac{(\log N)^2}{N^{1/3}}. \tag{7.6}
$$

在上述定理中，我们可以看到收敛速率与 $d$ 无关，因此缓解了维数灾难。常数 $C$ 可能依赖于 $u$ 的 Barron 范数，因此它对 $d$ 的依赖性可能并不完全清楚。

### 示例 7.5（标量守恒律）

利用定理 5.10 以及上述对泛化差距的界，我们可以证明弱 PINN 的总 $L^1$ 误差的如下严格上界（De Ryck 等人 2024c, 推论 3.10），我们将其记为

$$
\mathcal{E}(\theta) = \int_D |u_\theta(x,T)-u(x,T)|\,dx. \tag{7.7}
$$

因此，如果与 $u_\theta$ 和 $\mathcal{L}u_\theta$ 关联的正切核在优化路径上（近似）保持恒定，那么误差项 $\epsilon_k$ 将很小。

对于神经网络而言，这意味着神经正切核 (NTK) $\Theta[u_\theta]$ 和 $\Theta[\mathcal{L}u_\theta]$ 在优化路径上保持近似恒定。来自 De Ryck 等人 (2023)、基于 Wang 等人 (2022b) 的以下非正式引理证实，对于足够宽的神经网络确实如此。

### 引理 7.8

对于一个具有一个宽度为 $m$ 的隐藏层和线性微分算子 $\mathcal{L}$ 的神经网络 $u_\theta$，对所有 $k$，我们有 $\lim_{m\to\infty}\Theta[u_{\theta_k}] = \lim_{m\to\infty}\Theta[u_{\theta_0}]$ 和 $\lim_{m\to\infty}\Theta[\mathcal{L}u_{\theta_k}] = \lim_{m\to\infty}\Theta[\mathcal{L}u_{\theta_0}]$。因此，对于较宽的神经网络，误差项 $\epsilon_k$ (7.14) 很小，$\lim_{m\to\infty}\max_k\|\epsilon_k\|_2=0$。

现在，鉴于 (7.16) 与 (7.11) 相比结构简单得多，我们可以显式地研究相应的梯度下降动态，并得到以下收敛定理（De Ryck 等人 2023）。

### 定理 7.9

设 (7.16) 中的 $\mathbb{A}$ 可逆，其条件数为 $\kappa(\mathbb{A})$ (7.18)，并设 $0<c<1$。令 $\eta=c/\lambda_{\max}(\mathbb{A})$，$\vartheta=\theta_0+\mathbb{A}^{-1}\mathbb{C}$。则对任意 $k\in\mathbb{N}$ 有

$$
\|\widetilde{\theta}_k-\vartheta\|_2 \le \left(1-\frac{c}{\kappa(\mathbb{A})}\right)^k \|\theta_0-\vartheta\|_2. \tag{7.20}
$$

定量收敛速率 (7.20) 的一个直接后果如下：为了获得大小为 $\varepsilon$ 的误差，即 $\|\widetilde{\theta}_k-\vartheta\|_2\le\varepsilon$，我们可以直接计算出梯度下降（GD）步数 $N(\varepsilon)$ 为

$$
N(\varepsilon)=\frac{\ln(\varepsilon/\|\theta_0-\vartheta\|_2)}{\ln(1-c/\kappa(\mathbb{A}))} = O\left(\kappa(\mathbb{A})\ln\frac{1}{\varepsilon}\right). \tag{7.21}
$$

因此，对于固定的 $c$ 值，较大的条件数 $\kappa(\mathbb{A})$ 会因需要多得多的步数而严重阻碍简化梯度下降 (7.16) 的收敛。

## 7.3 训练与算子预处理

到目前为止，我们已经证明，在适当的假设下，物理信息机器学习的梯度下降算法的收敛速率归结为矩阵 $\mathbb{A}$ (7.13) 的条件数。然而，乍一看，该矩阵并不十分直观，我们希望将其与底层 PDE (2.1) 中的微分算子 $\mathcal{L}$ 联系起来。为此，我们首先引入所谓的 Hermitian 平方 $\mathcal{A}$，其定义为

$$
\mathcal{A}=\mathcal{L}^*\mathcal{L}, \tag{7.22}
$$

在算子意义下，其中 $\mathcal{L}^*$ 是微分算子 $\mathcal{L}$ 的伴随算子。注意，这个定义隐含地假设伴随算子 $\mathcal{L}^*$ 存在，并且 Hermitian 平方算子 $\mathcal{A}$ 定义在适当的函数空间上。作为示例，考虑微分算子为拉普拉斯算子，即 $\mathcal{L}u=-\Delta u$，

