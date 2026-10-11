

## 4.1.6.3 分析

我们定义斜率矩阵 $\mathbf{\Delta}$ 的 $l_1$ 和 $l_2$ 正则化项如下，

(4.7) $\parallel \mathbf{\Delta} \parallel_{1}: = \sum\limits_{j = 1}^{d}\left\| \mathbf{\Delta}_{j.} \right\|_{1},\quad \parallel \mathbf{\Delta} \parallel_{F}^{2}: = \sum\limits_{j = 1}^{d}\left\| \mathbf{\Delta}_{j.} \right\|_{2}^{2}.\qquad (4.7)$

正如我们在 [第 4.1.4 节](#9783110785937_013188.xhtml#b_9783110785944-004_s_001_s_004) 中讨论的那样，这两个正则化项分别诱导稀疏性和平滑性。不同之处在于，由于重参数化，现在受到惩罚的是参数 $\boldsymbol{\theta}(t - 1)$ 和 $\boldsymbol{\theta}(t)$ 之间的差异，而非它们包含的实际值（后者不太可能为零）。

所提出的重参数化可以在模型内存消耗方面带来巨大的改进。显然，减少的量取决于具体的数据集。因此，更令人惊讶的是，重参数化本身可以在不造成任何损害的情况下应用——它可以表示任何自然参数。让我们考虑一下我们先前直觉的一个恰当定义。为了通用性，设 $C$ 为底层图的任意团（例如一条边）。

**定义 4** (分段线性重参数化 [[567]](#backmatter-001.xhtml#b_9783110785944-010_ref_567))。*设 $G$ 为长度为 $T$ 的时空图，且 $\mathbf{D}(h) \in [0; 1]^{h \times h}$ 为下单位三角矩阵*[^(12)](#fn12)

(4.8) $\theta[C = x'] = \eta[\mathbf{D}(h)](\mathbf{\Delta}[C = x']) = \mathbf{D}(h)\mathbf{\Delta}[C = x'] \qquad (4.8)$

*其中 $h = T - (\max\{t' \mid v(t') \in C\} - \min\{t' \mid v(t') \in C\})$ 称为时空随机场。*

基于该定义，我们可以推导出一些有用的性质。

**引理 5** (重参数化的普适性)。*时空重参数化是普适的。即，分段线性重参数化是一个双射。*

**证明** 确实，根据定义 4，任意 $\mathbf{\Delta} \in \mathbb{R}^d$ 都可以通过与 $\mathbf{D}$ 相乘映射到某个 $\boldsymbol{\theta} \in \mathbb{R}^d$。要看到逆命题也成立，请注意对于每个 $t \in [T]$，由于单位三角性，$\det \mathbf{D}(h) = \prod_{i = 1}^{T}\mathbf{D}(h)_{i,i} = 1$。因此每个 $\mathbf{D}(h)$ 都是可逆的，分块对角矩阵 $\mathbf{D}^\circ$ 也是如此。因此，对于任何给定的自然参数 $\boldsymbol{\theta}[C = y]$，我们可以通过 $\mathbf{\Delta}[C = y] = \mathbf{D}^{-1}\boldsymbol{\theta}[C = y]$ 找到对应的重参数化。即 $\eta[\mathbf{D}]$ 是双射的，因此是普适的。 ◼

由于 $\eta[\mathbf{D}]$ 是普适的，任何自然参数都可以通过某个 $\mathbf{\Delta}$ 来表示。此外，$\eta[\mathbf{D}]$ 是 $\mathbf{\Delta}$ 的线性函数。函数的凸性在与线性函数复合时得以保持。因此，重参数化后的负平均对数似然 $\ell(\eta[\mathbf{D}](\mathbf{\Delta});\mathcal{D}) = A(\eta[\mathbf{D}](\mathbf{\Delta})) - \langle \eta[\mathbf{D}](\mathbf{\Delta}), \tilde{\boldsymbol{\mu}} \rangle$ 是 $\mathbf{\Delta}$ 的凸函数。

到目前为止，我们尚未节省任何内存，因为 $\mathbf{\Delta}$ 和 $\boldsymbol{\theta}$ 具有相同的维度。通过在重参数化目标上施加 $l_1$ 和 $l_2$ 正则化，我们得到如下问题

(4.9) $\min\limits_{\mathbf{\Delta} \in \mathcal{R}^{d}}\underbrace{A\left( {\eta_{D}(\mathbf{\Delta})} \right) - \left\langle {\eta_{D}(\mathbf{\Delta}),\widetilde{\boldsymbol{\mu}}} \right\rangle + \frac{\lambda_{2}}{2} \parallel \mathbf{\Delta} \parallel_{F}^{2} + \lambda_{1} \parallel \mathbf{\Delta} \parallel_{1}}_{\mathcal{l}^{\text{ST}}(\mathbf{\Delta};\mathcal{D})}.\qquad (4.9)$

以下定理表明，我们用于设计重参数化的直觉确实产生了预期的效果——它允许我们通过检测连续自然参数中可忽略不计的变化，将冗余转化为稀疏性。此外，多项式数量的样本足以以高概率实现较小的估计误差。

**定理 6** (STRF 一致性)。*考虑一个具有指数族密度的随机变量 $\mathbf{X}$，参数 $\boldsymbol{\theta}^* \in \mathbb{R}^d$ 其重参数化在所有等价参数中范数最小，以及一个长度为 $T$ 的广义序列结构。我们得到一个包含 $N = |\mathcal{D}|$ 个来自 $\mathbf{X}$ 的样本的数据集 $\mathcal{D}$。假设 $\|\nabla^2 A(\boldsymbol{\theta}^*)^{-1}\|_\infty \le \kappa$ 和 $\|\mathbf{\Delta}\|_\infty \le \gamma$，并设 $\lambda_1 = 4T\sqrt{\log(d)/N} \text{ and } \lambda_2 = \gamma^{-1}\lambda_1$。如果 $N \ge 324\kappa^4 d^{12} \log(d)/(T - d^2)^2$，则对于任意衰减矩阵 $\mathbf{D}$：*

*   *真实参数 $\boldsymbol{\theta}^*$ 与估计值 $\eta[\mathbf{D}](\hat{\mathbf{\Delta}})$ 之间的距离是有界的，即*
    $\|\eta[\mathbf{D}](\hat{\mathbf{\Delta}}) - \boldsymbol{\theta}^*\|_\infty \le 3\kappa d^2 \lambda_1$，
*   *估计值中的任何稀疏性都意味着真实参数中存在某些冗余，即* $\hat{\mathbf{\Delta}}[C = x'](t) = 0 \Rightarrow$
    $$
    \begin{matrix}
    \left| {\theta_{C = x'}^*(t - 1) - \theta_{C = x'}^*(t)} \right| \\
    \leq \frac{3d^2 \kappa \lambda_1}{T} + (t - 1)\left( {\max\limits_{i = 1}^{t - 1}\left| {\hat{\Delta}_{C = x'}(i)} \right| + \frac{3d^2 \kappa \lambda_1}{T}} \right),
    \end{matrix}
    $$
    *对于任意团 $C$ 和时间点 $t$ 均成立。上述两个陈述至少以 $1 - (2/d)$ 的概率成立。*

该陈述的证明见 [[567]](#backmatter-001.xhtml#b_9783110785944-010_ref_567)。

### 4.1.7 实验

我们在两个真实世界数据集上评估了我们提出方法的性能，其中每个数据集由一个空间图 $G_0 = (V_0, E_0)$ 描述，该图包含一组传感器 $V_0$ 和连接 $E_0$，以及一组历史传感器读数 $\mathcal{D}$。我们评估两种方法：具有原始参数化的 MRF (MRF) 和时空随机场[^(13)](#fn13)。

首先我们讨论模型训练。我们研究了生成模型的预测质量和稀疏性与正则化参数的关系。我们还展示了可分优化对训练时间的影响。接下来，讨论测试集上的预测质量，涉及训练模型的稀疏性（从而包括内存中的大小）。最后，我们讨论关于 STRF 模型可解释性的定性结果。

