
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

## 14 致谢

作者承认那些奠基性工作塑造了我们对深度学习理解的研究人员的贡献。

## 参考文献

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

