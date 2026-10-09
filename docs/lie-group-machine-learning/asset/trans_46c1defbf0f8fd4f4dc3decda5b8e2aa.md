
## 9.2.1 $R^+$ 的高斯分布

对于由正实数乘法构成的李群 $R^+$，其局部坐标由对数给出，热方程的解是对数密度函数：

$p(x) = \frac{1}{\sqrt{2\pi}\sigma x}\exp\left(-\frac{(\log(x)-\log(\mu))^2}{2\sigma^2}\right).$ (9.6)

给定样本 $x_1, \dots, x_n \in R^+$ 服从独立同分布的对数分布，它们的均值和方差的极大似然估计为

$\hat{\mu} = \left(\prod_{i=1}^{n} x_i\right)^{\frac{1}{n}}$ , $\quad \hat{\sigma}^2 = \frac{1}{n}\sum_{i=1}^{n}\left(\log(x_i)-\log(\hat{\mu})\right)^2$

其中 $\hat{\mu}$ 是几何均值，即流形 $R$ 上测地线距离平方和最小的点，也就是 $\sum_{i=1}^{n}\log(\mu^{-1}x_i)^2$ 取最小值的点。

### 9.2.2 SO(2) 的高斯分布

SO(2) 的参数是旋转角 $\theta \in [0, 2\pi)$。由于 SO(2) 通过映射 $\theta \mapsto e^{i\theta}$ 同构于 $S^1$，SO(2) 上高斯分布的均值 $\mu$ 和方差 $\sigma$ 由下式给出：

$p(\theta) = \frac{1}{\sqrt{2\pi}\sigma}\sum_{k=-\infty}^{+\infty}\exp\left(-\frac{(\theta-\mu-2k\pi)^2}{2\sigma^2}\right)$. (9.7)

上述方程是 $[-\pi, \pi]$ 周期内热方程的解，也被称为“环形高斯分布”（wrapped Gaussian），如图 9.4 所示。

现在，我们推导均值和方差的极大似然估计。给定独立样本集 $\theta_i \in [0, 2\pi), i = 1, \dots, n$，其分布形式与 (9.7) 相同，我们假设 $\sigma = 1$。那么，均值的极大似然估计为：

$\hat{\mu} = \operatorname*{arg\,max}_{\mu \in [0, 2\pi)} \prod_{i=1}^{n}\frac{1}{\sqrt{2\pi}}\sum_{k=-\infty}^{+\infty}\exp\left(-\frac{(\theta_i-\mu-2k\pi)^2}{2}\right)$ (9.8)

注意这两个指数函数是偶函数，且其导数函数是奇函数；对于固定的 $k$，我们有

$\frac{\partial}{\partial\mu}\exp\left(-\frac{(\theta_i-\mu-2k\pi)^2}{2}\right) = -\frac{\partial}{\partial\mu}\exp\left(-\frac{(\theta_i-\mu+2k\pi)^2}{2}\right)$

因此，当 (9.8) 的形式简化为仅保留 $k = 0$ 时，最大化问题变为

$\hat{\mu} = \operatorname*{arg\,max}_{\mu \in [0, 2\pi)} \prod_{i=1}^{n}\frac{1}{\sqrt{2\pi}}\exp\left(-\frac{(\theta_i-\mu)^2}{2}\right)$. (9.9)

![](img/456a7a56403cbb2b5f1a261793529a51_303_0.png)

![](img/456a7a56403cbb2b5f1a261793529a51_303_1.png)

![](img/456a7a56403cbb2b5f1a261793529a51_303_2.png)

上述方程是 $\mathrm{SO}(2)$ 在高斯分布下均值的极大似然方程。因此，我们有 $\hat{\mu} = 1/n \sum_{i=1}^{n} \theta_i$。由于 $\theta_i$ 表示方式的多样性，例如 $\theta_i$ 可以属于区间 $[0, 2\pi)$ 或属于 $[-\pi, \pi)$，这使得关于 $\hat{\mu}$ 的公式存在歧义，因此我们需要在特定问题中将 $\theta_i$ 限制在某个区间内。

对于方差极大似然估计的推导，考虑以下对数似然函数：

$l(\sigma; \hat{\mu}, \theta_1, \ldots, \theta_n) = \sum_{i=1}^{n} \log \left(\frac{1}{\sqrt{2}\pi \sigma} + \log \left(\sum_{k=-\infty}^{+\infty} \exp \left(-\frac{(\theta_i - \hat{\mu} - 2k\pi)^2}{2\sigma^2}\right)\right)\right)$

对 $\sigma$ 求导得到：

$\frac{\partial \mathrm{l}}{\partial \sigma} = -\frac{n}{\sigma} + \frac{1}{\sigma^3} \sum_{i=1}^{n} \left( \theta_i - \tilde{\mu} \right)^2 + \frac{1}{\sigma^3} \sum_{i=1}^{n} \left( \frac{\sum_{k=-\infty}^{+\infty} \left(2 k \pi \right)^2 \exp \left(-\frac{\left(\theta_i - \tilde{\mu} - 2 k \pi \right)^2}{2 \sigma^2} \right)}{\sum_{k=-\infty}^{+\infty} \exp \left(-\frac{\left(\theta_i - \tilde{\mu} - 2 k \pi \right)^2}{2 \sigma^2} \right)} \right)$

上述方程右侧的第三项收敛，但无法产生闭合形式的解。根据 [52]，我们可以看出环形高斯密度函数，即当 $\sigma^2 \leq 2 \pi$ 时，这与图像处理问题的角度约束是一致的，此时它近似于 (9.7) 中 $k=0$ 的求和项。因此，我们仅保留 $k=0$ 项。然后我们有

$\frac{\partial \mathrm{l}}{\partial \sigma} = -\frac{n}{\sigma} + \frac{1}{\sigma^3} \sum_{i=1}^{n} \left( \theta_i - \tilde{\mu} \right)^2.$

令上述方程等于 0；解出 $\sigma$，我们可得到近似方差的极大似然估计：

$\hat{\sigma}^2 = \frac{1}{n} \sum_{i=1}^{n} \left( \theta_i - \tilde{\mu} \right)^2$ (9.10)

### 9.2.3 SO(3) 的高斯分布

类似于 SO(2)，我们在 S3 上使用对数映射来定义均值为 $\mu$ 的环形高斯分布。应注意，密度函数不一定是 SO(3) 上热方程的解。设 $\mu(x) = \Phi(\log(\mu^{-1}x)) \in R^3$，其中 $\Phi: \mathrm{SO}(3) \to R^3$，$\Phi(A_{ij}) = \nu$ 构成标准同构。设 $\bar{\mu}(x) = \mu(x)/\|\mu(x)\|$；根据 (9.13)，SO(3) 的环形高斯密度函数为

$p(x) = \frac{1}{\sqrt{(2 \pi)^3 |\Sigma|}} \sum_{k=-\infty}^{+\infty} \exp \left(-\frac{1}{2} \left( \mu(x) - 2 k \pi \bar{\mu}(x) \right)^\mathrm{T} \Sigma^{-1} \left( \mu(x) - 2 k \pi \bar{\mu}(x) \right) \right)$ (9.11)

协方差结构定义为李代数 SO(3) 上的二次型，表示为 $3 \times 3$ 矩阵 $\Sigma$。

给定独立样本集 $x_1, \ldots, x_n \in \mathrm{SO}(3)$，其分布形式与 (9.11) 相同，下面推导均值和方差的极大似然估计。对于均值，不失一般性，可以假设协方差为单位矩阵。联合密度由以下密度给出：

$p(\mu; x_1, \ldots, x_n) = \prod_{i=1}^{n} \frac{1}{\sqrt{(2 \pi)^3}} \sum_{k=-\infty}^{+\infty} \exp \left(-\frac{1}{2} \| \mu(x_i) - 2 k \pi \bar{\mu}(x_i) \|^2 \right)$ (9.12)

注意 SO(3) 的测地线同构于 SO(2)，且密度函数 (9.11) 将测地线约束为 SO(2) 上的环形高斯。现在可以使用上一节中的相同假设，将求和公式中对应项的导数函数消去。最大化 $p(\mu; x_1, \dots, x_n)$ 等价于在以下公式中寻找 $\hat{\mu}$：

$\hat{\mu} = \arg_{\mu\in\mathrm{SO}(3)} \max \prod_{i=1}^{n} \frac{1}{\sqrt{(2\pi)^3}} \exp\left( -\frac{1}{2}\|\mu(x_i)\|^2\right)$

对上式取对数，我们可以得到极大似然估计的均值：

$\hat{\mu} = \arg_{\mu\in\mathrm{SO}(3)} \max \sum_{i=1}^{n} \|\Phi (\log (\mu^{-1}x_i))\|^2$

其中 $\|\Phi (\log (\mu^{-1}x_i))\|$ 是 $\mu$ 到 $x$ 的黎曼距离。因此，均值的极大似然估计也是所有样本点中测地线距离平方最小的点，即 SO(3) 的内在均值（inner mean value）。

类似于 SO(2)，我们假设方差足够小，即 $\lambda \lesssim 2\pi$，其中 $\lambda$ 是 $\Sigma$ 的特征值。使用上一节中的相同假设，我们得到近似方差的极大似然估计：

$\widehat{\sum} = \frac{1}{n} \sum_{i=1}^{n} \Phi (\log (\hat{\mu}^{-1}x_i)) \Phi (\log (\hat{\mu}^{-1}x_i))^T$

## 9.3 李群内在均值的计算

图 9.5(a) 展示了流形 $S^1$ 上的内在均值 $\mu$，其中每个数据点到 $\mu$ 的距离是 $S^1$ 上的测地线距离（曲线长度），所得到的均值也在 $S^1$ 上。图 9.5(b) 展示了直接计算欧氏距离的均值。计算得到的 $\mu$ 被称为外在均值（extrinsic mean），它通常不在流形上，例如 $\mu$ 在 $R^2$ 中而不在 $S^1$ 上的情况。

在 $R^d$ 空间中，$n$ 个数据点集 $\{x_i\}_{i=1}^{n} \in R^d$ 的均值可以通过 (9.4) 计算，其中样本 $x_i$ 可以是向量或矩阵，得到的 $\mu$ 可以保持

![](img/456a7a56403cbb2b5f1a261793529a51_305_0.png)

![](img/456a7a56403cbb2b5f1a261793529a51_305_1.png)

图 9.5：李群内在值的分布。

