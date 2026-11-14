

其中 \( C \) 是取决于分布的常数。这个界限强调了 VC-维 在控制假设类复杂性中的重要性。较大的 VC-维 需要更大的样本量以避免过拟合并确保可靠的泛化。一些详细示例如下：

- **示例 1：线性分类器在** \( \mathbb{R}^2 \)：考虑假设类 \( H \) 由 \( \mathbb{R}^2 \) 中的线性分类器组成。这些分类器是二维中的超平面，由以下定义：

```
h(x) = \text{sign}(w^T x + b)
```

其中 \( w \in \mathbb{R}^2 \) 是权重向量，\( b \in \mathbb{R} \) 是偏置项。\( \mathbb{R}^2 \) 中线性分类器的 **VC-维** 是 3。可以通过以下方式严格证明：对于 \( \mathbb{R}^2 \) 中的任意 3 个点集，假设类 \( H \) 可以将这些点打散。事实上，3 个点的任何可能的二元标记都可以由某个线性分类器实现。然而，对于 \( \mathbb{R}^2 \) 中的 4 个点，不可能打散所有可能的二元标记（例如，凸四边形的四个顶点），这意味着 VC-维 是 3。

- **示例 2：多项式分类器，次数为** \( d \)：考虑 \( \mathbb{R}^n \) 中的多项式假设类，次数为 \( d \)。假设类 \( H \) 包含形式的多项式：

```
h(x) = \sum_{i_1, i_2, \dots, i_n} \alpha_{i_1, i_2, \dots, i_n} x_1^{i_1} x_2^{i_2} \dots x_n^{i_n}
```

其中 \( \alpha_{i_1, i_2, \dots, i_n} \) 是系数，\( x = (x_1, x_2, \dots, x_n) \)。次数为 \( d \) 的 \( \mathbb{R}^n \) 中多项式分类器的 **VC-维** 增长为 \( O(n^d) \)，这表明假设类的复杂度随着输入空间的次数 \( d \) 和维度 \( n \) 而迅速增加。

神经网络取决于其架构，可以具有非常高的 VC-维。特别是，具有 \( L \) 层、每层包含 \( N \) 个神经元的神经网络的 **VC-维** 通常为 \( O(N^L) \)，这表明 VC-维 随着神经元数量和层数呈指数增长。这一结果提供了对神经网络复杂度及其在训练样本量不足时过拟合数据的能力的洞察。

假设类的 **VC-维** 是统计学习理论中的一个强大工具。它通过衡量假设类打散点集的能力来量化其复杂度，并与模型的泛化能力直接相关。**VC-维定理** 提供了泛化误差和样本复杂度的严格界限，使我们对模型复杂度与泛化之间的权衡有了基本的认识。该理论扩展到更复杂的假设类，如线性分类器、多项式分类器和神经网络，其中它作为控制过拟合并确保在未见数据上可靠性能的关键工具。

### 1.2.2 连续空间中的Rademacher复杂度

**文献综述**：Truong (2022) [31] 在他的文章中探讨了Rademacher复杂度如何影响深度学习中的泛化误差，特别是IID和Markov数据集。Gnecco和Sanguineti (2008) [32] 在再生核希尔伯特空间（RKHS）和函数逼近环境中开发了逼近误差界限。Astashkin (2010) [33] 讨论了对称函数空间中Rademacher函数的应用及其数学结构。Ying和Campbell (2010) [34] 将Rademacher复杂度应用于基于核的学习问题和支持向量机。Zhu等人 (2009) [35] 考察了认知模型和神经表征学习中的Rademacher复杂度。Astashkin等人 (2020) [36] 调查了Rademacher系统在函数空间中的行为及其在泛函分析中的作用。Sachs等人 (2023) [37] 引入了一种针对特定机器学习算法的改进Rademacher复杂度方法。Ma和Wang (2020) [38] 调查了深度残差网络中的Rademacher复杂度界限。Bartlett和Mendelson (2002) [39] 撰写了一篇关于复杂度度量的奠基性论文，为泛化界限提供了基本的理论洞察。Dzahini和Wild (2024) [40] 在他们的论文中将基于Rademacher的复杂度扩展到随机优化方法。McDonald和Shalizi (2011) [41] 表明，使用IID过程的序列Rademacher复杂度，如何控制时间序列模型的泛化误差，其中过去的结果值用于预测未来值。

令 \((\mathcal{X}, \Sigma, \mathcal{D})\) 表示一个概率空间，其中 \(\mathcal{X}\) 是可测空间，\(\Sigma\) 是 σ-代数，\(\mathcal{D}\) 是概率测度。函数类 \(\mathcal{F} \subset L^\infty(\mathcal{X}, \mathbb{R})\) 满足：

\(\sup_{f \in \mathcal{F}} \|f\|_\infty < \infty,\)

其中 \(\|f\|_\infty = \text{ess sup}_{x \in \mathcal{X}}|f(x)|\) 表示本质上确界。为了严谨，假设 \(\mathcal{F}\) 是可测的，意义在于对于每个 \(\epsilon > 0\)，存在一个可数子集 \(\mathcal{F}_\epsilon \subseteq \mathcal{F}\)，使得：

\(\sup_{f \in \mathcal{F}} \inf_{g \in \mathcal{F}_\epsilon} \|f - g\|_\infty \le \epsilon.\)

给定 \(S = \{x_1, x_2, \dots, x_n\} \sim \mathcal{D}^n\)，经验测度 \(\mathbb{P}_n\) 为：

\(\mathbb{P}_n(A) = \frac{1}{n} \sum_{i=1}^n \mathbb{I}_{\{x_i \in A\}}, \quad \forall A \in \Sigma.\)

在 \(\mathbb{P}_n\) 下 \(f \in \mathcal{F}\) 的积分近似于在 \(\mathcal{D}\) 下的总体积分：

\(\mathbb{P}_n[f] = \frac{1}{n} \sum_{i=1}^n f(x_i), \quad \mathcal{D}[f] = \int_{\mathcal{X}} f(x) d\mathcal{D}(x).\)

令 \(\boldsymbol{\sigma} = (\sigma_1, \dots, \sigma_n)\) 为独立的Rademacher随机变量：

\(\mathbb{P}(\sigma_i = +1) = \mathbb{P}(\sigma_i = -1) = \frac{1}{2}, \quad i = 1, \dots, n.\)

这些变量定义于与样本 \(S\) 独立的概率空间 \((\Omega, \mathcal{A}, \mathbb{P})\) 上。经验Rademacher复杂度的对偶与对称化也非常重要。\(\mathcal{F}\) 相对于 \(S\) 的经验Rademacher复杂度为：

\(\hat{\mathfrak{R}}_S(\mathcal{F}) = \mathbb{E}_{\boldsymbol{\sigma}} \left[ \sup_{f \in \mathcal{F}} \frac{1}{n} \sum_{i=1}^n \sigma_i f(x_i) \right],\)

其中 \(\mathbb{E}_{\boldsymbol{\sigma}}\) 表示对 \(\boldsymbol{\sigma}\) 的期望。上确界可以解释为 \(L^\infty(\mathcal{X}, \mathbb{R})\) 中的功能对偶范数，其中 \(\mathcal{F}\) 是单位球。使用对称化技术，Rademacher复杂度与 \(\mathbb{P}_n[f]\) 相对于 \(\mathcal{D}[f]\) 的偏差有关：

\(\mathbb{E}_S \sup_{f \in \mathcal{F}} |\mathbb{P}_n[f] - \mathcal{D}[f]| \le 2 \mathfrak{R}_n(\mathcal{F}),\)

其中：

\(\mathfrak{R}_n(\mathcal{F}) = \mathbb{E}_S \left[ \hat{\mathfrak{R}}_S(\mathcal{F}) \right].\)

这是通过先对样本进行对称化，然后调用Jensen不等式和 \(\boldsymbol{\sigma}\) 的独立性得出的。有一些使用覆盖数和熵的复杂度界限需要讨论。在度量熵中，我们令 \(\|\cdot\|_\infty\) 为 \(\mathcal{F}\) 上的度量。覆盖数 \(N(\epsilon, \mathcal{F}, \|\cdot\|_\infty)\) 满足：

\(N(\epsilon, \mathcal{F}, \|\cdot\|_\infty) = \inf \{m \in \mathbb{N} : \exists \{f_1, \dots, f_m\} \subseteq \mathcal{F}, \forall f \in \mathcal{F}, \exists i, \|f - f_i\|_\infty \le \epsilon \}.\)

关于Dudley熵积分，对于有界函数类 \(\mathcal{F}\)（在 \(\| \cdot \|_\infty\) 下紧）：

$$\mathfrak{R}_n(\mathcal{F}) \le \inf_{\alpha>0} \left( 4\alpha + \frac{12}{\sqrt{n}} \int_\alpha^\infty \sqrt{\log N(\epsilon, \mathcal{F}, \|\cdot\|_\infty)} d\epsilon \right). \quad (34)$$

还有与Talagrand浓度不等式的关系。Talagrand不等式为经验过程的上确界提供尾界：

$$\mathbb{P} \left( \sup_{f \in \mathcal{F}} |\mathbb{P}_n[f] - \mathcal{D}[f]| > \epsilon \right) \le 2 \exp \left( - \frac{n \epsilon^2}{2 \|f\|_\infty^2} \right), \quad (35)$$

这加强了 \(\mathfrak{R}_n(\mathcal{F})\) 与泛化之间的联系。连续函数类中有一些应用。一个例子是带高斯核的RKHS。对于作为带核 \(k(x, x')\) 的RKHS单位球的 \(\mathcal{F}\)，覆盖数满足：

$$\log N(\epsilon, \mathcal{F}, \|\cdot\|_\infty) \sim O \left( \frac{1}{\epsilon^2} \right), \quad (36)$$

得出：

$$\mathfrak{R}_n(\mathcal{F}) \sim O \left( \frac{1}{\sqrt{n}} \right). \quad (37)$$

对于 \(\mathcal{F} \subseteq H^s(\mathbb{R}^d)\)，覆盖数取决于平滑度 \(s\) 和维度 \(d\)：

$$\mathfrak{R}_n(\mathcal{F}) \sim O \left( \frac{1}{n^{s/d}} \right). \quad (38)$$

Rademacher复杂度深嵌于现代经验过程理论中。它与测度论工具、对称化和浓度不等式的复杂关系，为理解高维空间中的泛化提供了坚实的理论基础。

### 1.2.3 索博列夫嵌入

**文献综述**：Abderachid和Kenza (2024) [42] 在他们的论文中调查了使用Riemann-Liouville导数定义的分数索博列夫空间，并研究了它们的嵌入性质。它在这些分数空间和经典索博列夫空间之间建立了新的连续嵌入，为偏微分方程提供了应用。Giang等人 (2024) [43] 引入了加权索博列夫空间，并推导了新的Pólya-Szegö类型不等式。这些不等式在配备权函数的函数空间中建立紧嵌入结果方面起着关键作用。Ruiz和Fragkiadaki (2024) [44] 提供了一种使用Haar函数重新审视分数索博列夫嵌入定理的新方法，并展示了分数索博列夫空间的代数性质，这些性质在非线性分析中至关重要。Bilalov等人 (2025) [45] 分析了Banach函数空间中的紧索博列夫嵌入，将经典的Poincaré和Friedrichs不等式扩展到此设置，并为现代PDE理论中使用的函数空间提供了应用。Cheng和Shao (2025) [46] 为具有无界径向势的函数空间开发了加权索博列夫紧嵌入定理，并利用此结果证明了分数Schrödinger-Poisson方程基态解的存在性。Wei和Zhang (2025) [47] 建立了一个针对Schrödinger-Poisson方程中出现的变分问题量身定制的新嵌入定理，并使用Hardy-Sobolev嵌入来研究零质量情况，这是量子力学中的一个重要案例。Zhang和Qi (2025) [48] 研究了在准线性椭圆方程存在小扰动时索博列夫嵌入的紧性，并使用变分方法证明了多解存在性结果。Xiao和Yue (2025) [49] 为分数Laplacian函数空间建立了索博列夫嵌入定理，并将嵌入结果应用于图像处理，特别是边缘检测。Pesce和Portaro (2025) [50] 研究了内在Hölder空间及其与分数索博列夫嵌入的联系，并建立了新的嵌入结果，用于

