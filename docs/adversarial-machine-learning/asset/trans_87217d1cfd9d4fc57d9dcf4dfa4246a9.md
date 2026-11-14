

**算法 7.1 SVM**
**输入：** 数据库 $\mathbb{D} = \{(\mathbf{x}^{(i)}, y^{(i)})\}_{i=1}^N$ 其中 $\mathbf{x}^{(i)} \in \Re^D, y^{(i)} \in \{-1, 1\}$；核 $k : \Re^D \times \Re^D \to \Re$；凸损失 $\ell$；参数 $C > 0$。

1. $\boldsymbol{\alpha}^* \leftarrow$ 求解公式 (7.1) 中的 SVM 对偶问题。
2. 返回向量 $\boldsymbol{\alpha}^*$。

**定义 7.6** 可再生核希尔伯特空间（RKHS）是在空间 $\mathcal{X}$ 上的实值函数构成的希尔伯特空间$^4$，其中，对于每个点 $\mathbf{x} \in \mathcal{X}$，包含一个点评估函数 $k(\cdot, \mathbf{x})$，该函数对所有 $f \in \mathcal{H}$ 都具有再生核性质 $\langle f, k(\cdot, \mathbf{x})\rangle_{\mathcal{H}} = f(\mathbf{x})$。

特别地，$\langle k(\cdot, \mathbf{x}), k(\cdot, \mathbf{z})\rangle_{\mathcal{H}} = k(\mathbf{x}, \mathbf{z})$。表示定理（Kimeldorf & Wahba 1971）表明，最小化器 $f^* = \arg\min_{f \in \mathcal{H}} [\frac{1}{2} \|f\|_{\mathcal{H}}^2 + \frac{C}{N} \sum_{i=1}^n \ell(y^{(i)}, f(\mathbf{x}^{(i)}))]$ 位于函数 $k(\cdot, \mathbf{x}^{(i)}) \in \mathcal{H}$ 的张成中。事实上，上述对偶展开表明该子空间中的坐标由 $\alpha_i^* y^{(i)}$ 给出。我们将 SVM *机制* 定义为对偶优化，它返回向量 $\boldsymbol{\alpha}^*，如算法 7.1 所述。

## 7.3.1 平移不变核

文献中已提出了若干核函数/特征映射（Burges 1998; Cristianini & Shawe-Taylor 2000; Schölkopf & Smola 2001; Bishop 2006）。*平移不变核* 是我们在后续内容中研究的一类重要核（示例见表 7.1）。

**定义 7.7** 形式为 $k(\mathbf{x}, \mathbf{z}) = g(\mathbf{x} - \mathbf{z})$ 的核函数（其中 $g$ 为某个函数）称为 *平移不变*。

**表 7.1** 平移不变核示例及其在向量 $\Delta = \mathbf{x} - \mathbf{z}$ 上定义的 $g$ 函数

| 核 | $g(\Delta)$ |
| :--- | :--- |
| 径向基核 (RBF) | $\exp\left(-\frac{\|\Delta\|_2^2}{2\sigma^2}\right)$ |
| 拉普拉斯核 (Laplacian) | $\exp(-\|\Delta\|_1)$ |
| 柯西核 (Cauchy) | $\prod_{d=1}^D \frac{2}{1+\Delta_d^2}$ |

$^4$ 希尔伯特空间是关于其范数诱导度量完备的内积空间。

## 7.3.2 算法稳定性

在证明用于私有 SVM 学习的机制的微分隐私边界时，我们将利用 Bousquet & Elisseeff (2002) 确立的正则化 ERM 的一致稳定性。

回顾，我们说一对数据库 D(1), D(2) 是邻域的，如果它们在一个条目上有所不同，我们定义相对于邻域数据库的学习稳定性如下。

> **定义 7.8** 一个将数据库 D 映射为分类器的学习映射 A，如果说其相对于损失 ℓ ( · , · , · ) 具有 γ-一致稳定性，是指对于所有邻域数据库 D, D'，在 D 和 D' 上训练的分类器在所有测试示例上的损失接近，即 || ℓ ( · , A ( D )) - ℓ ( · , A ( D' )) ||∞ ≤ γ 。

稳定性对应于学习映射的平滑性，该概念通常用于统计学习理论中以产生紧密的风险边界，有时当基于类容量的方法（如基于 VC 维的方法）不适用时（Devroye & Wagner 1979; Kearns & Ron 1999; Bousquet & Elisseeff 2002; Kutin & Niyogi 2002）。直观上，如果一个学习映射是稳定的，那么它不会过度受噪声影响，且不太可能遭受过拟合。

## 7.4 基于输出扰动的微分隐私

我们现在专注于与合作者 Bartlett, Huang, 和 Taft 共同开发的一种基于拉普拉斯机制的输出扰动方法（Rubinstein, Bartlett, Huang, & Taft 2009; Rubinstein et al. 2012）。我们考虑具有有限 F 维特征映射的微分私有 SVM 学习。我们首先描述该机制，然后证明保证隐私所需的噪声参数范围（定理 7.10），并推导出该机制产生非私有 SVM 的近似结果的条件（定理 7.11）。

算法 7.2 描述了 PRIVATESVM-FINITE 机制，它是拉普拉斯机制的一个应用（参见第 7.2.1.1 节）：在形成 SVM 的原始解——权重向量 w ∈ R^F——之后，该机制向 w 添加独立同分布的零均值、尺度 λ 的拉普拉斯噪声。微分隐私源自 w 对数据扰动的 ℓ1-灵敏度 Δ，将拉普拉斯噪声尺度设为 λ = Δ/β。

要计算灵敏度——即当训练示例受到扰动时 w 相对于 ℓ1-范数的变化——我们利用正则化 ERM 的一致稳定性（参见定义 7.8）。

> **引理 7.9** 考虑一个损失函数 ℓ (y, ŷ)，其在 ŷ 中是凸的且为 L-Lipschitz，以及由有限 F 维特征映射 ϕ 诱导的 RKHS H，其中对所有 x ∈ R^D 的内核 k (x, x) ≤ κ^2 有界。对于每个数据库 S = {(x^(i), y^(i))}_{i=1}^N，定义
>
> w^(S) ∈ argmin_{w∈R^F} [ C/N Σ_{i=1}^N ℓ ( y^(i), f_w(x^(i)) ) + 1/2 ||w||_2^2 ] 。

**算法 7.2 PRIVATESVM-FINITE**
**输入：** 数据库 $\mathbb{D} = \{(\mathbf{x}^{(i)}, y^{(i)})\}_{i=1}^N$ 其中 $\mathbf{x}^{(i)} \in \Re^D, y^{(i)} \in \{-1, 1\}$；有限特征映射 $\phi : \Re^D \rightarrow \Re^F$ 及其诱导核 $k$；凸损失函数 $\ell$；以及参数 $\lambda, C > 0$。

1. $\boldsymbol{\alpha}^* \leftarrow$ 在 $\mathbb{D}$ 上运行算法 7.1，参数为 $C$，核 $k$，损失 $\ell$；
2. $\tilde{\mathbf{w}} \leftarrow \sum_{i=1}^N \alpha_i^* y^{(i)} \phi \left(\mathbf{x}^{(i)}\right)$；
3. $\boldsymbol{\mu} \leftarrow$ 从 $\text{Laplace}(\mathbf{0}, \lambda)$ 中抽取 $F$ 个标量的独立同分布样本；以及
4. 返回 $\hat{\mathbf{w}} = \tilde{\mathbf{w}} + \boldsymbol{\mu}$。

然后对于每对包含 $N$ 个条目的邻域数据库 $\mathbb{D}, \mathbb{D}'$，我们有 $\left\|\mathbf{w}^{(\mathbb{D})} - \mathbf{w}^{(\mathbb{D}')}\right\|_2 \leq 4LCk/N$，且 $\left\|\mathbf{w}^{(\mathbb{D})} - \mathbf{w}^{(\mathbb{D}')}\right\|_1 \leq 4LC\kappa\sqrt{F}/N$。

证明 该论证紧密遵循 SVM 一致稳定性的证明（Schölkopf & Smola 2001, 定理 12.4）。为方便起见，我们对任何训练集 $\mathbb{S}$ 定义

$R_{\text{reg}}(\mathbf{w}, \mathbb{S}) = \frac{C}{N} \sum_{i=1}^N \ell \left(y^{(i)}, f_{\mathbf{w}}\left(\mathbf{x}^{(i)}\right)\right) + \frac{1}{2} \|\mathbf{w}\|_2^2$
$R_{\text{emp}}(\mathbf{w}, \mathbb{S}) = \frac{1}{N} \sum_{i=1}^N \ell \left(y^{(i)}, f_{\mathbf{w}}\left(\mathbf{x}^{(i)}\right)\right)$。

然后一阶必要 KKT 条件蕴含

$\mathbf{0} \in \partial_{\mathbf{w}} R_{\text{reg}}(\mathbf{w}^{(\mathbb{D})}, \mathbb{D}) = C \partial_{\mathbf{w}} R_{\text{emp}}(\mathbf{w}^{(\mathbb{D})}, \mathbb{D}) + \mathbf{w}^{(\mathbb{D})}, \quad (7.2)$
$\mathbf{0} \in \partial_{\mathbf{w}} R_{\text{reg}}(\mathbf{w}^{(\mathbb{D}')}, \mathbb{D}') = C \partial_{\mathbf{w}} R_{\text{emp}}(\mathbf{w}^{(\mathbb{D}')}, \mathbb{D}') + \mathbf{w}^{(\mathbb{D}')}. \quad (7.3)$

其中 $\partial_{\mathbf{w}}$ 是相对于 $\mathbf{w}$ 的子微分算子。定义辅助风险函数

$\tilde{R}(\mathbf{w}) = C \left\langle \partial_{\mathbf{w}} R_{\text{emp}}(\mathbf{w}^{(\mathbb{D})}, \mathbb{D}) - \partial_{\mathbf{w}} R_{\text{emp}}(\mathbf{w}^{(\mathbb{D}')}, \mathbb{D}'), \mathbf{w} - \mathbf{w}^{(\mathbb{D}')} \right\rangle + \frac{1}{2} \left\| \mathbf{w} - \mathbf{w}^{(\mathbb{D}')} \right\|_2^2$。

注意 $\tilde{R}(\cdot)$ 映射到实数集。很容易看出 $\tilde{R}(\mathbf{w})$ 在 $\mathbf{w}$ 中是严格凸的。将 $\mathbf{w}^{(\mathbb{D}')}$ 代入 $\tilde{R}(\mathbf{w})$ 得到

$\tilde{R}(\mathbf{w}^{(\mathbb{D}')}) = C \left\langle \partial_{\mathbf{w}} R_{\text{emp}} \left(\mathbf{w}^{(\mathbb{D})}, \mathbb{D}\right) - \partial_{\mathbf{w}} R_{\text{emp}} \left(\mathbf{w}^{(\mathbb{D}')}, \mathbb{D}'\right), \mathbf{0} \right\rangle + \frac{1}{2} \|0\|_2^2$
$= \{0\},$

且根据公式 (7.3)

$C \partial_{\mathbf{w}} R_{\text{emp}}(\mathbf{w}^{(\mathbb{D})}, \mathbb{D}) + \mathbf{w} \in C \partial_{\mathbf{w}} R_{\text{emp}}(\mathbf{w}^{(\mathbb{D})}, \mathbb{D}) - C \partial_{\mathbf{w}} R_{\text{emp}}(\mathbf{w}^{(\mathbb{D}')}, \mathbb{D}') + \mathbf{w} - \mathbf{w}^{(\mathbb{D})}$
$= \partial_{\mathbf{w}} \tilde{R}(\mathbf{w}),$

这与公式 (7.2) 结合蕴含 $\mathbf{0} \in \partial_{\mathbf{w}} \tilde{R}(\mathbf{w}^{(\mathbb{D})})$，因此 $\tilde{R}(\mathbf{w})$ 在 $\mathbf{w}^{(\mathbb{D})}$ 处取得最小值。因此存在某个非正的 $r \in \tilde{R}(\mathbf{w}^{(\mathbb{D})})$。接下来，为了记号方便，将 $\tilde{R}(\mathbf{w}^{(\mathbb{D})})$ 的第一项按 $N/C$ 进行缩放并化简。在以下内容中，我们用

