

由于黑森矩阵度量的是似然的曲率，我们可以看到FIM告诉我们似然函数识别最佳参数集的效果如何。（如果似然函数是平坦的，我们无法推断关于参数的任何信息，但如果它是在单一点上的delta函数，最佳参数向量将被唯一确定。）因此，FIM与最大似然估计器的频率派不确定性概念密切相关，这种不确定性由我们期望在从模型中绘制的多个不同数据集上计算最大似然估计器时看到的方差所捕捉。

更精确地说，我们有以下定理。

### 定理 3.3.2. 如果 \( log \, p(x|\theta) \) 二次可微，并在某些正则性条件下，FIM等于NLL的预期黑森矩阵，即，

\[
\mathbf{F}(\theta)_{ij} \triangleq \mathbb{E}_{x\sim\theta} \left[ \left( \frac{\partial}{\partial \theta_i} log \, p(x|\theta) \right) \left( \frac{\partial}{\partial \theta_j} log \, p(x|\theta) \right) \right] = \mathbb{E}_{x\sim\theta} \left[ \frac{\partial^2}{\partial \theta_i \partial \theta_j} log \, p(x|\theta) \right] \tag{3.43}
\]

在证明此结果之前，我们建立以下重要的引理。

### 引理 3.3.1. 评分函数的期望值为零，即，

\[
\mathbb{E}_{p(x|\theta)} [\nabla log \, p(x|\theta)] = \mathbf{0} \tag{3.44}
\]

我们在标量情况下证明此引理。首先，注意由于 \(\int p(x|\theta) dx = 1\)，我们有

\[
\frac{\partial}{\partial \theta} \int p(x|\theta) dx = 0 \tag{3.45}
\]

将此与恒等式结合

\[
\frac{\partial}{\partial \theta} p(x|\theta) = \left[ \frac{\partial}{\partial \theta} log \, p(x|\theta) \right] p(x|\theta) \tag{3.46}
\]

我们有

\[
0 = \int \frac{\partial}{\partial \theta} p(x|\theta) dx = \int \left[ \frac{\partial}{\partial \theta} log \, p(x|\theta) \right] p(x|\theta) dx = \mathbb{E} [s(\theta)] \tag{3.47}
\]

现在我们回到主定理的证明。为简单起见，我们将专注于标量情况，遵循[Ric95, p263]的介绍。

**证明.** 对公式（3.47）求导，我们有

\[
0 = \frac{\partial}{\partial \theta} \int \left[ \frac{\partial}{\partial \theta} log \, p(x|\theta) \right] p(x|\theta) dx \tag{3.48}
\]

\[
= \int \left[ \frac{\partial^2}{\partial \theta^2} log \, p(x|\theta) \right] p(x|\theta) dx + \int \left[ \frac{\partial}{\partial \theta} log \, p(x|\theta) \right] \frac{\partial}{\partial \theta} p(x|\theta) dx \tag{3.49}
\]

\[
= \int \left[ \frac{\partial^2}{\partial \theta^2} log \, p(x|\theta) \right] p(x|\theta) dx + \int \left[ \frac{\partial}{\partial \theta} log \, p(x|\theta) \right]^2 p(x|\theta) dx \tag{3.50}
\]

因此

\[
-\mathbb{E}_{x\sim\theta} \left[ \frac{\partial^2}{\partial \theta^2} log \, p(x|\theta) \right] = \mathbb{E}_{x\sim\theta} \left[ \left( \frac{\partial}{\partial \theta} log \, p(x|\theta) \right)^2 \right] \tag{3.51}
\]

正如所声称的。

现在考虑给定 $N$ 个独立同分布样本 $\mathcal{D} = \{ \mathbf{x}_n : n = 1 : N \}$ 的NLL的黑森矩阵：

$$H_{ij} \triangleq -\frac{\partial^2}{\partial \theta_i \partial \theta_j} \log p(\mathcal{D}|\boldsymbol{\theta}) = - \sum_{n=1}^N \frac{\partial^2}{\partial \theta_i \partial \theta_j} \log p(\mathbf{x}_n|\boldsymbol{\theta})$$

根据上述定理，我们有

$$ \mathbb{E}_{p(\mathcal{D}|\boldsymbol{\theta})} [ \mathbf{H}(\mathcal{D}) | \boldsymbol{\theta} ] = N \mathbf{F}(\boldsymbol{\theta}) $$

这在推导最大似然估计器的采样分布时很有用，如第3.3.3节所讨论。

### 3.3.4.3 示例：二项分布的FIM

假设 $x \sim \text{Bin}(n, \theta)$。单个样本的对数似然为

$$l(\theta|x) = x \log \theta + (n-x) \log(1-\theta)$$

评分函数只是对数似然的梯度：

$$s(\theta|x) \triangleq \frac{d}{d\theta} l(\theta|x) = \frac{x}{\theta} - \frac{n-x}{1-\theta}$$

评分函数的梯度是

$$s'(\theta|x) = -\frac{x}{\theta^2} - \frac{n-x}{(1-\theta)^2}$$

因此Fisher信息由以下给出

$$F(\theta) = \mathbb{E}_{x\sim\theta} [ -s'(\theta|x) ] = \frac{n\theta}{\theta^2} + \frac{n-n\theta}{(1-\theta)^2} = \frac{n}{\theta} + \frac{n}{1-\theta} = \frac{n}{\theta(1-\theta)}$$

### 3.3.4.4 示例：一元高斯分布的FIM

考虑一元高斯分布 $p(x|\boldsymbol{\theta}) = \mathcal{N}(x|\mu, v)$。我们有

$$\ell(\boldsymbol{\theta}) = \log p(x|\boldsymbol{\theta}) = -\frac{1}{2v}(x-\mu)^2 - \frac{1}{2} \log(v) - \frac{1}{2} \log(2\pi)$$

偏导数由以下给出

$$\frac{\partial \ell}{\partial \mu} = (x-\mu)v^{-1}, \frac{\partial^2 \ell}{\partial \mu^2} = -v^{-1}$$

$$\frac{\partial \ell}{\partial v} = \frac{1}{2}v^{-2}(x-\mu)^2 - \frac{1}{2}v^{-1}, \frac{\partial^2 \ell}{\partial v^2} = -v^{-3}(x-\mu)^2 + \frac{1}{2}v^{-2}$$

$$\frac{\partial \ell}{\partial \mu \partial v} = -v^{-2}(x-\mu)$$

因此

$$\mathbf{F}(\boldsymbol{\theta}) = \left( \begin{matrix} \mathbb{E}[v^{-1}] & \mathbb{E}[v^{-2}(x-\mu)] \\ \mathbb{E}[v^{-2}(x-\mu)] & \mathbb{E}[v^{-3}(x-\mu)^2 - \frac{1}{2}v^{-2}] \end{matrix} \right) = \left( \begin{matrix} \frac{1}{v} & 0 \\ 0 & \frac{1}{2v^2} \end{matrix} \right)$$

### 3.3.4.5 示例：逻辑回归的FIM

考虑\(\ell_2\)正则化的二元逻辑回归。负对数联合分布具有以下形式：

\[
\mathcal{E}(\boldsymbol{w}) = -\log[p(\boldsymbol{y}|\mathbf{X}, \boldsymbol{w})p(\boldsymbol{w}|\lambda)] = -\boldsymbol{w}^\mathsf{T}\mathbf{X}^\mathsf{T}\boldsymbol{y} + \sum_{n=1}^N \log(1 + e^{\boldsymbol{w}^\mathsf{T}\boldsymbol{x}_n}) + \frac{\lambda}{2}\boldsymbol{w}^\mathsf{T}\boldsymbol{w}
\]

导数具有以下形式

\[
\nabla_{\boldsymbol{w}} \mathcal{E}(\boldsymbol{w}) = -\mathbf{X}^\mathsf{T}\boldsymbol{y} + \mathbf{X}^\mathsf{T}\boldsymbol{s} + \lambda \boldsymbol{w}
\]

其中 \(s_n = \sigma(\boldsymbol{w}^\mathsf{T}\boldsymbol{x}_n)\)。FIM由以下给出

\[
\mathbf{F}(\boldsymbol{w}) = \mathbb{E}_{p(\boldsymbol{y}|\mathbf{X}, \boldsymbol{w}, \lambda)} \left[ \nabla^2 \mathcal{E}(\boldsymbol{w}) \right] = \mathbf{X}^\mathsf{T} \boldsymbol{\Lambda} \mathbf{X} + \lambda \mathbf{I}
\]

其中 \(\boldsymbol{\Lambda}\) 是带有以下条目的 \(N \times N\) 对角矩阵

\[
\Lambda_{nn} = \sigma(\boldsymbol{w}^\mathsf{T}\boldsymbol{x}_n)(1 - \sigma(\boldsymbol{w}^\mathsf{T}\boldsymbol{x}_n))
\]

### 3.3.4.6 指数族分布的FIM

在本节中，我们讨论如何推导具有自然参数 \(\boldsymbol{\eta}\) 的指数族分布的FIM，它概括了许多前面的示例。回顾从等式（2.216）可知，对数划分函数的梯度是期望充分统计量

\[
\nabla_{\boldsymbol{\eta}} A(\boldsymbol{\eta}) = \mathbb{E}[\mathcal{T}(\boldsymbol{x})] = \boldsymbol{m}
\]

并且从等式（2.247）可知，对数似然的梯度是统计量减去其期望值：

\[
\nabla_{\boldsymbol{\eta}} \log p(\boldsymbol{x}|\boldsymbol{\eta}) = \mathcal{T}(\boldsymbol{x}) - \mathbb{E}[\mathcal{T}(\boldsymbol{x})]
\]

因此，关于自然参数的FIM \(\mathbf{F}_\boldsymbol{\eta}\) 由以下给出

\[
(\mathbf{F}_\boldsymbol{\eta})_{ij} = \mathbb{E}_{p(\boldsymbol{x}|\boldsymbol{\eta})} \left[ \frac{\partial \log p(\boldsymbol{x}|\boldsymbol{\eta})}{\partial \eta_i} \frac{\partial \log p(\boldsymbol{x}|\boldsymbol{\eta})}{\partial \eta_j} \right]
= \mathbb{E}_{p(\boldsymbol{x}|\boldsymbol{\eta})} [(\mathcal{T}(\boldsymbol{x})_i - m_i)(\mathcal{T}(\boldsymbol{x})_j - m_j)]
= \text{Cov}[\mathcal{T}(\boldsymbol{x})_i, \mathcal{T}(\boldsymbol{x})_j]
\]

或者，简言之，

\[
\mathbf{F}_\boldsymbol{\eta} = \text{Cov}[\mathcal{T}(\boldsymbol{x})]
\]

有时我们需要计算关于矩参数 \(\boldsymbol{m}\) 的Fisher：

\[
(\mathbf{F}_{\boldsymbol{m}})_{ij} = \mathbb{E}_{p(\boldsymbol{x}|\boldsymbol{m})} \left[ \frac{\partial \log p(\boldsymbol{x}|\boldsymbol{\eta})}{\partial m_i} \frac{\partial \log p(\boldsymbol{x}|\boldsymbol{\eta})}{\partial m_j} \right]
\]

