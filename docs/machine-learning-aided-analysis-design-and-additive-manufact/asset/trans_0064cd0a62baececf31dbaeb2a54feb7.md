

![](img/90ed165a39fa708ec438fcda79319c25_94_0.png)

**图 3.16** 2 型 FGP 循环板关于孔隙率的瞬态响应。

### 3.3.3 FGP 板的稳态响应

#### 3.3.3.1 验证示例

在此部分，首先对 CDQM 在 FGP 板稳态响应方面的应用进行了验证示例。图 3.17 显示了通过 CDQM 和 FEM 获得的 FGP 板稳态响应的对比结果，此时所有结构边缘均采用固定边界。如图 3.17 所示，CDQM 与 FEM 的位移曲线具有良好的一致性，证明了 CDQM 处理 FGP 结构稳态响应的正确性和通用性。

#### 3.3.3.2 稳态响应的参数化分析

基于 3.2.1 节中之前的验证，接下来的工作关注 FGP 结构稳态响应在不同孔隙系数和分布下的行为。通过图 3.18–3.20 评估了孔隙参数对 FGP 板稳态响应影响的定性规律。一方面，我们得出结论：无论分布和几何形状如何，不同的孔隙系数 $e_0$ 对位移幅的影响较小，而 2 型的位移幅通常大于 1 型。另一方面，对于 1 型孔隙分布，随着孔隙系数 $e_0$ 的增加，位移向高频移动，而这与 2 型孔隙分布的情况相反。此外，孔隙系数 $e_0$ 的影响程度对孔隙分布非常敏感，2 型孔隙分布引起的 $e_0$ 影响比 1 型分布显著得多。

具有复杂曲线边缘的功能梯度多孔四边形板的自由振动与受迫振动

![](img/90ed165a39fa708ec438fcda79319c25_95_0.png)

图 3.17 FGP 板稳态响应对比。

![](img/90ed165a39fa708ec438fcda79319c25_95_1.png)

图 3.18 FGP 四边形板关于孔隙参数的稳态响应。

![](img/90ed165a39fa708ec438fcda79319c25_95_2.png)

图 3.19 FGP 椭圆板关于孔隙参数的稳态响应。

功能梯度多孔复合结构

![](img/90ed165a39fa708ec438fcda79319c25_96_0.png)

**图 3.20** FGP 截圆板关于孔隙参数的稳态响应。

### 3.4 结论

建立了一个任意形状 FGP 板的通用理论模型，用于研究自由振动、瞬态和稳态响应。采用了谱谱切比雪夫法模拟虚拟弹簧的技术来模拟任意曲线边缘的各种约束。根据 FSDT 和 Lagrange–Ritz 方法得到了本构关系和能量方程。通过坐标变换和二维切比雪夫多项式，将 FGP 板的位移分量表示在称为计算区域的正方形区域。通过 Gauss–Lucas 迭代技术可以方便地获得 FGP 板振动的解。为了确认通用性和正确性，进行了一系列示例。结果，详细分析了孔隙系数和分布的影响，包括自由振动、瞬态响应和稳态响应。

### 致谢

作者感谢匿名评审员提供的宝贵反馈。作者还感谢感谢中国国家自然科学基金（资助号：52075554）、湖南省自然科学基金（2022J20070 和 2021J30841）以及中南大学创新驱动科研计划（资助号：2023CXQ049）的资金支持。本研究得到了中南大学直属高校基础研究经费（资助号：2022ZZTS0015）的支持。

### 参考文献

- [1] Chen Z, et al. Investigation on free vibration and transient response of functionally graded graphene platelets reinforced cylindrical shell resting on elastic foundation. Eur J Phys 2020;135(7).
- [2] Xue Y, et al. Free vibration analysis of porous plates with porosity distributions in the thickness and in-plane directions using isogeometric analysis. Int J Mech Sci 2019;12:546–62.
- [3] Tran TT, Pham Q-H, Nguyen-Thoi T. An edge-based smoothed finite element for free vibration analysis of Functionally Graded Porous (FGP) plates on Elastic Foundation Taking Into Mass (EFTM). Math Prob Eng 2020;2020:1–17.
- [4] Tran TT, Pham Q-H, Nguyen-Thoi T. Dynamic analysis of functionally graded plates resting on elastic foundation taking into mass subjected to moving loads using an edge-based smoothed finite element. SAE International 2020;2020:19
- [5] Tran TT, Pham Q-H, Nguyen-Thoi T. Static and free vibration of functionally graded variable-thickness plates using an edge-based smoothed finite element method. Def Tech 2021;17(9):771–86.
- [6] Tung PT, et al. Nonlinear bending analysis of fgp plates under various boundary conditions. Structures 2021;34:4803–13.
- [7] Xiao X, et al. Nonlinear in-plane instability of the confined fgp arches with nanocomposites reinforcement under directed-uniform pressure. Eng Struct 2022:252.
- [8] Yin Z, et al. An efficient scaled boundary element element in bending and analysis of functionally graded piezoelectric plates. Eng Anal Bound Mech 2021:113208:81.
- [9] Barati MR, Zenkour AM. Electromechanical vibration of plates functionally graded piezoelectric plates under various boundary conditions. J Vib Control 2016;64(4):1910–26.
