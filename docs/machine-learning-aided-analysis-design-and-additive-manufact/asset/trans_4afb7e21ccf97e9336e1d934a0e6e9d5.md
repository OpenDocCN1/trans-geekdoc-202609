

FG 多孔复合材料结构

![](img/90ed165a39fa708ec438fcda79319c25_311_0.png)

图 12.7 情况 B 第一阶阶频率的预测 (A) PDF 和 (B) CDF。

![](img/90ed165a39fa708ec438fcda79319c25_311_1.png)

图 12.8 情况 B 第二阶阶频率的预测 (A) PDF 和 (B) CDF。

## 12.5.3 熔融多孔无人机基座结构

第二个示例涉及用于四旋翼机的 FGP 无人机基座结构，其几何形状如图 12.9 所示。FGP 的厚为 1 cm，材料属性从底部到顶部变化。FGP 基座的金属和陶瓷部分由钢和氧化铝（Al2O$_3$）组成。基座的四个端固定，并对基座进行了随机有限元（FEM）分析。通过 FEM 计算，讨论了 FGP 不同网格的收敛性，并选择收敛最好的网格尺寸为 $h_{min}=0.1cm$。

为了增强 MLA-SFV 框架的有效性，研究了代表两种孔隙率分布的情况 A 和情况 B。同样，考虑了 FGP 基座顶部和底部弹性模量、密度和泊松比的不确定性信息，材料属性的变异输入数据列于表 12.6 中。

![](img/90ed165a39fa708ec438fcda79319c25_312_0.png)

**图 12.9** (A) 功能梯度多孔无人机基座的几何形状。(B) 采用采用有限元网格划分。

### 表 12.9 功能梯度多孔无人机基座的变异输入数据。

| 变异输入 | 分布类型 | 平均值 | 标准差 |
|---|---|---|---|
| $E_1$ (GPa) | 对数正态 | 380 | 19 |
| $E_2$ (GPa) | 对数正态 | 210 | 10.5 |
| $\rho_1$ (kg/m³) | 正态 | 7480 | 374 |
| $\rho_2$ (kg/m³) | 正态 | 3800 | 190 |
| | 对数正态 | 0.3 | 0.015 |

再次，为了建立合适的回归模型，对两种机器学习算法采用了不同的训练尺寸，并在图 12.10 中使用 $R^2$ 和 RMSE 的数学指标来测试准确性。从图中可以看出，对于情况 A 和情况 B，X-SVR 的训练样本量确定为 100，GPR 方法确定为 200。

为了说明 GPR 和 X-SVR 机器学习算法的回归差异，为情况 A 和情况 B 提供了这两种方法的对比测试。从两种方法预测的 FGP 基座第一、第三阶阶频率列在表 12.7 和表 12.8 中。同时，选择 100 万次模拟循环的粗略方法作为参考结果进行验证。

从表中可以看出，MLS-SFV 框架能够提供可靠的结果。与 MCS 结果相比，GPR 方法的绝对最大 RE 为 0.552%，而 X-SVR 方法的 RE 为 0.0379%。尽管与传统的 MCS 方法相比，两种机器学习算法都减少了大量的计算时间，但仍为 FGP 基座结构提供了准确的阶频率。

此外，两种方法在情况 A 和情况 B 下两个阶频率的 PDF 和 CDF 绘制在图 12.11–12.14 中，与……对比

![](img/90ed165a39fa708ec438fcda79319c25_313_0.png)

**图 12.10** 高斯过程回归和扩展支持向量回归估计的 (A) $R^2$ 和 (B) RMSE。

### 表 12.7 情况 A 中不同阶阶频率 (Hz) 的估计值。

| | 情况 A | | | | | |
|---|---|---|---|---|---|
| | MCS | X-SVR | RE (%) | GPR | RE (%) |
| **平均值** | | | | | | |
| 第一 | 1.732e–3 | 1.731e–3 | –0.0577 | 1.730e–3 | –0.1155 |
| 第三 | 5.354e–3 | 5.352e–3 | –0.0374 | 5.357e–3 | –0.0560 |
| **标准差** | | | | | | |
| 第一 | 0.953 | 0.951 | –0.2099 | 0.948 | –0.5247 |
| 第三 | 1.624 | 1.629 | 0.3079 | 1.633 | 0.5542 |

### 表 12.8 情况 B 中不同阶阶频率 (Hz) 的估计值。

| | 情况 B | | | | | |
|---|---|---|---|---|---|
| | MCS | X-SVR | RE (%) | GPR | RE (%) |
| **平均值** | | | | | | |
| 第一 | 1.621e–3 | 1.622e–3 | 0.0617 | 1.627e–3 | 0.3701 |
| 第三 | 3.872e–3 | 3.874e–3 | 0.0517 | 3.877e–3 | 0.1291 |
| **标准差** | | | | | | |
| 第一 | 0.941 | 0.943 | 0.2125 | 0.946 | 0.5313 |
| 第三 | 1.436 | 1.439 | 0.2089 | 1.443 | 0.4875 |![](img/90ed165a39fa708ec438fcda79319c25_314_0.png)

**图 12.11** 情况 A 第一阶阶频率的预测 (A) PDF 和 (B) CDF。(img/90ed165a39fa708ec438fcda79319c25_314_1.png)

**图 12.12** 情况 A 第三阶阶频率的预测 (A) PDF 和 (B) CDF。(img/90ed165a39fa708ec438fcda79319c25_314_2.png)

**图 12.13** MCS 方法的预测 (A) PDF 和 (B) CDF。从图中可以看出，机器学习算法预测的情况 A 两个阶频率的 PDF 和 CDF 与参考结果良好一致。此外，情况 B FGP 基座的可靠 PDF 和 CDF 证明了机器学习辅助分析的准确性和适用性。通过两个案例，MLA-SFV 框架的预测能力说明了机器学习辅助分析在实际工程中的潜力。

## 12.6 结论

在本章中不同的机器学习算法研究了 FGP 板结构的随机振动分析。为了获得随机输入与结构输出之间的内在关系（例如特征值），提出了基于核的 GPR 方法和带有基函数的 X-SVR 方法。通过计算有限的有限元分析作为训练数据，可以建立相应的回归模型并预测任何阶结构频率的详细统计信息（例如平均值、标准差）和概率分布（例如 PDF 和 CDF）。为了说明所提框架的稳健性，实施了一个验证案例和两个实际 FGP 板案例。结果表明，与 GPR 方法相比，X-SVR 方法仅需少量训练资源即可高效预测 FGP 板的阶频率。此外，机器学习辅助不确定性量化技术具有计算成本优势，可以应用于现实工程领域。

## 致谢

本文的工作得到了澳大利亚研究委员会项目 HI20010010、DP210101353、BH21010048 和 BH15010006 以及中国留学基金委员会（2017062006）的支持。研究在澳大利亚国家计算基础设施（NCI）提供的资源协助下完成。

## 参考文献

- [1] Karsh PK. Mukbhopadhyay T, Dey S. Stochastic low-velocity impact on functionally graded plates: probabilistic and non-probabilistic uncertainty quantification. Compos B Eng 2019;159:41–80. 
- [2] Koizumi M. In Japan. Compos B Eng 1997;28:1–4.
- [3] Ferrari J, Graham-Bray LL. Stochastic simulation of non-Gaussian/non-stationary properties in a functionally graded plate. Comput Methods Appl Mech Eng 2005;194:1675–92.
- [4] Kieback B, Reander A, Riedel H. Processing techniques for functionally graded materials. Mater Sci Eng 2003;36:2861–81.
- [5] Chen D, Yang J, Kitchoupas S. For forced vibrations of shear deformable functionally graded beams. Struct Mech 2016;109:148–22.
- [6] Yang J, Lee KM, Kitrimoulos S. Second-order statistics of the elastic buckling of functionally graded rectangular plates. Compos Sci Technol 2005;65:1165–75.
- [7] Shaker A, Abdelrahman R, Tawfik M, Sadek E. Stochastic finite element analysis of the free vibration of functionally graded materials. Comput Mech 2004;41:170–14.
- [8] Shogkar NL, Lal A. Stochastic nonlinear bending of piezoelectric functionally graded beam by optomechanical loadings with random properties. Compos Struct 2013;101:290–300.
- [9] Gibson LJ, Ashby ME. Cellular solids: structure and properties. Cambridge, UK: Cambridge University Press 1996.
- [10] Sofi A, Musciello G. Prediction of uncertainty structural properties by imprecise probability density functions via response surface method. Probab Eng 2020;60:10320.
- [11] Malik MH. ANN prediction for composite plates against low velocity impact both using finite element analysis. Compos Struct 2013;101:290–300.
- [12] Schulz E, Spbek M, Krause A. On Gaussian process regression: modeling, exploration, and exploiting functions. J Math Phys 2019;85:1–16.
- [13] Feng Y, Wang Q, Lu J, Chen X, Zhang T, et al. learning aided physics method for fracture mechanics of composite materials. Mater Sci 2021;161:103587.
- [14] Feng Y, Wang Q, Wu D, Gao W. Stochastic nonlocal damage analysis by a machine learning approach. Comput Methods Appl Mech Eng 2020;372:113371.
- [15] Wapnik V.N. An Overview of Statistical Learning Theory, 1999:10.
- [16] Igusa T, Buonaparte SG, Ellington BR. Bayesian analysis of uncertainty for structural engineering applications. Struct Saf 2002;24(2):165–86.

