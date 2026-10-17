
# 基于深度学习的正向建模与反演技术

![](img/020125e0e698f9771fbbd32f2ace1e80_82_0.png)

**图 2.26** 被动案例基础数据集中的数值示例。(a) 物体的材料（标签 0-3 的热物理属性见表 2.3），(b) 商业软件 COMSOL 计算的温度分布，(c) 网络预测的温度分布，(d) (b) 和 (c) 之间的绝对误差。

$N$ 是像素的数量（$N=32768$）。通过这一标准，基础数据集、增强数据集和开源数据集的平均误差分别为 $0.504\%$、$1.92\%$ 和 $2.91\%$。然而，整个数据集的平均误差仅衡量了结果。在本方案中，对结果进行了统计分析。这里，引入图 2.29 的提琴图来描述三个数据集的相对误差。

![](img/020125e0e698f9771fbbd32f2ace1e80_83_0.png)

# U-Net 在三维稳态热传导中的应用

**图 2.27** 被动案例增强数据集中的数值示例。(a) 物体的材料，(b) 商业软件 COMSOL 计算的温度分布，(c) 网络预测的温度分布，(d) (b) 和 (c) 之间的绝对误差。

![](img/020125e0e698f9771fbbd32f2ace1e80_84_0.png)

**图 2.28** 被动案例开源数据集中的数值示例。(a) 物体的材料（标签 0-3 的热物理属性见表 2.3），(b) 商业软件 COMSOL 计算的温度分布，(c) 网络预测的温度分布，(d) (b) 和 (c) 之间的绝对误差。

![](img/020125e0e698f9771fbbd32f2ace1e80_84_1.png)

**图 2.29** 三个数据集（被动案例）的提琴图。

![](img/020125e0e698f9771fbbd32f2ace1e80_85_0.png)

**图 2.30** 主动案例的训练曲线。

### 2.3.6 主动案例

- * 训练

在情况下，分别对基础数据集和增强数据集进行了训练。图 2.30 展示了训练集和测试集的损失。

- * 数值结果

从图 2.29 可以获得，基础数据集的平均误差高度集中在平均值附近。对于增强数据集，有少数大误差样本。由于开源数据集的高度复杂性，误差分布相对离散；这里所有样本的误差均小于 10%，这有力地证明了网络的鲁棒性。

## 72 基于深度学习的前向建模与反演技术

![](img/020125e0e698f9771fbbd32f2ace1e80_86_0.png)

图 2.31
激活状态下基础数据集的数值示例。(a) 物体的材料和热源（标签 0-3 的热物理属性如表 2.3 所示，而标签 4 为热源），(b) 由商业软件 COMSOL 计算的温度分布，(c) 由网络预测的温度分布，(d) (b) 和 (c) 之间的绝对误差。增强数据集中，图中的 (b)、(c) 和 (d) 分别代表由商业软件 COMSOL 计算的温度分布、由框架预测的温度分布以及绝对误差。

可以得出结论，该框架的预测结果与 COMSOL 的计算结果一致，因为误差非常微小。

- * C. 泛化能力

在激活场景中，还引入了一个开源数据集。数据集中的每个样本都包含具有不同热源的多种材料，这对预训练网络来说很难处理。

![](img/020125e0e698f9771fbbd32f2ace1e80_87_0.png)

**图 2.32**
激活状态下增强数据集的数值示例。(a) 物体的导热系数，(b) 由商业软件 COMSOL 计算的温度分布，(c) 由网络预测的温度分布，(d) (b) 和 (c) 之间的绝对误差。

图 2.33 展示了从开源数据集中随机取的三个示例。这里，(a) 显示了几何形状、材料类型（标签 0-3 的热物理属性如表 2.3 所示）和热源（标签为 4），(b) 和 (c) 分别是 COMSOL 计算和网络预测的温度分布，图中展示了 (b) 和 (c) 之间的误差。待测试的网络是在基础数据集上训练的。虽然误差比被动情况略大，但考虑到数据集的复杂性，它仍然处于接受范围内。可以得出，尽管框架从未遇到过类似的样本，但它仍然给出了相对准确的预测，这充分证明了框架的鲁棒性。

## 基于深度学习的前向建模与反演技术

![](img/020125e0e698f9771fbbd32f2ace1e80_88_0.png)

**图 2.33** 激活状态下开源数据集的数值示例。(a) 物体的材料和热源（标签 0-3 的热物理属性如表 2.3 所示，而标签 4 为热源），(b) 由商业软件 COMSOL 计算的温度分布，(c) 由网络预测的温度分布，(d) (b) 和 (c) 之间的绝对误差。

- - D. 统计分析

尽管激活场景的几何形状与被动情况相似，但额外的内部热源对误差有一定影响。观察到热源附近的温度发生了突变变化。然而，框架倾向于输出平滑函数，因此预测结果在热源表面存在一定的误差。为了分析源表面积的影响，计算并记录了几个不同热源的平均误差率，结果如表 2.6 所示。表 2.6 中的每个类别均从激活测试集中随机选取的 100 个样本组成。显然，热源面积与相对误差之间呈正相关。

利用小琴图展示了三个数据集的相对误差。从图 2.34 可以发现，基础数据集和增强数据集的平均误差都集中在平均值附近，而开源数据集的误差分布相对分散。由于大多数样本的误差小于 10%，网络的鲁棒性得到了证明。

## 表 2.6
不同表面积 $A$ 的热源平均误差率。

| $A(m^2)$ | 误差 | $A(m^2)$ | 误差 |
|---|---|---|---|
| 0.54 | 1.85% | 0.96 | 3.78% |
| 0.66 | 2.91% | 1.10 | 4.25% |
| 0.78 | 3.10% | 1.12 | 4.25% |
| 0.80 | 3.21% | 1.30 | 4.80% |
| 0.94 | 3.74% | 1.50 | 6.03% |

![](img/020125e0e698f9771fbbd32f2ace1e80_89_0.png)

## 图 2.34
三个数据集（被动情况）的小琴图。

### 2.3.6.3 计算加速

众周知，深度学习技术的主要动力之一是它通过充分利用 GPU 的并行计算能力使得同时预测温度场成为可能。在这部分，研究了神经网络与传统 FEM 求解器在计算速度上的对比。为了确保结果的严谨性，对比了两种方法在相同误差下的时间。当网格足够密集时，FEM 求解器产生准确的解。此时，$N_g$ 约为 $10^6$，随着网格数量增加，误差逐渐增大。如图 2.35 所示，框架揭示了关系。实验中，

## 76 基于深度学习的前向建模与反演技术

![](img/020125e0e698f9771fbbd32f2ace1e80_90_0.png)

### 图 2.35 误差与网格数量的关系

### 图 2.35 误差与网格数量的关系

当网格约为 16000 时，求解时间为 4.5 s。网格减少到 370 和 1420，误差分别为 0.1% 和 4.2%。对于被动和激活情况，分别为 0.58% 和 3.79%。考虑到神经网络只需要 0.015 s 即可获得相同的精度，可以得出其比 FEM 求解器加速了两个数量级。图 2.36 (a) 显示了框架的的对比。由于训练需要 30 分钟而数据生成需要 14 小时，总耗时如图 2.36 (b) 所示。然而，由于这些步骤是一次性的，不会随着样本数量增加而需要更多时间，神经网络在预测大量数据方面的优越性显而易见。

![](img/020125e0e698f9771fbbd32f2ace1e80_91_0.png)

**图 2.36** FEM 求解器的计算时间。(a) 训练良好的框架与 FEM 求解器的时间对比，(b) 框架与 FEM 求解器的总时间对比。

## 2.4 结论

在本章中，构建了一个基于 U-net 的深度学习框架，用于预测具有复杂几何形状和热属性的三物体温度场。研究了被动和激活场景。在计算精度效率方面，该框架表现出了明显的优点。为了更详细地分析深度学习模型，引入了三个数据集（基础数据集、增强数据集和开源数据集）。实验结果证实了该模型能够比传统算法 FEM 快两个数量级给出温度场的精确预测。此外，在基础数据集上训练的模型具有优异的泛化能力，证明了框架的鲁棒性。因此，凭借其卓越的加速性能和鲁棒的泛化能力，该框架为在广泛工程领域应用 3D 稳态热传递求解器提供了指南。

## 参考文献

+ [1] R.J. Goldstein, W.E. Ibele, S.V. Patankar, T.W. Simon, T.H. Kuhn, P.J. Strykowski, K.K. Tamma, J.V.R. Herberlein, J.H. Davidson, J. Bischof, F.A. Kulacki, U. Kortshagen, S. Garrick, V. Srinivasan, K. Ghosh, and

## 基于深度学习的正向建模与反演技术

[1] R. Mittal. Heat transfer—a review of 2004 literature. International Journal of Heat and Mass Transfer, 53(21):4343–4396, 2010.

[2] Pradip Majumdar. Computational Fluid Dynamics and Heat Transfer. CRC Press, Boca Raton, 2021.

[3] Y. Jaluria. Computational Heat Transfer. CRC Press, Inc. Boca Raton, USA, 2004.

[4] Y. Jaluria and K. E. Terrance. Computational heat transfer. Journal of Pressure Vessel Technology, 109(2):262–262, 1987.

[5] T. Myint and L. Debnath. Method of Separation of Variables, pages 231–272. Birkäuser, Boston, MA, 2007.

[6] Brett Norden and James Loscombe. Separation of variables. In Essential Mathematics for the Physical Sciences, 2053–2571, pages 2–1 to 20. Morgan & Clay Publishers, San Rafael, 2017.

[7] Willard Miller. Symmetry and Separation of Variables. Encyclopedia of Mathematics and its Applications. Cambridge University Press, Cambridge, 1984.

[8] I. Stakold and M. Holm. Green's Functions (Intuitive Ideas), chapter 1, pages 51–90. John Wiley & Sons, Ltd, Hoboken, NJ, 2011.

[9] Homayoon Beigi. Integral Transforms, pages 647–771. Springer US, Boston, MA, 2011.

[10] R.M. Gotta and D.M. Mikhailov. Integral transform method. Applied Mathematical Modelling, 17(3):156–161, 1993.

[11] Sineshash Chakraverty, Nisha Mahato, Perumanda Karunakar, and Tharasi Dillhese Rao. Numerical and Semi-Analytical Methods for Differential Equations, Chapter 2: Integral Transforms, pages 19–29, John Wiley & Sons, Hoboken, NJ, 2019.

[12] Sandip Mazumder. Chapter 2 - The finite method in. Sandip Mazumder, editor, Numerical Methods for Partial Differential Equations, pages 51–101. Academic Press, London, 2016.

[13] Randall LeVeque. Finite Difference Methods for Ordinary and Partial Differential Equations: Steady-State and Time-Dependent Problems (Classics in Applied Mathematics Classics in Applied Mathemat). Society for Industrial and Applied Mathematics, Philadelphia, USA, 2007.

[14] G.R. Liu and S.S. Quek. Chapter 3 - Fundamentals for finite element method. In G.R. Liu and S.S. Quek, editors, The Finite Element Method (Second Edition), pages 43–79. Butterworth-Heinemann, Oxford, second edition edition edition, 2014.

## U-Net在3D稳态热传导求解器应用

- [15] Singuresu S. Rao, editor, Chapter 16 – Three-dimensional problems. In Singuresu S. Rao, *The Finite Element Method in Engineering (Sixth Edition)*, pages 569–586. Butterworth-Heimann, Oxford, 2018.
- [16] R.W. Clough. The Finite Element Method in Plane Stress Analysis. In *ASCE Conf. on Electronic Comput.*, volume 23, page 345, 1960.
- [17] W. B. Zimmermann. *Multiphysics Modeling with Finite Element Methods*. World Scientific Publishing, Hackensack, NJ, USA, 2006.
- [18] Randall J. LeVeque. *Finite Volume Methods*, pages 64–86. Texts in Applied Mathematics. Cambridge University Press, Cambridge, 2002.
- [19] Olaf Kolditz. *Finite Volume Method*, pages 173–190. Springer, Berlin, Heidelberg, 2002.
- [20] Ian Goodfellow, Yoshua Bengio, and Andrew Courville. *Deep Learning*. MIT Press, Cambridge, 2016. http://www.deeplearning.org.
- [21] Francois Collet. *Deep Learning with Python*. Manning Publications Co., USA, 1st edition, New York, 2017.
- [22] Athanasios Voloudimos, Nicholas Daoulas, Anastasios Dalamis, Eftychos Protopapadakis, and Diego Andina. Deep learning for vision: a brief review. *Intelligence Neuroscience*, 2018, January 2018.
- [23] Li Deng and Yang Lu. *Deep Learning in Natural Language Processing*. Springer Publishing Company, Incorporated, 1st edition, Singapore, 2018.
- [24] Yinpeng Wang and Qi Ren. Sophisticated electromagnetic scattering solver based on deep learning. In *2021 International Applied Computational Electromagnetics Society Symposium (ACES)*, pages 1–3, 2021.
- [25] S. Q., Y. Li, X. Wu, and Y. Ren. Two-Dimensional Magnet Solver Based on Deep Learning Technique. *IEEE Journal on Multiscale and Multiphysics Computational Techniques*, 5:83–88, 2020.
- [26] Y. Li., Y. Wang, S. Qi., Q. Ren, L. Kang, S. D. Campbell, P. L. Werner, and D. H. Werner. Predicting Scattering from Complex Nano-Structures via Deep Learning. *IEEE Access*, 8:13993–13999, 2020.
- [27] Yinpeng Wang, Jianmei Zhou, Qi Ren, Yaoyao Li, and Donglin Su. 3-d steady heat conduction solver via deep learning. *IEEE Journal on Multiscale and Multiphysics Computational Techniques*, 6:100–108, 2021.
- [28] Jiang-Zhou Peng, Xianglei Li, Nadine Aubry, Zhihua Chen, and TaoWWu. Data-driven modeling of geometry-adaptive steady heat transfer based on convolutional neural networks, Case Studies in Thermal Engineering, 28:101651, 2021.

## 基于深度学习的正向建模与反演技术

[29] Behzad Zakeri, Amin Karimi. Deep learning of propagation on 3d domain. In Mahdi Gholi, Bahram Sadeghi, and Ebrahim Ansari, editors, Data Science: From Research to Application, pages 161–174, Springer, 2020.

[30] M. Edalatif, M. Tavakoli, and F. Ghalambaz. Deep learning to learn physics of heat transfer. Journal of Thermal Analysis and Calorimetry, 1–18, Jul, 2020.

[31] Y. Li, H. Wang, and X. Deng. Image-based reconstruction for 3D heat transfer problem. International Journal of Heat and Transfer, 134:656–667, May 2019.

[32] Mao Ma, Xiangyu Hu, Nils Thuerey, and Oskar Jaidn. A combined data-driven and physics-driven method for steady heat transfer using convolutional neural networks, arXiv:2005.08119, 2020.

[33] O. Ronneberger, P. Fischer, and T. Brox. U-net: Convolutional Networks for Biomedical Image Segmentation. In Proc. Int. Conf. Med. Image Comput.-Assist. Intervent., pages 234–241, Oct 2015.

[34] K. He, X. Zhang, S. Ren, and J. Sun. Deep Residual Learning for Image Recognition. In IEEE Conf. Computer Vision and Pattern Recognition Computer Society, pages 770–778, 2016.

[35] M. Abadi, P. Barham, J. Chen, and X. Zhang. Tensorflow: A System for Large-Scale Machine Learning. In 12th Symp. Des. Implement. (OSDI), pages 265–283, Nov. 2016.

# 3 复杂表面热通量的反演
## 基于 ConvLSTM

## 3.1 引言

标准热传导问题是指求解给定物体几何形状、热物理参数、初始条件和边界条件的内部分布及演变过程的过程。反向热传导问题（IHCP）是利用实验手段测量物体内部或边界某些点的温度及其随时间变化的历史，并利用热传导方程反演热通量或热传导系数。表面热通量的反演是典型的反演问题之一，在航天、核物理、冶金等工业研究领域具有广泛应用[1, 2]。

以航天[3]为例，当穿天飞机和航天器进入大气层时，其结构与空气摩擦会在表面产生大量热能，导致强烈的气动加热效应。表面热通量会沿结构向内传递，影响飞行结构的静态和动态特性。因此，在实际飞行过程中准确掌握飞行器面临的热荷对于飞行结构的设计和评估具有重要意义。然而，直接测量表面热荷面临一些困难：一方面，飞行器工作在力/热/振动/噪声等复杂环境中，外部探测的热通量易受多场负载环境的影响；另一方面，在表面防护结构中集成传感器较为困难，这种方法虽然有效但对防护结构影响较小，且该方法只能记录飞行期间的温度，难以准确揭示温度变化的历史特征。近年来开发的负载反演方法已成为

# 82 基于深度学习的前向建模与反演技术

通过在再入飞行器内部布置温度传感器并测量其内部温度，然后求解反热传导问题以获取外壁热载荷，是一种有效的方法。

## 3.2 反演研究的进展

### 3.2.1 传统方法

作为一种典型的病态问题[4]，热传导反问题对确定解数据的扰动极其敏感[5]。在过去的几十年，学者们通过各种方法进行了相关研究。在所有算法中，解析法最为准确，且没有理论误差[6, 7]。以一维平板为例[8]，可以使用级数展开法来重构边界热通量温度。

假设有一个均匀的无限板，在其外表面施加热通量。外面的温度和热流可以从内表面测得的时域温度 `T_0(t)` 和热通量值 `g_0(t)` 获得。显然，板上的所有点都满足被动热传导方程：

$$\rho C_p \frac{\partial T}{\partial t} = \kappa \nabla^2 T (3.1)$$

外表面的热通量满足：

$$q = -\kappa \frac{\partial T}{\partial x} (3.2)$$

对方程(3.1)两边同时求$n$阶导数，可以得到：

$$\frac{\partial^n T}{\partial t^n} = \alpha \nabla^{2n} T (3.3)$$

如果表面热通量可以分别表示为空间和时间的形式，板中任意点的温度可以用无穷级数表示。

$$T(x,t) = T_0(t) + \sum_{n=1}^{\infty} \left( \frac{x^2}{\alpha} \right)^n \frac{d^n T_0}{d t^n}}{(2n)!} (3.4)$$

$$\frac{x}{\kappa} \left[ q_0(t) + \sum_{n=1}^{\infty} \left( \frac{x^2}{\alpha} \right)^n \frac{d^n g_0}{d t^n} \right] (2n+1)!$$

应用方程3.2，外表面的热通量可以获得为：

$$q_0(t) = -\rho C_{\rho} \sum_{n=1}^{\infty} \frac{1}{(2n-1)!} \left(\frac{\delta^2}{\alpha}\right)^{n-1} \frac{dT_0}{dt^n} + \sum_{n=1}^{\infty} \frac{1}{(2n)!} \left(\frac{\delta^2}{\alpha}\right)^{n} \frac{dg_0}{dt^n} (3.5)$$

在实际应用中，通常取无穷级数展开的前几项作为近似。例如，当厚度较小时：

$$q_0(t) \approx -\rho C_{\rho} \frac{dT_0}{dt} + q_0(t) (3.6)$$

O.R. Burggraaf [8] 将方程3.6扩展到了圆柱和球体，并给出了示例进行验证。值得注意的是，尽管解析法计算准确且资源消耗低，但其应用范围并不宽广。很难发现该方法仅适用于非常简单的几何条件，且要求已知的温度和热流在时间和空间上是无限可微的。当面对二维或三维情况时，很难获得显式解，因此引入数值方法变得必要。

传统的数值方法通常包括离线方法和在线方法。例如，离线方法需要积分所有数据以获取未知的热通量，而在线方法只需要短时间内的温度测量数据。共线法方法都是基于函数的优化过程，可以进一步分为确定性优化和随机优化。确定性优化依赖于函数的梯度值。在每次迭代中，用当前参数计算正向热问题，并获得计算温度值与测量温度值之间的误差。迭代过程不断更新，最终达到代价函数的最小值。研究人员已将多种梯度算法应用于热通量重构。图3.1展示了一个基于梯度的方法示例。

例如，Zhou [9] 引入了共轭梯度（CG）算法来重构二维边界的空间或时间相关边界条件。结果显示，开发的方法可以适用于各种情况且具有相当的精度。1992年，Taler [10] 采用Newton-Raphson法通过瞬态温度段获取未知的热通量。随后2009年[11]，他们将Levenberg-Marquardt（LM）算法与ANSYS相结合，实现了热通量、对流传系数和温度的精度估计[12]。此外，Ngo [13]实施了Broyden-Fletcher-Goldfarb-Shanno（BFGS）方法来预测金属随时间变化的热通量热系数。

基于梯度的方法没有人为设置参数，反演精度较高，因此具有很强的通用性。然而，此类算法都受到初始值的影响，因此容易陷入局部最优。相比之下，随机优化在寻找全局最优解方面具有某些优势。如今，学者们引入了几种用于热通量重构的全局算法。例如，Kane等[14]利用遗传算法（GA）改进版本通过瞬态温度获取表面热通量，而Liu [15]实施了粒子群优化（PSO）在温度测量的基础上重构未知的热通量。尽管这些方法更有可能跳出局部最优，但由于计算量巨大且时间成本无法接受，它们难以应用于复杂结构的热载荷反演。此外，由于这些算法一次只能重构少数参数，它们不适用于实时场景。

非稳态传导表现出扩散特征，具有阻尼和延迟特性。阻尼特性表明边界热通量的变化对边界附近的温度影响较大，且影响随着与边界距离的增加而逐渐减少。延迟特性是内部温度对边界热通量的响应在时间上存在延迟。因此，获取表面热通量最有效的方法是在序列上进行估计，而不是整个时域内。

为此，Beck在1968年引入了序列函数法（SFM）[16]，并在1985年进行了详细描述。序列函数规格算法也被应用于Huang等人的研究中[17]，在每个时间步假设线性。注意的是，灵敏度系数是通过有限元法（FEM）获取的。SFM假设了热通量的指定公式并通过未来测量预测当前的未知热通量。通过这种方法：

$$J_p = \sum_{n=0}^{r-1} \sum_{m=1}^{M} [T(r_m, t^{n}) - \tilde{T}(r_m, t^{n})]^2$$

假设时间窗口内的热通量是线性的，第$[i+1]$次迭代的热通量估计为：

$$Q_{i+1}^p = Q_i^p - \frac{\sum_{n=0}^{r-1} \sum_{m=1}^{M} [T(r_m, t^{p+n}) - \tilde{T}(r_m, t^{p+n})] \frac{\partial G_n}{\partial Q^p}}{\sum_{n=0}^{r-1} \sum_{m=1}^{M} [\frac{\partial G_n}{\partial Q^p}]^2}$$

其中$\partial T/\partial Q^p$是$G_n$处的热通量，记录为$G_n$。满足：

$$\rho C_p \frac{\partial G_n}{\partial t} = n\nabla^2 G_n, t \in [t^{p-1}, t^{p+r-1}]$$

$$\kappa \frac{\partial G_n}{\partial t^{p+n}} = -n + 1$$

在计算过程中，从初始时刻的全场热分布和初步估计的$Q_i^p (n = 0, \dots, r-1)$ 通过热传导方程计算每个点的温度历史$T(r_m, t^{1+n}), (n = 0, \dots, r-1)$，并应用方程3.8获取灵敏度$G_n^p$。之后，可以使用$Q_1$和$T(r_m, t^{2+n}), (n = 0, \dots, r-1)$按照相同的方法重构$Q_2$。

除了序列函数法外，Al-Khality [18]采用了数字1D滤波HCPs，实现了高稳定性且无散射效应。

![图3.1 热通量反演中的基于梯度的方法。](img/020125e0e98f771fbb32face180_98.png)

其中 $h(t)$ 是对应系统函数的脉冲响应。通过上述方程的 $z$ 变换，可以得到：

```
