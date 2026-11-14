# 深度学习的数学基础







# 1 数学基础

深度学习是一种用于解决高维函数逼近问题的计算范式。其核心在于以下三方面的协同作用：

- **函数逼近：** 使用神经网络表示复杂的非线性函数。函数逼近是深度学习的基本概念之一，也是深度学习模型（尤其是神经网络）解决复杂问题的核心所在。在深度学习的语境下，函数逼近是指神经网络表示复杂、高维、非线性函数的能力，这些函数通常难以或无法使用传统数学技术建模。

- **优化理论：** 高效求解非凸优化问题。优化理论在深度学习中起着核心作用，因为训练深度神经网络的目标本质上是寻找一组最优参数（权重和偏置），以最小化预定义的目标（通常称为损失函数）。该目标通常衡量网络预测与真实值之间的差异。优化技术指导训练过程，并决定神经网络从数据中学习的效果。

- **统计学习理论：** 理解对未见数据的泛化行为。统计学习理论（SLT）为理解机器学习算法（包括深度学习模型）的行为提供了数学基础。它提供了关于模型如何从训练数据泛化到未见数据的关键见解，这对于确保深度学习模型不仅在训练集上准确，而且在新的、先前未见的数据上也能表现良好至关重要。SLT 有助于解决过拟合、偏差-方差权衡和泛化误差等基本挑战。

问题可以形式化为：

Find \(f_\theta : X \rightarrow Y\)，使 \(\mathbb{E}_{x,y \sim P}[\ell(f_\theta(x), y)]\) 最小化：

(1)

其中 \(X\) 为输入空间，\(Y\) 为输出空间，\(P\) 为数据分布，\(\ell(\cdot, \cdot)\) 为损失函数，\(\theta\) 为神经网络的参数。这项任务涉及多个学科的综合运用，下文将对每个学科进行严谨的详细探讨。

## 1.1 问题定义：风险泛函作为空间间的映射

### 1.1.1 可测函数空间

可测空间是度量论中的一个基本构造，记作 \((\mathcal{X}, \Sigma)\)，其中 \(\mathcal{X}\) 是一个非空集合，称为基础集或样本空间，而 \(\Sigma\) 是一个 \(\sigma\)-代数，即 \(\mathcal{X}\) 的特定子集集合，用于编码可测性的概念。\(\sigma\)-代数 \(\Sigma \subseteq 2^\mathcal{X}\)（即 \(\mathcal{X}\) 的幂集）满足三个公理，每个公理都确保在集合运算下具有封闭性这一关键特性。首先，\(\Sigma\) 在补运算下封闭，即对于任意集合 \(A \in \Sigma\)，其补集 \(A^c = \mathcal{X} \setminus A\) 也属于 \(\Sigma\)。这保证了以数学上一致的方式定义可测事件“不发生”的能力。其次，\(\Sigma\) 在可数并运算下封闭：对于任意可数集合 \(\{A_n\}_{n=1}^\infty \subseteq \Sigma\)，其并集 \(\bigcup_{n=1}^\infty A_n\) 也属于 \(\Sigma\)，从而使得通过可数无穷运算构造可测集成为可能。根据德摩根定律，这还意味着在可数交运算下封闭，因为 \(\bigcap_{n=1}^\infty A_n = (\bigcup_{n=1}^\infty A_n^c)^c\)，确保该框架能够容纳可数集合的交集。最后，空集 \(\emptyset \in \Sigma\) 的包含是一个公理，提供了一个空基线，确保 \(\sigma\)-代数非空并能表示某些结果的“不可能性”。

**文献综述：** Rao 等人（2024）[1] 在勒贝格可测函数空间内研究了逼近理论，对算子收敛性进行了分析。他们还建立了勒贝格空间中函数逼近的理论框架，并对函数空间中的对称性进行了严谨的研究。Mukhopadhyay 和 Ray（2025）[2] 对可测函数空间进行了全面介绍，重点介绍了 Lp-空间及其完备性性质。他们还确立了 Lp-空间在度量论中的基本作用，并讨论了连续函数空间与可测函数之间的关系。Szoldra（2024）[3] 在量子力学中考察了可测函数空间，探讨了可测可观测量在遍历论中的作用。他们将函数分析与度量论与量子态演化相结合，为函数空间中的量子机器学习提供了数学基础。Lee（2025）[10] 在 AI 模型的可测函数空间背景下研究了度量空间理论和函数分析。他形式化了函数空间如何对 AI 中的自参照结构进行建模，并在度量论与生成模型之间提供了桥梁。Song 等人（2025）[4] 在城市更新和绩效评估的背景下讨论了可测函数空间。他们使用可测函数空间开发了一种严格的评估指标，并探讨了应用数据科学和城市分析中的函数空间属性。Mennaoui 等人（2025）[5] 在演化方程理论中研究了可测函数空间，这是函数分析的一个关键概念。他们对可测算子函数进行了严格研究，并为函数空间及其在求解微分方程中的作用提供了新的见解。Pedroza（2024）[6] 使用函数空间研究了机器学习模型中的域稳定性。他建立了函数光滑性与域自适应之间的正式数学关系，并利用拓扑和可测函数空间分析学习模型中的稳定性条件。Cerveira-Vioglio 和 Ok（2024）[7] 为可测集值函数开发了一种新的积分理论。他们引入了对 Banach 值函数积分的泛化，并在可测函数空间中建立了弱紧性性质。Averin（2024）[8] 将可测函数空间应用于引力熵理论。他利用函数空间形式主义对熵界进行了严格证明，并将度量论与相对论场方程相结合。Potter（2025）[9] 在傅里叶分析和晶体结构的背景下研究了可测函数空间。他建立了关于可测函数傅里叶变换的新结果，并引入了一种用于研究不变移位算子中函数空间的新框架。

可测空间不仅仅是抽象结构，更是度量论、概率论和积分论的骨干。例如，实数 \(\mathbb{R}\) 上的 Borel \(\sigma\)-代数 \(\mathcal{B}(\mathbb{R})\) 是包含所有开区间 \((a, b)\)（其中 \(a, b \in \mathbb{R}\)）的最小 \(\sigma\)-代数。这个 \(\sigma\)-代数在定义勒贝格测度时至关重要，其中可测集将经典的区间概念推广到了包括既非开集也非闭集的集合。此外，由子集集合 \(\mathcal{C} \subseteq 2^{\mathcal{X}}\) 生成的 \(\sigma\)-代数（记作 \(\sigma(\mathcal{C})\)）提供了一个包含 \(\mathcal{C}\) 并满足所有 \(\sigma\)-代数性质的最小框架，从而能够系统地将可测性扩展到更复杂的场景。例如，从 \(\mathbb{R}\) 中的区间出发，可以构建 Borel \(\sigma\)-代数，这是现代分析中的一个关键工具。

可测空间的结构允许定义测度 \(\mu\)，即函数 \(\mu : \Sigma \rightarrow [0, \infty]\)，它为 \(\Sigma\) 中的每个集合赋予一个非负值，遵循两个关键公理：\(\mu(\emptyset) = 0\) 和可数可加性，后者指出对于任意不相交的集合 \(\{A_n\}_{n=1}^{\infty} \subseteq \Sigma\)，其并集的测度满足 \(\mu \left( \bigcup_{n=1}^{\infty} A_n \right) = \sum_{n=1}^{\infty} \mu(A_n)\)。这一性质对于将长度、面积和体积等直观概念扩展到任意可测集不可或缺，为勒贝格积分铺平了道路。若函数 \(f : \mathcal{X} \rightarrow \mathbb{R}\) 满足对于每个 Borel 集 \(B \in \mathcal{B}(\mathbb{R})\)，其原像 \(f^{-1}(B)\) 属于 \(\Sigma\)，则称该函数为 \(\Sigma\)-可测。这个定义确保了函数与 \(\sigma\)-代数的兼容性，这是在概率论中定义积分和期望的必要条件。

总结而言，可测空间代表了一种高度通用且数学严谨的框架



工作，支撑着分析和概率等广泛领域。其理论深度在于能够系统地处理无限运算，同时在定义测度、可测函数和积分时保持封闭性、一致性和灵活性。因此，可测空间的严格研究对于推进现代数学理论不可或缺，它在抽象集合论与现实世界现象的应用之间架起了一座桥梁。

设 $(\mathcal{X}, \Sigma_X, \mu_X)$ 和 $(\mathcal{Y}, \Sigma_Y, \mu_Y)$ 为可测空间。真实风险泛函定义为：

$$
\mathcal{R}(f) = \int_{\mathcal{X} \times \mathcal{Y}} \ell(f(x), y) dP(x, y), \quad (2)
$$

其中：

- \( f \) 属于假设空间 \(\mathcal{F} \subseteq L^p(\mathcal{X}, \mu_X)\)。
- \( P(x, y) \) 是 \(\mathcal{X} \times \mathcal{Y}\) 上的 Borel 概率测度，满足 \(\int_{\mathcal{X} \times \mathcal{Y}} 1 dP = 1\)。

### 1.1.2 作为泛函的风险

文献综述：Wang et al. (2025) [11] 基于泛函变分法开发了一种数学风险模型，并引入了损失泛函正则化框架，以最小化深度学习模型中的对抗风险。他们还在安全环境中提出了泛函风险的博弈论解释。Duim and Mesquita (2025) [12] 通过将风险定义为概率空间上的泛函，扩展了逆强化学习（IRL）框架，并使用贝叶斯泛函先验来建模风险敏感行为。他们还引入了一种迭代正则化风险泛函最小化方法。Khayat et al. (2025) [13] 建立了泛函 Sobolev 范数以量化对抗环境中的风险，并引入了一种使用深度神经架构的功能风险分解技术。他们还为受对抗扰动网络中的风险估计提供了深入的理论框架。Agrawal (2025) [14] 为风险作为损失泛函开发了变分框架，并使用损失函数的自适应加权来增强深度学习的泛化能力。他还对风险泛函最小化提供了严格的收敛性分析。Hailmichael and Ayaleew (2025) [15] 使用控制屏障函数（CBF）理论开发了风险感知的深度学习模型，并将风险建模为动态系统上的泛函，以优化稳定性和鲁棒性。他们还引入了一种风险最小化的受约束优化公式。Nguyen et al. (2025) [16] 为风险敏感的深度模型开发了一种泛函度量学习方法，并使用凸优化技术推导功能风险界。他们还为风险正则化学习建立了半监督损失函数。Luo et al. (2025) [17] 在深度学习模型中引入了风险泛函的几何解释，并使用积分变换技术来近似现实世界视觉系统中的风险。他们还开发了一种针对对抗鲁棒性的泛函方法。

泛函 \(\mathcal{R} : \mathcal{F} \rightarrow \mathbb{R}_+\) 是 Fréchet 可微的，如果：

$$
\forall f, g \in \mathcal{F}, \quad \mathcal{R}(f + \epsilon g) = \mathcal{R}(f) + \epsilon \langle \nabla \mathcal{R}(f), g \rangle + o(\epsilon), \quad (3)
$$

其中 \(\langle \cdot, \cdot \rangle\) 表示 \(L^2(\mathcal{X})\) 中的内积。在风险管理和决策理论领域，**风险泛函**的概念是一种数学形式化，它捕捉了给定结果或状态的风险是如何量化的。风险泛函，记为 \(\mathcal{R}\)，作为一个映射，从给定空间 \(X\)（代表可能的结果或状态）中取出元素，并返回一个实值风险度量。这个风险度量 \(\mathcal{R}(x)\) 表达了与特定元素 \(x \in X\) 相关的风险程度或不利结果。空间 \(X\) 可能因上下文而异——这可能是随机变量、轨迹或更复杂的函数空间。风险泛函将 \(x\) 映射到 \(\mathbb{R}\)，即 \(\mathcal{R} : X \rightarrow \mathbb{R}\)，其中每个 \(\mathcal{R}(x)\) 都反映了与特定实现 \(x\) 相关的风险。

风险泛函最基础的形式之一基于损失函数 \( L(x) \) 的期望，其中 \( x \in X \) 表示随机变量或状态，\( L(x) \) 量化了与该状态相关的损失。风险泛函可以表示为期望损失，数学上写作：

\(\mathcal{R}(x) = \mathbb{E}[L(x)] = \int_X L(x)p(x) dx\)

其中 \( p(x) \) 是结果 \( x \) 的概率密度函数，积分是在整个空间 \( X \) 上进行的。在这种设置中，\( L(x) \) 可以是任何衡量结果 \( x \) 严重性或不利性质的函数。在金融环境中，\( L(x) \) 可能代表投资组合的损失函数，而 \( p(x) \) 将是投资组合收益的概率密度函数。在许多情况下，会使用 \( L(x) \) 的特定形式，例如 \( L(x) = (x - \mu)^2 \)，其中 \( \mu \) 是目标或期望值。这种选择使得风险泛函代表结果 \( x \) 的**方差**，表示为：

\(\mathcal{R}(x) = \int_X (x - \mu)^2 p(x) dx\)

这种公式捕捉了围绕均值的结果的变异性或离散程度，是投资组合优化或风险管理等应用中常见的风险度量。另外，另一类广泛使用的风险泛函源于**基于分位数的风险度量**，例如**风险价值（VaR）**，它关注损失分布的极端尾部行为。置信水平 \(\alpha \in [0, 1]\) 下的 VaR 定义为最小值 \( l \)，使得 \( L(x) \) 超过 \( l \) 的概率不大于 \( 1 - \alpha \)，即：

\( P(L(x) \le l) \ge \alpha \)

这定义了一个阈值，超过该阈值后，最坏结果预计将以 \( 1 - \alpha \) 的概率发生。风险价值提供了在正常情况下最坏损失的度量，但不提供关于超过该阈值的损失严重程度的信息。为了解决这一局限性，引入了**条件风险价值（CVaR）**，它衡量在损失超过 VaR 阈值时的期望损失。数学上，水平 \(\alpha\) 下的 CVaR 由以下给出：

\(\text{CVaR}_\alpha(x) = \mathbb{E}[L(x) \mid L(x) \ge \text{VaR}_\alpha(x)]\)

这个条件期望对 VaR 阈值之外的潜在极端损失提供了更详细的评估。CVaR 是一个更全面的度量，捕捉尾部风险，并提供关于极端不利事件规模的宝贵信息。

在空间 \( X \) 表示**轨迹**或路径的情况下，例如在连续时间过程或动态系统的上下文中，风险泛函通常用时间上的积分来公式化。例如，考虑 \( x(t) \) 作为函数空间 \( \mathcal{C}([0, T], \mathbb{R}^n) \)（即区间 \([0, T]\) 上的连续函数空间）中的轨迹。在这种情况下，风险泛函可以量化轨迹随时间与参考轨迹或目标轨迹的总偏差。一个典型示例可以是总平方偏差，表示为：

\(\mathcal{R}(x) = \int_0^T \|x(t) - \bar{x}(t)\|^2 dt\)

其中 \( \bar{x}(t) \) 表示参考轨迹，\(\| \cdot \|\) 是一个范数，例如欧几里得范数。这个风险泛函量化了轨迹在整个时间间隔内与目标路径的总偏差（或**能量**），并用于控制理论和最优轨迹规划等各种应用。范数 \(\|x(t)\|\) 的一个常见选择可能是 \(\|x(t)\|^2 = \sum_{i=1}^n x_i^2(t)\)，其中 \(x_i(t)\) 是 \(\mathbb{R}^n\) 中轨迹 \(x(t)\) 的分量。

在某些情况下，可能结果的空间 \(X\) 可能不是有限维向量空间，而是 **Banach 空间** 或 **Hilbert 空间**，特别是当 \(x\) 表示函数或轨迹等复杂对象时。例如，空间 \(\mathcal{C}([0, T], \mathbb{R}^n)\) 是 Banach 空间，而风险泛函可能涉及



对该函数空间上的积分进行评估。在这种情况下，风险函数可以采用以下形式：

```
\mathcal{R}(x) = \int_0^T \|x(t)\|_p^p dt
```

其中，\(\| \cdot \|_p\) 是 p-范数，且 \(p \ge 1\)。当 \(p = 2\) 时，该风险函数表示轨迹的总**能量**，但也可使用其他范数来强调不同类型的风险。例如，\(L^\infty\)-范数将关注轨迹与目标路径之间的最大偏差。**凸性**的概念在风险函数理论中起着重要作用。凸性确保，两个状态 \(x_1\) 和 \(x_2\) 的**凸组合**所关联的风险小于或等于各个状态风险的加权平均。在数学上，对于 \(\lambda \in [0, 1]\)，凸性要求：

```
\mathcal{R}(\lambda x_1 + (1 - \lambda)x_2) \le \lambda \mathcal{R}(x_1) + (1 - \lambda)\mathcal{R}(x_2)
```

这一特性反映了风险管理中的多样化效应，即混合多个状态或结果通常会导致总体风险降低。凸风险函数在组合论中尤其重要，因为它们允许通过多样化来最小化风险。例如，如果 \(\mathcal{R}(x)\) 表示投资组合收益的方差，则凸性特性确保组合不同资产将产生比任何单个资产风险更低的整体风险的投资组合。**单调性**是风险函数的另一个重要属性，确保随着结果变得更不利，风险会增加。如果根据某些偏序关系 \(x_1\) 比 \(x_2\) 更差，则：

```
\mathcal{R}(x_1) \ge \mathcal{R}(x_2)
```

单调性确保风险函数的行为符合风险的直观概念：更不利的结果与更高的风险相关。在金融语境下，这体现在**损失**会增加相关风险度量的事实。最后，在某些应用中，风险函数源自扰动分析，以研究参数的微小变化如何影响总体风险。将 \(x(\epsilon)\) 视为扰动轨迹，其中 \(\epsilon\) 是一个小参数，风险函数对 \(\epsilon\) 的 Fréchet 导数由以下给出：

```
\frac{d}{d\epsilon}\mathcal{R}(x(\epsilon))\Big|_{\epsilon=0}
```

该导数量化了风险对系统扰动的敏感性，在稳定性和鲁棒性分析中至关重要。此类分析在**随机控制**和**优化**等领域至关重要，在其中理解模型参数的微小变化如何影响风险概况很重要。

因此，风险函数是量化和管理不确定性的强大工具，其表述可以适应各种环境，从随机变量和随机过程到连续轨迹和动态系统。风险函数为在复杂系统中评估和最小化风险提供了严格的数学框架，其灵活性使其适用于广泛的领域。

## 1.2 神经网络的逼近空间

神经网络假设空间 \(\mathcal{F}_\theta\) 参数化如下：

```
\mathcal{F}_\theta = \{f_\theta : \mathcal{X} \to \mathbb{R} \mid f_\theta(x) = \sum_{j=1}^n c_j \sigma(a_j \cdot x + b_j), \theta = (c, a, b)\}.
```

为了分析其容量，我们依赖于：

- 离散假设的 VC-维理论。
- 连续空间的 Rademacher 复杂度：

```
\(\mathcal{R}_N(\mathcal{F}) = \mathbb{E}_{\epsilon} \left[ \sup_{f \in \mathcal{F}} \frac{1}{N} \sum_{i=1}^N \epsilon_i f(x_i) \right],\) (14)
```

其中，\(\epsilon_i\) 是独立同分布的 Rademacher 随机变量。

### 1.2.1 离散假设的 VC-维理论

VC-维（Vapnik-Chervonenkis 维）是统计学习理论中的一个基本概念，用于量化假设类对一组数据点进行多种标记拟合的能力。VC-维对于理解分类器的泛化能力特别有用。该理论在机器学习中很重要，尤其是在评估过拟合和模型复杂性风险时。

**文献综述：** 有几篇文章非常严谨地探讨了离散假设的 VC-维理论。N. Bousquet 和 S. Thomassé (2015) [18] 在其论文中探讨了图论背景下的 VC-维，将其与结构性质（如 Erdős-Pósa 性质）联系起来。Yıldız 和 Alpaydın (2009) [19] 在其文章中计算了决策树假设空间的 VC-维，考虑了离散和连续特征。Zhang et al. (2012) [20] 引入了离散化的 VC-维，以连接实值和离散假设空间，为复杂度分析提供了新的理论工具。Riondato 和 Zdonik (2011) [21] 将 VC-维理论改编为数据库系统，使用理论视角分析 SQL 查询选择性。Riggle 和 Sonderegger (2010) [22] 在语言模型中研究了 VC-维，重点关注语法假设空间。Anderson (2023) [23] 对模糊系统中的 VC-维提供了全面综述，特别是在涉及离散结构的逻辑框架中。Fox et al. (2021) [24] 证明了有界 VC-维系统的关键猜想，提供了对组合论含义的见解。Johnson (2021) [25] 讨论了二进制表示和 VC-维，对离散假设建模具有含义。Janzing (2018) [26] 在其论文中关注因果推断框架中低 VC-维的假设类。Hüllermeier 和 Tehrani (2012) [27] 在其论文中探讨了 Choquet 积分的理论 VC-维，并将其应用于离散机器学习模型。Mehryar Mohri、Afshin Rostamizadeh 和 Ameet Talwalkar 撰写的《机器学习基础》[28] 在统计学习背景下对 VC-维提供了非常好的基础性讨论。Felipe Cucker 和 Ding-Xuan Zhou 撰写的另一本书《学习理论：一种近似理论视角》[29] 讨论了 VC-维在近似理论中的作用。Shai Shalev-Shwartz 和 Shai Ben-David 撰写的另一本书《理解机器学习：从理论到算法》[30] 包含关于假设空间和 VC-维的详细章节。

对于离散假设，VC-维理论适用于将一组输入点映射为二进制输出标签（通常为 0 或 1）的假设类。对于一个假设类，VC-维是指该类可以“击碎”的最大数据点集，其中“击碎”意味着该假设类可以实现这些点的所有可能标记。

我们将讨论 **形式数学框架**。设 \(X\) 为一个有限或无限集合，称为**实例空间**，它表示输入空间。考虑一个假设类 \(H\)，其中每个假设 \(h \in H\) 都是一个函数 \(h : X \rightarrow \{0, 1\}\)。函数 \(h\) 将 \(X\) 的每个元素分类为两个类之一：0 或 1。给定子集 \(S = \{x_1, x_2, \dots, x_k\} \subseteq X\)，如果对于每一个可能的标记 \(\vec{y} = (y_1, y_2, \dots, y_k) \in \{0, 1\}^k\)，都存在某个 \(h \in H\)，使得对于所有 \(i \in \{1, 2, \dots, k\}\)：

\(h(x_i) = y_i\) (15)

换句话说，假设类 \(H\) 击碎 \(S\) 是指它可以在集合 \(S\) 上产生每一个可能的二进制标记。**VC-维** \(VC(H)\) 被定义为 \(H\) 可以击碎的最大集合 \(S\) 的大小：

```
VC(H) = sup\{k | \exists S \subseteq X, |S| = k, S \text{ is shattered by } H\} \quad (16)
```

如果没有点集可以被击碎，则 VC-维为 0。VC-维的一些属性如下：

- 1. **击碎意味着非空假设类**：如果集合 \(S\) 被 \(H\) 击碎，则 \(H\) 非空。这直接源于这样一个事实：对于每个标记 \(\vec{y} \in \{0, 1\}^k\)，都存在某个 \(h \in H\) 产生相应的标记。因此，\(H\) 必须至少包含一个假设。

- 2. **击碎的上界**：给定假设类 \(H\)，如果存在 \(S \subseteq X\) 的大小为 \(k\) 的集合，使得 \(H\) 可以击碎 \(S\)，那么 \(X\) 中任何大小大于 \(k\) 的集合 \(S' \subseteq X\) 都不能被击碎。这给出了关键结果：

```
VC(H) \ge k \text{ if } H \text{ can shatter a set of size } k \quad (17)
```

- 3. **泛化的影响** 在 **统计学习** 理论中，一个核心结果是 VC-维与 **泛化误差** 之间的联系。具体来说，**VC-维** 限制了假设类对未见数据进行泛化的能力。VC-维越高，假设类越复杂，越有可能 **过拟合** 训练数据，从而导致泛化能力差。

我们将讨论 VC-维与泛化界（VC 定理）。**VC-维定理**（通常称为 **Hoeffding 界** 或 **泛化界**）对训练误差与真实误差之间的关系提供了概率保证。具体而言，它给出了泛化误差超过经验误差（训练误差）超过 \(\epsilon\) 的概率的上界。

设 \(\mathcal{D}\) 为抽取训练数据的分布，并让 \(\hat{err}(h)\) 和 \(err(h)\) 分别表示假设 \(h \in H\) 的 **经验误差** 和 **真实误差**：

```
\hat{err}(h) = \frac{1}{n} \sum_{i=1}^n \mathbf{1}_{\{h(x_i) \neq y_i\}} \quad (18)
```

```
err(h) = \mathbb{P}_{(x,y)\sim \mathcal{D}}(h(x) \neq y) \quad (19)
```

其中，\(\{(x_1, y_1), \dots, (x_n, y_n)\}\) 是来自分布 \(\mathcal{D}\) 的独立同分布（i.i.d.）样本。对于具有 **VC-维** \(d = \text{VC}(H)\) 的假设类 \(H\)，以至少 \(1 - \delta\) 的概率，对所有 \(h \in H\) 都有以下结论：

```
|\hat{err}(h) - err(h)| \le \epsilon \quad (20)
```

其中，\(\epsilon\) 被界定为：

```
\epsilon \le \sqrt{\frac{8}{n} \left( d \log \left( \frac{2n}{d} \right) + \log \left( \frac{4}{\delta} \right) \right)} \quad (21)
```

此结果表明，只要样本量 \(n\) 足够大且 VC-维 \(d\) 不太大，泛化误差（真实误差与经验误差之差）就会以高概率较小。为保证以高概率 \(1 - \delta\) 使泛化误差在 \(\epsilon\) 以内所需的样本复杂度 \(n\) 由以下给出：

```
n \ge \frac{C}{\epsilon^2} \left( d \log \left( \frac{1}{\epsilon} \right) + \log \left( \frac{1}{\delta} \right) \right) \quad (22)
```





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



与超抛物算子相关的函数空间。

Sobolev 嵌入定理指出：

\( W^{k,p}(\mathcal{X}) \hookrightarrow C^m(\mathcal{X}), \tag{39} \)

if \( k - \frac{d}{p} > m \), ensuring \( f_\theta \in C^\infty(\mathcal{X}) \) for smooth activations \( \sigma \). For a function \( u \in L^p(\Omega) \), its weak derivative \( D^\alpha u \) satisfies:

\( \int_\Omega u(x)D^\alpha \phi(x) \, dx = (-1)^{|\alpha|} \int_\Omega v(x)\phi(x) \, dx \quad \forall \phi \in C_c^\infty(\Omega), \tag{40} \)

where \( v \in L^p(\Omega) \) is the weak derivative. This definition extends the classical notion of differentiation to functions that may not be pointwise differentiable. The Sobolev norm encapsulates both function values and their derivatives:

\( \|u\|_{W^{k,p}(\Omega)} = \left( \sum_{|\alpha| \leq k} \| D^\alpha u \|_{L^p(\Omega)}^p \right)^{1/p}. \tag{41} \)

Key properties:

- **Semi-norm Dominance**: The \( W^{k,p} \) norm is controlled by the seminorm \( |u|_{W^{k,p}} \), ensuring sensitivity to high-order derivatives.
- **Poincaré Inequality**: For \( \Omega \) bounded, \( u - u_\Omega \) satisfies:

\( \|u - u_\Omega\|_{L^p} \leq C \| Du \|_{L^p}. \tag{42} \)

Sobolev spaces \( W^{k,p}(\Omega) \) embed into \( L^q(\Omega) \) or \( C^m(\overline{\Omega}) \), depending on \( k, p, q \), and \( n \). These embeddings govern the smoothness and integrability of \( u \) and its derivatives. There are several Advanced Theorems on Sobolev Embeddings. They are as follows:

- 1. **Sobolev Embedding Theorem**: Let \( \Omega \subset \mathbb{R}^n \) be a bounded domain with Lipschitz boundary. Then:
  - If \( k > n/p \), \( W^{k,p}(\Omega) \hookrightarrow C^{m,\alpha}(\overline{\Omega}) \) with \( m = \lfloor k - n/p \rfloor \) and \( \alpha = k - n/p - m \).
  - If \( k = n/p \), \( W^{k,p}(\Omega) \hookrightarrow L^q(\Omega) \) for \( q < \infty \).
  - If \( k < n/p \), \( W^{k,p}(\Omega) \hookrightarrow L^q(\Omega) \) where \( \frac{1}{q} = \frac{1}{p} - \frac{k}{n} \).
- 2. **Rellich-Kondrachov Compactness Theorem**: The embedding \( W^{k,p}(\Omega) \hookrightarrow L^q(\Omega) \) is compact for \( q < \frac{np}{n-kp} \). Compactness follows from:
  - (a) **Equicontinuity**: \( W^{k,p} \) boundedness ensures uniform control over oscillations.
  - (b) **Rellich's Selection Principle**: Strong convergence follows from uniform estimates and tightness.

The Proof of Sobolev Embedding starts with the Scaling Analysis. Define \( u_\lambda(x) = u(\lambda x) \). Then:

\( \| u_\lambda \|_{L^p(\Omega)} = \lambda^{-n/p} \| u \|_{L^p(\lambda^{-1} \Omega)}. \tag{43} \)

For derivatives:

\( \| D^\alpha u_\lambda \|_{L^p(\Omega)} = \lambda^{|\alpha| - n/p} \| D^\alpha u \|_{L^p(\lambda^{-1} \Omega)}. \tag{44} \)

The scaling relation \(\lambda^{k-n/p}\) aligns with the Sobolev embedding condition \(k > n/p\). Sobolev norms in \(\mathbb{R}^n\) are equivalent to decay rates of Fourier coefficients:

\(\|u\|_{W^{k,p}} \sim \left( \int_{\mathbb{R}^n} |\xi|^{2k} |\hat{u}(\xi)|^2 d\xi \right)^{1/2}.\)

For \(k > n/p\), Fourier decay implies uniform bounds, ensuring \(u \in C^{m,\alpha}\). Interpolation spaces bridge \(L^p\) and \(W^{k,p}\), providing finer embeddings. Duality: Sobolev embeddings are equivalent to boundedness of adjoint operators in \(L^q\). For \(-\Delta u = f\), \(u \in W^{2,p}(\Omega)\) ensures \(u \in C^{0,\alpha}(\overline{\Omega})\) if \(p > n/2\). Sobolev spaces govern variational problems in geometry, e.g., minimal surfaces and harmonic maps. On \(\Omega\) with fractal boundaries, trace theorems refine Sobolev embeddings.

### 1.2.4 Rellich-Kondrachov 紧性定理

The **Rellich-Kondrachov Compactness Theorem** is one of the most fundamental and deep results in the theory of Sobolev spaces, particularly in the study of functional analysis and the theory of partial differential equations. The theorem asserts the compactness of certain Sobolev embeddings under appropriate conditions on the domain and the function spaces involved. This result is of immense significance in mathematical analysis because it provides a rigorous justification for the fact that bounded sequences in Sobolev spaces, under certain conditions, have strongly convergent subsequences in lower-order normed spaces. In essence, the theorem states that while weak convergence in Sobolev spaces is relatively straightforward due to the Banach-Alaoglu theorem, strong convergence is not always guaranteed. However, under the assumptions of the Rellich-Kondrachov theorem, strong convergence in \(L^q(\Omega)\) can indeed be obtained from boundedness in \(W^{1,p}(\Omega)\). The compactness property ensured by this theorem is much stronger than mere boundedness or weak convergence and plays a crucial role in proving the existence of solutions to variational problems by ensuring that minimizing sequences possess convergent subsequences in an appropriate function space. The theorem can also be viewed as a generalization of the classical **Arzelà–Ascoli theorem**, extending compactness results to function spaces that involve derivatives.

### Literature Review

Lassoued (2026) [51] examined function spaces on the torus and their lack of compactness, highlighting cases where the classical Rellich-Kondrachov result fails. He extended compact embedding results to function spaces with periodic structures. He also discussed trace theorems and regular function spaces in this new context. Chen et al. (2024) [52] extended the Rellich-Kondrachov theorem to Hörmander vector fields, a class of differential operators that appear in hypoelliptic PDEs. They established a degenerate compact embedding theorem, generalizing previous results in the field. They also provided applications to geometric inequalities, highlighting the role of compact embeddings in PDE theory. Adams and Fournier (2003) [53] in their book provided a complete proof of the Rellich-Kondrachov theorem, along with a discussion of compact embeddings. They also covered function space theory, embedding theorems, and applications in PDEs. Brezis (2010) [54] wrote a highly recommended resource for understanding Sobolev spaces and their compactness properties. The book included applications to variational methods and weak solutions of PDEs. Evans (2022) [55] in his classic PDE textbook includes a discussion of compact Sobolev embeddings, their implications for weak convergence, and applications in variational methods. Maz'ya (2011) [56] provided a detailed treatment of Sobolev space theory, including compact embedding theorems in various settings.

To rigorously state the theorem, we consider a bounded open domain \(\Omega \subset \mathbb{R}^n\) with a **Lipschitz boundary**. For \(1 \le p < n\), the theorem asserts that the embedding

\(W^{1,p}(\Omega) \hookrightarrow L^q(\Omega)\)

is **compact** whenever \( q \le \frac{np}{n-p} \). More precisely, this means that if \(\{u_k\} \subset W^{1,p}(\Omega)\) is a bounded sequence in the Sobolev norm, i.e., there exists a constant \( C > 0 \) such that

\(\|u_k\|_{W^{1,p}(\Omega)} = \|u_k\|_{L^p(\Omega)} + \|\nabla u_k\|_{L^p(\Omega)} \le C, \quad (47)\)

then there exists a **subsequence** \(\{u_{k_j}\}\) and a function \( u \in L^q(\Omega) \) such that

\( u_{k_j} \to u \quad \text{strongly in } L^q(\Omega), \quad (48) \)

which means that

\(\|u_{k_j} - u\|_{L^q(\Omega)} \to 0 \quad \text{as } j \to \infty. \quad (49)\)

To establish this rigorously, we first recall the fact that **bounded sequences in** \( W^{1,p}(\Omega) \) **are weakly precompact**. Since \( W^{1,p}(\Omega) \) is a **reflexive Banach space** for \( 1 < p < \infty \), the Banach-Alaoglu theorem ensures that any bounded sequence \(\{u_k\}\) in \( W^{1,p}(\Omega) \) has a subsequence (still denoted by \(\{u_k\}\)) and a function \( u \in W^{1,p}(\Omega) \) such that

\( u_k \rightharpoonup u \quad \text{in } W^{1,p}(\Omega). \quad (50) \)

This means that for all test functions \(\varphi \in W^{1,p'}(\Omega)\), where \( p' \) is the Hölder conjugate of \( p \) satisfying \( \frac{1}{p} + \frac{1}{p'} = 1 \), we have

\( \int_\Omega u_k \varphi \, dx \to \int_\Omega u \varphi \, dx, \quad \int_\Omega \nabla u_k \cdot \nabla \varphi \, dx \to \int_\Omega \nabla u \cdot \nabla \varphi \, dx. \quad (51) \)

However, weak convergence alone does not imply compactness. To obtain strong convergence in \( L^q(\Omega) \), we need additional arguments. This is accomplished using the **Fréchet-Kolmogorov compactness criterion**, which states that a bounded subset of \( L^q(\Omega) \) is compact if and only if it is **tight** and **uniformly equicontinuous**. More formally, compactness follows if:

- 1. The sequence \( u_k(x) \) does not oscillate excessively at small scales.
- 2. The sequence \( u_k(x) \) does not escape to infinity in a way that prevents strong convergence.

To quantify this, we invoke the **Sobolev-Poincaré inequality**, which states that for \( p < n \), there exists a constant \( C \) such that

\( \|u - u_\Omega\|_{L^q(\Omega)} \le C \|\nabla u\|_{L^p(\Omega)}, \quad u_\Omega = \frac{1}{|\Omega|} \int_\Omega u(x) \, dx. \quad (52) \)

Applying this inequality to \( u_k - u \), we obtain

\( \|u_k - u\|_{L^q(\Omega)} \le C \|\nabla(u_k - u)\|_{L^p(\Omega)}. \quad (53) \)

Since \(\nabla u_k\) is weakly convergent in \( L^p(\Omega) \), we have

\( \|\nabla u_k - \nabla u\|_{L^p(\Omega)} \to 0. \quad (54) \)

Thus,

\( \|u_k - u\|_{L^q(\Omega)} \to 0, \quad (55) \)

which establishes the **strong convergence** in \( L^q(\Omega) \), completing the proof. The key insight is that compactness arises because the gradients of \( u_k \) provide control over the oscillations of \( u_k \), ensuring that the sequence cannot oscillate indefinitely without converging in norm. The crucial role of Sobolev embeddings is to guarantee that even though \( W^{1,p}(\Omega) \) does not embed compactly into itself, it does embed compactly into \( L^q(\Omega) \) for \( q < \frac{np}{n-p} \). This embedding ensures that weak convergence in \( W^{1,p}(\Omega) \) implies strong convergence in \( L^q(\Omega) \), proving the theorem.





# 2 通用逼近定理：精细证明

通用逼近定理（UAT）是神经网络理论中的一项基本结果，指出：在使用合适的激活函数的前提下，包含单个隐藏层且隐藏层神经元数量有限的前馈神经网络，可以以任意所需的精度逼近 R^n 上紧子集中的任何连续函数。该定理在机器学习、函数逼近和深度学习架构方面具有重要意义。

文献综述：Hornik 等人（1989 年）[57] 在其开创性论文中严格证明了，带有单个隐藏层和 sigmoid 激活函数的多层前馈神经网络可以逼近紧集上的任何连续函数。该研究扩展了此前的结果，并为现代对 UAT 的理解奠定了基础。

Cybenko（1989 年）[58] 使用 sigmoid 函数作为激活函数，给出了 UAT 的首批严格证明之一。他们表明，单隐藏层网络可以以任意精度逼近任何连续函数。

Barron（1993 年）[59] 通过量化逼近误差并分析收敛速率扩展了 UAT。这项工作为理解神经网络的实际效率至关重要。

Pinkus（1999 年）[60] 从逼近理论的角度对 UAT 提供了全面的综述，并讨论了不同激活函数下的逼近条件以及神经网络的理论极限。

Lu 等人（2017 年）[61] 研究了神经网络的宽度如何影响其逼近能力，挑战了“更深的网络总是更好”的观念。他们还深入探讨了深度与宽度之间的权衡。

Hanin 和 Sellke（2018 年）[62] 将 UAT 扩展到 ReLU 激活函数，表明深层 ReLU 网络在保持最小宽度约束的同时实现了通用逼近。

Garcia-Cervera 等人（2024 年）[63] 将通用逼近定理扩展到集值函数及其在深层算子网络（DeepONets）中的应用，这些网络在控制理论和 PDE 建模中很有用。

Majee 等人（2024 年）[64] 探讨了使用马尔可夫链蒙特卡罗（MCMC）技术求解逆问题时深层神经网络的通用逼近特性。

Toscano 等人（2024 年）[65] 引入了 Kurkova-Kolmogorov-Arnold 网络（KKANs），这是 UAT 的一种扩展，结合了 Kolmogorov 的叠加定理以提高逼近能力。

Son（2025 年）[66] 基于 UAT 建立了算子学习的新框架，为无需反向传播的深层网络提供了理论基础。

## 2.1 使用卷积算子进行逼近

让我们首先考虑卷积算子及其在通用逼近定理（UAT）背景下的函数逼近中的作用。假设 \( f : \mathbb{R}^n \rightarrow \mathbb{R} \) 是一个连续且有界的函数。函数 \( f \) 与核函数 \( \phi : \mathbb{R}^n \rightarrow \mathbb{R} \)（表示为 \( f * \phi \)）的卷积定义为

```
\( (f * \phi)(x) = \int_{\mathbb{R}^n} f(y)\phi(x - y) \, dy. \quad (56) \)
```

核函数 \( \phi(x) \) 通常被选择为光滑、紧支持且归一化，使得

```
\( \int_{\mathbb{R}^n} \phi(x) \, dx = 1. \quad (57) \)
```

为了局部逼近 \( f \)，我们引入缩放参数 \( \epsilon > 0 \) 并定义缩放核 \( \phi_\epsilon(x) \) 为

```
\( \phi_\epsilon(x) = \epsilon^{-n} \phi\left( \frac{x}{\epsilon} \right). \quad (58) \)
```

因子 \( \epsilon^{-n} \) 确保 \( \phi_\epsilon(x) \) 保持为概率密度函数，满足

```
\( \int_{\mathbb{R}^n} \phi_\epsilon(x) \, dx = \int_{\mathbb{R}^n} \phi(x) \, dx = 1. \quad (59) \)
```

函数 \( f \) 与缩放核 \( \phi_\epsilon \) 的卷积由下式给出：

$$(f * \phi_\epsilon)(x) = \int_{\mathbb{R}^n} f(y)\phi_\epsilon(x - y) \, dy.$$

进行变量替换 $z = \frac{x-y}{\epsilon}$，得到 $y = x - \epsilon z$ 且 $dy = \epsilon^n dz$。将其代入积分，得到

$$(f * \phi_\epsilon)(x) = \int_{\mathbb{R}^n} f(x - \epsilon z)\phi(z) \, dz.$$

这种表示表明 $(f * \phi_\epsilon)(x)$ 是 $f(x)$ 的平滑版本，平滑程度由参数 $\epsilon$ 控制。当 $\epsilon \to 0$ 时，核函数 \( \phi_\epsilon(x) \) 在 \( x\) 附近越来越集中，在极限下恢复 \( f(x) \)：

$$\lim_{\epsilon \to 0}(f * \phi_\epsilon)(x) = f(x),$$

假设 \( f \) 是连续的。该结果可以利用核函数 \( \phi \) 的属性（如其光滑性和紧支持性）以及支配收敛定理进行严格证明，支配收敛定理确保积分一致收敛到 \( f(x) \)。

现在，让我们考虑卷积算子在神经网络逼近函数 \( f \) 中的作用。单层前馈神经网络表示为

$$\hat{f}(x) = \sum_{i=1}^M c_i \sigma(w_i^T x + b_i),$$

其中 \( c_i \in \mathbb{R} \) 是系数，\( w_i \in \mathbb{R}^n \) 是权重向量，\( b_i \in \mathbb{R} \) 是偏置，\( \sigma : \mathbb{R} \to \mathbb{R} \) 是激活函数。

激活函数 \( \sigma(w_i^T x + b_i) \) 可以解释为局部响应函数，类似于卷积中的核函数 \( \phi(x - y) \)。

通过在两者之间建立类比，神经网络逼近可以写为

$$\hat{f}(x) \approx \sum_{i=1}^M f(x_i)\phi_\epsilon(x - x_i)\Delta x$$

其中 \( \phi_\epsilon(x) \) 被解释为由 \( w_i, b_i \) 和 \( \sigma \) 定义的参数化核函数，\( \Delta x \) 表示离散步长。

逼近误差 \( \|f - \hat{f}\|_\infty \) 可分解为两个分量：

$$\|f - \hat{f}\|_\infty \le \|f - f * \phi_\epsilon\|_\infty + \|f * \phi_\epsilon - \hat{f}\|_\infty.$$

项 \( \|f - f * \phi_\epsilon\|_\infty \) 表示用核函数 \( \phi_\epsilon \) 平滑 \( f \) 时引入的误差，只要 \( f \) 足够规整（例如，满足 Lipschitz 连续性），就可以通过选择足够小的 \( \epsilon \) 使该误差变得任意小。

项 \( \|f * \phi_\epsilon - \hat{f}\|_\infty \) 量化了离散引起的误差，该误差随着神经元数量 \( M \to \infty \) 而消失。

为了严格分析 \( \hat{f}(x) \) 到 \( f(x) \) 的收敛性，我们依赖于神经网络逼近器在函数空间中的稠密性。

通用逼近定理指出，对于紧定义域 \( \Omega \subset \mathbb{R}^n \) 上的任何连续函数 \( f \) 和任何 \( \epsilon > 0 \)，都存在一个具有有限多个神经元的神经网络 \( \hat{f} \)，使得

$$\sup_{x \in \Omega} |f(x) - \hat{f}(x)| < \epsilon.$$

该结果依赖于激活函数 \( \sigma \) 生成丰富基函数集的能力。

例如，如果 \( \sigma(x) = \max(0, x) \)（ReLU），则网络通过分段线性函数逼近 \( f(x) \)。

如果 \( \sigma(x) = \frac{1}{1+e^{-x}} \)（sigmoid），则网络生成类似于逻辑回归的平滑逼近。

在这个精细化的 UAT 证明中，卷积算子提供了一个统一的框架，用于理解神经网络逼近所依赖的平滑、定位和离散化过程。

\( \phi_\epsilon(x) \)、\( f * \phi_\epsilon(x) \) 和 \( \hat{f}(x) \) 之间的相互作用揭示了连接经典逼近理论与现代机器学习的深刻数学结构。

这种联系不仅增强了我们对神经网络的理论理解，还指导了针对实际应用的架构和算法设计。

### 2.1.1 Stone-Weierstrass 应用

文献综述：Rudin（1976 年）[67] 引入了魏尔斯特拉斯逼近定理，并证明了其推广，即 Stone-Weierstrass 定理。

他还讨论了函数空间的代数结构，以及该定理如何确保连续函数的一致多项式逼近。

他还展示了与紧性、一致收敛和 Banach 代数结构相关的示例和练习。

Stein 和 Shakarchi（2005 年）[68] 将 Stone-Weierstrass 定理扩展到测度论和函数分析中。

他还在 Lebesgue 积分的背景下证明了该定理。

他还讨论了该定理如何应用于 Hilbert 空间和正交多项式。

他还将该定理与傅里叶分析和谱分解联系起来。

Conway（2019 年）[69] 在 Banach 代数和 C*-代数的设置中探讨了 Stone-Weierstrass 定理。

他还将该定理扩展到非交换函数代数，并讨论了该定理在 Hilbert 空间中的算子论意义。

他还分析了该定理在谱理论中的应用。

Dieudonné（1981 年）[70] 追溯了函数分析的历史发展，包括 Stone-Weierstrass 定理的起源，并讨论了 Karl Weierstrass 和 Marshall Stone 的贡献。

他还探讨了该定理如何影响拓扑向量空间和算子理论，并包含了关于函数逼近公理化发展的观点。

Folland（1999 年）[71] 深入讨论了 Stone-Weierstrass 定理及其在概率论和 ergodic 理论中的应用，并使用该定理确立了测度空间中代数函数的稠密性。

他还将 Stone-Weierstrass 定理与 Lp 空间中的函数逼近联系起来。

他还探讨了 Stone-Weierstrass 定理与 Hahn-Banach 定理之间的相互作用。

Sugiura（2024 年）[72] 将 Stone-Weierstrass 定理扩展到机器学习中的储层计算研究，并证明某些神经网络可以在该定理的假设下对函数进行一致逼近。

他弥合了经典函数逼近与现代 AI 和深度学习之间的差距。

Liu 等人（2024 年）[73] 在赋范模态设置中研究了 Stone-Weierstrass 定理，并利用范畴论推广了函数逼近结果。

他还将该定理扩展到实值函数之外，应用于结构化数学对象。

Martinez-Barreto（2025 年）[74] 提供了该定理的带严格证明的现代表述，并回顾了算子代数和拓扑中的应用。

他还讨论了与函数逼近相关的开放问题。

Chang 和 Wei（2024 年）[75] 使用 Stone-Weierstrass 定理推导了新的算子不等式，并将该定理应用于量子力学中的函数分析。

Caballer 等人（2024 年）[76] 研究了 Stone-Weierstrass 定理失效的情况，并提供了反例和一致逼近的改进条件。

Chen（2024 年）[77] 将 Stone-Weierstrass 定理扩展到广义函数空间，并引入了一类新的均匀拓扑代数。

Rafiei 和 Akbarzadeh-T（2024 年）[78] 使用 Stone-Weierstrass 定理分析模糊逻辑系统中的函数逼近，并探讨了控制系统和 AI 中的应用。

Stone-Weierstrass 定理在函数分析中充当基石，连接了连续函数的代数结构与逼近理论。

当应用于通用逼近定理（UAT）时，该定理为断言神经网络可以逼近紧集上定义的任何连续函数提供了严格基础。

为了以最科学和最具数学严谨性的形式理解这一联系，我们必须仔细分析紧 Hausdorff 空间上连续函数的代数以及神经网络在逼近这些函数中的作用，确保以极高精度探讨所有数学细微差别。

令 \( X \) 为紧 Hausdorff 空间，并让 \( C(X) \) 表示 \( X \) 上连续实值函数的空间。

函数 \( f \in C(X) \) 的上确界范数 \( ||f||_\infty \) 定义为：

```
||f||_\infty = \sup_{x \in X} |f(x)| (67)
```

这个上确界范数在定义连续函数之间的接近程度时至关重要，因为我们试图用子代数 \( A \subset C(X) \) 中的函数 \( g \) 逼近任何函数 \( f \in C(X) \)。

The Stone-

**魏尔斯特拉斯定理**保证，如果子代数 $A$ 满足两个基本性质——（1）它包含常数函数，（2）它能分离点——那么 $A$ 在极准范数下的闭合将是整个空间 $C(X)$。为形式化这一点，我们定义**点分离性质**如下：对于每一对不同的点 $x_1, x_2 \in X$，存在函数 $h \in A$，使得 $h(x_1) \neq h(x_2)$。该条件确保来自 $A$ 的函数足够“丰富”，以区分 $X$ 中的不同点。数学上，这表示为：

$\exists h \in A \text{ such that } h(x_1) \neq h(x_2) \quad \forall x_1, x_2 \in X, x_1 \neq x_2$ (68)

给定这两个性质，Stone-Weierstrass 定理断言，对于任何连续函数 $f \in C(X)$ 和任何 $\epsilon > 0$，存在元素 $g \in A$，使得：

$\|f - g\|_\infty < \epsilon$ (69)

该结果确保，紧致豪斯多夫空间上的任何连续函数都可以由足够丰富的子代数中的函数任意逼近。在**通用逼近定理（UAT）**的背景下，我们试图将 Stone-Weierstrass 定理应用于神经网络的逼近能力。设 $K \subseteq \mathbb{R}^n$ 为一个紧子集，并设 $f \in C(K)$ 为该集合上定义的连续函数。带有非线性激活函数 $\sigma$ 的前馈神经网络形式为：

$\hat{f}_\theta(x) = \sum_{i=1}^N w_i \sigma(\langle \mathbf{w}_i, x \rangle + b_i)$ (70)

其中 $\langle \mathbf{w}_i, x \rangle$ 表示权重向量 $\mathbf{w}_i$ 与输入 $x$ 之间的内积，$b_i$ 表示偏置项。激活函数 $\sigma$ 通常是非线性的（如 sigmoid 或 ReLU 函数），参数 $\theta = \{w_i, b_i\}_{i=1}^N$ 是网络的权重和偏置。函数 $\hat{f}_\theta(x)$ 是对 $x$ 的仿射变换应用非线性激活后的加权和。

我们现在探讨神经网络与 Stone-Weierstrass 定理之间的联系。一个关键观察是：带有非线性激活的神经网络所定义的函数集是 $C(K)$ 的一个子代数，前提是激活函数 $\sigma$ 的非线性足够丰富。这种非线性确保网络可以分离 $K$ 中的点，这意味着对于任何两个不同的点 $x_1, x_2 \in K$，都存在一个网络函数 $\hat{f}_\theta$，在该点处取不同的值。这满足了 Stone-Weierstrass 定理要求的点分离条件。为形式化这一点，考虑两个不同的点 $x_1, x_2 \in K$。由于 $\sigma$ 是非线性的，经过适当选择权重和偏置的函数 $\hat{f}_\theta(x)$ 将满足：

$\hat{f}_\theta(x_1) \neq \hat{f}_\theta(x_2)$ (71)

因此，神经网络函数的代数满足点分离性质。通过应用 Stone-Weierstrass 定理，我们得出结论：该代数在 $C(K)$ 中稠密，这意味着对于任何连续函数 $f \in C(K)$ 和任何 $\epsilon > 0$，都存在一个神经网络函数 $\hat{f}_\theta$，使得：

$\|f(x) - \hat{f}_\theta(x)\|_\infty < \epsilon \quad \forall x \in K$ (72)

这一严格结果表明，带有非线性激活函数的神经网络可以在紧集上以极准范数任意逼近任何连续函数，从而证明了通用逼近定理。为进一步探讨这一点，考虑误差项：

$\|f(x) - \hat{f}_\theta(x)\|_\infty$ (73)

对于给定函数 $f$ 和紧集 $K$，通过增加神经网络隐藏层中的神经元数量，可以使该误差项任意小。这增加了网络的容量，实际上扩大了网络生成的函数子代数，从而提高了逼近精度。随着神经元数量的增加，网络逼近 C(K) 中任何函数的能力变得越来越精确，这与 Stone-Weierstrass 定理的结论一致，即网络函数在 C(K) 中形成一个稠密子代数。因此，通过 Stone-Weierstrass 定理推导出的通用逼近定理，严格证明了神经网络可以以任意所需的精度逼近紧集上的任何连续函数。激活函数的非线性与神经网络架构的结合，保证网络可以生成连续函数的稠密子代数，最终使其能够逼近 C(K) 中的任何函数。这一结果不仅形式化了神经网络的逼近能力，还为理解其作为通用逼近器的能力提供了深厚的理论基础。

## 2.2 深度与宽度：容量分析

### 2.2.1 表达能力界定

柯尔莫哥罗夫-阿诺德叠加定理是多变量连续函数及其分解数学分析中的基础结果，为支撑神经网络表达能力的框架提供了依据。它断言，任何连续多变量函数都可以表示为连续一元函数和加法的有限复合。它最早由安德烈·柯尔莫哥罗夫于 1956 年提出猜想，后来由弗拉基米尔·阿诺德于 1957 年严格证明。从形式上看，该定理保证任何连续多变量函数 \(f : [0, 1]^n \to \mathbb{R}\) 都可以表示为连续一元函数 \(\Phi_q\) 和 \(\psi_{pq}\) 的有限复合。具体来说，对于 \(f(x_1, x_2, \dots, x_n)\)，存在函数 \(\Phi_q : \mathbb{R} \to \mathbb{R}\) 和 \(\psi_{pq} : \mathbb{R} \to \mathbb{R}\)，使得

\[
f(x_1, x_2, \dots, x_n) = \sum_{q=0}^{2n} \Phi_q \left( \sum_{p=1}^n \psi_{pq}(x_p) \right),
\]
(74)

其中，函数 \(\psi_{pq}(x_p)\) 编码输入变量 \(x_p\) 的一元投影，而外层函数 \(\Phi_q\) 将这些投影汇总为最终输出。这一分解突出了多变量连续函数的一个基本性质：它们的表达性可以通过更简单的一元组件的分层复合来捕捉。

**文献综述：** 关于柯尔莫哥罗夫-阿诺德叠加定理（KST）有一些经典参考文献。Kolmogorov (1957) [79] 在其关于 KST 的奠基性论文中确立，任何多变量连续函数都可以表示为单变量连续函数和加法的叠加。这是一项突破性工作，因为它提供了一种与内积空间无关的通用函数分解方法。他证明存在函数 \(\phi_q\) 和 \(\psi_q\) 使得任何函数 \(f(x_1, x_2, \dots, x_n)\) 都可以表示为：

\[
f(x_1, \dots, x_n) = \sum_{q=1}^{2n+1} \phi_q \left( \sum_{p=1}^n \psi_{qp}(x_p) \right)
\]
(75)

其中 \(\psi_{qp}\) 是一元函数。柯尔莫哥罗夫为逼近理论和神经网络提供了数学基础，影响了现代机器学习架构。Arnold (1963) [80] 通过证明可以将叠加限制为最多两个变量的函数而不是一个变量，改进了柯尔莫哥罗夫定理。阿诺德的表述导出了**柯尔莫哥罗夫-阿诺德表示**：

\[
f(x_1, \dots, x_n) = \sum_{q=1}^{2n+1} \phi_q \left( x_q + \sum_{p=1}^n \psi_{qp}(x_p) \right)
\]
(76)

这使得该定理更适合实际计算。阿诺德增强了神经网络的表达能力，启发了高维环境下的替代函数表示。

Lorentz (2008) [81] 在其著作中讨论了 KST 在逼近理论和构造数学中的重要性。他提供了使用柯尔莫哥罗夫类型分解逼近多变量函数的误差估计。他展示了 KST 如何融入 Bernstein 逼近理论。他帮助在函数逼近的背景下构建 KST，将其与计算应用联系起来。Pinkus (1999) [60] 分析了 **KST 在多层感知机（MLP）中的作用**，展示了它如何影响神经网络中的函数表达性。他证明了前馈神经网络可以使用柯尔莫哥罗夫叠加逼近任意函数。他还提供了通用逼近所需的网络深度和宽度的界限。他在理解深度学习的理论威力方面发挥了关键作用。KST（2024–2025 年）有几项现代贡献。Guilhoto and Perdikaris (2024) [82] 探讨了如何使用深度学习架构重新表述 KST。他们提出了柯尔莫哥罗夫-阿诺德网络（KAN），这是一种受 KST 启发的新型神经网络。他们表明，KAN 在函数逼近任务中优于传统前馈网络。他们还提供了 KAN 在现实世界数据集中效率的经验证据。他们还引入了机器学习的新范式，使函数分解更具可解释性。Alhafiz, M. R. et al. (2025) [83] 将基于 KST 的网络应用于流体力学中的湍流建模。他们展示了 KAN 如何提高 Navier-Stokes 湍流模型的预测精度。他们表明，与经典湍流模型相比，计算复杂度有所降低。他们还开发了一个利用 KST 的数据驱动湍流建模框架。他们推进了计算流体力学（CFD）中的机器学习应用。Lorencin, I. et al. (2024) [84] 使用受 KST 启发的神经网络预测船舶推进系统参数。他们实现了 KAN 来建模混合船舶推进（柴油-电动和气体联合 - CODLAG），并展示了一个高精度的推进效率预测模型。他们还为船舶推进研究提供了一个新的基准数据集。他们将 KST 应用扩展到海军工程和自主系统。

| 论文 | 主要贡献 | 影响 |
| :--- | :--- | :--- |
| Kolmogorov (1957) | 原始 KST 定理 | 为函数分解奠定了基础 |
| Arnold (1963) | 使用两变量函数的改进 | 使 KST 更适合计算 |
| Lorentz (2008) | 逼近理论中的 KST | 将 KST 与函数逼近误差联系起来 |
| Pinkus (1999) | 神经网络中的 KST | 深度学习的理论基础 |
| Perdikaris (2024) | 深度学习重新诠释 | 提出了柯尔莫哥罗夫-阿诺德网络 |
| Alhafiz (2025) | 基于 KST 的湍流建模 | 改进了 CFD 模拟 |
| Lorencin (2024) | 海军推进中的 KST | 优化了船舶能源效率 |

在神经网络的背景下，这一结果确立了函数逼近的理论普遍性。单隐藏层神经网络通过将函数 \(f(x_1, x_2, \dots, x_n)\) 表示为以下形式来对其进行逼近：

\(f(x_1, x_2, \dots, x_n) \approx \sum_{i=1}^{W} a_i \sigma \left( \sum_{j=1}^{n} w_{ij} x_j + b_i \right), \tag{77}\)

其中 \(W\) 是隐藏层的宽度，\(\sigma\) 是非线性激活函数，\(w_{ij}\) 是权重，\(b_i\) 是偏置，\(a_i\) 是输出权重。这种浅层网络的表达能力在很大程度上取决于宽度 \(W\)，因为通用逼近定理保证 \(W \to \infty\) 足以任意精确地逼近任何连续函数。然而，对于固定的逼近误差 \(\epsilon > 0\)，所需宽度随输入维度 \(n\) 呈指数增长，满足以下下界：

\(W \ge C \cdot \epsilon^{-n}, \tag{78}\)

其中 \(C\) 取决于函数的 Lipschitz 常数。这种指数依赖性，有时被称为“维度灾难”，凸显了浅层架构在捕捉高维依赖关系时的低效性。




深度的优势在我们考虑使用分层表示的深度神经网络时变得明显。一个具有 \( D \) 层、每层宽度为 \( W \) 的深度网络将函数构建为逐层变换的组合：

```
\( h^{(k)} = \sigma \left( W^{(k)} h^{(k-1)} + b^{(k)} \right), \quad h^{(0)} = x, \quad (79) \)
```

其中 \( h^{(k)} \) 表示第 \( k \) 层的输出，\( W^{(k)} \) 是权重矩阵，\( b^{(k)} \) 是偏置向量，\( \sigma \) 是非线性激活函数。网络的最终输出则由以下公式给出：

```
\( f(x) \approx h^{(D)} = \sigma \left( W^{(D)} h^{(D-1)} + b^{(D)} \right). \quad (80) \)
```

网络的深度 \( D \) 使其能够近似函数的分层组合。例如，如果目标函数 \( f(x) \) 具有组合结构

```
\( f(x) = g_1 \circ g_2 \circ \cdots \circ g_D(x), \quad (81) \)
```

其中每个 \( g_i \) 都是一个简单函数，深度 \( D \) 直接对应嵌套变换的数量。这种分层组合结构使深度网络能够高效地近似函数，从而减少所需的参数数量。深度网络的近似误差 \( \epsilon \) 与 \( D \) 呈多项式下降，满足

```
\( \epsilon \le O \left( \frac{1}{D^2} \right), \quad (82) \)
```

这比浅层网络的误差缩放高效得多。根据柯尔莫戈罗夫-阿诺尔德定理，分解

```
\( f(x_1, x_2, \dots, x_n) = \sum_{q=0}^{2n} \Phi_q \left( \sum_{p=1}^n \psi_{pq}(x_p) \right) \quad (83) \)
```

这展示了深度网络如何与多元函数的结构自然对齐。内部函数 \( \psi_{pq} \) 捕获局部依赖，而外部函数 \( \Phi_q \) 将这些汇总为全局表示。这种分层分解反映了神经网络的基于深度的结构，其中每一层学习函数复杂性的特定方面。最后，具有 \( D \) 层、每层宽度为 \( W \) 的深度网络中的参数数量由以下公式给出：

```
\( P \le O(D \cdot W^2), \quad (84) \)
```

而浅层网络需要

```
\( P \ge O(W^n) \quad (85) \)
```

参数以实现相同的近似精度。参数数量中的这种指数差异说明了深度架构的卓越效率，特别是对于高维函数。通过利用柯尔莫戈罗夫-阿诺尔德定理固有的分层分解，深度网络获得的表达能力会随着维度和复杂度的增加而有利地扩展。

### 2.2.2 表达能力的傅里叶分析

文献综述：Juárez-Osorio 等人 (2024) [215] 应用傅里叶分析来设计用于时间序列预测的量子卷积神经网络（QCNNs）。傅里叶级数分解有助于分析和优化量子架构的表达能力，使 QCNNs 更擅长捕获数据中的周期性和非周期性结构。Umeano 和 Kyriienko (2024) [216] 引入了基于傅里叶的量子特征映射，将经典数据转换为具有增强表达能力的量子态。傅里叶变换在高效映射高维数据的同时发挥着保持可解释性的核心作用。Liu 等人 (2024) [217] 通过整合傅里叶分析和谱小波扩展了图卷积网络（GCNs），以提高图的表达能力。它弥合了频域分析与图嵌入之间的差距，使 GCNs 对复杂数据结构更有效。Vlasic (2024) [218] 提出了一种受傅里叶级数启发的特征映射技术，用于将经典数据编码到量子电路中。它展示了傅里叶系数如何增强量子模型的表示能力，从而带来更好的压缩和泛化性能。Kim 等人 (2024) [219] 引入了神经傅里叶建模（NFM），这是一种在保持表达能力的同时紧凑地表示时间序列数据的新方法。它在保留长期依赖性方面优于短时傅里叶变换（STFT）等传统模型。Xie 等人 (2024) [220] 探讨了如何利用傅里叶基函数来增强张量网络的表达能力，同时保持计算效率。它建立了机器学习架构中表达能力与模型复杂度之间的权衡。Liu 等人 (2024) [221] 将谱调制和傅里叶变换整合到文本到图像合成的隐式神经表示中。傅里叶分析在保持生成模型局部表达能力的同时提高了全局连贯性。Zhang (2024) [222] 展示了傅里叶和锁相放大谱技术如何表示机械信号中的长期变化。基于傅里叶的分解允许对机械故障和退化进行更具表达性的表示。Hamed 和 Lachiri (2024) [223] 将傅里叶变换应用于语音合成模型，提高了从文本到语音传递表达性内容的能力。傅里叶级数能够有效捕获韵律、节奏和音调变化。Lehmann 等人 (2024) [224] 将基于傅里叶的深度学习模型整合到地震活动预测中。它探索了傅里叶神经算子（FNOs）在捕捉不同地质环境中波传播方面的表达能力。

神经网络中表达能力的傅里叶分析旨在严谨地量化神经架构（由其深度和宽度表征）如何通过将函数分解为其傅里叶谱来近似函数。考虑一个可平方积分函数 \( f : \mathbb{R}^d \rightarrow \mathbb{R} \)，其傅里叶变换定义为

```
\hat{f}(\xi) = \int_{\mathbb{R}^d} f(\mathbf{x})e^{-i2\pi\xi\cdot\mathbf{x}} d\mathbf{x}
```

其中 \( \xi \in \mathbb{R}^d \) 表示频率。逆傅里叶变换按如下方式重构函数：

```
f(\mathbf{x}) = \int_{\mathbb{R}^d} \hat{f}(\xi)e^{i2\pi\xi\cdot\mathbf{x}} d\xi
```

幅值 \( |\hat{f}(\xi)| \) 反映了频率 \( \xi \) 对 \( f \) 的能量贡献。神经网络通过捕获 \( f \) 的傅里叶谱来近似 \( f \)，但架构从根本上决定了这种近似可以多有效地实现，尤其是在存在高频分量的情况下。

对于具有一个隐藏层和有限数量神经元的浅层网络，通用近似定理确立了：

```
f(\mathbf{x}) \approx \sum_{i=1}^n a_i\phi(\mathbf{w}_i \cdot \mathbf{x} + b_i)
```

其中 \( \phi \) 是激活函数，\( \mathbf{w}_i \in \mathbb{R}^d \) 是权重，\( b_i \in \mathbb{R} \) 是偏置，\( a_i \in \mathbb{R} \) 是系数。该表示的傅里叶变换可表示为

```
\hat{f}(\xi) \approx \sum_{i=1}^n a_i\hat{\phi}(\xi)e^{-i2\pi\xi\cdot\mathbf{b}_i}
```

其中 \(\hat{\phi}(\xi)\) 表示激活函数的傅里叶变换。对于 sigmoid 或 tanh 等平滑激活函数，当 \(\|\xi\| \to \infty\) 时，\(\hat{\phi}(\xi)\) 指数衰减，这限制了网络近似具有高频内容的函数的能力，除非宽度 \(n\) 极大。具体来说，傅里叶系数的衰减为

\(|\hat{f}(\xi)| \sim e^{-\beta \|\xi\|}\)

其中 \(\beta > 0\) 取决于 \(\phi\) 的平滑度。这种限制意味着，除非浅层网络的宽度随输入维度 \(d\) 指数增长，否则它们倾向于近似低频函数。另一方面，深度网络利用其分层结构来克服这些限制。具有 \(L\) 层的深度网络递归地组合函数，产生以下形式的输出

\(f(\mathbf{x}) = \phi_L(\mathbf{W}^{(L)}\phi_{L-1}(\mathbf{W}^{(L-1)} \cdots \phi_1(\mathbf{W}^{(1)}\mathbf{x} + \mathbf{b}^{(1)}) \cdots ) + \mathbf{b}^{(L)})\)

其中 \(\phi_l\) 是第 \(l\) 层的激活函数，\(\mathbf{W}^{(l)}\) 是权重矩阵，\(\mathbf{b}^{(l)}\) 是偏置向量。可以迭代地分析这种组合的傅里叶变换。如果 \(\mathbf{h}^{(l)} = \phi_l(\mathbf{W}^{(l)}\mathbf{h}^{(l-1)} + \mathbf{b}^{(l)})\) 表示第 \(l\) 层的输出，则

\(\widehat{\mathbf{h}^{(l)}}(\xi) = \hat{\phi}_l(\xi) * \widehat{\mathbf{W}^{(l)}\mathbf{h}^{(l-1)}}(\xi)\)

其中 \(*\) 表示卷积，\(\hat{\phi}_l\) 是激活函数的傅里叶变换。这种卷积的递归应用放大了高频分量，使深度网络能够近似其傅里叶谱呈多项式衰减的函数。具体来说，深度网络的傅里叶系数衰减为

\(|\hat{f}(\xi)| \sim \|\xi\|^{-\alpha L}\)

其中 \(\alpha\) 取决于激活函数。这与浅层网络中观察到的指数衰减形成鲜明对比。

激活函数在塑造神经网络的傅里叶谱方面起着关键作用。例如，整流线性单元（ReLU）\(\phi(x) = \max(0, x)\) 将显著的高频分量引入网络。ReLU 激活函数的傅里叶变换由以下公式给出：

\(\hat{\phi}(\xi) = \frac{1}{2\pi i \xi}\)

它比平滑激活函数的傅里叶变换衰减得更慢。因此，基于 ReLU 的网络在近似具有振荡行为的函数方面特别有效。为了说明，请考虑函数

\(f(\mathbf{x}) = \sin(2\pi \boldsymbol{\xi} \cdot \mathbf{x})\)

当 \(\|\boldsymbol{\xi}\|\) 较大时，浅层网络需要指数级数量的神经元来近似 \(f\)，但深度网络可以通过利用其分层结构，使用多项式更少的参数实现相同的近似。深度网络的表达能力可以通过其近似带限函数的能力进一步量化，即傅里叶谱支持在 \(\|\boldsymbol{\xi}\| \le \omega_{\max}\) 上的函数 \(f\)。对于宽度为 \(n\) 的浅层网络，所需的神经元数量按以下方式缩放：

\(n \sim (\omega_{\max})^d\)

其中 \(d\) 是输入维度。相比之下，对于深度为 \(L\) 的深度网络，宽度按以下方式缩放：

\(n \sim (\omega_{\max})^{d/L}\)

这反映了深度在将频率分量近似分布到各层时的指数级效率。例如，如果 \(f(\mathbf{x}) = \cos(2\pi \boldsymbol{\xi} \cdot \mathbf{x})\) 且 \(\|\boldsymbol{\xi}\| = \omega_{\max}\)，深度网络需要


significantly fewer parameters than a shallow network to approximate \( f \) to the same accuracy.

In summary, the Fourier analysis of expressivity rigorously demonstrates the superiority of deep networks over shallow ones in approximating complex functions. Depth introduces a hierarchical compositional structure that enables the efficient representation of high-frequency components, while width provides a rich basis for approximating the function's Fourier spectrum. Together, these properties explain the remarkable capacity of deep neural networks to approximate functions with intricate spectral structures, offering a mathematically rigorous foundation for understanding their expressivity.

# 3 训练动态与 NTK 线性化

Literature Review: Trevisan et al. [85] investigated how knowledge distillation can be analyzed using the Neural Tangent Kernel (NTK) framework and demonstrated that under certain conditions, the training dynamics of a student model in knowledge distillation closely follow NTK linearization. They explored how NTK affects generalization and feature transfer in the distillation process. They provided theoretical insight into why knowledge distillation improves performance in deep networks. Bonfanti et al. (2024) [86] studied how NTK behaves in the nonlinear regime, particularly in Physics-Informed Neural Networks (PINNs). They showed that when PINNs operate outside the NTK regime, their performance degrades due to high sensitivity to initialization and weight updates. They established conditions under which NTK linearization is insufficient for PINNs, emphasizing the need for nonlinear adaptations. They provided practical guidelines for designing PINNs that maintain stable training dynamics. Jacot et al. (2018) [87] introduced the Neural Tangent Kernel (NTK) as a fundamental framework for analyzing infinite-width neural networks. They proved that as width approaches infinity, neural networks evolve as linear models governed by the NTK. They derived generalization bounds for infinitely wide networks and connected training dynamics to kernel methods. They established NTK as a core tool in deep learning theory, leading to further developments in training dynamics research. Lee et al. (2019) [88] extended NTK theory to arbitrarily deep networks, showing that even deep architectures behave as linear models under gradient descent and proved that training dynamics remain stable regardless of network depth when width is sufficiently large. They explored practical implications for initializing and optimizing deep networks. They strengthened NTK theory by confirming its validity beyond shallow networks. Yang and Hu (2022) [89] challenged the conventional NTK assumption that feature learning is negligible in infinite-width networks and showed that certain activation functions can induce nontrivial feature learning even in infinite-width regimes. They suggested that feature learning can be integrated into NTK theory, opening new directions in kernel-based deep learning research. Xiang et al. (2023) [90] investigated how finite-width effects impact training dynamics under NTK assumptions and showed that finite-width networks deviate from NTK predictions due to higher-order corrections in weight updates. They derived corrections to NTK theory for practical networks, improving its predictive power for real-world architectures. They refined NTK approximations, making them more applicable to modern deep-learning models. Lee et al. (2019) [91] extended NTK linearization to deep convolutional networks, analyzing their training dynamics under infinite width and showed how locality and weight sharing in CNNs impact NTK behavior. They also demonstrated practical consequences for CNN training in real-world applications. They bridged NTK theory and convolutional architectures, providing new theoretical tools for CNN analysis.

## 3.1 梯度流与稳定点

The dynamics of gradient flow in neural network training are fundamentally governed by the continuous evolution of parameters \(\theta(t)\) under the influence of the negative gradient of the loss function, expressed as

\[\frac{d\theta(t)}{dt} = -\nabla_\theta \mathcal{L}(\theta(t)).\] (98).

The loss function, typically of the form

\[\mathcal{L}(\theta) = \frac{1}{2n} \sum_{i=1}^n \|f(x_i; \theta) - y_i\|^2,\] (99)

measures the discrepancy between the network's predicted outputs $f(x_i; \theta)$ and the true labels $y_i$. At stationary points of the flow, the condition

\[\nabla_\theta \mathcal{L}(\theta^*) = 0.\] (100)

holds, indicating that the gradient vanishes. To classify these stationary points, the Hessian matrix \(H = \nabla_\theta^2 \mathcal{L}(\theta)\) is examined. For eigenvalues \(\{\lambda_i\}\) of \(H\), the nature of the stationary point is determined: \(\lambda_i > 0\) for all \(i\) corresponds to a local minimum, \(\lambda_i < 0\) for all \(i\) to a local maximum, and mixed signs indicate a saddle point. Under gradient flow \(\frac{d\theta(t)}{dt} = -\nabla_\theta \mathcal{L}(\theta(t))\), the trajectory converges to critical points:

\[\lim_{t \to \infty} \|\nabla_\theta \mathcal{L}(\theta(t))\| = 0.\] (101)

The gradient flow also governs the temporal evolution of the network's predictions \(f(x; \theta(t))\). A Taylor series expansion of \(f(x; \theta)\) about an initial parameter \(\theta_0\) gives:

\[f(x; \theta) = f(x; \theta_0) + J_f(x; \theta_0)(\theta - \theta_0) + \frac{1}{2}(\theta - \theta_0)^\top H_f(x; \theta_0)(\theta - \theta_0) + \mathcal{O}(\|\theta - \theta_0\|^3),\] (102)

where \(J_f(x; \theta_0) = \nabla_\theta f(x; \theta_0)\) is the Jacobian and \(H_f(x; \theta_0)\) is the Hessian of \(f(x; \theta)\) with respect to \(\theta\). In the NTK (neural tangent kernel) regime, higher-order terms are negligible due to the large parameterization of the network, and the linear approximation suffices:

\[f(x; \theta) \approx f(x; \theta_0) + J_f(x; \theta_0)(\theta - \theta_0).\] (103)

Under gradient flow, the time derivative of the network's predictions is given by:

\[\frac{df(x; \theta(t))}{dt} = J_f(x; \theta(t)) \frac{d\theta(t)}{dt}.\] (104)

Substituting the parameter dynamics \(\frac{d\theta(t)}{dt} = -\nabla_\theta \mathcal{L}(\theta(t)) = -\sum_{i=1}^n (f(x_i; \theta(t)) - y_i) J_f(x_i; \theta(t))\), this becomes:

\[\frac{df(x; \theta(t))}{dt} = -\sum_{i=1}^n J_f(x; \theta(t)) J_f(x_i; \theta(t))^\top (f(x_i; \theta(t)) - y_i).\] (105)

Defining the NTK as \(\mathcal{K}(x, x'; \theta) = J_f(x; \theta) J_f(x'; \theta)^\top\), and assuming constancy of the NTK during training (\(\mathcal{K}(x, x'; \theta) \approx \mathcal{K}_0(x, x')\)), the evolution equation simplifies to:

\[\frac{df(x; \theta(t))}{dt} = -\sum_{i=1}^n \mathcal{K}_0(x, x_i) (f(x_i; \theta(t)) - y_i).\] (106)

Rewriting in matrix form, let \(\mathbf{f}(t) = [f(x_1; \theta(t)), \dots, f(x_n; \theta(t))]^\top\) and \(\mathbf{y} = [y_1, \dots, y_n]^\top\). The NTK matrix \(\mathcal{K}_0 \in \mathbb{R}^{n \times n}\) evaluated at initialization defines the system:

\[\frac{d\mathbf{f}(t)}{dt} = -\mathcal{K}_0 (\mathbf{f}(t) - \mathbf{y}).\] (107)

The solution to this linear system is:

\[\mathbf{f}(t) = e^{-\mathcal{K}_0 t} \mathbf{f}(0) + (\mathbf{I} - e^{-\mathcal{K}_0 t}) \mathbf{y}.\] (108)

As \( t \to \infty \), the predictions converge to the labels: \(\mathbf{f}(t) \to \mathbf{y}\), implying zero training error. The eigenvalues of \(\mathcal{K}_0\) determine the rates of convergence. Diagonalizing \(\mathcal{K}_0\) as \(\mathcal{K}_0 = Q\Lambda Q^\top\), where \(Q\) is orthogonal and \(\Lambda = \text{diag}(\lambda_1, \dots, \lambda_n)\), the dynamics in the eigenbasis are:

\[\frac{d\tilde{\mathbf{f}}(t)}{dt} = -\Lambda(\tilde{\mathbf{f}}(t) - \tilde{\mathbf{y}}), \quad (109),\]

with \(\tilde{\mathbf{f}}(t) = Q^\top \mathbf{f}(t)\) and \(\tilde{\mathbf{y}} = Q^\top \mathbf{y}\). Solving, we obtain:

\[\tilde{\mathbf{f}}(t) = e^{-\Lambda t}\tilde{\mathbf{f}}(0) + (\mathbf{I} - e^{-\Lambda t})\tilde{\mathbf{y}}. \quad (110)\]

Each mode decays exponentially with a rate proportional to the eigenvalue \(\lambda_i\). Modes with larger \(\lambda_i\) converge faster, while smaller eigenvalues slow convergence.

The NTK framework thus rigorously explains the linearization of training dynamics in overparameterized neural networks. This linear behavior ensures that the optimization trajectory remains within a convex region of the parameter space, leading to both convergence and generalization. By leveraging the constancy of the NTK, the complexity of nonlinear neural networks is reduced to an analytically tractable framework that aligns closely with empirical observations.

### 3.1.1 海森矩阵结构

The Hessian matrix, \(H(\theta) = \nabla_\theta^2 \mathcal{L}(\theta)\), serves as a critical construct in the mathematical framework of optimization, capturing the second-order partial derivatives of the loss function \(\mathcal{L}(\theta)\) with respect to the parameter vector \(\theta \in \mathbb{R}^d\). Each element \(H_{ij} = \frac{\partial^2 \mathcal{L}(\theta)}{\partial \theta_i \partial \theta_j}\) reflects the curvature of the loss surface along the \((i, j)\)-direction. The symmetry of \(H(\theta)\), guaranteed by the Schwarz theorem under the assumption of continuous second partial derivatives, implies \(H_{ij} = H_{ji}\). This property ensures that the eigenvalues \(\lambda_1, \lambda_2, \dots, \lambda_d\) of \(H(\theta)\) are real and the eigenvectors \(\mathbf{v}_1, \mathbf{v}_2, \dots, \mathbf{v}_d\) are orthogonal, satisfying the eigenvalue equation

\(H(\theta)\mathbf{v}_i = \lambda_i \mathbf{v}_i \quad \text{for all } i. \quad (111)\)

The behavior of the loss function around a specific parameter value \(\theta_0\) can be rigorously analyzed using a second-order Taylor expansion. This expansion is given by:

\(\mathcal{L}(\theta) = \mathcal{L}(\theta_0) + (\theta - \theta_0)^\top \nabla_\theta \mathcal{L}(\theta_0) + \frac{1}{2}(\theta - \theta_0)^\top H(\theta_0)(\theta - \theta_0) + \mathcal{O}(\|\theta - \theta_0\|^3). \quad (112)\)

Here, the term \((\theta - \theta_0)^\top \nabla_\theta \mathcal{L}(\theta_0)\) represents the linear variation of the loss, while the quadratic term \(\frac{1}{2}(\theta - \theta_0)^\top H(\theta_0)(\theta - \theta_0)\) describes the curvature effects. The eigenvalues of \(H(\theta_0)\) dictate the nature of the critical point \(\theta_0\). Specifically, if all \(\lambda_i > 0\), \(\theta_0\) is a local minimum; if all \(\lambda_i < 0\), it is a local maximum; and if the eigenvalues have mixed signs, \(\theta_0\) is a saddle point. The leading-order approximation to the change in the loss function, \(\Delta \mathcal{L} \approx \frac{1}{2} \delta \theta^\top H(\theta_0) \delta \theta\), highlights the dependence on the eigenstructure of \(H(\theta_0)\). In the context of gradient descent, parameter updates follow the iterative scheme:

\(\theta^{(t+1)} = \theta^{(t)} - \eta \nabla_\theta \mathcal{L}(\theta^{(t)}), \quad (113)\)

where \(\eta\) is the learning rate. Substituting the Taylor expansion of \(\nabla_\theta \mathcal{L}(\theta^{(t)})\) around \(\theta_0\) gives:

\(\theta^{(t+1)} = \theta^{(t)} - \eta \left[ \nabla_\theta \mathcal{L}(\theta_0) + H(\theta_0)(\theta^{(t)} - \theta_0) \right]. \quad (114)\)

To analyze this update rigorously, we project \(\theta^{(t)} - \theta_0\) onto the eigenbasis of \(H(\theta_0)\), expressing it as:

\(\theta^{(t)} - \theta_0 = \sum_{i=1}^d c_i^{(t)} \mathbf{v}_i, \quad (115)\)


其中 $c_i^{(t)} = \mathbf{v}_i^\top (\theta^{(t)} - \theta_0)$. 将此展开式代入梯度下降更新规则，得到：

\( c_i^{(t+1)} = c_i^{(t)} - \eta \left[ \mathbf{v}_i^\top \nabla_\theta \mathcal{L}(\theta_0) + \lambda_i c_i^{(t)} \right] . \quad (116) \)

该迭代方案的收敛性由条件 \(|1 - \eta \lambda_i| < 1\) 决定，该条件相对于 \(H(\theta_0)\) 的频谱约束了学习率 \(\eta\)。对于幅值较大的特征值 \(\lambda_i\)，过大的学习率 \(\eta\) 可能导致振荡或发散更新。

在神经切线核（NTK）范式中，神经网络在训练过程中的演化可以通过对网络输出在初始化点附近进行线性化来近似。令 \(f_\theta(x)\) 表示输入 \(x\) 对应的网络输出。将 \(f_\theta(x)\) 在 \(\theta_0\) 附近线性化得到：

\( f_\theta(x) \approx f_{\theta_0}(x) + \nabla_\theta f_{\theta_0}(x)^\top (\theta - \theta_0) . \quad (117) \)

NTK 定义为：

\( K(x, x') = \nabla_\theta f_{\theta_0}(x)^\top \nabla_\theta f_{\theta_0}(x') , \quad (118) \)

对于足够宽的网络，NTK 在训练过程中保持近似不变。参数的训练动力学由以下式描述：

\( \frac{d\theta}{dt} = -\nabla_\theta \mathcal{L}(\theta) , \quad (119) \)

在 NTK 近似下，上式变为：

\( \frac{d\theta}{dt} = -K \nabla_\theta \mathcal{L}(\theta) , \quad (120) \)

其中 \(K\) 为在初始化点评估得到的 NTK 矩阵。损失函数的演化由 \(K\) 的特征值决定，这些特征值控制不同方向上的收敛速率。

海森矩阵（Hessian）的谱特性在神经网络的泛化性能中起着关键作用。实证研究表明，\(H(\theta)\) 的特征值谱通常表现出“块体-尖峰”结构，即靠近零的密集特征值块体和少数几个较大的离群值。块体对应于损失景观中的平坦方向，有助于模型的鲁棒性和泛化性能，而尖峰则代表与过拟合相关的尖锐方向。这种谱结构可以使用随机矩阵理论进行分析，其中特征值密度 \(\rho(\lambda)\) 由诸如 Marchenko-Pastur 分布等分布建模：

\( \rho(\lambda) = \frac{1}{2\pi\lambda q} \sqrt{(\lambda_+ - \lambda)(\lambda - \lambda_-)} , \quad (121) \)

其中 \(\lambda_\pm = (1 \pm \sqrt{q})^2\) 为谱界，\(q = \frac{d}{n}\) 是参数数量与数据点数量之比。这一严谨分析将海森矩阵结构与神经网络的优化动力学和泛化性能联系起来，为训练过程提供了全面的数学理解。海森矩阵 \(H(\theta)\) 满足：

\( H(\theta) = \nabla_\theta^2 \mathcal{L}(\theta) = \mathbb{E}_{(x,y)} \left[ \nabla_\theta f_\theta(x) \nabla_\theta f_\theta(x)^\top \right] . \quad (122) \)

对于超参数化网络，\(H(\theta)\) 几乎退化，意味着存在平坦极小值。

### 3.1.2 NTK 线性化

梯度流下的神经网络动力学可以从网络的参数化表示 \(f_\theta(x)\) 着手进行全面描述，其中 \(\theta \in \mathbb{R}^p\) 表示可训练参数集合，\(x \in \mathbb{R}^d\) 是输入，\(f_\theta(x) \in \mathbb{R}^m\) 表示输出。训练目标是在数据集 $\{(x_i, y_i)\}_{i=1}^n$ 上最小化损失函数 $\mathcal{L}(\theta)$，其中 \(x_i \in \mathbb{R}^d\) 和 \(y_i \in \mathbb{R}^m\) 表示输入-目标对。训练过程中参数的演化由梯度流方程 \(\frac{d\theta}{dt} = -\nabla_\theta \mathcal{L}(\theta)\) 控制，其中 \(\nabla_\theta \mathcal{L}(\theta)\) 是损失函数对参数的梯度。为了分析网络输出的动力学，我们首先考虑 \(f_\theta(x)\) 的时间导数。利用链式法则，这表示为：

\(\frac{\partial f_\theta(x)}{\partial t} = \nabla_\theta f_\theta(x)^\top \frac{d\theta}{dt}.\) \tag{123}

代入 \(\frac{d\theta}{dt} = -\nabla_\theta \mathcal{L}(\theta)\)，得：

\(\frac{\partial f_\theta(x)}{\partial t} = -\nabla_\theta f_\theta(x)^\top \nabla_\theta \mathcal{L}(\theta).\) \tag{124}

损失函数 \(\mathcal{L}(\theta)\) 的梯度可以用训练数据显式表示。对于数据集上的通用损失函数，其形式为：

\(\mathcal{L}(\theta) = \frac{1}{n} \sum_{i=1}^n \ell(f_\theta(x_i), y_i),\) \tag{125}

其中 \(\ell(f_\theta(x_i), y_i)\) 表示第 \(i\) 个数据点的损失。因此，损失对参数的梯度由以下式给出：

\(\nabla_\theta \mathcal{L}(\theta) = \frac{1}{n} \sum_{i=1}^n \nabla_\theta f_\theta(x_i) \nabla_{f_\theta(x_i)} \ell(f_\theta(x_i), y_i).\) \tag{126}

将此代入 \(f_\theta(x)\) 的时间导数中，得到：

\(\frac{\partial f_\theta(x)}{\partial t} = -\frac{1}{n} \sum_{i=1}^n \nabla_\theta f_\theta(x)^\top \nabla_\theta f_\theta(x_i) \nabla_{f_\theta(x_i)} \ell(f_\theta(x_i), y_i).\) \tag{127}

为了引入神经切线核（NTK），我们将其定义为网络输出对参数的雅可比矩阵的格拉姆矩阵：

\(\Theta(x, x'; \theta) = \nabla_\theta f_\theta(x)^\top \nabla_\theta f_\theta(x').\) \tag{128}

使用此定义，输出的时间演化变为：

\(\frac{\partial f_\theta(x)}{\partial t} = -\frac{1}{n} \sum_{i=1}^n \Theta(x, x_i; \theta) \nabla_{f_\theta(x_i)} \ell(f_\theta(x_i), y_i).\) \tag{129}

在超参数化范式中，当参数数量 \(p\) 显著大于训练数据点数量 \(n\) 时，实证和理论观察表明 NTK \(\Theta(x, x'; \theta)\) 在训练过程中保持近似不变。具体来说，\(\Theta(x, x'; \theta) \approx \Theta(x, x'; \theta_0)\)，其中 \(\theta_0\) 表示初始化时的参数。这种恒定性大大简化了网络训练动力学的分析。为了说明这一点，考虑控制输出动力学的微分方程的解。令 \(F(t) \in \mathbb{R}^{n \times m}\) 表示所有训练输入的网络输出矩阵，其中第 \(i\) 行对应于 \(f_\theta(x_i)\)。动力学可以用矩阵形式表示为：

\(\frac{\partial F(t)}{\partial t} = -\frac{1}{n} \Theta(\theta_0) \nabla_F \mathcal{L}(F),\) \tag{130}

其中 \(\Theta(\theta_0) \in \mathbb{R}^{n \times n}\) 为在初始化点评估得到的 NTK 矩阵，\(\nabla_F \mathcal{L}(F)\) 是损失对输出矩阵 \(F\) 的梯度。对于均方误差损失的特殊情况，\(\mathcal{L}(F) = \frac{1}{2n} \|F - Y\|_F^2\)，其中 \(Y \in \mathbb{R}^{n \times m}\) 是目标输出矩阵，梯度简化为：

\(\nabla_F \mathcal{L}(F) = \frac{1}{n} (F - Y).\) \tag{131}

将此代入动力学中，得到：

$$\frac{\partial F(t)}{\partial t} = -\frac{1}{n^2}\Theta(\theta_0)(F(t) - Y).$$ (132)

该微分方程的解为：

$$F(t) = Y + e^{-\frac{\Theta(\theta_0)}{n^2}t}(F(0) - Y),$$ (133)

其中 \(F(0)\) 表示网络的初始输出。当 \(t \to \infty\) 时，指数项消失，网络输出收敛到目标 \(Y\)，前提是 \(\Theta(\theta_0)\) 为正定矩阵。收敛速率由 \(\Theta(\theta_0)\) 的特征值决定，较小的特征值对应于沿相关特征向量方向较慢的收敛。为了理解该系统的驻点，我们注意到当 \(\frac{\partial F(t)}{\partial t} = 0\) 时会出现驻点。根据动力学，这意味着：

$$\Theta(\theta_0)(F - Y) = 0.$$ (134)

如果 \(\Theta(\theta_0)\) 可逆，则得到 \(F = Y\)，表明网络在驻点处精确插值训练数据。然而，如果 \(\Theta(\theta_0)\) 不是满秩的，则驻点构成满足 \((I - \Pi)(F - Y) = 0\) 的解子空间，其中 \(\Pi\) 是投影到 \(\Theta(\theta_0)\) 的列空间上的投影算子。

NTK 框架为分析训练动力学提供了严谨的数学视角，阐明了神经网络中参数演化、核属性和损失收敛之间的相互作用。通过 NTK 对训练动力学进行线性化，我们深入了解了超参数化网络在梯度流下的演化方式及其如何达到驻点，揭示了其以非凡精度插值数据的能力。

## 3.2 NTK 范式

神经切线核（NTK）范式是理解高度超参数化神经网络中梯度下降动力学的基础框架。考虑由 \(\boldsymbol{\theta} \in \mathbb{R}^P\) 参数化的神经网络 \(f(\mathbf{x}; \boldsymbol{\theta})\)，其中 \(P\) 表示参数总数，\(\mathbf{x} \in \mathbb{R}^d\) 是输入向量。对于训练数据集 \(\{(\mathbf{x}_i, y_i)\}_{i=1}^N\)，时间 \(t\) 时的损失函数 \(L(t)\) 由以下式给出：

$$L(t) = \frac{1}{2N} \sum_{i=1}^N (f(\mathbf{x}_i; \boldsymbol{\theta}(t)) - y_i)^2.$$ (135)

参数根据梯度下降演化为 \(\boldsymbol{\theta}(t + 1) = \boldsymbol{\theta}(t) - \eta \nabla_{\boldsymbol{\theta}} L(t)\)，其中 \(\eta > 0\) 是学习率。在 NTK 范式中，我们考虑网络输出在初始化点 \(\boldsymbol{\theta}_0\) 附近的一阶泰勒展开：

$$f(\mathbf{x}; \boldsymbol{\theta}) \approx f(\mathbf{x}; \boldsymbol{\theta}_0) + \nabla_{\boldsymbol{\theta}} f(\mathbf{x}; \boldsymbol{\theta}_0)^\top (\boldsymbol{\theta} - \boldsymbol{\theta}_0).$$ (136)

该线性近似将 \(f\) 的非线性动力学转化为更简单的线性化形式。为了分析训练，我们引入雅可比矩阵 \(J \in \mathbb{R}^{N \times P}\)，其中 \(J_{ij} = \frac{\partial f(\mathbf{x}_i; \boldsymbol{\theta}_0)}{\partial \theta_j}\)。数据集上聚合预测的输出向量 \(\mathbf{f}(t) \in \mathbb{R}^N\) 按以下方式演化：

$$\mathbf{f}(t) = \mathbf{f}(0) + J(\boldsymbol{\theta}(t) - \boldsymbol{\theta}_0).$$ (137)

NTK \(\Theta \in \mathbb{R}^{N \times N}\) 定义为

$$\Theta_{ij} = \nabla_{\boldsymbol{\theta}} f(\mathbf{x}_i; \boldsymbol{\theta}_0)^\top \nabla_{\boldsymbol{\theta}} f(\mathbf{x}_j; \boldsymbol{\theta}_0).$$ (138)





当 \( P \to \infty \) 时，NTK 收敛于一个确定性矩阵，在训练期间保持近乎不变。将 \( \mathbf{f}(t) \) 的线性形式代入梯度下降更新方程，得到

\[ \mathbf{f}(t+1) = \mathbf{f}(t) - \frac{\eta}{N} \Theta (\mathbf{f}(t) - \mathbf{y}), \]

其中 \( \mathbf{y} \in \mathbb{R}^N \) 是真实标签向量。定义残差 \( \mathbf{r}(t) = \mathbf{f}(t) - \mathbf{y} \)，训练动力学可归约为

\[ \mathbf{r}(t+1) = \left( I - \frac{\eta}{N} \Theta \right) \mathbf{r}(t). \]

特征值分解 \( \Theta = Q \Lambda Q^\top \)（其中 \( Q \) 为正交矩阵，\( \Lambda = \text{diag}(\lambda_1, \dots, \lambda_N) \) 为对角矩阵）使我们能够在 \( \Theta \) 的特征基下分析残差的衰减：

\[ \tilde{\mathbf{r}}(t+1) = \left( I - \frac{\eta}{N} \Lambda \right) \tilde{\mathbf{r}}(t), \]

其中 \( \tilde{\mathbf{r}}(t) = Q^\top \mathbf{r}(t) \)。每个分量按如下方式衰减

\[ \tilde{r}_i(t) = \left( 1 - \frac{\eta \lambda_i}{N} \right)^t \tilde{r}_i(0). \]

当 \( \eta \) 较小时，训练动力学近似为连续过程，受以下方程支配

\[ \frac{d\mathbf{r}(t)}{dt} = -\frac{1}{N} \Theta \mathbf{r}(t), \]

其解为

\[ \mathbf{r}(t) = \exp \left( - \frac{\Theta t}{N} \right) \mathbf{r}(0). \]

针对特定架构（例如全连接 ReLU 网络）的 NTK 可利用逐层协方差矩阵推导。设 \( \Sigma^{(l)}(\mathbf{x}, \mathbf{x}') \) 表示第 \( l \) 层预激活之间的协方差。\( \Sigma^{(l)} \) 的递推关系为

\[ \Sigma^{(l)}(\mathbf{x}, \mathbf{x}') = \frac{1}{2\pi} \| \mathbf{z}^{(l-1)}(\mathbf{x}) \| \| \mathbf{z}^{(l-1)}(\mathbf{x}') \| (\sin \theta + (\pi - \theta) \cos \theta), \]

其中 \( \theta = \cos^{-1} \left( \frac{\Sigma^{(l-1)}(\mathbf{x}, \mathbf{x}')}{\sqrt{\Sigma^{(l-1)}(\mathbf{x}, \mathbf{x}) \Sigma^{(l-1)}(\mathbf{x}', \mathbf{x}')}} \right) \)。NTK 是所有层贡献的总和，量化了参数更新如何在网络中传播。

在无限宽度极限下，NTK 框架预测泛化特性，因为核矩阵 \( \Theta \) 既支配训练行为也支配测试时行为。NTK 将神经网络与经典核方法联系起来，在深度学习与近似理论中成熟的理论工具之间搭建了一座桥梁。该模式的确定性和可分析性使得对网络性能、收敛速度以及对初始化和学习率变化的鲁棒性能够进行精确刻画。

# 4 泛化界：PAC-Bayes 与谱分析

## 4.1 PAC-Bayes 形式主义

文献综述：McAllester (1999) [92] 提出了 PAC-Bayes 界，这是一项基本定理，为贝叶斯学习模型提供泛化保证。他建立了复杂度与经验风险之间的权衡，成为现代 PAC-Bayesian 分析的理论基础。Catoni (2007) [93] 在其著作中严格扩展了 PAC-Bayes 框架，将其与信息论和统计力学概念相联系，并引入了指数先验和 Gibbs 先验用于学习，改进了有监督分类的 PAC-Bayesian 界。Germain et al. (2009) [94] 将 PAC-Bayes 理论应用于线性分类器，包括 SVM 和逻辑回归。他们证明，PAC-Bayesian 泛化界优于经典 Vapnik-Chervonenkis (VC) 维界。Seeger (2002) [95] 将 PAC-Bayes 界扩展到高斯过程模型，为贝叶斯分类器证明了严格的泛化保证。他为概率核方法奠定了基础。Alquier et al. (2006) [96] 将变分推断与 PAC-Bayes 界联系起来，证明变分近似可以保留 PAC-Bayesian 界的泛化保证。Dziugaite and Roy (2017) [97] 首次将 PAC-Bayes 应用于深度学习。他们为随机神经网络推导了非平凡泛化界，连接了理论与实践。Rivasplata et al. (2020) [98] 提出了新的 PAC-Bayes 界，改进了现有保证，使 PAC-Bayesian 界对现代机器学习应用更加实用。Lever et al. (2013) [99] 探索了 PAC-Bayes 理论中的数据依赖先验，表明自适应先验可带来更紧的泛化界。Rivasplata et al. (2018) [100] 引入了实例依赖先验，改进了个性化学习，使 PAC-Bayesian 方法在现实世界机器学习问题中更加有用。Lindemann et al. (2024) [101] 将 PAC-Bayes 理论与符合预测相结合，以改进控制系统中的形式验证，展示了 PAC-Bayes 与安全关键型应用的相关性。

PAC-Bayes 形式主义是统计学习理论中的基础框架，旨在为学习算法的泛化性能提供概率保证。通过结合 PAC（Probably Approximately Correct，可能近似正确）框架与贝叶斯推理的原理，PAC-Bayes 提出的界限刻画了在有限数据样本下，从后验分布中抽取的假设的预期性能。本文对 PAC-Bayes 形式主义进行了极为严谨且数学精确的描述，强调其理论构造及其含义。

PAC-Bayes 形式主义的核心在于，基于假设 \( h \in \mathcal{H} \) 在有限数据集 \( S \sim \mathcal{D}^m \) 上的表达，严格量化其泛化能力的雄心，其中 \( \mathcal{D} \) 代表底层且通常未知的数据分布。PAC 框架最初旨在对真实风险提供高置信度保证

\[ R(h) = \mathbb{E}_{z \sim \mathcal{D}}[\ell(h, z)], \tag{146} \]

PAC-Bayes 通过融入贝叶斯推理原则对其进行了丰富。这种整合不仅针对单个假设，还针对 \( \mathcal{H} \) 上的分布 \( Q \) 提供界限，从而产生对泛化的精巧刻画，固有地考虑了假设空间中的变异性和不确定性。一些数学构造：真实风险与经验风险。由期望损失定义的真实风险 \( R(h) \)，通常由于 \( \mathcal{D} \) 的未知性而不可获取。取而代之的是，经验风险

\[ \hat{R}(h, S) = \frac{1}{m} \sum_{i=1}^m \ell(h, z_i) \tag{147} \]

作为可计算的代理。PAC-Bayes 解决的关键问题是：_\( \hat{R}(h, S) \) 与 \( R(h) \) 有何关系，以及如何对偏差进行概率界定？_ 对于 \( \mathcal{H} \) 上的分布 \( Q \)，这些风险概括为：

\[ R(Q) = \mathbb{E}_{h \sim Q}[R(h)], \quad \hat{R}(Q, S) = \mathbb{E}_{h \sim Q}[\hat{R}(h, S)]. \tag{148} \]

这种概括至关重要，因为它使分析能够超越单个假设，考虑概率集合，其中 \( Q(h) \) 代表基于观测数据的假设空间上的后验信念。我们现在需要讨论先验分布与后验分布如何编码知识与复杂性。先验 \( P \) 是 \( \mathcal{H} \) 上的固定分布，反映了关于假设合理性的预数据假设。关键的是，\( P \) 必须与 \( S \) 独立，以避免偏差界限。然而，后验 \( Q \) 是数据依赖的，通常选择以最小化经验风险与复杂性的组合。这一选择由 PAC-Bayes 不等式指导，该不等式通过 \( Q \) 与 \( P \) 之间的 Kullback-Leibler (KL) 散度对 \( Q \) 进行正则化：

\[ \text{KL}(Q\|P) = \int_{\mathcal{H}} Q(h) \log \frac{Q(h)}{P(h)} dh. \tag{149} \]

KL 散度量化了将 \( P \) 更新为 \( Q \) 的信息成本，作为惩罚项阻止过于复杂的后验。这种正则化对于防止过拟合至关重要，确保 \( Q \) 在数据忠实性与模型简单性之间取得平衡。

让我们推导 PAC-Bayes 不等式：概率与信息论基础。PAC-Bayes 不等式的推导依赖于概率工具与信息论论证的结合。核心步骤涉及从 \( P \) 到 \( Q \) 的测度变换，利用以下恒等式：

\[ \mathbb{E}_{h \sim Q}[f(h)] = \mathbb{E}_{h \sim P} \left[ f(h) \frac{Q(h)}{P(h)} \right]. \tag{150} \]

这使得 \( Q \) 可以被纳入原本仅适用于固定 \( h \) 的界限中。通过分析 \(\hat{R}(h, S)\) 与 \( R(h) \) 之间偏差的矩生成函数，并将 Hoeffding 不等式应用于经验损失，我们得到对于任意 \( Q \) 和 \( P \)，以至少 \( 1 - \delta \) 的概率持有的以下界：

\[ R(Q) \le \hat{R}(Q, S) + \sqrt{\frac{\text{KL}(Q\|P) + \log \frac{1}{\delta}}{2m}}. \tag{151} \]

因此，泛化界给出为：

\[ \mathcal{L}(f) - \mathcal{L}_{\text{emp}}(f) \le \sqrt{\frac{\mathcal{KL}(Q\|P) + \log(1/\delta)}{2N}}. \tag{152} \]

其中 \(\mathcal{KL}(Q\|P)\) 量化了后验 \( Q \) 与先验 \( P \) 之间的散度。该界引人注目之处在于，它明确将真实风险 \( R(Q) \) 与经验风险 \(\hat{R}(Q, S)\)、KL 散度及样本量 \( m \) 联系起来。PAC-Bayes 界包含了三种竞争力量：经验风险 \(\hat{R}(Q, S)\)、复杂性惩罚 \(\text{KL}(Q\|P)\) 和置信项 \(\sqrt{\frac{\log \frac{1}{\delta}}{2m}}\)。这种相互作用反映了学习中的基本权衡：

- 1. **经验风险：** \(\hat{R}(Q, S)\) 捕捉了后验 \( Q \) 拟合训练数据的程度。
- 2. **复杂性：** KL 散度确保 \( Q \) 保持接近 \( P \)，阻止过拟合并促进泛化。
- 3. **置信：** 项 \(\sqrt{\frac{\log \frac{1}{\delta}}{2m}}\) 随样本量增大而减小，使界更紧并增强可靠性。

KL 项还引入了一种固有的正则化效应，惩罚与先验知识偏差显著的假设。这与奥卡姆剃刀一致，倾向于与数据一致的更简单解释。

PAC-Bayes 形式主义的若干扩展与高级应用。虽然经典 PAC-Bayes 框架假设数据为独立同分布，但最近的进展已将该理论推广至处理结构化数据，例如时间序列和基于图的学习。此外，还探索了替代散度度量，如 Rényi 散度或 Wasserstein 距离，以适应 KL 散度可能不适用的场景。在实际环境中，PAC-Bayes



界限在分析神经网络、贝叶斯集成模型和随机过程中起到了关键作用，即使在高维非凸优化景观中也能提供理论保证。

## 4.2 频谱正则化

频谱正则化的概念指的是神经网络在学习高频模式之前优先学习低频模式，它源于傅里叶分析、优化理论以及深度神经网络固有属性的结合。这一现象与神经网络的功能逼近能力紧密相关，可以通过傅里叶分解和梯度下降优化过程的视角严谨地理解。

### 文献综述

Jin 等人 (2025) [102] 引入了一种新颖的混淆谱正则化技术，以提高机器学习模型的公平性。该研究聚焦于稳健混淆矩阵的谱范数，并提出了一种控制谱属性的方法，以确保更稳健、无偏的学习。它为正则化如何减轻分类任务中的偏差提供了洞察。

Ye 等人 (2025) [103] 将带正则化的谱聚类应用于检测复杂网络中的小簇。该工作通过集成正则化方法增强了谱聚类技术，从而在异常检测和社区检测任务中实现了更好的性能。该方法在高噪声数据环境中显著提高了鲁棒性。

Bhattacharjee 和 Bharadwaj (2025) [104] 探讨了频域表示如何从基于自编码器的特征提取与随机正则化技术相结合中获益。作者提出了一种对称自编码器 (SymAE)，可实现更好的频谱特征泛化，尤其适用于高维数据和深度学习应用。

Wu 等人 (2025) [105] 将频谱正则化应用于地球物理数据处理，具体用于高分辨率速度谱分析。该方法通过使用双曲 Radon 变换正则化，提高了地震成像中速度估计的分辨率，展示了频谱正则化如何惠及传统机器学习以外的应用。

Ortega 等人 (2025) [106] 将 Tikhonov 正则化应用于大气谱分析，以优化高分辨率光谱观测中的气体检索策略。该工作通过减少谱测量中的噪声，显著提高了甲烷 (CH4) 和一氧化二氮 (N2O) 的检测准确性，展示了频谱正则化在遥感与环境监测中的影响。

Kazmi 等人 (2025) [107] 提出了一种基于频谱正则化的联邦学习模型，以提高网络安全威胁检测的鲁棒性。该模型利用深度学习架构中的基于谱范数的正则化，解决了软件定义网络 (SDN) 中非 IID 数据的问题。

Zhao 等人 (2025) [108] 引入了一种正则化深度谱聚类方法，增强了特征选择和聚类鲁棒性。作者利用投影自适应特征选择结合谱图正则化，提高了高维数据集中的聚类准确性和可解释性。

Saranya 和 Menaka (2025) [109] 将频谱正则化与基于量子的机器学习相结合，以分析脑电图信号用于自闭症谱障碍 (ASD) 检测。所提出的方法利用基于小波的正则化改进空间滤波和特征提取，从而实现更可靠的 EEG 模式识别。

Dhalbisoit 等人 (2024) [110] 开发了一种正则化零强制 (RZF) 方法，用于超 5G 网络中的频谱效率优化。作者证明，频谱正则化技术可以显著提高无线通信系统的信噪比，优化大规模 MIMO 架构中的数据传输。

Wei 等人 (2025) [111] 探索了频谱正则化在医学影像中的应用，特别是在 3D 近红外光谱断层扫描中。所提出的模型集成了正则化卷积神经网络 (CNN)，以提高组织成像的分辨率和准确性，展示了频谱正则化在生物医学工程中的应用。

让我们定义一个目标函数 \( f(\mathbf{x}) \)，其中 \( \mathbf{x} \in \mathbb{R}^d \)，及其傅里叶变换 \( \hat{f}(\boldsymbol{\xi}) \) 为

\(\hat{f}(\boldsymbol{\xi}) = \int_{\mathbb{R}^d} f(\mathbf{x}) e^{-i 2 \pi \boldsymbol{\xi} \cdot \mathbf{x}} \, d\mathbf{x}\) (153)

此变换将 \( f(\mathbf{x}) \) 分解为由 \( \boldsymbol{\xi} \) 索引的频率分量。在深度学习的背景下，我们试图用神经网络输出 \( f_{\text{NN}}(\mathbf{x}; \boldsymbol{\theta}) \) 来近似 \( f(\mathbf{x}) \)，其中 \( \boldsymbol{\theta} \) 表示可训练参数集。待最小化的损失函数通常是均方误差：

\(\mathcal{L}(\boldsymbol{\theta}) = \int_{\mathbb{R}^d} |f(\mathbf{x}) - f_{\text{NN}}(\mathbf{x}; \boldsymbol{\theta})|^2 \, d\mathbf{x}\) (154)

我们可以等价地在傅里叶域中表示此损失，利用 Parseval 定理：

\(\mathcal{L}(\boldsymbol{\theta}) = \int_{\mathbb{R}^d} \left| \hat{f}(\boldsymbol{\xi}) - \hat{f}_{\text{NN}}(\boldsymbol{\xi}; \boldsymbol{\theta}) \right|^2 \, d\boldsymbol{\xi}\) (155)

为了求解 \( \boldsymbol{\theta} \)，我们采用梯度下降：

\(\boldsymbol{\theta}^{(t+1)} = \boldsymbol{\theta}^{(t)} - \eta \nabla_{\boldsymbol{\theta}} \mathcal{L}(\boldsymbol{\theta})\) (156)

其中 \( \eta \) 是学习率。损失函数对 \( \boldsymbol{\theta} \) 的梯度为

\(\nabla_{\boldsymbol{\theta}} \mathcal{L}(\boldsymbol{\theta}) = 2 \int_{\mathbb{R}^d} \left( \hat{f}_{\text{NN}}(\boldsymbol{\xi}; \boldsymbol{\theta}) - \hat{f}(\boldsymbol{\xi}) \right) \nabla_{\boldsymbol{\theta}} \hat{f}_{\text{NN}}(\boldsymbol{\xi}; \boldsymbol{\theta}) \, d\boldsymbol{\xi}\) (157)

这一梯度下降过程的核心在于梯度 \( \nabla_{\boldsymbol{\theta}} f_{\text{NN}}(\boldsymbol{\xi}; \boldsymbol{\theta}) \) 相对于频率分量 \( \boldsymbol{\xi} \) 的行为。对于神经网络，尤其是具有 ReLU 激活函数的网络，输出对参数的梯度预期会随高频分量而衰减。这可以近似为

\(\mathcal{R}(\boldsymbol{\xi}) \sim \frac{1}{1 + \| \boldsymbol{\xi} \|^2}\) (158)

这意味着神经网络在训练早期迭代中固有地对目标函数的低频分量更敏感。这种频谱衰减是网络激活函数结构的直接后果，因为其更平滑、低阶项对低频特征更敏感。为了理解神经切核 (NTK) 的作用（它支配神经网络的线性化动力学），我们定义 NTK 为

\(\Theta(\mathbf{x}, \mathbf{x}'; \boldsymbol{\theta}) = \sum_{i=1}^P \frac{\partial f_{\text{NN}}(\mathbf{x}; \boldsymbol{\theta})}{\partial \theta_i} \frac{\partial f_{\text{NN}}(\mathbf{x}'; \boldsymbol{\theta})}{\partial \theta_i}\) (159)

NTK 本质上描述了网络输出如何随其参数变化。训练期间网络输出的演化可由受 NTK 支配的线性系统的解近似。时刻 \( t \) 的网络输出由以下公式给出：

\( f_{\text{NN}}(\mathbf{x}; t) = \sum_k c_k \left( 1 - e^{-\eta \lambda_k t} \right) \phi_k(\mathbf{x}) \) (160)

其中 \(\{ \lambda_k \}\) 是 \( \Theta \) 的特征值，\(\{ \phi_k(\mathbf{x}) \}\) 是对应的特征函数。特征值 \( \lambda_k \) 决定每个频率模式的收敛速度，低频模式（大 \( \lambda_k \)）收敛速度快于高频模式（小 \( \lambda_k \)）：

\( 1 - e^{-\eta \lambda_k t} \to 1 \text{ for large } \lambda_k \text{ and } 1 - e^{-\eta \lambda_k t} \to 0 \text{ for small } \lambda_k \) (161)

频率分量的差分学习率导致了频谱正则化现象，其中网络先学习函数的低频分量，以及


高频模式只有在低频模式已被足够准确地近似后才开始适应。在更正式的语境下，谱偏差也可以用 Sobolev 空间来理解。神经网络函数 \(f_{\text{NN}}\) 可以看作 Sobolev 空间 \(W^{m,2}\) 中的一个函数，其中该空间内函数 \(f\) 的范数定义为

```
\(\|f\|_{W^{m,2}}^2 = \int_{\mathbb{R}^d} (1 + \|\boldsymbol{\xi}\|^2)^m \left| \hat{f}(\boldsymbol{\xi}) \right|^2 d\boldsymbol{\xi}\) (162)
```

训练神经网络时，优化过程会隐式正则化高阶 Sobolev 范数，这意味着网络最初会使用低阶导数（对应于低频模式）来近似目标函数。可以通过在损失函数中引入正则化项来表达这一点：

```
\(\mathcal{L}_{\text{eff}}(\boldsymbol{\theta}) = \mathcal{L}(\boldsymbol{\theta}) + \lambda \|f_{\text{NN}}\|_{W^{m,2}}^2\) (163)
```

其中 \(\lambda\) 是一个正则化参数，用于控制近似中数据忠实度与平滑度之间的权衡。

因此，谱正则化是由于网络架构、梯度下降优化的性质以及神经网络能够学习的函数的固有平滑性而产生的后果。NTK 的数学结构和 Sobolev 空间的正则化性质为理解为什么神经网络优先学习低频模式提供了严谨的框架，强化了神经网络在训练初期隐式偏向平滑、低频近似的观点。这一见解对神经网络的泛化行为及其近似复杂函数的能力具有深远影响。

# 5 神经网络基础

文献综述：Goodfellow 等人（2016）[112] 撰写了一本关于深度学习最全面的书籍之一，涵盖了神经网络的理论基础、优化技术和概率模型。它被广泛用于学术课程和研究。Haykin（2009）[113] 从信号处理的角度解释了神经网络，涵盖了感知机、反向传播和循环网络，采用了强大的数学方法。Schmidhuber（2015）[114] 对深度学习架构进行了历史和理论综述，包括循环神经网络（RNNs）、卷积神经网络（CNNs）和长短期记忆网络（LSTM）。Bishop（2006）[115] 从贝叶斯视角阐述了神经网络和概率图形模型，强调了学习的统计基础。Poggio 和 Smale（2003）[116] 在神经网络、核方法和函数近似之间建立了理论联系。LeCun（2015）[117] 讨论了现代深度学习背后的原理，包括反向传播、无监督学习和分层特征提取。Cybenko（1989）[58] 证明了通用逼近定理，表明带有单隐藏层的神经网络可以逼近任何连续函数。Hornik 等人（1989）[57] 扩展了 Cybenko 的定理，证明多层感知机（MLPs）是通用函数逼近器。Pinkus（1999）[60] 从逼近理论的角度对神经网络进行了严谨的数学讨论。Tishby 和 Zaslavsky（2015）[118] 引入了信息瓶颈框架来理解深度神经网络，解释了网络如何学习高效压缩和编码信息。

## 5.1 感知机与人工神经元

感知机是人工神经网络最简单的形式，作为二分类器运行。它计算输入特征 \(\vec{x} = [x_1, x_2, \dots, x_n]^T \in \mathbb{R}^n\) 与相应权重向量 \(\vec{w} = [w_1, w_2, \dots, w_n]^T \in \mathbb{R}^n\) 的线性组合 \(z\)，并加上偏置项 \(b \in \mathbb{R}\)。这可以表示为

```
\(z = \vec{w}^T \vec{x} + b = \sum_{i=1}^n w_i x_i + b.\) (164)
```

为了确定输出，该值被传递通过阶梯激活函数，在数学上定义为

```
\(\phi(z) = \begin{cases} 1, & z \ge 0, \\ 0, & z < 0. \end{cases}\) (165)
```

因此，感知机的决策过程可以表示为

```
\(y = \phi(\vec{w}^T \vec{x} + b),\) (166)
```

其中 \(y \in \{0, 1\}\)。方程 \(\vec{w}^T \vec{x} + b = 0\) 在 \(\mathbb{R}^n\) 中定义了一个超平面，它充当决策边界。对于任何输入 \(\vec{x}\)，分类由 \(\vec{w}^T \vec{x} + b\) 的符号决定，具体来说，如果 \(\vec{w}^T \vec{x} + b \ge 0\) 则 \(y = 1\)，否则 \(y = 0\)。从几何上看，这种分类对应于将输入空间划分为两个不同的半空间。为了训练感知机，监督学习算法使用标记的训练数据 \(\{(\vec{x}_i, y_i)\}_{i=1}^m\) 迭代调整权重 \(\vec{w}\) 和偏置 \(b\)，其中 \(y_i\) 表示真实标签。当预测输出 \(y_{\text{pred}} = \phi(\vec{w}^T \vec{x}_i + b)\) 与 \(y_i\) 不同时，权重向量和偏置根据以下规则更新：

```
\(\vec{w} \leftarrow \vec{w} + \eta(y_i - y_{\text{pred}})\vec{x}_i,\) (167)
```

和

```
\(b \leftarrow b + \eta(y_i - y_{\text{pred}}),\) (168)
```

其中 \(\eta > 0\) 是学习率。每个单独的权重 \(w_j\) 更新如下

```
\(w_j \leftarrow w_j + \eta(y_i - y_{\text{pred}})x_{ij}.\) (169)
```

对于线性可分数据集，感知机收敛定理断言，算法将在有限次更新后收敛到一个解。具体来说，更新次数由以下界限：

```
\(\frac{R^2}{\gamma^2},\) (170)
```

其中 \(R = \max_i \|\vec{x}_i\|\) 是输入向量的最大范数，\(\gamma\) 是最小间隔，定义为

```
\(\gamma = \min_i \frac{y_i(\vec{w}^T \vec{x}_i + b)}{\|\vec{w}\|}.\) (171)
```

感知机的局限性，特别是其无法解决线性不可分问题（如 XOR 问题），使得扩展到具有非线性激活函数的人工神经元成为必要。一个常用的选择是 Sigmoid 激活函数

```
\(\phi(z) = \frac{1}{1 + e^{-z}},\) (172)
```

它将 \(z \in \mathbb{R}\) 映射到连续区间 \((0, 1)\)。Sigmoid 函数的导数（对基于梯度的优化至关重要）为

```
\(\phi'(z) = \phi(z)(1 - \phi(z)).\) (173)
```

另一种广泛使用的激活函数是双曲正切 \(\tanh(z)\)，定义为

```
\(\tanh(z) = \frac{e^z - e^{-z}}{e^z + e^{-z}},\) (174)
```

其导数为

tanh'(z) = 1 - tanh^2(z).

(175)

ReLU（修正线性单元）定义为

\(\phi(z) = \max(0, z),\)

(176)

其导数为

\(\phi'(z) = \begin{cases} 1, & z > 0, \\ 0, & z \le 0. \end{cases}\)

(177)

这些非线性激活使网络能够近似非线性决策边界，这一能力在感知机中不存在。人工神经元构成了多层感知机（MLPs）的基础，其中神经元被组织成层。对于 \(L\) 层网络，输入 \(\vec{x}\) 逐层变换。在第 \(l\) 层，输出为

\(\vec{z}^{(l)} = \phi^{(l)}(\vec{W}^{(l)}\vec{z}^{(l-1)} + \vec{b}^{(l)}),\)

(178)

其中 \(\vec{W}^{(l)} \in \mathbb{R}^{n_l \times n_{l-1}}\) 是权重矩阵，\(\vec{b}^{(l)} \in \mathbb{R}^{n_l}\) 是偏置向量，\(\phi^{(l)}\) 是激活函数。网络的输出为

\(\hat{\vec{y}} = \phi^{(L)}(\vec{W}^{(L)}\vec{z}^{(L-1)} + \vec{b}^{(L)}).\)

(179)

通用逼近定理保证，拥有足够神经元和非线性激活的 MLP 可以以任意精度逼近任何连续函数 \(f : \mathbb{R}^n \to \mathbb{R}^m\)。形式上，对于任何 \(\epsilon > 0\)，存在一个 MLP \(g(\vec{x})\)，使得

\(\|f(\vec{x}) - g(\vec{x})\|_\infty < \epsilon\)

(180)

对所有 \(\vec{x} \in \mathbb{R}^n\) 成立。训练 MLP 最小化一个损失函数 \(L\)，该函数量化预测输出 \(\hat{\vec{y}}\) 与真实标签 \(\vec{y}\) 之间的误差。对于回归，均方误差为

\(L = \frac{1}{m} \sum_{i=1}^m \|\hat{\vec{y}}_i - \vec{y}_i\|^2,\)

(181)

对于分类，交叉熵损失为

\(L = -\frac{1}{m} \sum_{i=1}^m \left[ \vec{y}_i^T \log \hat{\vec{y}}_i + (1 - \vec{y}_i)^T \log(1 - \hat{\vec{y}}_i) \right].\)

(182)

优化使用随机梯度下降（SGD），按照以下方式更新参数 \(\Theta = \{ \vec{W}^{(l)}, \vec{b}^{(l)} \}_{l=1}^L\)：

\(\Theta \leftarrow \Theta - \eta \nabla_\Theta L.\)

(183)

梯度通过反向传播计算：

\(\frac{\partial L}{\partial \vec{W}^{(l)}} = \delta^{(l)} \vec{z}^{(l-1)T},\)

(184)

其中 \(\delta^{(l)}\) 是第 \(l\) 层的误差信号，递归计算为

\(\delta^{(l)} = (\vec{W}^{(l+1)T} \delta^{(l+1)}) \circ \phi'^{(l)}(\vec{z}^{(l)}).\)

(185)

这种递归结构，结合链式法则的应用，能够高效地将误差信号从输出层向回传播到输入层。

因此，人工神经元及其扩展为现代深度学习奠定了基础。其数学基础和计算框架对于解决从分类和回归到复杂决策等各种问题起着关键作用。其表述中线性代数、微积分和优化理论的相互作用，确保了这些网络既在理论上稳健，又在实践中强大。





## 5.2 前馈神经网络

前馈神经网络（FNNs）是设计用于通过组合仿射变换和非线性激活函数来逼近任意映射 \(f : \mathbb{R}^n \rightarrow \mathbb{R}^m\) 的数学构造。其核心，这些网络由 \(L\) 层组成，其中每一层 \(k\) 通过以下操作将其输入 \(\vec{a}_{k-1} \in \mathbb{R}^{m_{k-1}}\) 转换为输出 \(\vec{a}_k \in \mathbb{R}^{m_k}\)：

\(\vec{a}_k = f_k(W_k \vec{a}_{k-1} + \vec{b}_k).\) (186)

这里，\(W_k \in \mathbb{R}^{m_k \times m_{k-1}}\) 表示权重矩阵，\(\vec{b}_k \in \mathbb{R}^{m_k}\) 是偏置向量，\(f_k : \mathbb{R}^{m_k} \rightarrow \mathbb{R}^{m_k}\) 是逐元素激活函数。形式上，如果我们将输入层表示为 \(\vec{a}_0 = \vec{x}\)，则网络的最终输出 \(\vec{y} \in \mathbb{R}^m\) 由 \(\vec{a}_L = f_L(W_L \vec{a}_{L-1} + \vec{b}_L)\) 给出。此序列中的每个变换可以描述为 \(\vec{z}_k = W_k \vec{a}_{k-1} + \vec{b}_k，随后是激活 \(\vec{a}_k = f_k(\vec{z}_k)\)。仿射变换 \(\vec{z}_k = W_k \vec{a}_{k-1} + \vec{b}_k\) 包含了使用权重 \(W_k\) 对输入进行线性组合以及添加偏置 \(\vec{b}_k\)。对于任何两层 \(k\) 和 \(k+1\)，整体变换可以表示为

\(\vec{z}_{k+1} = W_{k+1}(W_k \vec{a}_{k-1} + \vec{b}_k) + \vec{b}_{k+1}.\) (187)

展开后，我们有

\(\vec{z}_{k+1} = W_{k+1} W_k \vec{a}_{k-1} + W_{k+1} \vec{b}_k + \vec{b}_{k+1}.\) (188)

如果没有由 \(f_k\) 引入的非线性，网络将退化为单一仿射变换

\(\vec{y} = W \vec{x} + \vec{b},\) (189)

其中 \(W = W_L W_{L-1} \cdots W_1\) 且

\(\vec{b} = W_L W_{L-1} \cdots W_2 \vec{b}_1 + \cdots + \vec{b}_L.\) (190)

因此，引入非线性激活函数至关重要，因为它使网络能够逼近非线性映射。激活函数 \(f_k\) 逐元素地应用于预激活向量 \(\vec{z}_k\)。激活函数的选择显著影响网络的行为和训练。例如，Sigmoid 激活 \(f(x) = \frac{1}{1+e^{-x}}\) 将输入压缩到范围 \((0, 1)\)，其导数由

\(f'(x) = f(x)(1 - f(x)).\) (191)

双曲正切激活 \(f(x) = \tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}\) 将输入映射到 \((-1, 1)\)，其导数为

\(f'(x) = 1 - \tanh^2(x).\) (192)

ReLU 激活 \(f(x) = \max(0, x)\)，常用于现代网络，其导数为

\(f'(x) = \begin{cases} 1 & x > 0, \\ 0 & x \le 0. \end{cases}\) (193)

这些导数对于基于梯度的优化至关重要。训练前馈神经网络的目标是最小化损失函数 \(\mathcal{L}\)，该函数测量在数据集 \(\{(\vec{x}_i, \vec{t}_i)\}_{i=1}^N\) 上预测输出 \(\vec{y}_i\) 与真实目标 \(\vec{t}_i\) 之间的差异。对于回归问题，通常使用均方误差（MSE），给出为

\(\mathcal{L} = \frac{1}{N} \sum_{i=1}^N \|\vec{y}_i - \vec{t}_i\|^2 = \frac{1}{N} \sum_{i=1}^N \sum_{j=1}^m (y_{i,j} - t_{i,j})^2.\) (194)

在分类任务中，交叉熵损失被广泛采用，定义为

\(\mathcal{L} = -\frac{1}{N} \sum_{i=1}^N \sum_{j=1}^m t_{i,j} \log(y_{i,j}),\) (195) 其中 \( t_{i,j} \) 表示独热编码标签。\(\mathcal{L}\) 相对于网络参数的梯度使用反向传播计算，该方法迭代应用链式法则，将误差从输出层传播到输入层。在反向传播过程中，输出层的误差信号计算为

\(\delta_L = \frac{\partial \mathcal{L}}{\partial \vec{z}_L} = \nabla_y \mathcal{L} \odot f'_L(\vec{z}_L),\) (196)

其中 \( \odot \) 表示 Hadamard 积。对于隐藏层，误差信号向后传播为

\(\delta_k = (W_{k+1}^T \delta_{k+1}) \odot f'_k(\vec{z}_k).\) (197)

损失相对于权重和偏置的梯度随后由

\(\frac{\partial \mathcal{L}}{\partial W_k} = \delta_k \vec{a}_{k-1}^T, \quad \frac{\partial \mathcal{L}}{\partial \vec{b}_k} = \delta_k.\) (198)

这些梯度用于通过随机梯度下降（SGD）等优化算法更新参数，其中

\( W_k \leftarrow W_k - \eta \frac{\partial \mathcal{L}}{\partial W_k}, \quad \vec{b}_k \leftarrow \vec{b}_k - \eta \frac{\partial \mathcal{L}}{\partial \vec{b}_k},\) (199)

其中 \( \eta > 0 \) 为学习率。通用逼近定理严格确立，至少具有一个隐藏层和足够多神经元的前馈神经网络可以逼近紧致域 \( D \subset \mathbb{R}^n \) 上的任何连续函数 \( f : \mathbb{R}^n \rightarrow \mathbb{R}^m \)。具体来说，对于任何 \( \epsilon > 0 \)，存在一个网络 \( \hat{f} \)，使得对所有 \( \vec{x} \in D \) 均有 \( \| f(\vec{x}) - \hat{f}(\vec{x}) \| < \epsilon \)。这种表达能力源于仿射变换和非线性激活的组合使网络能够通过将输入空间划分为区域并为每个区域分配不同的函数行为来逼近高度复杂的函数。

总之，前馈神经网络是一个强大的数学框架，植根于线性代数、微积分和优化。其在输入和输出空间之间建模复杂映射的能力使其成为机器学习的基石，严格的数学原理支撑着其结构和训练。仿射变换、非线性激活和基于梯度的优化的组合使这些网络能够在广泛的应用中实现无与伦比的灵活性和性能。

## 5.3 激活函数

在 **神经网络** 的语境中，激活函数作为使网络能够逼近复杂非线性映射的关键组件。当神经网络处理输入数据时，每个神经元计算输入的加权和，然后应用激活函数 \( \sigma(z) \) 以产生输出。数学上，设神经元的输入向量为 \( \mathbf{x} = (x_1, x_2, \dots, x_n) \)，与这些输入关联的权重向量为 \( \mathbf{w} = (w_1, w_2, \dots, w_n) \)。相应的偏置项表示为 \( b \)。传递给激活函数的净输入 \( z \) 由以下给出：

\( z = \mathbf{w}^\top \mathbf{x} + b = \sum_{i=1}^n w_i x_i + b \) (200)

其中 \( \mathbf{w}^\top \mathbf{x} \) 表示权重向量和输入向量的点积。然后将激活函数 \( \sigma(z) \) 应用于此净输入以获得神经元的输出 \( a \)：

\( a = \sigma(z) = \sigma \left( \sum_{i=1}^n w_i x_i + b \right).\) (201)

激活函数将 *非线性* 引入神经元的响应，这是神经网络的关键方面，因为如果没有它，网络只能对输入数据执行线性变换，从而限制了其逼近复杂现实世界函数的能力。由 \(\sigma(z)\) 引入的非线性至关重要，因为它使网络能够捕捉输入和输出之间的复杂关系，使神经网络能够解决需要分层特征提取的问题，例如图像分类、时间序列预测和语言建模。非线性的重要性在考虑多层神经网络的数学表述时最为明显。对于具有 \(L\) 层的前馈神经网络，网络的输出 \(\hat{y}\) 由一系列仿射变换和激活函数的复合给出。设 \(\mathbf{x}\) 表示输入向量，\(W_k\) 和 \(b_k\) 分别为第 \(k\) 层的权重矩阵和偏置向量，\(\sigma_k\) 为第 \(k\) 层的激活函数。网络的输出为：

$$\hat{y} = \sigma_L(W_L\sigma_{L-1}(W_{L-1} \cdots \sigma_1(W_1\mathbf{x} + b_1) + b_2) + \cdots + b_L). \quad (202)$$

如果 \(\sigma(z)\) 是线性函数，例如 \(\sigma(z) = c \cdot z\) 对于某个常数 \(c\)，则此类函数的复合仍然会产生线性函数。具体来说，如果每个 \(\sigma_k\) 都是线性的，则整个网络函数将简化为单一线性变换：

$$\hat{y} = c_1 \cdot \mathbf{x} + c_2, \quad (203)$$

其中 \(c_1\) 和 \(c_2\) 是依赖于网络参数的常数。在这种情况下，无论层数多少，网络的表达能力都不会超过简单的线性回归模型。因此，激活函数引入的 *非线性* 使神经网络能够逼近 *任何连续函数*，正如 *通用逼近定理* 所保证的。该定理指出，具有至少一个隐藏层和足够多神经元的前馈神经网络可以逼近任何连续函数 \(f(\mathbf{x})\)，前提是激活函数是非线性的且网络具有足够的容量。

接下来，考虑激活函数 \(\sigma(z)\) 必须具备的数学属性。首先，它必须是 *可微分* 的，以允许使用 *反向传播* 等基于梯度的优化方法进行训练。反向传播依赖于微积分的 *链式法则* 来计算损失函数 \(\mathcal{L}\) 相对于网络参数（权重和偏置）的梯度。假设 \(\mathcal{L} = \mathcal{L}(\hat{y}, \mathbf{y})\) 是损失函数，其中 \(\hat{y}\) 是网络的预测输出，\(\mathbf{y}\) 是真实标签。在训练期间，我们使用链式法则计算 \(\mathcal{L}\) 相对于权重的梯度。设 \(a_k = \sigma_k(z_k)\) 表示第 \(k\) 层激活函数的输出，其中 \(z_k\) 是激活函数的输入。损失相对于第 \(k\) 层权重的梯度由以下给出：

$$\frac{\partial \mathcal{L}}{\partial W_k} = \frac{\partial \mathcal{L}}{\partial a_k} \frac{\partial a_k}{\partial z_k} \frac{\partial z_k}{\partial W_k}. \quad (204)$$

术语 \(\frac{\partial a_k}{\partial z_k}\) 是激活函数的 *导数*，对于基于梯度的优化有效工作，该导数必须存在且定义明确。如果激活函数不可微分，反向传播算法将无法计算梯度，从而阻止训练过程继续进行。

现在考虑实际中常用的特定形式的激活函数。**Sigmoid** 激活函数是最著名的之一，定义为：

$$\sigma(z) = \frac{1}{1 + e^{-z}}. \quad (205)$$

其导数为：

$$\sigma'(z) = \sigma(z)(1 - \sigma(z)), \quad (206)$$





可以通过对 \(\sigma(z)\) 的表达式应用链式法则来推导。虽然 sigmoid 是可微且光滑的，但它存在 *梯度消失问题*，特别是对于 \(z\) 取很大正或负值时。具体来说，当 \(z \to \infty\) 时，\(\sigma'(z) \to 0\)，同样当 \(z \to -\infty\) 时，\(\sigma'(z) \to 0\)。这导致在反向传播过程中梯度非常小，使得当输入值变得极端时，网络难以学习。为了缓解梯度消失问题，**双曲正切（tanh）**函数常被用作替代方案。它定义为：

\(\tanh(z) = \frac{e^z - e^{-z}}{e^z + e^{-z}},\tag{207}\)

导数为：

\(\tanh'(z) = 1 - \tanh^2(z).\tag{208}\)

tanh 函数输出范围为 \((-1, 1)\) 的值，这有助于将数据中心化到零附近。虽然 tanh 函数克服了与 sigmoid 函数相关的一些梯度消失问题，但对于大的 \(|z|\) 它仍然存在该问题，此时梯度接近零。**整线性单元（ReLU）**是另一种常用的激活函数。它定义为：

\(\text{ReLU}(z) = \max(0, z),\tag{209}\)

导数为：

\(\text{ReLU}'(z) = \begin{cases} 1, & z > 0, \\ 0, & z \le 0. \end{cases}\tag{210}\)

ReLU 特别有利，因为它计算效率高，只需要与零进行比较。此外，对于 \(z\) 的正值，导数是常数且等于 1，这有助于避免梯度消失问题。然而，ReLU 可能会受到 *失活 ReLU 问题* 的影响，即如果权重初始化不当或学习率过高，神经元对所有输入都输出零，导致不参与学习过程的非活跃神经元。为了解决失活 ReLU 问题，引入了 **漏整线性单元（Leaky ReLU）** 激活函数，定义为：

\(\text{Leaky ReLU}(z) = \begin{cases} z, & z > 0, \\ \alpha z, & z \le 0, \end{cases}\tag{211}\)

其中 \(\alpha\) 是一个小常数，通常取 0.01。Leaky ReLU 的导数为：

\(\text{Leaky ReLU}'(z) = \begin{cases} 1, & z > 0, \\ \alpha, & z \le 0. \end{cases}\tag{212}\)

Leaky ReLU 通过允许 \(z\) 为负值时存在小的非零梯度，确保神经元不会完全失活。最后，对于分类任务，特别是当存在多个类别时，**Softmax** 激活函数通常用于神经网络的输出层。Softmax 函数定义为：

\(\text{Softmax}(z_i) = \frac{e^{z_i}}{\sum_{j=1}^m e^{z_j}},\tag{213}\)

其中 \(z_i\) 是输出层中第 \(i\) 个神经元的输入，分母确保输出之和为 1，从而使其可解释为概率。Softmax 函数通常用于多类分类问题，网络必须从几个可能的类别中预测一个类别。

总之，激活函数是神经网络的重要组成部分，使其能够学习数据中的复杂模式，从而成功将神经网络应用于各种任务。不同的激活函数——如 sigmoid、tanh、ReLU、漏整线性单元和 Softmax——各自具有独特的优势和局限性，它们的选择显著影响神经网络的性能和训练动态。

## 5.4 损失函数

在神经网络中，**损失函数**是一种关键的数学工具，用于量化模型预测输出与真实输出或目标之间的差异。设 **x**_<sub>i</sub>_ 为输入向量，**y**_<sub>i</sub>_ 为第 _i_ 个训练样本对应的目标向量。网络由权重 **W** 参数化，生成一个表示为 \(\hat{\mathbf{y}}_i = f(\mathbf{x}_i; \mathbf{W})\) 的预测，其中 \(f(\mathbf{x}_i; \mathbf{W})\) 表示模型的输出。训练神经网络的目标是尽量减少所有训练样本中预测输出 \(\hat{\mathbf{y}}_i\) 与真实标签 **y**_<sub>i</sub>_ 之间的差异，从而有效学习从输入到输出的映射函数。一个典型的目标函数是 _N_ 个样本数据集上的**平均损失**：

\(\mathcal{L}(\mathbf{W}) = \frac{1}{N} \sum_{i=1}^N L(\mathbf{y}_i, \hat{\mathbf{y}}_i)\) (214)

其中 \(L(\mathbf{y}_i, \hat{\mathbf{y}}_i)\) 表示损失函数，用于计算每个数据点上真实输出 **y**_<sub>i</sub>_ 与预测输出 \(\hat{\mathbf{y}}_i\) 之间的误差。为了最小化此目标函数，使用了诸如**梯度下降**之类的优化算法。权重 **W** 的通用更新规则如下：

\(\mathbf{W} \leftarrow \mathbf{W} - \eta \nabla_{\mathbf{W}} \mathcal{L}(\mathbf{W})\) (215)

其中 \(\eta\) 是**学习率**，\(\nabla_{\mathbf{W}} \mathcal{L}(\mathbf{W})\) 是损失函数关于权重的梯度。梯度是通过**反向传播**计算的，它应用微积分中的**链式法则**将误差向后通过网络传播，更新参数以最小化损失。为此，我们使用损失关于每一层权重和偏置的偏导数，确保误差适当地分配到所有层。对于回归任务，**均方误差（MSE）**损失经常被使用。该损失函数将误差量化为预测值与真实值之间平均平方差。_N_ 个样本数据集的 MSE 如下：

\(L_{\text{MSE}} = \frac{1}{N} \sum_{i=1}^N (\mathbf{y}_i - \hat{\mathbf{y}}_i)^2\) (216)

其中 \(\hat{\mathbf{y}}_i = f(\mathbf{x}_i; \mathbf{W})\) 是网络对第 _i_ 个输入 **x**_<sub>i</sub>_ 的预测输出。MSE 关于网络输出 \(\hat{\mathbf{y}}_i\) 的梯度为：

\(\frac{\partial L_{\text{MSE}}}{\partial \hat{\mathbf{y}}_i} = 2 (\hat{\mathbf{y}}_i - \mathbf{y}_i)\) (217)

该梯度指导权重更新朝着最小化平方误差的方向进行，从而使模型更好地拟合训练数据。对于**分类任务**，通常采用**交叉熵损失**，因为它特别适用于输出是多个类别上概率分布的任务。在二分类情况下，目标标签 **y**_<sub>i</sub>_ 为 0 或 1，二元交叉熵损失函数定义为：

\(L_{\text{CE}} = -\frac{1}{N} \sum_{i=1}^N [y_i \log(\hat{y}_i) + (1 - y_i) \log(1 - \hat{y}_i)]\) (218)

其中 \(\hat{y}_i = f(\mathbf{x}_i; \mathbf{W})\) 是第 _i_ 个样本属于正类（即类别 1）的预测概率。对于多类分类，目标标签 **y**_<sub>i</sub>_ 是表示真实类别的独热编码向量，交叉熵损失的一般形式为：

\(L_{\text{CE}} = -\frac{1}{N} \sum_{i=1}^N \sum_{c=1}^C y_{i,c} \log(\hat{y}_{i,c})\) (219)

其中 \(C\) 是类别的数量，\(\hat{y}_{i,c} = f(\mathbf{x}_i; \mathbf{W})\) 是第 _i_ 个样本属于类别 \(c\) 的预测概率。交叉熵损失关于预测概率 \(\hat{\mathbf{y}}_i\) 的梯度为：

\(\frac{\partial L_{\text{CE}}}{\partial \hat{y}_{i,c}} = \hat{y}_{i,c} - y_{i,c}\) (220)

该梯度通过调整模型参数来减少预测概率与实际类别标签之间的差异，从而促进权重更新。

在神经网络训练中，优化过程通常涉及正则化技术以防止**过拟合**，尤其是在处理高维数据或深层网络时。**L2 正则化**（也称为**脊回归**）是一种常见的方法，它通过向损失函数添加与权重 L2 范数平方成正比的项来惩罚大权重。正则化损失函数变为：

\(L_{\text{reg}} = L_{\text{MSE}} + \lambda \sum_{j=1}^n W_j^2\) (221)

其中 \(\lambda\) 是正则化强度，\(W_j\) 表示网络的参数。正则化损失关于权重的梯度为：

\(\frac{\partial L_{\text{reg}}}{\partial W_j} = \frac{\partial L_{\text{MSE}}}{\partial W_j} + 2\lambda W_j\) (222)

这一额外项抑制了权重的大值，降低了模型的复杂性，并有助于其更好地泛化到未见数据。另一种正则化形式是 **L1 正则化**（或**拉索回归**），它通过向损失函数添加权重的 L1 范数来促进模型的稀疏性。L1 正则化损失函数为：

\(L_{\text{reg}} = L_{\text{MSE}} + \lambda \sum_{j=1}^n |W_j|\) (223)

该正则化损失函数关于权重的梯度为：

\(\frac{\partial L_{\text{reg}}}{\partial W_j} = \frac{\partial L_{\text{MSE}}}{\partial W_j} + \lambda \text{sign}(W_j)\) (224)

其中 \(\text{sign}(W_j)\) 是符号函数，当 \(W_j\) 为正值时返回 1，为负值时返回 -1，当 \(W_j = 0\) 时返回 0。L1 正则化通过将许多权重强制为精确为零，鼓励模型仅选择一小部分特征，从而简化模型并提高可解释性。神经网络的优化过程可以看作是求解一个**非凸优化问题**，因为所使用的高度非线性激活函数和深层架构。在此背景下，**随机梯度下降（SGD）**通常用于执行优化，通过基于随机小批量数据计算的梯度来更新权重。SGD 的更新规则可表示为：

\(\mathbf{W} \leftarrow \mathbf{W} - \eta \nabla_{\mathbf{W}} L_{\text{batch}}\) (225)

其中 \(\nabla_{\mathbf{W}} L_{\text{batch}}\) 是在小批量上计算的损失函数梯度，\(\eta\) 是学习率。由于目标函数的非凸性，SGD 倾向于收敛到**局部最小值**或**鞍点**，而不是全局最小值，特别是在具有多层的深度神经网络中。

总之，损失函数通过量化预测输出与真实输出之间的误差，在指导神经网络训练中的优化过程方面起着核心作用。不同


根据问题的性质采用不同的损失函数，MSE 常用于回归，而交叉熵用于分类。引入 L2 和 L1 正则化等正则化技术以防止过拟合并确保更好的泛化能力。通过梯度下降等优化算法，基于损失函数的梯度迭代更新神经网络参数，最终目标是在所有训练样本上最小化损失。

# 6 训练神经网络

**文献综述:** Sorrenson (2025) [119] 引入了一种框架，使无限制神经网络的精确最大似然训练成为可能。它提出了基于概率模型的新训练方法，并将其应用于科学应用。Liu 和 Shi (2015) [120] 将先进的神经网络理论应用于气象预测。它使用灵敏度分析和新的训练技术来缓解样本量限制。Das 等人 (2025) [121] 将有限积分变换 (FIT) 与梯度增强物理信息神经网络 (g-PINN) 相结合，优化工程应用中的训练。Zhang 等人 (2025) [122] 在其论文中探讨了神经切线核 (NTK) 理论，以建模深度网络的梯度下降训练过程及其在结构识别中的意义。Ali 和 Hussein (2025) [123] 开发了一种混合方法，结合模糊集理论和人工神经网络，通过启发式优化增强训练鲁棒性。Li (2025) [124] 引入了一种基于深度学习的策略，用于训练不完全信息广博式博弈中的神经网络，强调离线训练技术。Hu 等人 (2025) [125] 探索了基于深度学习的 PDE 求解器的收敛特性，分析训练损失和函数空间特性。Chen 等人 (2025) [126] 开发了一种基于 Transformer 的神经网络训练框架用于风险分析，包含特征映射和博弈论解释。Sun 等人 (2025) [127] 建立了一套新的基准测试套件，用于优化在脉冲神经网络训练中的神经架构搜索 (NAS) 技术。Zhang 等人 (2025) [128] 提出了一种神经网络的新型迭代训练方法，增强了理论和实践中的收敛保证。

## 6.1 反向传播算法

考虑一个具有 \( L \) 层的神经网络，其中每一层 \( l \)（\( l = 1, 2, \dots, L \)）由权重矩阵 \( \mathbf{W}^{(l)} \in \mathbb{R}^{n_l \times n_{l-1}} \)、偏置向量 \( \mathbf{b}^{(l)} \in \mathbb{R}^{n_l} \)、以及逐元素应用的激活函数 \( \sigma^{(l)} \) 组成。网络对第 \( i \) 个训练样本的输入向量 \( x^{(i)} \in \mathbb{R}^{n_0} \) 进行处理，其中 \( n_0 \) 是输入特征的数量，并将其通过各层传播以产生输出 \( \hat{y}^{(i)} \in \mathbb{R}^{n_L} \)，其中 \( n_L \) 是输出单元的数量。需要优化的网络参数（权重和偏置）\( \theta = \{\mathbf{W}^{(l)}, \mathbf{b}^{(l)}\}_{l=1}^L \) 旨在最小化一个损失函数，该函数捕获所有训练样本中预测输出 \( \hat{y}^{(i)} \) 与真实目标 \( y^{(i)} \) 之间的误差。对于每个训练样本，我们将损失函数 \( \mathcal{L}(\hat{y}^{(i)}, y^{(i)}) \) 定义为平方误差：

\[
\mathcal{L}(\hat{y}^{(i)}, y^{(i)}) = \frac{1}{2} \|\hat{y}^{(i)} - y^{(i)}\|_2^2, \quad (226)
\]

其中 \( \| \cdot \|_2 \) 表示欧几里得范数。整个数据集的总损失 \( J(\theta) \) 是各个损失的平均值：

\[
J(\theta) = \frac{1}{N} \sum_{i=1}^N \mathcal{L}(\hat{y}^{(i)}, y^{(i)}), \quad (227)
\]

其中 \( N \) 是训练样本的数量。对于平方误差损失，可以写成：

\[
J(\theta) = \frac{1}{2N} \sum_{i=1}^N \|\hat{y}^{(i)} - y^{(i)}\|_2^2. \quad (228)
\]

网络的前向传播包括计算每一层的激活值。对于第 \( l \) 层，预激活 \( z^{(l)} \) 的计算如下：

\[
z^{(l)} = \mathbf{W}^{(l)}a^{(l-1)} + \mathbf{b}^{(l)}, \quad (229)
\]

其中 \( a^{(l-1)} \) 是前一层的激活值，\(\mathbf{W}^{(l)}\) 是连接第 \( (l-1) \) 层到第 \( l \) 层的权重矩阵。该层的输出，即激活值 \( a^{(l)} \)，是通过将激活函数 \( \sigma^{(l)} \) 逐元素应用于 \( z^{(l)} \) 计算得到的：

\[
a^{(l)} = \sigma^{(l)}(z^{(l)}). \quad (230)
\]

网络的最终输出由最后一层的激活值 \( a^{(L)} \) 给出，即预测输出 \( \hat{y}^{(i)} \)：

\[
\hat{y}^{(i)} = a^{(L)}. \quad (231)
\]

反向传播算法计算损失函数 \( J(\theta) \) 相对于每个参数（权重和偏置）的梯度。首先，计算输出层的误差。令 \( \delta^{(L)} \) 表示第 \( L \) 层的误差。这是通过对输出层的激活值求损失函数的导数来计算的：

\[
\delta^{(L)} = \frac{\partial \mathcal{L}}{\partial a^{(L)}} \odot \sigma^{(L)\prime}(z^{(L)}), \quad (232)
\]

其中 \( \odot \) 表示逐元素乘法，\( \sigma^{(L)\prime}(z^{(L)}) \) 是对 \( z^{(L)} \) 逐元素应用的激活函数的导数。对于平方误差损失，相对于激活值的导数为：

\[
\frac{\partial \mathcal{L}}{\partial a^{(L)}} = \hat{y}^{(i)} - y^{(i)} \quad (233)
\]

因此，输出层的误差项为：

\[
\delta^{(L)} = (\hat{y}^{(i)} - y^{(i)}) \odot \sigma^{(L)\prime}(z^{(L)}) \quad (234)
\]

为了将误差向后传播通过网络，我们计算隐藏层的误差。对于每个隐藏层 \( l = L-1, L-2, \dots, 1 \)，误差 \( \delta^{(l)} \) 通过链式法则计算：

\[
\delta^{(l)} = (\mathbf{W}^{(l+1)T}\delta^{(l+1)}) \odot \sigma^{(l)\prime}(z^{(l)}) \quad (235)
\]

其中 \( \mathbf{W}^{(l+1)T} \in \mathbb{R}^{n_{l+1} \times n_l} \) 是连接第 \( l \) 层到第 \( l+1 \) 层的权重矩阵的转置。该方程利用了这样一个事实：第 \( l \) 层的误差取决于下一层的误差，由权重调制，并受第 \( l \) 层激活函数导数的影响。一旦所有层的误差 \( \delta^{(l)} \) 都已计算，我们就可以计算损失函数相对于参数（权重和偏置）的梯度。损失相对于权重 \( \mathbf{W}^{(l)} \) 的梯度为：

\[
\frac{\partial J(\theta)}{\partial \mathbf{W}^{(l)}} = \frac{1}{N} \sum_{i=1}^N \delta^{(l)} (a^{(l-1)})^T \quad (236)
\]

损失相对于偏置 \( \mathbf{b}^{(l)} \) 的梯度为：

\[
\frac{\partial J(\theta)}{\partial \mathbf{b}^{(l)}} = \frac{1}{N} \sum_{i=1}^N \delta^{(l)} \quad (237)
\]

计算这些梯度后，我们使用诸如梯度下降之类的优化算法更新参数。权重更新规则为：

\[
\mathbf{W}^{(l)} \leftarrow \mathbf{W}^{(l)} - \eta \frac{\partial J(\theta)}{\partial \mathbf{W}^{(l)}}, \quad (238)
\]

偏置更新规则为：

\[
\mathbf{b}^{(l)} \leftarrow \mathbf{b}^{(l)} - \eta \frac{\partial J(\theta)}{\partial \mathbf{b}^{(l)}} \quad (239)
\]

其中 \( \eta \) 是学习率，控制梯度下降更新中的步长。前向传播、反向传播和参数更新的过程会在多个迭代周期中重复，每个迭代周期包含一次前向传播、一次后向传播和一次参数更新，直到网络收敛到损失函数的局部最小值。

在反向传播的每一步中，链式法则被递归应用以将误差向后传播通过网络，调整每个权重和偏置以最小化总损失。激活函数 \( \sigma^{(l)'}(z^{(l)}) \) 的导数至关重要，因为它决定了每一层误差是如何被调制的。取决于激活函数的选择（例如，ReLU、sigmoid 或 tanh），导数将采取不同的形式，这一选择直接影响网络的学习动态和收敛速度。因此，反向传播是神经网络训练的计算支柱。通过高效的误差传播计算损失函数相对于网络参数的梯度，反向传播使网络能够迭代调整其参数，逐渐最小化误差并提高其在各项任务中的性能。这一过程在数学上是严谨的，利用了微积分和优化的基本原理，确保神经网络能够从其训练数据中有效学习。

## 6.2 梯度下降变体

使用梯度下降及其变体训练神经网络是一个计算密集的过程，旨在最小化一个可微的标量损失函数 \(\mathcal{L}(\boldsymbol{\theta})\)，其中 \(\boldsymbol{\theta}\) 表示神经网络的参数向量。损失函数通常表示为

\[
\mathcal{L}(\boldsymbol{\theta}) = \frac{1}{N} \sum_{i=1}^N \ell(\boldsymbol{\theta}; \boldsymbol{x}_i, y_i), \quad (240)
\]

其中 \((\boldsymbol{x}_i, y_i)\) 是训练数据集中大小为 \(N\) 的输入-输出对，\(\ell(\boldsymbol{\theta}; \boldsymbol{x}_i, y_i)\) 是样本特定的损失。最小化问题通过迭代求解，从初始猜测 \(\boldsymbol{\theta}^{(0)}\) 开始，并根据以下规则更新：

\[
\boldsymbol{\theta}^{(k+1)} = \boldsymbol{\theta}^{(k)} - \eta \nabla_{\boldsymbol{\theta}} \mathcal{L}(\boldsymbol{\theta}), \quad (241)
\]

其中 \(\eta > 0\) 是学习率，\(\nabla_{\boldsymbol{\theta}} \mathcal{L}(\boldsymbol{\theta})\) 是损失相对于 \(\boldsymbol{\theta}\) 的梯度。通过反向传播计算的梯度遵循链式法则，并通过网络的各层传播以最优地调整权重和偏置。在具有 \( L \) 层的前馈神经网络中，计算过程如下。第 \( l \) 层的输入为

\[
\boldsymbol{z}^{(l)} = \boldsymbol{W}^{(l)} \boldsymbol{a}^{(l-1)} + \boldsymbol{b}^{(l)}, \quad (242)
\]

其中 \(\boldsymbol{W}^{(l)} \in \mathbb{R}^{n_l \times n_{l-1}}\) 和 \(\boldsymbol{b}^{(l)} \in \mathbb{R}^{n_l}\) 分别是该层的权重矩阵和偏置向量，\(\boldsymbol{a}^{(l-1)}\) 是前一层的激活向量。输出则为

\[
\boldsymbol{a}^{(l)} = f^{(l)}(\boldsymbol{z}^{(l)}), \quad (243)
\]

其中 \( f^{(l)} \) 是激活函数。反向传播从计算输出层的误差开始，

\[
\boldsymbol{\delta}^{(L)} = \frac{\partial \ell}{\partial \boldsymbol{a}^{(L)}} \odot f'^{(L)}(\boldsymbol{z}^{(L)}), \quad (244)
\]

其中 \( f'^{(L)}(\cdot) \) 是激活函数的导数。对于隐藏层，误差递归地传播为

\[
\boldsymbol{\delta}^{(l)} = (\boldsymbol{W}^{(l+1)})^\top \boldsymbol{\delta}^{(l+1)} \odot f'^{(l)}(\boldsymbol{z}^{(l)}). \quad (245)




然后计算权重和偏置更新的梯度为

$$
\frac{\partial \mathcal{L}}{\partial W^{(l)}} = \delta^{(l)}(a^{(l-1)})^\top
$$ (246)

和

$$
\frac{\partial \mathcal{L}}{\partial b^{(l)}} = \delta^{(l)},
$$ (247)

分别。梯度下降的动态深受损失面曲率的影响，由黑塞矩阵封装

$$
H(\theta) = \nabla_\theta^2 \mathcal{L}(\theta).
$$ (248)

对于较小的步长 \(\eta\)，损失函数的变化可近似为

$$
\Delta \mathcal{L} \approx -\eta \| \nabla_\theta \mathcal{L}(\theta) \|^2 + \frac{\eta^2}{2} (\nabla_\theta \mathcal{L}(\theta))^\top H(\theta) \nabla_\theta \mathcal{L}(\theta).
$$ (249)

这表明，收敛性不仅由梯度幅值决定，还取决于沿梯度方向的损失面曲率。\(H(\theta)\) 的特征值 \(\lambda_1, \lambda_2, \dots, \lambda_d\) 决定了局部几何，较大的条件数 \(\kappa = \frac{\lambda_{max}}{\lambda_{min}}\) 由于病态而减慢收敛。随机梯度下降（SGD）通过基于单个数据样本 \((x_i, y_i)\) 计算更新来修改标准梯度下降，从而得到

$$
\theta^{(k+1)} = \theta^{(k)} - \eta \nabla_\theta \ell(\theta; x_i, y_i).
$$ (250)

虽然 SGD 将方差引入更新中，但这种随机性有助于逃离以零梯度但混合曲率为特征的鞍点。为了平衡计算效率和稳定性，小批量 SGD 在随机选定的大小为 \(|\mathcal{B}|\) 的子集 \(\mathcal{B} \subset \{1, \dots, N\}\) 上计算梯度，得到

$$
\nabla_\theta \mathcal{L}_\mathcal{B}(\theta) = \frac{1}{|\mathcal{B}|} \sum_{i \in \mathcal{B}} \nabla_\theta \ell(\theta; x_i, y_i).
$$ (251)

动量方法通过融入过去梯度的记忆来增强收敛性。速度项

$$
v^{(k+1)} = \gamma v^{(k)} + \eta \nabla_\theta \mathcal{L}(\theta)
$$ (252)

累积梯度信息，参数更新为

$$
\theta^{(k+1)} = \theta^{(k)} - v^{(k+1)}.
$$ (253)

在 \(H(\theta)\) 的特征空间中分析动量，其中 \(H = Q \Lambda Q^\top\)，揭示了每个特征方向上的有效步长为

$$
\eta_{\text{eff}, i} = \frac{\eta}{1 - \gamma \lambda_i},
$$ (254)

这表明动量在低曲率方向上加速收敛，同时抑制高曲率方向上的振荡。自适应梯度方法（如 AdaGrad、RMSProp 和 Adam）为单个参数优化学习率。在 AdaGrad 中，自适应学习率为

$$
\eta_i^{(k+1)} = \frac{\eta}{\sqrt{G_{ii}^{(k+1)} + \epsilon}},
$$ (255)

其中

$$
G_{ii}^{(k+1)} = G_{ii}^{(k)} + (\nabla_{\theta_i} \mathcal{L}(\theta))^2.
$$ (256)

RMSProp 使用指数加权平均对其进行修改

$$
G_{ii}^{(k+1)} = \beta G_{ii}^{(k)} + (1 - \beta) (\nabla_{\theta_i} \mathcal{L}(\theta))^2.
$$ (257)

Adam 将 RMSProp 与动量相结合，其中一阶矩和二阶矩为

$$
m^{(k+1)} = \beta_1 m^{(k)} + (1 - \beta_1) \nabla_\theta \mathcal{L}(\theta)
$$

和

$$
v^{(k+1)} = \beta_2 v^{(k)} + (1 - \beta_2) \left( \nabla_\theta \mathcal{L}(\theta) \right)^2.
$$

偏差校正得到

$$
\hat{m}^{(k+1)} = \frac{m^{(k+1)}}{1 - \beta_1^k}, \quad \hat{v}^{(k+1)} = \frac{v^{(k+1)}}{1 - \beta_2^k}.
$$

最终参数更新为

$$
\theta^{(k+1)} = \theta^{(k)} - \eta \frac{\hat{m}^{(k+1)}}{\sqrt{\hat{v}^{(k+1)} + \epsilon}}.
$$

总之，梯度下降及其变体为优化神经网络参数提供了丰富的框架。虽然标准梯度下降提供了一种基本方法，但动量和自适应梯度等高级方法通过根据损失面的景观和训练动态定制更新，显著增强了收敛性。

### 6.2.1 SGD（随机梯度下降）优化器

文献综述：Lauand 和 Meyn (2025) [175] 使用马尔可夫动力学为 SGD 建立了理论框架，以改进收敛特性。它将准周期线性系统集成到 SGD 中，增强了其在非平稳环境中的鲁棒性。Maranjyan 等人 (2025) [176] 开发了一种异步 SGD 算法，满足时间复杂度的理论下界。它引入了基于环的通信，以优化并行执行而不降低收敛率。Gao 和 Gündüz (2025) [177] 提出了一种基于随机梯度下降的方法，用于优化无线网络中的图神经网络。它严谨地分析了随机优化问题，并证明了其收敛保证。Yoon 等人 (2025) [178] 研究了多代理学习中的联邦 SGD，并推导了其通信效率的理论保证，同时实现平衡。Verma 和 Maiti (2025) [179] 为基于 SGD 的优化器提出了周期性学习率（使用正弦和余弦函数），理论上证明了其在稳定性和计算效率方面的优势。Borowski 和 Miasojedow (2025) [180] 扩展了 Robbins-Monro 定理以分析 SGD 的收敛保证，深化了对投影随机逼近算法的理论理解。Dong 等人 (2025) [181] 将随机梯度下降应用于脑网络建模，为优化神经控制策略提供了理论框架。Jiang 等人 (2025) [182] 分析了去中心化 SGD 中的偏差-方差权衡，证明了收敛率，并为有偏梯度提出了误差纠正机制。Sonobe 等人 (2025) [183] 将 SGD 与贝叶斯推断相联系，提出了随机优化方法如何逼近后验分布的理论分析。Zhang 和 Jia (2025) [184] 考察了强化学习中策略梯度的理论特性，证明了随机最优控制问题的收敛保证。

随机梯度下降（SGD）优化器是一种迭代方法，旨在通过沿负梯度方向更新参数向量 \(\mathbf{w}\) 来最小化目标函数 \(f(\mathbf{w})\)。基本优化问题可表示为

$$
\min_{\mathbf{w}} f(\mathbf{w}),
$$

其中

$$
f(\mathbf{w}) = \frac{1}{N} \sum_{i=1}^N \ell(\mathbf{w}; \mathbf{x}_i, y_i)
$$

表示从数据集 \(\{(\mathbf{x}_i, y_i)\}_{i=1}^N\) 构建的经验风险。这里，\(\ell(\mathbf{w}; \mathbf{x}_i, y_i)\) 表示损失函数，\(\mathbf{w} \in \mathbb{R}^d\) 是参数向量，\(N\) 是数据集大小，\(f(\mathbf{w})\) 近似真实总体风险

\(\mathbb{E}_{\mathbf{x},y}[\ell(\mathbf{w}; \mathbf{x}, y)].\) (264)

标准梯度下降涉及更新规则

\(\mathbf{w}^{(t+1)} = \mathbf{w}^{(t)} - \eta \nabla f(\mathbf{w}^{(t)}),\) (265)

其中 \(\eta > 0\) 是学习率，且

\(\nabla f(\mathbf{w}) = \frac{1}{N} \sum_{i=1}^N \nabla \ell(\mathbf{w}; \mathbf{x}_i, y_i)\) (266)

是全梯度。然而，对于大规模数据集，计算 \(\nabla f(\mathbf{w})\) 在计算上变得不可行，这促使采用随机逼近。随机逼近依赖于使用单个数据点或一小批数据点来估计梯度 \(\nabla f(\mathbf{w})\) 的想法。表示迭代 \(t\) 中采样的随机索引为 \(i_t\)，随机梯度可写为

\(\widehat{\nabla} f(\mathbf{w}^{(t)}) = \nabla \ell(\mathbf{w}^{(t)}; \mathbf{x}_{i_t}, y_{i_t}).\) (267)

因此，更新规则变为

\(\mathbf{w}^{(t+1)} = \mathbf{w}^{(t)} - \eta \widehat{\nabla} f(\mathbf{w}^{(t)}).\) (268)

对于大小为 \(m\) 的小批量 \(\mathcal{B}_t\)，随机梯度推广为

\(\widehat{\nabla} f(\mathbf{w}^{(t)}) = \frac{1}{m} \sum_{i \in \mathcal{B}_t} \nabla \ell(\mathbf{w}^{(t)}; \mathbf{x}_i, y_i).\) (269)

\(\widehat{\nabla} f(\mathbf{w})\) 的一个重要性质是其无偏性：

\(\mathbb{E}[\widehat{\nabla} f(\mathbf{w})] = \nabla f(\mathbf{w}).\) (270)

然而，\(\widehat{\nabla} f(\mathbf{w})\) 的方差定义为

\(\text{Var}[\widehat{\nabla} f(\mathbf{w})] = \mathbb{E}[\|\widehat{\nabla} f(\mathbf{w}) - \nabla f(\mathbf{w})\|^2],\) (271)

将随机噪声引入更新中，其中 \(\text{Var}[\widehat{\nabla} f(\mathbf{w})] \approx \frac{\sigma^2}{m}\) 且

\(\sigma^2 = \mathbb{E}[\|\nabla \ell(\mathbf{w}; \mathbf{x}) - \nabla f(\mathbf{w})\|^2]\) (272)

是梯度的方差。为了分析 SGD 的收敛特性，我们假设 \(f(\mathbf{w})\) 是 \(L\)-光滑的，即

\(\|\nabla f(\mathbf{w}_1) - \nabla f(\mathbf{w}_2)\| \leq L \|\mathbf{w}_1 - \mathbf{w}_2\|,\) (273)

且 \(f(\mathbf{w})\) 下界由 \(f^* = \inf_{\mathbf{w}} f(\mathbf{w})\) 界定。使用泰勒展开，我们可以写成

\(f(\mathbf{w}^{(t+1)}) \leq f(\mathbf{w}^{(t)}) - \eta \|\nabla f(\mathbf{w}^{(t)})\|^2 + \frac{\eta^2 L}{2} \|\widehat{\nabla} f(\mathbf{w}^{(t)})\|^2.\) (274)

取期望得到

\(\mathbb{E}[f(\mathbf{w}^{(t+1)})] \leq \mathbb{E}[f(\mathbf{w}^{(t)})] - \frac{\eta}{2} \mathbb{E}[\|\nabla f(\mathbf{w}^{(t)})\|^2] + \frac{\eta^2 L}{2} \sigma^2,\) (275)





表明收敛速度取决于学习率 \(\eta\)、平滑度常数 \(L\) 与梯度方差 \(\sigma^2\) 之间的相互作用。当 \(\eta\) 足够小时，收敛中的主导项为 \(-\frac{\eta}{2} \mathbb{E}[\|\nabla f(\mathbf{w}^{(t)})\|^2]\)，从而导致 \(f(\mathbf{w}^{(t)})\) 单调下降。在强凸情况下，若 \(f(\mathbf{w})\) 满足

\(f(\mathbf{w}_1) \ge f(\mathbf{w}_2) + \nabla f(\mathbf{w}_2)^\top (\mathbf{w}_1 - \mathbf{w}_2) + \frac{\mu}{2} \|\mathbf{w}_1 - \mathbf{w}_2\|^2\) (276)

其中 \(\mu > 0\)，SGD 实现线性收敛。具体来说，

\(\mathbb{E}[\|\mathbf{w}^{(t)} - \mathbf{w}^*\|^2] \le (1 - \eta \mu)^t \|\mathbf{w}^{(0)} - \mathbf{w}^*\|^2 + \frac{\eta \sigma^2}{2\mu}.\) (277)

对于非凸函数，其中 \(\nabla^2 f(\mathbf{w})\) 既可能有正特征值也可能有负特征值，SGD 可能收敛到局部最小化点或鞍点。随机性在逃离严格鞍点 \(\mathbf{w}_s\) 中起着关键作用，在该点 \(\nabla f(\mathbf{w}_s) = 0\) 但 \(\lambda_{\min}(\nabla^2 f(\mathbf{w}_s)) < 0\)。

### 6.2.2 Adam（自适应矩估计）优化器

文献综述：Kingma 和 Ba (2014) [165] 提出了 Adam 优化器。他们将 Adam 阐述为一种自适应梯度优化方法，结合了动量和自适应学习率技术。作者严格证明了其相对于传统优化器（如 SGD 和 RMSProp）的优势。Reddy 等人 (2019) [166] 分析了 Adam 的收敛特性，并找出了其可能无法收敛的情况。作者提出了 AMSGrad，这是 Adam 的改进型，能够保证更好的理论收敛行为。Jin 等人 (2024) [167] 提出了 MIAdam（多重积分 Adam），该方法修改了 Adam 的更新规则以增强泛化能力。作者从理论和实证上证明了其在避免尖锐极小值方面的有效性。Adly 等人 (2024) [168] 提出了 EXAdam，这是对 Adam 的改进，在参数更新中使用交叉矩。这在保持 Adam 自适应性的同时实现了更快的收敛。理论推导表明更新中的方差减少有所改进。Liu 等人 (2024) [169] 为 Adam 应用于线性反问题时的收敛性提供了严格的数学证明。作者将 Adam 的收敛速度与标准梯度下降进行了比较，并证明了其在含噪环境下的效率。Yang (2025) [170] 通过引入有偏随机优化框架推广了 Adam。作者表明，在特定条件下，Adam 的偏差校正步骤不足，导致在强凸函数上收敛效果不佳。Park 和 Lee (2024) [171] 开发了 SMMF，这是一种新型的 Adam 变体，对动量张量进行因子分解，从而减少内存占用。理论界限表明，SMMF 在保持 Adam 自适应性的同时提高了效率。Mahjoubi 等人 (2025) [172] 对深度学习模型中的 Adam、SGD 和 RMSProp 进行了比较分析。该研究展示了 Adam 胜过其他方法的场景，特别是在高维优化问题中。Seini 和 Adam (2024) [173] 考察了 Adam 优化框架如何适应人机协作学习模型。该论文为将 Adam 集成到 AI 驱动的教育平台提供了理论基础。Teessar (2024) [174] 讨论了 Adam 在调查和社会科学研究中的应用，其中自适应优化用于微调问卷分析模型。这凸显了 Adam 在深度学习之外的多功能性。

自适应矩估计（Adam）优化器可被视为一种精巧的混合优化算法，它结合了基于动量的方法和自适应学习率技术的元素，因此成为复杂机器学习模型（特别是深度学习模型）优化中的基石。Adam 的公式核心在于在每次参数更新时计算并使用损失函数梯度的一阶矩和二阶矩（即均值和方差）。这一过程根据每个参数梯度各自的统计特性，有效地调整了每个参数的学习率。基于矩的调整能够提供对目标函数条件数差和梯度噪声等问题的鲁棒性，这些问题在大规模优化中普遍存在。

从数学角度看，在每次迭代 \( t \) 中，Adam 优化器根据梯度 \( g_t \) 更新参数向量 \( \theta_t \in \mathbb{R}^n \)，其中 \( n \) 是模型的参数数量，\( g_t \) 是目标函数对 \( \theta_t \) 的梯度，即 \( g_t = \nabla_\theta f(\theta_t) \)。从本质上讲，Adam 计算两个不同的量：一阶矩估计 \( m_t \) 和二阶矩估计 \( v_t \)，它们分别是梯度和平方梯度的递归移动平均值。

一阶矩估计 \( m_t \) 由以下公式给出

\( m_t = \beta_1 m_{t-1} + (1 - \beta_1)g_t, \) (278)

其中 \( \beta_1 \in [0, 1) \) 是一阶矩的衰减率。该递归方程代表梯度的加权移动平均，旨在捕捉优化过程中的 *方向性动量*。通过引入一阶矩，Adam 积累关于历史梯度的信息，这有助于减轻振荡并稳定收敛方向。项 \( (1 - \beta_1) \) 确保最近的梯度 \( g_t \) 在 \( m_t \) 的计算中获得更大的权重。同样，二阶矩估计 \( v_t \)（代表平方梯度的指数衰减平均值）按以下公式更新

\( v_t = \beta_2 v_{t-1} + (1 - \beta_2)g_t^2, \) (279)

其中 \( \beta_2 \in [0, 1) \) 是二阶矩的衰减率。平方梯度的这一移动平均捕捉了每次迭代梯度的 *方差*。因此，二阶矩 \( v_t \) 充当目标函数 *曲率* 的估计，这使优化器能够相应地调整每个参数的步长。具体来说，\( v_t \) 的较大值对应于经历高梯度方差的参数，表明需要较小的更新以防止过冲，而 \( v_t \) 的较小值对应于低梯度方差的参数，在这些参数中较大的更新是合适的。这种机制类似于根据损失函数的局部几何自动为每个参数调节学习率。在初始化时，\( m_t \) 和 \( v_t \) 通常都设置为零。这种初始化引入了对零的偏差，尤其是在初始时间步，导致矩估计在早期迭代中表现不足。为了纠正这种偏差，引入了 *偏差校正* 项。偏差校正后的一阶矩 \( \hat{m}_t \) 由以下公式给出

\( \hat{m}_t = \frac{m_t}{1 - \beta_1^t}, \) (280)

偏差校正后的二阶矩 \( \hat{v}_t \) 由以下公式给出

\( \hat{v}_t = \frac{v_t}{1 - \beta_2^t}. \) (281)

这些校正的目的是抵消 \( m_t \) 和 \( v_t \) 由于初始化为零而低估真实值的初始趋势。随着迭代的推进，偏差校正项变得不那么重要，矩估计收敛到其真实值，从而允许更准确的参数更新。参数 \( \theta_t \) 的实际更新规则通过分别使用偏差校正后的一阶矩和二阶矩估计 \( \hat{m}_t \) 和 \( \hat{v}_t \) 确定。更新方程由以下公式给出

\( \theta_{t+1} = \theta_t - \eta \frac{\hat{m}_t}{\sqrt{\hat{v}_t} + \epsilon}, \) (282)

其中 \( \eta \) 是全局学习率，\( \epsilon \) 是一个小常数（通常为 \( 10^{-8} \)），添加到分母中以保证数值稳定性。该更新规则同时结合了动量（通过 \( \hat{m}_t \)）和自适应学习率（通过 \( \hat{v}_t \)）。因子 \( \sqrt{\hat{v}_t} + \epsilon \) 尤为关键，因为它确保梯度方差较大的参数（即 \( v_t \) 中数值较大的参数）获得较小的更新，而梯度方差较小的参数（即 \( v_t \) 中数值较小的参数）获得较大的



更新，从而防止在高方差区域出现发散。

Adam 中的学习率调整本质上是动态的，因为它由二阶矩估计 \(\hat{v}_t\) 控制，这意味着 Adam 为每个参数具有每参数学习率。对于每个参数，学习率与其对应的二阶矩估计 \(\hat{v}_t\) 的平方根成反比，从而产生 *自适应学习率*。这使得 Adam 能够在高度非凸优化景观中有效工作，因为它在梯度表现出高方差的方向上降低学习率，从而稳定更新，并在梯度方差较低的地方提高学习率，加速收敛。在 Adam 应用于凸目标函数的情况下，收敛性可以在数学上进行分析。在标准假设下，例如梯度有界且学习率递减，可以通过证明以下内容来展示 Adam 的收敛性：

\(\sum_{t=1}^{\infty} \eta_t^2 < \infty \quad \text{and} \quad \sum_{t=1}^{\infty} \eta_t = \infty, \quad (283)\)

其中 \(\eta_t\) 是时间步 \(t\) 的学习率。第一个条件确保学习率衰减足够快以保证收敛，而第二个条件确保学习率不会衰减得太快，从而允许在算法推进过程中持续更新。然而，Adam 并非没有局限性。一个显著的问题源于二阶矩估计 \(v_t\) 可能衰减得太快，导致在梯度方差相对较低的区域出现过于激进的更新。为了解决这个问题，引入了 AMSGrad 变体。AMSGrad 通过将 \(v_t\) 替换为以下内容来修改二阶矩更新规则：

\(\hat{v}_t^{\text{new}} = \max(\hat{v}_{t-1}, \hat{v}_t), \quad (284)\)

从而确保 \(\hat{v}_t\) 永不减少，这有助于防止优化器在二阶矩估计可能计算错误的情况下进行过大的更新。通过强制 \(\hat{v}_t\) 增加或保持不变，AMSGrad 减少了大型、不稳定的参数更新的可能性，从而提高了优化器的稳定性和收敛性，特别是在困难或病态的优化问题中。此外，Adam 的进一步扩展（如 AdaBelief）通过引入基于信念的机制来修正矩估计，对二阶矩估计进行了额外的修改。具体来说，AdaBelief 以一种基于梯度方向 *信念* 进行调整的方式来估计二阶矩 \(\hat{v}_t\)，在梯度可能稀疏或噪声较大的情况下提供了进一步的稳定性。这些创新凸显了 Adam 及其变体在优化各种机器学习任务中的复杂损失函数方面的灵活性。

最终，Adam 优化器是一种高度精巧、数学严谨的优化算法，有效地结合了动量和自适应学习率。通过同时使用梯度的一阶矩和二阶矩，Adam 动态调整参数更新，为非凸、高维目标函数提供了一个强大且高效的优化框架。偏差校正与优化器的自适应特性相结合，使其能够在广泛的问题设置中有效工作，使其成为许多机器学习和深度学习应用的首选方法。Adam 背后的数学严谨性确保其仍然是一种高度稳定且高效的优化技术，能够克服机器学习模型中大规模和噪声梯度信息带来的许多挑战。

### 6.2.3 RMSProp（根均方传播）优化器

文献综述：Bensaid 等人 (2024) [155] 对 RMSProp 在非凸设置下的收敛特性进行了严谨分析。它利用稳定性理论来考察 RMSProp 如何适应不同的损失景观，并展示了适应性在确保收敛中发挥的关键作用。该研究从理论上阐明了 RMSProp 在平滑噪声梯度方面的效率。Liu 和 Ma (2024) [156] 研究了自适应优化器（包括 RMSProp）中观察到的损失振荡。它解释了 RMSProp 的指数移动平均机制如何导致这种现象，并提出了一种关于调整超参数以减轻振荡的新视角。Li (2024) [157] 探讨了自适应优化器的基本理论特性，重点关注 RMSProp。它严谨地考察了平滑条件与 RMSProp 自适应特性之间的相互作用，展示了它如何在稳定性和收敛速度之间取得平衡。Heredia (2024) [158] 提出了一种使用积分微分方程分析 RMSProp 的新数学框架。该模型提供了更深层的理论洞察，阐明了 RMSProp 如何以不同于 AdaGrad 和 Adam 的方式更新梯度，特别是在梯度平滑方面。Ye (2024) [159] 讨论了包括 RMSProp 在内的预处理方法如何增强梯度下降优化。它解释了为什么 RMSProp 的自适应学习率在高维设置中有益，并为其在正则化优化问题中的有效性提供了理论依据。Compagnoni 等人 (2024) [160] 采用随机微分方程 (SDEs) 来建模 RMSProp 和其他自适应优化器的行为。它提供了关于噪声如何影响优化过程以及 RMSProp 如何适应不同梯度景观的新理论洞察。Yao 等人 (2024) [161] 对包括 RMSProp 在内的一阶优化方法进行了系统响应曲线分析。作者们为 RMSProp 发展出一个动态方程，解释了其在深度学习任务中的稳定性和有效性。Wen 和 Lei (2024) [162] 探索了一种将 RMSProp 风格的更新与 ADMM 方法相结合的替代优化框架。它为 RMSProp 在非凸优化问题中的收敛提供了理论保证。Hannibal 等人 (2024) [163] 批评了包括 RMSProp 在内的流行优化器的收敛特性。它严谨地证明，在某些设置下，RMSProp 可能不会导致全局最小值，强调了超参数调整的重要性。Yang (2025) [164] 通过分析随机梯度更新中偏差的影响，扩展了对类似 RMSProp 的自适应优化器的理论理解。它对偏差如何影响收敛进行了严谨的数学处理。

根均方传播（RMSProp）优化器是梯度下降算法的一种复杂变体，它在非线性、非凸优化问题中为每个参数自适应地调整学习率。标准梯度下降的根本问题在于恒定学习率 \(\eta\)，它无法考虑参数空间不同方向中梯度幅值的变化。这种缺乏适应性会导致优化效率低下，其中大梯度可能导致过冲，而小梯度导致收敛缓慢。RMSProp 通过根据历史梯度幅值动态调整学习率来解决这个问题，提供了一种更定制、更高效的方法。考虑目标函数 \(f(\theta)\)，其中 \(\theta \in \mathbb{R}^n\) 是我们旨在优化的参数向量。令 \(\nabla f(\theta)\) 表示 \(f(\theta)\) 关于 \(\theta\) 的梯度，即偏导数向量：

```
\(\nabla f(\theta) = \left[ \frac{\partial f(\theta)}{\partial \theta_1}, \frac{\partial f(\theta)}{\partial \theta_2}, \cdots, \frac{\partial f(\theta)}{\partial \theta_n} \right]^T .\) (285)
```

在传统梯度下降中，\(\theta\) 的更新规则为：

```
\(\theta_{t+1} = \theta_t - \eta \nabla f(\theta_t),\) (286)
```

其中 \(\eta\) 是学习率，一个标量常数。然而，这种方法没有考虑到参数空间中不同方向上的梯度幅值可能存在显著差异的事实，尤其是在高维非凸函数中。RMSProp 优化器通过根据历史梯度幅值的比例为每个参数自适应地调整学习率来引入解决方案。RMSProp 中的关键修改是引入每个参数 \(\theta_i\) 的平方梯度运行平均值，表示为 \(E[g^2]_{i,t}\)，它捕捉了随时间推移的梯度累积幅值。\(E[g^2]_{i,t}\) 的更新规则由指数移动平均公式给出：

```
\(E[g^2]_{i,t} = \beta E[g^2]_{i,t-1} + (1 - \beta)g_{i,t}^2,\) (287)
```



其中 \( g_{i,t} = \frac{\partial f(\theta_t)}{\partial \theta_i} \) 是目标函数关于参数 \( \theta_i \) 在时间步 \( t \) 处的梯度，\( \beta \) 是衰减因子，通常设置为接近 1 的值（例如，\( \beta = 0.9 \)）。这个递归关系允许梯度历史影响当前更新，同时指数式地遗忘较旧的梯度信息。\( \beta \) 的值决定了平方梯度的记忆，较高的 \( \beta \) 值会给过去的梯度更多权重。RMSProp 中 \( \theta_i \) 的更新如下：

\(\theta_{i,t+1} = \theta_{i,t} - \frac{\eta}{\sqrt{E[g^2]_{i,t} + \epsilon}} g_{i,t}, \quad (288)\)

其中 \( \epsilon \) 是一个微小的正常数（通常 \( \epsilon = 10^{-8} \)），引入它是为了避免除以零并确保数值稳定性。项 \(\frac{1}{\sqrt{E[g^2]_{i,t} + \epsilon}}\) 根据平方梯度历史的幅度，动态调整每个参数的学习率。这种调整使 RMSProp 能够在历史梯度较小的方向上迈出更大的步长，在历史梯度较大的方向上迈出更小的步长，从而实现更稳定、更高效的优化过程。

从数学角度看，RMSProp 相对于传统梯度下降的关键优势在于其能够根据目标函数的局部几何特性自适应地调整学习率。在目标函数陡峭（梯度较大）的区域，RMSProp 通过除以 \(\sqrt{E[g^2]_{i,t}}\) 降低有效学习率，从而减轻步长过大（overshooting）的风险。相反，在梯度较小的平坦区域，RMSProp 会提高学习率，从而实现更快的收敛。这种自调节机制在高维优化任务中至关重要，因为不同方向上的梯度幅度可能相差很大，这在涉及神经网络的深度学习任务中很常见。RMSProp 中使用的平方梯度指数移动平均类似于一种局部归一化形式，其中每个参数都按其梯度平方运行平均值的倒数进行缩放。这种归一化确保优化器不会对任何特定方向的梯度过于敏感，从而稳定优化过程。更正式地说，如果目标函数 \( f(\theta) \) 沿某些方向表现出尖锐的曲率，RMSProp 会通过缩小这些方向上的步长来减轻此类曲率的影响。这种缩放行为可以被视为一种梯度再加权形式，其中每个参数梯度的影响受其历史行为的调制，使优化器对病态优化问题更具鲁棒性。引入 \( \epsilon \) 确保分母永远不会变为零，即使某个参数 \( \theta_i \) 的平方梯度历史变得极小也是如此。这对于保持算法的数值稳定性至关重要，特别是在梯度可能在许多迭代中消失或变得极小的场景中，如在训练非常深的神经网络等某些深度学习应用中所见。通过为学习率提供一个微小的非零下界，\( \epsilon \) 确保更新保持平滑且可预测。

RMSProp 的性能在很大程度上受 \( \beta \) 选择的影响，\( \beta \) 控制着长期历史与最近梯度信息之间的权衡。当 \( \beta \) 接近 1 时，优化器更多地依赖历史梯度，这有助于捕捉优化景观中的长期趋势。另一方面，较小的 \( \beta \) 值使优化器能够更灵敏地响应最近的梯度变化，这在高度非平稳环境或快速变化的优化景观中可能有益。在深度学习背景下，RMSProp 特别适用于优化具有复杂、高维参数空间的目标函数，例如训练深度神经网络时遇到的情况。此类目标函数的非凸性通常会导致网络不同层之间的梯度幅度存在显著差异。RMSProp 通过基于历史梯度调整学习率来帮助平衡这些层之间的更新，确保所有层都能获得适当的更新，而不会被任何单一层的大梯度所主导。这种适应性有助于防止梯度爆炸或梯度消失，这是深度学习优化中的常见问题。

总结来说，RMSProp 通过基于每个参数的历史平方梯度自适应调整学习率，提供了一种强健且高效的优化技术。平方梯度历史的指数衰减使 RMSProp 能够在稳定性与适应性之间取得平衡，防止步长过大并促进非凸优化问题中的更快收敛。引入 \(\epsilon\) 确保了数值稳定性，而参数 \(\beta\) 则在控制过去梯度影响方面提供了灵活性。这使得 RMSProp 特别适合高维优化任务，尤其在深度学习应用中，参数空间非常广阔，且各维度的梯度幅度可能存在显著差异。通过有效归一化梯度并动态调整学习率，RMSProp 显著提升了基于梯度的优化方法的效率和稳定性。

## 6.3 过拟合与正则化技术

文献综述：Goodfellow (2016) 等人 [112] 对深度学习进行了全面介绍，其中包含对过拟合和正则化技术的深入讨论。书中解释了 L1/L2 正则化、Dropout、批量归一化和数据增强等方法，这些方法有助于提高泛化能力。作者探讨了偏差-方差权衡以及减少神经网络过拟合的实际解决方案。Hastie et al. (2009) [129] 讨论了统计学习模型中的过拟合问题，特别是回归和分类。本书涵盖了岭回归（L2）和 Lasso（L1）等正则化技术，以及用于防止过拟合的交叉验证技术。这是理解机器学习中模型复杂度控制的基础。Bishop (2006) [115] 在其著作中提供了机器学习模型的深入数学基础，特别关注贝叶斯推断、早停和权重衰减等正则化方法。书中强调了正则化的概率解释，展示了如何通过贝叶斯模型中的先验分布来减轻过拟合。Murphy (2012) [130] 在其著作中呈现了一种贝叶斯机器学习方法，从概率视角介绍了正则化技术。书中讨论了惩罚方法、贝叶斯回归和变分推断，作为控制模型复杂度和防止过拟合的工具。本书对于希望了解机器学习模型不确定性估计的人来说非常有用。Srivastava et al. (2014) [131] 提出了 Dropout，这是一种广泛使用的深度学习正则化技术。作者展示了在训练期间随机丢弃单元如何减少神经元的共适应，从而增强模型的泛化能力。该技术仍然是现代神经网络训练流程的关键部分。Zou and Hastie (2005) [132] 提出了 Elastic Net，即 L1（Lasso）和 L2（Ridge）正则化的组合，解决了 Lasso 在处理相关特征时的局限性。它在高维数据中特别有用，因为在高维数据中，特征选择和正则化至关重要。Vapnik (1995) [133] 在其著作中介绍了统计学习理论和 VC 维，后者用于量化模型复杂度。它提供了解释过拟合原因以及正则化约束如何降低泛化误差的数学框架。它构成了支持向量机（SVM）和结构风险最小化的理论基础。Ng (2004) [134] 比较了 L1（Lasso）和 L2（Ridge）正则化，展示了它们对特征选择和模型稳定性的影响。研究表明，L1 正则化对稀疏模型更有效，而 L2 在高度相关的特征空间中能更好地保留信息。这项工作对于为特定数据集选择合适的正则化技术至关重要。Li (2025) [135] 探索了在高维临床试验数据中应用正则化技术，使用集成方法、贝叶斯优化和深度学习正则化技术。文章强调了正则化在防止医疗 AI 过拟合中的实际应用。Yasuda (2025) [136] 专注于混合机器学习模型中的正则化，特别是高斯-离散 RBM。它扩展了 L1/L2 惩罚和 Dropout 策略，以提高深度生成模型的泛化能力。对于从事深度学习架构和无监督学习的人来说，这很有价值。

神经网络中的过拟合是一个关键问题，模型会过度拟合训练数据，不仅捕捉真实的基本模式，还会捕捉噪声和异常值


存在于数据中。这导致对未见数据的泛化能力较差，从而得到一个模型，其训练误差较低但测试误差较高。从数学上讲，考虑一个数据集 $\mathcal{D} = \{(\mathbf{x}_i, y_i)\}_{i=1}^N$，其中 $\mathbf{x}_i \in \mathbb{R}^d$ 表示每个数据点的输入特征向量，$y_i \in \mathbb{R}$ 表示相应的目标值。目标是拟合一个由权重 $\mathbf{w} \in \mathbb{R}^M$ 参数化的神经网络模型 $f(\mathbf{x}; \mathbf{w})$，其中 $M$ 表示模型中的参数数量。模型的目标是最小化经验风险，即预测值与真实目标值之间的均方误差：

$$\hat{R}(\mathbf{w}) = \frac{1}{N} \sum_{i=1}^N L(f(\mathbf{x}_i; \mathbf{w}), y_i)$$ (289)

其中 $L$ 表示损失函数，通常为平方误差 $L(\hat{y}_i, y_i) = (\hat{y}_i - y_i)^2$。在此框架下，神经网络试图在训练集上最小化经验风险。然而，真正的目标是最小化期望风险 $R(\mathbf{w})$，它反映了模型在数据真实分布 $P(\mathbf{x}, y)$ 上的性能。该期望风险由以下公式给出：

$$R(\mathbf{w}) = \mathbb{E}_{\mathbf{x},y}[L(f(\mathbf{x}; \mathbf{w}), y)]$$ (290)

当模型将 $\hat{R}(\mathbf{w})$ 最小化到过小的值，但 $R(\mathbf{w})$ 仍然很大时，就会发生过拟合，这表明模型拟合了训练数据中的噪声，而非捕捉真实数据分布。这种差异源于过于复杂的模型，它学习的是记忆训练数据，而非对不同输入进行泛化。对过拟合现象的一个基本洞察来自泛化误差的偏差-方差分解。模型对真实目标函数 $g(\mathbf{x})$ 的预测 $\hat{f}(\mathbf{x})$ 的总误差可分解为：

$$\mathcal{E} = \mathbb{E}[(g(\mathbf{x}) - \hat{f}(\mathbf{x}))^2] = \text{Bias}^2(\hat{f}(\mathbf{x})) + \text{Var}(\hat{f}(\mathbf{x})) + \sigma^2$$ (291)

其中 $\text{Bias}^2(\hat{f}(\mathbf{x}))$ 表示预期模型预测与真实函数之间的平方差，$\text{Var}(\hat{f}(\mathbf{x}))$ 是模型在不同训练集上的预测方差，$\sigma^2$ 是由于数据固有噪声而不可消除的误差。在过拟合的背景下，模型通常表现出低偏差（因为它很好地拟合了训练数据）但高方差（因为它对训练数据的波动非常敏感）。因此，正则化技术旨在降低模型的方差，同时保持其捕捉数据中真实潜在关系的能力，从而提高泛化能力。减轻过拟合最流行的方法之一是 L2 正则化（也称为权重衰减），它基于权重的平方大小向损失函数添加惩罚项。正则化后的损失函数由以下公式给出：

$$\hat{R}_{\text{reg}}(\mathbf{w}) = \hat{R}(\mathbf{w}) + \lambda\|\mathbf{w}\|_2^2 = \hat{R}(\mathbf{w}) + \lambda \sum_{j=1}^M w_j^2$$ (292)

其中 $\lambda$ 是控制正则化强度的正常数。正则化损失函数关于权重的梯度为：

$$\nabla_\mathbf{w} \hat{R}_{\text{reg}}(\mathbf{w}) = \nabla_\mathbf{w} \hat{R}(\mathbf{w}) + 2\lambda\mathbf{w}$$ (293)

项 $2\lambda\mathbf{w}$ 引入了权重收缩，防止模型拟合过大的权重，从而通过降低模型复杂度来防止过拟合。这种正则化方法是控制模型容量的一种直接方式，通过惩罚大权重值，得到一个泛化性能更好的更简单模型。相比之下，L1 正则化基于权重的绝对值添加惩罚：

$$\hat{R}_{\text{reg}}(\mathbf{w}) = \hat{R}(\mathbf{w}) + \lambda\|\mathbf{w}\|_1 = \hat{R}(\mathbf{w}) + \lambda \sum_{j=1}^M |w_j|$$ (294)

L1 正则化损失函数的梯度为：

$$\nabla_{\mathbf{w}}\hat{R}_{\text{reg}}(\mathbf{w}) = \nabla_{\mathbf{w}}\hat{R}(\mathbf{w}) + \lambda \text{sgn}(\mathbf{w})$$

其中 sgn(w) 表示逐元素符号函数。L1 正则化具有一个独特的性质，即在权重中诱导稀疏性，这意味着它将许多权重驱动到恰好为零，从而有效地选择一个最重要特征的子集。这种特征选择机制在高维环境中特别有用，因为许多输入特征可能是无关的。一种更高级的正则化技术是丢弃法（dropout），它在训练期间随机停用一部分神经元。设 h_i 表示给定层中第 i 个神经元的激活值。在训练期间，丢弃法生成一个二元掩码 m_i，其采样自成功概率为 p 的伯努利分布，即 m_i ~ Bernoulli(p)，使得：

$$\mathbf{h}_i^{\text{drop}} = \frac{1}{p}\mathbf{m}_i \odot \mathbf{h}_i$$

其中 $\odot$ 表示逐元素乘法。系数 1/p 确保训练期间激活值的期望保持不变。丢弃法迫使网络学习冗余表示，减少对特定神经元的依赖并促进更好的泛化。通过训练具有共享权重的子网络集成，丢弃法有助于防止网络记忆训练数据，从而减少过拟合。早停法是防止过拟合的另一种技术，它涉及在验证误差开始增加时停止训练过程。模型在训练集上进行训练，但在单独的验证集上评估其性能。如果验证误差 R_val(t) 在若干个 epoch 后增加，则停止训练以防止进一步过拟合。从数学上讲，停止标准是：

$$t^* = \arg \min_t R_{\text{val}}(t)$$

其中 t* 表示验证误差达到最小值的 epoch。这种技术避免了在模型开始丧失泛化能力之后继续拟合训练数据的风险。数据增强通过对原始数据应用变换来人为扩大训练数据集。设 T = {T1, T2, ..., TK} 表示一组变换（例如旋转、缩放和平移）。对于每个训练样本 (xi, yi)，增强数据集 D' 由 K 个新样本组成：

$$\mathcal{D}' = \{ (T_k(\mathbf{x}_i), y_i) \mid i = 1, 2, \dots, N, k = 1, 2, \dots, K \}$$

这些变换创建新的、多样的样本，有助于模型更好地泛化，防止其过度拟合原始的、可能包含噪声的数据。数据增强在图像处理等领域特别有用，其中旋转和翻转等变换不会改变底层标签，但提供了额外的学习样本。批量归一化对每个小批量的激活值进行归一化，以减少内部协变量偏移并稳定学习过程。给定一个具有激活值 h_i 的小批量 \(\mathcal{B} = \{\mathbf{h}_i\}_{i=1}^m\)，小批量中激活值的均值和方差计算如下：

$$\mu_{\mathcal{B}} = \frac{1}{m} \sum_{i=1}^m \mathbf{h}_i, \quad \sigma_{\mathcal{B}}^2 = \frac{1}{m} \sum_{i=1}^m (\mathbf{h}_i - \mu_{\mathcal{B}})^2$$

归一化后的激活值如下给出：

$$\hat{\mathbf{h}}_i = \frac{\mathbf{h}_i - \mu_{\mathcal{B}}}{\sqrt{\sigma_{\mathcal{B}}^2 + \epsilon}}$$

其中 \(\epsilon\) 是一个用于数值稳定性的小常数。批量归一化有助于平滑优化景观，从而加快收敛速度，并通过防止模型在损失景观中陡峭、狭窄的极小值处陷入困境来减轻过拟合风险。

总之，过拟合是神经网络训练中的一个重大挑战，其防止需要一组旨在控制模型复杂度、提高泛化能力和降低对训练数据中噪声敏感度的技术的组合。L2 和 L1 正则化、丢弃法以及早停法等正则化方法，结合数据增强和批量归一化等策略，对于提高神经网络在未见数据上的性能并确保其不过度拟合训练集至关重要。这里概述的数学公式和优化策略为理解和缓解机器学习模型中的过拟合提供了详细且严谨的框架。

### 6.3.1 Dropout（丢弃法）

丢弃法（Dropout）是神经网络中的一种正则化技术，旨在解决过拟合问题，即模型在训练数据上表现良好，但在未见数据上无法泛化的情况。机器学习中过拟合的一般问题在于：当模型变得过于复杂、参数数量过多，并且学习的是对数据中的噪声建模，而非真实潜在模式时。这可能导致在新的、未见数据上泛化性能不佳。在神经网络的背景下，解决方案通常涉及 _正则化技术_，以惩罚复杂度并防止模型记忆数据。由 Geoffrey Hinton 等人提出的丢弃法，是一种通过在训练过程中引入随机性来正则化神经网络的独特且强大的方法，它迫使模型更好地泛化并防止过拟合。要理解丢弃法背后的数学原理，设 \( f_\theta(x) \) 表示带有参数 \(\theta\) 的神经网络对输入 \( x \) 的输出。训练期间的目标是最小化一个损失函数，该函数衡量预测输出与真实目标 \( y \) 之间的差异。在没有任何正则化的情况下，目标是最小化经验损失：

$$L_{\text{empirical}}(\theta) = \frac{1}{N} \sum_{i=1}^N \mathcal{L}(f_\theta(x_i), y_i)$$ (301)

其中 \( \mathcal{L}(f_\theta(x_i), y_i) \) 是损失函数（例如交叉熵或均方误差），\( N \) 是数据样本的数量。一个在没有正则化的情况下训练以最小化该损失函数的模型可能会过度拟合训练数据，捕捉噪声而非数据的底层分布。丢弃法通过在每次训练迭代中随机“丢弃”网络的一部分神经元来解决这个问题，这在数学上通过修改神经元的激活值来表示。

让我们考虑一个前馈神经网络，第 \( i \) 层神经元的一组激活值为 \( a_i \)，其计算方式为 \( a_i = f(Wx_i + b_i) \)，其中 \( W \) 表示权重矩阵，\( x_i \) 表示神经元的输入，\( b_i \) 表示偏置。在带有丢弃法的训练期间，为每个神经元引入一个随机伯努利变量 \( r_i \)，其中：

$$r_i \sim \text{Bernoulli}(p)$$ (302)

其中概率 \( p \) 表示保留概率（即神经元保持活跃的概率），而 \( 1 - p \) 表示神经元被“丢弃”（设为零）的概率。第 \( i \) 个神经元的激活值随后修改如下：

$$a'_i = r_i \cdot a_i = r_i \cdot f(Wx_i + b_i)$$ (303)

其中 \( r_i \) 是每个神经元的随机二进制掩码。在每次前向传递期间，不同的神经元会被随机丢弃，网络实际上在训练一个不同的子网络，迫使网络学习一组不依赖于任何特定神经元的更鲁棒的特征。这样一来，丢弃法充当一种 _集成学习_ 形式，因为每次前向传递都对应于一个


网络的不同实现。

The mathematical expectation of the loss function with respect to the dropout mask $r$ can be written as:

$$ \mathbb{E}_r[L_{\text{dropout}}(\theta, r)] = \frac{1}{N} \sum_{i=1}^N \mathcal{L}(f_\theta(x_i, r), y_i) $$ (304)

其中 $f_\theta(x_i, r)$ 是带有掩码 $r$ 的网络输出。由于掩码是随机的，损失是对所有可能的掩码配置的期望。这种随机性诱导了一种隐式的 *集成效应*，其中模型不仅在单一参数集 $\theta$ 上进行训练，实际上是在对一个 *模型分布* 进行训练，每个模型对应于一个不同的掩码配置。因此，模型被正则化，因为网络被迫在这些不同的子网络之间进行泛化，从而防止了对训练数据的过拟合。深入理解脱节的一种方法是考虑其与 *贝叶斯推断* 的联系。在深度学习的背景下，脱节可以被视为对 *贝叶斯后推断* 的近似。在贝叶斯术语中，鉴于数据 $D$，我们寻求网络参数 $\theta$ 的后验分布，可以表示为：

$$ p(\theta|D) = \frac{p(D|\theta)p(\theta)}{p(D)} $$ (305)

其中 $p(D|\theta)$ 是给定参数的数据似然，$p(\theta)$ 是参数上的先验分布，$p(D)$ 是数据的边缘似然。脱节通过对许多不同子网络输出求平均来近似这个后验，每个子网络对应于一个不同的掩码配置。这一解释通过观察得以形式化：每次使用不同掩码的前向传播都对应于模型的不同实现，而对所有掩码求平均则给出了贝叶斯后验的近似。因此，在脱节下，给定数据 $x$ 时，网络的期望输出为：

$$ \mathbb{E}_r[f_\theta(x)] = \frac{1}{M} \sum_{i=1}^M f_\theta(x, r_i) $$ (306)

其中 $r_i$ 是从伯努利分布中绘制的掩码，$M$ 是掩码配置的蒙特卡罗样本数量。这种期望可以被解释为一种 *集成平均*，其中每个单独的前向传播都对应于从后验中采样的一个不同模型。

Dropout is also highly effective because it controls the *bias-variance tradeoff*. The bias-variance tradeoff is a fundamental concept in statistical learning, where increasing model complexity reduces bias but increases variance, and vice versa. A highly complex model tends to have low bias but high variance, meaning it fits the training data very well but fails to generalize to new data. Regularization techniques, such as dropout, seek to reduce variance without increasing bias excessively. Dropout achieves this by introducing stochasticity in the learning process. By randomly deactivating neurons during training, the model is forced to learn *robust features* that do not depend on the presence of specific neurons. In mathematical terms, the variance of the model's output can be expressed as:

脱节之所以非常有效，是因为它控制了 *偏差-方差权衡*。偏差-方差权衡是统计学习中的一个基本概念，其中增加模型复杂度会降低偏差但增加方差，反之亦然。高度复杂的模型往往具有低偏差但高方差，这意味着它在训练数据上拟合得很好，但无法泛化到新数据。正则化技术（如脱节）旨在在不过度增加偏差的前提下降低方差。脱节通过在学习过程中引入随机性来实现这一点。通过在训练期间随机禁用神经元，模型被迫学习不依赖于特定神经元存在的 *鲁棒特征*。从数学上讲，模型输出的方差可以表示为：

$$ \text{Var}(f_\theta(x)) = \mathbb{E}_r[(f_\theta(x))^2] - (\mathbb{E}_r[f_\theta(x)])^2 $$ (307)

By averaging over multiple dropout configurations, the variance is reduced, leading to better generalization performance. Although dropout introduces some bias by reducing the network's capacity (since fewer neurons are available at each step), the variance reduction outweighs the bias increase, resulting in improved generalization. Another key mathematical aspect of dropout is its relationship with *stochastic gradient descent (SGD)*. In the standard SGD framework, the parameters $\theta$ are updated using the gradient of the loss with respect to the parameters. In the case of dropout, the gradient is computed based on a stochastic subnetwork at each training iteration, which introduces an element of randomness into the optimization process. The parameter update rule with dropout can be written as:

通过对多个脱节配置求平均，方差得以降低，从而带来更好的泛化性能。虽然脱节通过降低网络容量（因为每个步骤中可用的神经元较少）引入了一些偏差，但方差的减少超过了偏差的增加，从而实现了更好的泛化。脱节的另一个关键数学方面是其与 *随机梯度下降（SGD）* 的关系。在标准 SGD 框架中，参数 $\theta$ 使用损失对参数的梯度进行更新。在脱节的情况下，梯度是在每次训练迭代中基于随机子网络计算的，这将随机性引入优化过程。带有脱节的参数更新规则可以表示为：

\(\theta_{t+1} = \theta_t - \eta \nabla_\theta \mathbb{E}_r [L_{\text{dropout}}(\theta, r)]\) (308)

where \(\eta\) is the learning rate, and \(\nabla_\theta\) is the gradient of the loss with respect to the model parameters. The expectation is taken over all possible dropout configurations, which means that at each step, the gradient update is based on a different realization of the model. This stochasticity helps the optimization process by preventing the model from getting stuck in local minima, improving convergence towards global minima, and enhancing generalization. Finally, it is important to note that dropout has a close connection with low-rank approximations. During each forward pass with dropout, certain neurons are effectively removed, which reduces the rank of the weight matrix, as some rows or columns of the matrix are set to zero. This stochastic reduction in rank forces the network to learn lower-dimensional representations of the data, effectively performing low-rank regularization. This aspect of dropout can be formalized by observing that each dropout mask corresponds to a sparse matrix, and the network is effectively learning a low-rank approximation of the data distribution. By doing so, dropout prevents the network from learning overly complex representations that could overfit the data, leading to improved generalization.

其中 \(\eta\) 是学习率，\(\nabla_\theta\) 是损失对模型参数的梯度。期望是对所有可能的脱节配置取值，这意味着在每个步骤中，梯度更新都基于模型的一个不同实现。这种随机性通过防止模型陷入局部极小值、改善向全局极小值的收敛以及增强泛化能力来帮助优化过程。最后，重要的是要注意，脱节与低秩近似密切相关。在每次带有脱节的前向传播中，某些神经元实际上被移除，这降低了权重矩阵的秩，因为矩阵的某些行或列被置为零。这种随机的秩降低迫使网络学习数据的低维表示，实际上执行了低秩正则化。脱节的这一特性可以通过观察得以形式化：每个脱节掩码都对应一个稀疏矩阵，而网络实际上正在学习数据分布的低秩近似。通过这样做，脱节防止网络学习可能过拟合数据的过度复杂的表示，从而实现了更好的泛化。

In summary, dropout is a powerful and mathematically sophisticated regularization technique that introduces randomness into the training process. By randomly deactivating neurons during each forward pass, dropout forces the model to generalize better and prevents overfitting. Dropout can be understood as approximating Bayesian posterior inference over the model parameters and acts as a form of ensemble learning. It controls the bias-variance tradeoff, reduces variance, and improves generalization. The stochastic nature of dropout also introduces a form of noise injection during training, which aids in avoiding local minima and ensures convergence to global minima. Additionally, dropout induces low-rank regularization, which further improves generalization by preventing overly complex representations. Through these mathematical and statistical insights, dropout has become a cornerstone technique in deep learning, enhancing the performance of neural networks on unseen data.

总而言之，脱节是一种强大且在数学上非常复杂的正则化技术，它将随机性引入训练过程。通过在每次前向传播期间随机禁用神经元，脱节迫使模型更好地泛化并防止过拟合。脱节可以理解为对模型参数进行贝叶斯后验推断的近似，并充当一种集成学习形式。它控制偏差-方差权衡，降低方差并改善泛化。脱节的随机性还在训练过程中引入了一种噪声注入形式，这有助于避免局部极小值并确保收敛到全局极小值。此外，脱节诱导低秩正则化，通过防止过度复杂的表示来进一步改善泛化。通过这些数学和统计洞察，脱节已成为深度学习中的基石技术，增强了神经网络在未见数据上的性能。

### 6.3.2 L1/L2 正则化与过拟合

L1 and L2 regularization plays a critical role in mitigating overfitting. Overfitting occurs when a model fits not only the underlying data distribution but also the noise in the data, leading to poor generalization to unseen examples. Overfitting is especially prevalent in models with a large number of features, where the model becomes overly flexible and may capture spurious correlations between the features and the target variable. This often results in a model with high variance, where small fluctuations in the data cause significant changes in the model predictions. To combat this, regularization techniques are employed, which introduce a penalty term into the objective function, discouraging overly complex models that fit noise.

L1 和 L2 正则化在缓解过拟合方面起着关键作用。当模型不仅拟合了底层数据分布，还拟合了数据中的噪声时，就会发生过拟合，导致对未见样本的泛化性能差。在特征数量较多的模型中，过拟合尤为普遍，此时模型变得过于灵活，可能会捕捉特征与目标变量之间的虚假相关性。这通常会导致高方差模型，即数据中的微小波动会引起模型预测的显著变化。为应对这一问题，采用了正则化技术，在目标函数中引入惩罚项，以抑制拟合噪声的过度复杂模型。

Given a set of \(n\) observations \(\{(\mathbf{x}_i, y_i)\}_{i=1}^n\), where each \(\mathbf{x}_i \in \mathbb{R}^p\) is a feature vector and \(y_i \in \mathbb{R}\) is the corresponding target value, the task is to find a parameter vector \(\theta \in \mathbb{R}^p\) that minimizes the loss function. In standard linear regression, the objective is to minimize the mean squared error (MSE), defined as:

给定一组 \(n\) 个观测值 \(\{(\mathbf{x}_i, y_i)\}_{i=1}^n\)，其中每个 \(\mathbf{x}_i \in \mathbb{R}^p\) 是特征向量，$y_i \in \mathbb{R}$ 是相应的目标值，任务是找到一个参数向量 $\theta \in \mathbb{R}^p$ 来最小化损失函数。在标准线性回归中，目标是最小化均方误差（MSE），定义为：

\(\mathcal{L}(\theta) = \frac{1}{n} \sum_{i=1}^n (y_i - \mathbf{x}_i^T \theta)^2 = \frac{1}{n} \|\mathbf{X}\theta - \mathbf{y}\|^2\) (309)

where \(\mathbf{X} \in \mathbb{R}^{n \times p}\) is the design matrix, with rows \(\mathbf{x}_i^T\), and \(\mathbf{y} \in \mathbb{R}^n\) is the vector of target values. The solution to this problem, without any regularization, is given by the ordinary least squares

其中 $\mathbf{X} \in \mathbb{R}^{n \times p}$ 是设计矩阵，行向量为 $\mathbf{x}_i^T$，$\mathbf{y} \in \mathbb{R}^n$ 是目标值向量。在没有任何正则化的情况下，该问题的解由普通最小二乘法给出



## (OLS) 解：

```
\hat{\theta}_{\text{OLS}} = (\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y}
```

然而，这种公式在 \( p \) 较大或 \( \mathbf{X}^T\mathbf{X} \) 接近奇异时可能导致过拟合。在这种情况下，**正则化**用于修改损失函数，向目标函数中添加惩罚项 \( \mathcal{R}(\theta) \)，以抑制参数 \( \theta_i \) 取较大值。**正则化损失函数**如下所示：

```
\mathcal{L}_{\text{regularized}}(\theta) = \mathcal{L}(\theta) + \lambda \mathcal{R}(\theta)
```

其中，\( \lambda \) 是控制惩罚强度的**正则化参数**。项 \( \mathcal{R}(\theta) \) 通过对系数幅度施加约束来惩罚模型的复杂性。让我们探讨两种广泛使用的正则化形式：**L1 正则化**（Lasso）和 **L2 正则化**（Ridge）。L1 正则化涉及将参数向量 \( \theta \) 的 \( \ell_1 \)-范数作为惩罚项：

```
\mathcal{R}_{L1}(\theta) = \sum_{i=1}^p |\theta_i|
```

相应的 **L1 正则化损失函数**为：

```
\mathcal{L}_{L1}(\theta) = \frac{1}{n} \|\mathbf{X}\theta - \mathbf{y}\|^2 + \lambda \sum_{i=1}^p |\theta_i|
```

这种公式促进了参数向量 \( \theta \) 的稀疏性，导致许多系数变为恰好零，从而有效地执行**特征选择**。在许多特征不相关的高维场景中，L1 正则化通过强制排除不相关特征来帮助降低模型复杂度。L1 惩罚的几何效应可以这样理解：由 \( \ell_1 \)-范数定义的约束区域在 \( p \) 维空间中是一个**菱形**区域。求解此优化问题时，系数通常位于该菱形的边界上，从而导致许多系数恰好为零的稀疏解。从数学上讲，求解 L1 正则化优化问题得到的**软阈值**解如下：

```
\hat{\theta}_i = \text{sign}(\theta_i) \max(0, |\theta_i| - \lambda)
```

这种软阈值特性会在系数幅度小于 \( \lambda \) 时将系数驱动为零，从而得到稀疏解。另一方面，L2 正则化使用参数向量 \( \theta \) 的 \( \ell_2 \)-范数作为惩罚项：

```
\mathcal{R}_{L2}(\theta) = \sum_{i=1}^p \theta_i^2
```

相应的 **L2 正则化损失函数**为：

```
\mathcal{L}_{L2}(\theta) = \frac{1}{n} \|\mathbf{X}\theta - \mathbf{y}\|^2 + \lambda \sum_{i=1}^p \theta_i^2
```

该惩罚项不会强制任何系数恰好为零，而是将系数**收缩**向零，从而有效降低其幅度。当特征存在多重共线性时，L2 正则化通过减少高度相关特征的影响来帮助稳定解。带有 L2 正则化的优化问题得到的是**脊回归**解，其表达式如下：

```
\hat{\theta}_{\text{ridge}} = (\mathbf{X}^T\mathbf{X} + \lambda \mathbf{I})^{-1}\mathbf{X}^T\mathbf{y}
```

其中，**I** 是单位矩阵。L2 惩罚在参数空间中引入**圆形或球形**约束，从而得到所有系数幅度均被降低但没有系数被消除的解。**弹性网**正则化是一种结合 L1 和 L2 正则化的混合技术。弹性网的正则化损失函数如下所示：

\(\mathcal{L}_{\text{ElasticNet}}(\theta) = \frac{1}{n}\|\mathbf{X}\theta - \mathbf{y}\|^2 + \lambda_1 \sum_{i=1}^p |\theta_i| + \lambda_2 \sum_{i=1}^p \theta_i^2 \tag{318}\)

在此例中，\(\lambda_1\) 和 \(\lambda_2\) 分别控制 L1 和 L2 惩罚的强度。弹性网正则化在处理许多特征相关的数据集时特别有用，因为它结合了 L1 正则化的**诱导稀疏性**特性与 L2 正则化的**增强稳定性**特性。已有研究表明，弹性网在某些情况下优于 L1 和 L2 正则化，尤其是在存在相关特征组时。优化问题可使用**坐标下降**或**近端梯度方法**求解，这些方法能高效处理混合惩罚。正则化参数 \(\lambda\) 的选择对于控制**偏差-方差权衡**至关重要。\(\lambda\) 取较小值会导致低惩罚模型，更容易过拟合；\(\lambda\) 取较大值会迫使系数收缩向零，可能导致欠拟合。因此，为 \(\lambda\) 选择最优值以在偏差和方差之间取得平衡非常重要。这可以通过使用**交叉验证**技术实现，即在数据子集上训练模型，并在剩余数据上评估其性能。

总之，L1 和 L2 正则化技术通过控制模型复杂度，在解决过拟合问题中发挥着重要作用。L1 正则化鼓励稀疏性和特征选择，而 L2 正则化则在不消除任何特征的前提下降低系数幅度。通过将这些正则化项纳入目标函数，我们可以实现更平衡的偏差-方差权衡，提升模型对新的未见数据的泛化能力。

## 6.4 超参数调优

文献综述：Luo et al. (2003) [137] 对贝叶斯优化进行了深入探讨，这是一种广泛使用的超参数调优方法。该文涵盖了理论基础、实际应用以及确定超参数适当范围的高级策略。对于有兴趣采用概率方法调优机器学习模型的研究人员来说，这是一份必备资源。Alrayes et al. (2025) [138] 探讨了在应用于物联网网络的机器学习模型中，利用统计学习和优化算法来微调超参数的方法。该论文强调隐私保护方法，因此对于在安全数据环境中工作的从业者来说非常有价值。Cho et al. (2020) [139] 讨论了在使用贝叶斯优化进行深度神经网络超参数调优时的基本增强策略。Ibrahim et al. (2025) [140] 将重点放在了 XGBoost（一种广泛使用的机器学习模型）的超参数调优上，应用场景为医疗诊断。它展示了调优技术的比较分析，以优化现实世界医疗应用中的模型性能。Abdel-Salam et al. (2025) [141] 引入了一种使用多种优化算法调优深度学习模型的演进框架。它提出了一种在训练深度网络时优于传统技术的新方法。Vali (2025) [142] 在其博士论文中介绍了向量量化技术如何帮助减少深度学习模型的超参数搜索空间。它强调了语音和图像处理应用中的计算效率。Vincent and Jidesh (2023) [143] 在其论文中探讨了各种超参数优化技术，并使用 AutoML 模型在图像分类数据集上比较了它们的性能。该文侧重于贝叶斯优化，并引入了遗传算法、差分进化以及协方差矩阵自适应进化策略（CMA-ES）用于获取函数优化。结果表明，CMA-ES 和差分进化增强了贝叶斯优化，而遗传算法则会降低其性能。

Razavi-Termeh et al. (2025) [144] 探讨了地理空间人工智能（GeoAI）在绘制易淹区图中的作用，利用元启发式算法进行超参数调优。它为环境科学中的机器学习应用提供了洞察。Kiran and Ozyildirim (2022) [145] 提出了一种分布式可变长度遗传算法，用于优化强化学习（RL）中的超参数，提高训练效率和鲁棒性。与传统的深度强化学习不同，后者由于复杂性而缺乏广泛调优，我们的方法系统地提升了各种 RL 任务的性能，并优于贝叶斯方法。结果表明，更多的代际会产生最佳且计算效率高的解，推动了 RL 在现实世界应用中的发展。

神经网络中的超参数调优是一项复杂的高度数学化的优化挑战，是实现给定任务最优性能的基础。该过程可表述为双层优化问题，其中外层优化涉及选择超参数 \( h \in \mathcal{H} \) 以最小化验证损失函数 \( \mathcal{L}_{\text{val}}(\theta^*(h); h) \)，而内层优化则通过最小化训练损失 \( \mathcal{L}_{\text{train}}(\theta; h) \) 来确定最优模型参数 \( \theta^* \)。这可以严谨地表述为：

```
\( h^* = \arg \min_{h \in \mathcal{H}} \mathcal{L}_{\text{val}}(\theta^*(h); h), \quad \text{where} \quad \theta^*(h) = \arg \min_{\theta} \mathcal{L}_{\text{train}}(\theta; h). \quad (319) \)
```

此处，\( \mathcal{H} \) 表示超参数空间，通常是高维、非凸且遍历开销很大的。训练损失函数 \( \mathcal{L}_{\text{train}}(\theta; h) \) 通常表示为在训练数据集 \( \{(x_i, y_i)\}_{i=1}^N \) 上计算的经验风险：

```
\( \mathcal{L}_{\text{train}}(\theta; h) = \frac{1}{N} \sum_{i=1}^N \ell(f(x_i; \theta, h), y_i), \quad (320) \)
```

其中，\( f(x_i; \theta, h) \) 是给定输入 \( x_i \)、参数 \( \theta \) 和超参数 \( h \) 时的神经网络输出，而 \( \ell(a, b) \) 是量化预测 \( a \) 与真实值 \( b \) 之间差异的损失函数。对于分类任务，\( \ell \) 通常采用交叉熵损失的形式：

```
\( \ell(a, b) = - \sum_{k=1}^C b_k \log a_k, \quad (321) \)
```

其中，\( C \) 是类别数量，\( a_k \) 和 \( b_k \) 分别是第 \( k \) 个类别的预测概率和真实概率。训练过程的核心是通过随机梯度下降（SGD）等基于梯度的方法优化 \( \theta \)。参数更新遵循：

```
\( \theta^{(t+1)} = \theta^{(t)} - \eta \nabla_\theta \mathcal{L}_{\text{train}}(\theta^{(t)}; h), \quad (322) \)
```

其中，\( \eta > 0 \) 是学习率，这是一个控制步长的关键超参数。SGD 的稳定性和收敛性取决于 \( \eta \)，其必须满足：

```
\( 0 < \eta < \frac{2}{\lambda_{\max}(H)}, \quad (323) \)
```

其中，\( \lambda_{\max}(H) \) 是海森矩阵 \( H = \nabla_\theta^2 \mathcal{L}_{\text{train}}(\theta; h) \) 的最大特征值。该条件确保梯度下降步长不会越过最小值。为了分析收敛行为，临界点 \( \theta^* \) 附近的损失函数 \( \mathcal{L}_{\text{train}}(\theta; h) \) 可通过二阶泰勒展开近似为：

```
\( \mathcal{L}_{\text{train}}(\theta; h) \approx \mathcal{L}_{\text{train}}(\theta^*; h) + \frac{1}{2}(\theta - \theta^*)^\top H(\theta - \theta^*), \quad (324) \)
```

其中，\( H \) 是二阶导数的海森矩阵。\( H \) 的特征值揭示了损失曲面的局部曲率，正特征值表示凸性方向，负



鞍点对应的特征值。正则化通常通过惩罚大参数值来提高泛化能力。对于 \( L_2 \) 正则化，修改后的训练损失为：

\(\mathcal{L}_{train}^{reg}(\theta; h) = \mathcal{L}_{train}(\theta; h) + \frac{\lambda}{2}\|\theta\|_2^2,\) (325)

其中 \(\lambda > 0\) 是正则化系数。正则化损失的梯度变为：

\(\nabla_\theta \mathcal{L}_{train}^{reg}(\theta; h) = \nabla_\theta \mathcal{L}_{train}(\theta; h) + \lambda \theta.\) (326)

另一个关键超参数是权重初始化策略，它影响整个网络中激活值和梯度的规模。对于具有 \( n_\text{in} \) 个输入的层，He 初始化从以下分布中采样权重：

\( w_{ij} \sim \mathcal{N}\left(0, \frac{2}{n_\text{in}}\right),\) (327)

以确保在数据通过各层传播时，激活值的方差保持稳定。激活函数 \( g(z) \) 也起着至关重要的作用。修正线性单元（ReLU）定义为 \( g(z) = \max(0, z) \)，它引入稀疏性并缓解梯度消失问题。然而，它存在“神经元死亡”问题，因为其导数 \( g'(z) \) 在 \( z \le 0 \) 时为零。寻找最优超参数可以使用网格搜索、随机搜索或更先进的方法（如贝叶斯优化）。在贝叶斯优化中，构建一个代理模型 \( p(\mathcal{L}_{val}(h)) \)（通常为高斯过程（GP））来近似验证损失。采集函数 \( a(h) \)（例如预期改进（EI））通过在低预测损失区域的开发与不确定区域的探索之间取得平衡，来指导对 \( \mathcal{H} \) 的探索：

\( a(h) = \mathbb{E} \left[ \max(0, \mathcal{L}_{val,min} - \mathcal{L}_{val}(h)) \right],\) (328)

其中 \( \mathcal{L}_{val,min} \) 是观测到的最佳验证损失。由于 \( \mathcal{H} \) 的高维性以及优化问题的嵌套特性，超参数调优计算量密集。早停是一种广泛使用的策略，当验证损失的改善低于阈值时停止训练：

\(\frac{\mathcal{L}_{val}^{(t+1)} - \mathcal{L}_{val}^{(t)}}{\mathcal{L}_{val}^{(t)}} < \epsilon,\) (329)

其中 \( \epsilon > 0 \) 是一个小常数。像 Hyperband 这样的高级技术利用多保真优化，根据部分训练评估动态将资源分配给有前景的超参数配置。

总之，训练神经网络的超参数调优是一个在数学上极为严谨的过程，基于嵌套优化、基于梯度的方法、概率建模和计算启发式。从学习率和正则化到初始化及优化策略的每个组件，都为定义神经网络性能的复杂相互作用做出了贡献。

### 6.4.1 网格搜索

文献综述：Rohman 和 Farikhin (2025) [397] 探索了网格搜索和随机搜索在糖尿病预测背景下用于随机森林分类器的超参数调优中的影响。该研究对不同的超参数调优策略进行了比较分析，并表明网格搜索通过系统选择最优超参数组合来提高分类准确率。

Rohman (2025) [398] 应用基于网格搜索的超参数调优来优化早期脑肿瘤检测的机器学习模型。该研究强调了系统超参数选择的重要性，并提供了关于网格搜索如何影响医疗应用中诊断准确率和计算效率的见解。

Nandi 等人 (2025) [399] 考察了网格搜索在婴儿哭声识别系统中用于深度学习超参数调优的应用。作者提出了一种新的流水线，用于系统选择神经网络的最佳超参数，从而在声音分类中提高精确率和召回率。

Sianga 等人 (2025) [400] 应用网格搜索和随机搜索来优化预测心血管疾病风险的机器学习模型。该研究发现，网格搜索在准确率方面始终优于随机方法，突出了其在医疗诊断模型中的有效性。

Li 等人 (2025) [401] 应用结合网格搜索的分层 5 折交叉验证来微调预测术后并发症的极端梯度提升（XGBoost）模型。结果表明，超参数调优显著提高了预测性能，网格搜索带来了最佳的模型稳定性和可解释性。

Lázaro 等人 (2025) [402] 实现了网格搜索和贝叶斯优化，以优化航空安全中事故分类的 K 近邻（KNN）和决策树。该研究强调了不同超参数调优方法如何影响基于 NLP 的事故报告中机器学习模型的泛化能力。

Li 等人 (2025) [403] 提出了 RAINER，这是一种集成了网格搜索以实现最优超参数调优的集成学习模型。该研究表明，参数优化如何增强降雨模型的预测能力，使网格搜索成为气候建模中不可或缺的步骤。

Khurshid 等人 (2025) [404] 比较了糖尿病预测模型中贝叶斯优化与网格搜索的超参数调优。该研究发现，虽然贝叶斯方法计算速度更快，但网格搜索提供了更精确的超参数选择，特别是对于具有结构化医疗数据的模型。

Kanwar 等人 (2025) [405] 应用网格搜索来调整滑坡易感性制图中的随机森林分类器。该研究表明，微调后的模型改进了高风险区域的识别，减少了预测滑坡模型中的假阳性。

Fadil 等人 (2025) [406] 评估了网格搜索和随机搜索在腐蚀预测中用于 XGBoost 回归模型的超参数调优中的作用。作者发现，基于网格搜索的模型获得更高的 R² 分数，因此非常适合复杂的化学建模应用。

网格搜索是一种高度结构化且详尽的机器学习超参数调优方法，其中系统地探索预定义的超参数值网格。其目标是识别出能为给定机器学习模型产生最优性能指标的超参数集 \(\vec{h} = (h_1, h_2, ..., h_p)\)。令 \(p\) 表示需要调优的超参数总数，对于每个超参数 \(h_i\)，令候选集为 \(\mathcal{H}_i = \{h_{i1}, h_{i2}, ..., h_{im_i}\}\)，其中 \(m_i\) 是 \(h_i\) 的候选值数量。超参数搜索空间则是所有候选集的笛卡尔积：

\(\mathcal{S} = \mathcal{H}_1 \times \mathcal{H}_2 \times \dots \times \mathcal{H}_p.\) (330)

因此，需要评估的配置总数为：

\(|\mathcal{S}| = \prod_{i=1}^p m_i.\) (331)

例如，如果我们有两个超参数 \(h_1\) 和 \(h_2\)，每个都有 3 个可能值，那么需要探索的组合总数为 9。随着超参数数量的增加，搜索空间呈指数级增长，带来了巨大的计算挑战。网格搜索涉及遍历 \(\mathcal{S}\) 中的所有配置，评估每个配置下模型的性能。

让我们定义性能指标 \(M(\vec{h}, \mathcal{D}_{train}, \mathcal{D}_{val})\)，它量化给定超参数配置 \(\vec{h}\) 下模型的性能，其中 \(\mathcal{D}_{train}\) 和 \(\mathcal{D}_{val}\) 分别是训练数据集和验证数据集。该指标可能代表准确率、错误率、F1 分数或任何其他相关标准，具体取决于手头的问题。随后通过在搜索空间上最大化或最小化 \(M\) 来调优超参数：

\(\vec{h}^* = \arg \max_{\vec{h} \in \mathcal{S}} M(\vec{h}, \mathcal{D}_{train}, \mathcal{D}_{val}),\) (332)



或者在最小化问题的情况下：

$$
\vec{h}^* = \arg \min_{\vec{h} \in \mathcal{S}} M(\vec{h}, \mathcal{D}_{train}, \mathcal{D}_{val}).
$$ (333)

对于每个超参数组合，模型在 \(\mathcal{D}_{train}\) 上训练并在 \(\mathcal{D}_{val}\) 上评估。该过程需要对 \(\mathcal{S}\) 中的所有 \(|\mathcal{S}|\) 个配置进行重复评估，每个配置产生一个性能指标。为了减轻过拟合并确保性能指标的可靠性，经常使用交叉验证。在 \(k\)-折交叉验证中，数据集 \(\mathcal{D}_{train}\) 被划分为 \(k\) 个不相交的子集 \(\mathcal{D}_1, \mathcal{D}_2, \dots, \mathcal{D}_k\)。模型在 \(\mathcal{D}_{train}^{(j)} = \bigcup_{i \neq j} \mathcal{D}_i\) 上训练并在 \(\mathcal{D}_j\) 上验证。对于每个折 \(j\)，我们计算性能指标：

$$
M_j(\vec{h}) = M(\vec{h}, \mathcal{D}_{train}^{(j)}, \mathcal{D}_j).
$$ (334)

超参数配置 \(\vec{h}\) 的总体交叉验证性能是 \(k\) 个单独折性能的平均值：

$$
\overline{M}(\vec{h}) = \frac{1}{k} \sum_{j=1}^k M_j(\vec{h}).
$$ (335)

因此，带交叉验证的网格搜索旨在通过最大化或最小化所有折的平均性能来找到最优超参数。网格搜索的计算复杂度是一个关键考量。如果我们用 \(C\) 表示训练和评估单个配置的模型的成本，则网格搜索的总成本为：

$$
\mathcal{O} \left( \prod_{i=1}^p m_i \cdot k \cdot C \right),
$$ (336)

其中 \(k\) 表示交叉验证中的折数。随着超参数数量 \(p\) 和候选值数量 \(m_i\) 的增加，总计算时间会呈指数级增长。对于大搜索空间，网格搜索可能变得计算成本高昂，使其对于高维超参数优化问题变得不切实际。为了以具体示例说明，请考虑两个超参数 \(h_1\) 和 \(h_2\) 及以下候选值集合：

$$
\mathcal{H}_1 = \{0.01, 0.1, 1.0\}, \quad \mathcal{H}_2 = \{0.1, 1.0, 10.0\}.
$$ (337)

搜索空间是：

$$
\mathcal{S} = \mathcal{H}_1 \times \mathcal{H}_2 = \{(0.01, 0.1), (0.01, 1.0), (0.01, 10.0), (0.1, 0.1), \dots, (1.0, 10.0)\}.
$$ (338)

需要评估9个配置。对于每个配置，假设我们执行3折交叉验证，其中第一个折的性能指标为：

$$
M_1(0.1, 1.0) = 0.85, \quad M_2(0.1, 1.0) = 0.87, \quad M_3(0.1, 1.0) = 0.86,
$$ (339)

得出交叉验证性能：

$$
\overline{M}(0.1, 1.0) = \frac{1}{3} \sum_{j=1}^3 M_j(0.1, 1.0) = \frac{1}{3}(0.85 + 0.87 + 0.86) = 0.86.
$$ (340)

该过程对 \(h_1\) 和 \(h_2\) 的所有9个组合重复进行。虽然网格搜索是详尽且确定性的，但它可能无法有效地探索超参数空间，尤其是当超参数数量较大时。搜索被限制在离散网格上，无法在点之间进行插值以捕获可能位于网格值之间的最优配置。此外，由于网格搜索独立评估每个配置，对于高维空间来说可能计算成本高昂，因为配置数量随 \(p\) 和 \(m_i\) 呈指数增长。

总之，网格搜索是一种方法学严谨且系统化的超参数优化方法，确保所有预定义配置都得到详尽评估。然而，其计算成本随超参数数量及其各自候选值的数量呈指数增长，这可能限制其在大规模问题中的适用性。因此，当计算预算有限时，通常会使用更先进的技术，如随机搜索、贝叶斯优化或进化算法来进行超参数调优。尽管存在这些挑战，网格搜索仍然是展示超参数调优原则的强大工具，并且非常适合相对较小搜索空间的问题。

### 6.4.2 随机搜索

文献综述：Sianga 等人 (2025) [400] 探讨了在心血管疾病风险预测中调优机器学习模型的随机搜索与网格搜索。研究发现，随机搜索在保持高准确性的同时显著减少计算时间，使其在医疗应用的高维数据集中更具优势。Lázaro 等人 (2025) [402] 将随机搜索和网格搜索应用于使用 NLP 优化事故分类模型。该研究强调了随机搜索在调优 K-最近邻 (KNN) 和决策树方面的效率，实现了更快的收敛且准确度损失极小。Emmanuel 等人 (2025) [407] 引入了一种结合随机搜索与差分进化优化的混合方法，以增强基于深度学习的蛋白质相互作用模型。该研究展示了随机搜索如何提高泛化能力并减少过拟合。Gaurav 等人 (2025) [408] 评估了用于驾驶员识别的随机森林分类器中的随机搜索优化。他们比较了随机搜索、贝叶斯优化和遗传算法，得出结论：随机搜索在效率与性能之间取得了平衡。Kanwar 等人 (2025) [405] 将随机搜索超参数调优应用于滑坡风险评估的随机森林模型。研究发现，随机搜索显著减少计算时间而不影响模型准确性，使其非常适合大规模地理空间分析。Ning 等人 (2025) [409] 评估了随机搜索用于优化感染性胰腺坏死患者的死亡率预测模型。作者得出结论：随机搜索在寻找最优超参数方面优于详尽的网格搜索，并带来显著的速度提升。Muñoz 等人 (2025) [410] 提出了一种将随机搜索与秘书算法相结合的新型优化策略，以提高超参数调优效率。它展示了随机搜索如何适应实时 AI 应用中的动态优化问题。Balcan 等人 (2025) [411] 探讨了随机搜索在深度学习优化中的理论基础。他们对有效调优所需的样本复杂性提供了严格分析，为随机搜索效率建立了数学保证。Azimi 等人 (2025) [412] 在超级电容器建模中将随机搜索与元启发式算法（例如，遗传算法和粒子群优化）进行了比较。结果表明，随机搜索为深度学习模型中的超参数优化提供了一个强健的基线。Shibina 和 Thasleema (2025) [413] 将随机搜索应用于医疗诊断中集成学习分类器的优化。结果表明，随机搜索在使用语音特征检测帕金森病方面寻找最优超参数具有优势，使其成为贝叶斯优化的一种实用替代方案。

在机器学习中，超参数调优是选择超参数最佳配置 \(h = (h_1, h_2, \dots, h_d)\) 的过程，其中每个 \(h_i\) 表示第 \(i\) 个超参数。超参数 \(h\) 控制模型学习的关键方面，例如学习率、正则化强度或神经网络架构。这些超参数并非通过学习过程本身直接优化，而是在训练开始之前设定。给定一组超参数后，模型性能通过计算损失函数 \(L(h)\) 进行评估，该函数通常表示验证集上的误差，可能还包括用于减轻过拟合的正则化项。目标是最小化此损失函数以找到最优超参数集合：

$$
\mathbf{h}^* = \arg \min_{\mathbf{h}} L(\mathbf{h}), \tag{341}
$$

其中 \(L(\mathbf{h})\) 是量化模型对未见数据泛化能力的损失函数。此函数的最小化通常受限于每个 \(h_i\) 可取值的范围或类型，形成一个约束优化问题：

$$
\mathbf{h}^* = \arg \min_{\mathbf{h} \in \mathcal{H}} L(\mathbf{h}), \tag{342}
$$

其中 \(\mathcal{H}\) 表示可行超参数空间。超参数调优通常通过选择高效探索该空间的搜索方法来执行，目标是找到损失函数的全局或局部最优解。

一种这样的搜索方法是**随机搜索**，这是一种简单而有效的探索超参数空间的方法。与详尽搜索每个超参数的网格值（如网格搜索）不同，随机搜索从每个超参数 \(h_i\) 的预定义分布中采样超参数 \(\mathbf{h}_t = (h_{t,1}, h_{t,2}, \dots, h_{t,d})\)。对于每次迭代 \(t\)，超参数从与每个超参数 \(h_i\) 相关的概率分布 \(\mathcal{D}_i\) 中独立采样，概率分布可以是连续的或离散的。具体地，对于连续超参数，\(h_{t,i}\) 从区间 \(H_i = [a_i, b_i]\) 上的均匀分布或正态分布中抽取：

$$
h_{t,i} \sim \mathcal{U}(a_i, b_i), \quad h_{t,i} \in H_i, \tag{343}
$$

其中 \(\mathcal{U}(a_i, b_i)\) 表示 \(a_i\) 和 \(b_i\) 之间的均匀分布。对于离散超参数，\(h_{t,i}\) 从离散值集合 \(H_i = \{h_{i1}, h_{i2}, \dots, h_{iN_i}\}\) 中采样，每个值等可能：

$$
h_{t,i} \sim \mathcal{D}_i, \quad h_{t,i} \in \{h_{i1}, h_{i2}, \dots, h_{iN_i}\}, \tag{344}
$$

其中 \(\mathcal{D}_i\) 表示集合 \(\{h_{i1}, h_{i2}, \dots, h_{iN_i}\}\) 上的离散分布。因此，每个超参数从其对应的分布中独立选择。在选择一组新的超参数 \(\mathbf{h}_t\) 后，模型使用此配置进行训练，并通过计算损失函数 \(L(\mathbf{h}_t)\) 评估其性能。该过程重复 \(T\) 次迭代，生成一组超参数配置序列 \(\mathbf{h}_1, \mathbf{h}_2, \dots, \mathbf{h}_T\)，并对每个配置计算相关的损失函数值 \(L(\mathbf{h}_1), L(\mathbf{h}_2), \dots, L(\mathbf{h}_T)\)。然后选择最小化损失的一组超参数 \(\mathbf{h}^*\) 作为最优超参数：

$$
\mathbf{h}^* = \arg \min_{t \in \{1, 2, \dots, T\}} L(\mathbf{h}_t). \tag{345}
$$

因此，随机搜索对超参数空间进行近似优化，每次迭代的计算成本为 \(C\)（评估给定超参数集合的模型性能所需的时间），总计算成本为 \(O(T \cdot C)\)。这使得随机搜索成为一种计算上可行的方法，尤其是当 \(T\) 适中时。随机搜索的计算效率可以与网格搜索相比较，网格搜索通过将每个超参数 \(h_i\) 离散化为一组值 \(h_{i1}, h_{i2}, \dots, h_{in_i}\) 来详尽搜索超参数空间，其中 \(n_i\) 是第 \(i\) 个超参数的值的数量。网格搜索配置的总数由以下公式给出：

$$
N_{\text{grid}} = \prod_{i=1}^{d} n_i, \tag{346}
$$

网格搜索的计算成本为 \(O(N_{\text{grid}} \cdot C)\)，它随超参数数量 \(d\) 呈指数增长。从这个意义上说，当超参数空间的维度 \(d\) 较大时，网格搜索可能变得极其昂贵。另一方面，随机搜索需要



只需 $T$ 次评估，并且由于每次评估相互独立，计算成本随 $T$ 线性增长，当 $d$ 较大时效率更高。随机搜索的概率性质进一步提升了其效率。假设只有部分超参数（例如 $k$）显著影响模型性能。令 $S$ 为 $\mathcal{H}$ 的子空间，由产生低损失值的超参数配置组成；令补空间 $\mathcal{H} \setminus S$ 对应不太可能实现低损失的配置。在这种情况下，任务变为在子空间 $S$ 中搜索，而非整个空间 $\mathcal{H}$。随机搜索方法非常适合此类问题，因为它可以通过从优先考虑超参数空间中低损失区域的分布 $\mathcal{D}_i$ 中抽取超参数值，从而从概率上关注相关子空间。更正式地说，从相关子空间 $S$ 选择超参数集 $\mathbf{h}_t$ 的概率由：

\(P(\mathbf{h}_t \in S) = \prod_{i=1}^d P(h_{t,i} \in S_i),\quad (347)\)

给出，其中 \(S_i\) 是第 \(i\) 个超参数的相关区域，\(P(h_{t,i} \in S_i)\) 是第 \(i\) 个超参数位于相关区域内的概率。随着迭代次数 \(T\) 增加，随机搜索选择超参数集 \(\mathbf{h}_t \in S\) 的概率也随之增加，当 \(T \to \infty\) 时趋近于 1：

\(P(\mathbf{h}_t \in S) = 1 - (1 - P_0)^T,\quad (348)\)

其中 \(P_0\) 是一次迭代中从相关子空间采样超参数集的概率。因此，随机搜索倾向于探索低损失配置的子空间，随着 \(T\) 增加，找到最优或近似最优配置的机会随之提高。

随机搜索的探索行为与网格搜索形成对比。尽管网格搜索具有系统性，但可能无法有效探索超参数空间中分布稀疏的区域。当超参数空间为高维时，无论超参数的相关性如何，网格搜索都必须评估指数级多的配置。当只有小部分超参数对损失函数有显著贡献时，这会导致低效。随机搜索通过在整个空间中独立且均匀地采样，不受维度灾难的影响，能够更有效地定位对模型性能至关重要的区域。从数学角度看，当超参数与损失函数呈现平滑或连续关系时，随机搜索具有额外优势。在这种情况下，随机搜索可以从概率上探测空间，发现网格搜索因其固定网格结构可能遗漏的损失梯度。此外，即使损失函数为非凸函数，只要空间被充分探索，随机搜索也能找到最优解。在存在高度不规则损失曲面的情况下，这一点尤其相关，因为随机搜索比受限于其固定采样网格的网格搜索更有可能有效地逃离局部最小值。

综上所述，随机搜索是机器学习中超参数优化的一种高效且可扩展的方法。通过从预定义概率分布中采样超参数并评估相关损失函数，随机搜索为高维超参数空间提供了一种计算上可行的方法，在许多情况下优于网格搜索。其概率性质使其能够关注超参数空间的相关区域，因此在只有部分超参数对模型性能产生显著影响时尤其有利。随着迭代次数 \(T\) 增加，随机搜索更有可能收敛到最优配置，使其成为复杂模型超参数调优的强大工具。

### 6.4.3 贝叶斯优化

文献综述：Chang 等人（2025）[414] 在用于预测滑坡位移的机器学习模型中应用了贝叶斯优化（BO）进行超参数调优。该研究探讨了 BO 在优化支持向量机（SVM）、长短期记忆网络（LSTM）和门控循环单元（GRU）方面的影响，展示了贝叶斯技术如何提高模型精度和收敛速度。Cihan（2025）[415] 使用贝叶斯优化来微调 XGBoost、LightGBM、弹性网络（Elastic Net）和自适应增强（Adaptive Boosting）模型，用于预测生物质气化产出。研究发现，贝叶斯优化在降低计算开销的同时提高预测精度，优于网格搜索和随机搜索。Makomere 等人（2025）[416] 将贝叶斯优化集成到基于深度学习的工业过程建模中进行超参数调优。该研究提供了关于 BO 如何提高模型泛化能力并减少化学过程监测中预测误差的见解。Bakir（2025）[417] 引入了 TuneDroid，这是一个基于贝叶斯优化的自动化框架，用于网络安全中卷积神经网络（CNN）的超参数调优。结果表明，贝叶斯优化在加快模型训练的同时提高了恶意软件检测精度。Khurshid 等人（2025）[404] 比较了基于 XGBoost 的糖尿病预测模型中贝叶斯优化和随机搜索的超参数调优。研究得出结论，与传统搜索方法相比，贝叶斯优化在速度和精度之间提供了更好的权衡。Liu 等人（2025）[418] 探索了贝叶斯优化在微调深度学习模型以预测工程系统声学性能方面的能力。作者展示了贝叶斯方法如何在降低计算成本的同时提高预测精度。Balcan 等人（2025）[411] 对深度学习中贝叶斯优化所需的样本复杂性进行了严谨分析。研究结果表明，与其他超参数调优技术相比，贝叶斯优化收敛到最优解所需的样本更少。Ma 等人（2025）[419] 将贝叶斯优化与支持向量机（SVM）集成，用于高速加工中的异常检测。他们发现，贝叶斯优化允许更有效地探索超参数空间，从而提高模型可靠性。Bouzaidi 等人（2025）[420] 探索了贝叶斯优化对基于 CNN 的图像分类模型的影响。研究展示了贝叶斯技术如何在迁移学习场景中优于网格搜索等传统方法。Mustapha 等人（2025）[421] 将贝叶斯优化集成到结合卷积神经网络（CNN）和视觉变换器（ViT）的混合深度学习框架中，用于肺炎检测。结果证实，贝叶斯优化提高了医学影像中多模态架构的效率。

贝叶斯优化（BO）是一种强大且在数学上精巧的方法，用于优化复杂的黑盒目标函数，在机器学习模型的超参数调优背景下尤其有用。这些目标函数（记为 $f : \mathcal{X} \rightarrow \mathbb{R}$）通常由于模型训练耗时或观测含噪等因素而评估代价高昂。在超参数调优中，目标函数通常表示机器学习模型在特定超参数配置下的某些性能指标（例如，准确率、误差或损失）。贝叶斯优化的目标是找到超参数设置 $\mathbf{x}^* \in \mathcal{X}$，以最小化（或最大化）目标函数，使得：

$$\mathbf{x}^* = \arg \min_{\mathbf{x} \in \mathcal{X}} f(\mathbf{x})$$ (349)

由于穷举搜索在计算上不可行，BO 采用概率方法来高效探索超参数空间。这是通过将目标函数 $f(\mathbf{x})$ 视为随机函数，并利用 **代理模型** 来近似它来实现的，从而允许对空间 $\mathcal{X}$ 中哪些点进行评估做出战略决策。代理模型通常由 **高斯过程 (GP)** 表示，该过程在 $\mathcal{X}$ 的任何一点提供预测和不确定性估计。GP 是一种非参数概率模型，假设任何有限点集上的函数值服从联合高斯分布。具体而言，对于一个



一组观测点 $\{ \mathbf{x}_1, \mathbf{x}_2, \dots, \mathbf{x}_n \}$，相应的函数值 $\{ f(\mathbf{x}_1), f(\mathbf{x}_2), \dots, f(\mathbf{x}_n) \}$ 被假设服从如下联合分布：

```
\(\begin{bmatrix} f(\mathbf{x}_1) \\ f(\mathbf{x}_2) \\ \vdots \\ f(\mathbf{x}_n) \end{bmatrix} \sim \mathcal{N}(\mathbf{m}, \mathbf{K})\)
```

其中 $\mathbf{m} = [m(\mathbf{x}_1), m(\mathbf{x}_2), \dots, m(\mathbf{x}_n)]^\top$ 是均值向量，$\mathbf{K}$ 是协方差矩阵，其元素由协方差（或核）函数 $k(\mathbf{x}, \mathbf{x}')$ 定义，该函数编码了关于目标函数平滑性和周期性的假设。核函数在确定高斯过程的性质方面起着至关重要的作用。一种常用的核函数是 **平方指数（SE）核函数**，其定义为：

```
\(k(\mathbf{x}, \mathbf{x}') = \sigma_f^2 \exp \left( - \frac{\| \mathbf{x} - \mathbf{x}' \|^2}{2\ell^2} \right)\)
```

其中 $\sigma_f^2$ 是方差，用于缩放函数值，$\ell$ 是长度尺度，它通过规定函数值随输入变化的速度来控制函数的平滑度。一旦高斯过程被指定，贝叶斯优化将在每次新评估后更新目标函数上的后验分布。给定一组 $n$ 个观测对 $\{ (\mathbf{x}_i, y_i) \}_{i=1}^n$，其中 $y_i = f(\mathbf{x}_i) + \epsilon_i$ 且 $\epsilon_i \sim \mathcal{N}(0, \sigma^2)$ 表示观测噪声，我们更新高斯过程的后验以反映观测数据。在新点 $\mathbf{x}_*$ 处的后验均值 $\mu(\mathbf{x}_*)$ 和方差 $\sigma^2(\mathbf{x}_*)$ 由以下方程给出：

```
\(\mu(\mathbf{x}_*) = \mathbf{k}_*^\top \mathbf{K}^{-1} \mathbf{y}\)
\(\sigma^2(\mathbf{x}_*) = k(\mathbf{x}_*, \mathbf{x}_*) - \mathbf{k}_*^\top \mathbf{K}^{-1} \mathbf{k}_*\)
```

其中 $\mathbf{k}_*$ 是测试点 $\mathbf{x}_*$ 与观测点 $\mathbf{x}_1, \mathbf{x}_2, \dots, \mathbf{x}_n$ 之间的协方差向量，$\mathbf{K}$ 是观测点的协方差矩阵。更新后的均值 $\mu(\mathbf{x}_*)$ 提供了模型对 $\mathbf{x}_*$ 处函数值的最佳估计，而 $\sigma^2(\mathbf{x}_*)$ 量化了与该估计相关的不确定性。

在贝叶斯优化中，核心目标是选择下一个要评估的超参数设置 $\mathbf{x}_*$，以便在仍朝着全局最优方向取得进展的同时，将函数评估次数最小化。这是通过优化一个 **获取函数** 来实现的。获取函数 $\alpha(\mathbf{x})$ 代表在输入空间中利用目标函数预期较低的区域与探索模型不确定性较高的区域之间的权衡。已提出多种获取函数，包括 **预期改进（EI）**、**改进概率（PI）** 和 **置信上界（UCB）**。 **预期改进（EI）** 获取函数是最广泛使用的函数之一，定义如下：

```
\(\text{EI}(\mathbf{x}) = (f_{\text{best}} - \mu(\mathbf{x})) \Phi \left( \frac{f_{\text{best}} - \mu(\mathbf{x})}{\sigma(\mathbf{x})} \right) + \sigma(\mathbf{x}) \phi \left( \frac{f_{\text{best}} - \mu(\mathbf{x})}{\sigma(\mathbf{x})} \right)\)
```

其中 $f_{\text{best}}$ 是目标函数的最佳观测值，$\Phi(\cdot)$ 和 $\phi(\cdot)$ 分别是标准正态分布的累积分布函数和概率密度函数，$\sigma(\mathbf{x})$ 是 $\mathbf{x}$ 处的标准差。第一项衡量改进的潜力，并按实现该改进的概率加权，第二项反映 $\mathbf{x}$ 处的不确定性，鼓励在不确定区域进行探索。在每次迭代中，通过最大化获取函数来选择下一个点 $\mathbf{x}_*$：

```
\(\mathbf{x}_* = \arg \max_{\mathbf{x} \in \mathcal{X}} \text{EI}(\mathbf{x})\)
```

另一种获取函数是 **改进概率（PI）**，它更简单，并直接衡量在 **x** 处的目标函数超过当前最佳值的概率：

\(\text{PI}(\mathbf{x}) = \Phi \left( \frac{f_{\text{best}} - \mu(\mathbf{x})}{\sigma(\mathbf{x})} \right) \quad (356)\)

另一种常见的获取函数是 **置信上界（UCB）**，它通过选择具有最高置信上界的点来平衡探索和利用：

\(\text{UCB}(\mathbf{x}) = \mu(\mathbf{x}) + \kappa\sigma(\mathbf{x}) \quad (357)\)

其中 \(\kappa\) 是一个超参数，用于控制探索（\(\kappa\) 较大）和利用（\(\kappa\) 较小）之间的权衡。选择 \(\mathbf{x}_*\) 后，在此点评估函数，并利用观测值 \(y_* = f(\mathbf{x}_*)\) 更新高斯过程的后验分布。这一过程不断迭代，每次新的观测都会改进模型对目标函数的理解，从而引导对最优 \(\mathbf{x}^*\) 的搜索。贝叶斯优化的主要优势之一在于，其能够通过将搜索集中在输入空间最有前景的区域，高效地优化评估成本高昂的函数。然而，随着观测数量的增加，由于需要逆转协方差矩阵 \(\mathbf{K}\)，维护高斯过程模型的计算复杂度会随点数立方增长。这种立方复杂度 \(\mathcal{O}(n^3)\) 对于大型数据集来说可能是不可接受的。为缓解这一问题，已发展出 **稀疏高斯过程** 等技术，这些技术通过使用更小的一组诱导点来近似完整的协方差矩阵，从而在降低计算成本的同时保持高斯过程模型的灵活性。

综上所述，贝叶斯优化是一种数学严谨且高效的超参数调优方法，其中使用高斯过程代理模型来近似未知的目标函数，获取函数通过平衡探索和利用来引导对最优解的搜索。尽管存在计算挑战，尤其是在高维问题中，该方法在评估目标函数成本高昂的场景中广泛适用，并且已被证明在许多实际场景中优于传统优化技术。

# 7 卷积神经网络

## 文献综述

Goodfellow et. al. (2016) [112] 撰写了深度学习领域最奠基性的教材之一，深入介绍了卷积神经网络。该书介绍了包括卷积、反向传播和优化方法在内的理论原理，同时也讨论了卷积神经网络在图像处理及其他领域的应用。LeCun et. al. (2015) [117] 对卷积神经网络和深度学习进行了历史概述。LeCun 是卷积神经网络的发明者之一，他解释了为什么卷积有助于图像识别，并讨论了它们在视觉、语音和强化学习中的应用。Krizhevsky et. al. (2012) [146] 和 Krizhevsky et. al. (2017) [147] 介绍了 AlexNet，即第一个现代深度卷积神经网络，它赢得了 2012 年 ImageNet 挑战赛。这表明深度卷积神经网络可以在图像分类任务中达到前所未有的准确性，为深度学习的主导地位铺平了道路。Simonyan 和 Zisserman (2015) [148] 介绍了 VGGNet，表明使用小型 3x3 卷积增加网络深度可以提高性能。它还提供了关于层设计选择及其对准确性影响的见解。He et. al. (2016) [149] 介绍了 ResNet，它通过使用跳跃连接解决了深度网络中的梯度消失问题。这一革命性的卷积神经网络设计允许训练深度高达 1000 层的模型。Cohen 和 Welling (2016) [150] 利用群论扩展了卷积神经网络，实现了等变特征学习。这提高了卷积神经网络对旋转和平移的鲁棒性，使其在基于对称性的任务中更加高效。Zeiler 和 Fergus (2014) [151] 引入了反卷积技术来可视化卷积神经网络特征图，使其更容易解释和调试。它展示了不同



层检测模式、纹理和对象。Liu et al. (2021) [152] 引入了视觉变换器（Vision Transformers，ViTs），在某些视觉任务中优于 CNN。本文讨论了 CNN 的局限性以及变换器如何与 CNN 架构混合。Lin et al. (2013) [153] 引入了 1x1 卷积，提高了特征学习效率。这一概念成为 ResNet 和 MobileNet 等现代 CNN 架构的关键组件。Rumelhart et al. (1986) [154] 形式化了反向传播，这是用于 CNN 的训练方法。如果没有这一发现，CNN 和深度学习今天将不会存在。

## 7.1 关键概念

卷积神经网络（Convolutional Neural Network，CNN）是一种深度学习模型，主要用于分析网格状数据，例如图像、视频以及具有空间或时间依赖性的时间序列数据。CNN 的基本操作是 **卷积** 操作，用于从输入数据中提取局部模式。CNN 的输入通常表示为张量 \(\mathbf{I} \in \mathbb{R}^{H \times W \times C}\)，其中 \(H\) 是高度，\(W\) 是宽度，\(C\) 是通道数（对于 RGB 图像，\(C = 3\)）。

CNN 的核心是卷积层，其中输入图像 \(\mathbf{I}\) 与一组滤波器或核 \(\mathbf{K} \in \mathbb{R}^{f_h \times f_w \times C}\) 进行卷积，其中 \(f_h\) 和 \(f_w\) 分别是滤波器的高度和宽度。滤波器 \(\mathbf{K}\) 在输入图像 \(\mathbf{I}\) 上滑动，此卷积的结果是一组特征图，指示图像中的某些局部模式。特征图上位置 \((i, j)\) 处的逐元素卷积由以下公式给出：

\(\mathbf{I} * \mathbf{K} = \sum_{p=1}^{f_h} \sum_{q=1}^{f_w} \sum_{r=1}^{C} \mathbf{I}_{i+p-1, j+q-1, r} \cdot \mathbf{K}_{p,q,r}\) (358)

其中 \(\mathbf{I}_{i+p-1, j+q-1, r}\) 表示输入图像在位置 \((i + p - 1, j + q - 1)\) 处第 \(r\) 个通道的值，\(\mathbf{K}_{p,q,r}\) 是 \((p, q, r)\) 处的相应滤波器值。此操作对输出特征图的每个位置 \((i, j)\) 执行。生成的特征图 \(\mathbf{F}\) 具有空间尺寸 \(H' \times W'\)，其中：

\(H' = \left\lfloor \frac{H + 2p - f_h}{s} \right\rfloor + 1, \quad W' = \left\lfloor \frac{W + 2p - f_w}{s} \right\rfloor + 1\) (359)

其中 \(p\) 是填充，\(s\) 是滤波器滑动过程中的步幅。卷积操作提供输入图像的平移不变表示，因为每个滤波器在整个图像中检测模式。在此卷积之后，通常会应用非线性激活函数，即 **整流线性单元（Rectified Linear Unit，ReLU）**，以向网络引入非线性并确保其能够建模复杂模式。ReLU 激活函数按元素操作，并由以下公式给出：

\(\text{ReLU}(x) = \max(0, x)\) (360)

因此，对于每个特征图 \(\mathbf{F}\)，ReLU 后的输出为：

\(\mathbf{F}'_{i,j,k} = \max(0, \mathbf{F}_{i,j,k})\) (361)

这确保了特征图中的负值被丢弃，有助于激活的稀疏表示，减轻了深层中的梯度消失问题。在 CNN 中，池化操作紧随卷积层和激活层之后。池化用于降低特征图的空间尺寸，从而降低计算复杂度，并使表示更不受平移影响。**最大池化** 是最常见的形式，它在指定窗口大小 \(p_h \times p_w\) 内选择最大值。给定输入特征图 \(\mathbf{F} \in \mathbb{R}^{H' \times W' \times K}\)，最大池化按以下方式操作：

\(\mathbf{P}_{i,j,k} = \max (\mathbf{F}_{i,j,k}, \mathbf{F}_{i+1,j,k}, \mathbf{F}_{i,j+1,k}, \mathbf{F}_{i+1,j+1,k})\) (362)

其中 **P** 是池化后的特征图。此池化操作有效地降低了每个特征图的空间尺寸，生成输出 $\mathbf{P} \in \mathbb{R}^{H'' \times W'' \times K}$，其中：

$$H'' = \left\lfloor \frac{H'}{p_h} \right\rfloor, \quad W'' = \left\lfloor \frac{W'}{p_w} \right\rfloor$$ (363)

最大池化通过仅捕获局部区域内最强的特征、丢弃无关信息并确保网络对小平移具有不变性，引入了一种鲁棒性。CNN 架构通常包含多个卷积层，随后跟有池化层。经过这些操作后，特征图被展平为一维向量，并传入一个或多个 **全连接（稠密）层**。全连接层计算如下形式的线性变换：

$$\mathbf{z}^{(l)} = \mathbf{W}^{(l)}\mathbf{a}^{(l-1)} + \mathbf{b}^{(l)}$$ (364)

其中 $\mathbf{a}^{(l-1)}$ 是层的输入，$\mathbf{W}^{(l)}$ 是权重矩阵，$\mathbf{b}^{(l)}$ 是偏置向量。此线性变换的输出随后通过非线性激活函数（例如用于分类任务的 ReLU 或 softmax）传递。对于分类，通常应用 **softmax** 函数将输出转换为概率分布：

$$\mathbf{y}_i = \frac{\exp(z_i)}{\sum_{j=1}^C \exp(z_j)}$$ (365)

其中 $C$ 是输出类别的数量，$\mathbf{y}_i$ 是第 $i$ 个类别的概率。softmax 函数确保输出概率之和为 1，从而提供有效的分类输出。CNN 使用 **反向传播** 进行训练，它计算损失函数 $\mathcal{L}$ 相对于网络参数（即权重和偏置）的梯度。反向传播使用 **链式法则** 将误差梯度通过每一层传播。相对于卷积滤波器 $\mathbf{K}$ 的梯度由以下公式计算：

$$\frac{\partial \mathcal{L}}{\partial \mathbf{K}} = \frac{\partial \mathcal{L}}{\partial \mathbf{F}} * \mathbf{I}$$ (366)

其中 $*$ 表示卷积操作。同样，全连接层的梯度由以下公式计算：

$$\frac{\partial \mathcal{L}}{\partial \mathbf{W}^{(l)}} = \mathbf{a}^{(l-1)} \cdot \frac{\partial \mathcal{L}}{\partial \mathbf{z}^{(l)}}$$ (367)

计算梯度后，使用诸如 **梯度下降** 之类的优化算法更新权重：

$$\mathbf{W}^{(l)} \leftarrow \mathbf{W}^{(l)} - \eta \frac{\partial \mathcal{L}}{\partial \mathbf{W}^{(l)}}$$ (368)

其中 $\eta$ 是学习率。此优化确保网络参数沿负梯度方向调整，最小化损失函数，从而提高 CNN 的性能。通常会应用正则化技术以避免过拟合。例如，**脱校正（Dropout）** 在训练期间随机停用一部分神经元，防止网络过度依赖任何特定特征，并促进更好的泛化能力。给定层 $l$ 上具有脱校正率 $p$ 的脱校正操作定义为：

$$\mathbf{a}^{(l)} \sim \text{Dropout}(\mathbf{a}^{(l)}, p)$$ (369)

其中激活 $\mathbf{a}^{(l)}$ 以概率 $p$ 随机设置为零，其余激活按 $\frac{1}{1-p}$ 缩放。另一种正则化技术是 **批量归一化**，它将每层的输入归一化为零均值和单位方差，从而提高训练速度和稳定性。在数学上，批量归一化定义为：

$$\hat{x} = \frac{x - \mu_B}{\sigma_B}, \quad \mathbf{y} = \gamma \hat{x} + \beta$$ (370)

其中 \(\mu_B\) 和 \(\sigma_B\) 是批次的均值和标准差，\(\gamma\) 和 \(\beta\) 是学习的缩放和平移参数。

总之，**卷积神经网络（Convolutional Neural Network，CNN）** 的数学支柱高度依赖于卷积操作、非线性激活、池化和全连接变换。卷积层通过对输入数据应用滤波器来提取层次化特征，而池化降低空间尺寸并引入平移不变性。全连接层将这些特征聚集用于分类或回归任务。网络使用反向传播和诸如梯度下降之类的优化技术进行训练。使用诸如脱校正和批量归一化之类的正则化方法来提高泛化能力和训练效率。CNN 背后的数学形式主义对于理解其在各种机器学习任务（尤其是计算机视觉）中的强大能力至关重要。

## 7.2 图像处理中的应用

### 7.2.1 图像分类

文献综述：Thiriveedhi et al. (2025) [185] 提出了一种基于 CNN 的新型架构，用于诊断急性淋巴细胞白血病（Acute Lymphoblastic Leukemia，ALL），集成了可解释人工智能（Explainable AI，XAI）技术。所提出的模型通过为医学图像分类提供人类可解释的见解，优于传统 CNN。该研究突出了 CNN 如何能够有效应用于医学成像并提高透明度。Ramos-Briceño et al. (2025) [186] 展示了 CNN 在疟原虫检测中的卓越分类准确率。该研究使用深度 CNN 对血液样本中的疟疾种类进行分类，并达到了最先进的性能。该论文为生物医学应用中的基于 CNN 的图像分类提供了有价值的见解。Espino-Salinas et al. (2025) [187] 将 CNN 应用于心理健康诊断，通过将运动活动模式分类为图像。该论文探讨了 CNN 超越传统图像分类的新应用，将时间序列数据转换为可视化表示，并利用 CNN 检测精神障碍。Ran et al. (2025) [188] 引入了一种基于 CNN 的高光谱成像方法，用于早期诊断胰腺神经内分泌肿瘤。该论文强调了 CNN 处理多光谱数据以用于复杂医学成像任务的能力，进一步扩展了其在病理学和癌症检测中的实用性。Araujo et al. (2025) [189] 演示了如何在工业监控和预测性维护中使用 CNN。该研究介绍了一种基于 CNN 的创新方法，利用热成像检测 ZnO 避雷器中的故障，证明了 CNN 在无损检测应用中的鲁棒性。Sari et al. (2025) [190] 将 CNN 应用于文化遗产保护，具体为蜡染图案分类。该研究展示了 CNN 在精细图像分类中的适应性，并强调了深度学习在自动化纺织图案识别中的重要性。Wang et al. (2025) [191] 提出了 CF-WIAD，一种新型半监督学习方法，利用 CNN 进行皮肤病变分类。该研究演示了如何有效地使用 CNN 分类皮肤病学图像，特别是在低数据环境中，这是医学 AI 的关键挑战。Cai et al. (2025) [192] 引入了 DFNet，一种基于 CNN 的残差网络，通过结合差分特征来改进特征提取。该研究强调了 CNN 在高级特征工程中的作用，这对于面部识别和对象分类等应用至关重要。Vishwakarma and Deshmukh (2025) [193] 提出了 CNNM-FDI，一种基于 CNN 的火灾检测模型，增强了实时安全监控。该研究探讨了 CNN 在环境监测中的应用，强调了早期灾害预防的快速响应分类模型。Ranjan et al. (2025) [194] 将 CNN、自编码器（Autoencoders）、GAN 和零样本学习（Zero-Shot Learning）相结合，以改进高光谱图像分类。该研究强调了如何通过生成模型增强 CNN 来提高有限标签数据集中的分类性能，这是遥感应用中的关键领域。

卷积神经网络（CNNs）中图像分类的过程涉及一个复杂的sophisti-



cated 线性代数、微积分、概率论和优化的相互作用。主要目标是将高维输入图像映射到特定类别标签。令 \(\mathbf{I} \in \mathbb{R}^{H \times W \times C}\) 表示输入图像，其中 \(H, W\) 和 \(C\) 分别是图像的高度、宽度和通道数（通常 RGB 图像为 3）。图像的每个像素可以表示为 \(\mathbf{I}(i, j, c)\)，它表示像素位置 \((i, j)\) 处 \(c\) 通道的强度。CNN 的目标是通过包含卷积、非线性、池化和全连接层的分层特征提取过程，将原始输入图像转换为标签，通常为 \(M\) 个类别之一。

卷积操作是 CNN 的核心，并构成特征提取过程的基础。令 \(\mathbf{K} \in \mathbb{R}^{k \times k \times C}\) 为一个空间尺寸为 \(k \times k\) 且具有 \(C\) 个通道的滤波器（或内核），其中 \(k\) 通常是小奇整数，如 3 或 5。滤波器 \(\mathbf{K}\) 与输入图像 \(\mathbf{I}\) 进行卷积以生成特征图 \(\mathbf{S} \in \mathbb{R}^{(H-k+1) \times (W-k+1) \times F}\)，其中 \(F\) 是卷积中使用的滤波器数量。对于特征图中的给定空间位置 \((i, j)\)，卷积操作定义为：

```
\(\mathbf{S}_{i,j,f} = \sum_{m=0}^{k-1} \sum_{n=0}^{k-1} \sum_{c=0}^{C-1} \mathbf{I}(i+m, j+n, c) \cdot \mathbf{K}_{m,n,c,f} \tag{371}\)
```

其中 \(\mathbf{S}_{i,j,f}\) 表示对应于第 \(f\) 个滤波器的特征图中位置 \((i, j)\) 处的值。该操作计算像素 \((i, j)\) 周围 \(k \times k \times C\) 感受野内像素值的加权和，权重由滤波器值给出。结果是一张新特征图，捕捉图像中的边缘或纹理等局部模式。这种局部特征提取在整个图像的每个位置 \((i, j)\) 上执行，为每个滤波器生成一组特征图。为了向网络引入非线性并使其能够建模复杂函数，将特征图 \(\mathbf{S}\) 传递通过非线性激活函数，通常是整流线性单元 (ReLU)，其按元素定义为：

```
\(\sigma(x) = \max(0, x) \tag{372}\)
```

该激活函数对负值输出 0，并将正值保持不变，确保网络能够学习复杂的非线性关系。特征图的激活函数输出表示为 \(\mathbf{S}^+\)，其中 \(\mathbf{S}^+\) 的每个元素计算如下：

```
\(\mathbf{S}^+_{i,j,f} = \max(0, \mathbf{S}_{i,j,f}) \tag{373}\)
```

这种按元素操作增强了网络捕获和表示复杂模式的能力，从而有助于学习过程。在卷积和激活之后，特征图通过池化操作进行下采样。最常见的池化形式是最大池化，它选择特征图局部区域中的最大值。给定大小为 \(p \times p\) 和步长为 \(s\) 的池化窗口，特征图 \(\mathbf{S}^+\) 的最大池化操作由以下公式给出：

```
\(\mathbf{P}_{i,j,f} = \max_{(u,v) \in p \times p} \mathbf{S}^+_{i+u, j+v, f} \tag{374}\)
```

其中 \(\mathbf{P}\) 表示池化后的特征图。该操作将特征图的空间尺寸降低 \(p\) 倍，同时保留每个区域中最重要的特征。池化具有多种用途，包括降维、平移不变性和噪声降低。它还通过限制网络中的参数和计算数量来帮助防止过拟合。

一旦通过卷积、激活和池化获得特征图，它们将被展平为一个一维向量 \(\mathbf{F} \in \mathbb{R}^N\)，其中 \(N\) 是池化后特征图中的元素总数。然后将展平向量 \(\mathbf{F}\) 输入到一个或多个全连接层。这些层对输入执行线性变换，本质上是输入的加权和，随后加上偏置项。全连接层的输出可以表示为：

\(\mathbf{O} = \mathbf{W} \cdot \mathbf{F} + \mathbf{b}\) (375)

其中 \(\mathbf{W} \in \mathbb{R}^{M \times N}\) 是权重矩阵，\(\mathbf{b} \in \mathbb{R}^M\) 是偏置向量，\(\mathbf{O} \in \mathbb{R}^M\) 是每个 \(M\) 个类别的原始输出或 logit。全连接层根据卷积层和池化层学习到的特征计算各类别的一组 logits。为了将 logits 转换为类别概率，应用 **softmax** 函数。softmax 函数是 logistic 函数到多类的推广，将 logits 转换为概率分布。类别 \(k\) 的概率由以下公式给出：

\( P(y = k \mid \mathbf{O}) = \frac{e^{O_k}}{\sum_{k=1}^M e^{O_k}} \) (376)

其中 \(O_k\) 是类别 \(k\) 对应的 logit，分母确保所有类别的概率之和为 1。选择概率最高的类别标签作为最终预测：

\( y = \arg \max_k P(y = k \mid \mathbf{O}) \) (377)

预测基于计算的类别概率进行，网络在训练期间旨在最小化预测概率与真实标签之间的差异。为了优化网络参数，我们最小化一个 **损失函数**，它衡量预测概率与实际标签之间的差异。**交叉熵损失**常用于分类任务，定义为：

\( \mathcal{L} = - \sum_{k=1}^M y_k \log P(y = k \mid \mathbf{O}) \) (378)

其中 \(y_k\) 是 one-hot 编码的真实标签，\(P(y = k \mid \mathbf{O})\) 是类别 \(k\) 的预测概率。训练的目标是最小化此损失函数，这相当于在预测概率分布下最大化正确类别的似然性。

网络参数的优化使用 **梯度下降** 及其变体，例如随机梯度下降 (SGD)，这些方法根据损失函数的梯度迭代更新参数。梯度使用 **反向传播** 计算，该方法应用微积分的链式法则来计算损失对每个参数的偏导数。对于全连接层，损失对权重 \(\mathbf{W}\) 的梯度由以下公式给出：

\( \nabla_\mathbf{W} \mathcal{L} = \frac{\partial \mathcal{L}}{\partial \mathbf{O}} \cdot \frac{\partial \mathbf{O}}{\partial \mathbf{W}} = \delta \cdot \mathbf{F}^T \) (379)

其中 \(\delta = \frac{\partial \mathcal{L}}{\partial \mathbf{O}}\) 是 logits 的误差项（也称为 delta），\(\mathbf{F}^T\) 是展平特征向量的转置。参数使用以下规则更新：

\( \mathbf{W} \leftarrow \mathbf{W} - \eta \nabla_\mathbf{W} \mathcal{L} \) (380)

其中 \(\eta\) 是学习率，控制更新的步长。此过程对每个批次的训练数据重复执行，直到网络收敛到一组最小化损失函数的参数。通过这种复杂且迭代的过程，CNN 能够通过从原始输入数据中自动提取分层特征来学习对图像进行分类。卷积、激活、池化和全连接层的组合使网络能够学习输入图像的越来越抽象和高级别的表示，最终在图像分类任务中实现高准确性。

### 7.2.2 对象检测

文献综述：Naseer 和 Jalal (2025) [195] 提出了一种集成 RGB-D 图像的多模态深度学习框架，用于增强语义场景分类。该研究利用基于卷积神经网络 (CNN) 的对象检测模型来提取和处理 RGB 和深度图像的特征，旨在提高杂乱和复杂环境中的场景识别准确性。通过引入多模态输入，该模型有效解决了传统对象检测框架中常见的遮挡和背景噪声问题。研究人员展示了当 CNN 与深度感知语义信息相结合时，如何显著增强对象定位和分类性能。通过广泛评估，他们验证了其框架优于各种实际场景中的传统单流 CNN，为深度学习基于的对象检测系统中 RGB-D 集成提供了有力依据。Wang 和 Wang (2025) [196] 在 Faster R-CNN 对象检测框架基础上构建，引入了一种显著提高高度动态和复杂环境下检测准确性的新改进。该研究提出了一种优化的锚框生成机制，使网络能够高效检测不同尺寸和宽高比的对象，特别是小型或严重遮挡的对象。通过引入精炼的区域建议网络 (RPN)，作者减轻了定位错误并降低了假正检测。论文还探讨了特征金字塔网络 (FPN) 在分层特征提取中的影响，证明了其在提高细粒度细节检测方面的有效性。作者进行了广泛的实证评估，将其改进的 Faster R-CNN 模型与现有对象检测架构进行比较，证明其在精度和召回率方面表现出色，尤其适用于涉及自定义图标生成和用户界面设计的应用。Ramana 等人 (2025) [197] 引入了一种深度卷积图神经网络 (DCGNN)，它集成光谱金字塔池化 (SPP) 和融合关键点生成，以显著提高 3D 对象检测性能。该研究将 ResNet-50 用作骨干 CNN 架构，并通过引入多尺度光谱特征聚合增强其特征提取能力。通过集成图神经网络 (GNN)，该模型能够有效捕获对象组件之间的空间关系，从而实现高度准确的 3D 边界框预测。所提方法在多个基准数据集上经过严格评估，展示了其处理遮挡、尺度变化和视角变化的卓越能力。此外，论文提出了一种新颖的融合策略，将基于关键点的对象表示与光谱域特征嵌入相结合，使模型在自动化 3D 对象检测任务中实现无与伦比的鲁棒性。Shin 等人 (2025) [198] 探讨了基于深度学习的对象检测在微流体和液滴基生物工程领域的应用。作者利用 YOLOv10n，一种先进的基于 CNN 的对象检测框架，开发了一种用于跟踪和分类高通量实验设置中双重乳液液滴的自动化系统。通过微调 YOLO 架构，该研究在检测灵敏度和分类准确性方面取得了显著提升，实现了液滴形态、相分离动态和稳定性特征的实时识别。研究人员进一步引入了一种自适应特征精炼策略，其中 CNN 模型不断从实时实验变化中学习，从而实现液滴误分类的自动校准和纠正。论文还展示了这种 AI 驱动方法在药物递送系统、封装技术和合成生物学应用中的实际意义。Taca 等人 (2025) [199] 对多种基于 CNN 的对象检测架构应用于大规模农业数据集的蚜虫分类进行了全面的比较分析。研究人员评估了 YOLO、SSD、Faster R-CNN 和 EfficientDet 的性能，分析了它们在准确性、推理速度和计算效率方面的权衡。通过涉及 48,000 张标注图像的广泛实验设置，作者证明某些 CNN 模型在特定检测场景中表现出色，例如 YOLO 用于实时蚜虫定位，Faster R-CNN 用于高精度分类。此外，论文引入了一种创新的混合集成策略，结合


多种 CNN 架构的优势，以实现最佳检测性能。作者在实际农业环境中验证了其研究结果，强调了深度学习驱动的害虫检测在可持续农业实践中的重要性。Ulaş et al. (2025) [200] 探索了基于 CNN 的对象检测在天文学时间序列分析领域的应用，专门针对食双星光曲线中的类振荡模式。该研究系统评估了多种最先进的对象检测模型，包括 YOLO、Faster R-CNN 和 SSD，以确定其在识别指示天体振荡行为的瞬态光度波动方面的有效性。本文的一项关键贡献是引入了一个定制预处理管道，通过小波信号分解技术去除噪声并增强特征可见性来优化原始观测数据。研究人员进一步实现了一种混合检测机制，将基于 CNN 的空间特征提取与循环神经网络（RNNs）相结合，以捕捉光曲线数据集中的空间和时间依赖性。在大规模天文学数据集上的广泛验证表明，这种方法在检测振荡行为方面显著优于传统统计方法，为天体物理事件分类的 AI 驱动自动化铺平了道路。

Valensi et al. (2025) [201] 提出了一个用于肺部超声（LUS）成像中胸膜线检测与分割的高级半监督深度学习框架，充分利用基础模型和基于 CNN 的对象检测架构的强大功能。该研究指出了医学影像中传统完全监督学习的不足，其中标注数据集有限且创建成本高昂。为克服这一挑战，研究人员采用半监督学习策略，结合自训练技术和伪标签来提升模型泛化能力。该框架采用基于 YOLOv8 的对象检测，专门针对医学特征定位进行优化，能显著提升低对比度和高噪声超声图像中的检测精度。此外，该研究集成了多尺度特征提取策略，将卷积层与注意力机制相结合，以确保在不同成像条件下对胸膜线进行精确识别。实验结果表明，这种混合方法显著提高了分割精度，特别是在检测与气胸和胸腔积液相关的微妙异常方面，使其成为临床诊断应用中极具价值的工具。

Arulalan et al. (2025) [202] 提出了一种优化的对象检测管道，将一种新型卷积神经网络（CNN）架构 BS2ResNet 与双向 LSTM（LTK-Bi-LSTM）相结合，以改进时空对象识别。与仅关注静态空间特征的传统基于 CNN 的对象检测器不同，本研究引入了一种同时捕获空间和时间依赖性的混合深度学习框架。所提 BS2ResNet 模型通过使用瓶颈挤压激励模块来增强特征提取，该模块能够选择性强调重要空间信息，同时抑制冗余特征图。此外，集成 LTK-Bi-LSTM 层使模型能够有效捕获时间相关性，从而在动态环境中检测移动对象时具有高度鲁棒性。该方法在多个基准数据集上得到验证，包括自动驾驶和视频监控数据集，在处理遮挡、快速运动和低光照条件方面表现出卓越性能。研究结果表明，将深度卷积网络与基于序列的建模相结合，可显著提高复杂现实场景中对象检测的准确性，为智能交通、安全和实时监控等应用提供关键改进。

Zhu et al. (2025) [203] 研究了一种针对基于 CNN 的对象检测模型的新型对抗攻击策略，重点关注显著性目标检测和伪装目标检测等二值图像分割任务。本文引入了一种高迁移性对抗攻击框架，该框架能够生成对抗性扰动，从而欺骗包括 YOLO、Mask R-CNN 和基于 U-Net 的分割网络在内的广泛深度学习模型。研究人员采用对抗样本增强，其中合成对抗模式通过基于梯度的优化技术迭代优化，确保对抗攻击在不同架构和数据集上仍然有效。一项特别重要的贡献是引入了双阶段攻击管道，其中模型首先学习生成局部的高影响力对抗噪声，然后针对跨模型泛化进行优化。大量实验表明，这种方法显著降低了多种最先进模型的检测性能，揭示了当前基于 CNN 的对象检测器中的关键漏洞。这项研究为深度学习安全提供了宝贵见解，并强调了在自动驾驶系统、医学影像和生物识别安全等关键应用中迫切需要强大的对抗防御机制。

Guo et al. (2025) [204] 引入了一种基于深度学习的农业监测系统，利用 CNN 进行农学实体检测和属性提取。该研究指出了传统基于规则和人工标注系统在农业监测中的局限性，这些系统容易出错且效率低下。通过利用基于 CNN 的对象检测模型，所提系统能够实现实时作物分析，准确识别植株高度、叶片结构和病害症状等关键农学属性。本研究的一项重要创新是引入跨层特征融合，将不同网络深度的多尺度卷积特征相结合，以提高在不同光照和环境条件下检测的鲁棒性。此外，作者采用混合特征选择机制，将空间注意力网络与频谱域特征提取相结合，增强了模型高精度区分健康作物和病害作物的能力。该研究通过严格的田间试验得到验证，表明基于 CNN 的农学监测可以显著提高作物产量预测，减少精准农业中的人工劳动，并优化农业作业中的资源配置。

卷积神经网络（CNNs）中的对象检测是一种多方面的计算过程，同时交织了分类和定位。它涉及检测图像中的对象并通过边界框预测其位置。这一任务可以从数学上分解为分类和回归的综合问题，两者都由深度神经网络的卷积层精细处理。这些层在不同抽象级别提取分层特征，从边缘和角点等低级特征开始，一直到纹理和对象部件等高级语义概念。然后，这些特征图由全连接层处理，用于分类和边界框回归任务。

在数学框架中，设输入图像由矩阵 \( I \in \mathbb{R}^{H \times W \times C} \) 表示，其中 \( H \)、\( W \) 和 \( C \) 分别是高度、宽度和通道数（RGB 图像通常为 3）。CNN 中的卷积操作是提取空间特征层次结构的基本构建块。卷积操作涉及将核 \( K \in \mathbb{R}^{m \times n \times C} \) 应用于输入图像，其中 \( m \) 和 \( n \) 是核的空间维度，\( C \) 是输入通道数。卷积操作通过在图像上滑动核，并计算核与图像块之间的逐元素乘法来执行，从而得到特征图 \( O(x, y) \) 的以下方程：

```
O(x, y) = \sum_{i=0}^{m-1} \sum_{j=0}^{n-1} \sum_{c=0}^{C-1} I(x+i, y+j, c) \cdot K(i, j,c) \qquad (381)
```

这里，\( O(x, y) \) 表示位置 \( (x, y) \) 处的特征图，由应用核 \( K \) 生成。求和是在核在图像上滑动时的空间范围内进行的。这种卷积操作有助于网络捕获输入图像中的局部模式，例如边缘、角点和纹理，这些对于识别对象至关重要。执行卷积后，应用非线性激活函数（如整流线性单元 ReLU）来引入系统的非线性。ReLU 激活函数由以下公式给出：

```
f(x) = \max(0, x) \qquad (382)
```


该激活函数有助于网络建模特征之间复杂的非线性关系，且计算效率高。ReLU的应用确保网络能够学习对象检测等任务所需的复杂决策边界。

在基于CNN的对象检测中，目标是预测对象的类别，并通过边界框定位其位置。边界框由四个坐标参数化：\((x, y)\)表示框的中心，\(w, h\)表示宽度和高度。该任务可视为双重问题：(1) 分类对象，(2) 预测最能编码对象空间位置的边界框。在数学上，这要求网络对图像中每个对象输出类别概率和边界框坐标。分类任务通常使用softmax函数执行，该函数将网络每个类别 \(i\) 的原始输出logits \(z_i\) 转换为概率 \(P(y_i|r)\)。softmax函数定义为：

\(P(y_i|r) = \frac{\exp(z_i)}{\sum_{j=1}^k \exp(z_j)}\) (383)

其中 \(k\) 是可能类别的数量，\(z_i\) 是类别 \(i\) 的原始得分，\(P(y_i|r)\) 是区域 \(r\) 属于类别 \(y_i\) 的概率。该函数确保预测得分是有效概率且总和为一，从而使网络能够就每个区域中对象的类别做出概率性决策。同时，网络还必须为每个对象预测边界框的四个参数。网络预测的边界框参数通常表示为 \(\hat{B} = (\hat{x}, \hat{y}, \hat{w}, \hat{h})\)，而真实边界框表示为 \(B = (x, y, w, h)\)。预测边界框与真实边界框之间的误差使用损失函数来量化，其中平滑 \(L_1\) 损失是边界框回归常用的度量。边界框每个参数的平滑 \(L_1\) 损失定义为：

\(\mathcal{L}_{\text{bbox}} = \sum_{i=1}^4 \text{SmoothL1}(B_i - \hat{B}_i)\) (384)

平滑 \(L_1\) 函数定义为：

\(\text{SmoothL1}(x) = \begin{cases} 0.5x^2 & \text{if } |x| < 1 \\ |x| - 0.5 & \text{if } |x| \ge 1 \end{cases}\) (385)

该损失函数用于减少大误差的影响，从而使训练过程更加鲁棒。目标是在训练阶段最小化此损失，以提高网络预测对象类别和边界框的能力。

训练时，使用结合分类损失和边界框回归损失的组合损失函数。总损失函数可写为：

\(\mathcal{L} = \mathcal{L}_{\text{cls}} + \mathcal{L}_{\text{bbox}}\) (386)

其中 \(\mathcal{L}_{\text{cls}}\) 是分类损失，通常使用预测概率与真实标签之间的交叉熵来计算。分类的交叉熵损失由以下公式给出：

\(\mathcal{L}_{\text{cls}} = -\sum_{i=1}^k y_i \log(\hat{y}_i)\) (387)

其中 \(y_i\) 是真实标签，\(\hat{y}_i\) 是类别 \(i\) 的预测概率。因此，训练的总目标函数是分类损失和边界框回归损失的加权和，网络被优化以最小化此组合损失函数。基于区域的CNN（R-CNN）等对象检测架构采用两阶段方法，将任务分解为生成区域提议和对这些区域进行分类。区域提议网络（RPN）用于生成候选区域 \( r_1, r_2, \dots, r_n \)，然后将其传递给网络以获取其特征表示。随后，全连接层对每个提议执行边界框细化和分类。R-CNN的损失函数结合了每个提议的分类损失和边界框回归损失，目标是最小化：

\(\mathcal{L}_{\text{R-CNN}} = \mathcal{L}_{\text{cls}} + \mathcal{L}_{\text{bbox}}\) (388)

另一种流行的架构是YOLO（You Only Look Once），它将对象检测视为单回归任务。图像被划分为 \( S \times S \) 单元的网格，每个单元预测类别概率和边界框参数。每个单元的输出向量由以下部分组成：

\(\hat{y}_i = (x, y, w, h, c, P_1, P_2, \dots, P_k)\) (389)

其中 \((x, y)\) 是边界框中心的坐标，\(w\) 和 \(h\) 是框的尺寸，\(c\) 是置信度分数，\(P_1, P_2, \dots, P_k\) 是类别概率。YOLO的总损失结合了分类损失、边界框回归损失和置信度损失，可写为：

\(\mathcal{L}_{\text{YOLO}} = \mathcal{L}_{\text{cls}} + \mathcal{L}_{\text{bbox}} + \mathcal{L}_{\text{conf}}\) (390)

其中 \(\mathcal{L}_{\text{cls}}\) 是分类损失，\(\mathcal{L}_{\text{bbox}}\) 是边界框回归损失，\(\mathcal{L}_{\text{conf}}\) 是置信度损失，用于惩罚置信度低的预测。这种方法使YOLO能够在一次网络传递中进行对象检测预测，从而实现更快的推理。单发多框检测器（SSD）通过在多个特征尺度上生成边界框来改进YOLO，从而能够检测不同大小的对象。SSD的损失函数与YOLO类似，由分类损失和边界框定位损失组成，由以下公式给出：

\(\mathcal{L}_{\text{SSD}} = \mathcal{L}_{\text{cls}} + \mathcal{L}_{\text{loc}}\) (391)

其中 \(\mathcal{L}_{\text{cls}}\) 是分类损失，\(\mathcal{L}_{\text{loc}}\) 是边界框回归的平滑 \(L_1\) 损失。这种多尺度方法增强了网络在不同分辨率级别检测对象的能力，提高了其对不同大小对象的鲁棒性。

因此，CNN中的对象检测涉及一种复杂的架构，包括卷积、激活、池化和多阶段损失函数，这些架构指导网络准确检测和定位图像中的对象。架构和损失函数的选择对检测系统的性能和效率起着关键作用，R-CNN、YOLO和SSD等现代架构各自根据应用需求提供独特的优势。

## 7.3 实际应用

### 7.3.1 医学影像

**文献综述：** Yousif et al. (2024) [205] 应用CNN进行黑色素瘤皮肤癌检测，集成二进制灰狼优化（GWO）算法以增强特征选择。它展示了深度学习在分类皮肤镜图像方面的有效性，并突出了准确分类的特征提取技术。Rahman et al. (2025) [206] 提供了一篇系统综述，涵盖了使用医学影像的CNN白血病检测。该研究比较了ResNet、VGG和EfficientNet等不同深度学习架构，为未来研究提供基准。Joshi and Gowda (2025) [207] 引入了一种基于注意力引导的图CNN（VSA-GCNN）用于脑肿瘤分割和分类。它利用MRI扫描中的空间关系来提高诊断准确性。将图神经网络（GNN）与CNN相结合是医学影像中一种新颖的方法。Ng et al. (2025) [208] 开发了一种基于CNN的心脏MRI分析模型，用于在不使用造影剂的情况下预测缺血性心肌病。它突出了深度学习模型从非造影图像中提取诊断信息的能力，减少了对侵入性程序的需求。Nguyen et al. (2025) [209] 提出了一种使用CNN的乳腺X线摄影多视图肿瘤区域自适应合成模型。该方法通过使用3D空间特征提取技术增强乳腺癌检测，改善肿瘤定位和分类。Chen et al. (2025) [210] 探讨了使用惩罚最小二乘（PLS）方法的医学图像基于CNN的去噪。该研究将深度学习应用于MRI扫描的降噪，从而提高了低信噪比（SNR）图像的清晰度。Pradhan et al. (2025) [211] 讨论了基于CNN的糖尿病视网膜病变检测。它引入了一种空洞残差U-Net架构，增强了图像分割性能，用于视网膜疾病早期诊断。Örenç et al. (2025) [212] 评估了用于X射线图像中腺样体肥大检测的集成CNN模型。它展示了迁移学习和特征融合技术，这些技术改进了基于CNN的医学诊断。Jiang et al. (2025) [213] 引入了一种用于MRI图像去噪的跨模态注意力网络，在某些成像模态缺失时尤其有效。它突出了使用CNN进行跨域知识迁移。Al-Haidri et al. (2025) [214] 开发了一种基于CNN的框架，用于心脏MRI扫描中的自动心肌纤维化分割。它强调定量特征提取技术，以提高心脏诊断的精度。

卷积神经网络（CNN）已成为医学影像领域不可或缺的工具，其驱动力在于能够直接从图像数据中自动学习特征的空间层次结构，而无需手工制作特征提取。CNN中的卷积层旨在利用输入数据的空间结构，使其特别适合医学影像任务，因为图像中的空间关系通常编码关键诊断信息。CNN的基本构建块——卷积运算——在数学上表达为

$$S(i, j) = \sum_{m=-k}^{k} \sum_{n=-k}^{k} I(i + m, j + n) \cdot K(m, n),\tag{392}$$

其中 S(i, j) 表示位置(i, j)处输出特征图的值，I(i, j) 是输入图像，K(m, n) 是卷积核（可学习权重矩阵），k 表示卷积核半径（例如，3 × 3 卷积核的 k = 1）。该方程本质上捕捉了通过在图像上滑动卷积核来提取局部模式（如边缘、纹理及更复杂特征）的过程。卷积操作针对多通道输入（例如RGB图像或多模态医学图像）的每个通道执行，结果跨通道求和，从而生成多维特征图。对于3D输入张量，卷积扩展为包含深度：

$$S(i, j, d') = \sum_{d=1}^{D} \sum_{m=-k}^{k} \sum_{n=-k}^{k} I(i + m, j + n, d) \cdot K(m, n, d),\tag{393}$$

其中 D 是输入张量的深度，d' 是输出特征图的深度索引。CNN在卷积层后融入非线性激活函数，以向模型引入非线性，使其能够学习复杂映射。一种常用的激活函数是修正线性单元（ReLU），在数学上定义为

$$f(x) = \max(0, x).\tag{394}$$

该函数确保激活的稀疏性，这有利于计算效率和泛化性能。更高级的激活函数，如参数化ReLU（PReLU），通过允许负斜率的可学习参数来扩展这一概念：

$$f(x) = \begin{cases} x & \text{if } x > 0, \\ ax & \text{if } x \le 0, \end{cases}\tag{395}$$



其中 $a$ 是一个可学习参数。池化层在 CNN 中被采用以降低特征图的空间维度，从而降低计算复杂度和过拟合风险。最大池化在数学上定义为

$$
P(i, j) = \max_{(m,n)\in\mathcal{R}} S(i + m, j + n), \quad (396)
$$

其中 $\mathcal{R}$ 是池化区域（例如，$2 \times 2$）。平均池化则计算均值：

$$
P(i, j) = \frac{1}{|\mathcal{R}|} \sum_{(m,n)\in\mathcal{R}} S(i + m, j + n). \quad (397)
$$

在医学影像中，CNN 广泛用于图像分类任务，例如检测异常（如肿瘤、骨折或病变）。考虑一个分类问题，其中输入为乳腺X线摄影图像，输出为二进制标签 $y \in \{0, 1\}$，指示良性或恶性。CNN 模型输出一个概率分数 $\hat{y}$，计算如下

$$
\hat{y} = \sigma(z) = \frac{1}{1 + e^{-z}}, \quad (398)
$$

其中 $z$ 是 sigmoid 激活之前的最后一层的输出。然后使用二元交叉熵损失函数来训练模型：

$$
\mathcal{L} = -\frac{1}{N} \sum_{i=1}^N [y_i \log(\hat{y}_i) + (1 - y_i) \log(1 - \hat{y}_i)]. \quad (399)
$$

对于图像分割任务，其目标是为每个像素分配标签，通常使用 U-Net 等架构。U-Net 采用编码器-解码器结构，编码器通过一系列卷积层和池化层提取特征，解码器通过上采样和拼接操作重建图像。分割的目标函数通常是 Dice 系数损失，定义为

$$
\mathcal{L}_{\text{Dice}} = 1 - \frac{2 \sum_i p_i g_i}{\sum_i p_i + \sum_i g_i}, \quad (400)
$$

其中 $p_i$ 和 $g_i$ 分别是像素 $i$ 的预测值和真实值。在图像重建的背景下，例如磁共振成像（MRI）中，CNN 被用于从欠采样 k 空间数据重建高质量图像。重建问题被表述为最小化重建图像 $I_{\text{pred}}$ 与真实值 $I_{\text{true}}$ 之间的差异，通常使用 $\ell_2$ 范数：

$$
\mathcal{L}_{\text{reconstruction}} = \|I_{\text{pred}} - I_{\text{true}}\|_2^2. \quad (401)
$$

生成对抗网络（GAN）也已应用于医学影像，特别是用于增强图像分辨率或从噪声输入合成真实图像。GAN 由一个生成器 $G$ 和一个判别器 $D$ 组成，其中 $G$ 学习从潜在噪声 $z$ 生成图像 $G(z)$，$D$ 区分真实图像和伪造图像。$G$ 和 $D$ 的损失函数由以下给出

$$
\mathcal{L}_D = -\mathbb{E}[\log D(x)] - \mathbb{E}[\log(1 - D(G(z)))], \quad (402)
$$

$$
\mathcal{L}_G = -\mathbb{E}[\log D(G(z))]. \quad (403)
$$

多模态影像，即结合不同模态（例如 MRI 和 PET）的数据，进一步凸显了 CNN 的实用性。例如，MRI 和 PET 图像的特征图在中间层进行拼接，以利用互补信息，提高诊断准确性。通常会引入注意力机制来关注图像中最相关的区域。例如，空间注意力图 $A_s$ 可以计算为

$$
A_s = \sigma(W_2 \cdot \text{ReLU}(W_1 \cdot F + b_1) + b_2), \quad (404)
$$

其中 $F$ 是输入特征图，$W_1$ 和 $W_2$ 是可学习权重矩阵，$b_1$ 和 $b_2$ 是偏置。尽管取得了成功，医学影像中的 CNN 仍面临数据稀缺和可解释性等挑战。迁移学习通过在小型医学数据集上微调预训练模型来解决数据稀缺问题。Grad-CAM 等技术通过可视化影响网络预测的区域来提供可解释性。在数学上，Grad-CAM 计算类别 $c$ 的特征图 $A^k$ 的重要性为

$$
\alpha_k^c = \frac{1}{Z} \sum_{i,j} \frac{\partial y^c}{\partial A_{i,j}^k}, \quad (405)
$$

其中 $y^c$ 是类别 $c$ 的得分，$Z$ 是归一化常数。然后得到类别激活图为

$$
L_{\text{Grad-CAM}}^c = \text{ReLU} \left( \sum_k \alpha_k^c A^k \right). \quad (406)
$$

总之，CNN 通过实现复杂医学图像的自动化和高精度分析，改变了医学影像。它们的应用涵盖疾病检测、分割、重建和多模态影像，持续的进步正在解决数据效率和可解释性方面的挑战。它们的数学基础和计算框架为该关键领域未来的创新提供了坚实基础。

### 7.3.2 自动驾驶汽车

### 文献综述

Ojala 和 Zhou (2024) [323] 提出了一种基于 CNN 的方法，用于在自动驾驶中从热图像中检测和估计物体距离。他们开发了一种使用单热相机的深度卷积模型用于距离估计，并在 CNN 管道中引入了热成像数据预处理的理论公式。

Popordanoska 和 Blaschko (2025) [324] 调查了包括自动驾驶车辆在内的高风险领域中 CNN 校准的数学基础。他们分析了用于自动驾驶感知的 CNN 中的置信度校准问题，并开发了一种受贝叶斯启发的正则化方法，以提高 CNN 在自动驾驶中的决策可靠性。

Alfieri 等人 (2024) [325] 探索了用于自动驾驶车辆最优路线规划的带有 CNN 的深度强化学习（DRL）方法。他们将基于 CNN 的视觉模型与深度 Q 学习相结合，实现了真实驾驶条件下的自适应路径优化，并建立了 Q 学习与基于 CNN 的物体检测之间用于自主导航的新理论联系。

Zanardelli (2025) [326] 考察了自动驾驶车辆系统中使用 CNN 的决策框架。他开发了一个将 CNN 与强化学习相结合的统计模型，以改进自动驾驶汽车的决策，并对 CNN 如何处理真实驾驶环境中的不确定性提供了严格的概率分析。

Norouzi 等人 (2025) [327] 分析了迁移学习在自动驾驶车辆感知的 CNN 模型中的作用。他们引入了用于使用多传感器数据融合进行车辆物体检测的预训练 CNN，并为将卡尔曼滤波和 Dempster-Shafer 理论与 CNN 相结合提供了严格的理论依据。

Wang 等人 (2024) [328] 调查了自动驾驶汽车基于 CNN 的感知模型中不确定性定量的数学。他们使用贝叶斯 CNN 来模型自动驾驶中语义分割的不确定性，并提出了一种基于 Dempster-Shafer 理论的融合机制，用于组合多个 CNN 输出。

Xia 等人 [329] 将基于 CNN 的感知模型与强化学习（RL）相结合，以提高自动驾驶车辆轨迹跟踪。他们使用 CNN 进行车道检测，并将其集成到基于 RL 的路径规划器中。他们还建立了一个将基于 CNN 的场景识别与控制理论相联系的理论框架。

Liu 等人 (2024) [330] 引入了一种用于自动驾驶汽车时空分析的基于 CNN 的多视图特征提取框架。他们开发了一种混合 CNN-图注意力模型来提取时态驾驶模式。他们还在自动驾驶车辆决策中的 CNN 多视图学习和特征融合方面取得了理论进展。

Chakraborty 和 Deka (2025) [331] 将基于 CNN 的多模态传感器融合应用于自动驾驶车辆和无人机，用于实时导航。他们对用于实时感知的 CNN 特征融合机制进行了理论分析，并开发了掩码区域 CNN（Mask-RCNN）以增强自主导航中的物体识别。

Mirindi 等人 (2025) [332] 调查了 CNN 和 AI 在智能自主交通中的作用。他们对自动驾驶中的 AI 采用统一理论进行了理论讨论，并引入了混合循环神经网络（RNN）和 CNN 架构用于车辆轨迹预测。

卷积神经网络（CNN）在自动驾驶汽车的实现中是基础的，构成了感知和决策系统的支柱，使这些车辆能够解释和响应其环境。CNN 的核心是卷积运算，它在数学上将输入图像或信号转换为特征图，从而允许提取空间层次信息。连续形式下的卷积运算定义为：

$$
s(t) = \int_{-\infty}^{\infty} x(\tau)w(t-\tau)d\tau, \quad (407)
$$

其中 \(x(\tau)\) 表示输入，\(w(t-\tau)\) 是滤波器或内核，\(s(t)\) 是输出特征。在离散域中，特别是对于图像处理，该运算可以写为：

$$
S(i, j) = \sum_{m=-k}^{k} \sum_{n=-k}^{k} X(i+m, j+n) \cdot W(m, n), \quad (408)
$$

其中 \(X(i, j)\) 表示输入图像坐标 \((i, j)\) 处的像素强度，\(W(m, n)\) 表示卷积核值。该运算能够检测边缘、角点或纹理等局部模式，随后跨层聚合这些模式以识别形状和物体等复杂特征。在自动驾驶汽车的背景下，CNN 处理来自摄像头、LiDAR 和雷达的传感器数据，以识别其他车辆、行人、路标和车道边界等关键特征。对于物体检测，基于 CNN 的架构（如 YOLO（You Only Look Once）和 Faster R-CNN）采用类似 ResNet 的骨干网络，该网络使用连续的卷积层从输入图像中提取层次化特征。物体检测任务涉及两个主要输出：边界框坐标和物体类别概率。在数学上，边界框回归被建模为多任务学习问题。边界框回归的损失函数通常表述为：

$$
L_{\text{reg}} = \sum_{i=1}^{N} \sum_{j \in \{x,y,w,h\}} \text{SmoothL1}(t_{ij} - \hat{t}_{ij}), \quad (409)
$$

其中 \(t_{ij}\) 和 \(\hat{t}_{ij}\) 分别是地面实测和预测的边界框参数（例如，中心坐标 \(x, y\) 和尺寸 \(w, h\)）。同时，分类损失（通常为交叉熵）计算为：

$$
L_{\text{cls}} = -\sum_{i=1}^{N} \sum_{c=1}^{C} y_{i,c} \log(p_{i,c}), \quad (410)
$$

其中 \(y_{i,c}\) 是一个二进制指示器，指示索引 \(i\) 的对象是否属于类别 \(c\)，\(p_{i,c}\) 是预测概率。总损失函数是加权组合：

$$
L_{\text{total}} = \alpha L_{\text{reg}} + \beta L_{\text{cls}}. \quad (411)
$$

语义分割是另一项关键任务，需要进行像素级分类，为图像中的每个像素分配标签（例如，道路、车辆、行人）。通常使用全卷积网络（FCN）或 U-Net 架构来实现此目的。这些架构采用编码器-解码器结构，编码器提取空间特征，解码器重建



空间分辨率以生成逐像素预测。语义分割的损失函数是对所有像素和类别求和，给出如下：

\( L = - \sum_{i=1}^N \sum_{c=1}^C y_{i,c} \log(p_{i,c}), \quad (412) \)

其中 \( y_{i,c} \) 是像素 \( i \) 和类别 \( c \) 的基准真值（ground-truth）二值标签，\( p_{i,c} \) 是预测概率。高级架构还采用跳跃连接来保留高分辨率空间信息，从而实现更清晰的分割边界。

深度估计对于自动驾驶车辆理解其周围环境的三维结构至关重要。CNN 用于从单目图像或立体图像对中预测深度图。深度估计过程被建模为回归问题，损失函数旨在最小化预测深度 \( \hat{d}_i \) 与基准真值深度 \( d_i \) 之间的差异。此任务中常用的损失函数是尺度不变损失：

\( L_{\text{scale-inv}} = \frac{1}{n} \sum_{i=1}^n \left( \log d_i - \log \hat{d}_i \right)^2 - \frac{1}{n^2} \left( \sum_{i=1}^n \left( \log d_i - \log \hat{d}_i \right) \right)^2 . \quad (413) \)

该损失确保相对深度差异最小化，这对于准确的三维重建至关重要。车道检测是另一项关键应用，它使用 CNN 来检测道路车道和边界。该任务通常涉及将车道标线预测为多项式曲线。CNN 处理输入图像以提取车道特征，后处理涉及拟合曲线，例如：

\( y = ax^2 + bx + c, \quad (414) \)

其中 \( a,b,c \) 是由网络预测的系数。拟合过程最小化误差函数，通常是检测到的车道点与曲线之间平方差之和：

\( E = \sum_{i=1}^N (y_i - (ax_i^2 + bx_i + c))^2 . \quad (415) \)

在自动驾驶汽车中，这些 CNN 任务被集成到一个端到端管线中。来自摄像头、LiDAR 和雷达的输入数据首先使用 CNN 进行处理，以提取与车辆感知相关的特征。然后，包括目标检测、语义图、深度图和车道边界在内的输出将传递给规划模块，该模块计算车辆的轨迹。例如，检测到的对象提供障碍物信息，而车道边界指导路径规划算法。规划过程涉及求解优化问题，其中目标函数包含来自 CNN 输出的约束。例如，轨迹优化问题可能最小化代价函数：

\( J = \int_0^T \left( w_1 \dot{x}^2 + w_2 \dot{y}^2 + w_3 c(t) \right) \, dt, \quad (416) \)

其中 \( \dot{x} \) 和 \( \dot{y} \) 是横向和纵向速度，\( c(t) \) 是基于对象检测的碰撞惩罚。

总之，CNN 为自动驾驶汽车的感知任务提供了计算框架，能够实时解释复杂的传感器数据。通过利用卷积、损失优化和分层特征提取的数学原理，CNN 将原始传感器数据转化为可操作的洞察，为安全高效的自动驾驶铺平了道路。

## 7.4 常用 CNN 架构

文献综述：Choudhury 等人（2024）[333] 对 CNN 架构进行了比较性理论研究，包括 AlexNet、VGG 和 ResNet，用于基于卫星的飞机识别。他们分析了 VGG、AlexNet 和 ResNet 中使用的架构差异和学习策略，并从理论上解释了 VGG 的深度、AlexNet 的特征提取和 ResNet 的残差学习如何促进 CNN 的发展。Almubarok 和 Rosiani（2024）[334] 讨论了 CNN 架构的计算效率，特别是将 AlexNet、VGG 和 ResNet 与 MobileNetV2 进行比较。他们建立了 AlexNet、VGG 和 ResNet 中深度、参数数量和精度之间的理论效率权衡，并强调了由于跳跃连接，ResNet 在优化方面的优势，与 AlexNet 和 VGG 的传统深层结构相比。Ding（2024）[335] 探讨了 CNN 架构（AlexNet、VGG 和 ResNet）在医学图像分类中的应用，特别是在中医（TCM）领域。他介绍了带有挤压激励（SE）模块的 ResNet-101，扩展了对 CNN 中深度特征表示的理论理解，并讨论了 VGG 的权重共享策略和 AlexNet 的分层特征提取，从而提高了分类精度。He 等人（2015）[336] 引入了残差学习，展示了深层 CNN 如何从恒等映射中受益以解决梯度消失问题。他们从理论上证明了深层网络中残差块的合理性，并确立了 ResNet 恒等映射作为深层优化的理论基础。Simonyan 和 Zisserman（2014）[148] 提出了 VGG 架构，展示了深度改进如何增强特征提取。他们制定了增加 CNN 深度及其对特征层次结构影响的理论公式，并为深层 CNN 中感受野扩展提供了分析框架。Krizhevsky 等人（2012）[337] 介绍了 AlexNet，这是在 ImageNet 分类中实现最先进性能的第一个 CNN 模型。他们将 ReLU 激活函数作为 CNN 训练的突破引入，并建立了脱校正则化理论，防止深层网络过拟合。Sultana 等人（2019）[338] 比较了 AlexNet、VGG 和 ResNet 在目标识别中的特征提取策略。他们对 CNN 架构中的分层特征学习进行了理论解释，并研究了 VGG 使用小型卷积滤波器及其对特征图深度的影响。Sattler 等人（2019）[339] 调查了 AlexNet、VGG 和 ResNet 等 CNN 架构的根本局限性。他们确立了 CNN 中卷积滤波器的形式约束，并为分类任务中的 CNN 泛化误差开发了理论模型。

### 7.4.1 AlexNet

**AlexNet 卷积神经网络（CNN）** 是一种深度学习模型，用于对原始像素值进行图像分类。给定一个输入图像，表示为 3D 张量 \(\mathbf{I}_0 \in \mathbb{R}^{H \times W \times C}\)，其中 \(H\) 是高度，\(W\) 是宽度，\(C\) 表示输入通道数（通常 RGB 图像中 \(C = 3\)），网络执行一系列操作，如卷积、激活函数、池化和全连接层，将此输入转换为最终输出向量 \(\mathbf{y} \in \mathbb{R}^K\)，其中 \(K\) 是输出类别数。AlexNet 的目标是最小化衡量预测输出与真实标签之间差异的损失函数，通常使用 **交叉熵损失函数**。

AlexNet 架构的核心是 **卷积层**，其设计目的是通过在输入图像上卷积一组滤波器来学习图像中的局部模式。具体来说，第一个卷积层对输入图像 \(\mathbf{I}_0\) 与一组滤波器 \(\mathbf{W}_1^{(k)} \in \mathbb{R}^{F_1 \times F_1 \times C}\) 执行卷积操作，其中 \(F_1\) 是滤波器的大小，\(C\) 是输入中的通道数。对于给定的滤波器 \(\mathbf{W}_1^{(k)}\) 和输入图像 \(\mathbf{I}_0\)，在位置 \((i, j)\) 处的卷积操作定义为：

\(Y_1^{(k)}(i, j) = \sum_{u=1}^{F_1} \sum_{v=1}^{F_1} \sum_{c=1}^{C} W_1^{(k)}(u, v, c) \cdot I_0(i + u - 1, j + v - 1, c) + b_1^{(k)}\) (417)

其中 \( b_1^{(k)} \) 是第 \( k \) 个滤波器的偏置项，卷积的输出是特征图 \( Y_1^{(k)}(i,j) \)，它捕获每个空间位置 \( (i, j) \) 处滤波器的响应。此卷积操作的结果是一组特征映射 \( Y_1^{(k)} \in \mathbb{R}^{H' \times W'} \)，如果不应用填充，则输出的尺寸为 \( H' = H - F_1 + 1 \) 和 \( W' = W - F_1 + 1 \)。卷积操作之后，输出特征映射 \( Y_1^{(k)} \) 传递到 **ReLU（整流线性单元）** 激活函数，该函数向网络引入非线性。ReLU 函数定义为：

\(\text{ReLU}(z) = \max(0, z)\)

该函数将特征图 \( Y_1^{(k)} \) 中的负值转换为零，同时保持正值不变，从而使网络能够对数据中的复杂非线性模式进行建模。ReLU 激活函数的输出表示为 \( A_1^{(k)}(i,j) = \text{ReLU}(Y_1^{(k)}(i, j)) \)。激活函数之后，执行 **最大池化** 操作以降采样特征映射并减少其空间维度。给定大小为 \( P \times P \) 的池化窗口，最大池化操作计算每个窗口中的最大值，其数学表达式为：

\( Y_1^{\text{pool}}(i,j) = \max \left( A_1^{(k)} (i', j') : (i', j') \in \text{pooling window} \right) \)

其中 \( A_1^{(k)} \) 是 ReLU 之后的特征图，生成的汇聚输出 \( Y_1^{\text{pool}}(i,j) \) 具有减少的空间维度，通常为 \( H'' = \frac{H'}{P} \) 和 \( W'' = \frac{W'}{P} \)。此操作有助于保留最重要的特征，同时丢弃不相关的空间细节，从而使网络对输入图像中的小平移更具鲁棒性。卷积和池化操作在多个层中重复，每个层都从输入数据中学习越来越复杂的模式。例如，在第二个卷积层中，我们将第一层的特征映射 \( A_1^{(k)} \) 与一组新的滤波器 \( \mathbf{W}_2^{(k)} \in \mathbb{R}^{F_2 \times F_2 \times K_1} \) 进行卷积，其中 \( K_1 \) 是第一个卷积层生成的特征映射数量。第二层的卷积表示为：

\( Y_2^{(k)}(i,j) = \sum_{u=1}^{F_2} \sum_{v=1}^{F_2} \sum_{c=1}^{K_1} W_2^{(k)}(u, v, c) \cdot A_1^{(c)}(i + u - 1, j + v - 1) + b_2^{(k)} \)

此过程对每个后续卷积层进行迭代，每组新滤波器学习更高级别的特征，如边缘、纹理和物体部件。每个卷积层生成的激活映射传递到 ReLU 激活函数，并在每个卷积层后应用最大池化以减少空间维度。

最后一个卷积层之后，特征映射被 **展平** 为一维向量 \( \mathbf{a}_f \in \mathbb{R}^N \)，其中 \( N \) 是所有通道和空间维度上的激活总数。然后将此展平向量传递到 **全连接（FC）层** 进行分类。每个全连接层执行线性变换，随后进行非线性激活。全连接层中第 \( i \) 个神经元的输出由以下公式给出：

\( z_i = \sum_{j=1}^N W_{ij} \cdot a_f(j) + b_i \)

其中 \( W_{ij} \) 是连接前一层神经元 \( j \) 与当前层神经元 \( i \) 的权重，\( b_i \) 是偏置项。全连接层的输出是一个类别得分向量 \( \mathbf{z} \in \mathbb{R}^K \)，它表示输入图像属于每个类别的未归一化对数概率。要将这些得分转换为有效的概率分布，应用 **softmax** 函数：

\(\sigma(z_i) = \frac{e^{z_i}}{\sum_{j=1}^K e^{z_j}}\)


softmax 函数确保输出值位于范围 [0, 1] 且总和为 1，从而表示 $K$ 个类别上的概率分布。网络的最终输出是一个概率向量 $\hat{\mathbf{y}} \in \mathbb{R}^K$，其中每个元素 $\hat{y}_i$ 对应输入图像属于类别 $i$ 的预测概率。要训练 AlexNet 模型，网络最小化预测概率 $\hat{\mathbf{y}}$ 与真实标签 $\mathbf{y}$ 之间的 **交叉熵损失** 函数，其公式为：
$$L = - \sum_{i=1}^K y_i \log(\hat{y}_i)$$ (423)

其中 $y_i$ 是真实标签（如果图像属于类别 $i$，则为 1，否则为 0），$\hat{y}_i$ 是类别 $i$ 的预测概率。训练的目标是调整网络中的权重 $W$ 和偏置 $b$ 以最小化该损失。网络参数使用 **梯度下降** 进行更新。要计算梯度，使用 **反向传播** 算法。全连接层中损失相对于权重 $W$ 的梯度由以下公式给出：
$$\frac{\partial L}{\partial W} = \frac{\partial L}{\partial z} \cdot \frac{\partial z}{\partial W}$$ (424)

其中 $\frac{\partial L}{\partial z}$ 是损失相对于层输出的梯度，$\frac{\partial z}{\partial W}$ 是输出相对于权重的梯度。然后使用梯度下降更新规则利用这些梯度更新权重：
$$W \leftarrow W - \eta \cdot \frac{\partial L}{\partial W}$$ (425)

其中 $\eta$ 是学习率。该过程对网络中的每一层进行迭代重复。

训练期间通常会应用诸如 **丢弃法** 之类的正则化技术来防止过拟合。丢弃法涉及在每个训练步骤中随机将一部分激活值设置为零，这有助于防止网络过度依赖任何单一特征，并鼓励模型学习更鲁棒的特征。训练完成后，AlexNet 模型可以通过将新图像传递给网络并选择概率最高的类别来对其进行分类。卷积层、ReLU 激活、池化层、全连接层和 softmax 激活的组合使 AlexNet 成为图像分类任务的一种强大且高效的架构。

### 7.4.2 ResNet

ResNet 架构的核心在于 _残差学习_ 的概念，即网络不学习直接变换 $\mathbf{y} = f(\mathbf{x}; \mathbf{W})$，而是学习残差函数 $\mathcal{F}(\mathbf{x}; \mathbf{W})$，也就是输入与输出之间的差异。因此，网络输出 $\mathbf{y}$ 可以表示为：
$$\mathbf{y} = \mathcal{F}(\mathbf{x}; \mathbf{W}) + \mathbf{x}$$ (426)

这种表述与传统神经网络的核心区别在于，传统网络直接从输入 $\mathbf{x}$ 到输出 $\mathbf{y}$ 学习映射。引入恒等快捷连接 $\mathbf{x}$ 提供了一种强大的机制，使网络能够学习残差；如果最优残差变换是恒等函数，网络本质上可以学习 $\mathbf{y} = \mathbf{x}$，从而改善优化。这减少了训练更深层网络的挑战，因为深层通常会导致梯度消失，而梯度可以通过这些快捷连接直接传播，绕过中间层。

让我们形式化这个残差学习。设残差块的输入为 $\mathbf{x}_l$，输出为 $\mathbf{y}_l$。在传统神经网络中，第 $l$ 层从输入到输出的变换将是：

\[\mathbf{y}_l = \mathcal{F}(\mathbf{x}_l; \mathbf{W}_l)\] (427)

其中 $\mathcal{F}$ 表示由该层学习的函数，由 $\mathbf{W}_l$ 参数化。相比之下，对于 ResNet，输出是学习到的残差函数 $\mathcal{F}(\mathbf{x}_l; \mathbf{W}_l)$ 与输入 $\mathbf{x}_l$ 本身的和，得到：

\[\mathbf{y}_l = \mathcal{F}(\mathbf{x}_l; \mathbf{W}_l) + \mathbf{x}_l\] (428)

添加恒等快捷连接使网络在需要时可以绕过层，从而促进学习过程并解决梯度消失问题。为了形式化优化问题，我们将残差学习目标定义为关于参数 $\mathbf{W}_l$ 最小化损失函数 $\mathcal{L}$：

\[\mathcal{L} = \sum_{i=1}^N \mathcal{L}_i(\mathbf{y}_i, \mathbf{t}_i)\] (429)

其中 $N$ 是训练样本的数量，$\mathbf{t}_i$ 是目标输出，$\mathcal{L}_i$ 是第 $i$ 个样本的损失。训练过程涉及通过梯度下降调整参数 $\mathbf{W}_l$，而这反过来需要损失函数相对于网络参数的梯度。$\mathcal{L}$ 相对于 $\mathbf{W}_l$ 的梯度可以表示为：

\[\frac{\partial \mathcal{L}}{\partial \mathbf{W}_l} = \sum_{i=1}^N \frac{\partial \mathcal{L}_i}{\partial \mathbf{y}_i} \cdot \frac{\partial \mathbf{y}_i}{\partial \mathbf{W}_l}\] (430)

由于残差块将输入直接加到输出上，输出相对于权重 $\mathbf{W}_l$ 的导数由以下公式给出：

\[\frac{\partial \mathbf{y}_l}{\partial \mathbf{W}_l} = \frac{\partial \mathcal{F}(\mathbf{x}_l; \mathbf{W}_l)}{\partial \mathbf{W}_l}\] (431)

现在，让我们探讨一下残差连接的添加如何直接影响反向传播过程。在传统前馈网络中，每一层的反向传播梯度仅取决于前一层的输出。然而，在残差网络中，梯度流得到了增强，因为恒等映射 $\mathbf{x}_l$ 直接传递给后续层。这确保了随着网络加深，梯度不会丢失，这一现象在非常深层的网络中至关重要。第 $l$ 层相对于损失 $\mathcal{L}$ 的梯度为：

\[\frac{\partial \mathcal{L}}{\partial \mathbf{x}_l} = \frac{\partial \mathcal{L}}{\partial \mathbf{y}_l} \cdot \frac{\partial \mathbf{y}_l}{\partial \mathbf{x}_l}\] (432)

由于 $\mathbf{y}_l = \mathcal{F}(\mathbf{x}_l; \mathbf{W}_l) + \mathbf{x}_l$，$\mathbf{y}_l$ 相对于 $\mathbf{x}_l$ 的导数为：

\[\frac{\partial \mathbf{y}_l}{\partial \mathbf{x}_l} = \mathbf{I} + \frac{\partial \mathcal{F}(\mathbf{x}_l; \mathbf{W}_l)}{\partial \mathbf{x}_l}\] (433)

其中 $\mathbf{I}$ 是单位矩阵。这确保了梯度 $\frac{\partial \mathcal{L}}{\partial \mathbf{x}_l}$ 可以更容易地通过网络传播，因为它现在被单位矩阵项增强。因此，这一项有助于在反向传播过程中保持梯度的幅度，解决了深层网络中通常出现的梯度消失问题。此外，为了确保残差块输入和输出的维度匹配，特别是当通道数量发生变化时，ResNet 引入了 _投影快捷连接_。当 $\mathbf{x}_l$ 和 $\mathbf{y}_l$ 的维度不一致时使用这些连接，通常通过 $1 \times 1$ 卷积实现。投影快捷连接将残差块的输出修改为：

\[\mathbf{y}_l = \mathcal{F}(\mathbf{x}_l; \mathbf{W}_l) + \mathbf{W}_x \cdot \mathbf{x}_l\] (434)

其中 $\mathbf{W}_x$ 是卷积滤波器，$\mathcal{F}(\mathbf{x}_l; \mathbf{W}_l)$ 是残差变换。引入 $1 \times 1$ 卷积确保输入 $\mathbf{x}_l$ 映射到适当的维度，同时仍然受益于残差学习框架。可以通过堆叠多个残差块来扩展 ResNet 架构。对于具有 $L$ 层的网络，通过整个网络后的输出可以递归地写成：

$\mathbf{y}^{(L)} = \mathbf{x} + \mathcal{F}(\mathbf{y}^{(L-1)}; \mathbf{W}_L)$ (435)

其中 $\mathbf{y}^{(L-1)}$ 是经过 $L - 1$ 层后的输出。该公式的递归特性确保网络输出逐层构建，每一层都相对于传递给它的输入贡献一个变换。从数学上讲，深层残差网络中损失函数相对于参数的梯度可以递归地表示，每一层的梯度都涉及来自恒等快捷连接的贡献。这通过在反向传播过程中保持梯度的稳定和一致流动，促进了非常深层网络的训练。

因此，*残差神经网络 (ResNet)* 通过引入残差学习，显著提高了深度神经网络的可训练性，使网络能够专注于学习输入与输出之间的差异，而不是整个变换。这种方法结合恒等快捷连接和用于维度匹配的投影快捷连接，确保梯度能够有效地通过网络流动，即使在非常深层的架构中也是如此。由此产生的 ResNet 架构已被证明能够实现数百层网络的训练，在从图像分类到语义分割的广泛任务中取得了出色的性能，同时缓解了梯度消失等问题。通过其递归结构和严谨的数学表述，ResNet 已成为现代深度学习中的基础架构。

### 7.4.3 VGG

**视觉几何组 (VGG) 卷积神经网络 (CNN)** 由 Simonyan 和 Zisserman 于 2014 年提出，详细探讨了深度对深度神经网络性能的影响，特别是在图像分类等计算机视觉任务中。VGG 架构基于以下假设：当使用小而一致的卷积核构建时，更深层的网络更能捕捉数据中的层次化模式，特别是在视觉识别领域。与其他 CNN 架构相比，VGG 优先使用堆叠在不断增加深度中的小型 $3 \times 3$ 卷积滤波器（步幅为 1），而不是依赖较大的滤波器（例如 $5 \times 5$ 或 $7 \times 7$），从而在不牺牲表示能力的情况下提供计算优势。这种设计选择本质上鼓励稀疏的局部感受野，确保在扩展到更深层时具有更丰富的学习能力。

设 $I \in \mathbb{R}^{H \times W \times C}$ 表示高度为 $H$、宽度为 $W$、通道数为 $C$ 的输入图像，其中通道对应不同的颜色表示（例如，对于 $C = 3$ 则为 RGB）。对于特定层 $k$ 上应用的卷积操作，输出特征图 $O^{(k)}$ 可以通过将输入 $I$ 与一组对应第 $k$ 层的卷积核 $K^{(k)}$ 进行卷积来计算。每个空间位置 $i, j$ 的卷积可以描述为：

$O_{i,j}^{(k)} = \sum_{u=1}^{k_h} \sum_{v=1}^{k_w} \sum_{c'=1}^{C_{in}} K_{u,v,c',c}^{(k)} I_{i+u,j+v,c'} + b_c^{(k)}$ (436)

其中 $O_{i,j}^{(k)}$ 是第 $k$ 个滤波器的特征图在位置 $(i, j)$ 处的输出值，$K_{u,v,c',c}^{(k)}$ 是第 $k$ 层中从 $c'$ 到 $c$ 的滤波器的 $u, v$ 第空间元素，$b_c^{(k)}$ 表示偏置项


输出通道 c。卷积层的核 $K^{(k)}$ 通常用小值初始化并在训练过程中学习，而偏置 $b^{(k)}$ 则用于偏移神经元的激活。VGG 架构的一个关键方面是，这些卷积层之后始终跟随非线性 **ReLU（整线性单元）** 激活函数，这些函数为模型引入了局部非线性。ReLU 函数在数学上定义为：

$ReLU(x) = \max(0, x)$ (437)

这种变换按元素应用，确保负值映射为零，其效果是仅激活正特征响应。ReLU 引入的非线性有助于网络学习复杂模式，并克服在更深网络中经常出现的梯度消失等问题。在 VGG 中，网络是通过堆叠这些带有 ReLU 激活的卷积层构建的。每个卷积层之后都跟随 **最大池化** 操作，通常使用 $2 \times 2$ 过滤器和步长为 2。最大池化减少特征图的空间维度，并从图像的每个区域提取最显著的特征。最大池化操作在数学上表达为：

$O_{i,j} = \max_{(u,v) \in P} I_{i+u, j+v}$ (438)

其中 $P$ 是池化窗口，$O_{i,j}$ 是位置 $(i, j)$ 处的池化值。池化操作执行下采样，在保留最突出特征的同时确保平移不变性。此池化操作的效果是降低计算复杂度，减少参数数量，并使网络对输入图像中的小平移和失真不变。VGG 架构通常在若干卷积层和池化层从输入图像中提取相关特征后，最终以一系列 **全连接（FC）层** 结束。设最后一个卷积层的输出在展平后表示为 $X \in \mathbb{R}^d$，其中 $d$ 表示通过展平最后一个卷积特征图获得的特征向量的维度。然后全连接层将此向量转换为输出，表达如下：

$\mathbf{O} = \mathbf{WX} + \mathbf{b}$ (439)

其中 $\mathbf{W} \in \mathbb{R}^{d' \times d}$ 是全连接层的权重矩阵，$\mathbf{b} \in \mathbb{R}^{d'}$ 是偏置向量，$\mathbf{O} \in \mathbb{R}^{d'}$ 是输出向量。输出向量 $\mathbf{O}$ 表示分类任务中每个 $d'$ 个可能类别的未归一化得分。这通常接着应用 **softmax** 函数，将这些原始得分转换为概率分布：

$\sigma(o_i) = \frac{e^{o_i}}{\sum_{j=1}^{d'} e^{o_j}}$ (440)

其中 $o_i$ 是类别 $i$ 的得分，softmax 函数确保输出为正且和为一，从而便于将其解释为类别概率。softmax 函数在多类分类任务中是一个关键步骤，因为它将输出归一化为概率格式。在训练阶段，模型最小化预测概率与实际类别标签之间的 **交叉熵损失**，后者通常表示为 one-hot 编码向量。交叉熵损失由以下公式给出：

$L = - \sum_{i=1}^{d'} y_i \log(p_i)$ (441)

其中 $y_i$ 是类别 $i$ 的真实标签，采用 one-hot 编码形式，$p_i$ 是类别 $i$ 的预测概率。此损失函数是分类任务的适当目标，因为它衡量真实与预测概率分布之间的差异。VGG 网络中参数的优化是使用 **随机梯度下降（SGD）** 或其变体进行的。梯度下降中的权重更新规则为：

$\mathbf{W} \leftarrow \mathbf{W} - \eta \nabla_{\mathbf{w}} L$ (442)

其中 $\eta$ 是学习率，$\nabla_{\mathbf{w}}L$ 是损失相对于权重的梯度。梯度通过 **反向传播** 计算，应用导数的链式法则将错误向后传播通过网络，根据每个参数对最终输出错误的贡献更新每一层的权重。

VGG 架构的一个关键优势在于其使用比之前网络（如 AlexNet，其使用较大的卷积过滤器）更小、更深的层。通过使用多个小核（例如 \(3 \times 3\)），VGG 网络可以在不指数级增加参数数量的情况下创建更丰富的表示。通过堆叠这些小卷积过滤器实现的网络深度，使模型能够从原始像素数据中提取越来越抽象和分层的特征。尽管取得了成功，但由于参数数量庞大，VGG 的计算需求相对较高，尤其是在全连接层中。全连接层将一层中的每个神经元连接到下一层中的每个神经元，占据了模型总参数的很大一部分。为了缓解这一局限性，后来的架构（如 **ResNet**）引入了 **跳跃连接**，允许梯度更高效地流经网络，从而实现更深层的架构而无需承担相同的计算成本。尽管如此，VGG 网络在深度卷积网络的设计中树立了重要先例，展示了深度架构的威力和小卷积过滤器的有效性。该模型的简单性和直观设计影响了后续架构，强化了这样一种观念：当精心构建时，更深的模型可以在图像分类等复杂任务中实现卓越性能，尽管面临计算成本和模型复杂度带来的挑战。

# 8 循环神经网络 (RNNs)

## 文献综述

Schmidhuber (2015) [114] 从广泛的历史视角对神经网络（包括 RNNs）进行了综述。Schmidhuber 描述了长短期记忆网络（LSTM）等关键架构及其在解决梯度消失问题中的重要性。他还解释了训练 RNN 的基本学习算法，并对序列预测和语音识别等应用提供了见解。Lipton et. al. (2015) [264] 对 RNN 及其各种实现进行了严格的批评。作者讨论了训练 RNN 的根本挑战，包括长程依赖和计算低效问题。该文还提出了比较不同架构（如 vanilla RNNs、LSTMs 和 GRUs）的基准测试。Pascanu et. al. (2013) [265] 正式分析了训练 RNN 为何困难，特别是关注梯度消失和梯度爆炸问题。作者提出梯度裁剪作为实际解决方案，并讨论了提高 RNN 训练效率的方法。Goodfellow et. al. (2016) [112] 在其著作中专门用一章讨论循环神经网络，探讨了其理论基础、通过时间反向传播（BPTT）以及 LSTM 和 GRU 等关键架构。它还提供了训练深度 RNN 中使用的优化技术的数学推导。Jaeger (2001) [266] 引入了回声状态网络（ESN），这是一种只需训练输出权重的替代循环架构。ESN 方法在 RNN 研究中变得非常有影响力，特别是在解决稳定性和效率问题方面。Hochreiter 和 Schmidhuber (1997) [267] 引入了 LSTM 架构，该架构通过引入带有门控机制的内存单元解决了 RNN 中的梯度消失问题。LSTM 现在已成为序列建模任务（如语音识别和自然语言处理）的标准。Kawakami (2008) [268] 深入探讨了 RNN 的监督学习技术，特别是针对序列标注问题。Graves 讨论了连接主义时序分类（CTC），这是一种用于基于 RNN 的



语音和手写识别。Bengio et al. (1994) [269]从数学上证明了为什么RNN在学习长期依赖性方面存在困难。它找出了梯度消失和梯度爆炸问题的根本原因，为未来的架构（如LSTM）奠定了基础。Bhattamishra et al. (2020) [270]严格比较了RNN和Transformer的理论能力。作者分析了表达能力、记忆保持和训练效率，提供了关于为什么Transformer在NLP中越来越多地取代RNN的见解。Siegelmann (1993) [271]对RNN进行了严格的理论处理，分析了其收敛特性、稳定性条件和计算复杂度。它讨论了用于理解RNN泛化和优化挑战的数学框架。

## 8.1 关键概念

循环神经网络（RNN）是一类专门为处理序列数据而设计的神经架构，利用其递归结构来建模时间依赖性。RNN的核心在于隐藏状态\(\mathbf{h}_t \in \mathbb{R}^m\)的概念，它随时间演变，作为当前输入\(\mathbf{x}_t \in \mathbb{R}^n\)和前一个隐藏状态\(\mathbf{h}_{t-1}\)的函数。这种演变由递归关系控制：

\(\mathbf{h}_t = f_h(\mathbf{W}_{xh}\mathbf{x}_t + \mathbf{W}_{hh}\mathbf{h}_{t-1} + \mathbf{b}_h) \quad \text{(443)}\)

其中\(\mathbf{W}_{xh} \in \mathbb{R}^{m \times n}\)是输入到隐藏的权重矩阵，\(\mathbf{W}_{hh} \in \mathbb{R}^{m \times m}\)是隐藏到隐藏的权重矩阵，\(\mathbf{b}_h \in \mathbb{R}^m\)是偏置向量，\(f_h\)是一个非线性激活函数，通常是

\(\tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}} \quad \text{(444)}\)

或修正线性单元\(\text{ReLU}(x) = \max(0, x)\)。该更新方程的递归性质确保\(\mathbf{h}_t\)固有地编码了关于序列\(\{\mathbf{x}_1, \mathbf{x}_2, \dots, \mathbf{x}_t\}\)的信息，使网络能够维护过去输入的动态表示。时间\(t\)的输出\(\mathbf{y}_t \in \mathbb{R}^o\)计算如下：

\(\mathbf{y}_t = f_y(\mathbf{W}_{hy}\mathbf{h}_t + \mathbf{b}_y) \quad \text{(445)}\)

其中\(\mathbf{W}_{hy} \in \mathbb{R}^{o \times m}\)是隐藏到输出的权重矩阵，\(\mathbf{b}_y \in \mathbb{R}^o\)是输出偏置，\(f_y\)是一个激活函数，例如softmax函数：

\(f_y(\mathbf{z})_i = \frac{e^{z_i}}{\sum_{j=1}^o e^{z_j}} \quad \text{(446)}\)

用于分类任务。通过迭代展开递归关系，时间\(t\)的隐藏状态可以表示为：

\(\mathbf{h}_t = f_h(\mathbf{W}_{xh}\mathbf{x}_t + \mathbf{W}_{hh}f_h(\mathbf{W}_{xh}\mathbf{x}_{t-1} + \mathbf{W}_{hh}f_h(\dots f_h(\mathbf{W}_{xh}\mathbf{x}_1 + \mathbf{W}_{hh}\mathbf{h}_0 + \mathbf{b}_h) + \mathbf{b}_h) + \mathbf{b}_h) + \mathbf{b}_h) \quad \text{(447)}\)

这种展开说明了网络捕获的时间依赖的深度，并突出了维持长期记忆的计算挑战。具体来说，损失函数\(L\)的梯度，由以下给出：

\(L = \sum_{t=1}^T \ell(\mathbf{y}_t, \mathbf{y}_t^{\text{true}}) \quad \text{(448)}\)

与\(\ell(\mathbf{y}_t, \mathbf{y}_t^{\text{true}})\)代表任务特定的损失，例如交叉熵：

\(\ell(\mathbf{y}_t, \mathbf{y}_t^{\text{true}}) = -\sum_{i=1}^o \mathbf{y}_t^{\text{true}}(i) \log \mathbf{y}_t(i) \quad \text{(449)}\)

通过时间反向传播（BPTT）计算。例如，L相对于\(\mathbf{W}_{hh}\)的梯度由以下给出：

\(\frac{\partial L}{\partial \mathbf{W}_{hh}} = \sum_{t=1}^T \sum_{k=1}^t \frac{\partial \ell_t}{\partial \mathbf{h}_t} \prod_{j=k+1}^t \frac{\partial \mathbf{h}_j}{\partial \mathbf{h}_{j-1}} \frac{\partial \mathbf{h}_k}{\partial \mathbf{W}_{hh}},\)

其中\(\prod_{j=k+1}^t \frac{\partial \mathbf{h}_j}{\partial \mathbf{h}_{j-1}}\)代表从时间步k到t的导数链。与前馈神经网络不同，后者独立处理每个输入，RNN维护一个作为动态内存的隐藏状态\(\mathbf{h}_t\)，随着输入序列的进展递归演化。正式地，给定输入序列\(\{\mathbf{x}_1, \mathbf{x}_2, \dots, \mathbf{x}_T\}\)，其中\(\mathbf{x}_t \in \mathbb{R}^n\)表示时间t的输入向量，隐藏状态\(\mathbf{h}_t \in \mathbb{R}^m\)通过递归关系更新：

\(\mathbf{h}_t = f_h(\mathbf{W}_{xh}\mathbf{x}_t + \mathbf{W}_{hh}\mathbf{h}_{t-1} + \mathbf{b}_h),\)

其中\(\mathbf{W}_{xh} \in \mathbb{R}^{m \times n}\)，\(\mathbf{W}_{hh} \in \mathbb{R}^{m \times m}\)，和\(\mathbf{b}_h \in \mathbb{R}^m\)是可学习参数，\(f_h\)是一个非线性激活函数，例如tanh或ReLU。递归结构固有地允许隐藏状态\(\mathbf{h}_t\)编码直到时间t的整个序列历史。每个时间步的输出\(\mathbf{y}_t \in \mathbb{R}^o\)计算如下：

\(\mathbf{y}_t = f_y(\mathbf{W}_{hy}\mathbf{h}_t + \mathbf{b}_y),\)

其中\(\mathbf{W}_{hy} \in \mathbb{R}^{o \times m}\)和\(\mathbf{b}_y \in \mathbb{R}^o\)是额外的可学习参数，\(f_y\)是一个可选的输出激活函数，例如用于分类的softmax函数。为了阐明递归动态，我们可以用初始隐藏状态\(\mathbf{h}_0\)和所有先前输入\(\{\mathbf{x}_1, \dots, \mathbf{x}_t\}\)明确展开\(\mathbf{h}_t\)：

\(\mathbf{h}_t = f_h(\mathbf{W}_{xh}\mathbf{x}_t + \mathbf{W}_{hh}f_h(\mathbf{W}_{xh}\mathbf{x}_{t-1} + \mathbf{W}_{hh}f_h(\dots f_h(\mathbf{W}_{xh}\mathbf{x}_1 + \mathbf{W}_{hh}\mathbf{h}_0 + \mathbf{b}_h) + \mathbf{b}_h) + \mathbf{b}_h) + \mathbf{b}_h).\)

这种嵌套结构突出了时间依赖性和训练中的潜在挑战，例如梯度消失和梯度爆炸问题。在训练期间，损失函数L（汇总预测输出\(\mathbf{y}_t\)和基础真值\(\mathbf{y}_t^{\text{true}}\)之间的差异）通常定义为：

\(L = \sum_{t=1}^T \ell(\mathbf{y}_t, \mathbf{y}_t^{\text{true}}),\)

其中\(\ell\)是任务特定的损失函数，例如均方误差（MSE）

\(\ell(\mathbf{y}, \mathbf{y}^{\text{true}}) = \frac{1}{2} \| \mathbf{y} - \mathbf{y}^{\text{true}} \|^2\)

用于回归，或用于分类的交叉熵损失。为了优化L，采用基于梯度的方法，需要计算L相对于所有参数（如\(\mathbf{W}_{xh}\)、\(\mathbf{W}_{hh}\)和\(\mathbf{b}_h\)）的导数。使用时间反向传播（BPTT），L相对于\(\mathbf{W}_{hh}\)的梯度表示为：

\(\frac{\partial L}{\partial \mathbf{W}_{hh}} = \sum_{t=1}^T \sum_{k=1}^t \frac{\partial \ell_t}{\partial \mathbf{h}_t} \prod_{j=k+1}^t \frac{\partial \mathbf{h}_j}{\partial \mathbf{h}_{j-1}} \frac{\partial \mathbf{h}_k}{\partial \mathbf{W}_{hh}}.\)

这里，

\(\prod_{j=k+1}^t \frac{\partial \mathbf{h}_j}{\partial \mathbf{h}_{j-1}}\)

是编码\(\mathbf{h}_k\)对\(\mathbf{h}_t\)影响的雅可比矩阵乘积。雅可比\(\frac{\partial \mathbf{h}_j}{\partial \mathbf{h}_{j-1}}\)本身由以下给出：

\(\frac{\partial \mathbf{h}_j}{\partial \mathbf{h}_{j-1}} = \mathbf{W}_{hh} \odot f'_h(\mathbf{a}_j),\)

其中

\(\mathbf{a}_j = \mathbf{W}_{xh}\mathbf{x}_j + \mathbf{W}_{hh}\mathbf{h}_{j-1} + \mathbf{b}_h,\) (459)

和\(f'_h(\mathbf{a}_j)\)表示激活函数的逐元素导数。这些雅可比的反复乘法可能导致梯度的指数增长或衰减，具体取决于谱半径\(\rho(\mathbf{W}_{hh})\)。具体来说，如果\(\rho(\mathbf{W}_{hh}) > 1\)，梯度爆炸，而如果\(\rho(\mathbf{W}_{hh}) < 1\)，梯度消失，严重阻碍长序列的训练过程。为了解决这些问题，诸如长短期记忆（LSTM）网络和门控循环单元（GRU）等修改引入了门控机制，明确调节信息流。在LSTM中，由加法动态控制的单元状态\(\mathbf{c}_t\)防止梯度消失。单元状态按以下方式更新：

\(\mathbf{c}_t = \mathbf{f}_t \odot \mathbf{c}_{t-1} + \mathbf{i}_t \odot \tanh(\mathbf{W}_c \mathbf{x}_t + \mathbf{U}_c \mathbf{h}_{t-1} + \mathbf{b}_c),\) (460)

其中\(\mathbf{f}_t\)是遗忘门，\(\mathbf{i}_t\)是输入门，\(\mathbf{U}_c\)、\(\mathbf{W}_c\)和\(\mathbf{b}_c\)是可学习参数。

## 8.2 序列建模与长短期记忆（LSTM）和GRU

文献综述：Potter and Egon (2024) [387]对RNN及其增强（LSTM和GRU）在时间序列预测中的应用进行了广泛研究。作者对这些架构进行了经验比较，并分析了它们在捕捉序列数据中长期依赖性方面的有效性。该研究得出结论，GRU计算效率高，但表达能力略逊于LSTM，而标准RNN则存在梯度消失问题。Yatkin et al. (2025) [388]将拓扑视角引入RNN（包括LSTM和GRU），以解决现实应用中的不一致性。作者提出增强稳定性的机制，以提高RNN在金融和气候建模中的性能。他们的结果表明，经过拓扑优化的GRU在长序列上保持记忆方面优于传统LSTM。Saifullah (2024) [389]将LSTM和GRU网络应用于生物医学图像分类（鸡蛋受精检测）。该文表明，GRU更简单的架构导致更快的收敛，而由于更好的记忆保持，LSTM达到略高的准确率。结果突出了LSTM与GRU在特定领域的优势，特别是在处理稀疏特征表示方面。Alonso (2024) [390]严格探讨了RNN、LSTM和GRU的数学基础。作者对门控机制、梯度消失解决方案以及改善序列建模的优化技术进行了深入分析。在GRU与LSTM之间绘制了隐藏状态动态的理论比较，支持其在NLP和时间序列预测中的应用。Tu et al. (2024) [391]在一项医学AI研究中评估了LSTM和GRU，用于预测镇静期间患者的生理指标。作者发现，LSTM在时间序列医学数据中保留更多长期依赖性，使其适合患者监测，而由于计算开销较低，GRU更适合实时预测。Zuo et al. (2025) [392]应用混合GRU，利用实时位置跟踪预测商店中客户的移动。作者提出了一种修改的GRU-LSTM混合模型，在轨迹预测中实现了最先进的准确率。该研究表明，单独的GRU可能缺乏精细的记忆保持，但混合方法提高了预测能力。Lima et al. (2025) [393]开发了一种工业AI应用，展示了GRU在过程优化中的效率。该研究发现，GRU在钢板加热实时预测控制方面优于LSTM，展示了其在需要更快计算的应用中的效率。Khan et al. (2025) [394]将LSTM与统计ARIMA模型集成，以改善风力发电预测。他们证明，混合LSTM-ARIMA模型在处理天气相关序列数据方面优于独立的RNN，此类数据波动性很大。Guo and Feng (2024) [395]在一项环境AI研究中提出了一种时空注意力增强的LSTM模型，用于预测温室气候变量。该研究引入了一种新颖的位置感知LSTM架构，提高了多步预测能力，这对于精准农业至关重要。Abdelhamid (2024) [396]利用深度RNN架构（包括LSTM和GRU）探索了基于物联网的能源预测。该研究得出结论，GRU提供



faster inference speeds but LSTMs capture more accurate long-range dependencies, making them more reliable for complex forecasting.

Sequence modeling in Recurrent Neural Networks (RNNs) represents a powerful framework for capturing temporal dependencies in sequential data, enabling the learning of both short-term and long-term patterns. The primary characteristic of RNNs lies in their recurrent architecture, where the hidden state $h_t$ at time step $t$ is updated as a function of both the current input $x_t$ and the hidden state at the previous time step $h_{t-1}$. Mathematically, this recurrent relationship can be expressed as:

$$
h_t = f(W_h h_{t-1} + W_x x_t + b_h) \quad (461)
$$

Here, $W_h$ and $W_x$ are weight matrices corresponding to the previous hidden state $h_{t-1}$ and the current input $x_t$, respectively, while $b_h$ is a bias term. The function $f(\cdot)$ is a non-linear activation function, typically chosen as the hyperbolic tangent tanh or rectified linear unit (ReLU). The output $y_t$ at each time step is derived from the hidden state $h_t$ through a linear transformation, followed by a non-linear activation, yielding:

$$
y_t = g(W_y h_t + b_y) \quad (462)
$$

where $W_y$ is the weight matrix connecting the hidden state to the output space, and $b_y$ is the associated bias term. The function $g(\cdot)$ is generally a softmax activation for classification tasks or a linear activation for regression problems. The key feature of this structure is the interdependence of the hidden state across time steps, allowing the model to capture the history of past inputs and produce predictions that incorporate temporal context. Training an RNN involves minimizing a loss function $L$, which quantifies the discrepancy between the predicted outputs $y_t$ and the true outputs $y_t^{\text{true}}$ across all time steps. A common loss function used in classification tasks is the cross-entropy loss, while regression tasks often utilize mean squared error. To optimize the parameters of the network, the model employs **Backpropagation Through Time (BPTT)**, a variant of the standard backpropagation algorithm adapted for sequential data. The primary challenge in BPTT arises from the recurrent nature of the network, where the hidden state at each time step depends on the previous hidden state. The gradient of the loss function with respect to the hidden state at time step $t$ is computed recursively, reflecting the temporal structure of the model. The chain rule is applied to compute the gradient of the loss with respect to the hidden state:

$$
\frac{\partial L}{\partial h_t} = \frac{\partial L}{\partial y_t} \cdot \frac{\partial y_t}{\partial h_t} + \sum_{t'=t+1}^{T} \frac{\partial L}{\partial h_{t'}} \cdot \frac{\partial h_{t'}}{\partial h_t} \quad (463)
$$

Here, $\frac{\partial L}{\partial y_t}$ is the gradient of the loss with respect to the output, and $\frac{\partial y_t}{\partial h_t}$ represents the Jacobian of the output with respect to the hidden state. The second term in this expression corresponds to the accumulated gradients propagated from future time steps, incorporating the temporal dependencies across the entire sequence. This recursive gradient calculation allows for updating the weights and biases of the RNN, adjusting them to minimize the total error across the sequence. The gradients of the loss function with respect to the parameters of the network, such as $W_h, W_x$, and $W_y$, are computed using the chain rule. For example, the gradient of the loss with respect to $W_x$ is:

$$
\frac{\partial L}{\partial W_x} = \sum_{t=1}^{T} \frac{\partial L}{\partial h_t} \cdot x_t^{\top} \quad (464)
$$

This captures the contribution of each input to the overall error at all time steps, ensuring that the model learns the correct relationships between inputs and hidden states. Similarly, the gradients with respect to $W_h$ and $b_h$ account for the recurrence in the hidden state, enabling the model to adjust its internal parameters in response to the sequential nature of the data. Despite their theoretical elegance, RNNs face significant practical challenges during training, primarily due to the **vanishing gradients problem**. This issue arises when the gradients propagate through many time steps, causing them to decay exponentially, especially when using activation functions like tanh. As a result, the influence of distant time steps diminishes, making it difficult for the network to learn long-term dependencies. The mathematical manifestation of this problem is seen in the norm of the Jacobian matrices associated with the hidden state updates. If the spectral radius of the weight matrices $W_h$ is close to or greater than 1, the gradients can either vanish or explode, leading to unstable training dynamics. To mitigate this issue, several solutions have been proposed, including the use of Long Short-Term Memory (LSTM) networks and Gated Recurrent Units (GRUs), which introduce gating mechanisms to better control the flow of information through the network. LSTMs, for example, incorporate a memory cell $C_t$, which allows the network to store information over long periods of time. The update rules for the LSTM are governed by three gates: the forget gate $f_t$, the input gate $i_t$, and the output gate $o_t$, which control how much of the previous memory and new information to retain. The equations governing the LSTM are:

$$
f_t = \sigma(W_f h_{t-1} + U_f x_t + b_f) \quad (465)
$$

$$
i_t = \sigma(W_i h_{t-1} + U_i x_t + b_i) \quad (466)
$$

$$
o_t = \sigma(W_o h_{t-1} + U_o x_t + b_o) \quad (467)
$$

$$
\tilde{C}_t = \tanh(W_C h_{t-1} + U_C x_t + b_C) \quad (468)
$$

$$
C_t = f_t \cdot C_{t-1} + i_t \cdot \tilde{C}_t \quad (469)
$$

$$
h_t = o_t \cdot \tanh(C_t) \quad (470)
$$

In these equations, the forget gate $f_t$ determines how much of the previous memory cell $C_{t-1}$ to retain, the input gate $i_t$ governs how much new information to store in the candidate memory cell $\tilde{C}_t$, and the output gate $o_t$ controls how much of the memory cell should influence the current output. The LSTM's architecture allows for the maintenance of long-term dependencies by selectively forgetting or retaining information, effectively alleviating the vanishing gradient problem, and enabling the network to learn from longer sequences. The GRU, an alternative to the LSTM, simplifies this architecture by combining the forget and input gates into a single update gate $z_t$, and introduces a reset gate $r_t$ to control the influence of the previous hidden state. The GRU's update rules are:

$$
z_t = \sigma(W_z h_{t-1} + U_z x_t + b_z) \quad (471)
$$

$$
r_t = \sigma(W_r h_{t-1} + U_r x_t + b_r) \quad (472)
$$

$$
\tilde{h}_t = \tanh(W h_{t-1} + U x_t + b) \quad (473)
$$

$$
h_t = (1 - z_t) \cdot h_{t-1} + z_t \cdot \tilde{h}_t \quad (474)
$$

Here, $z_t$ controls the amount of the previous hidden state $h_{t-1}$ to retain, and $r_t$ determines how much of the previous hidden state should influence the candidate hidden state $\tilde{h}_t$. The GRU's simplified structure still allows it to effectively capture long-range dependencies while being computationally more efficient than the LSTM.

In summary, sequence modeling in RNNs involves a series of recurrent updates to the hidden state, driven by both the current input and the previous hidden state, and is trained via backpropagation through time. The introduction of specialized gating mechanisms in LSTMs and GRUs alleviates issues such as vanishing gradients, enabling the networks to learn and maintain long-term dependencies. Through these advanced architectures, RNNs can effectively model complex temporal relationships, making them powerful tools for tasks such as time-series prediction, natural language processing, and sequence generation.

## 8.3 应用于自然语言处理

### 文献综述

Yang et al. (2020) [377] 探索了深度学习模型（包括 RNN）在电子商务平台情感分析中的有效性。它强调了 RNN 架构（包括 LSTM 和 GRU）如何通过捕捉客户评论中的序列依赖关系，优于传统的 NLP 技术。该研究提供了实证证据，证明 RNN 在分析消费者情绪方面具有更高的准确性。Manikandan et al. (2025) [378] 研究了 RNN 如何改进电子邮件过滤中的垃圾邮件检测。通过利用循环结构，该研究展示了 RNN 如何有效识别电子邮件文本中指示垃圾邮件或网络钓鱼尝试的模式。它还将基于 RNN 的模型与其他 ML 方法进行比较，突出了 RNN 在处理上下文词序列方面的鲁棒性。Isiaka et al. (2025) [379] 研究了 AI 技术（特别是深度学习模型）在预测性医疗保健应用中的应用。它强调了 RNN 如何使用 NLP 技术分析患者记录和医学报告。该研究表明，基于 RNN 的 NLP 模型通过从非结构化文本数据中提取有意义的见解，增强了医疗诊断和决策。Petrov et al. (2025) [380] 讨论了 RNN 在文本数据情感分类中的作用，这是一项基本的 NLP 任务。该论文评估了各种基于 RNN 的架构，包括 BiLSTM，以提高社交媒体文本和聊天机器人响应中情感识别的准确性。Liang (2025) [381] 关注 RNN 在教育环境中的应用，具体用于自动评分和反馈生成。该研究提出了一种基于 RNN 的 NLP 系统，能够分析学生回答，提供实时评估，并生成上下文反馈。Jin (2025) [382] 探讨了 RNN 如何优化与药学教育相关的文本生成任务。它展示了 NLP 驱动的 RNN 模型如何从医学文献生成高质量的文本摘要，确保制药行业准确的知识传播。McNicholas et al. (2025) [383] 研究了 RNN 如何通过从非结构化医学文本中提取见解来促进危重症中的临床决策。该研究强调，基于 RNN 的 NLP 模型通过基于临床记录和医师报告预测结果来改善患者护理。Abbas 和 Khammas (2024) [384] 引入了一种基于 RNN 的 NLP 技术，用于检测 IoT 网络中的恶意软件。该研究说明了 RNN 分类器如何处理日志和文本模式以识别恶意软件，使 RNN 在网络安全应用中至关重要。Kalonia 和 Upadhyay (2025) [385] 使用 NLP 技术将 RNN 应用于软件故障预测。它展示了循环网络如何分析错误报告和软件文档以预测软件应用程序中的潜在故障，帮助开发人员进行主动调试。Han et al. (2025) [386] 讨论了 RNN 在对话式 AI 中的应用，重点关注聊天机器人和虚拟助手。该研究提出了一种由 RNN 驱动的 NLP 模型，用于改进对话管理和用户交互，显著增强了 AI 驱动聊天系统的响应能力。

循环神经网络（RNN）是专门设计用于处理序列数据的深度学习架构，这一关键特性使其在自然语言处理（NLP）的应用中不可或缺。RNN 的数学基础在于其处理输入序列 $x_1, x_2, ..., x_T$ 的能力，其中 $T$ 表示序列的长度。在每个时间步 $t$，网络使用当前输入 $x_t$ 和先前隐藏状态 $h_{t-1}$ 更新其隐藏状态 $h_t$。这种递归关系在数学上由以下方程表示：

$$
h_t = \sigma(W_h h_{t-1} + W_x x_t + b) \quad (475)
$$

这里，$\sigma$ 是非线性激活函数，如双曲正切（tanh）或整线性单元（ReLU），$W_h$ 是与前一隐藏状态 $h_{t-1}$ 相关的权重矩阵，$W_x$ 是与当前输入 $x_t$ 相关的权重矩阵，$b$ 是偏置项。由 $\sigma$ 引入的非线性使网络能够学习输入和输出之间的复杂关系。每个时间步的输出 $y_t$ 计算如下：

$$
y_t = W_y h_t + c \quad (476)
$$


where $W_y$ 是对应输出的权重矩阵，$c$ 是输出的偏置项。然后使用输出 $y_t$ 计算每个时间步可能输出的预测概率分布，通常通过分类任务的 softmax 函数：

```
P(y_t|h_t) = \text{softmax}(W_y h_t + c)
```

在诸如语言建模等 NLP 任务中，目标是给定所有先前单词来预测序列中的下一个单词。RNN 被训练用于基于先前单词来估计下一个单词 $w_t$ 的条件概率分布 $P(w_t|w_1, w_2, \dots, w_{t-1})$。序列 $w_1, w_2, \dots, w_T$ 的完整似然可以写成：

```
P(w_1, w_2, \dots, w_T) = \prod_{t=1}^T P(w_t|w_1, w_2, \dots, w_{t-1})
```

对于 RNN，这种条件概率通过递归更新隐藏状态并为每个单词生成概率分布来建模。在每个时间步，下一个单词的概率计算如下：

```
P(w_t|h_{t-1}) = \text{softmax}(W_y h_t + c)
```

网络通过最小化真实单词序列的负对数似然来训练：

```
\mathcal{L} = - \sum_{t=1}^T \log P(w_t|h_{t-1})
```

此损失函数指导权重矩阵 $W_h, W_x, \text{和 } W_y$ 的优化，以最大化正确单词序列的似然。随着网络从大型数据集中学习，它发展出基于序列中先前单词提供的上下文来预测单词的能力。RNN 在 NLP 中的一个关键扩展是机器翻译，即将一种语言中的一个单词序列映射到目标语言中的另一个序列。这通常使用序列到序列（Seq2Seq）架构来建模，该架构由两个 RNN 组成：编码器和解码器。编码器 RNN 处理输入序列 $x_1, x_2, \dots, x_T$，在每个时间步更新其隐藏状态：

```
h_t^{\text{enc}} = \sigma(W_h^{\text{enc}} h_{t-1}^{\text{enc}} + W_x^{\text{enc}} x_t + b^{\text{enc}})
```

编码器的最终隐藏状态 $h_T^{\text{enc}}$ 传递给解码器作为其初始隐藏状态。解码器 RNN 通过在每个时间步更新其隐藏状态来生成目标序列 $y_1, y_2, \dots, y_T$，同时使用先前的隐藏状态 $h_{t-1}^{\text{dec}}$ 和先前的输出 $y_{t-1}$：

```
h_t^{\text{dec}} = \sigma(W_h^{\text{dec}} h_{t-1}^{\text{dec}} + W_x^{\text{dec}} y_{t-1} + b^{\text{dec}})
```

解码器在每个时间步生成目标词汇表上的概率分布：

```
P(y_t|h_t^{\text{dec}}) = \text{softmax}(W_y^{\text{dec}} h_t^{\text{dec}} + c^{\text{dec}})
```

Seq2Seq 模型的训练基于最小化交叉熵损失函数：

```
\mathcal{L} = - \sum_{t=1}^T \log P(y_t|h_t^{\text{dec}})
```

这确保网络学习将输入序列映射到输出序列。通过在大量配对语句语料库上训练，Seq2Seq 模型学习将句子从一种语言翻译成另一种语言，其中编码器捕获输入句子的上下文，解码器生成翻译后的句子。

RNN 在情感分析中也很有效，这是一项将句子情感（积极、消极或中性）进行分类的任务。给定单词序列 \(x_1, x_2, \dots, x_T\)，RNN 依次处理每个单词，更新其隐藏状态：

\[ h_t = \sigma(W_h h_{t-1} + W_x x_t + b) \]

处理完整个句子后，最终隐藏状态 \(h_T\) 用于分类情感。通过对最终隐藏状态应用 softmax 函数来获取输出：

\[ y = \text{softmax}(W_y h_T + c) \]

其中 \(W_y\) 是与输出层关联的权重矩阵。网络被训练以最小化交叉熵损失：

\[ \mathcal{L} = -\sum_{t=1}^T \log P(y|h_T) \]

这使 RNN 能够通过学习单词与情感标签之间的关系来分类句子的整体情感。情感分析对客户反馈分析、社交媒体监控和舆情挖掘等应用很有用。在命名实体识别（NER）中，RNN 用于识别和分类文本中的命名实体，如人员、地点和组织。RNN 处理序列中的每个单词 \(x_t\)，在每个时间步更新其隐藏状态：

\[ h_t = \sigma(W_h h_{t-1} + W_x x_t + b) \]

在每个时间步，输出是可能实体标签上的概率分布：

\[ P(y_t|h_t) = \text{softmax}(W_y h_t + c) \]

网络被训练以最小化交叉熵损失：

\[ \mathcal{L} = -\sum_{t=1}^T \log P(y_t|h_t) \]

通过学习用适当的实体标签分类每个单词，RNN 可以执行信息提取任务，例如在文本中识别人员、组织和地点。这对于文档分类、知识图构建和问答等应用至关重要。在语音识别中，RNN 用于将口语转录为文本。RNN 的输入由一系列声学特征组成，例如从音频信号中提取的梅尔频率倒谱系数（MFCCs）。在每个时间步 \(t\)，RNN 更新其隐藏状态：

\[ h_t = \sigma(W_h h_{t-1} + W_x x_t + b) \]

在每个时间步，输出是音素或单词上的概率分布：

\[ P(w_t|h_t) = \text{softmax}(W_y h_t + c) \]

网络通过最小化负对数似然来训练：

\[ \mathcal{L} = -\sum_{t=1}^T \log P(w_t|h_t) \]

通过学习声学特征与相应单词或音素之间的映射，RNN 可以将语音转录为文本，这对于语音助手、转录服务和语音转文本系统等应用至关重要。

总之，RNN 是处理机器翻译、情感分析、命名实体识别和语音识别等 NLP 任务中序列数据的强大工具。它们按时间依赖方式处理输入序列的能力使其能够捕获长程依赖，因此非常适合 NLP 及其他领域的复杂任务。然而，梯度消失和梯度爆炸等挑战需要使用更先进的架构，如 LSTM 和 GRU，以增强其在现实世界应用中的性能。

# 9 高级架构

## 9.1 Transformer 和注意力机制

文献综述：Vaswani 等人 [340] 引入了 Transformer 架构，用完全基于注意力的框架取代循环模型以进行序列处理。他们制定了自注意力机制，从数学上定义了查询-键-值（QKV）变换。他们证明了相对于 RNN 的可扩展性优势，展示了 O(1) 并行化优势，并引入了多头注意力，实现了上下文化嵌入。Nannepagu 等人 [341] 探索了将 Transformer 与深度强化学习（DQN）相结合的混合 AI 架构。他们开发了 Transformer 增强强化学习的理论框架，并讨论了自注意力如何改进用于金融时间序列预测的特征表示。Rose 等人 [342] 研究了用于网络安全应用的视觉 Transformer（ViT），考察了基于注意力的异常检测。他们从理论上比较了自注意力与 CNN 特征提取，并为网络安全检测模型中的注意力权重优化提出了一种新的损失函数。Buehler [343] 探索了图神经网络（GNN）与 Transformer 架构之间的理论相互作用。他们开发了同构自注意力，该机制保留图拓扑信息，并在 Transformer 注意力中引入了图结构位置嵌入。Tabipour 和 Madanizadeh [344] 将 Set Transformer 作为高维动态系统中 Transformer 的理论扩展进行了研究，并引入了置换不变自注意力机制以在决策任务中替代标准 Transformer，并从理论上形式化了非序列数据的注意力机制。Kim 等人（2024）[310] 开发了基于 Transformer 的视频监控异常检测框架。他们形式化了一种新的时空自注意力机制来检测视频中的异常，并扩展了标准 Transformer 架构以处理高维视频数据。Li 和 Dong [345] 研究了无线通信网络中基于 Transformer 的注意力机制。他们为大规模 MIMO 信道估计引入了混合空间和时间注意力层，并提供了基于注意力的信号恢复的严格数学证明。Asefa 和 Assabie [346] 研究了基于 Transformer 的翻译模型的特定语言适应。他们引入了低资源语言翻译的注意力机制正则化，并分析了不同位置编码策略对翻译质量的影响。Liao 和 Chen [347] 将 Transformer 架构应用于深度伪造检测，分析了面部特征分析的自注意力机制。他们从理论上比较了用于伪造检测的 CNN 和 ViT，并引入了注意力头脱机以提高对抗攻击的鲁棒性。Jiang 等人 [348] 提出了一种基于 Transformer 的医学影像重建新方法。他们引入了空间和通道 Transformer（SCFormer）以增强基于注意力的特征聚合，并从理论上将对比学习扩展到 Transformer 编码器。

Transformer 模型是一种高级神经网络架构，其根本由自注意力机制定义，该机制使序列数据能够进行全局上下文感知计算。该模型处理由以下表示的输入序列：

```
\mathbf{X} \in \mathbb{R}^{n \times d_{\text{model}}},\qquad (494)
```

其中 $n$ 表示序列长度，$d_{\text{model}}$ 表示嵌入维度。序列中的每个标记使用可训练矩阵 $\mathbf{W}^Q, \mathbf{W}^K,$ 和 $\mathbf{W}^V$ 投影到三个学习空间——查询 $\mathbf{Q}$、键 $\mathbf{K}$ 和值 $\mathbf{V}$ 中，使得：

```
\mathbf{Q} = \mathbf{X}\mathbf{W}^Q, \quad \mathbf{K} = \mathbf{X}\mathbf{W}^K, \quad \mathbf{V} = \mathbf{X}\mathbf{W}^V,\qquad (495)
```

其中 $\mathbf{W}^Q, \mathbf{W}^K, \mathbf{W}^V \in \mathbb{R}^{d_{\text{model}} \times d_k}$，$d_k$ 为查询和键的维度。标记之间的成对相似度由点积 $\mathbf{Q}\mathbf{K}^{\top}$ 决定，并按因子


\frac{1}{\sqrt{d_k}} 以确保数值稳定性，得到原始注意力分数：

\[\mathbf{S} = \frac{\mathbf{Q}\mathbf{K}^\top}{\sqrt{d_k}}\]

其中 \(\mathbf{S} \in \mathbb{R}^{n \times n}\)。这些分数使用 softmax 函数归一化，得到注意力权重 \(\mathbf{A}\)，其中

\[A_{ij} = \frac{\exp(S_{ij})}{\sum_{k=1}^n \exp(S_{ik})}\]

确保 \(\sum_{j=1}^n A_{ij} = 1\)。注意力机制的输出计算为值的加权和：

\[\mathbf{Z} = \mathbf{A}\mathbf{V}\]

其中 \(\mathbf{Z} \in \mathbb{R}^{n \times d_v}\)，\(d_v\) 为值向量的维数。该过程可简洁地表示为

\[\text{Attention}(\mathbf{Q}, \mathbf{K}, \mathbf{V}) = \text{softmax} \left( \frac{\mathbf{Q}\mathbf{K}^\top}{\sqrt{d_k}} \right) \mathbf{V}.\]

多头注意力通过将 \(\mathbf{Q}, \mathbf{K}, \mathbf{V}\) 分割为 \(h\) 个不同的头来扩展此机制，每个头在其子空间中运行。对于第 \(i\) 个头：

\[\text{head}_i = \text{Attention}(\mathbf{Q}_i, \mathbf{K}_i, \mathbf{V}_i)\]

其中 \(\mathbf{Q}_i = \mathbf{X}\mathbf{W}_i^Q\)，\(\mathbf{K}_i = \mathbf{X}\mathbf{W}_i^K\)，\(\mathbf{V}_i = \mathbf{X}\mathbf{W}_i^V\)。所有头的输出被拼接并线性变换：

\[\text{MultiHead}(\mathbf{Q}, \mathbf{K}, \mathbf{V}) = \text{Concat}(\text{head}_1, \dots, \text{head}_h)\mathbf{W}^O.\]

其中 \(\mathbf{W}^O \in \mathbb{R}^{hd_v \times d_{\text{model}}}\)。该架构使模型能够同时捕获多种类型的关系。位置编码被添加到输入嵌入 \(\mathbf{X}\) 中以保留序列顺序。这些编码 \(\mathbf{P} \in \mathbb{R}^{n \times d_{\text{model}}}\) 定义为：

\[P_{(pos, 2i)} = \sin \left( \frac{\text{pos}}{10000^{2i/d_{\text{model}}}} \right), \quad P_{(pos, 2i+1)} = \cos \left( \frac{\text{pos}}{10000^{2i/d_{\text{model}}}} \right)\]

确保每个位置 pos 和维度索引 \(i\) 具有独特的表示。前馈网络 (FFN) 应用两个带有中间 ReLU 激活的密集层：

\[\text{FFN}(\mathbf{z}) = \max(0, \mathbf{z}\mathbf{W}_1 + \mathbf{b}_1)\mathbf{W}_2 + \mathbf{b}_2.\]

其中 \(\mathbf{W}_1 \in \mathbb{R}^{d_{\text{model}} \times d_{\text{ff}}}\)，\(\mathbf{W}_2 \in \mathbb{R}^{d_{\text{ff}} \times d_{\text{model}}}\)，且 \(d_{\text{ff}} > d_{\text{model}}\)。残差连接和层归一化贯穿始终以稳定训练，输出由

\[\mathbf{H}_{\text{out}} = \text{LayerNorm}(\mathbf{H}_{\text{in}} + \text{FFN}(\mathbf{H}_{\text{in}})).\]

训练优化输出分布上的交叉熵损失：

\[\mathcal{L} = - \sum_{t=1}^T \log P(y_t \mid y_{<t}, \mathbf{x})\]

其中 \(P(y_t \mid y_{<t}, \mathbf{x})\) 使用 logits \(\mathbf{z}_t \mathbf{W}_{\text{out}} + \mathbf{b}_{\text{out}}\) 的 softmax 进行建模，参数为 \(\mathbf{W}_{\text{out}}, \mathbf{b}_{\text{out}}\)。Transformer 由于计算 \(\mathbf{Q}\mathbf{K}^\top\)，每个注意力层的复杂度为 \(O(n^2 d_k)\)，但其并行化能力使其比循环网络更高效。这种数学形式化，加上稀疏注意力和动态规划等创新，已使 Transformer 成为现代序列建模任务的基石。

尽管这种二次复杂度对很长序列构成挑战，但与需要 O(n) 个顺序步骤的 RNN 相比，它允许更大的并行化。此外，存储注意力权重的 O(n^2) 内存复杂度可以通过稀疏近似或层次结构注意力来缓解。Transformer 架构的灵活性和有效性源于其通过适当修改其组件来处理多样化任务的能力。例如，在视觉 Transformer (ViT) 中，输入序列由展平的图像补丁形成，位置编码捕获空间关系。相比之下，在翻译等序列到序列任务中，交叉注意力机制使解码器能够关注编码器输出的相关部分。

总之，Transformer 在神经网络设计中代表了范式转移，用注意力取代循环，实现了前所未有的可扩展性和性能。注意力机制的严格数学基础，结合多头注意力、位置编码和前馈层等架构创新，奠定了其在各领域的成功。

## 9.2 生成对抗网络（GANs）

文献综述：Goodfellow et. al. [349] 在其里程碑论文中介绍了生成对抗网络 (GANs)，其中生成器和判别器在极小极大博弈中竞争。他们建立了对抗学习的理论基础，并使用博弈论开发了 GAN 的数学表述。他们还在深度学习中引入了非合作极小极大优化。

Chappidi 和 Sundaram [350] 将图神经网络 (GNNs) 与 GAN 相结合，用于复杂的现实世界感知任务。他们从理论上将 GAN 与强化学习集成，用于自改进模型，并开发了增强 GAN 收敛稳定性的双重 Q 学习机制。

Joni [351] 为基于 GAN 的生成模型用于高级图像合成提供了全面的理论概述。他们形式化了 GAN 损失函数及其优化挑战，并引入了渐进式增长 GAN 作为高分辨率图像生成的解决方案。

Li et. al. (2024) [305] 将 GAN 扩展到材料科学，优化了晶体结构预测过程。他们开发了用于分子建模的 GAN 框架，并展示了 GAN 在计算机视觉任务之外的科学模拟中的应用。

Sekhavat (2024) [299] 分析了艺术图像生成中 GAN 的哲学和理论基础。他从认知科学角度讨论了 GAN，并建立了 GAN 训练与计算美学之间的联系。

Kalaiarasi 和 Sudharani (2024) [352] 考察了基于 GAN 的图像隐写术，利用对抗训练优化数据隐藏技术。他们将对抗训练的理论特性扩展到安全应用，并展示了 GAN 如何最大限度地减少数据隐藏中的感知失真。

Arjmandi-Tash 和 Mansourian (2024) [353] 探索了科学计算中的 GAN，生成了逼真的光电探测器数据集。他们展示了 GAN 作为合成数据增强的理论工具，并为传感器建模制定了 GAN 损失函数的概率方法。

Gao (2024) [354] 在物理信息学习中弥合了 GAN 与偏微分方程 (PDEs) 之间的差距。他建立了使用基于 GAN 的架构求解 PDE 的理论框架，并开发了结合对抗方法和变分方法的新损失函数。

Hisama et. al. [355] 将 GAN 应用于计算化学，生成新的合金催化剂结构。他们引入了 Wasserstein GAN (WGANs) 用于分子设计，并使用 GAN 生成的潜空间来预测催化剂活性。

Wang 和 Zhang (2024) [356] 提出了一种用于医学图像分割的改进 GAN 框架。他们开发了一种新的注意力增强 GAN 用于鲁棒分割，并提供了对抗分割损失函数的数学表述。

生成对抗网络 (GANs) 是一个复杂的数学框架，旨在通过利用生成器 \(G\) 和判别器 \(D\) 两个神经网络之间的竞争动态来建模复杂的概率分布。这些网络由权重 \(\theta_G \in \Theta_G\) 和 \(\theta_D \in \Theta_D\) 参数化，它们的相互作用在数学上被表述为两人零和博弈。

生成器 \(G : \mathbb{R}^d \to \mathbb{R}^n\) 将潜在变量 \(\mathbf{z} \sim p_{\mathbf{z}}(\mathbf{z})\) 映射到合成数据样本 \(\hat{\mathbf{x}} = G(\mathbf{z})\)，其中 \(p_{\mathbf{z}}\) 是先验概率分布（通常是均匀分布或高斯分布）。判别器 \(D : \mathbb{R}^n \to [0, 1]\) 分配一个概率分数 \(D(\mathbf{x})\)，指示 \(\mathbf{x}\) 是源自真实数据分布 \(p_{\text{data}}(\mathbf{x})\) 还是生成分布 \(p_g(\mathbf{x})\)，后者隐式定义为 \(p_{\mathbf{z}}\) 在 \(G\) 下的推前度量，即 \(p_g = G_{\#}p_{\mathbf{z}}\)。管理 GAN 的优化问题表述为

```
\min_G \max_D V(D, G) = \mathbb{E}_{\mathbf{x} \sim p_{\text{data}}}[\log D(\mathbf{x})] + \mathbb{E}_{\mathbf{z} \sim p_{\mathbf{z}}}[\log(1 - D(G(\mathbf{z})))], \quad (506)
```

其中 \(\mathbb{E}\) 表示期望算子。该目标旨在最大化判别器区分真实样本和生成样本的能力，同时最小化生成器生成可与真实数据区分的样本的能力。对于固定的生成器 \(G\)，最优判别器 \(D^*\) 通过最大化 \(V(D, G)\) 得到，结果为

```
D^*(\mathbf{x}) = \frac{p_{\text{data}}(\mathbf{x})}{p_{\text{data}}(\mathbf{x}) + p_g(\mathbf{x})}. \quad (507)
```

将 \(D^*\) 代入价值函数将其简化为

```
V(D^*, G) = \mathbb{E}_{\mathbf{x} \sim p_{\text{data}}} \left[ \log \frac{p_{\text{data}}(\mathbf{x})}{p_{\text{data}}(\mathbf{x}) + p_g(\mathbf{x})} \right] + \mathbb{E}_{\mathbf{x} \sim p_g} \left[ \log \frac{p_g(\mathbf{x})}{p_{\text{data}}(\mathbf{x}) + p_g(\mathbf{x})} \right]. \quad (508)
```

该表达式等价于最小化 \(p_{\text{data}}\) 与 \(p_g\) 之间的 Jensen-Shannon (JS) 散度，定义为

```
\text{JS}(p_{\text{data}} \| p_g) = \frac{1}{2} \text{KL}(p_{\text{data}} \| M) + \frac{1}{2} \text{KL}(p_g \| M), \quad (509)
```

其中 \(M = \frac{1}{2}(p_{\text{data}} + p_g)\)，\(\text{KL}(p \| q) = \int p(\mathbf{x}) \log \frac{p(\mathbf{x})}{q(\mathbf{x})} d\mathbf{x}\) 是 Kullback-Leibler 散度。在 Nash 平衡点，\(p_g = p_{\text{data}}\)，JS 散度消失，对所有 \(\mathbf{x}\) 均有 \(D^*(\mathbf{x}) = \frac{1}{2}\)。训练期间的梯度更新使用随机梯度下降推导。对于判别器，梯度由以下给出

```
\nabla_{\theta_D} V(D, G) = \mathbb{E}_{\mathbf{x} \sim p_{\text{data}}} [\nabla_{\theta_D} \log D(\mathbf{x})] + \mathbb{E}_{\mathbf{z} \sim p_{\mathbf{z}}} [\nabla_{\theta_D} \log(1 - D(G(\mathbf{z})))]. \quad (510)
```

训练生成对抗网络 (GAN) 涉及对判别器参数 \(\theta_D\) 和生成器参数 \(\theta_G\) 进行迭代更新。判别器参数通过梯度上升来最大化价值函数 \(V(D, G)\)，而生成器参数通过梯度下降来最小化同一价值函数。将 \(D\) 和 \(G\) 相对于其参数的梯度表示为 \(\nabla_{\theta_D}\) 和 \(\nabla_{\theta_G}\)，更新如下：

```
\theta_D \leftarrow \theta_D + \eta_D \nabla_{\theta_D} [\mathbb{E}_{x \sim p_{\text{data}}} [\log D(x)] + \mathbb{E}_{z \sim p_z} [\log (1 - D(G(z)))]] , \quad (511)
```

和

```
\theta_G \leftarrow \theta_G - \eta_G \nabla_{\theta_G} [\mathbb{E}_{z \sim p_z} [\log (1 - D(G(z)))]] . \quad (512)
```

在实践中，为了解决梯度消失问题，通常使用生成器的替代损失函数，定义为：

```
-\mathbb{E}_{z \sim p_z} [\log D(G(z))] . \quad (513)
```

这种修改确保了当判别器表现良好时具有更强的梯度信号，从而有效改善生成器的训练动态。对于生成器，原始表述中的梯度表示为

```
\nabla_{\theta_G} V(D, G) = -\mathbb{E}_{\mathbf{z} \sim p_{\mathbf{z}}} [\nabla_{\theta_G} \log(1 - D(G(\mathbf{z})))], \quad (514)
```



但由于当 \( D(G(\mathbf{z})) \) 接近 0 时会出现梯度消失，因此更倾向于使用非饱和生成器损失：

\[
\mathcal{L}_G = -\mathbb{E}_{\mathbf{z}\sim p_\mathbf{z}}[\log D(G(\mathbf{z}))]. \quad (515)
\]

GANs的收敛性与 \( D^*(\mathbf{x}) \) 的性质以及 \( p_g \) 与 \( p_{\text{data}} \) 的对齐性本质上是相关联的。然而，由于目标函数的非凸性，模式崩溃和训练不稳定性经常被观察到。Wasserstein GANs（WGANs）通过用Wasserstein-1距离取代JS散度来解决这些问题，其定义为

\[
W(p_{\text{data}}, p_g) = \inf_{\gamma \in \Pi(p_{\text{data}}, p_g)} \mathbb{E}_{(\mathbf{x}, \mathbf{y}) \sim \gamma} [||\mathbf{x} - \mathbf{y}||]. \quad (516)
\]

其中 \( \Pi(p_{\text{data}}, p_g) \) 是 \( p_{\text{data}} \) 和 \( p_g \) 的所有耦合集合。利用Kantorovich-Rubinstein对偶性，Wasserstein距离被重新表述为

\[
W(p_{\text{data}}, p_g) = \sup_{||f||_L \le 1} \mathbb{E}_{\mathbf{x} \sim p_{\text{data}}}[f(\mathbf{x})] - \mathbb{E}_{\mathbf{x} \sim p_g}[f(\mathbf{x})]. \quad (517)
\]

其中 \( f \) 是一个1-Lipschitz函数。为了强制执行Lipschitz约束，应用了梯度惩罚，确保 \( ||\nabla f(\mathbf{x})|| \le 1 \)。

GANs的数学框架整合了博弈论、优化和信息几何的要素。其训练涉及求解高维非凸博弈，由于鞍点以及 \( G \) 与 \( D \) 之间复杂的相互作用，收敛的理论保证具有挑战性。尽管如此，GANs代表了生成建模的一种数学优雅范式，正在进行的研究正在扩展其理论和实践能力。

## 9.3 自动编码器和变分自动编码器

### 文献综述

Zhang等人（2024）[303] 探索了VAEs与图像压缩中速率失真理论之间的理论联系。他们建立了将概率自动编码与有损图像压缩联系起来的数学框架，并引入了分层变分推断以提高生成建模能力。

Wang和Huang（2025）[304] 开发了过参数化VAEs中收敛的正式数学证明。他们为训练VAEs建立了严格的数学极限，并引入了神经切核（NTK）理论来研究VAEs在过参数化下的行为。

Li等人（2024）[305] 将VAEs扩展到材料科学，优化晶体结构预测。他们开发了基于VAE的分子建模框架，并展示了生成模型在图像应用之外的作用。

Huang（2024）[306] 回顾了VAEs、GANs和扩散模型在图像生成中的关键技术。他们分析了VAEs中与基于扩散的方法相比的概率建模，并建立了生成模型的理论层次结构。

Chenebuah（2024）[307] 研究了用于能源材料模拟和分子性质预测的自动编码器。他们引入了一种用于物理模拟的新型AE-VAE混合模型，并建立了密度泛函理论（DFT）与自动编码器之间的理论联系。

Furth等人（2024）[308] 探索了用于预测化学性质的图神经网络（GNNs）和VAEs。他们为基于图的学习建立了VAEs的理论属性，并将自动编码器扩展到化学反应预测。

Gong等人 [309] 研究了用于材料设计的条件变分自动编码器（CVAEs）。他们为条件生成建模引入了新的损失函数，并从理论上证明了VAEs如何优化材料选择。

Kim等人 [310] 使用基于Transformer的自动编码器（AEs）进行视频异常检测。他们建立了AEs用于时间序列异常检测的理论改进，并使用时空自动编码器嵌入来捕捉视频中的异常。

Albert等人（2024）[311] 比较了用于降维的核心学习嵌入（KLE）和变分自动编码器。他们引入了用于大气建模的基于VAE的模型，并建立了VAEs与基于核的模型之间的数学比较。

Sharma等人（2024）[312] 探索了自动编码器在网络入侵检测中的实际应用。他们将自动编码器确立为异常检测的强大特征提取器，并对自动编码器潜空间表示进行了正式研究。

一个 **自动编码器 (AE)** 是一种无监督学习模型，试图在较低维的潜空间中学习输入数据 $\mathbf{x} \in \mathbb{R}^d$ 的紧凑表示。该模型由两个主要组件组成：编码器函数 $f_{\theta_e}$ 和解码器函数 $f_{\theta_d}$。编码器 $f_{\theta_e} : \mathbb{R}^d \rightarrow \mathbb{R}^l$ 将输入数据 $\mathbf{x}$ 映射到潜码 $\mathbf{z}$，其中 $l \ll d$，表示压缩信息。解码器 $f_{\theta_d} : \mathbb{R}^l \rightarrow \mathbb{R}^d$ 然后从这个潜码重建输入，产生一个近似值 $\hat{\mathbf{x}}$。通常用于训练自动编码器的损失函数是重建损失，通常表述为均方误差（MSE）：

\[
\mathcal{L}(\mathbf{x}, \hat{\mathbf{x}}) = \|\mathbf{x} - \hat{\mathbf{x}}\|_2^2. \quad (518)
\]

优化过程旨在在数据集 $D$ 上最小化重建误差，假设输入数据 $\mathbf{x}$ 上存在分布 $p(\mathbf{x})$。目标是通过求解以下优化问题来学习最优参数 $\theta_e$ 和 $\theta_d$：

\[
\min_{\theta_e, \theta_d} \mathbb{E}_{\mathbf{x} \sim p(\mathbf{x})} \left[ \|\mathbf{x} - f_{\theta_d}(f_{\theta_e}(\mathbf{x}))\|_2^2 \right]. \quad (519)
\]

这种表述驱动编码器-解码器架构朝着学习保留输入数据关键特征的潜在表示方向发展，从而允许其被高效重建。此问题的解通常通过 **随机梯度下降 (SGD)** 来寻求，其中计算损失相对于模型参数的梯度并通过网络进行反向传播。与确定性自动编码器相反，**变分自动编码器 (VAE)** 引入了概率模型以更好地捕捉潜在变量的分布。VAE使用潜在变量 $\mathbf{z} \in \mathbb{R}^l$ 对数据生成过程进行建模，并旨在通过对所有可能的潜在变量进行积分来最大化观测数据 $\mathbf{x}$ 的似然性。具体来说，我们有联合分布：

\[
p(\mathbf{x}, \mathbf{z}) = p(\mathbf{x}|\mathbf{z})p(\mathbf{z}). \quad (520)
\]

其中 $p(\mathbf{x}|\mathbf{z})$ 是给定潜在变量的数据似然性，而 $p(\mathbf{z})$ 是潜在变量的先验分布，通常选择为标准高斯分布 $\mathcal{N}(\mathbf{z}; \mathbf{0}, I)$。先验假设 $p(\mathbf{z}) = \mathcal{N}(0, I)$ 简化了建模，因为它对潜空间不施加特定结构，从而允许对数据分布进行灵活建模。VAE中的编码器输出潜在变量上的分布 $q_{\theta_e}(\mathbf{z}|\mathbf{x})$，通常建模为均值 $\mu_{\theta_e}(\mathbf{x})$ 和方差 $\sigma_{\theta_e}(\mathbf{x})$ 的多元高斯分布，即 $q_{\theta_e}(\mathbf{z}|\mathbf{x}) = \mathcal{N}(\mathbf{z}; \mu_{\theta_e}(\mathbf{x}), \sigma_{\theta_e}^2(\mathbf{x})I)$。解码器生成给定潜在变量 $\mathbf{z}$ 的数据 $\mathbf{x}$ 的似然性，表示为 $p_{\theta_d}(\mathbf{x}|\mathbf{z})$，对于连续数据通常采用高斯分布的形式。VAE训练中的一个核心挑战是 **边缘似然性** $p(\mathbf{x})$，它表示观测数据的概率。由于对潜在变量的积分，这个边缘似然性是不可处理的：

\[
p(\mathbf{x}) = \int p_{\theta_d}(\mathbf{x}|\mathbf{z})p(\mathbf{z}) d\mathbf{z}. \quad (521)
\]

为解决这一问题，VAE训练采用 **变分推断**，它使用变分分布 $q_{\theta_e}(\mathbf{z}|\mathbf{x})$ 来近似真实后验 $p(\mathbf{z}|\mathbf{x})$。目标是优化 **证据下界 (ELBO)**，它是对数似然性 $\log p(\mathbf{x})$ 的下界。ELBO是利用 **Jensen不等式** 推导出来的：

\[
\log p(\mathbf{x}) \ge \mathbb{E}_{q_{\theta_e}(\mathbf{z}|\mathbf{x})} [\log p_{\theta_d}(\mathbf{x}|\mathbf{z})] - \text{KL}(q_{\theta_e}(\mathbf{z}|\mathbf{x}) \| p(\mathbf{z})). \quad (522)
\]

其中第一项是给定潜在变量的数据的预期对数似然性，第二项是近似后验与先验之间的 **Kullback-Leibler (KL)散度**



$q_{\theta_e}(\mathbf{z}|\mathbf{x})$ 和先验 \( p(\mathbf{z}) \)。KL 散度充当正则化器，惩罚偏离先验分布的行为。然后可以将 ELBO 写为：

\(\mathcal{L}_{\text{VAE}}(\mathbf{x}) = \mathbb{E}_{q_{\theta_e}(\mathbf{z}|\mathbf{x})} [\log p_{\theta_d}(\mathbf{x}|\mathbf{z})] - \text{KL}(q_{\theta_e}(\mathbf{z}|\mathbf{x}) \| p(\mathbf{z})).\)

这种表述平衡了两个竞争目标：从 **z** 重构 **x** 的似然最大化，以及后验 \( q_{\theta_e}(\mathbf{z}|\mathbf{x}) \) 与先验 \( p(\mathbf{z}) \) 之间的偏差最小化。为了进行优化，我们需要计算 ELBO 相对于参数 \(\theta_e\) 和 \(\theta_d\) 的梯度。但是，由于从分布 \( q_{\theta_e}(\mathbf{z}|\mathbf{x}) \) 中采样是不可微的，因此应用了**重参数化技巧**。这个技巧允许我们将隐变量 **z** 重参数化为：

\(\mathbf{z} = \mu_{\theta_e}(\mathbf{x}) + \sigma_{\theta_e}(\mathbf{x}) \cdot \epsilon,\)

其中 \(\epsilon \sim \mathcal{N}(0, I)\) 是一个标准高斯噪声向量。这使得梯度可以通过隐空间进行反向传播，并允许优化过程通过随机梯度下降进行。在实践中，**蒙特卡洛方法**被用来估计 ELBO 中的期望。这包括从变分后验 \( q_{\theta_e}(\mathbf{z}|\mathbf{x}) \) 中绘制 \(K\) 个样本 \(\mathbf{z}_k\) 并将期望近似为：

\(\hat{\mathcal{L}}_{\text{VAE}}(\mathbf{x}) = \frac{1}{K} \sum_{k=1}^K \log p_{\theta_d}(\mathbf{x}|\mathbf{z}_k) - \frac{1}{K} \sum_{k=1}^K \log q_{\theta_e}(\mathbf{z}_k|\mathbf{x}).\)

这种近似允许高效优化，即使隐空间是高维的且精确期望在计算上不可行。因此，VAE 的**训练过程**包括以下步骤：首先，编码器为每个输入 **x** 产生一个分布 \( q_{\theta_e}(\mathbf{z}|\mathbf{x}) \)；然后，从该分布中采样隐变量 **z**；最后，解码器从隐变量 **z** 重构数据 \(\hat{\mathbf{x}}\)。网络被训练以最大化 ELBO，这有效地平衡了重构损失和 KL 散度项。

在此严谨的探讨中，我们介绍了自编码器和变分自编码器的数学基础。两者之间的核心区别在于 VAE 中引入了概率框架，该框架利用变分推断来优化边缘似然的可处理下界。通过此过程，VAE 学习通过从隐空间采样并重构输入来生成数据，同时通过 KL 散度项的正则化来保持结构良好的隐分布。VAE 的优化框架基于变分推断和重参数化技巧，使基于梯度的优化技术能够高效训练深度生成模型。

# 10 强化学习

文献综述：Sutton 和 Barto (2018) [272] (2021) [273] 撰写了一本关于强化学习的权威教材。它涵盖了基本概念，包括马尔可夫决策过程 (MDP)、时序差分学习、策略梯度方法和函数近似。第二版扩展了深度强化学习内容，涵盖了 DDPG、A3C 和 PPO 等高级算法。Bertsekas 和 Tsitsiklis (1996) [274] 通过引入神经动态规划（即用于不确定性下决策的动态规划方法的扩展），为强化学习奠定了理论基础。它严谨地涵盖了近似动态规划、策略迭代和值函数近似。Kakade (2003) [275] 在其论文中形式化了 RL 的样本复杂度，为智能体学习最优策略所需数据量提供了理论保证。它引入了 PAC-RL (probably approximately correct RL) 框架，该框架显著影响了 RL 算法的评估方式。Szepesvári (2010) [276] 提供了强化学习算法的严谨而简洁的概述，包括值迭代、Q-learning、SARSA、函数近似和策略梯度方法。它为收敛性证明和性能界限提供了深刻的理论洞察。Haarnoja 等人 (2018) [277] 引入了软演员-评论家 (SAC)，这是一种离策略深度强化学习算法，可同时最大化预期奖励和熵。它为处理高维连续动作空间中的勘探-利用权衡提供了强大的理论框架。Mnih 等人 (2015) [278] 引入了深度 Q 网络 (DQN)，展示了如何将深度学习与 Q-learning 相结合，在 Atari 游戏中实现人类水平的性能。作者解决了强化学习中的关键挑战，包括函数近似和稳定性改进。Konda 和 Tsitsiklis (2003) [279] 对演员-评论家方法进行了严谨的理论分析，该方法结合了基于策略和基于值的学习。它正式确立了演员-评论家算法的收敛性证明，并引入了用于策略改进的自然梯度方法。Levine (2018) [280] 为强化学习引入了概率推断框架，将 RL 与贝叶斯推断联系起来。它为最大熵强化学习提供了理论基础，解释了为什么熵正则化目标能带来更好的勘探和稳定性。Mannor 等人 (2022) [281] 对强化学习理论进行了最严谨的数学处理之一。它涵盖了几个主题：RL 算法的 PAC 保证、勘探的复杂度界限、RL 与控制理论之间的联系、流行 RL 方法的收敛速率。Borkar (2008) [282] 严谨分析了随机近似方法，这些方法构成了 TD-learning、Q-learning 和策略梯度方法等 RL 算法的理论支柱。Borkar 从动态系统视角提供了收敛性分析，提供了深刻的数学洞察。

## 10.1 关键概念

强化学习 (RL) 是机器学习的一个分支，涉及智能体在环境中做出决策以最大化随时间推移的累积奖励。这种形式化的决策过程可以使用智能体、状态、动作和奖励等概念来描述，所有这些概念都在马尔可夫决策过程 (MDP) 的框架内进行了数学表述。以下对这些关键概念进行了极其严谨的数学讨论。智能体通过根据环境的当前状态采取动作与环境交互。智能体的目标是最大化随时间推移的预期累积奖励。策略 \(\pi\) 是从状态到动作概率分布的映射。形式上，策略 \(\pi\) 可以写为：

```
\pi : \mathcal{S} \rightarrow \mathcal{P}(\mathcal{A}), (526)
```

其中 \(\mathcal{S}\) 是状态空间，\(\mathcal{A}\) 是动作空间，\(\mathcal{P}(\mathcal{A})\) 是动作上的概率分布集合。策略可以是*确定性*的：

```
\pi(a_t|s_t) = \begin{cases} 1 & \text{if } a_t = \pi(s_t), \\ 0 & \text{otherwise,} \end{cases} (527)
```

其中 \(\pi(s_t)\) 是在状态 \(s_t\) 下选择的动作，或者是*随机*的，在这种情况下，策略为每个状态 \(s_t\) 分配一个动作概率分布。强化学习的目标是找到一个*最优策略* \(\pi^*(s_t)\)，它从任何初始状态开始最大化预期回报（累积奖励）。最优策略定义为：

```
\pi^*(s_t) = \arg \max_{\pi} \mathbb{E} \left[ \sum_{k=0}^{\infty} \gamma^k r_{t+k} \mid s_t \right], (528)
```

其中 \(\gamma\) 是*折扣因子*，它决定未来奖励的权重，\(\mathbb{E}[\cdot]\) 表示在策略 \(\pi\) 下的期望。最优策略可以从*最优动作值函数* \(Q^*(s_t, a_t)\) 中推导出来，我们将在下一节中对其进行定义。状态 \(s_t \in \mathcal{S}\) 描述了时间 \(t\) 时智能体的当前情况，封装了所有影响的相关信息



代理人的决策过程。状态空间 $\mathcal{S}$ 可以是 *离散* 或 *连续* 的。状态转移由概率分布 $P(s_{t+1}|s_t, a_t)$ 控制，它表示在动作 $a_t$ 下从状态 $s_t$ 移动到状态 $s_{t+1}$ 的概率。这些转移满足 *马尔可夫性质*，意味着未来状态仅取决于当前状态和动作，而不取决于之前状态或动作的历史：

$P(s_{t+1}|s_t, a_t) = P(s_{t+1}|s_t, a_t) \quad \forall s_t, s_{t+1} \in \mathcal{S}, a_t \in \mathcal{A}.$ (529)

此外，转移概率满足 *归一化条件*：

\(\sum_{s_{t+1} \in \mathcal{S}} P(s_{t+1}|s_t, a_t) = 1 \quad \forall s_t, a_t.\) (530)

*状态分布* $\rho_t(s_t)$ 表示代理人在时间 $t$ 处于状态 $s_t$ 的概率。状态分布随时间根据转移概率演化：

\(\rho_{t+k}(s_{t+k}) = \sum_{s_t \in \mathcal{S}} P(s_{t+k}|s_t, a_t)\rho_t(s_t),\) (531)

其中 $\rho_t(s_t)$ 是时间 $t$ 的初始分布，$\rho_{t+k}(s_{t+k})$ 是时间 $t + k$ 的分布。代理人在时间 $t$ 于状态 $s_t$ 采取的动作 $a_t$ 会导致转移到状态 $s_{t+1}$ 并获得奖励 $r_t$。代理人旨在选择能最大化其长期奖励的动作。*动作值函数* $Q(s_t, a_t)$ 量化了在状态 $s_t$ 下采取动作 $a_t$ 之后遵循最优策略所期望的累积奖励。它定义为：

\(Q(s_t, a_t) = \mathbb{E} \left[ \sum_{k=0}^{\infty} \gamma^k r_{t+k} \mid s_t, a_t \right].\) (532)

最优动作值函数 $Q^*(s_t, a_t)$ 满足 *贝尔曼最优方程*：

\(Q^*(s_t, a_t) = R(s_t, a_t) + \gamma \sum_{s_{t+1} \in \mathcal{S}} P(s_{t+1}|s_t, a_t) \max_{a_{t+1}} Q^*(s_{t+1}, a_{t+1}).\) (533)

这个递归方程为诸如 *值迭代* 和 *策略迭代* 等动态规划方法奠定了基础。最优策略 $\pi^*(s_t)$ 通过选择最大化动作值函数的动作得到：

\(\pi^*(s_t) = \arg \max_{a_t \in \mathcal{A}} Q^*(s_t, a_t).\) (534)

*最优值函数* $V^*(s_t)$，表示在最优策略下从状态 $s_t$ 获得的期望回报，由以下给出：

\(V^*(s_t) = \max_{a_t \in \mathcal{A}} Q^*(s_t, a_t).\) (535)

最优值函数满足贝尔曼方程：

\(V^*(s_t) = \max_{a_t \in \mathcal{A}} \left[ R(s_t, a_t) + \gamma \sum_{s_{t+1} \in \mathcal{S}} P(s_{t+1}|s_t, a_t) V^*(s_{t+1}) \right].\) (536)

时间 $t$ 的 *奖励* $r_t$ 是一个标量值，表示代理人在状态 $s_t$ 下采取动作 $a_t$ 后获得的即时收益（或成本）。它是一个将状态-动作对映射到实数的函数 $R(s_t, a_t)$：

\(r_t = R(s_t, a_t).\) (537)

代理人的目标是最大化累积奖励，即从时间 $t$ 开始的 *总回报*：

\(G_t = \sum_{k=0}^{\infty} \gamma^k r_{t+k}.\) (538)

代理人寻找最大化期望回报的策略 $\pi$。期望回报的贝尔曼方程为：

$$V^\pi(s_t) = R(s_t, \pi(s_t)) + \gamma \sum_{s_{t+1}\in\mathcal{S}} P(s_{t+1}|s_t, \pi(s_t))V^\pi(s_{t+1}).$$ (539)

这个递归关系有助于求解最优值函数。RL 问题通常建模为 *马尔可夫决策过程 (MDP)*，定义为元组：

$$\mathcal{M} = (\mathcal{S}, \mathcal{A}, P, R, \gamma),$$ (540)

其中：

- $\mathcal{S}$ 是状态空间，
- $\mathcal{A}$ 是动作空间，
- $P(s_{t+1}|s_t, a_t)$ 是状态转移概率，
- $R(s_t, a_t)$ 是奖励函数，
- $\gamma$ 是折扣因子。

代理人的目标是通过找到最大化累积期望奖励的最优策略 $\pi^*(s_t)$ 来求解 MDP。强化学习为不确定环境下的决策提供了一个强大的框架，其中代理人旨在随时间最大化累积奖励。核心概念——代理人、状态、动作、奖励——在马尔可夫决策过程的结构中被形式化为数学，从而能够应用动态规划、Q 学习和策略梯度方法等优化技术来解决复杂的决策问题。

## 10.2 深度 Q 学习

文献综述：Alonso 和 Arias (2025) [357] 严谨地探讨了 Q 学习的数学基础及其收敛特性。作者分析了粘度解和汉密尔顿-雅可比-贝尔曼 (HJB) 方程，展示了 Q 学习近似如何与这些原理相一致。该工作为不同函数近似设置下的 Q 学习提供了新的理论保证。Lu 等人 (2024) [358] 提出了一种分解经验贝尔曼算子，以减轻深度 Q 学习中的维度灾难。作者提供了严格的理论分析，说明分解如何在保持最优性的同时降低复杂度。该研究提高了深度强化学习模型的可扩展性。Humayoo (2024) [359] 使用时间尺度分离技术将时序差分 (TD) 学习扩展到深度 Q 学习。它引入了一种 Q(\(\Delta\))-学习方法，可在复杂环境中提高稳定性和收敛速度。实证结果验证了其在 Atari 基准测试中的性能。Jia 等人 (2024) [360] 将深度 Q 学习 (DQL) 与博弈论相结合，用于无线网络中的抗干扰策略。它提供了严格的理论框架，说明多代理 Q 学习如何提高对抗攻击的韧性。该研究引入了多臂老虎机算法及其收敛特性。Chai 等人 (2025) [361] 对非静态马尔可夫决策过程 (MDP) 中的迁移学习进行了数学分析。它将深度 Q 学习扩展到环境随时间变化的场景，为这些领域中的 Q 学习建立了误差界。Yao 和 Gong (2024) [362] 为拜占庭攻击下的多代理系统 (MASs) 开发了一种具有韧性的深度 Q 网络 (DQN) 模型。该工作引入了一种新颖的分布式 Q 学习方法，对对抗扰动具有可证明的鲁棒性。Liu 等人 (2025) [363] 引入了 SGD-TripleQNet，这是一个集成三个深度 Q 网络的多 Q 学习框架。作者为其模型提供了数学基础和收敛证明。该论文将强化学习与随机梯度下降 (SGD) 优化相连接。Masood 等人 (2025) [364] 将深度 Q 学习与博弈论 (GT) 相结合，以优化智慧农业中的能源效率。它提出了一种动态能源分配的数学模型，证明了基于 Q 学习的决策环境中存在纳什均衡。Patrick (2024) [365] 将经济建模与深度 Q 学习相连接。它使用深度强化学习 (DRL) 制定动态定价策略，并提供了数学证明，说明 RL 如何适应经济冲击。Mimouni 和 Avrachenkov (2025) [366] 引入了一种新颖的深度 Q 学习算法，该算法结合了最优停止问题中的关键概念 Whittle 指数。它证明了收敛界，并将模型应用于电子邮件推荐系统，展示了优于传统 Q 学习方法的性能。

深度 Q 学习 (DQL) 是一种高级强化学习 (RL) 技术，其目标是通过使用深度神经网络来近似最优动作值函数 \(Q^*(s, a)\)。在传统 Q 学习中，动作值函数 \(Q(s, a)\) 将状态-动作对映射到从该状态-动作对出发、在遵循最优策略假设下的期望回报或累积折扣奖励。形式上，Q 函数定义为：

$$
Q(s, a) = \mathbb{E} \left[ \sum_{t=0}^{\infty} \gamma^t r_t \mid s_0 = s, a_0 = a \right] \tag{541}
$$

其中 \(\gamma \in [0, 1]\) 是折扣因子，它决定了未来奖励相对于即时奖励的权重，\(r_t\) 是在时间步 \(t\) 收到的奖励。最优 Q 函数 \(Q^*(s, a)\) 满足贝尔曼最优方程：

$$
Q^*(s, a) = \mathbb{E} \left[ r_t + \gamma \max_{a'} Q^*(s_{t+1}, a') \mid s_0 = s, a_0 = a \right] \tag{542}
$$

其中 \(s_{t+1}\) 是在状态 \(s\) 下采取动作 \(a\) 后的下一个状态，最大化项代表最优的未来期望奖励。该方程代表了最优动作值函数的递归结构，其中每个 Q 值基于当前步骤获得的奖励和从下一个状态期望的最大未来奖励进行更新。目标是通过迭代更新来学习最优 Q 函数，通常使用时序差分 (TD) 方法。在深度 Q 学习中，Q 函数由深度神经网络近似，因为直接存储每个状态-动作对的 Q 值对于大状态和动作空间在计算上是不可行的。设近似 Q 函数为 \(Q_\theta(s, a)\)，其中 \(\theta\) 表示近似动作值函数的神经网络参数（权重和偏置）。深度 Q 网络 (DQN) 旨在学习 \(Q_\theta(s, a)\)，使其随时间密切逼近 \(Q^*(s, a)\)。Q 函数的更新遵循 TD 误差原理，其目标是最小化当前 Q 值与从贝尔曼方程导出的目标 Q 值之间的差异。训练 DQN 的损失函数由以下给出：

$$
L(\theta) = \mathbb{E}_{(s_t, a_t, r_t, s_{t+1}) \sim \mathcal{D}} \left[ (y_t - Q_\theta(s_t, a_t))^2 \right] \tag{543}
$$

其中 \(\mathcal{D}\) 表示包含之前转换 \((s_t, a_t, r_t, s_{t+1})\) 的经验重放缓冲区。Q 值的目标 \(y_t\) 定义为：

$$
y_t = r_t + \gamma \max_{a'} Q_{\theta^-}(s_{t+1}, a') \tag{544}
$$

这里，\(\theta^-\) 表示目标网络的参数，它是在线网络参数 \(\theta\) 的缓慢更新副本。目标网络 \(Q_{\theta^-}\) 用于为 Q 值更新生成稳定的目标，其参数会定期通过在每 \(T\) 步后从在线网络 \(\theta\) 复制参数来更新。其背后的想法是通过防止由于 Q 网络预测的反馈循环导致 Q 值快速变化来稳定训练。网络参数 \(\theta\) 的更新规则遵循梯度下降方法，并表示为：

$$
\nabla_\theta L(\theta) = \mathbb{E}_{(s_t, a_t, r_t, s_{t+1}) \sim \mathcal{D}} \left[ (y_t - Q_\theta(s_t, a_t)) \nabla_\theta Q_\theta(s_t, a_t) \right] \tag{545}





其中 \nabla_\theta Q_\theta(s_t, a_t) 是 Q-函数相对于参数 \theta 的梯度，通过神经网络的反向传播计算得出。该梯度用于更新 Q 网络的参数，以最小化损失函数。在强化学习中，智能体必须在探索（尝试新动作）和利用（选择能最大化奖励的动作）之间取得平衡。这通常通过使用 epsilon-贪婪策略来处理，其中智能体以概率 \epsilon 选择随机动作，以概率 1 - \epsilon 选择 Q 值最高的动作。epsilon 值会随时间衰减，以确保随着智能体的学习，从探索转向更多的利用。epsilon-贪婪动作选择规则如下：

a_t = \begin{cases} \text{random action}, & \text{with probability } \epsilon \\ \arg \max_a Q_\theta(s_t, a), & \text{with probability } 1 - \epsilon \end{cases} (546)

该政策鼓励智能体在训练初期探索不同的动作，并随着训练逐渐利用学习到的 Q 值。\epsilon 的衰减通常遵循退火时间表，以有效平衡探索和利用。在 Deep Q-Learning 中稳定训练的一个关键组件是使用经验回放。在标准 Q 学习中，更新基于连续的状态转移，这可能导致连续数据点之间存在高度相关性。这种相关性会减慢学习速度，甚至导致不稳定。经验回放通过存储过去经验的缓冲区，并在训练期间从该缓冲区中采样随机小批量来解决此问题。这打破了连续样本之间的相关性，并产生更稳定、更高效的更新。在数学上，训练网络的损失函数涉及从经验回放缓冲区 \mathcal{D} 中随机采样状态转移 (s_t, a_t, r_t, s_{t+1})，Q 值的更新是根据采样经验使用 Bellman 误差计算的：

L(\theta) = \mathbb{E}_{(s_t, a_t, r_t, s_{t+1}) \sim \mathcal{D}} \left[ \left( r_t + \gamma \max_{a'} Q_{\theta^-}(s_{t+1}, a') - Q_\theta(s_t, a_t) \right)^2 \right] (547)

这种方法确保 Q 值的更新方式对经验被观察的顺序不那么敏感，从而促进更稳定的学习动态。

尽管取得了成功，DQL 算法仍可能受到某些问题的困扰，例如由于 Bellman 方程中的最大化步骤而导致的过估计偏差和不稳定性。过估计偏差之所以发生，是因为最大化操作 \max_{a'} Q_{\theta^-}(s_{t+1}, a') 倾向于高估真实值，因为 Q 值是基于同一 Q 网络更新的。为解决这一问题，引入了 Double Q-learning，它使用两个独立的 Q 网络分别用于动作选择和值估计，从而减少过估计偏差。在 Double Q-learning 中，目标 Q 值使用以下方程计算：

y_t = r_t + \gamma Q_{\theta^-} \left( s_{t+1}, \arg \max_{a'} Q_\theta(s_{t+1}, a') \right) (548)

这种方法通过将动作选择与 Q 值估计过程解耦，有助于缓解过估计问题。\arg \max 的值来自在线网络 Q_\theta，而下一状态的 Q 值则使用目标网络 Q_{\theta^-} 进行估计。改进 DQL 框架的另一个扩展是 Dueling Q-Learning，它将 Q-函数分解为两个独立的组件：状态值函数 V_\theta(s) 和优势函数 A_\theta(s, a)。Q-函数随后表示为：

Q_\theta(s, a) = V_\theta(s) + A_\theta(s, a) (549)

这种分解使智能体能够独立于特定动作来学习状态的值 V_\theta(s)，从而减少学习所需的参数数量。在许多动作具有相似预期奖励的环境中，这尤其有益，因为它使智能体能够专注于识别状态的值，而不是过度拟合于单个动作。

总之，Deep Q-Learning 是一种先进的强化学习方法，利用深度神经网络来逼近最优 Q-函数，使智能体能够处理大型状态和动作空间。DQL 的数学公式涉及基于时序差分误差最小化损失函数，利用经验回放稳定学习，并使用目标网络防止不稳定。Double Q-learning 和 Dueling Q-learning 等扩展进一步提高了算法的性能和稳定性。尽管取得了显著的成功，Deep Q-Learning 仍面临过估计偏差和不稳定性等挑战，这些挑战已通过对原始算法的创新修改得到解决。

## 10.3 游戏与机器人中的应用

文献综述：Khlifi (2025) [368] 将双重深度 Q 网络（DDQN）应用于自动驾驶。该文讨论了将强化学习技术从游戏转移到自动驾驶汽车，展示了深度强化学习如何处理动态环境中的复杂决策。引入了一种新颖的奖励函数以提高路径效率和安全性。Kuczkowski (2024) [369] 将多目标强化学习（MORL）扩展到交通和机器人系统，并为智慧城市应用中的机器人引入了节能强化学习。他还评估了基于强化学习的交通控制系统如何优化旅行时间并降低能耗。Krauss 等人 (2025) [370] 探讨了用于训练基于强化学习的神经网络的进化算法。该方法将基于突变的进化与强化学习相结合，优化了机器人控制和游戏 AI 的强化学习策略。该方法在多智能体机器人环境中显示出学习速度和适应性的改进。Ahamed 等人 (2025) [371] 为机器人足球开发了强化学习策略，实现了自适应球踢机制，并使用游戏引擎训练机器人，弥合了模拟学习与现实世界机器人之间的差距。他们还提出了模块化机器人阵型，展示了强化学习如何优化团队比赛。Elmquist 等人 (2024) [372] 专注于机器人强化学习中的模拟到现实迁移，并开发了一个可以适应现实世界不完美之处（例如，照明、纹理变化）的强化学习模型。他们使用深度学习和基于图像的指标来衡量模拟与现实世界训练环境之间的差异。Kobanda 等人 (2024) [373] 为机器人控制和游戏 AI 引入了一种离线强化学习（ORL）的分层方法。该研究提出了允许强化学习模型在不同任务之间转移知识的策略子空间，并证明了其在自适应视频游戏 AI 的目标条件强化学习中的有效性。Shefin 等人 (2024) [367] 专注于游戏和机器人操纵中安全关键的强化学习应用。他们引入了一个可解释强化学习（XRL）框架，使 AI 决策更具可解释性，并将其应用于机器人抓取任务，确保安全可靠的交互。Xu 等人 (2025) [374] 开发了 UPEGSim，一个基于 Gazebo 的水下机器人游戏仿真框架。他们使用强化学习优化水下无人机战斗中的规避策略，并强调了强化学习在军事和搜救机器人中的应用。Patadiya 等人 (2024) [375] 使用深度强化学习在赛车游戏（Forza Horizon 5）中创建自动驾驶玩家。他们将 AlexNet 与 DRL 结合，用于游戏中的基于视觉的自动驾驶智能体。该模型通过自我对弈学习最佳驾驶策略。Janjua 等人 (2024) [376] 探讨了机器人和开放世界游戏中强化学习的可扩展性挑战。他们研究了强化学习在动态、开放式环境（例如，过程生成的游戏世界）中的适应性，并讨论了强化学习智能体的泛化技术，提高了其在不可预测场景中的性能。

强化学习（RL）是机器学习的一个子领域，其中智能体通过与环境交互来学习做出决策。智能体的目标是通过采取影响其环境的行动，随时间最大化累积奖励信号。RL 框架正式由 *马尔可夫决策过程 (MDP)* 表示，它由一个 5 元组 $(\mathcal{S}, \mathcal{A}, P, r, \gamma)$ 定义，其中：

- $\mathcal{S}$ 是状态空间，表示智能体可能处于的所有可能状态。





- $\mathcal{A}$ 是动作空间，表示智能体可以采取的所有可能动作。
- $P(s'|s,a)$ 是状态转移概率，定义了在动作 $a$ 下从状态 $s$ 转移到状态 $s'$ 的概率。
- $r(s,a)$ 是奖励函数，定义了在状态 $s$ 下采取动作 $a$ 后获得的即时奖励。
- \(\gamma \in [0, 1)\) 是折扣因子，决定未来奖励的重要性。

RL 的目标是让智能体学习一个策略 \(\pi : \mathcal{S} \rightarrow \mathcal{A}\)，以最大化其预期 _回报_（累积折扣奖励），其数学表达式为：

\(J(\pi) = \mathbb{E}_\pi \left[ \sum_{t=0}^\infty \gamma^t r(s_t, a_t) \right] ,\) (550)

其中，$s_t$ 表示时刻 $t$ 的状态，$a_t = \pi(s_t)$ 是根据策略 $\pi$ 采取的动作。期望是在策略 $\pi$ 下，关于智能体与环境交互所取的。智能体通过选择能随时间获得最多奖励的动作，来最大化这一预期回报。最优 _值函数_ $V^*(s)$ 定义为从状态 $s$ 开始所能获得的最大预期回报，并由 _贝尔曼最优方程_ 规定：

\(V^*(s) = \max_a \mathbb{E} \left[ r(s, a) + \gamma V^*(s') \right] ,\) (551)

其中，$s'$ 是下一状态，期望是关于转移动力学 $P(s'|s,a)$ 取的。_动作值函数_ $Q^*(s,a)$ 表示在状态 $s$ 下采取动作 $a$，随后遵循最优策略所能获得的最大预期回报。它满足 $Q^*(s,a)$ 的贝尔曼最优方程：

\(Q^*(s,a) = \mathbb{E} \left[ r(s,a) + \gamma \max_{a'} Q^*(s',a') \right] ,\) (552)

其中，$a'$ 是下一步要采取的动作，期望再次关于状态转移概率取。这些贝尔曼方程是许多 RL 算法的基础，这些算法通过迭代逼近值函数来学习最优策略。为了求解这些方程，最广泛使用的方法之一是 _Q-learning_，这是一种非策略、无模型的 RL 算法。Q-learning 根据以下规则迭代更新动作值函数 $Q(s,a)$：

\(Q(s_t, a_t) \leftarrow Q(s_t, a_t) + \alpha \left[ r(s_t, a_t) + \gamma \max_{a'} Q(s_{t+1}, a') - Q(s_t, a_t) \right] ,\) (553)

其中，\(\alpha\) 是控制更新步长的学习率，\(\gamma\) 是折扣因子。Q-learning 的核心思想是，智能体无需环境模型即可学习最优动作值函数 \(Q^*(s, a)\)。智能体通过与环境交互并获得反馈（奖励），不断改进其动作值估计。该更新的迭代特性确保在所有状态-动作对被无限次访问且 \(\alpha\) 适当衰减的条件下，收敛到最优 \(Q^*\)。相比之下，_策略梯度_ 方法直接优化由向量 \(\theta\) 参数化的策略 \(\pi_\theta$。这些方法在高维或连续动作空间中非常有用，因为动作值方法在这些空间中可能效果不佳。策略梯度方法的目标是最大化预期回报 \(J(\pi_\theta)$，其表达式为：

\(J(\pi_\theta) = \mathbb{E}_{s_t,a_t\sim\pi_\theta} \left[ \sum_{t=0}^\infty \gamma^t r(s_t, a_t) \right] .\) (554)

策略使用 _梯度上升_ 方法进行更新，预期回报关于 \(\theta$ 的梯度计算如下：

\(\nabla_\theta J(\pi_\theta) = \mathbb{E}_{s_t,a_t\sim\pi_\theta} \left[ \nabla_\theta \log \pi_\theta(a_t|s_t)Q(s_t, a_t) \right] ,\) (555)

其中，$Q(s_t, a_t)$ 是动作值函数，\(\nabla_\theta \log \pi_\theta(a_t|s_t)$ 是得分函数，表示策略似然对策略参数的敏感性。沿着此梯度，策略参数 \(\theta$ 将被更新以提高智能体的性能。这种方法称为 REINFORCE，当动作空间很大或为连续空间，且策略需要使用复杂模型（如深度神经网络）进行参数化时，它特别有效。在 Q-learning 和策略梯度方法中，探索与利用都是关键概念。探索是指尝试尚未充分测试的新动作，而利用是指选择已知能获得高奖励的动作。ε-贪婪策略是平衡探索与利用的常见方法，即以概率 \(\epsilon$ 智能体选择随机动作，以概率 \(1 - \epsilon$ 选择预期奖励最高的动作。随着智能体的学习，\(\epsilon$ 通常会随时间衰减，以减少探索并更多地利用已学习的策略。在更复杂的环境中，会使用玻尔兹曼探索或熵正则化技术，在策略中保持可控的随机性以鼓励探索。在多智能体游戏中，RL 变得更加复杂。当多个智能体交互时，环境不再是静态的，因为每个智能体的动作都会影响其他智能体。在这种情况下，可以通过博弈论使用 RL 来寻找最优策略。这里的一个基本概念是纳什均衡，即在假设所有其他智能体的策略保持不变的情况下，没有智能体能够通过改变其策略来提高其回报。在数学上，对于两个智能体 \(i$ 和 \(j$，纳什均衡 \((\pi_i^*, \pi_j^*)$ 满足：

- \(r_i(\pi_i^*, \pi_j^*) \ge r_i(\pi_i, \pi_j^*) \quad \text{and} \quad r_j(\pi_i^*, \pi_j^*) \ge r_j(\pi_i^*, \pi_j), \quad (556)\)

其中，$r_i(\pi_i, \pi_j)$ 是智能体 $i$ 在对抗智能体 $j$ 的策略 \(\pi_j$ 时采用策略 \(\pi_i$ 的回报函数。在多智能体 RL 中寻找纳什均衡是一项复杂且计算挑战巨大的任务，它要求智能体在非平稳环境中学习，因为其他智能体的策略也会随时间变化。在机器人领域，RL 用于解决高维控制任务，例如运动规划和轨迹优化。机器人的状态空间通常由其位置、速度及其他物理参数的向量表示，而动作空间则包含控制输入，例如关节转矩或线速度。在这种情况下，RL 算法学习将状态映射为动作，以针对特定任务优化机器人的性能，例如尽量减少能耗或在最短时间内完成任务。机器人的动力学通常由微分方程建模：

- \(\dot{x}(t) = f(x(t), u(t)), \quad (557)\)

其中，$x(t)$ 是时刻 $t$ 的状态向量，$u(t)$ 是控制输入。通过 RL，机器人学习优化控制策略 $u(t)$ 以最大化奖励函数，该函数通常涉及任务成功与效率的组合。具体来说，深度 RL 允许使用神经网络表示高度复杂的控制策略，使机器人能够处理需要高维感官输入和决策的任务，例如物体操作或自主导航。

在游戏领域，RL 通过使智能体能够在手工制作的特征或简单的表格表示不足的环境中学习复杂策略，彻底改变了该领域。在深度强化学习（DRL）中，一个关键挑战是稳定训练过程，因为神经网络容易出现过拟合、梯度爆炸和梯度消失等问题。会使用经验回放和目标网络等技术来缓解这些挑战，确保稳定且高效的学习。因此，强化学习以其在马尔可夫决策过程、贝尔曼方程和策略优化方法方面的理论基础，为解决序列决策问题提供了一种数学丰富且极其严谨的方法。其在游戏和机器人等领域的应用不仅展示了其多功能性，还将机器学习的边界推向了现实世界、高复杂度的场景。





# 11 自然语言处理（NLP）

文献综述：Jurafsky 和 Martin (2023) [225] 撰写了一本 NLP 理论的基石著作，涵盖语法、语义和话语分析等基本概念，同时介绍了面向 NLP 的深度学习方法。该书将语言学理论与概率和神经方法相结合，是学生和研究人员不可或缺的资源。它详细解释了序列标注、解析、Transformer 和 BERT 模型。Manning 和 Schütze (1999) [226] 撰写了一本 NLP 的基础性文本，特别是针对概率模型。它涵盖了隐马尔可夫模型（HMM）、n-gram 语言模型和期望最大化（EM）等概念，这些概念至今仍是现代基于 Transformer 的 NLP 模型的基础。它还介绍了隐语义分析（LSA），这是现代词嵌入的前身。Liu 和 Zhang (2018) [227] 对基于深度学习的 NLP 进行了详细探讨，包括词嵌入、循环神经网络（RNN）、LSTM、GRU 和 Transformer。它介绍了神经网络的数学基础，成为经典 NLP 与深度学习之间的桥梁。Allen (1994) [228] 撰写了一本 NLP 的开创性著作，专注于符号化和基于规则的方法。它详细涵盖了语义解析、话语建模和知识表示。尽管它早于深度学习出现，但它为逻辑和语言学方法在 NLP 中的应用奠定了坚实的理论基础。Koehn (2009) [231] 撰写了一部关于统计 NLP 的权威著作，特别是基于短语的翻译、对齐模型和解码算法等机器翻译技术。即使在基于神经的翻译模型（例如基于 Transformer 的系统）占据主导地位的今天，它依然具有重要意义。现在我们介绍一些自然语言处理（NLP）领域的近期著作。Hempelmann [230] 探讨了如何将语言学幽默理论融入大型语言模型（LLM）。它讨论了将形式幽默理论整合到神经模型中，以及是否可以使用 LLM 来测试语言学假设。Eisenstein (2020) [232] 撰写了一本连接理论与实践的现代 NLP 教材。它涵盖了概率方法和深度学习方法，包括依赖句法分析、序列到序列模型和注意力机制。与许多教材不同，它还讨论了 NLP 模型中的伦理和偏见问题。Otter 等人 (2018) [233] 对 NLP 中的神经架构进行了全面综述，涵盖了 CNN、RNN、注意力机制以及 NLP 的强化学习。它既讨论理论含义也讨论实证进展，是语言任务中深度学习的重要参考文献。《计算语言学牛津手册》(2022) [234] 提供了一本涵盖 NLP 和计算语言学整个领域的论文集，包括形态学、句法、语义、话语处理和深度学习应用。它呈现了不同 NLP 领域中的理论辩论和实际应用。Li 等人 (2025) [229] 引入了一种先进的多头注意力机制，将探索性因子分析与 NLP 模型相结合。它增强了我们对 Transformer 如何编码句法和语义关系的理解。

## 11.1 文本分类

文献综述：Liu 等人 (2024) [235] 对文本分类技术进行了系统综述，涵盖传统机器学习方法（例如 SVM、朴素贝叶斯、决策树）和深度学习方法（CNN、RNN、LSTM 和 Transformer）。它还讨论了 TF-IDF、词嵌入和基于 BERT 的表示等特征提取技术。Çekik (2025) [236] 引入了一种基于粗糙集的文本分类方法，强调术语加权策略如何影响分类准确性。它探讨了特征降维和基于熵的选择方法，以增强文本分类器。Zhu 等人 (2025) [237] 提出了一种基于熵的前缀调优方法，用于层次化文本分类。它展示了熵正则化如何增强 BERT 和 GPT 等基于 Transformer 的分类器，用于多标签和层次化分类。Matrane 等人 (2024) [238] 调查了阿拉伯语 NLP 中方言文本分类面临的挑战。它提出了针对低资源方言的预处理优化，并展示了迁移学习如何提高分类准确性。Moqbel 和 Jain (2025) [239] 将文本分类应用于在线产品评论中的欺骗检测。它整合了认知评价理论和基于 NLP 的文本挖掘，以区分虚假评论和真实评论。Kumar 等人 (2025) [240] 专注于医学文本分类，展示了如何利用 NLP 技术从电子健康记录（EHR）和文本数据中提取的患者症状来诊断疾病。Yin (2024) [241] 对基于方面的情感分析（ABSA）进行了深入探讨，讨论了细粒度文本分类中的挑战。它引入了新的基于 BERT 的技术，以提高方面级情感分类的准确性。Raghavan (2024) [242] 使用文本数据研究人格分类。它评估了基于 NLP 的人格预测模型的性能，并比较了基于词典、深度学习和基于 Transformer 的方法。Semeraro 等人 (2025) [243] 引入了 EmoAtlas，这是一种融合心理词典、人工智能和网络科学的工具，用于对文本数据进行情感分类。它将其准确性与 BERT 和 ChatGPT 进行了比较。Cai 和 Liu (2024) [244] 为话语分析中的文本分类提供了一种实用方法。它探索了基于 Python 的技术，用于分析治疗谈话和会话文本中的情感分类。

文本分类是机器学习和自然语言处理（NLP）中的一个基本问题，其目标是根据文本内容为给定文本分配预定义的类别。该过程包括多个步骤，例如文本预处理、特征提取、模型训练和评估。在本回答中，我们将探讨这些步骤，重点关注文本分类中使用的底层数学原理和模型。文本分类的第一步是对原始文本数据进行预处理。这通常涉及以下操作：

- **分词**：将文本拆分为单词或标记。
- **停用词删除**：删除不承载重要意义的常见词（例如 "and"、"the" 等）。
- **词干提取与词形还原**：将单词还原为其基础形式或词根形式，例如 "running" 变为 "run"。
- **小写化**：将所有单词转换为小写以确保一致性。
- **标点删除**：删除标点符号。

这些操作会生成清洁且标准化的文本，以便进行特征提取。文本预处理完成后，下一步是将文本转换为可输入机器学习模型的数字表示。最常用的特征提取方法包括：

- 1. 词袋模型（Bag-of-Words, BoW）
- 2. 词频-逆文档频率（Term Frequency-Inverse Document Frequency, TF-IDF）

在第一种方法（**词袋（BoW）模型**）中，每个文档都表示为一个向量，其中每个维度对应语料库中的一个唯一单词。每个维度的值是该单词在文档中的频率。如果我们有一个包含 $N$ 个文档的语料库和一个包含 $M$ 个单词的词汇表，则文档 $i$ 可以表示为向量 $\mathbf{x}_i \in \mathbb{R}^M$，其中：

```
x_i = [f(w_1, d_i), f(w_2, d_i), ..., f(w_M, d_i)]  (558)
```

其中 f(w_j, d_i) 是单词 w_j 在文档 d_i 中的频率。词袋模型仅捕捉文档中术语的频率，而忽略它们的顺序。虽然该模型简单且计算效率高，但它并未捕捉文档中单词之间的句法或语义关系。

一种更复杂、更优化的表示可以通过 **术频-逆文档频率（TF-IDF）** 获得，它通过将单词的原始频率乘以其



在语料库中的相对重要性。TF-IDF 是一种更高级的技术，旨在根据词语的重要性对词语进行加权。它同时考虑了词语在文档中的频率以及该词语在所有文档中的稀有性。词语 $w$ 在文档 $d$ 中的术语频率（TF）定义为：

\(\text{TF}(w, d) = \frac{\text{count}(w, d)}{\text{total number of words in } d}\)

逆文档频率（IDF）由以下公式给出：

\(\text{IDF}(w) = \log \left( \frac{N}{\text{DF}(w)} \right)\)

其中 $N$ 是文档总数，$\text{DF}(w)$ 是包含词语 $w$ 的文档数量。TF-IDF 分数是这两者的乘积：

\(\text{TF-IDF}(w, d) = \text{TF}(w, d) \cdot \text{IDF}(w)\)

有几种可用于文本分类的机器学习模型，从简单模型到复杂模型不等。文本分类的一种常见方法是使用线性模型，如逻辑回归或线性支持向量机（SVM）。给定文档 $i$ 的特征向量 \(\mathbf{x}_i\)，类标签 $y_i$ 的预测可以如下进行：

\(\hat{y}_i = \sigma(\mathbf{w}^T \mathbf{x}_i + b)\)

其中 \(\sigma\) 是用于二分类的 Sigmoid 函数，\(\mathbf{w}\) 和 $b$ 分别是权重向量和偏置项。模型参数 \(\mathbf{w}\) 和 $b$ 是通过最小化损失函数（如二元交叉熵损失）来学习的。更复杂的模型，如 *神经网络（NN）*，涉及更深层的数学公式。在典型的前馈神经网络中，目标是学习一组参数，将输入向量 \(\mathbf{x}_i\) 映射到输出标签 $y_i$。网络由多层互连的神经元组成，每层都对输入应用非线性变换。给定输入向量 \(\mathbf{x}_i\)，网络的输出计算如下：

\(\mathbf{h}_i^{(l)} = \sigma(\mathbf{W}^{(l)}\mathbf{h}_i^{(l-1)} + \mathbf{b}^{(l)})\)

其中 \(\mathbf{h}_i^{(l)}\) 是第 $l$ 层的激活值，\(\sigma\) 是激活函数（例如 ReLU、Sigmoid 或 Tanh），\(\mathbf{W}^{(l)}\) 是权重矩阵，\(\mathbf{b}^{(l)}\) 是第 $l$ 层的偏置项。网络的输入在生成最终分类输出之前会经过多个隐藏层。输出层通常应用 *Softmax* 函数以获取可能类别上的概率分布：

\(P(y_c|\mathbf{x}_i) = \frac{\exp(\mathbf{W}_c^T \mathbf{h}_i + b_c)}{\sum_{c'} \exp(\mathbf{W}_{c'}^T \mathbf{h}_i + b_{c'})}\)

其中 \(\mathbf{W}_c\) 和 $b_c$ 是类 $c$ 的权重和偏置，\(\mathbf{h}_i$ 是最后一个隐藏层的输出。网络通过最小化 *交叉熵损失函数* 进行训练：

\(\mathcal{L}(\mathbf{W}, \mathbf{b}) = - \sum_{c=1}^C y_{i,c} \log P(y_c|\mathbf{x}_i)\)

其中 $y_{i,c}$ 是类 $c$ 的独热编码标签，目标是最小化预测概率分布与真实类分布之间的差异。在整个过程中，*优化* 在微调模型参数以最小化分类错误方面起着关键作用。常见的优化技术包括 *随机梯度下降（SGD）* 及其变体，如 *Adam* 和 *RMSProp*，它们根据损失函数对参数的梯度迭代更新模型参数。给定由 \(\theta\) 参数化的损失函数 \(\mathcal{L}(\theta)\)，损失对参数 \(\theta_i\) 的梯度计算如下：

\(\frac{\partial \mathcal{L}(\theta)}{\partial \theta_i}\)

那么梯度下降的参数更新规则为：

$\theta_i \leftarrow \theta_i - \eta \frac{\partial \mathcal{L}(\theta)}{\partial \theta_i} \quad (567)$

其中 $\eta$ 是学习率。对于每次迭代，此更新规则沿负梯度方向调整模型参数，最终收敛到一组最小化分类错误的参数。

总而言之，文本分类是一个高级且多方面的问题，需要深入理解多种数学原理，包括线性代数、概率论、优化和函数分析。从文本预处理到特征提取、模型训练和评估的整个过程，都涉及严格的数学技术的应用，使文本能够被有效分类为有意义的类别。这些步骤中的每一个，无论简单还是复杂，都在利用数学精巧的模型和算法将原始文本数据转化为可操作的洞察方面发挥着不可或缺的作用。

## 11.2 机器翻译

文献综述：Wu 等人（2020）[245] 介绍了端到端神经机器翻译（NMT），重点研究序列到序列模型、注意力机制和 Transformer 架构。它解释了编码器-解码器框架、自注意力和位置编码，为现代 NMT 奠定了基础。Hettiarachchi 等人（2024）[246] 提出了使用 Transformers 进行阿姆哈拉语到英语的机器翻译。它介绍了字符嵌入和正则化技术，用于处理低资源语言，这是多语言 NLP 中的一项关键挑战。Das 和 Sahoo（2024）[247] 讨论了词对齐模型，这是 SMT 中的一个基本概念。它解释了 IBM Model 1-5、HMM 对齐以及对齐在短语模型中的作用。它还探讨了处理跨语言句法差异的挑战。Oluwatoki 等人（2024）[248] 提出了基于 Transformer 的约鲁巴语到英语的 MT 系统之一。它强调了多语言 NLP 模型在资源匮乏语言方面的困难，并提出了基于 Rouge 的 MT 系统评估方法。Uçkan 和 Kurt [249] 讨论了词嵌入（Word2Vec、GloVe、FastText）在 MT 中的作用。它涵盖了向量空间中的语义表示，这对于 NMT 中的上下文感知翻译至关重要。讨论了 MT 中的多词表达（MWEs），这是 NLP 中的一项主要挑战。它涵盖了惯用表达、搭配和动词短语，展示了神经模型在多词消歧方面的困难。Pastor 等人（2024）[250] 讨论了 MT 中的多词表达（MWEs），这是 NLP 中的一项主要挑战。它涵盖了惯用表达、搭配和动词短语，展示了神经模型在多词消歧方面的困难。Fernandes（2024）[251] 比较了开源大型语言模型（LLM）和 NMT 系统在翻译 EN-PT-BR（英语-葡萄牙语-巴西葡萄牙语）字幕中的空间语义。它强调了传统 MT 和神经 MT 在捕捉上下文空间含义方面的局限性。Jozić（2024）[252] 将 ChatGPT 的翻译能力与专门的 MT 系统（如 eTranslation（欧盟委员会 MT 模型））进行了评估。它表明通用 LLM 可以与专用 NMT 系统相媲美，但在领域特定翻译方面存在困难。Yang（2025）[253] 介绍了用于 NMT 输出的错误检测模型，使用基于 Transformer 的分类器来检测机器生成翻译中的句法和语义错误。

机器翻译（MT）在自然语言处理（NLP）中是一项高度复杂的计算任务，需要使用统计、基于规则和深度学习模型，通常由概率和神经网络框架支撑，将一种语言（源语言）的文本转换为另一种语言（目标语言）。目标是从给定的源序列 $S = \{s_1, s_2, \dots, s_T\}$ 中，通过建模条件概率 $P(T \mid S)$ 来确定最可能的目标序列 $T = \{t_1, t_2, \dots, t_N\}$。最优翻译通常定义为：

$$T^* = \arg \max_T P(T \mid S) \quad (568)$$

这涉及在给定 S 的情况下估计 T 的概率，假设翻译可以用概率描述。在最基本的统计机器翻译（SMT）形式中，此概率通常通过一系列翻译模型来建模，这些模型将翻译过程分解为可管理的组件。SMT 中的条件概率 P(T | S) 可以使用贝叶斯定理进行分解：

$$P(T | S) = \frac{P(S,T)}{P(S)} = \frac{P(T | S)P(S)}{P(S)} \quad \text{(569)}$$

鉴于这种分解，早期 SMT 模型（如 IBM 模型）的核心旨在对源语言和目标语言对上的联合概率 P(S, T) 进行建模。具体来说，在像 IBM Model 1 这样的基于词的模型中，任务归结为估计将源语言 S 中的每个词翻译为目标语言 T 中对应词的概率。联合概率可以写成：

$$P(S,T) = \prod_{i=1}^{T} \prod_{j=1}^{N} t(s_i | t_j) \quad \text{(570)}$$

其中 t(si | tj) 是将源句子中的词 si 翻译为目标句子中的词 tj 的概率。这些概率 t(si | tj) 的估计通常通过分析平行语料库，利用 Expectation-Maximization (EM) 等技术来实现，这使得可以从大量双语文本数据中无监督地学习这些翻译概率。EM 算法在计算源语言和目标语言中词的预期对齐之间进行迭代，并相应地优化模型参数。然而，基于词的翻译模型没有考虑语言的结构，这常常导致次优翻译，尤其是在句法结构差异显著的语言中。挑战源于无法通过简单的词对词映射捕捉的词序差异和惯用表达。为了克服这些局限性，IBM Model 2 引入了词对齐的概念，引入了一个额外的隐藏变量 A，表示源句和目标句中词之间的可能对齐。这可以表示为：

$$P(S,T,A) = \prod_{i=1}^{T} \prod_{j=1}^{N} t(s_i | t_j)a(s_i | t_j) \quad \text{(571)}$$

其中 a(si | tj) 表示源语言中词 si 与目标语言中词 tj 之间的对齐概率。通过优化这些对齐概率，SMT 系统通过更好地建模源句和目标句之间的关系来提高翻译质量。然而，估计 a(si | tj) 需要计算成本高昂的算法，可以使用 EM 等方法进行迭代优化。

序列到序列（Seq2Seq）模型引入了一种更复杂的方法，通过利用深度学习技术显著改进了翻译过程。Seq2Seq 的核心是编码器-解码器框架，其中编码器处理整个源句子并将其编码为上下文向量，解码器生成目标序列。在此方法中，翻译概率公式化为：

$$P(T | S) = P(t_1 | S) \prod_{i=2}^{N} P(t_i | t_{<i}, S) \quad \text{(572)}$$

其中 t<i 表示之前生成的目标词，捕捉了翻译的顺序性。Seq2Seq 模型的关键优势在于其能够一次性建模整个句子，与基于词的模型相比，为源序列和目标序列提供了更丰富、更灵活的表示。编码器通常使用循环神经网络（RNN）或更高级的变体实现，例如长短期记忆网络（LSTM）或门控循环单元



(GRU) 网络，将源序列 $S$ 编码为隐藏状态。时间步 $t$ 的隐藏状态是递归计算的，基于输入 $x_t$（时间步 $t$ 的源词表示）和前一时刻的隐藏状态 $h_{t-1}$：

$$h_t = f(h_{t-1}, x_t)$$ (573)

其中 $f$ 表示更新函数，通常被参数化为非线性函数，例如 sigmoid 或 tanh。该递归生成一系列隐藏状态 $\{h_1, h_2, \dots, h_T\}$，每个状态都编码了源句子的相关信息。在这个模型中，解码器通过条件化于前一个标记 $t_{<i}$ 和上下文向量 $c$ 来逐个标记生成目标序列，上下文向量 $c$ 通常是编码器的最后一个隐藏状态。生成下一个目标词的条件概率由以下给出：

$$P(t_i \mid t_{<i}, S) = \text{softmax}(W h_t)$$ (574)

其中 $W$ 是学习到的权重矩阵，$h_t$ 是时间步 $t$ 的解码器隐藏状态。softmax 函数将网络输出转换为词汇表上的概率分布，概率最高的词被选为下一个目标词。

通过注意力机制，对 Seq2Seq 引入了一项重大改进。这使解码器在翻译过程中能够动态关注源句子的不同部分，而不仅仅依赖于一个固定长度的上下文向量。注意力机制为每个源词计算一组注意力权重 $\alpha_{t,i}$，这些权重用于计算编码器隐藏状态的加权和，以形成动态上下文向量 $c_t$。解码器中时间步 $t$ 和源词 $i$ 的注意力权重 $\alpha_{t,i}$ 计算如下：

$$
\alpha_{t,i} = \frac{\exp(e_{t,i})}{\sum_{k=1}^T \exp(e_{t,k})}
$$ (575)

其中 $e_{t,i} = \text{score}(h_t, h_i)$ 是一个学习到的评分函数，可以建模为：

$$e_{t,i} = \vec{v}^T \tanh(W_1 h_t + W_2 h_i)$$ (576)

这种注意力机制使模型在生成目标句子中每个词时能够自适应地关注源句子的相关部分，从而克服了长句中固定长度上下文向量的局限性。训练机器翻译模型通常涉及优化一个损失函数，以量化预测目标序列与真实目标序列之间的差异。最常见的损失函数是负对数似然：

$$L(\theta) = - \sum_{i=1}^N \log P(t_i \mid t_{<i}, S; \theta)$$ (577)

其中 $\theta$ 表示模型的参数。神经网络的参数使用基于梯度的优化技术进行更新，例如随机梯度下降（SGD）或 Adam，每个参数的损失函数梯度通过反向传播计算。在反向传播中，梯度是通过递归地将链式法则应用于网络各层来计算的。对于参数 $\theta$，梯度由以下给出：

$$
\frac{\partial L(\theta)}{\partial \theta} = \frac{\partial L(\theta)}{\partial y} \frac{\partial y}{\partial \theta}
$$ (578)

其中 $y$ 表示网络的输出，$\frac{\partial L(\theta)}{\partial y}$ 是损失相对于输出的梯度。这些梯度随后通过网络向后传播以更新参数，从而最小化损失函数。翻译质量通常使用自动评估指标（如 BLEU，即双语评估替代）来评价，它衡量机器生成翻译与人工参考译文之间的 n-gram 重叠度。长度为 n 的 n-gram 的 BLEU 分数计算如下：

BLEU(T, R) = exp \(\left( \sum_{n=1}^N w_n \log p_n(T, R) \right)\) (579)

其中 \(p_n(T, R)\) 是目标翻译 \(T\) 与参考译文 \(R\) 之间 n-gram 的精确率，\(w_n\) 是分配给每个 n-gram 长度的权重。尽管有所进步，机器翻译仍面临挑战，例如处理罕见或未登录词、习惯用语以及跨语言复杂句法结构的对齐。迁移学习、无监督学习和域自适应等方法正在被探索，以解决这些问题并提高机器翻译系统的鲁棒性和准确性。

## 11.3 聊天机器人与对话式人工智能

### 文献综述

Linnemann 和 Reimann (2024) [254] 探讨了对话式人工智能（尤其是聊天机器人）如何影响人类互动和社会心理学。它讨论了大型语言模型（LLMs）在对话系统中的作用及其应用，为聊天机器人融入人类沟通提供了理论视角。

Merkel 和 Schorr (2024) [255] 对不同类型的会话代理及其 NLP 能力进行了分类。它讨论了从基于规则的聊天机器人到基于 Transformer 的模型的演变，强调了自然语言处理如何增强了聊天机器人的可用性。

Kushwaha 和 Singh (2022) [256] 对聊天机器人架构进行了技术分析，涵盖意图识别、实体提取和对话管理。它将传统的基于 ML 的聊天机器人模型与深度学习方法进行了比较。

Macedo 等人 (2024) [257] 提出了一个面向医疗保健的聊天机器人，利用对话式人工智能协助帕金森病患者。它详细介绍了用于交互式医疗保健应用的语音转文本和 NLP 技术。

Gupta 等人 (2024) [258] 阐述了基于生成式人工智能的聊天机器人的理论基础，解释了类似 ChatGPT 的 LLM 如何影响对话式人工智能。它还介绍了一个评估聊天机器人效果的框架。

Foroughi 和 Iranmanesh (2025) [259] 考察了基于 AI 的聊天机器人如何影响电子商务中的消费者行为。它引入了一个理论框架来理解聊天机器人的采用和信任。

Jandhyala (2024) [260] 深入探讨了聊天机器人开发，涵盖 NLP 技术、意图识别和多轮对话管理。它还讨论了聊天机器人部署的最佳实践。

Pavlović 和 Savić (2024) [261] 探讨了对话式人工智能在数字营销中的应用，分析了基于 LLM 的聊天机器人如何改善客户体验。它还评估了聊天机器人交互中的情感分析和反馈循环。

Mannava 等人 (2024) [262] 考察了聊天机器人在儿童教育中的伦理和功能方面，重点关注 NLP 模型如何调整以适应适合儿童的交互。

Sherstinova 和 Mikhaylovskiy (2024) [263] 专注于聊天机器人 NLP 中的语言特定挑战，讨论了对话式人工智能模型在处理俄罗斯语等形态丰富的语言时所面临的困难。

聊天机器人和对话式人工智能已发展为自然语言处理（NLP）最为复杂的应用之一，NLP 是人工智能的一个子领域，致力于使机器能够理解、生成和交互于人类语言中。对话式人工智能的核心在于能够以连贯且流畅的方式生成有意义且符合语境的回复。这一挑战深深植根于自然语言本身的复杂性以及试图近似人类理解的数学模型之中。这项复杂的任务涉及在不同层次上处理语言：句法（结构）、语义（含义）和语用（语境）。这些系统采用概率和代数技术来处理语言复杂性，并使用统计模型、深度神经网络和优化算法来生成、理解和回应语言。

在数学上，对话式人工智能可以被视为从一组词语或符号（输入）到另一组（输出）的一系列变换。第一个数学方面是 *语言建模*，这对于预测词序的可能性至关重要。一系列词语 $w_1, w_2, ..., w_n$ 的概率分布通常使用概率链式法则计算：

$P(w_1, w_2, ..., w_n) = \prod_{i=1}^n P(w_i | w_1, w_2, ..., w_{i-1})$ (580)

其中 $P(w_i | w_1, w_2, ..., w_{i-1})$ 模拟了给定所有前缀词时词 $w_i$ 的条件概率。这是语言生成任务中的核心概念。在传统的 *n-gram 模型*中，这个条件概率是通过仅考虑固定数量的前缀词来估计的。例如，*二元模型*假设一个词的概率仅取决于前一个词，从而得出：

$P(w_i | w_1, w_2, ..., w_{i-1}) \approx P(w_i | w_{i-1})$ (581)

然而，更高级的对话式人工智能系统，例如基于 *循环神经网络（RNNs）* 的系统，试图对更长序列中的依赖关系进行建模。具体来说，RNNs 通过维护一个捕获到时间步 $t$ 为止上下文的隐藏状态 $h_t$ 来递归处理输入序列 $w_1, w_2, ..., w_n$。隐藏状态按以下方式计算：

$h_t = \sigma(W_h h_{t-1} + W_x x_t + b)$ (582)

其中 $\sigma$ 是非线性激活函数（例如，*tanh* 或 *sigmoid*），$W_h, W_x$ 是权重矩阵，$b$ 是偏置项。虽然 RNNs 提供了捕捉序列依赖性的机制，但它们存在 *梯度消失* 问题，尤其是在处理长序列时。为解决此问题，引入了 *长短期记忆网络（LSTM）* 单元和 *门控循环单元（GRUs）* ，带有特殊的门控机制，有助于减轻长时间跨度上的信息丢失。这些网络引入了记忆单元和门，用于调节网络中的信息流。例如，LSTM 记忆单元由以下方程控制：

$f_t = \sigma(W_f x_t + U_f h_{t-1} + b_f), \quad i_t = \sigma(W_i x_t + U_i h_{t-1} + b_i), \quad o_t = \sigma(W_o x_t + U_o h_{t-1} + b_o)$ (583)
$c_t = f_t \cdot c_{t-1} + i_t \cdot \tanh(W_c x_t + U_c h_{t-1} + b_c), \quad h_t = o_t \cdot \tanh(c_t)$ (584)

其中 $f_t, i_t, o_t$ 分别是遗忘门、输入门和输出门，$c_t$ 表示单元状态，它跨越时间步携带信息。因此，LSTM 通过更结构化地控制信息流，能够更好地捕捉长距离依赖关系。近年来，*变换器模型* 通过用并行化的自注意力机制取代 RNNs 的序列特性，彻底改变了对话式人工智能。Transformer 模型使用 *多头自注意力* 来衡量序列中每个词相对于所有其他词的重要性。自注意力机制基于查询 $Q$ 和键 $K$ 计算值 $V$ 的加权和，注意力计算如下：

$\text{Attention}(Q, K, V) = \text{softmax} \left( \frac{QK^T}{\sqrt{d_k}} \right) V$ (585)

其中 $d_k$ 是键向量的维度。这种操作使模型能够同时关注输入序列的所有部分，从而更好地处理长距离依赖关系，并通过并行处理序列来提高计算效率。与 RNNs 不同，Transformer 不按固定顺序处理标记，而是利用位置编码来注入序列顺序信息。位置 $i$ 和维度 $2k$ 的位置编码由以下给出：

$PE(i, 2k) = \sin \left( \frac{i}{10000^{2k/d}} \right), \quad PE(i, 2k+1) = \cos \left( \frac{i}{10000^{2k/d}} \right)$ (586)





其中 d 是嵌入维度，k 是位置编码维度的索引。这种方法使 Transformer 比 RNN 和 LSTM 更高效地处理更长的序列，并是 BERT、GPT 等其他最先进的对话模型的基础。对话式 AI 中的语义理解涉及将句子翻译成系统可操作的形式化表示。捕捉含义的一种知名方法是 *组合语义学*，它将句子的含义视为其各部分含义的函数。为此，常使用 *λ 演算* 来将句子含义表示为作用于其参数的函数。例如，句子 ”John saw the car” 可以表示为 lambda 表达式：

\lambda x.see(x, car)

其中 see(x, y) 是表示“看到”动作的谓词，而 \lambda x 对动作的主语进行量化。这使得能够从更简单的组件中构建复杂含义。对话管理是对话式 AI 系统的另一个关键方面。这是在对话过程中保持连贯性和上下文的过程。这包括在先前对话历史的背景下理解用户输入，并生成与上下文相关的回复。为对话状态建模，通常采用 *马尔可夫决策过程 (MDPs)*。在这种情况下，对话状态表示为一组可能的状态，动作是这些状态之间的转换。目标是选择（回复）动作以最大化累积奖励，在此例中，这对应于维持连贯且引人入胜的对话。状态 s 下的价值函数 V(s) 可使用 Bellman 方程计算：

V(s) = \max_a \left[ R(s, a) + \gamma \sum_{s'} P(s'|s, a)V(s') \right]

其中 R(s, a) 是从状态 s 采取动作 a 的即时奖励，\gamma 是折扣因子，而 P(s'|s, a) 表示在动作 a 下转移到下一状态 s' 的概率。通过求解该方程，系统可以确定最佳策略，以回应用户输入并最大化长期对话质量。一旦对话状态更新，对话式 AI 的下一步就是生成回复。这通常通过 *序列到序列模型* 实现，其中输入序列（例如用户查询）由编码器处理以生成固定大小的上下文向量，解码器生成输出序列（例如聊天机器人的回复）。这些模型的基本结构可表示为：

y_t = \text{Decoder}(y_{t-1}, h_t)

其中 y_t 表示时间 t 生成的标记，h_t 是来自编码器的隐藏状态。注意力机制被纳入此框架，使解码器在每个步骤都能关注输入序列的不同部分，从而提高生成回复的质量。训练对话模型需要通过 *反向传播* 和 *梯度下降* 来优化参数。通常将损失函数（即 *交叉熵损失*）最小化以更新模型参数：

\mathcal{L}(\theta) = - \sum_{i=1}^N y_i \log(\hat{y}_i)

其中 \hat{y}_i 是正确标记 y_i 的预测概率，N 是序列长度。参数 \theta 通过梯度下降迭代更新，调整权重以最小化误差。

总结来说，聊天机器人和对话式 AI 系统建立在涉及统计学、线性代数、优化和神经网络的丰富数学框架之上。从语言建模到对话管理的每一步都依赖于精心构建的数学基础，这些基础推动机器能够以智能且有意义的方式与人类进行交互。随着深度学习和优化技术的进步，对话式 AI 继续拓展机器在自然语言中理解和生成内容的边界，从而实现更复杂、更具人性化的交互。

# 12 深度学习框架

## 12.1 TensorFlow

文献综述：Takhsha et. al. (2025) [283] 引入了一个用于医疗深度学习应用的基于 TensorFlow 的框架。作者提出了一种新型深度学习诊断系统，将 Choquet 积分理论与基于 TensorFlow 的模型相结合，提高了医学影像中深度学习决策的可解释性。Singh and Raman (2025) [284] 将 TensorFlow 扩展到图神经网络 (GNNs)，讨论了 TensorFlow 的计算图结构如何与图理论相一致。这为将深度学习应用于非欧几里得数据结构提供了严谨的数学基础。Yao et. al. (2024) [285] 对 TensorFlow 易受对抗攻击的漏洞进行了批判性分析，并引入了一个稳健的深度学习集成框架。作者探讨了使用 TensorFlow 进行基于自编码器的异常检测，以增强网络安全防御。Chen et. al. (2024) [286] 对各种大数据应用的 TensorFlow 预训练模型进行了广泛比较。它讨论了迁移学习、微调和自监督学习等技术，强调了 TensorFlow 如何自动化超参数调优。Dumić (2024) [287] 撰写了一本严谨的教育资源，指导学习者使用 TensorFlow 构建神经网络。它弥合了深度学习理论与 TensorFlow 实际实现之间的差距，强调了梯度下降、反向传播和权重初始化。Bajaj et. al. (2024) [288] 使用 TensorFlow 实现了用于手写数字识别的 CNN，并对卷积操作、激活函数和优化技术进行了严谨的数学拆解。它强调了 TensorFlow 在大规模字符识别任务中的计算效率。Abbass and Fyath (2024) [289] 引入了一个用于光纤通信建模的基于 TensorFlow 的框架。它探讨了如何通过使用 TensorFlow 进行预测分析和信道均衡，利用深度学习优化光纤传输效率。Prabha et. al. (2024) [290] 严谨分析了 TensorFlow 在精准农业中的作用，重点关注用于作物监测的时间序列分析、计算机视觉和强化学习。它深入探讨了 TensorFlow 的 API 优化，用于处理传感器数据和遥感图像。Abdelmadjid and Abdeljalil (2024) [291] 研究了用于边缘计算的 TensorFlow Lite，在低功耗设备上严格测试了优化的 CNN 架构。它在资源受限环境中提供了计算效率、能耗和模型准确性的理论比较。Mlambo (2024) [292] 架起了贝叶斯推断与深度学习之间的桥梁，为在 TensorFlow 中实现的贝叶斯神经网络 (BNNs) 提供了严谨的推导。它探讨了 TensorFlow 如何将概率模型与深度学习框架相结合。

TensorFlow 主要基于 *张量* 进行操作，张量是标量、向量和矩阵的多维数组推广。例如，标量是 0 阶张量，向量是 1 阶张量，矩阵是 2 阶张量，而高阶张量代表多维数组。这些张量可以数学上表示为：

```
$$ \mathcal{T} \in \mathbb{R}^{d_1 \times d_2 \times ... \times d_n} $$ (591)
```

其中 $d_1, d_2, ..., d_n$ 表示张量的维度。TensorFlow 利用高效的 *张量操作*，以计算优化的方式操作大规模数据。这些操作是 TensorFlow 模型中所有变换和计算的基础。例如，两个向量 \(\vec{a}\) 和 \(\vec{b}\) 的点积是一个标量：

\(\vec{a} \cdot \vec{b} = \sum_{i=1}^n a_i b_i\) (592)

同样，对于矩阵，矩阵乘法 \(A \cdot B\) 等操作经过高度优化，利用 GPU 和 TPU 等设备上的批处理和并行性。TensorFlow 的底层库（如 Eigen）采用这些并行策略来优化内存使用并减少计算时间。TensorFlow 效率的核心在于其计算图，该图表示不同操作之间的关系。计算图是一个有向无环图 (DAG)，其中节点表示计算操作，边表示数据（张量）的流动。图中的每个操作都是一个函数 f，将一组输入映射到输出张量：

\(y = f(x_1, x_2, \dots, x_n)\) (593)

该图由用户或 TensorFlow 自动构建，其中节点表示加法、乘法或更复杂的变换等操作。一旦定义了计算图，TensorFlow 就通过重新排序计算、应用代数变换或并行化独立子图来优化该图。取决于用户的偏好，该图以动态方式（急切执行）或在优化之后（静态图执行）执行。自动微分是 TensorFlow 的另一项关键特性，它依赖于微分链式法则来计算梯度。标量值函数 f(x1, x2, ..., xn) 相对于输入张量 xi 的梯度计算如下：

\(\frac{\partial f}{\partial x_i} = \sum_{j=1}^n \frac{\partial f}{\partial y_j} \frac{\partial y_j}{\partial x_i}\) (594)

其中 yj 表示网络前向传播过程中计算的中间变量。在神经网络的上下文中，此链式法则在反向传播过程中用于将错误从输出层向后传播到输入层，其目标是更新网络权重以最小化损失函数 L。考虑一个具有简单架构的神经网络，包含输入层、一个隐藏层和一个输出层。令 X 表示输入张量，W1 和 b1 表示隐藏层的权重和偏置，W2 和 b2 表示输出层的权重和偏置。前向传播可写为：

\(h = \sigma(W_1 X + b_1)\) (595)
\(\hat{y} = W_2 h + b_2\) (596)

其中 \(\sigma\) 是激活函数，例如 ReLU 函数 \(\sigma(x) = \max(0, x)\)，而 \(\hat{y}\) 是预测输出。训练模型的目标是最小化损失函数 \(L(\hat{y}, y)\)，其中 y 表示真实标签。损失函数可以采用不同形式，例如回归任务的均方误差：

\(L(\hat{y}, y) = \frac{1}{N} \sum_{i=1}^N (y_i - \hat{y}_i)^2\) (597)

或分类任务的交叉熵损失：

\(L(\hat{y}, y) = - \sum_{i=1}^C y_i \log(\hat{y}_i)\) (598)

其中 C 是类别数，\(\hat{y}_i\) 是在 softmax 函数下类别 i 的预测概率。优化此损失函数需要计算 L 相对于模型参数 W1, b1, W2, b2 的梯度。这是通过反向传播实现的，它


通过网络层迭代应用链式法则。为了执行优化，TensorFlow 采用如 *梯度下降 (GD)* 之类的算法。参数 \(\theta\) 的基本梯度下降更新规则如下：

```
\(\theta_{t+1} = \theta_t - \eta \nabla_\theta L(\theta)\) (599)
```

其中 \(\eta\) 是学习率，\(\nabla_\theta L(\theta)\) 表示损失函数相对于模型参数 \(\theta\) 的梯度。梯度下降的变体，例如 *随机梯度下降 (SGD)*，使用训练数据的子集（小批量）而非整个数据集来更新参数：

```
\(\theta_{t+1} = \theta_t - \eta \nabla_\theta \frac{1}{m} \sum_{i=1}^m L(\theta, x_i, y_i)\) (600)
```

其中 \(m\) 是批量大小，\((x_i, y_i)\) 是小批量中的数据点。更复杂的优化器，如 *Adam*（自适应矩估计），同时使用动量（一阶矩）和缩放（二阶矩）来为每个参数自适应调整学习率。Adam 的更新规则如下：

```
\(m_t = \beta_1 m_{t-1} + (1 - \beta_1) \nabla_\theta L(\theta)\) (601)
\(v_t = \beta_2 v_{t-1} + (1 - \beta_2)(\nabla_\theta L(\theta))^2\) (602)
\(\hat{m}_t = \frac{m_t}{1 - \beta_1^t}, \quad \hat{v}_t = \frac{v_t}{1 - \beta_2^t}\) (603)
\(\theta_{t+1} = \theta_t - \eta \frac{\hat{m}_t}{\sqrt{\hat{v}_t} + \epsilon}\) (604)
```

其中 \(\beta_1\) 和 \(\beta_2\) 是指数衰减率，\(\epsilon\) 是一个用于防止除以零的小常数。同时引入一阶和二阶矩使 Adam 能够自适应地调整学习率，从而加快收敛。除了标准优化方法，TensorFlow 还支持 *分布式计算*，可在多个设备（如 GPU 和 TPU）上进行模型训练。在分布式环境中，模型参数被分割到不同的工作节点，每个节点处理一部分数据。各工作节点计算的梯度被平均，全局参数随后更新：

```
\(\theta_{t+1} = \theta_t - \eta \frac{1}{N} \sum_{i=1}^N \nabla_\theta L_i(\theta)\) (605)
```

其中 \(L_i(\theta)\) 是在第 \(i\) 个设备上计算的损失，\(N\) 是设备总数。TensorFlow 高效的并行性确保大规模数据处理任务能够以高计算吞吐量执行，从而加快大规模数据集上的模型训练。

TensorFlow 还支持在不同平台上进行 *模型部署*。*TensorFlow Lite* 通过将训练模型转换为优化后的更小格式，使移动设备上的模型推理成为可能。该过程涉及 *量化*，它降低了权重和激活值的精度，从而减少内存占用和计算时间。转换过程旨在平衡模型精度与性能，确保深度学习模型能够在智能手机和物联网设备等资源受限设备上高效运行。对于 *Web应用*，TensorFlow 提供了 *TensorFlow.js*，允许用户直接在浏览器中运行机器学习模型，利用客户端 GPU 或 CPU 的计算能力。这对于需要低延迟预测且无需将数据发送到服务器的实时交互尤其有用。此外，TensorFlow 提供了超出基本机器学习任务的生态系统。例如，*TensorFlow Extended (TFX)* 支持在生产环境中部署机器学习模型，自动化从模型训练到部署的步骤。*TensorFlow Probability* 支持概率建模与不确定性估计，这在强化学习和贝叶斯推断等领域至关重要。

## 12.2 PyTorch

文献综述：北京航空航天大学银河燕石团队 [293] 考察了在空间站中对宇航员面部进行实时识别时使用 PyTorch 作为深度学习框架的情况。该研究探讨了 PyTorch 模型中的贝叶斯编码理论及其在优化神经网络架构方面的重要性。该研究对 PyTorch 模型中的概率分布进行了理论探讨，展示了深度学习如何应用于受限计算环境。Tabel (2024) [294] 将 PyTorch 扩展到尖峰神经网络 (SNNs)，这是一种受生物启发的神经网络类型。该研究详细介绍了一种利用 PyTorch 计算图来学习尖峰时序的新理论方法。该论文连接了神经形态计算与 PyTorch 的自动微分，扩展了时序深度学习背后的理论。Naderi 等人 (2024) [295] 引入了一种混合物理基础深度学习框架，将离散元建模 (DEM) 与基于 PyTorch 的网络相集成。该研究展示了如何将物理模拟问题表述为 PyTorch 中的深度学习模型，为科学计算中的神经求解器提供了新的见解。Polaka (2024) [296] 评估了 PyTorch 中的强化学习 (RL) 理论，探讨了 RL 框架在安全人工智能应用中的数学严谨性。作者为在 PyTorch 中理解深度强化学习 (DeepRL) 提供了坚实的理论基础，强调了前沿 RL 理论是如何嵌入该框架中的。Erdogan 等人 (2024) [297] 探讨了在使用 PyTorch 构建的大规模推荐系统中降低随机通信开销的理论框架。该研究引入了一种优化的梯度同步方法，可增强用于分布式计算的基于 PyTorch 的深度学习模型。Liao 等人 (2024) [298] 扩展了在 PyTorch 中实现的迭代部分扩散模型 (IPDM) 框架，用于医学图像处理，并推进了 PyTorch 中深度生成模型的理论，特别是在基于扩散的学习技术方面。Sekhavat 等人 (2024) [299] 考察了 PyTorch 中深度学习与人工智能创造力之间的理论交叉点，引用了尼采式哲学概念。作者还探讨了 PyTorch 如何实现神经创造力，并为计算美学提供了严格的理论模型。Cai 等人 (2025) [300] 开发了一种基于 Shapley 值的神经网络可解释性新理论框架，在 PyTorch 中实现，并利用 PyTorch 的 autograd 系统分析特征重要性，增强了可解释人工智能 (XAI) 的数学严谨性。Na (2024) [301] 提出了一种使用 PyTorch 的新型集成学习理论，专门用于弱监督学习 (WSL)。该论文扩展了 PyTorch 中的贝叶斯学习模型以处理稀疏标记数据，解决了 WSL 中的关键缺口。Khajah (2024) [302] 使用 PyTorch 结合了项目反应理论 (IRT) 和贝叶斯知识追踪 (BKT) 来建模可推广的技能发现。该研究利用 PyTorch 的概率编程能力，为自适应学习系统提出了一种严谨的统计理论。

PyTorch 中的动态计算图构成了其高效、灵活执行机器学习任务（尤其是深度学习模型）的核心。要理解其底层的数学和计算原理，必须探索计算图如何运作、代表什么，以及在机器学习程序执行过程中如何变化。与 TensorFlow（Eager 执行模式之前）等框架中使用的静态计算图不同，PyTorch 在前向传播执行操作时动态构建计算图。这使 PyTorch 能够适应执行过程中可能变化的各种输入大小、模型结构和控制流。这种适应性对于使 PyTorch 能够处理循环神经网络 (RNNs)（处理长度不一的序列）或在计算步骤中包含条件语句的模型至关重要。

计算图本身可以在数学上表示为有向无环图 (DAG)，其中节点表示操作和中间结果，边表示节点之间的数据流。每个操作（例如加法、乘法或非线性激活）都应用于张量，这些操作的输出将用作后续（subse-


频繁操作。PyTorch动态计算图的核心特征是其 **运行时构建**。例如，当创建张量 **A** 时，它可能参与一系列操作，最终导致损失函数 **L** 的计算。随着每个操作的执行，PyTorch在表示输入张量 **A** 的节点与表示输出张量 **B** 的节点之间构建一条边。数学上，这些张量之间的转换可以表示为：

**B** = *f*(**A**; *θ*) (606)

其中 *f* 表示转换函数（可能是线性或非线性操作），*θ* 表示该转换中涉及的参数（例如，神经网络中的权重或偏置）。动态图的构建使 PyTorch 能够处理 **可变长度序列**，这在 **时间序列预测**、**自然语言处理（NLP）** 和语音识别等任务中很常见。序列的长度可以根据输入数据而变化，因此，计算所需的迭代次数或层数也会随之变化。例如，在 **循环神经网络（RNN）** 中，每个时间步 *t_ 的隐藏状态 **h**_t_ 是前一时刻隐藏状态 **h**_t−1_ 和当前时间步输入 **x**_t_ 的函数。这可以数学上描述为：

**h**_t_ = *f*(**W**_h_**h**_t−1_ + **W**_x_**x**_t_ + **b**) (607)

其中 *f_ 通常是非线性激活函数（例如双曲正切或 Sigmoid），**W**_h_、**W**_x_、**b** 分别表示权重矩阵和偏置向量。这个方程概括了 RNN 的递归特性，即每个输出依赖于前一输出和当前输入。在静态计算图中，每个序列的操作数需要预先定义，这会导致在处理不同长度的序列时效率低下。然而，在 PyTorch 中，计算图是为每个序列动态创建的，这允许高效处理不同长度的序列并避免冗余计算。

PyTorch高效的关键在于 **自动微分**，由其 **autograd 系统** 管理。当张量 **A** 具有属性 `requires_grad=True` 时，PyTorch 开始跟踪对其执行的所有操作。假设张量 **A** 参与一系列操作以计算标量损失 **L**。例如，如果损失是输出张量 **Y** 的函数，该张量通过多层计算得出，目标是求 **L** 关于 **A** 的梯度。这需要计算雅各比矩阵，它表示 **Y** 的每个分量关于 **A** 的每个分量的梯度。使用微分的链式法则，损失关于 **A** 的梯度由以下公式给出：

∂**L**/∂**A** = Σᵢ ∂**L**/∂**Y**_i_ · ∂**Y**_i_/∂**A** (608)

这是 **多元链式法则** 的应用，其中 ∂**L**/∂**Y**_i_ 表示损失关于输出张量第 *i_-th 分量的梯度，∂**Y**_i_/∂**A** 是从 **A** 到 **Y** 的转换的雅各比矩阵。这种计算通过 **反向传播** PyTorch 动态构建的计算图中的梯度来实现。图中的每个操作节点都有关联的梯度，当我们从损失回溯到输入参数时，该梯度会沿图反向传播。例如，如果 **Y** = **A** · **B**，则损失关于 **A** 的梯度为：

∂**L**/∂**A** = ∂**L**/∂**Y** · **B**_T_ (609)

同样，关于 **B** 的梯度为：

∂**L**/∂**B** = ∂**L**/∂**Y** · **A**_T_ (610)

这展示了梯度如何通过计算图向后传递，利用每个节点中存储的操作来计算所需的导数。动态构建图的优势在于，不需要像静态图方法那样预先构建整个图。相反，图会在操作执行时动态更新，从而既更节省内存又计算效率更高。PyTorch 动态图的一个重要特性是其在计算中处理条件语句的能力。考虑一种基于条件语句在计算中具有不同分支的情况。在静态图中，此类条件语句需要预先确定整个图，包括所有可能的分支。相比之下，PyTorch 根据输入数据构建图的相关部分，从而有效实现分支计算。例如，假设在神经网络模型中有一个决策过程，输出取决于输入张量是否超过阈值 x_i > t：

```
y_i = \begin{cases} \mathbf{A} \cdot \mathbf{x}_i + \mathbf{b} & \text{if } x_i > t \\ \mathbf{C} \cdot \mathbf{x}_i + \mathbf{d} & \text{otherwise} \end{cases} (611)
```

在静态图中，我们需要设计两个独立的分支，并可能处理未使用分支的计算成本。在 PyTorch 的动态图中，仅执行相关分支，并相应更新图以反映必要的操作。PyTorch 动态图构建的内存效率在处理大型模型和在大型数据集上训练时尤为明显。在构建深度神经网络（DNNs）等模型时，前向传播和反向传播期间对每个张量执行的操作都会记录在计算图中。这允许高效重用中间结果，并且仅在图构建期间为每个张量分配必要的内存。这与静态计算图形成对比，静态图需要预先定义完整图并分配内存，可能导致不必要的内存消耗。

总而言之，PyTorch 中的动态计算图是一种强大的工具，允许灵活的模型构建和高效的计算。通过在前向传播执行期间逐步构建图，PyTorch 能够动态适应输入大小、控制流和可变长度序列，从而更高效地利用内存和计算资源。autograd 系统实现了自动微分，应用微积分链式法则来计算所有模型参数的梯度。这种灵活性是 PyTorch 在深度学习研究和生产中广受欢迎的关键原因，因为它将高性能与灵活性和透明性相结合，使研究人员和工程师能够在不牺牲效率的情况下尝试动态架构和复杂的控制流。

## 12.3 JAX

文献综述：Li et al. (2024) [313] 提出了基于 JAX 的可微分密度泛函理论（DFT），使材料科学模拟中实现端到端可微分性。该论文通过利用 JAX 的自动微分和并行化能力，将机器学习理论扩展到量子化学领域，以高效优化密度泛函模型。Bieberich 和 Li (2024) [314] 使用 JAX 和 Diffrax 探索了量子机器学习（QML），以高效求解神经微分方程。他们开发了一种量子神经常微分方程的新理论模型，并讨论了 JAX 如何促进高效的基于 GPU 的量子模拟。Dagrêu et al. (2024) [315] 分析了 JAX 和 PyTorch 中黑森-向量积（HVP）计算在深度学习中的效率。他们建立了深度学习和优化中计算二阶导数的数学基础，展示了 JAX 出色的自动微分能力。Lohoff 和 Neftci (2025) [316] 开发了一种深度强化学习（DRL）模型，用于优化 JAX 的 autograd 引擎以用于科学计算。他们通过一个理论框架展示了强化学习如何提高 JAX 中的计算效率。





该方法消除了深度学习中的冗余计算。Legrand et al. (2024) [317] 引入了一个用于预测编码网络（PCNs）的基于 JAX 和 Rust 的深度学习库。他们探索了超越传统反向传播的神经网络理论扩展，为分层生成模型提供了形式化框架。Alzás and Radev (2024) [318] 使用 JAX 为核反应创建了可微分模型，展示了其在高能物理模拟中的强大能力。他们为理论物理建立了一个新的可微分框架，利用 JAX 的基于梯度的优化来改进核物理建模。Edenhofer et al. (2024) [319] 在 JAX 中开发了高斯过程和变分推理框架，扩展了传统的贝叶斯方法。他们使用 JAX 在统计物理和深度学习之间架起了桥梁，在高斯过程与深度神经网络之间制定了理论联系。Chan et al. (2024) [320] 提出了一个用于长尾 X 射线分类的基于 JAX 的量子机器学习框架。他们在 JAX 中引入了一种新型量子迁移学习技术，展示了其在医学影像中相对于经典深度学习模型的优势。Ye et al. (2025) [321] 使用 JAX 对电子转移动力学进行建模，连接了深度学习和密度泛函理论（DFT）。他们开发了一个用于建模电荷转移反应的新理论框架，利用 JAX 的高性能计算能力用于量子化学应用。Khan et al. (2024) [322] 利用 JAX 高效的自动微分能力，将 NODEs 扩展到高维动态系统。他们为将 NODEs 扩展到随机和混沌系统建立了严格的数学框架，利用 JAX 的高速并行化能力。

JAX 是一个先进的数值计算框架，旨在优化高性能科学计算任务，特别侧重于自动微分、硬件加速和即时编译（JIT）。这些功能对于机器学习、优化、物理模拟和计算科学等应用至关重要，在这些应用中，大规模、高维计算必须在速度和效率兼顾的前提下执行。在其核心，JAX 整合了基于线性代数、优化理论、张量微积分和数值微分等高级概念的深层数学结构，为跨多核 CPU、GPU 和 TPU 的可扩展计算奠定了基础。该框架利用反向模式微分和即时编译的强大功能，在确保正确性和准确性的同时显著减少计算时间。接下来的严谨探讨将从数学和概念上剖析这些操作，解释其内部运作机制及其理论含义。

JAX 的自动微分是其高效计算梯度、雅可比矩阵、黑森矩阵及其他导数的核心。对于许多应用，感兴趣的函数涉及在优化和机器学习任务中计算相对于模型参数的梯度。自动微分允许使用反向模式微分技术高效计算这些梯度。让我们考虑一个函数 $f : \mathbb{R}^n \rightarrow \mathbb{R}^m$，并假设我们希望计算标量值输出相对于每个输入变量的梯度。$f$ 的梯度，表示为 $\nabla_{\mathbf{x}}f$，是偏导数向量：

```
$\nabla_{\mathbf{x}} f(\mathbf{x}) = \left( \frac{\partial f_1}{\partial x_1}, \frac{\partial f_1}{\partial x_2}, \dots, \frac{\partial f_1}{\partial x_n}, \dots, \frac{\partial f_m}{\partial x_n} \right), \quad \text{(612)}$
```

其中 $f = (f_1, f_2, \dots, f_m)$ 表示 $m$ 个标量输出的向量，$\mathbf{x} = (x_1, x_2, \dots, x_n)$ 表示输入向量。反向模式微分通过按逆序应用链式法则来计算此梯度。如果 $f$ 由多个中间函数组成，例如 $f = g \circ h$，其中 $g : \mathbb{R}^m \rightarrow \mathbb{R}^p$ 且 $h : \mathbb{R}^n \rightarrow \mathbb{R}^m$，则 $f$ 相对于 $\mathbf{x}$ 的梯度是通过递归应用链式法则计算的：

```
$\nabla_{\mathbf{x}} f(\mathbf{x}) = \left( \frac{\partial g}{\partial h} \right) \cdot \left( \frac{\partial h}{\partial x_1}, \frac{\partial h}{\partial x_2}, \dots, \frac{\partial h}{\partial x_n} \right). \quad \text{(613)}$
```

链式法则的这种递归应用确保每个中间梯度计算都沿函数层向后传播，与前向模式微分相比减少了所需的遍历次数。当输出数量 \(m\) 远小于输入数量 \(n\) 时，这种技术尤其有利，因为它最大限度地降低了计算复杂度。在 JAX 中，自动微分通过诸如 `jax.grad` 之类的函数使用，该函数可应用于标量值函数，以返回其相对于向量值输入的梯度。要计算高阶导数（如黑森矩阵），JAX 允许使用类似原理计算二阶及更高阶导数。标量函数 \(f(\mathbf{x})\) 的黑森矩阵 \(H\) 由二阶导数矩阵给出：

\(H = \left( \frac{\partial^2 f}{\partial x_i \partial x_j} \right),\)
(614)

这通过再次应用链式法则来计算。二阶导数可以通过对梯度再次求导来高效计算，并且可以通过继续链式法则的递归应用将此过程扩展到更高阶导数。

JAX 高性能计算方法中的一个核心概念是 **JIT (即时编译)**，它通过将 Python 函数编译为针对底层硬件架构优化的机器码，提供显著的性能提升。JAX 中的即时编译建立在 **XLA (加速线性代数)** 编译器的基础上。XLA 通过将多个操作融合为单个内核来优化张量操作的执行，从而减少与启动单个计算内核相关的开销。这种技术对于机器学习任务中常见的矩阵乘法、卷积和其他张量操作尤其有效。例如，考虑一系列简单的操作 \(f = \text{Op}_1(\text{Op}_2(\dots (\text{Op}_n(\mathbf{x}))))\)，其中 \(\text{Op}_i\) 表示应用于输入张量 \(\mathbf{x}\) 的不同数学操作。在没有优化的情况下，每个操作通常会单独执行，引入显著开销。然而，JAX 的 JIT 编译器会识别此序列并应用融合变换，从而生成单个复合操作：

\(\text{Optimized}(f(\mathbf{x})) = \text{Fused Op}(\mathbf{x}),\)
(615)

其中 Fused Op 表示原始操作序列的高度优化版本。此优化最大限度地减少了内核启动次数并降低内存访问开销，从而加速计算。JIT 编译器分析函数的计算图并识别将操作合并为更高效形式的机会，最终加速在 GPU 或 TPU 等硬件加速器上的计算。

JAX 通过 `jax.vmap` 算子提供的 **向量化** 功能是高性能计算的另一项关键优化。此功能自动在数据批次上向量化函数，允许在多个数据点上并行应用相同操作。从数学上讲，对于函数 \(f : \mathbb{R}^n \to \mathbb{R}^m\) 和输入批次 \(\mathbf{X} \in \mathbb{R}^{B \times n}\)，向量化函数可表示为：

\(\mathbf{Y} = \text{vmap}(f)(\mathbf{X}),\)
(616)

其中 \(B\) 是批次大小，\(\mathbf{Y}\) 是 \(\mathbb{R}^{B \times m}\) 中的矩阵，包含将 \(f\) 应用于 \(\mathbf{X}\) 每一行的结果。JAX 应用的数学操作与将 \(f\) 应用于每个单独行 \(\mathbf{X}_i\) 相同，但好处是整个批次并行处理，高效利用可用硬件资源。能够 **跨多设备并行化计算** 是 JAX 最强大的功能之一，它通过 `jax.pmap` 算子实现。该算子允许在不同设备（如多个 GPU 或 TPU）上并行执行函数。假设我们有一个函数 \(f : \mathbb{R}^n \to \mathbb{R}^m\) 和一组分布在 \(p\) 个设备上的输入 \(\mathbf{X} = (\mathbf{X}_1, \mathbf{X}_2, \dots, \mathbf{X}_p)\)。该函数的并行执行可写为：

\(\mathbf{Y} = \text{pmap}(f)(\mathbf{X}),\)
(617)

其中每个设备独立计算其部分 \(f(\mathbf{X}_i)，并将结果收集到最终输出 \(\mathbf{Y}\) 中。此功能对于大规模分布式训练至关重要



机器学习模型中，模型的参数和数据必须分布在多个设备上，以确保高效训练。并行化有效地减少了计算时间，因为每个设备在数据和模型参数的不同子集上运行。**GPU/TPU 加速**是 JAX 性能的另一个关键方面，它由 cuBLAS 等库为 GPU 促成，这些库专门用于优化矩阵运算。许多数值计算任务中使用的主要操作是矩阵乘法，JAX 通过利用这些操作的硬件加速实现来优化这一点。考虑两个矩阵 **A** 和 **B** 的矩阵乘法，其中 \(\mathbf{A} \in \mathbb{R}^{n \times m}\) 和 \(\mathbf{B} \in \mathbb{R}^{m \times p}\)，生成一个矩阵 \(\mathbf{C} \in \mathbb{R}^{n \times p}\)：

\(\mathbf{C} = \mathbf{A} \times \mathbf{B}.\) (618)

使用 cuBLAS 或类似库，JAX 可以在 GPU 上执行此操作，利用硬件的大规模并行处理能力高效执行乘法。可以通过考虑 GPU 的特定内存层次结构来进一步优化此操作，其中大型矩阵乘法被分解为适合 GPU 高速内存的较小块。此技术最大限度地减少内存带宽限制，加速计算。除了这些核心操作外，JAX 允许使用 `jax.custom_jvp` 装饰器定义**自定义梯度**，使用户能够手动指定雅克比-向量积 (JVP) 以进行更高效的梯度计算。此功能在机器学习应用中特别有用，其中某些操作可能具有无法自动计算的自定义梯度。例如，在像 softmax 这样非平凡的激活函数中，为了效率，可能会显式提供自定义梯度函数：

\(\frac{\partial \text{softmax}(\mathbf{x})}{\partial \mathbf{x}} = \text{diag}(\text{softmax}(\mathbf{x})) - \text{softmax}(\mathbf{x}) \cdot \text{softmax}(\mathbf{x})^T.\) (619)

因此，JAX 同时提供了灵活性和性能，能够支持既需要高效性又需要定义复杂自定义导数的科学计算应用。

通过提供自动微分、JIT 编译、向量化、并行化、硬件加速和自定义梯度等高级功能，JAX 能够处理广泛的高性能计算任务，使其成为解决复杂科学和工程问题的宝贵工具。该框架不仅确保数值方法的正确性，还利用现代硬件的能力，实现对大规模模拟、机器学习和优化任务至关重要的性能。

# 13 附录

## 13.1 线性代数基础

### 13.1.1 矩阵与向量空间

**矩阵的定义：** 矩阵 \(A\) 是按行和列排列的数字（或来自字段 \(\mathbb{F}\) 的元素）的矩形数组：

\(A = \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1n} \\ a_{21} & a_{22} & \cdots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn} \end{bmatrix} \in \mathbb{F}^{m \times n}\) (620)

其中 \(a_{ij}\) 表示 \(A\) 在第 \(i\) 行和第 \(j\) 列的**元素**。如果 \(m = n\)，则为**方阵**。如果所有非对角元素均为零，则矩阵为**对角矩阵**。对于矩阵 \(A \in \mathbb{F}^{m \times n}\) 和 \(B \in \mathbb{F}^{m \times n}\)，以下是矩阵运算：

- **加法**：按元素定义：
  $$(A + B)_{ij} = A_{ij} + B_{ij}$$ (621)

- **标量乘法**：对于 $\alpha \in \mathbb{F}$，
  $$(\alpha A)_{ij} = \alpha \cdot A_{ij}$$ (622)

- **矩阵乘法**：如果 $A \in \mathbb{F}^{m \times p}$ 和 $B \in \mathbb{F}^{p \times n}$，则乘积 $C = AB$ 由以下给出：
  $$C_{ij} = \sum_{k=1}^p A_{ik} B_{kj}$$ (623)

仅当 $A$ 的列数等于 $B$ 的行数时，此定义才有效。

- **转置**：$A$ 的转置，记作 $A^T$，满足：
  $$(A^T)_{ij} = A_{ji}$$ (624)

- **行列式**：如果 $A \in \mathbb{F}^{n \times n}$，则其行列式递归给出为：
  $$\det(A) = \sum_{j=1}^n (-1)^{1+j} a_{1j} \det(A_{1j})$$ (625)

其中 $A_{1j}$ 是通过删除第一行和第 $j$ 列得到的 $(n - 1) \times (n - 1)$ 子矩阵。

- **逆矩阵**：方阵 $A$ 可逆当且仅当存在 $A^{-1}$ 使得：
  $$AA^{-1} = A^{-1}A = I$$ (626)

其中 $I$ 是单位矩阵。

### 13.1.2 向量空间与线性变换

**向量空间** 关于字段 $\mathbb{F}$ 的向量空间是带有两个运算的集合 $V$：

- **向量加法**：$\mathbf{v} + \mathbf{w}$ 对于 $\mathbf{v}, \mathbf{w} \in V$
- **标量乘法**：$\alpha \mathbf{v}$ 对于 $\alpha \in \mathbb{F}$ 和 $\mathbf{v} \in V$

满足 8 个向量空间公理（结合律、交换律、单位元的存在等）。如果集合 $\{\mathbf{v}_1, \mathbf{v}_2, \dots, \mathbf{v}_n\}$ 满足以下条件，则它是一组基：

- 线性无关：
  $$\sum_{i=1}^n \alpha_i \mathbf{v}_i = 0 \Rightarrow \alpha_i = 0, \forall i$$ (627)

- 张成 $V$，意味着每个 $\mathbf{v} \in V$ 都可以写成：
  $$\mathbf{v} = \sum_{i=1}^n \beta_i \mathbf{v}_i$$ (628)

$V$ 的**维度**，记作 $\dim(V)$，是基向量的数量。**线性变换**：函数 $T: V \to W$ 是线性的，如果：
  $$T(\alpha \mathbf{v} + \beta \mathbf{w}) = \alpha T(\mathbf{v}) + \beta T(\mathbf{w})$$ (629)

$T$ 的**矩阵表示**是矩阵 $A$，使得：
  $$T(\mathbf{x}) = A \mathbf{x}$$ (630)

### 13.1.3 特征值与特征向量

**定义：** 对于方阵 $A \in \mathbb{F}^{n \times n}$，特征值 $\lambda$ 和特征向量 $\mathbf{v} \neq 0$ 满足：

$$A\mathbf{v} = \lambda\mathbf{v}$$ (631)

**特征方程：** 特征值通过求解以下方程得到：

$$\det(A - \lambda I) = 0$$ (632)

这给出了关于 $\lambda$ 的 $n$ 次多项式。$(A - \lambda I)\mathbf{v} = 0$ 的所有解 $\mathbf{v}$ 的集合是与 $\lambda$ 相关的特征空间。

### 13.1.4 奇异值分解 (SVD)

**定义：** 对于任意 $A \in \mathbb{F}^{m \times n}$，**奇异值分解** (SVD) 表示：

$$A = U\Sigma V^T$$ (633)

其中 $U \in \mathbb{F}^{m \times m}$ 是正交矩阵 ($U^T U = I$)，$V \in \mathbb{F}^{n \times n}$ 是正交矩阵 ($V^T V = I$)，$\Sigma$ 是一个 $m \times n$ 对角矩阵：

$$\Sigma = \begin{bmatrix} \sigma_1 & 0 & \cdots & 0 \\ 0 & \sigma_2 & \cdots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \cdots & \sigma_r \end{bmatrix}$$ (634)

其中 $\sigma_i$ 是**奇异值**，由以下给出：

$$\sigma_i = \sqrt{\lambda_i}$$ (635)

其中 $\lambda_i$ 是 $A^T A$ 的特征值。

## 13.2 概率与统计

### 13.2.1 概率分布

**概率分布**是一种数学函数，用于提供实验中不同可能结果发生的概率。随机变量 $X$ 可以取样本空间 $S$ 中的值，概率分布描述了概率在这些可能结果上的分布方式。

**离散概率分布：** 对于从可数集合取值的离散随机变量 $X$，**概率质量函数** (PMF) 定义为：

$$P(X = x_i) = p(x_i), \quad \forall x_i \in S$$ (636)

PMF 满足以下属性：

- 对于每个 $x_i \in S$，$0 \le p(x_i) \le 1$。

- 所有可能结果的概率之和为 1：

$$\sum_{x_i \in S} p(x_i) = 1$$ (637)

离散概率分布的一个例子是**二项分布**，它描述了在固定数量的独立伯努利试验中成功次数。二项分布的 PMF 为：

$$P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}, \quad k = 0, 1, \dots, n$$ (638)

其中 \(n\) 是试验次数，\(p\) 是每次试验的成功概率，\(k\) 是成功次数。

**连续概率分布：** 对于从连续集合（例如实数轴）取值的连续随机变量 \(X\)，使用**概率密度函数** (PDF) 而不是 PMF。PDF \(f(x)\) 的定义方式使得对于任何区间 \([a, b]\)，\(X\) 落在该区间内的概率为：

$$P(a \le X \le b) = \int_a^b f(x) \, dx$$ (639)

PDF 必须满足：

- 对所有 \(x\)，\(f(x) \ge 0\)。

- \(X\) 整个范围上的总概率为 1：
  $$\int_{-\infty}^{\infty} f(x) \, dx = 1$$ (640)

连续概率分布的一个例子是**正态分布**，其 PDF 由以下给出：

$$f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}, \quad x \in \mathbb{R}$$ (641)

其中 \(\mu\) 是均值，\(\sigma^2\) 是分布的方差。

### 13.2.2 贝叶斯定理

贝叶斯定理基于可能与事件相关的条件的先验知识，描述了事件的概率。它是概率论和统计学领域的基本结果。

设 \(A\) 和 \(B\) 为两个事件。那么，贝叶斯定理给出了在 \(B\) 条件下 \(A\) 的条件概率：

$$P(A|B) = \frac{P(B|A)P(A)}{P(B)}$$ (642)

其中 \(P(A|B)\) 是在 \(B\) 条件下 \(A\) 的后验概率，\(P(B|A)\) 是似然，即在 \(A\) 条件下观察到 \(B\) 的概率，\(P(A)\) 是 \(A\) 的先验概率，\(P(B)\) 是 \(B$ 的边缘似然，计算如下：

$$P(B) = \sum_i P(B|A_i)P(A_i)$$ (643)

在连续情况下，贝叶斯定理写为：

$$P(A|B) = \frac{P(B|A)P(A)}{P(B)} = \frac{P(B|A)P(A)}{\int P(B|A')P(A') \, dA'}$$ (644)

这允许根据观察到的证据 \(B\) 更新关于假设 \(A\) 的信念。让我们考虑一种疾病的诊断测试。设 \(A\) 为某人患有该疾病的事件，设 \(B\)



为检测呈阳性的事件。我们感兴趣的是在检测呈阳性的情况下，某人患有该疾病的概率，即 P(A|B)。根据贝叶斯定理，我们有：

$P(A|B) = \frac{P(B|A)P(A)}{P(B)}$ (645)

其中 P(B|A) 是在该人患有疾病的情况下检测结果为阳性的概率（灵敏度），P(A) 是患病的先验概率，P(B) 是检测结果为阳性的总概率。

### 13.2.3 统计量

统计量总结了数据或概率分布的属性。一些关键的统计量包括均值、方差、标准差和偏度。

统计量是一个函数 M : S → R，它为统计空间 S 中的元素赋予一个实值量，其中 S 可以表示数据集、概率分布或随机过程。在数学上，统计量必须满足某些属性，例如可测性、变换下的不变性以及收敛一致性，才能被良好定义。统计量大致可分为以下几类：

- 1. 中心趋势度量（例如，均值、中位数、众数）
- 2. 离散度量（例如，方差、标准差、四分位数间距）
- 3. 形状度量（例如，偏度、峰度）
- 4. 关联度量（例如，协方差、相关系数）
- 5. 信息论度量（例如，熵、互信息）

这些度量中的每一个都为数据集或概率分布的特征提供了不同的见解。有几种中心趋势度量。给定概率空间 (Ω, F, P) 和随机变量 X : Ω → R，期望（或均值）定义为：

$\mathbb{E}[X] = \int_{\Omega} X(\omega) dP(\omega)$ (646)

如果 X 是具有概率质量函数 p(x) 的离散随机变量，则：

$\mathbb{E}[X] = \sum_{x \in \mathbb{R}} xp(x)$ (647)

如果 X 是具有概率密度函数 f(x) 的连续随机变量，则：

$\mathbb{E}[X] = \int_{-\infty}^{\infty} xf(x) dx$ (648)

概率分布的中位数 m 定义为：

$P(X \le m) \ge \frac{1}{2}, \quad P(X \ge m) \ge \frac{1}{2}$ (649)

就累积分布函数 F(x) 而言，中位数 m 满足：

$F(m) = \frac{1}{2}$ (650)

**众数**定义为最大化概率密度函数的点 $x_m$：

$$x_m = \arg \max_x f(x)$$

随机变量 $X$ 的方差 $\sigma^2$ 由以下给出：

$$\text{Var}(X) = \mathbb{E}[(X - \mathbb{E}[X])^2]$$

展开该表达式：

$$\text{Var}(X) = \mathbb{E}[X^2] - (\mathbb{E}[X])^2$$

**标准差** $\sigma$ 定义为方差的平方根：

$$\sigma = \sqrt{\text{Var}(X)}$$

如果 $Q_1$ 和 $Q_3$ 分别表示数据集的第一四分位数和第三四分位数（其中 $Q_1$ 是第 25 个百分位数，$Q_3$ 是第 75 个百分位数），则四分位数间距为：

$$IQR = Q_3 - Q_1$$

随机变量 $X$ 的**偏度**定义为：

$$\gamma_1 = \frac{\mathbb{E}[(X - \mathbb{E}[X])^3]}{\sigma^3}$$

它量化了概率分布的不对称性。**峰度**由以下给出：

$$\gamma_2 = \frac{\mathbb{E}[(X - \mathbb{E}[X])^4]}{\sigma^4}$$

正态分布具有 $\gamma_2 = 3$，偏离此值表明分布具有厚尾或轻尾。有几种关联度量。**协方差**定义如下：给定两个随机变量 $X$ 和 $Y$，它们的**协方差**为：

$$\text{Cov}(X, Y) = \mathbb{E}[(X - \mathbb{E}[X])(Y - \mathbb{E}[Y])]$$

展开：

$$\text{Cov}(X, Y) = \mathbb{E}[XY] - \mathbb{E}[X]\mathbb{E}[Y]$$

皮尔逊相关系数定义为：

$$\rho(X, Y) = \frac{\text{Cov}(X, Y)}{\sigma_X \sigma_Y}$$

其中 $\sigma_X$ 和 $\sigma_Y$ 分别是 $X$ 和 $Y$ 的标准差。信息论度量是熵，离散概率分布 $p(x)$ 的**熵**由以下给出：

$$H(X) = -\sum_x p(x) \log p(x)$$

对于具有密度 $f(x)$ 的连续分布，**微分熵**为：

$$h(X) = -\int_{-\infty}^{\infty} f(x) \log f(x) dx$$

给定两个随机变量 $X$ 和 $Y$，它们的互信息为：

$$I(X; Y) = H(X) + H(Y) - H(X, Y)$$

它衡量了解 $X$ 在多大程度上减少了关于 $Y$ 的不确定性。统计量满足线性和不变性，即：

- **- 期望是线性的：**

  \(\mathbb{E}[aX + bY] = a\mathbb{E}[X] + b\mathbb{E}[Y]\)

- **- 方差具有平移不变性，但按平方缩放：**

  \(\text{Var}(aX + b) = a^2\text{Var}(X)\)

对于收敛和渐近行为，**大数定律**保证经验均值收敛到期望值，而**中心极限定理**指出，独立同分布随机变量的和在分布上收敛到正态分布。

随机变量 \(X\) 的**均值**或**期望值**（记为 \(\mathbb{E}[X]\)）表示 \(X\) 的平均值。对于离散随机变量：

\(\mathbb{E}[X] = \sum_{x_i \in S} x_i p(x_i)\)

对于连续随机变量，期望值由以下给出：

\(\mathbb{E}[X] = \int_{-\infty}^{\infty} x f(x) \, dx\)

随机变量 \(X\) 的**方差**（记为 \(\text{Var}(X)\)）衡量分布的离散程度或分散度。对于离散随机变量：

\(\text{Var}(X) = \mathbb{E}[X^2] - (\mathbb{E}[X])^2\)

对于连续随机变量：

\(\text{Var}(X) = \int_{-\infty}^{\infty} x^2 f(x) \, dx - \left( \int_{-\infty}^{\infty} x f(x) \, dx \right)^2\)

**标准差**是方差的平方根，并提供与随机变量相同单位的分布离散度量：

\(\text{SD}(X) = \sqrt{\text{Var}(X)}\)

随机变量 \(X\) 的**偏度**量化了概率分布的不对称性。它定义为：

\(\text{Skew}(X) = \frac{\mathbb{E}[(X - \mathbb{E}[X])^3]}{(\text{Var}(X))^{3/2}}\)

正偏度表示分布在右侧有长尾，而负偏度表示分布在左侧有长尾。随机变量 \(X\) 的**峰度**衡量分布的“尾重性”，即概率质量有多少集中在尾部。它定义为：

\(\text{Kurt}(X) = \frac{\mathbb{E}[(X - \mathbb{E}[X])^4]}{(\text{Var}(X))^2}\)

峰度高的分布具有厚尾，而与正态分布相比，峰度低的分布具有薄尾。

## 13.3 优化技术

### 13.3.1 梯度下降 (GD)

梯度下降是一种用于最小化可微函数的迭代优化算法。其目标是找到函数取得最小值的点。在数学上，可以这样表述。给定可微目标函数 \( f : \mathbb{R}^n \rightarrow \mathbb{R} \)，梯度下降更新规则为：

```
\mathbf{x}_{k+1} = \mathbf{x}_k - \eta \nabla f(\mathbf{x}_k)
```

其中：

- \(\mathbf{x}_k \in \mathbb{R}^n\) 是 \(n\) 维空间中的当前点（迭代索引 \(k\)），
- \(\nabla f(\mathbf{x}_k)\) 是在 \(\mathbf{x}_k\) 处的目标函数梯度，
- \(\eta\) 是学习率（步长）。

为分析梯度下降的收敛性，我们假设 \(f\) 是**凸**的且**可微**，并且具有**Lipschitz 连续梯度**。也就是说，存在常数 \(L > 0\)，使得：

```
\|\nabla f(\mathbf{x}) - \nabla f(\mathbf{y})\| \leq L\|\mathbf{x} - \mathbf{y}\|, \quad \forall \mathbf{x}, \mathbf{y} \in \mathbb{R}^n.
```

该属性确保 \(f\) 的梯度变化不会太快，从而允许我们界定收敛速率。以下是每次迭代中函数值下降的上界：

```
f(\mathbf{x}_{k+1}) - f(\mathbf{x}^*) \leq (1 - \eta L)(f(\mathbf{x}_k) - f(\mathbf{x}^*)),
```

其中 \(\mathbf{x}^*\) 是全局最小值。因此，我们有以下收敛速率：

```
f(\mathbf{x}_k) - f(\mathbf{x}^*) \leq (1 - \eta L)^k(f(\mathbf{x}_0) - f(\mathbf{x}^*)).
```

为使其收敛，我们需要 \(\eta L < 1\)。因此，必须仔细选择步长 \(\eta\) 以确保收敛。

### 13.3.2 随机梯度下降 (SGD)

随机梯度下降是梯度下降的一种变体，它在每次迭代时使用随机选择的数据子集（小批量）来近似目标函数的梯度。当数据集较大时，这可以显著降低计算成本。

令目标函数为对应于每个数据点的各个函数 \(f_i(\mathbf{x})\) 的和：

```
f(\mathbf{x}) = \frac{1}{m} \sum_{i=1}^m f_i(\mathbf{x}),
```

其中 \(m\) 是数据点的数量。在**随机梯度下降**中，更新规则变为：

```
\mathbf{x}_{k+1} = \mathbf{x}_k - \eta \nabla f_{i_k}(\mathbf{x}_k),
```

其中 \(i_k\) 是第 \(k\) 次迭代中随机选择的索引，\(\nabla f_{i_k}(\mathbf{x})\) 是对应于该随机选择数据点的函数 \(f_{i_k}(\mathbf{x})\) 的梯度。随机梯度由以下给出：

```
\nabla f_{i_k}(\mathbf{x}_k) = \nabla f_{i_k}(\mathbf{x}_k).
```

鉴于梯度是随机的，SGD 的收敛性分析更为复杂。假设每个 \(f_i\) 都是凸且可微的，并且使用强凸性假设（即，存在常数 \(m > 0\)，使得 \(f\) 满足不等式）：

```
f(\mathbf{x}) - f(\mathbf{y}) \geq m\|\mathbf{x} - \mathbf{y}\|^2, \quad \forall \mathbf{x}, \mathbf{y} \in \mathbb{R}^n,
```





SGD 收敛到最优解的速率为：

\[
\mathbb{E}[f(\mathbf{x}_k) - f(\mathbf{x}^*)] \le \frac{C}{k},\quad (681)
\]

其中 \(C\) 是取决于步长 \(\eta\)、随机梯度的方差以及强凸性常数 \(m\) 的常数。这种较慢的收敛速率是由于梯度估计中固有的噪声造成的。通常会采用方差降低技术，例如 **小批量 SGD**（每次迭代使用多个数据点）或 **动量**（累积过去的梯度），以提高收敛速度和稳定性。

### 13.3.3 二阶方法

二阶方法不仅使用梯度 \(\nabla f(\mathbf{x})\)，还使用 **Hessian 矩阵** \(\mathbf{H}(\mathbf{x}) = \nabla^2 f(\mathbf{x})\)，即目标函数的二阶偏导数矩阵。二阶方法的更新规则为：

\[
\mathbf{x}_{k+1} = \mathbf{x}_k - \eta \mathbf{H}^{-1}(\mathbf{x}_k) \nabla f(\mathbf{x}_k),\quad (682)
\]

其中 \(\mathbf{H}^{-1}(\mathbf{x}_k)\) 是 Hessian 矩阵的逆矩阵。

与梯度下降相比，二阶方法通常具有更快的收敛速度，尤其是当函数 \(f\) 具有良好条件数的曲率时。然而，计算 Hessian 矩阵的计算开销很大，限制了这些方法的可扩展性。牛顿法是一种广泛使用的二阶优化技术，同时使用梯度和 Hessian 矩阵。更新规则如下：

\[
\mathbf{x}_{k+1} = \mathbf{x}_k - \eta \mathbf{H}^{-1}(\mathbf{x}_k) \nabla f(\mathbf{x}_k).\quad (683)
\]

在目标函数两次连续可微且 Hessian 矩阵正定的假设下，牛顿法在最优点附近具有二阶收敛性。更准确地说，如果 \(\mathbf{x}_k\) 足够接近最优点 \(\mathbf{x}^*\)，则误差 \(\|\mathbf{x}_k - \mathbf{x}^*\|\) 以二阶速率下降：

\[
\|\mathbf{x}_{k+1} - \mathbf{x}^*\| \le C \|\mathbf{x}_k - \mathbf{x}^*\|^2,\quad (684)
\]

其中 \(C\) 是取决于 Hessian 矩阵条件数的常数。

由于直接计算 Hessian 矩阵代价高昂，拟牛顿方法旨在每次迭代时近似逆 Hessian 矩阵。最流行的拟牛顿方法之一是 **Broyden–Fletcher–Goldfarb–Shanno (BFGS)** 方法，它维护逆 Hessian 矩阵的近似值，并在每次迭代时进行更新。我们上面讨论的内容总结如下：

- **梯度下降 (GD)**: 一种优化算法，沿目标函数梯度的反方向更新参数向量。在凸性假设下，通过适当选择步长，可以保证收敛。
- **随机梯度下降 (SGD)**: 梯度下降的一种变体，在每次迭代时使用数据的随机子集来估计梯度。虽然更快且计算开销较低，但其收敛速度较慢且噪声更大，需要方差降低技术才能进行高效训练。
- **二阶方法**: 这些方法使用 Hessian 矩阵（目标函数的二阶导数）来加速收敛，在最优点附近通常表现出二阶收敛。然而，计算 Hessian 矩阵的计算成本限制了其实际应用。拟牛顿方法（如 BFGS）近似 Hessian 矩阵以提高效率。

每种方法都有其优势和权衡，基于梯度的方法因其简单和高效而被广泛使用，而二阶方法提供更快的收敛，但计算成本更高。

## 13.4 矩阵微积分

### 13.4.1 矩阵求导

考虑一个大小为 m × n 的矩阵 A，其中 A = [a_ij]。为了求导目的，我们将关注将矩阵映射为标量或其他矩阵的函数 f(A)。我们的目标是计算 f(A) 关于 A 的导数。设 f(A) 为矩阵 A 的标量函数。该标量函数关于 A 的导数定义为：

\[
\frac{\partial f(\mathbf{A})}{\partial \mathbf{A}} = \left[ \frac{\partial f(\mathbf{A})}{\partial a_{ij}} \right] \quad (685)
\]

这是一个矩阵，其中第 (i,j) 项是标量函数关于元素 a_ij 的偏导数。让我们以 Frobenius 范数求导为例。考虑矩阵 A 的 Frobenius 范数，定义为：

\[
\|\mathbf{A}\|_F = \sqrt{\sum_{i=1}^m \sum_{j=1}^n a_{ij}^2} \quad (686)
\]

要计算 \(\|\mathbf{A}\|_F\) 关于 A 的导数，我们首先应用链式法则：

\[
\frac{\partial \|\mathbf{A}\|_F}{\partial a_{ij}} = \frac{2a_{ij}}{2\|\mathbf{A}\|_F} = \frac{a_{ij}}{\|\mathbf{A}\|_F} \quad (687)
\]

因此，Frobenius 范数的梯度是矩阵 \(\frac{\mathbf{A}}{\|\mathbf{A}\|_F}\)。常见函数的矩阵导数如下：

- **矩阵迹**: 对于矩阵 A，迹 Tr(A) 关于 A 的导数是单位矩阵：

\[
\frac{\partial \text{Tr}(\mathbf{A})}{\partial \mathbf{A}} = \mathbf{I} \quad (688)
\]

- **矩阵乘积**: 设 A 和 B 为矩阵，考虑乘积 f(A) = AB。该乘积关于 A 的导数为：

\[
\frac{\partial (\mathbf{AB})}{\partial \mathbf{A}} = \mathbf{B}^T \quad (689)
\]

- **矩阵逆**: A 的逆关于 A 的导数为：

\[
\frac{\partial (\mathbf{A}^{-1})}{\partial \mathbf{A}} = -\mathbf{A}^{-1} \left( \frac{\partial \mathbf{A}}{\partial \mathbf{A}} \right) \mathbf{A}^{-1} \quad (690)
\]

### 13.4.2 张量求导

张量是一组分量的多维数组，在基变换时按照一定规则进行变换。为简单起见，让我们关注二阶张量（即 m × n 形式的矩阵），但结果可以扩展到高阶张量。

设 T 为一个张量，由分量数组 \(T_{i_1, i_2, ..., i_k}\) 表示，其中索引 \(i_1, i_2, ..., i_k\) 是张量的维度。设 f(T) 为依赖于张量 T 的标量值函数。该函数关于张量分量 \(T_{i_1, ..., i_k}\) 的导数由以下公式给出：

\[
\frac{\partial f(\mathbf{T})}{\partial T_{i_1, ..., i_k}} = \text{Jacobian of } f(\mathbf{T}) \text{ with respect to } T_{i_1, ..., i_k} \quad (691)
\]

例如，考虑二阶张量的函数 $f(\mathbf{T})$，其中 $\mathbf{T}$ 是一个矩阵。求导规则遵循与矩阵求导类似的原则。雅可比矩阵以相同的方式为每个张量分量计算，基于对单个张量分量的偏导数。

考虑一个二阶张量 $\mathbf{T}$，让我们计算 $\mathbf{T}$ 的 Frobenius 范数的导数：

\[
\|\mathbf{T}\|_F = \sqrt{\sum_{i_1, i_2, \dots, i_k} T_{i_1, \dots, i_k}^2} \quad (692)
\]

对 $T_{i_1, \dots, i_k}$ 求导，我们得到：

\[
\frac{\partial \|\mathbf{T}\|_F}{\partial T_{i_1, \dots, i_k}} = \frac{2 T_{i_1, \dots, i_k}}{2 \|\mathbf{T}\|_F} = \frac{T_{i_1, \dots, i_k}}{\|\mathbf{T}\|_F} \quad (693)
\]

这是 Frobenius 范数的梯度，其中每个分量 $T_{i_1, \dots, i_k}$ 由 Frobenius 范数归一化。对于高阶张量，求导遵循相同的原理，但扩展到多索引分量。如果 $\mathbf{T}$ 是一个三阶张量，例如 $T_{i_1, i_2, i_3}$，则 $f(\mathbf{T})$ 对任何分量的导数由以下公式给出：

\[
\frac{\partial f(\mathbf{T})}{\partial T_{i_1, i_2, i_3}} = \text{Jacobian of } f(\mathbf{T}) \text{ with respect to the multi-index components.} \quad (694)
\]

对于两个张量 $\mathbf{T}_1$ 和 $\mathbf{T}_2$（假设阶数分别为 $p$ 和 $q$）的张量积，其乘积是另一个阶数为 $p + q$ 的张量。张量积 $\mathbf{T}_1 \otimes \mathbf{T}_2$ 的求导遵循乘法法则：

\[
\frac{\partial (\mathbf{T}_1 \otimes \mathbf{T}_2)}{\partial \mathbf{T}_1} = \mathbf{T}_2, \quad \frac{\partial (\mathbf{T}_1 \otimes \mathbf{T}_2)}{\partial \mathbf{T}_2} = \mathbf{T}_1 \quad (695)
\]

该张量积法则适用于高阶张量，求导遵循张量缩约规则。对矩阵和张量进行求导的过程将求导规则扩展到多维数据结构，需要谨慎应用链式法则、乘法法则，并理解函数的雅可比矩阵。对于矩阵，导数是偏导数组成的矩阵；而对于张量，导数通常表示为关于多索引分量的张量。在高阶张量求导中，我们递归应用这些原则，考虑多索引表示法，并遵循定义分量如何相互作用的张量缩约规则。

我们从带有矩阵参数的标量值函数求导开始。设 \(f : \mathbb{R}^{m \times n} \to \mathbb{R}\) 为矩阵 \(\mathbf{X}\) 的标量函数。\(f\) 的微分 \(df\) 定义为：

\[
df = \lim_{\|\mathbf{H}\| \to 0} \frac{f(\mathbf{X} + \mathbf{H}) - f(\mathbf{X})}{\|\mathbf{H}\|} \quad (696)
\]

其中 \(\mathbf{H}\) 是一个无穷小扰动。\(f\) 的全导数由以下公式给出：

\[
df = \text{tr} \left( \left( \frac{\partial f}{\partial \mathbf{X}} \right)^T d\mathbf{X} \right). \quad (697)
\]

矩阵梯度的定义：梯度 \(\mathbf{D_X}f\)（或雅可比矩阵）是满足以下条件的唯一矩阵：

\[
df = \text{tr} \left( \mathbf{D_X}^T d\mathbf{X} \right) . \quad (698)
\]

这确保了求导与 Frobenius 内积 \(\langle \mathbf{A}, \mathbf{B} \rangle = \text{tr}(\mathbf{A}^T \mathbf{B})\) 是对偶的，从而赋予了 **Hilbert 空间结构**。让我们从二次型求导的示例开始。设 \(f(\mathbf{X}) = \text{tr}(\mathbf{X}^T \mathbf{A} \mathbf{X})\)。在微小扰动 \(\mathbf{H}\) 下展开：

\[
f(\mathbf{X} + \mathbf{H}) = \text{tr}((\mathbf{X} + \mathbf{H})^T \mathbf{A} (\mathbf{X} + \mathbf{H})). \quad (699)
\]




展开并分离线性项：

$$df = \text{tr}(\mathbf{H}^T \mathbf{A} \mathbf{X}) + \text{tr}(\mathbf{X}^T \mathbf{A} \mathbf{H}). \tag{700}$$

利用迹的循环性质：

$$df = \text{tr}(\mathbf{H}^T(\mathbf{A}\mathbf{X} + \mathbf{A}^T\mathbf{X})). \tag{701}$$

因此，导数为：

$$\frac{\partial f}{\partial \mathbf{X}} = \mathbf{A}\mathbf{X} + \mathbf{A}^T\mathbf{X}. \tag{702}$$

如果 $\mathbf{A}$ 是对称的 ($\mathbf{A}^T = \mathbf{A}$)，这简化为：

$$\frac{\partial f}{\partial \mathbf{X}} = 2\mathbf{A}\mathbf{X}. \tag{703}$$

### 关于矩阵值函数的微分

考虑一个可微函数 $\mathbf{F} : \mathbb{R}^{m \times n} \to \mathbb{R}^{p \times q}$。**Fréchet 导数** $\mathcal{D}_\mathbf{X}\mathbf{F}$ 是一个满足以下条件的**四阶张量**：

$$d\mathbf{F} = \mathcal{D}_\mathbf{X}\mathbf{F} : d\mathbf{X}. \tag{704}$$

关于矩阵逆的微分，对于 $\mathbf{F}(\mathbf{X}) = \mathbf{X}^{-1}$ 我们使用恒等式：

$$d(\mathbf{X}\mathbf{X}^{-1}) = 0 \Rightarrow d\mathbf{X}\mathbf{X}^{-1} + \mathbf{X}d\mathbf{X}^{-1} = 0. \tag{705}$$

求解 $d\mathbf{X}^{-1}$ 得：

$$d\mathbf{X}^{-1} = -\mathbf{X}^{-1}(d\mathbf{X})\mathbf{X}^{-1}. \tag{706}$$

因此，导数是**负双线性算子**：

$$\mathcal{D}_\mathbf{X}(\mathbf{X}^{-1}) = -(\mathbf{X}^{-1} \otimes \mathbf{X}^{-1}). \tag{707}$$

其中 $\otimes$ 表示 Kronecker 积。

### 关于张量值函数的微分

我们需要一个可微张量函数 $\mathcal{F} : \mathbb{R}^{m \times n \times p} \to \mathbb{R}^{a \times b \times c}$，其**Fréchet 导数**应为一个满足以下条件的**高阶张量** $\mathcal{D}_\mathcal{X}\mathcal{F}$：

$$d\mathcal{F} = \mathcal{D}_\mathcal{X}\mathcal{F} : d\mathcal{X}. \tag{708}$$

### 让我们进行张量收缩的微分

如果 $f(\mathcal{X}) = \mathcal{X} : \mathcal{A}$，其中 $\mathcal{X}, \mathcal{A}$ 是二阶张量，则：

$$\frac{\partial}{\partial \mathcal{X}}(\mathcal{X} : \mathcal{A}) = \mathcal{A}. \tag{709}$$

对于四阶张量 $\mathcal{C}$，如果 $f(\mathcal{X}) = \mathcal{C} : \mathcal{X}$，则：

$$\frac{\partial}{\partial \mathcal{X}}(\mathcal{C} : \mathcal{X}) = \mathcal{C}. \tag{710}$$

### 微分也可以在非欧几里得空间中进行

对于流形 $\mathcal{M}$，微分通过切空间 $T_\mathbf{X}\mathcal{M}$ 定义，协变导数 $\nabla_\mathbf{X}$ 满足 **Levi-Civita 连接**：

$$\nabla_\mathbf{X}\mathbf{Y} = \lim_{\epsilon \to 0} \frac{\text{Proj}_{T_{\mathbf{X}+\epsilon\mathbf{H}}\mathcal{M}}(\mathbf{Y}(\mathbf{X} + \epsilon\mathbf{H})) - \mathbf{Y}(\mathbf{X})}{\epsilon}. \tag{711}$$

### 我们也可以使用变分原理进行微分

如果 $f(\mathbf{X})$ 是一个能量泛函，则源自 **Gâteaux 导数** 的微分为：

$$\delta f = \lim_{\epsilon \to 0} \frac{f(\mathbf{X} + \epsilon\mathbf{H}) - f(\mathbf{X})}{\epsilon}. \tag{712}$$

对于泛函，微分使用 **欧拉-拉格朗日方程**：

$$\frac{d}{dt} \int_\Omega L(\mathbf{X}, \nabla \mathbf{X}) dV = 0. \tag{713}$$

# 14 致谢

作者承认那些奠基性工作塑造了我们对深度学习理解的研究人员的贡献。

# 参考文献

- [1] Rao, N., Farid, M., and Raiz, M. (2024). λ-Szász 算子与广义 Beta 函数及近似理论的对称性. Symmetry, 16(12), 1703.
- [2] Mukhopadhyay, S.N., Ray, S. (2025). 函数空间. 载于：测度与积分. 数学科学大学教材. Springer, Singapore.
- [3] Szoldra, T. (2024). 量子系统中的遍历性破缺：从精确时间演化到机器学习 (博士论文).
- [4] SONG, W. X., CHEN, H., CUI, C., LIU, Y. F., TONG, D., GUO, F., ... 和 XIAO, C. W. (2025). 建立可持续城市更新模型的理论、方法学与实施考量. 自然资源学报, 40(1), 20-38.
- [5] El Mennaoui, O., Kharou, Y., and Laasri, H. (2025). 极大正则性框架中的演化半群. Evolution Equations and Control Theory, 0-0.
- [6] Pedroza, G. (2024). 机器学习域稳定性条件研究：一种数学方法. arXiv 预印本 arXiv:2412.00464.
- [7] Cerveira-Vioglio, S., and Ok, E. A. (2024). 集值函数的抽象积分. Journal of Mathematical Analysis and Applications, 129169.
- [8] Averin, A. (2024). 引力熵界的表述与证明. arXiv 预印本 arXiv:2412.02470.
- [9] Potter, T. (2025). 在 L²(ℝⁿ) 下在晶体学平移下不变的子空间. arXiv e-prints, arXiv-2501.
- [10] Lee, M. (2025). 人工智能中自我认同的涌现：一种数学框架及与生成式大语言模型的实证研究. Axioms, 14(1), 44.
- [11] Wang, R., Cai, L., Wu, Q., and Niyato, D. (2025). 具有内在动态防御能力的服务功能链部署. IEEE Transactions on Mobile Computing.
- [12] Duim, J. L., and Mesquita, D. P. (2025). 通过逆强化学习实现人工智能价值对齐. 巴西计算与应用数学学会论文集, 11(1), 1-2.
- [13] Khayat, M., Barka, E., Serhani, M. A., Sallabi, F., Shuaib, K., and Khater, H. M. (2025). 基于人工智能与机器学习赋能安全运营中心——系统文献综述. IEEE Access.
- [14] Agrawal, R. (2025). 基于 DenseNet 的自适应加权损失函数进行黑色素瘤检测. 计算机科学及其应用新兴趋势, 283.
- [15] Hailemichael, H., and Ayalew, B. 基于混合模型学习与控制屏障函数的锂离子电池自适应安全快充. 可在 SSRN 5110597 上查阅.
- [16] Nguyen, E., Xiao, J., Fan, Z., and Ruan, D. 基于度量学习推理的无对比剂颅内血管几何完整估计. 在 Medical Imaging with Deep Learning 中.
- [17] Luo, Z., Bi, Y., Yang, X., Li, Y., Wang, S., and Ye, Q. 主干道无信号交叉口碰撞风险预警的新型机器视觉方法. Frontiers in Physics, 13, 1527956.
- [18] Bousquet, N., Thomassé, S. (2015). VC-维与 Erdős–Pósa 性质. Discrete Mathematics, 338(12), 2302-2317.
- [19] Asian, O., Yildiz, O. T., Alpaydin, E. (2009 年 9 月). 决策树的 VC-维计算. 在 2009 年第 24 届计算机与信息科学国际研讨会上 (第 193-198 页). IEEE.
- [20] Zhang, C., Bian, W., Tao, D., Lin, W. (2012). 用于分析实函数类复杂度的离散化 Vapnik-Chervonenkis 维. IEEE 神经网络与学习系统汇刊, 23(9), 1461-1472.
- [21] Riondato, M., Akdere, M., Çetintemel, U., Zdonik, S. B., Upfal, E. (2011). SQL 查询的 VC-维及采样选择性估计. 在 Machine Learning and Knowledge Discovery in Databases: European Conference, ECML PKDD 2011, Athens, Greece, September 5-9, 2011, Proceedings, Part II 22 (第 661-676 页). Springer Berlin Heidelberg.
- [22] Bane, M., Riggle, J., Sonderegger, M. (2010). 基于约束的文法的 VC 维. Lingua, 120(5), 1194-1208.
- [23] Anderson, A. (2023). 模糊 VC 组合数学与连续逻辑中的距离性. arXiv 预印本 arXiv:2310.04393.
- [24] Fox, J., Pach, J., Suk, A. (2021). 有界 VC-维蕴含 Schur-Erdős 猜想. Combinatorica, 41(6), 803-813.
- [25] Johnson, H. R. (2021). 有限 VC 维的二进制串. arXiv 预印本 arXiv:2101.06490.
- [26] Janzing, D. (2018). 通过低 VC 维因果模型类合并联合分布. arXiv 预印本 arXiv:1804.03206.
- [27] Hüllermeier, E., Fallah Tehrani, A. (2012 年 7 月). 关于 Choquet 积分的 vc-维. 在 International Conference on Information Processing and Management of Uncertainty in Knowledge-Based Systems 上 (第 42-50 页). Berlin, Heidelberg: Springer Berlin Heidelberg.
- [28] Mohri, M. (2018). 机器学习基础.
- [29] Cucker, F., Zhou, D. X. (2007). 学习理论：一种逼近理论视角 (第 24 卷). Cambridge University Press.
- [30] Shalev-Shwartz, S., Ben-David, S. (2014). 理解机器学习：从理论到算法. Cambridge University Press.
- [31] Truong, L. V. (2022). 基于 Rademacher 复杂度的深度学习泛化界. arXiv 预印本 arXiv:2208.04284.
- [32] Gnecco, G., and Sanguineti, M. (2008). 通过 Rademacher 复杂度的逼近误差界. Applied Mathematical Sciences, 2, 153-176.
- [33] Astashkin, S. V. (2010). 对称空间中的 Rademacher 函数. Journal of Mathematical Sciences, 169(6), 725-886.




- [34] Ying 和 Campbell (2010). 用于学习核问题的 Rademacher 混沌复杂度. 神经计算, 22(11), 2858-2886.

- [35] 朱, J., Gibson, B., and Rogers, T. T. (2009). 人类 Rademacher 复杂度. 神经信息处理系统进展, 22.

- [36] Astashkin, S. V., Astashkin, S. V., and Mazlum. (2020). 函数空间中的 Rademacher 系统. 巴塞尔: Birkhäuser.

- [37] Sachs, S., van Erven, T., Hodgkinson, L., Khanna, R., and Şimşekli, U. (2023 年 7 月). 基于算法相关 Rademacher 复杂度的泛化保证. 在《第三十六届年度学习理论大会》(第 4863-4880 页). PMLR.

- [38] Ma 和 Wang (2020). Rademacher 复杂度与残差网络的泛化误差. 数学科学通报, 18(6), 1755-1774.

- [39] Bartlett, P. L., and Mendelson, S. (2002). Rademacher 和高斯复杂度: 风险界和结构结果. 机器学习研究杂志, 3(Nov), 463-482.

- [40] Bartlett, P. L., and Mendelson, S. (2002). Rademacher 和高斯复杂度: 风险界和结构结果. 机器学习研究杂志, 3(Nov), 463-482.

- [41] McDonald, D. J., and Shalizi, C. R. (2011). 平稳序列的 Rademacher 复杂度. arXiv 预印本 arXiv:1106.0730.

- [42] Abderachid, S., and Kenza, B. 黎曼-利奥维尔分数 Sobolev 空间中的嵌入及其应用.

- [43] Giang, T. H., Tri, N. M., and Tuan, D. A. (2024). 关于带权的某些 Sobolev 和 Pólya-Szegö 类型不等式及其应用. arXiv 预印本 arXiv:2412.15490.

- [44] Ruiz, P. A., and Fragkiadaki, V. (2024). 分数 Sobolev 嵌入和代数性质: 二元视角. arXiv 预印本 arXiv:2412.12051.

- [45] Bilalov, B., Mamedov, E., Sezer, Y., and Nasibova, N. (2025). Banach 函数空间中的紧性: Poincaré 和 Friedrichs 不等式. 巴勒莫数学协会记录第 2 系列, 74(1), 68.

- [46] Cheng, M., and Shao, K. (2025). 不齐非线性分数 Schrödinger-Poisson 方程的基态. 复变量与椭圆方程, 1-17.

- [47] Wei, J., and Zhang, L. (2025). 零质量和带权 Hardy Sobolev 亚临界指数的 Schrödinger-Poisson 方程 Nehari-Pohozaev 类型基态解. 几何分析杂志, 35(2), 48.

- [48] Zhang, X., and Qi, W. (2025). R<sup>N</sup> 中一类带小扰动的非齐次准线性椭圆系统的多重性结果. arXiv 预印本 arXiv:2501.01602.

- [49] Xiao, J., and Yue, C. (2025). 分数拉普拉斯算子的迹原理及其在图像处理中的应用. La Matematica, 1-26.

- [50] Pesce, A., and Portaro, S. (2025). 与超抛物算子相关的分数 Sobolev 空间. arXiv 预印本 arXiv:2501.05898.

- [51] LASSOUED, D. (2026). 环面上的函数及多周期函数研究. Kragujevac 数学杂志, 50(2), 297-337.

- [52] Chen, H., Chen, H. G., and Li, J. N. (2024). Hörmander 向量场的嵌入尖锐结果和几何不等式. arXiv 预印本 arXiv:2404.19393.

- [53] Adams, R. A., and Fournier, J. J. (2003). Sobolev 空间. Elsevier.

- [54] Brezis, H., and Brézis, H. (2011). 函数分析、Sobolev 空间和偏微分方程 (第 2 卷, 第 3 期, 第 5 页). 纽约: Springer.

- [55] Evans, L. C. (2022). 偏微分方程 (第 19 卷). 美国数学学会.

- [56] Maz'â, V. G. (2011). Sobolev 空间: 与椭圆偏微分方程的应用. Springer.

- [57] Hornik, K., Stinchcombe, M., and White, H. (1989). 多层前馈网络是通用逼近器. 神经网络, 2(5), 359-366.

- [58] Cybenko, G. (1989). Sigmoidal 函数的叠加逼近. 控制、信号与系统数学, 2(4), 303-314.

- [59] Barron, A. R. (1993). Sigmoidal 函数叠加的通用逼近界. IEEE 信息论汇刊, 39(3), 930-945.

- [60] Pinkus, A. (1999). 神经网络中 MLP 模型的逼近理论. 数值计算年鉴, 8, 143-195.

- [61] Lu, Z., Pu, H., Wang, F., Hu, Z., and Wang, L. (2017). 神经网络的表达能力: 从宽度视角看. 神经信息处理系统进展, 30.

- [62] Hanin, B., and Sellke, M. (2017). 使用最小宽度 relu 网络逼近连续函数. arXiv 预印本 arXiv:1710.11278.

- [63] García-Cervera, C. J., Kessler, M., Pedregal, P., and Periago, F. 集合值映射的通用逼近和 DeepONet 对可控性映射的逼近.

- [64] Majee, S., Abhishek, A., Strauss, T., and Khan, T. (2024). MCMC-Net: 使用神经网络加速逆问题中的马尔可夫链蒙特卡罗. arXiv 预印本 arXiv:2412.16883.

- [65] Toscano, J. D., Wang, L. L., and Karniadakis, G. E. (2024). KKANs: Kurkova-Kolmogorov-Arnold 网络及其学习动态. arXiv 预印本 arXiv:2412.16738.

- [66] Son, H. (2025). ELM-DeepONets: 通过极端学习机进行无反向传播训练的深度算子网络. arXiv 预印本 arXiv:2501.09395.

- [67] Rudin, W. (1964). 数学分析原理 (第 3 卷). 纽约: McGraw-hill.

- [68] Stein, E. M., and Shakarchi, R. (2009). 实分析: 测度论、积分与希尔伯特空间. 普林斯顿大学出版社.

- [69] Conway, J. B. (2019). 函数分析教程 (第 96 卷). Springer.

- [70] Dieudonné, J. (2020). 函数分析史. 在《函数分析、全纯性与逼近理论》(第 119-129 页). CRC Press.

- [71] Folland, G. B. (1999). 实分析: 现代技术及其应用 (第 40 卷). John Wiley and Sons.

- [72] Sugiura, S. (2024). 关于用于一致逼近的储层计算的普遍性.

- [73] LIU, Y., LIU, S., HUANG, Z., and ZHOU, P. 规范模体以及积分、级数展开和微分的范畴化.

- [74] Barreto, D. M. (2025). Stone-Weierstrass 定理.

- [75] Chang, S. Y., and Wei, Y. (2024). 广义 Choi–Davis–Jensen 算子不等式及其应用. 对称性, 16(9), 1176.

- [76] Caballer, M., Dantas, S., and Rodríguez-Vidanes, D. L. (2024). 在 Stone-Weierstrass 定理失效中寻找线性结构. arXiv 预印本 arXiv:2405.06453.

- [77] Chen, D. (2024). 一致拓扑中的 Machado–Bishop 定理. 逼近理论杂志, 304, 106085.

- [78] Rafiei, H., and Akbarzadeh-T, M. R. (2024). 用于系统辨识与控制的带嵌入模糊语言神经网络. IEEE 人工智能汇刊.

- [79] Kolmogorov, A. N. (1957). 关于通过一元连续函数的叠加和加法表示多元连续函数. 在《科学院院报》(第 114 卷, 第 5 期, 第 953-956 页). 俄罗斯科学院.

- [80] Arnold, V. I. (2009). 关于将多元函数表示为变量数较少的函数的叠加. 收集著作: 函数表示、天体力学和 KAM 理论, 1957–1965, 25-46.

- [81] Lorentz, G. G. (1966). 函数逼近, Athena 系列. 数学选题.

- [82] Guilhoto, L. F., and Perdikaris, P. (2024). Kolmogorov 叠加定理的深度学习替代方案. arXiv 预印本 arXiv:2410.01990.

- [83] Alhafiz, M. R., Zakaria, K., Dung, D. V., Palar, P. S., Dwianto, Y. B., and Zuhal, L. R. (2025). 用于数据驱动湍流建模的 Kolmogorov-Arnold 网络. 在 AIAA SCITECH 2025 论坛 (第 2047 页).

- [84] Lorencin, I., Mrzljak, V., Poljak, I., and Etinger, D. (2024 年 9 月). 使用 Kolmogorov-Arnold 网络预测 CODLAG 推进系统参数. 在 2024 IEEE 第 22 届纪念国际智能系统与信息学 symposium (SISY) (第 173-178 页). IEEE.

- [85] Trevisan, D., Cassara, P., Agazzi, A., and Scardera, S. 知识蒸馏的 NTK 分析.

- [86] Bonfanti, A., Bruno, G., and Cipriani, C. (2024). 物理信息神经网络非线性模式面临的挑战. arXiv 预印本 arXiv:2402.03864.

- [87] Jacot, A., Gabriel, F., and Hongler, C. (2018). 神经切核: 神经网络中的收敛与泛化. 神经信息处理系统进展, 31.

- [88] Lee, J., Xiao, L., Schoenholz, S., Bahri, Y., Novak, R., Sohl-Dickstein, J., and Pennington, J. (2019). 任意深度宽神经网络在梯度下降下演变为线性模型. 神经信息处理系统进展, 32.

- [89] Yang, G., and Hu, E. J. (2020). 无限宽神经网络中的特征学习. arXiv 预印本 arXiv:2011.14522.

- [90] Xiang, L., Dudziak, L., Abdelfattah, M. S., Chau, T., Lane, N. D., and Wen, H. (2021). 可微分架构搜索中的零成本操作评分. arXiv 预印本 arXiv:2106.06799.



- [91] Lee, J., Xiao, L., Schoenholz, S., Bahri, Y., Novak, R., Sohl-Dickstein, J., 和 Pennington, J. (2019). 任何深度的宽神经网络在梯度下降下演变为线性模型. 神经信息处理系统进展, 32.

- [92] McAllester, D. A. (1999, July). PAC-Bayesian 模型平均. 在第十二届年度计算机学习理论会议论文集中（第 164-170 页）.

- [93] Catoni, O. (2007). PAC-Bayesian 有监督分类：统计学习的热力学. arXiv 预印本 arXiv:0712.0248.

- [94] Germain, P., Lacasse, A., Laviolette, F., 和 Marchand, M. (2009, June). PAC-Bayesian 线性分类器的学习. 在第 26 届国际机器学习会议论文集中（第 353-360 页）.

- [95] Seeger, M. (2002). PAC-Bayesian 高斯过程分类的泛化误差界. 机器学习研究期刊, 3(Oct), 233-269.

- [96] Alquier, P., Ridgway, J., 和 Chopin, N. (2016). 关于吉布斯后验变分近似的性质. 机器学习研究期刊, 17(236), 1-41.

- [97] Dziugaite, G. K., 和 Roy, D. M. (2017). 计算具有比训练数据多得多参数的深度（随机）神经网络的非真空泛化界. arXiv 预印本 arXiv:1703.11008.

- [98] Rivasplata, O., Kuzborskij, I., Szepesvári, C., 和 Shawe-Taylor, J. (2020). 超出常规界限的 PAC-Bayes 分析. 神经信息处理系统进展, 33, 16833-16845.

- [99] Lever, G., Laviolette, F., 和 Shawe-Taylor, J. (2013). 通过分布依赖先验获得更紧的 PAC-Bayes 界. 理论计算机科学, 473, 4-28.

- [100] Rivasplata, O., Parrado-Hernández, E., Shawe-Taylor, J. S., Sun, S., 和 Szepesvári, C. (2018). 具有实例依赖先验的稳定算法 PAC-Bayes 界. 神经信息处理系统进展, 31.

- [101] Lindemann, L., Zhao, Y., Yu, X., Pappas, G. J., 和 Deshmukh, J. V. (2024). 基于符合预测的形式验证与控制. arXiv 预印本 arXiv:2409.00536.

- [102] Jin, G., Wu, S., Liu, J., Huang, T., 和 Mu, R. (2025). 通过混淆谱正则化增强强公平性. arXiv 预印本 arXiv:2501.13273.

- [103] Ye, F., Xiao, J., Ma, W., Jin, S., 和 Yang, Y. (2025). 在随机块模型中检测小簇. 统计论文, 66(2), 37.

- [104] Bhattacharjee, A., 和 Bharadwaj, P. (2025). 基于对称自编码器的相干谱特征提取. IEEE 选定主题应用地球观测和遥感杂志.

- [105] Wu, Q., Hu, B., Liu, C. et al. (2025). 基于高精度双曲 Radon 变换的 \(L_{q_1} - L_{q_2}\) 正则化速度分析. 纯与应用地球物理.

- [106] Ortega, I., Hannigan, J. W., Baier, B. C., McKain, K., 和 Smale, D. (2025). 推进 NDACC/IRWG 高精度直接太阳 FTIR 观测的 CH4 和 N2O 检索策略. EGUsphere, 2025, 1-32.

- [107] Kazmi, S. H. A., Hassan, R., Qamar, F., Nisar, K., 和 Al-Betar, M. A. (2025). 用于网络威胁情报的联邦条件变分自编码器：解决 SDN 环境中的非 IID 数据. IEEE Access.

- [108] Zhao, Y., Bi, Z., Zhu, P., Yuan, A., 和 Li, X. (2025). 带投影自适应特征选择的深度谱聚类. IEEE 地球科学与遥感汇刊.

- [109] Saranya, S., 和 Menaka, R. (2025). 基于 EEG 信号常见空间模式的自闭症检测量子机器学习方法. IEEE Access.

- [110] Dhalbiso, S., Mohapatra, A., 和 Rout, A. (2024, March). 超越 5G 系统的无单元大规模 MIMO 设计，采用 MMSE 和 RZF 处理. 在机器学习、物联网和大数据国际会议论文集中（第 263-273 页）. 新加坡：Springer Nature Singapore.

- [111] Wei, C., Li, Z., Hu, T., Zhao, M., Sun, Z., Jia, K., ... 和 Jiang, S. (2025). 用于 3D 近红外光谱断层扫描的模型卷积神经网络. IEEE 医学成像汇刊.

- [112] Goodfellow, I. (2016). 深度学习（第 196 卷）. MIT 出版社.

- [113] Haykin, S. (2009). 神经网络与学习机器，第 3 版. 皮尔逊教育印度.

- [114] Schmidhuber, J. (2015). 神经网络中的深度学习：概述.

- [115] Bishop, C. M., 和 Nasrabadi, N. M. (2006). 模式识别与机器学习（第 4 卷，第 4 期，第 738 页）. 纽约：Springer.

- [116] Poggio, T., 和 Smale, S. (2003). 学习的数学：处理数据. AMS 公告, 50(5), 537-544.

- [117] LeCun, Y., Bengio, Y., 和 Hinton, G. (2015). 深度学习. 自然, 521(7553), 436-444.

- [118] Tishby, N., 和 Zaslavsky, N. (2015, April). 深度学习与信息瓶颈原理. 在 2015 年 IEEE 信息理论研讨会 (ITW) 中（第 1-5 页）. IEEE.

- [119] Sorrenson, P. (2025). 自由形式流：用于科学应用的生成模型（博士论文）.

- [120] Liu, W., 和 Shi, X. (2025). 长江中下游 7 月降水的增强神经网络预测系统.

- [121] Das, P., Mondal, D., Islam, M. A., Al Mohotadi, M. A., 和 Roy, P. C. (2025). 用于具有任意性能的 FGM 球形结构热弹性分析的解析有限积分变换和梯度增强机器学习方法. 理论与应用力学快报, 100576.

- [122] Zhang, R. (2025). 用于连续结构系统辨识的物理信息并行神经网络.

- [123] Ali, S., 和 Hussain, A. (2025). 三角形模糊流系统性能预测的神经智能启发式方法. 机械工程师学会论文集，N 部分：纳米材料、纳米工程和纳米系统期刊, 23977914241310569.

- [124] Li, S. (2025). 不完全信息广泛形式博弈的可扩展、可泛化且离线方法.

- [125] Hu, T., Jin, B., 和 Wang, F. (2025). 单调椭圆问题的迭代深 Ritz 方法. 计算物理学期刊, 113791.

- [126] Chen, P., Zhang, A., Zhang, S., Dong, T., Zeng, X., Chen, S., ... 和 Zhou, Q. (2025). 基于多任务分类变量的 Transformer 神经网络模型的海事近失预测框架及模型可解释性分析方法. 可靠性工程与系统安全, 110845.

- [127] Sun, G., Liu, Z., Gan, L., Su, H., Li, T., Zhao, W., 和 Sun, B. (2025). SpikeNAS-Bench：脉冲神经网络架构 NAS 算法基准测试. IEEE 人工智能汇刊.

- [128] Zhang, Z., Wang, X., Shen, J., Zhang, M., Yang, S., Zhao, W., ... 和 Wang, J. (2025). 非固定偏置迭代器：一种新的迭代格式. IEEE Access.

- [129] Rosa, G. J. (2010). 统计学习基础：数据挖掘、推理与预测，作者 HASTIE, T., TIBSHIRANI, R., 和 FRIEDMAN, J.

- [130] Murphy, K. P. (2012). 机器学习：概率视角. MIT 出版社.

- [131] Srivastava, N., Hinton, G., Krizhevsky, A., Sutskever, I., 和 Salakhutdinov, R. (2014). Dropout：防止神经网络过拟合的简单方法. 机器学习研究期刊, 15(1), 1929-1958.

- [132] Zou, H., 和 Hastie, T. (2005). 通过弹性网进行正则化和变量选择. 皇家统计学会 B 系列（统计方法论）期刊, 67(2), 301-320.

- [133] Vapnik, V. (2013). 统计学习理论的本质. Springer Science and Business Media.

- [134] Ng, A. Y. (2004, July). 特征选择，L1 与 L2 正则化，以及旋转不变性. 在第二十一届国际机器学习会议论文集中（第 78 页）.

- [135] Li, T. (2025). 基于贝叶斯优化和深度学习的抗 HER2 药物临床试验策略优化.

- [136] Yasuda, M., 和 Sekimoto, K. (2024). 具有稀疏正则化隐藏层的高斯-离散受限玻尔兹曼机. 行为计量学, 1-19.

- [137] Xiaodong Luo, William C. Cruz, Xin-Lei Zhang, Heng Xiao, (2023), 在迭代集成平滑器中提高定位性能的超参数优化. 地球能源科学与工程, 第 231 卷，B 部分，212404

- [138] Alrayes, F.S., Maray, M., Alshuhail, A. et al. (2025) 用于高维大数据环境中 IoT 网络的基于统计学习和优化算法的隐私保护方法. 科学报告 15, 3338. https://doi.org/10.1038/s41598-025-87454-1

- [139] Cho, H., Kim, Y., Lee, E., Choi, D., Lee, Y., 和 Rhee, W. (2020). 使用贝叶斯优化进行深度神经网络超参数调整的基本增强策略. IEEE Access, 8, 52588-52608.

- [140] IBRAHIM, M. M. W. (2025). 优化结核病治疗预测：马来西亚槟城 XGBoost 与超参数的比较研究. Sains Malaysiana, 54(1), 3741-3752.

- [141] Abdel-salam, M., Elhoseny, M. 和 El-hasnony, I.M. 疫苗供应链管理的智能安全进化框架，使用机器学习和区块链. SN 计算机科学, 6, 121 (2025). https://doi.org/10.1007/s42979-024-03609-3




- [142] Vali, M. H. (2025). 深度神经网络中用于语音和图像处理的向量量化。

- [143] Vincent, A.M., Jidesh, P. 使用进化算法改进AutoML系统的超参数优化框架。Sci Rep 13, 4737 (2023). https://doi.org/10.1038/s41598-023-32027-3

- [144] Razavi-Termeh, S. V., Sadeghi-Niaraki, A., Ali, F., and Choi, S. M. (2025). 使用地理空间人工智能(GeoAI)改进易洪区域制图：一种由基于数学的元启发式算法增强的非参数算法。环境管理期刊, 375, 124238.

- [145] Kiran, M., and Ozyildirim, M. (2022). 深度强化学习应用的超参数调优。arXiv预印本 arXiv:2201.11182。

- [146] Krizhevsky, A., Sutskever, I., and Hinton, G. E. (2012). 基于深度卷积神经网络的ImageNet分类。神经信息处理系统进展, 25.

- [147] Krizhevsky, A., Sutskever, I., and Hinton, G. E. (2017). 基于深度卷积神经网络的ImageNet分类。ACM通讯, 60(6), 84-90.

- [148] Simonyan, K., and Zisserman, A. (2014). 用于大规模图像识别的非常深层卷积网络。arXiv预印本 arXiv:1409.1556。

- [149] He, K., Zhang, X., Ren, S., and Sun, J. (2016). 面向图像识别的深度残差学习。在IEEE计算机视觉和模式识别会议论文集中（第770-778页）。

- [150] Cohen, T., and Welling, M. (2016年6月). 群等变卷积网络。在国际机器学习会议上（第2990-2999页）。PMLR。

- [151] Zeiler, M. D., and Fergus, R. (2014). 可视化与理解卷积网络。载于：Computer Vision–ECCV 2014：第13届欧洲会议，瑞士苏黎世，2014年9月6-12日，论文集，第I部分 13（第818-833页）。Springer International Publishing。

- [152] Liu, Z., Lin, Y., Cao, Y., Hu, H., Wei, Y., Zhang, Z., ... and Guo, B. (2021). Swin Transformer：基于移动窗口的层次视觉Transformer。在IEEE/CVF国际计算机视觉会议论文集中（第10012-10022页）。

- [153] Lin, M. (2013). 网络中的网络。arXiv预印本 arXiv:1312.4400。

- [154] Rumelhart, D. E., Hinton, G. E., and Williams, R. J. (1986). 通过反向传播错误进行表示学习。自然, 323(6088), 533-536.

- [155] Bensaid, B., Poëtte, G., and Turpault, R. (2024). 动量和RMSProp针对局部平滑函数的迭代收敛：自适应是关键。arXiv预印本 arXiv:2407.15471。

- [156] Liu, Q., and Ma, W. (2024). 纪元锯齿效应：揭示Adam及其他优化器中的训练损失振荡。arXiv预印本 arXiv:2410.10056。

- [157] Li, H. (2024). 机器学习应用中非线性优化的平滑性与自适应性（博士论文，麻省理工学院）。

- [158] Heredia, C. (2024). 使用积分-微分方程建模AdaGrad、RMSProp和Adam。arXiv预印本 arXiv:2411.09734。

- [159] Ye, Q. (2024). 加速梯度下降优化和正则化的预处理。arXiv预印本 arXiv:2410.00232。

- [160] Compagnoni, E. M., Liu, T., Islamov, R., Proske, F. N., Orvieto, A., and Lucchi, A. (2024). 通过SDE视角看自适应方法：关于噪声作用的理论见解。arXiv预印本 arXiv:2411.15958。

- [161] Yao, B., Zhang, Q., Feng, R., and Wang, X. (2024). 基于系统响应曲线的面向 cyber-physical-social intelligence 的一阶优化算法。并行与计算：实践与经验, 36(21), e8197.

- [162] Wen, X., and Lei, Y. (2024年6月). 无梯度训练深度神经网络的快速ADMM框架。在2024年国际神经网络联合会议(IJCNN)上（第1-8页）。IEEE。

- [163] Hannibal, S., Jentzen, A., and Thang, D. M. (2024). 数据驱动监督深度学习中不收敛到全局极小值：Adam和随机梯度下降优化在带ReLU激活的深度神经网络训练中被证明无法收敛到全局极小值。arXiv预印本 arXiv:2410.10533。

- [164] Yang, Z. (2025). 自适应有偏随机优化。IEEE模式分析与机器智能汇刊。

- [165] Kingma, D. P., and Ba, J. (2014). Adam：一种随机优化方法。arXiv预印本 arXiv:1412.6980。

- [166] Reddi, S. J., Kale, S., and Kumar, S. (2019). 关于Adam及其后的收敛性。arXiv预印本 arXiv:1904.09237。

- [167] Jin, L., Nong, H., Chen, L., and Su, Z. (2024). 一种通过多重积分增强Adam泛化能力的方法。arXiv预印本 arXiv:2412.12473。

- [168] Adly, A. M. (2024). EXAdam：自适应交叉矩的力量。arXiv预印本 arXiv:2412.20302。

- [169] Liu, Y., Cao, Y., and Lin, J. 线性逆问题中ADAM算法的收敛性分析。

- [170] Yang, Z. (2025). 自适应有偏随机优化。IEEE模式分析与机器智能汇刊。

- [171] Park, K., and Lee, S. (2024). SMMF：面向内存高效优化的平方矩阵化动量分解。arXiv预印本 arXiv:2412.08894。

- [172] Mahjoubi, M. A., Lamrani, D., Saleh, S., Moutaouakil, W., Ouhmida, A., Hamida, S., ... and Raihani, A. (2025). 使用随机梯度下降在MRI图像上优化ResNet50性能用于阿尔茨海默病分类。基于智能的医学, 100219.

- [173] Seini, A. B., and Adam, I. O. (2024). 面向自适应工作和学习成果的人机协作：活动理论视角。

- [174] Teessar, J. (2024). 问卷基础研究中真实回答的复杂性：一项综合分析。

- [175] Lauand, C. K., and Meyn, S. (2025). 准随机逼近的马可维亚基础。SIAM控制与优化期刊, 63(1), 402-430。

- [176] Maranjyan, A., Tyurin, A., and Richtárik, P. (2025). Ringmaster ASGD：第一个具有最优时间复杂度的异步SGD。arXiv预印本 arXiv:2501.16168。

- [177] Gao, Z., and Gündüz, D. (2025). 用于无线网络中去中心化任务的空中图神经网络。IEEE信号处理汇刊。

- [178] Yoon, T., Choudhury, S., and Loizou, N. (2025). 多人联邦学习：以更少通信达到平衡。arXiv预印本 arXiv:2501.08263。

- [179] Verma, K., and Maiti, A. (2025). 基于正弦和余弦的梯度下降法学习率。应用智能, 55(5), 352。

- [180] Borowski, M., and Miasojedow, B. (2025). 投影随机近似算法的收敛性。arXiv电子预印, arXiv:2501.

- [181] Dong, K., Chen, S., Dan, Y., Zhang, L., Li, X., Liang, W., ... and Sun, Y. (2025). 大脑刺激干预的新视角：大脑网络动态的最优随机跟踪控制。arXiv预印本 arXiv:2501.08567。

- [182] Jiang, Y., Kang, H., Liu, J., and Xu, D. (2025). 带有有偏梯度的去中心化随机梯度下降的收敛性。IEEE信号处理汇刊。

- [183] Sonobe, N., MomoZaki, T., and Nakagawa, T. (2025). 基于密度幂差分的广义后验分布的随机优化采样。arXiv预印本 arXiv:2501.07790。

- [184] Zhang, X., and Jia, G. (2025). 无限时域随机线性二次最优控制问题中策略梯度的收敛性。数学分析与应用期刊, 129264.

- [185] Thiriveedhi, A., Ghanta, S., Biswas, S., and Pradhan, A. K. (2025). ALL-Net：整合CNN和可解释AI以增强急性淋巴细胞白血病的诊断与解读。PeerJ计算机科学, 11, e2600.

- [186] Ramos-Briceño, D. A., Flammia-D'Aleo, A., Fernández-López, G., Carrión-Nessi, F. S., and Forero-Peña, D. A. (2025). 基于深度学习的疟原虫检测：用于准确识别恶性疟原虫和间日疟原虫的卷积神经网络模型。科学报告, 15(1), 3746.

- [187] Espino-Salinas, C. H., Luna-García, H., Cepeda-Arguëlles, A., Trejo-Vázquez, K., Flores-Chaires, L. A., Mercado Reyna, J., ... and Villalba-Condori, K. O. (2025). 抑郁症和精神分裂症检测的卷积神经网络。诊断学, 15(3), 319.

- [188] Ran, T., Huang, W., Qin, X., Xie, X., Deng, Y., Pan, Y., ... and Zou, D. (2025). 使用高光谱成像和深度学习进行胰腺神经内分瘤液基细胞学诊断。EngMedicine, 2(1), 100059.

- [189] Araujo, B. V. S., Rodrigues, G. A., de Oliveira, J. H. P., Xavier, G. V. R., Lebre, U., Cordeiro, C., ... and Ferreira, T. V. (2025). 使用卷积神经网络和图像处理技术结合信号对齐监测ZnO避雷器。测量, 116889.

- [190] Sari, I. P., Elvitaria, L., and Rudiansyah, R. (2025). 基于卷积神经网络(CNN)的蜡染图案分类数据驱动方法。Jurnal Mandiri IT, 13(3), 323-331.





- [191] Wang, D., An, K., Mo, Y., Zhang, H., Guo, W., and Wang, B. Cf-Wiad: Consistency Fusion with Weighted Instance and Adaptive Distribution for Enhanced Semi-Supervised Skin Lesion Classification. Available at SSRN 5109182.
- [192] Cai, P., Zhang, Y., He, H., Lei, Z., and Gao, S. (2025). DFNet: A Differential Feature-Incorporated Residual Network for Image Recognition. Journal of Bionic Engineering, 1-14.
- [193] Vishwakarma, A. K., and Deshmukh, M. (2025). CNNM-FDI: Novel Convolutional Neural Network Model for Fire Detection in Images. IEIE Journal of Research, 1-14.
- [194] Ranjan, P., Kaushal, A., Girdhar, A., and Kumar, R. (2025). Revolutionizing hyperspectral image classification for limited labeled data: unifying autoencoder-enhanced GANs with convolutional neural networks and zero-shot learning. Earth Science Informatics, 18(2), 1-26.
- [195] Naseer, A., and Jalal, A. Multimodal Deep Learning Framework for Enhanced Semantic Scene Classification Using RGB-D Images.
- [196] Wang, Z., and Wang, J. (2025). Personalized Icon Design Model Based on Improved Faster-RCNN. Systems and Soft Computing, 200193.
- [197] Ramana, R., Vasudevan, V., and Murugan, B. S. (2025). Spectral Pyramid Pooling and Fused Keypoint Generation in ResNet-50 for Robust 3D Object Detection. IEIE Journal of Research, 1-13.
- [198] Shin, S., Land, O., Seider, W., Lee, J., and Lee, D. (2025). Artificial Intelligence-Empowered Automated Double Emulsion Droplet Library Generation.
- [199] Taca, B. S., Lau, D., and Rieder, R. (2025). A comparative study between deep learning approaches for aphid classification. IEEE Latin America Transactions, 23(3), 198-204.
- [200] Ulaş, B., Szklenár, T., and Szabó, R. (2025). Detection of Oscillation-like Patterns in Eclipsing Binary Light Curves using Neural Network-based Object Detection Algorithms. arXiv preprint arXiv:2501.17538.
- [201] Valensi, D., Lupu, L., Adam, D., and Topilsky, Y. Semi-Supervised Learning, Foundation Models and Image Processing for Pleural Line Detection and Segmentation in Lung Ultrasound. Foundation Models and Image Processing for Pleural Line Detection and Segmentation in Lung Ultrasound.
- [202] V, A., V, P. and Kumar, D. An effective object detection via BS2ResNet and LTK-Bi-LSTM. Multimed Tools Appl (2025). https://doi.org/10.1007/s11042-024-20433-2
- [203] Zhu, X., Chen, W., and Jiang, Q. (2025). High-transferability black-box attack of binary image segmentation via adversarial example augmentation. Displays, 102957.
- [204] Guo, X., Zhu, Y., Li, S., Wu, S., and Liu, S. (2025). Research and Implementation of Agronomic Entity and Attribute Extraction Based on Target Localization. Agronomy, 15(2), 354.
- [205] Yousif, M., Jassam, N. M., Salim, A., Bardan, H. A., Mutlak, A. F., Sallibi, A. D., and Ataalla, A. F. Melanoma Skin Cancer Detection Using Deep Learning Methods and Binary GWO Algorithm.
- [206] Rahman, S. I. U., Abbas, N., Ali, S., Salman, M., Alkhayat, A., Khan, J., ... and Gu, Y. H. (2025). Deep Learning and Artificial Intelligence-Driven Advanced Methods for Acute Lymphoblastic Leukemia Identification and Classification: A Systematic Review. Comput Model Eng Sci, 142(2).
- [207] Pratap Joshi, K., Gowda, V. B., Bidare Divakarachari, P., Siddappa Parameshwarappa, P., and Patra, R. K. (2025). VSA-GCNN: Attention Guided Graph Neural Networks for Brain Tumor Segmentation and Classification. Big Data and Cognitive Computing, 9(2), 29.
- [208] Ng, B., Eyre, K., and Chetrit, M. (2025). Prediction of ischemic cardiomyopathy using a deep neural network with non-contrast cine cardiac magnetic resonance images. Journal of Cardiovascular Magnetic Resonance, 27.
- [209] Nguyen, H. T., Lam, T. B., Truong, T. T. N., Duong, T. D., and Dinh, V. Q. Mv-Trams: An Efficient Tumor Region-Adapted Mammography Synthesis Under Multi-View Diagnosis. Available at SSRN 5109180.
- [210] Chen, W., Xu, T., and Zhou, W. (2025). Task-based Regularization in Penalized Least-Squares for Binary Signal Detection Tasks in Medical Image Denoising. arXiv preprint arXiv:2501.18418.
- [211] Pradhan, P. D., Talmale, G., and Wazalwar, S. Deep dive into precision (DDiP): Unleashing advanced deep learning approaches in diabetic retinopathy research for enhanced detection and classification of retinal abnormalities. In Recent Advances in Sciences, Engineering, Information Technology and Management (pp. 518-530). CRC Press.
- [212] Örenç, S., Acar, E., Özerdem, M. S., Şahin, S., and Kaya, A. (2025). Automatic Identification of Adenoid Hypertrophy via Ensemble Deep Learning Models Employing X-ray Adenoid Images. Journal of Imaging Informatics in Medicine, 1-15.
- [213] Jiang, M., Wang, S., Chan, K. H., Sun, Y., Xu, Y., Zhang, Z., ... and Tan, T. (2025). Multimodal Cross Global Learnable Attention Network for MR images denoising with arbitrary modal missing. Computerized Medical Imaging and Graphics, 102497.
- [214] Al-Haidri, W., Levchuk, A., Zotov, N., Belousova, K., Ryzhkov, A., Fokin, V., ... and Brui, E. (2025). Quantitative analysis of myocardial fibrosis using a deep learning-based framework applied to the 17-Segment model. Biomedical Signal Processing and Control, 105, 107555.
- [215] Osorio, S. L. J., Ruiz, M. A. R., Mendez-Vazquez, A., and Rodriguez-Tello, E. (2024). Fourier Series Guided Design of Quantum Convolutional Neural Networks for Enhanced Time Series Forecasting. arXiv preprint arXiv:2404.15377.
- [216] Umeano, C., and Kyriienko, O. (2024). Ground state-based quantum feature maps. arXiv preprint arXiv:2404.07174.
- [217] Liu, N., He, X., Laurent, T., Di Giovanni, F., Bronstein, M. M., and Bresson, X. (2024). Advancing Graph Convolutional Networks via General Spectral Wavelets. arXiv preprint arXiv:2405.13806.
- [218] Vlasic, A. (2024). Quantum Circuits, Feature Maps, and Expanded Pseudo-Entropy: A Categorical Theoretic Analysis of Encoding Real-World Data into a Quantum Computer. arXiv preprint arXiv:2410.22084.
- [219] Kim, M., Hioka, Y., and Witbrock, M. (2024). Neural Fourier Modelling: A Highly Compact Approach to Time-Series Analysis. arXiv preprint arXiv:2410.04703.
- [220] Xie, Y., Daigavane, A., Kotak, M., and Smidt, T. (2024). The price of freedom: Exploring tradeoffs between expressivity and computational efficiency in equivariant tensor products. In ICML 2024 Workshop on Geometry-grounded Representation Learning and Generative Modeling.
- [221] Liu, G., Wei, Z., Zhang, H., Wang, R., Yuan, A., Liu, C., ... and Cao, G. (2024, April). Extending Implicit Neural Representations for Text-to-Image Generation. In ICASSP 2024-2024 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP) (pp. 3650-3654). IEEE.
- [222] Zhang, M. (2024). Lock-in spectrum: a tool for representing long-term evolution of bearing fault in the time–frequency domain using vibration signal. Sensor Review, 44(5), 598-610.
- [223] Hamed, M., and Lachiri, Z. (2024, July). Expressivity Transfer In Transformer-Based Text-To-Speech Synthesis. In 2024 IEEE 7th International Conference on Advanced Technologies, Signal and Image Processing (ATSIP) (Vol. 1, pp. 443-448). IEEE.
- [224] Lehmann, F., Gatti, F., Bertin, M., Grenié, D., and Clouteau, D. (2024). Uncertainty propagation from crustal geologies to rock-site ground motion with a Fourier Neural Operator. European Journal of Environmental and Civil Engineering, 28(13), 3088-3105.
- [225] Jurafsky, D. (2000). Speech and language processing.
- [226] Manning, C., and Schutze, H. (1999). Foundations of statistical natural language processing. MIT press.
- [227] Liu, Y., and Zhang, M. (2018). Neural network methods for natural language processing.
- [228] Allen, J. (1988). Natural language understanding. Benjamin-Cummings Publishing Co., Inc.
- [229] Li, Z., Zhao, Y., Zhang, X., Han, H., and Huang, C. (2025). Word embedding factor based multi-head attention. Artificial Intelligence Review, 58(4), 1-21.
- [230] Hempelmann, C. F., Rayz, J., Dong, T., and Miller, T. (2025, January). Proceedings of the 1st Workshop on Computational Humor (CHum). In Proceedings of the 1st Workshop on Computational Humor (CHum).
- [231] Koehn, P. (2009). Statistical machine translation. Cambridge University Press.
- [232] Eisenstein, J. (2019). Introduction to natural language processing. The MIT Press.
- [233] Otter, D. W., Medina, J. R., and Kalita, J. K. (2020). A survey of the usages of deep learning for natural language processing. IEEE transactions on neural networks and learning systems, 32(2), 604-624.
- [234] Mitkov, R. (Ed.). (2022). The Oxford handbook of computational linguistics. Oxford university press.
- [235] Liu, X., Tao, Z., Jiang, T., Chang, H., Ma, Y., and Huang, X. (2024). ToDA: Target-oriented Diffusion Attacker against Recommendation System. arXiv preprint arXiv:2401.12578.
- [236] Çekik, R. (2025). Effective Text Classification Through Supervised Rough Set-Based Term Weighting. Symmetry, 17(1), 90.
- [237] Zhu, H., Xia, J., Liu, R., and Deng, B. (2025). SPIRIT: Structural Entropy Guided Prefix Tuning for Hierarchical Text Classification. Entropy, 27(2), 128.
- [238] Matrane, Y., Benabbou, F., and Ellaky, Z. (2024). Enhancing Moroccan Dialect Sentiment Analysis through Optimized Preprocessing and transfer learning Techniques. IEEE Access.
- [239] Moqbel, M., and Jain, A. (2025). Mining the truth: A text mining approach to understanding perceived deceptive counterfeits and online ratings. Journal of Retailing and Consumer Services, 84, 104149.





- [240] Kumar, V., Iqbal, M. I., and Rathore, R. (2025). 疾病检测中的自然语言处理（NLP）——关于如何利用 NLP 技术分析和分类医疗文本数据以进行疾病诊断的讨论。疾病检测中的 AI：进展与应用, 53-75.

- [241] Yin, S. (2024). 基于方面的情感分析的现状与挑战。应用与计算工程, 114, 25-31.

- [242] Raghavan, M. (2024). 你是 AI 所说的那个人吗？探讨自然语言处理算法从文本中“预测”人格特质的作用（南佛罗里达大学博士论文）。

- [243] Semeraro, A., Vilella, S., Improta, R., De Duro, E. S., Mohammad, S. M., Ruffo, G., and Stella, M. (2025). EmoAtlas：一种融合心理词典、人工智能与网络科学的文本情感网络分析器。行为研究方法, 57(2), 77.

- [244] Cai, F., and Liu, X. 用 Python 进行话语分析的数据分析：以 Dennis Tay 著《治疗谈话》为例。纽约：Routledge, 2024. ISBN: 9781032419015（精装本：41.24 美元），xiii+ 182 页。自然语言处理, 1-4.

- [245] Wu, Yonghui. “Google 的神经机器翻译系统：弥合人类与机器翻译之间的差距。” arXiv 预印本 arXiv:1609.08144 (2016).

- [246] Hettiarachchi, H., Ranasinghe, T., Rayson, P., Mitkov, R., Gaber, M., Premasiri, D., ... and Uyangodage, L. (2024). 首届低资源语言语言模型研讨会（LoResLM 2025）概述。arXiv 预印本 arXiv:2412.16365.

- [247] Das, B. R., and Sahoo, R. (2024). 统计机器翻译中的词对齐：问题与挑战。Nov Joun of Appl Sci Res, 1 (6), 01-03.

- [248] Oluwatoki, T. G., Adetunmbi, O. A., and Boyinbode, O. K. 基于 Transformer 的约鲁巴语到英语机器翻译（TYEMT）系统及 Rouge 评分。

- [249] ÜÇKAN, T., and KURT, E. NLP 中的词嵌入。计算机科学与工程的开创性与创新研究, 58.

- [250] Pastor, G. C., Monti, J., Mitkov, R., and Hidalgo-Ternero, C. M. (2024). 机器翻译与翻译技术中多词单元的最新进展。机器翻译与翻译技术中多词单元的最新进展。

- [251] Fernandes, R. M. 解码空间语义：开源 LLM 与 NMT 系统在 EN-PT-BR 字幕翻译中的性能比较分析（圣保罗大学博士论文）。

- [252] Jozić, K. (2024). 在真实环境中测试 ChatGPT 作为英语-克罗地亚语机器翻译系统的能力：欧洲央行的 eTranslation 与 ChatGPT 对比（萨格勒布大学人文社会科学学院英语语言与文学系博士论文）。

- [253] Yang, M. (2025). 基于改进机器学习方法的英文翻译错误自适应识别。国际高速电子与系统杂志, 2540236.

- [254] Linnemann, G. A., and Reimann, L. E. (2024). 人工智能作为应用社会心理学的新活动领域——扩大研究范围的论证。

- [255] Merkel, S., and Schorr, S. OPP：应用领域与创新技术。

- [256] Kushwaha, N. S., and Singh, P. (2022). 基于人工智能的聊天机器人：一个案例研究。管理与服务科学杂志 (JMSS), 2(1), 1-13.

- [257] Macedo, P., Madeira, R. N., Santos, P. A., Mota, P., Alves, B., and Pereira, C. M. (2024). 面向帕金森病患者的通过激励与支持进行锻炼的交互代理。应用科学, 15(1), 223.

- [258] Gupta, R., Nair, K., Mishra, M., Ibrahim, B., and Bhardwaj, S. (2024). 生成式人工智能的采用与影响：理论基础与研究议程。信息管理数据洞察国际杂志, 4(1), 100232.

- [259] Foroughi, B., Iranmanesh, M., Yadegaridehkordi, E., Wen, J., Ghobakhloo, M., Senali, M. G., and Annamalai, N. (2025). 影响使用 ChatGPT 获取购物信息的因素。国际消费者研究杂志, 49(1), e70008.

- [260] Jandhyala, V. S. V. (2024). 构建 AI 聊天机器人和虚拟助手：面向有志专业人士的技术指南。计算机应用与信息技术研究国际杂志 (IJRCAIT), 7(2), 448-463.

- [261] Pavlović, N., and Savić, M. (2024). ChatGPT 平台对数字营销中消费者体验和用户满意度的影响。经济领域理论与实践研究, 15(3), 636-646.

- [262] Mannava, V., Mitrevski, A., and Plöger, P. G. (2024, August). 探索交互式 AI 用于儿童-机器人交互的适用性。载于 2024 年第 33 届 IEEE 机器人与人类交互通信国际会议 (ROMAN) (pp. 1821-1827). IEEE.

- [263] Sherstinova, T., Mikhaylovskiy, N., Kolpashchikova, E., and Kruglikova, V. (2024, April). 弥补俄语处理中的差距：人工智能与日常对话。载于 2024 年第 35 届开放创新协会会议 (FRUCT) (pp. 665-674). IEEE.

- [264] Lipton, Z. C. (2015). 序列学习中循环神经网络的批判性综述。arXiv 预印本, CoRR, abs/1506.00019.

- [265] Pascanu, R. (2013). 关于训练循环神经网络的难度。arXiv 预印本 arXiv:1211.5063.

- [266] Jaeger, H. (2001). “回声状态”方法用于分析和训练循环神经网络——附勘误说明。德国波恩：德国信息技术国家研究中心 GMD 技术报告, 148(34), 13.

- [267] Hochreiter, S. (1997). 长短期记忆。神经计算 MIT-Press.

- [268] Kawakami, K. (2008). 带循环神经网络的监督序列标注（博士论文，Ph. D. 学位论文）。

- [269] Bengio, Y., Simard, P., and Frasconi, P. (1994). 使用梯度下降学习长期依赖关系是困难的。IEEE 神经网络交易, 5(2), 157-166.

- [270] Bhattamishra, S., Patel, A., and Goyal, N. (2020). 关于 Transformer 的计算能力及其在序列建模中的影响。arXiv 预印本 arXiv:2006.09286.

- [271] Siegelmann, H. T. (1993). 循环神经网络的理论基础。

- [272] Sutton, R. S. (2018). 强化学习：导论。A Bradford Book.

- [273] Barto, A. G. (2021). 强化学习：导论。Richard Sutton 著。SIAM 评论, 6(2), 423.

- [274] Bertsekas, D. P. (1996). 神经动态规划。Athena Scientific.

- [275] Kakade, S. M. (2003). 关于强化学习的样本复杂性。伦敦大学学院（英国）。

- [276] Szepesvári, C. (2022). 强化学习算法。Springer Nature.

- [277] Haarnoja, T., Zhou, A., Abbeel, P., and Levine, S. (2018, July). 软行为-评论者：带随机行为者的非策略最大熵深度强化学习。载于国际机器学习会议 (pp. 1861-1870). PMLR.

- [278] Mnih, V., Kavukcuoglu, K., Silver, D., Rusu, A. A., Veness, J., Bellemare, M. G., ... and Hassabis, D. (2015). 通过深度强化学习实现人类水平控制。Nature, 518(7540), 529-533.

- [279] Konda, V., and Tsitsiklis, J. (1999). 行为-评论者算法。神经信息处理系统进展, 12.

- [280] Levine, S. (2018). 强化学习与控制作为概率推断：教程与综述。arXiv 预印本 arXiv:1805.00909.

- [281] Mannor, S., Mansour, Y., and Tamar, A. (2022). 强化学习：基础。在线手稿。

- [282] Borkar, V. S., and Borkar, V. S. (2008). 随机逼近：动态系统视角（第 9 卷）。剑桥：剑桥大学出版社。

- [283] Takhsha, Amir Reza, Maryam Rastgarpour, and Mozhgan Naderi. “基于 Choquet 积分和微分进化优化的 CXR 图像中 COVID-19 识别特征级集成模型。” arXiv 预印本 arXiv:2501.08241 (2025).

- [284] Singh, P., and Raman, B. (2025). 图神经网络：将深度学习扩展到图。载于《通过张量视角深度学习》(pp. 423-482)。新加坡：Springer Nature Singapore.

- [285] Yao, L., Shi, Q., Yang, Z., Shao, S., and Hariri, S. (2024). 开发边缘鲁棒 ML 集成以容忍 ICS 对抗攻击。arXiv 预印本 arXiv:2409.18244.

- [286] Chen, K., Bi, Z., Niu, Q., Liu, J., Peng, B., Zhang, S., ... and Feng, P. (2024). 深度学习与机器学习，推动大数据分析与管理：Tensorflow 预训练模型。arXiv 预印本 arXiv:2409.13566.

- [287] Dumić, E. (2024). 使用 TensorFlow 和 Keras 学习神经网络设计。载于 ICERI2024 论文集 (pp. 10689-10696). IATED.

- [288] Bajaj, K., Bordoloi, D., Tripathy, R., Mohapatra, S. K., Sarangi, P. K., and Sharma, P. (2024, September). 基于 TensorFlow 的奥迪亚语手写数字识别卷积神经网络。载于 2024 年科学工程与技术计算研究进展国际会议 (ACROSET) (pp. 1-5). IEEE.

- [289] Abbass, A. M., and Fyath, R. S. (2024). 基于人工神经网络的光纤信道建模改进方法：以几何星座整形 WDM 系统为例。应用研究与技术杂志, 22(6), 768-780.





- [290] Prahba, D., Subramanian, R. S., Dinesh, M. G., and Girija, P. (2024). 基于人工智能赋能精准农业的可持续农业. 载于《面向精准农业的人工智能》(第159-182页). Auerbach 出版社.

- [291] Abdelmadjid, S. A. A. D., and Abdeldjallil, A. I. D. I. (2024年11月). 面向边缘计算的优化深度学习模型：基于Raspberry PI4的实时植物病害检测比较研究. 载于《2024年第四届嵌入式与分布式系统国际会议(EDiS)》(第273-278页). IEEE.

- [292] Mlambo, F. (2024). 什么是贝叶斯神经网络.

- [293] Team, G. Y. 比芳：空间站新型自由飞行立方体机器人.

- [294] Tabel, L. (2024). 脉冲神经网络中的延迟学习.

- [295] Naderi, S., Chen, B., Yang, T., Xiang, J., Heaney, C. E., Latham, J. P., ... and Pain, C. C. (2024). 嵌入神经网络的离散元求解方法. 粉体技术, 448, 120258.

- [296] Polaka, S. K. R. (2024). 面向安全强化学习的神经网络验证.

- [297] Erdogan, L. E., Kanakagiri, V. A. R., Keutzer, K., and Dong, Z. (2024). 推荐系统的随机通信避免. arXiv预印本 arXiv:2411.01611.

- [298] Liao, F., Tang, Y., Du, Q., Wang, J., Li, M., and Zheng, J. (2024). 基于迭代部分扩散模型的域渐进式低剂量CT成像. IEEE医学成像汇刊.

- [299] Sekhavat, Y. (2024). 基于尼采理论，探寻秩序与混沌中人工智能艺术的创造基础. 视觉艺术理论原理.

- [300] Cai, H., Yang, Y., Tang, Y., Sun, Z., and Zhang, W. (2025). 基于Shapley值的类激活映射以提升神经网络的可解释性. 可视化计算机, 1-19.

- [301] Na, W. (2024). Rach-Space：面向弱监督学习的新型集成学习方法 (硕士学位论文，塔夫茨大学).

- [302] Khajah, M. M. (2024). 基于多维可推广IRT和技能发现的BKT性能增强. 教育数据挖掘期刊, 16(1), 233-278.

- [303] Zhang, Y., Duan, Z., Huang, Y., and Zhu, F. (2024). 理论边界引导的神经图像编码器分层VAE. arXiv预印本 arXiv:2403.18535.

- [304] Wang, L., and Huang, W. (2025). 过参数化变分自编码器收敛性分析：神经切换核视角. 机器学习, 114(1), 15.

- [305] Li, C. N., Liang, H. P., Zhao, B. Q., Wei, S. H., and Zhang, X. (2024). 机器学习辅助晶体结构预测简化方法. 材料信息学期刊, 4(3), N-A.

- [306] Huang, Y. (2024). 基于扩散概率模型的图像生成研究进展. 科学、工程与技术前沿, 85, 452-456.

- [307] Chenebuah, E. T. (2024). 具有目标特性的能源材料人工智能模拟与设计 (博士学位论文，渥太华大学—渥太华大学).

- [308] Furth, N., Imel, A., and Zawodzinski, T. A. (2024年11月). 还原电位和溶解度预测的图编码器. 载于《电化学学会会议摘要prime2024》(第3期, 第344-344页). 电化学学会公司.

- [309] Gong, J., Deng, Z., Xie, H., Qiu, Z., Zhao, Z., and Tang, B. Z. (2025). 通过数据阐释解析聚集诱导发光材料的设计. 先进科学, 12(3), 2411345.

- [310] Kim, H., Lee, C. H., and Hong, C. (2024年7月). VATMAN：面向事故和恶意行为监控的视频异常Transformer. 载于《2024年IEEE国际高级视频和信号监控会议(AVSS)》(第1-7页). IEEE.

- [311] Albert, S. W., Doostan, A., and Schaub, H. (2024). 用于不确定大机载建模的维度约减. 航天器与火箭期刊, 1-13.

- [312] Sharma, D. K., Hota, H. S., and Rababaah, A. R. (2024). 面向现实世界应用的机器学习 (博士学位论文，印度理工学院帕特纳分校计算机科学与工程系).

- [313] Li, T., Shi, Z., Dale, S. G., Vignale, G., and Lin, M. Crystal：基于JAX的可微分材料密度泛函理论框架.

- [314] Bieberich, S., Li, P., Ngai, J., Patel, K., Vogt, R., Ranade, P., ... and Stafford, S. (2024). 基于理论容错量子计算机求解神经微分方程的量子机器学习：校准与基准测试.

- [315] Dagrèou, M., Ablin, P., Vaiter, S., and Moreau, T. (2024). 如何计算Hessian-向量乘积. 载于《ICLR 2024第三篇博客文章专题》.

- [316] Lohoff, J., and Neftci, E. (2024). 基于深度强化学习的自动微分优化. arXiv预印本 arXiv:2406.05027.

- [317] Legrand, N., Weber, L., Waade, P. T., Daugaard, A. H. M., Khodadadi, M., Mikuš, N., and Mathys, C. (2024). pyghf：面向预测编码的神经网络库. arXiv预印本 arXiv:2410.09206.

- [318] Alzás, P. B., and Radev, R. (2024). 低能量中微子物理的可微分核去激发模拟. arXiv预印本 arXiv:2404.00180.

- [319] Edenhofer, G., Frank, P., Roth, J., Leike, R. H., Guerdi, M., Scheel-Platz, L. I., ... and Enßlin, T. A. (2024). 重构数值信息场理论(NIFTy. re)：高斯过程与变分推断库. arXiv预印本 arXiv:2402.16683.

- [320] Chan, S., Kulkarni, P., Paul, H. Y., and Parekh, V. S. (2024年9月). 拓展视野：面向长尾胸部X射线分类的混合量子迁移学习. 载于《2024年IEEE国际量子计算与工程会议(QCE)》(第1卷, 第572-582页). IEEE.

- [321] Ye, H., Hu, Z., Yin, R., Boyko, T. D., Liu, Y., Li, Y., ... and Li, Y. (2025). 锰孔雀石/有机化合物界面的电子转移：机制、调控及结构重排与分解中的两阶段动力学差异. 地球化学与宇宙化学期刊, 388, 253-267.

- [322] Khan, M., Ludl, A. A., Bankier, S., Björkegren, J. L., and Michoel, T. (2024). 基于相关工具变量集的GWAS位点多效性基因调控效应因果基因预测. PLOS遗传学, 20(11), e1011473.

- [323] Ojala, K., and Zhou, C. (2024). 基于单目热成像图像的室外物体距离测定.

- [324] Popordanoska, T., and Blaschko, M. (2024). 推进深度学习中的校准：理论、方法与应用.

- [325] Alfieri, A., Cortes, J. M. P., Pastore, E., Castiglione, C., and Rey, G. M. Z. 面向带运输资源的作业车间调度的深度Q网络方法.

- [326] Zanardelli, R. (2025). 面向决策的统计学习方法及其在工业4.0中的应用.

- [327] Norouzi, M., Hosseini, S. H., Khoshnevisan, M., and Moshiri, B. (2025). 预训练CNN模型与数据融合技术在Unity3D面向联网车辆中的应用. 应用智能, 55(6), 390.

- [328] Wang, R., Yang, T., Liang, C., Wang, M., and Ci, Y. (2025). 可靠的自动驾驶环境感知：语义分割的不确定性量化. 交通工程期刊，A部分：系统, 151(3), 04024117.

- [329] Xia, Q., Chen, P., Xu, G., Sun, H., Li, L., and Yu, G. (2024). 嵌入强化学习与预览模型的自适应路径跟踪控制器，用于自动驾驶. IEEE车辆技术汇刊.

- [330] Liu, Q., Tang, Y., Li, X., Yang, F., Wang, K., and Li, Z. (2024). MV-STGHAT：面向联网与自动驾驶车辆决策的多视角时空图混合注意力网络. IEEE车辆技术汇刊.

- [331] Chakraborty, D., and Deka, B. (2025). 基于多模态无人机传感器测量的深度学习选择性特征融合荔枝果实检测. IEEE人工智能汇刊.

- [332] Mirindi, D., Khang, A., and Mirindi, F. (2025). 推动绿色交通系统的人工智能与自动化：全面综述. 推动绿色交通系统的人工智能与自动化：方法、技术与应用, 1-19.

- [333] Choudhury, B., Rajakumar, K., Badhale, A. A., Roy, A., Sahoo, R., and Margret, I. N. (2024年6月). 基于卫星的飞机识别高级模型比较分析. 载于《2024年面向电气、电子、通信与计算机工程的智能系统国际会议(ICSSECC)》(第483-488页). IEEE.

- [334] Almubarok, W., Rosiani, U. D., and Asmara, R. A. (2024年11月). 面向资源受限设备的鲇鱼分类MobileNetV2剪枝以提升效率. 载于《2024年第十届信息技术国际研讨会(ITIS)》(第271-277页). IEEE.

- [335] Ding, Q. (2024年2月). 基于深度学习的舌象分类技术. 载于《2024年第三届电气工程、大数据与算法国际会议(EEBDA)》(第802-810页). IEEE.

- [336] He, K., Zhang, X., Ren, S., and Sun, J. (2016). 图像识别的深度残差学习. 载于《IEEE计算机视觉与模式识别会议论文集》(第770-778页).

- [337] Krizhevsky, A., Sutskever, I., and Hinton, G. E. (2012). 基于深度卷积神经网络的ImageNet分类. 神经信息处理系统进展, 25.





- [338] Sultana, F., Sufian, A., and Dutta, P. (2018年11月). 使用卷积神经网络的图像分类进展。载于2018年第四届计算智能与通信网络研究国际会议(ICRCICN) (第122-129页). IEEE.

- [339] Sattler, T., Zhou, Q., Pollefeys, M., and Leal-Taixe, L. (2019). 了解基于CNN的绝对相机姿态回归的局限性。载于IEEE/CVF计算机视觉与模式识别会议论文集 (第3302-3312页).

- [340] Vaswani, A. (2017). 注意力就是你所需要的一切。神经信息处理系统进展.

- [341] Nanpegagu, M., Babu, D. B., and Madhuri, C. B. 利用混合AI模型：用于先进股市预测的DQN、Prophet、BERT、ART-NN和基于Transformer的方法.

- [342] De Rose, L., Andresini, G., Appice, A., and Malerba, D. (2024). VINCENT：通过视觉变换器和知识蒸馏进行网络威胁检测。计算机与安全, 103926.

- [343] Buehler, M. J. (2025). 面向变换器自适应动态的图感知同构注意力。arXiv预印本 arXiv:2501.02393.

- [344] Tabibpour, S. A., and Madanizadeh, S. A. (2024). 使用集合变换器求解高维动态规划。可在SSRN上获取 5040295.

- [345] Li, S., and Dong, P. (2024年10月). 用于超大规模MIMO系统的混合注意力变换器增强信道估计。载于2024年第16届无线通信与信号处理国际会议(WCSP) (第394-399页). IEEE.

- [346] Asefa, S. H., and Assabie, Y. (2024). 基于字符嵌入和组合正则化技术的阿姆哈拉语到英语的变换器机器翻译。IEEE Access.

- [347] Liao, M., and Chen, M. (2024年11月). 一种基于视觉变换器的新深度伪造检测方法。载于算法、高性能计算与人工智能国际会议(AHPCAI 2024) (第13403卷, 第953-957页). SPIE.

- [348] Jiang, L., Cui, J., Xu, Y., Deng, X., Wu, X., Zhou, J., and Wang, Y. (2024年8月). SC-Former：用于高质量PET图像重建的带对比学习的空间与通道变换器。载于2024年IEEE控制论与智能系统国际会议(CIS)和IEEE机器人、自动化与机电一体化国际会议(RAM) (第26-31页). IEEE.

- [349] Goodfellow, I., Pouget-Abadie, J., Mirza, M., Xu, B., Warde-Farley, D., Ozair, S., ... and Bengio, Y. (2014). 生成对抗网络。神经信息处理系统进展, 27.

- [350] CHAPPIDI, J., and SUNDARAM, D. M. (2024). 带图神经网络的双Q学习：一种用于挑战性生态系统中动物检测的新方法。理论与应用信息技术期刊, 102(23).

- [351] Joni, R. (2024). 深度学习探索：用于图像分析的照明技术与视觉清晰度 (No. 12808). EasyChair.

- [352] Kalaiarasi, G., Sudharani, B., Jonnalagadda, S. C., Battula, H. V., and Sanagala, B. (2024年7月). 图像隐写术综合调查。载于2024年第2届可持续计算与智能系统国际会议(ICSCSS) (第1225-1230页). IEEE.

- [353] Arjmandi-Tash, A. M., Mansourian, A., Rahsepar, F. R., and Abdi, Y. (2024). 基于机器学习的光电探测器响应度预测。高级理论与仿真, 2301219.

- [354] Gao, Y. (2024). 神经网络与应用数学的交汇：GAN、PINN和变换器。香港大学在线论文(HKUTO).

- [355] Hisama, K., Ishikawa, A., Aspera, S. M., and Koyama, M. (2024). 使用机器学习势和生成式人工智能进行氨合成多元合金催化剂的理论催化剂筛选。物理化学期刊C, 128(44), 18750-18758.

- [356] Wang, M., and Zhang, Y. (2024). 使用改进的生成对抗网络在复杂背景中进行图像分割。高级计算机科学与应用国际期刊, 15(5).

- [357] Alonso, N. I., and Arias, F. (2025). Q学习与汉密尔顿-雅各比-贝尔曼方程的数学。Fernando, Q学习与汉密尔顿-雅各比-贝尔曼方程的数学 (2025年1月5日).

- [358] Lu, C., Shi, L., Chen, Z., Wu, C., and Wierman, A. (2024). 通过近似分解克服强化学习中的维度灾难。arXiv预印本 arXiv:2411.07591.

- [359] Humayoo, M. (2024). Q学习中的时间尺度分离：扩展TD(Δ)以进行动作值函数分解。arXiv预印本 arXiv:2411.14019.

- [360] Jia, L., Qi, N., Su, Z., Chu, F., Fang, S., Wong, K. K., and Chae, C. B. (2024). 无线通信中抗干扰防御的博弈论与强化学习：当前研究、挑战与解决方案。IEEE通信调查与教程.

- [361] Chai, J., Chen, E., and Fan, J. (2025). 用于非平稳离线强化学习的深度迁移Q学习。arXiv预印本 arXiv:2501.04870.

- [362] Yao, J., and Gong, X. (2024年10月). 面向多智能体系统的通信高效且鲁棒的分布式深度强化学习。载于2024年IEEE无人系统国际会议(ICUS) (第1521-1526页). IEEE.

- [363] Liu, Y., Yang, T., Tian, L., and Pei, J. (2025). SGD-TripleQNet：车辆变道决策的集成深度强化学习模型。数学, 13(2), 235.

- [364] Masood, F., Ahmad, J., Al Mazroa, A., Alasbali, N., Alazeb, A., and Alshehri, M. S. (2025). 使用深度博弈论的6G智慧农业绿色通信多IRS辅助低碳电源管理。计算智能, 41(1), e70022.

- [365] Patrick, B. 动态经济模型的强化学习.

- [366] El Mimouni, I., and Avrachenkov, K. (2025年1月). 带惠特尔指数的深度Q学习用于上下文不安分盗贼：应用于电子邮件推荐系统。载于北极光深度学习会议2025.

- [367] Shefin, R. S., Rahman, M. A., Le, T., and Alqahtani, S. (2024). xSRL：安全感知可解释强化学习——安全作为可解释性的产物。arXiv预印本 arXiv:2412.19311.

- [368] Khlifi, A., Othmani, M., and Kherallah, M. (2025). 使用基于DDQN的深度强化学习实现自动驾驶的新方法.

- [369] Kuczkowski, D. (2024). 交通仿真的能量效率多目标强化学习算法.

- [370] Krauss, R., Zielasko, J., and Drechsler, R. 使用自适应突变的人工神经网络大规模进化优化.

- [371] Ahamed, M. S., Pey, J. J. J., Samarakoon, S. B. P., Muthugala, M. V. J., and Elara, M. R. (2025). 可重构机器人足球的强化学习。IEEE Access.

- [372] Elmquist, A., Serban, R., and Negrut, D. (2024). 一种用于量化自主机器人图像中仿真与现实差异的方法论。IEEE传感器期刊.

- [373] Kobanda, A., Portelas, R., Maillard, O. A., and Denoyer, L. (2024). 用于持续离线强化学习的策略分层子空间。arXiv预印本 arXiv:2412.14865.

- [374] Xu, J., Xie, G., Zhang, Z., Hou, X., Zhang, S., Ren, Y., and Niyato, D. (2025). UPEGSim：面向水下追逃游戏的无人水下车辆RL仿真器。IEEE物联网期刊, 12(3), 2334-2346.

- [375] Patadiya, K., Jain, R., Motheriya, J., Palaniappan, D., Kumar, P., and Premavathi, T. (2024年12月). 基于汽车游戏生成自动播放器模式的深度学习应用。载于2024年第16届计算智能与通信网络国际会议(CICN) (第233-237页). IEEE.

- [376] Janjua, J. I., Kousar, S., Khan, A., Ihsan, A., Abbas, T., and Saeed, A. Q. (2024年12月). 开放空间强化学习中的可扩展性增强。载于2024年决策辅助科学与应用国际会议(DASA) (第1-8页). IEEE.

- [377] Yang, L., Li, Y., Wang, J., and Sherratt, R. S. (2020). 基于情感词典和深度学习的中文电子商务产品评论情感分析。IEEE Access, 8, 23522-23530.

- [378] Manikandan, C., Kumar, P. S., Nikitha, N., Sanjana, P. G., and Dileep, Y. 使用自然语言处理过滤电子邮件.

- [379] ISIAKA, S. O., BABATUNDE, R. S., and ISIAKA, R. M. 探索预测医学中的人工智能(AI)技术：系统评述.

- [380] Petrov, A., Zhao, D., Smith, J., Volkov, S., Wang, J., and Ivanov, D. 文本数据中情感状态分类的深度学习方法.

- [381] Liang, M. (2025). 在虚拟教育环境中利用自然语言处理进行自动评估和反馈生成。科学与工程计算方法期刊, 14727978251314556.

- [382] Jin, L. (2025). 药学科普知识整合与传播的人工智能算法优化策略研究。技术科学期刊, 7(1), 45-55.

- [383] McNicholas, B. A., Madden, M. G., and Laffey, J. G. (2025). 危重症医学中的自然语言处理：机遇、挑战与未来方向。危重症医学, 1-5.

- [384] Abd Al Abbas, M., and Khammas, B. M. (2024). 使用循环神经网络的高效物联网恶意软件检测技术。伊拉克信息与通信技术期刊, 7(3), 29-42.




- [385] Kalonia, S., and Upadhyay, A. (2025). 基于深度学习的软件故障预测方法. 载于《人工智能与机器学习在可持续发展中的应用》(pp. 326-348). CRC Press.

- [386] Han, S. C., Weld, H., Li, Y., Lee, J., and Poon, J. 面向对话式AI的深度学习自然语言理解.

- [387] Potter, K., and Egon, A. 时间序列预测的循环神经网络 (RNN).

- [388] Yatkin, M. A., Köregesaar, M., and Işlak, Ü. (2025). 基于循环神经网络的机器学习一致性增强拓扑方法. 应用科学, 15(2), 933.

- [389] Saifullah, S. (2024). 基于深度学习的鸡蛋受精卵分类中LSTM和GRU模型的比较分析.

- [390] Noguer i Alonso, Miquel. 循环神经网络的数学 (2024年10月27日). 可在SSRN获取: https://ssrn.com/abstract=5001243 或 http://dx.doi.org/10.2139/ssrn.5001243

- [391] Tu, Z., Jeffries, S. D., Morse, J., and Hemmerling, T. M. (2024). 镇静下生理指标预测的时间序列模型比较. 临床监测与计算杂志, 1-11.

- [392] Zuo, Y., Jiang, J., and Yada, K. (2025). 基于室内定位系统的商店内轨迹预测中混合门控循环单元的应用. 科学报告, 15(1), 1055.

- [393] Lima, R., Scardua, L. A., and De Almeida, G. M. (2024). 使用神经网络预测钢坯再热炉内部温度. Authorea预印本.

- [394] Khan, S., Muhammad, Y., Jadoon, I., Awan, S. E., and Raja, M. A. Z. (2025). 基于LSTM-SMI和ARIMA架构的强健风力发电厂预测. 应用软计算, 112765.

- [395] Guo, Z., and Feng, L. (2024). 基于时空位置注意力LSTM的温室温湿度多步预测. 随机环境研究与风险评估, 1-28.

- [396] Abdelhamid, N. M., Khechekhouche, A., Mostefa, K., Brahim, L., and Talal, G. (2024). 基于物联网的光伏发电短时预测Deep-RNN模型. 工程与精确科学研究, 5(2), e11461-e11461.

- [397] Rohman, F. N., and Farikhsin, B. S. 糖尿病分类中随机森林算法的超参数调优.

- [398] Rahman, M. 利用机器学习技术进行早期脑肿瘤检测.

- [399] Nandi, A., Singh, H., Majumdar, A., Shaw, A., and Maiti, A. 通过类别平衡和模型调优利用深度学习优化婴儿声音识别.

- [400] Sianga, B. E., Mbago, M. C., and Msengwa, A. S. (2025). 使用机器学习算法预测心血管疾病患病率. 基于智能的医学, 100199.

- [401] Li, L., Hu, Y., Yang, Z., Luo, Z., Wang, J., Wang, W., ... and Zhang, Z. (2025). 通过整合可穿戴连续生理和临床数据探究心脏瓣膜手术后肺并发症风险评估. BMC医学信息学与决策, 25(1), 1-11.

- [402] Lázaro, F. L., Madeira, T., Melicio, R., Valério, D., and Santos, L. F. (2025). 基于自然语言处理和机器学习模型识别航空事故中的人为因素. 航空航天, 12(2), 106.

- [403] Li, Z., Zhong, J., Wang, H., Xu, J., Li, Y., You, J., ... and Dev, S. (2025). RAINER: 用于降雨模式预测的鲁棒集成学习网格搜索调优框架. arXiv预印本 arXiv:2501.16900.

- [404] Khurshid, M. R., Manzoor, S., Sadiq, T., Hussain, L., Khan, M. S., and Dutta, A. K. (2025). 揭示糖尿病发病: 用于增强预测的带贝叶斯优化的优化XGBoost. PloS one, 20(1), e0310218.

- [405] Kanwar, M., Pokharel, B., and Lim, S. (2025). 使用超参数优化和网格搜索技术的新随机森林方法用于滑坡易感性制图. 国际环境科学与技术杂志, 1-16.

- [406] Fadil, M., Akrom, M., and Herowati, W. (2025). 基于机器学习的喹诺林化合物腐蚀抑制预测. 应用信息学与计算杂志, 9(1), 173-177.

- [407] Emmanuel, J., Isewon, I., and Oyelade, J. (2025). 使用修改的差分进化优化算法的优化深度森林算法: 宿主-病原体蛋白-蛋白相互作用预测的一个案例. 计算与结构生物技术杂志.

- [408] Gaurav, A., Gupta, B. B., Attar, R. W., Alhomoud, A., Arya, V., and Chui, K. T. (2025). 基于鱼鹰和海鞘群优化的随机森林模型在先进交通系统中驾驶员识别. 科学报告, 15(1), 2453.

- [409] Ning, C., Ouyang, H., Xiao, J., Wu, D., Sun, Z., Liu, B., ... and Huang, G. (2025). 感染性胰腺坏死患者死亡率预测的可解释机器学习模型的开发与验证. eClinicalMedicine, 80.

- [410] Muñoz, V., Ballester, C., Copaci, D., Moreno, L., and Blanco, D. (2025). 使用秘书算法加速超参数优化. Neurocomputing, 129455.

- [411] Balcan, M. F., Nguyen, A. T., and Sharma, D. (2025). 具有结构化参数依赖双函数的神经网络中模型超参数数据驱动调优的样本复杂度. arXiv预印本 arXiv:2501.13734.

- [412] Azimi, H., Kalhor, E. G., Nabavi, S. R., Behbahani, M., and Vardini, M. T. (2025). 基于数据的超级电容器容量预测建模: 集成机器学习和元启发式算法. 台湾化学工程师学会杂志, 170, 105996.

- [413] Shibina, V., and Thaseema, T. M. (2025). 基于受自然启发的松鼠搜索算法和集成学习分类器的帕金森病语音特征诊断. 伊朗计算机科学杂志, 1-25.

- [414] Chang, F., Dong, S., Yin, H., Ye, X., Wu, Z., Zhang, W., and Zhu, H. (2025). 基于InSAR和机器学习的北向水库滑坡3D位移时间序列预测. 岩石力学与岩土工程杂志.

- [415] Cihan, P. (2025). 基于贝叶斯超参数优化的生物质气化气体预测机器学习模型. 应用科学, 15(3), 1018.

- [416] Makomere, R., Rutto, H., Alugongo, A., Koech, L., Suter, E., and Kohitlthetse, I. (2025). 使用具有超参数调优和数据增强的Python驱动计算框架增强干式SO2捕获估计. 非常规资源, 100145.

- [417] Bakr, H. (2025). 一种用于恶意软件检测的CNN预训练模型特征提取器调优新方法. 模式识别与应用, 28(1), 26.

- [418] Liu, Y., Yin, H., and Li, Q. (2025). 基于深度学习和超参数优化的多维亥姆霍兹共振器声吸收性能预测. Physica Scripta.

- [419] Ma, Z., Zhao, M., Dai, X., and Chen, Y. (2025). 基于混合正则化支持向量数据描述的高速加工异常检测. 机器人与计算机集成制造, 94, 102962.

- [420] El-Bouzaidi, Y. E. I., Hibbi, F. Z., and Abdoun, O. (2025). 优化卷积神经网络中超参数调优和迁移学习的影响. 载于《优化与机器学习创新》(pp. 301-326). IGI Global科学出版.

- [421] Mustapha, B., Zhou, Y., Shan, C., and Xiao, Z. (2025). 使用混合卷积和视觉变换器网络增强胸部X光片中的肺炎检测. 当前医学影像, e15734056326685.
