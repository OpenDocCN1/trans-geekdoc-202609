
随后，我们研究了监督学习的两种主要量子方法。核方法具有可解释性且与经典理论良好集成，而变分模型提供了更大的灵活性和适应性，特别是在数据和任务要求尚不完全明确的情况下。

在合成数据集和真实数据集上的实证基准表明，量子推理模型在特定情况下可以匹配或略优于经典基准，但尚未在大规模上证明优势。实际部署仍受到 `NISQ`（中等规模无量子）时代硬件的深度、噪声和可扩展性。

尽管如此，我们还回顾了几个应用案例研究——包括药物发现、高能物理和金融建模，在这些领域，量子模型正在被积极探索和测试。这些努力凸显了量子推理作为混合计算策略部分的潜力，特别是在数据稀缺或高维的场景下。

### 量子机器学习

最后，我们反思了开放的挑战和研究方向，从更好的量子特征映射设计到对量子设置下泛化和学习复杂性的深层理论理解。

## 参考文献

- [1] Schuld M and Petruccione F 2018 Supervised Learning with Quantum Computers (Cham: Springer International)
- [2] Havíček V, Coréles A, Demme K, Harrow AW, Kandala A, Chow J M and Gambetta J M 2019 Supervised learning with quantum-enhanced feature spaces Nature 567 209–212
- [3] Schuld M and Killoran N 2019 Quantum machine learning in Hilbert spaces Phys. Rev. Lett. 122 040504
- [4] Lloyd S, Schuld M, Thomsen A, Sutter D and Woerner S 2024 Quantum embedding for machine learning arXiv:2001.03622
- [5] Gentetta G, Thomas D and Woerner S 2024 The complexity of quantum support vector machines Quantum 8 1225
- [6] Giul-Fuster E, Eisert J and Duko V 2020 On the expressivity of embedding quantum kernels Mach.Learn. Sci. Tech. 5 025003
- [7] Wierch D, Izaac J, Wang C and Yen-Yu Lin C 2022 General parameter-rule shifts for quantum gradients Quantum 66 677
- [8] Schuld M, Bergholt V, Gogolin C, Izaac J and Killoran N 2019 Evaluating algorithms on quantum hardware Phys. Rev. A 99 032331
- [9] R N and Kumar S 2025 Enhanced quantum ensemble classification with shallow circuit and parallelism mechanism Concurr. Comput.: Pract. Exp. 37 e70166
- [10] Suzuki Y, Yano H, Gao Q, Uno S, Tanaka A, Akiyama M and Yamamoto N 2020 Analysis and synthesis of feature map for kernel-based quantum classifier Quant. Mach. Intell. 29
- [11] Schuld M, Fingeruther M and Petruccione F 2017 Implementing a distance-based classifier with a quantum interference circuit Europhys. Lett. 119 600002
- [12] Sen P, Bhatia A S, Bhangu K S and Elbgeti A 2022 Variational quantum classifiers through the lens of the hessian PLoS One 17 e062346
- [13] Hur T, Lim K and Park D 2022 Quantum convolutional neural network for classical data classification Quant. Mach. Intell. 4 3
- [14] Butmatharajaya S, Buesamae N and Taagragol U 2023 MNIST quantum classifier models implementations and benchmarking AI Conf. Proc. 2006 070002
- [15] Wang H, Ding Y, Gu J, Lin Y, Pan D, Chong FT and Han S 2022 QuantumQAS: noise-adaptive search for robust quantum circuits (HPCA) 2022 IEEE Int. Symp. on High-Performance Computer Architecture pp 692–708
- [16] Şkar S 2024 Quantum transfer learning for MNIST classification using a hybrid-classical approach arXiv:2408.03531
- [17] Ranga P, Rajapat A, Kumar P and Vasilakos A V 2024 Hybrid-classical neural networks for efficient MNIST binary image classification Mathematics 12 3684
- [18] Grant E, Benedetti M, Cao S, Hallam, Lockhart J, Stojevic V, Green A G and Severini S 2018 Hierarchical quantum classifiers npi Quantum Inf. 4 65
- [19] Khan D, Disenhof S and von Lindenfeld O 2023 Kernel-based quantum machine learning at recorded rate; many-body distribution functions as quantum representations J. Chem. Phys. 159 034106
- [20] Sathan D and Baicho S 2024 Drug target interaction prediction using variational quantum classifier 2024 Int. Conf. on Next Generation Computing Applications (NextComp) (Piscataway, NJ: IEEE) pp 1–7.
- [21] Paliwal D, Koteswara S N, Gudhanti R, Yadav D and Raj P 2024 Insight into quantum computing and deep learning approach for drug design Lett. Drug Des. Discov. 21 1632–1651
- [22] Gianelle A, Koppenberg P, Lucchesi D, Nicortra D, Rodrigues E, Sestini L, de Vrites J and Zuliani D 2022 Quantum machine learning for b-jet charge identification J. High Energy Phys. 2022 14
- [23] Wu S L et al 2021 Application of quantum machine learning using the quantum kernel algorithm on high energy physics at the LHC Phys. Rev. Res. 3 032221
- [24] Incudini M, Bosco D, Martini F, Grossi M, Serra G and Pierro A D 2024 Automatic and effective discovery of quantum kernels IEEE Trans. Emerg. Top. Comput. Intell. 1–10
- [25] Meglio A D et al 2024 Quantum computing for high-energy physics: state of the art and challenges PRX Quantum 5 037001
- [26] Miyabe S et al 2023 Quantum multiple kernel learning in financial tasks arXiv:2312.00260

其动力显而易见：由于希尔伯特空间随系统规模指数级增长，量子化学是经典计算机要求最高的应用领域之一。即使是中等分子，使用精确对角化或经典近似方案进行模拟也面临挑战。相比之下，量子计算机表示这些状态，而变分算法提供了一种可行路径，利用相对浅的电路来导航指数巨大的量子态空间。

`VQE` 之后，变分方法迅速引发了一波算法创新，导致了泛化拟态，例如用于更高效求解问题的`幺正耦合簇 (UCC)`，以及扩展到更广泛的问题类别，如使用`量子近似优化算法 (QAOA)` 进行组合优化。如今，变分算法已成为大多数实际量子应用的核心，涵盖了从化学、材料科学到金融和机器学习的多个领域。

## 5.1 模型描述

变分量子算法的工作原理是将问题编码到代价函数中，该函数可以在量子设备上进行评估，并通过经典优化进行最小化。变分算法的基本组成部分包括参数化量子电路（拟态）、用于评估代价的量子测量程序，以及更新参数的经典优化循环。这种混合反馈机制使得在硬件限制存在的情况下高效探索量子态成为可能。

设 $|\psi(\theta)\rangle = U(\theta)|\psi_0\rangle$ 表示由电路 $U(\theta)$ 准备的量子态，其中 $|\psi_0\rangle$ 是初始参考态。变分算法的目标是寻找参数 $\theta$ 以最小化特定问题的代价函数（通常是哈密顿算符 $H$ 的期望值），评估方法为：

$E(\theta) = \langle\psi(\theta)|H|\psi(\theta)\rangle$ (5.2)

该代价通过测量哈密顿分解中的项（通常是泡泡利算符之和）并在经典端进行组合来计算。

变分算法的两个主要子类——`VQE` 和 `QAOA`——说明了该框架在连续和离散优化设置中的灵活性。

### 5.1.1 变分量子本征求解器

`VQE` 作为一种实用的量子-经典混合算法被引入，用于估计量子哈密顿量的基态能量。其动力直接来源于量子力学中的变分原理：对于任何试探态 $|\psi\rangle$，量 $\langle\psi|H|\psi\rangle$ 是基态能量 $E_0$ 的上界。试探态越接近真实的基态，期望值就越低。

在 `VQE` 中，哈密顿量 $H$ 通常代表分子的电子结构，使用二量子化形式通过费米子产生符和湮灭算符表示。这些算符通过 Jordan-Wigner [4] 或 Bravyi-Kitaev [5] 等映射转换为比特算符。生成的比特哈密顿量是泡泡利矩阵张量积的加权和：

$H = \sum_{i \in \mathbb{R}} c_i P_i, \quad (5.3)$

其中 $P_i \in \{I, X, Y, Z\}^{\otimes n}$，$c_i$ 是由问题哈密顿量定义的系数。为了估计能量 $E(\theta)$，必须在量子硬件上测量每个项 $\langle \psi(\theta)|P_i|\psi(\theta)\rangle$ 并根据 $c_i$ 加权。所需的测量次数可能非常多，这促成了诸如测量分组 [6-8]、经典影子 [9, 10] 和基旋转分组 [11] 等策略，以减少测量开销。

拟态 $U(\theta)$ 在 `VQE` 的性能中起着核心作用。常见的选择包括：

- `硬件高效拟态 [12]`，它们使用原生门操作和纠缠层。
- `受问题启发的拟态`，例如化学中的 `UCC [13]` 拟态。
- `自适应拟态`，例如 `ADAPT-VQE [14]`，它根据算符梯度增长电路。

经典优化器可以是无梯度的（例如 `COBYLA [15]`, `Nelder-Mead [16]`）或基于梯度的（例如 `Adam [17]`, `L-BFGS [18]`），取决于取决于是否存在可用或可估计的解析梯度。

### 5.1.2 量子近似优化算法

`QAOA [19]` 是一种用于解决组合优化问题的变分算法。`QAOA` 通过将问题编码到经典代价函数 $C(z)$ 来工作，其中 $z \in \{0, 1\}^n$ 代表位串，并构造代价哈密顿量 $H$，其特征值对应于不同解的代价值。

为了探索解空间，`QAOA` 通过交替使用代价哈密顿量和混合哈密顿量 $H_M$ 生成的幺正变换定义参数化量子态，$H_M$ 通常选择为：

$H_M = \sum_{j=1}^n X_j, \quad (5.4)$

这诱导了位串之间的转换。`QAOA` 态定义为：

$|\psi(\gamma, \beta)\rangle = \prod_{j=1}^p e^{-i\beta_j H_M} e^{-i\gamma_j H_C}|\psi_0\rangle, \quad (5.5)$

其中 $p$ 是深度或 `QAOA` 层数，$\gamma, \beta \in \mathbb{R}^p$ 是变分参数。初始态 $|\psi_0\rangle$ 通常是所有位串的叠加，通过对每个比特应用哈达玛门制备。最终量子态 $|v(\gamma, \beta)\rangle$ 编码了解的概率分布，目标是通过最小化期望值来最大化代价函数

$\langle v(\gamma, \beta)|H_c|v(\gamma, \beta)\rangle.$ (5.6)

## 5.2 案例研究与应用

变分算法的灵活性和混合结构使其能够在广泛的领域中应用。这些应用利用了算法近似复杂量子态或优化代价函数的能力。两个最著名的领域——量子化学和组合优化——分别是 `VQE` 和 `QAOA` 的动机问题。自此以后，变分算法的应用显著扩大，包括量子机器学习、量子控制和量子误差消除。

### 5.2.1 量子化学与材料科学

变分算法最具影响的短期应用可能在于模拟分子系统。`VQE` 已用于估计小分子的基态能量，如 `H2` [24]、`LiH` [25]、`BeH` [26] 和 `H2O` [27]，为早期量子硬件提供了基准。在这些问题中，分子哈密顿量从第一性电子结构理论推导出来，然后通过 Jordan-Wigner 或 Bravyi-Kitaev 等映射转换为比特表示。

这些量子模拟特别有前景，因为具有此类配置作用（`FCI`）的经典方法随系统规模指数级增长。`VQE` 提供了一种多项式缩放的替代方案，前提是能够找到并训练合适的拟态。在最近的工作中，自适应方法和受拟态启发的 `UCC` 等构造提高了准确性同时减少了电路深度。材料科学应用（例如建模配合物或强关联系统）也在探索中，尽管它们需要更高保真度的设备和更深的电路，而目前在大多数硬件上是不可行的。

### 5.2.2 组合优化

`QAOA` 专门为解决经典的组合优化问题设计，这些问题在计算机科学、运筹学、物流和金融领域无处不在。这些问题通常涉及在约束条件下对离散变量的代价函数进行优化。示例：

#### 量子机器学习

- `最大割切（MaxCut）`：寻找图的划分方式，使得两个划分区域之间的边边数量最大化 [20, 28]。
- `最大独立集（Maximum independent set）`：识别图中最大的互相邻节点集合 [22]。
- `顶点染色与图染色（Vertex color and graph coloring）`：与资源分配和调度相关 [29, 30]。
- `旅行推员问题（Traveling salesman problem）`：经典的路线优化问题 [31, 32]。

在这些应用中，问题被编码进对角哈密顿量 $H_c$ 中，而 `QAOA` 通过交替应用 $H_c$ 和混合哈密顿量 $H_d$ 生成参数化的量子态。随后使用经典后处理来提取与候选解相对应的结果。

尽管 `QAOA` 必须在现实基准测试中优于经典算法，但它在小型问题实例上展示了潜力，特别是在可以使用问题特定结构或初始化策略的设置下。针对热启动 `QAOA`、逐层训练和优化景图分析的持续研究旨在提高其可扩展性和训练性。

### 5.2.3 量子机器学习

变分框架已扩展到机器学习任务中，其目标不再是寻找基态，而是训练量子模型来执行分类、回归或生成建模。在这种背景下，变分电路充当可训练模型——类似于神经网络——通过更新其参数来最小化定义在经典或量子数据上的损失函数。

另一个极具前景的方向是构建量子分类器，通过训练变分电路来对经典或量子输入进行标记。这些分类器可以被视为神经网络的量子模拟，其参数化门门层和纠缠操作作为非线性变换。量子神经网络的架构和训练将是下一章（第6章）的主题，在该章中我们将讨论它们的结构、表达能力以及在量子学习理论中的作用。

另一个应用是量子生成建模，通过训练变分电路来产生目标分布的统计特性。这些方法特别适用于量子硬件，因为生成过程本质上是概率性的。我们将在随后的第 7 章中详细探索这些模型，该章节将关注量子机器学习中的生成建模。
