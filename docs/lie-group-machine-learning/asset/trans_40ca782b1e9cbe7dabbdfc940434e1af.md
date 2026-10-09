

### A. 特征提取通过特征矩阵特征值分布的集中度来执行。

对于每个图像 $A_j^i$，我们将其投影为一个 2n 维向量，即

$$X_j^i = A_j^i v .$$

我们将 $v$ 称为投影向量，将 $X_j^i$ 称为投影特征向量。经过辛酉矩阵变换后，得到两个新的辛酉矩阵。利用这两个辛酉正交矩阵重构原始图像，并将原始图像投影到这两个辛酉正交矩阵上。在这个投影空间中，使用辛酉分类器进行图像分类。对于不同的人脸图像，选择一些图像作为训练样本。在此过程中，图像通过特征提取并以辛酉矩阵的形式表达。利用辛酉矩阵的简化方法，我们可以简化图像矩阵，从而获得图像的特征子空间。然后，将图像作为训练样本，图像库中的其他图像作为待识别样本。

对于图像库中待识别的图像，将其组合为相同的特征组合，用辛酉矩阵表示该图像，然后对该矩阵进行奇异值分解以获得相应的辛酉表示方法。然后，我们在人脸识别过程中使用辛酉群分类器算法来处理图像。

### 3.4.2 实例验证

为了验证辛酉群分类器算法的性能，我们使用 ORL 和 YALE 两种人脸图像库测试了该算法的性能。ORL 库在 3.3.2 节中有描述。YALE 数据库由 15 人组成（每人 11 张图像），包含较大的光照和面部变化。测试系统的硬件环境是 *Pentium* (*R*) 4 *CPU* (2.80 *GHz*)，配备 512 *MB* 内存。软件平台为 *MATLAB* 6.5。对于图像库中的图像，我们首先计算其辛酉矩阵，并使用辛酉算法进行训练。然后，在数据库中查找同一人的另一张图像表达，根据找到图像的正确率，获得算法的识别效率。如图 3.8 所示，比较了若干种算法的性能。

图 3.9 展示了两种分类算法在 ORL 库中的识别率。对于 ORL 库中的每一类图像，我们使用样本 2、3、...、9 作为训练样本，其余作为测试样本。与识别算法相比，当训练组较大时，图像的识别率更高。

图 3.10 展示了两种分类算法在 YALE 库中的识别率。对于 YALE 库中的每种图像，选择 2、3、...、10 张图像作为分类样本，其余作为测试样本。与 PCA 识别算法相比，辛酉群分类算法的识别效率较高。

![](img/456a7a56403cbb2b5f1a261793529a51_134_0.png)

图 3.8：辛酉群分类算法的人脸识别效果图。

![](img/456a7a56403cbb2b5f1a261793529a51_134_1.png)

图 3.9：ORL 库中的人脸识别率。

![](img/456a7a56403cbb2b5f1a261793529a51_135_0.png)

**图 3.10：** YALE 库中的识别率。

在识别图像的过程中，我们使用辛酉群分类算法将多张图像作为训练样本。这里，我们给出了仅使用一张图像作为训练样本、其他图像作为测试样本时辛酉群分类算法的识别率。通过识别过程，我们发现即使只有一张图像作为训练样本，辛酉群分类器算法也具有较高的识别精度。这是因为，对于一张图像，经过辛酉分类算法处理的图像获得了图像的特征向量，且该特征向量对于同一人脸的不同图像是稳定的。表 3.3 和 3.4 给出了在仅有一个训练样本的情况下，几种分类算法在 ORL 和 YALE 库上的性能对比 [36, 37]。

**表 3.3：** 几种算法在 ORL 库上的性能对比。

| 分类算法 | 训练样本数量 | 平均识别准确率 (%) |
| :--- | :--- | :--- |
| 辛酉群 | 1 | 92.6 |
| Spectroface | 1 | 90.8 |
| 线性子空间 | 1 | 84.2 |

**表 3.4：** 几种算法在 YALE 库上的性能对比。

| 分类算法 | 训练样本数量 | 平均识别准确率 (%) |
|---|---|---|
| 辛酉群 | 1 | 92.6 |
| Spectroface | 1 | 95.7 |
| 线性子空间 | 1 | 84.4 |

结果表明，即使只有一个训练分类样本，平均识别的准确率仍处于较高水平，且与线性子空间方法相比，辛酉群的正确率相对较高。

# 3.5 总结

作为一种新的机器学习方法，李群机器学习受到了研究人员的广泛关注。目前，李群机器学习理论已应用于许多领域，例如在分类领域已有若干成功案例。在本章中，我们讨论了李群机器学习中辛酉群分类器的设计方法，研究了李群机器学习框架下的辛酉群分类器算法，并使用该分类器进行了图像识别和数据集分类。因此，显示了该方法的优势。

# 参考文献

- [1] Feng K, Qin MZ. Symplectic Algebraic Algorithm of Hamiltonian System. 浙江: 浙江大学出版社, 2006.
- [2] Shaw WT. Symplectic Geometry of null Infinity and Two-surface Twistors. 牛津大学数学研究所, 英国.
- [3] Gao L, Li YM, Chen XR, Yang KQ. An Attempt to Seismic Ray Tracing with Symplectic Algorithm. 地球物理学报, 2000, 5(3), 402–410.
- [4] Wu Y, Hu JY, Yin XG. Symplectic Integrators of the Equations of Multibody System Dynamics on Manifolds. 力学进展, 2002, 2(32), 189–195.
- [5] Wang SX, Liu YW, Wu HT. Study on Computational Accuracy of Robot Dynamics. 机械工程学报, 1998, 34(1), 14–20.
- [6] Han XS, Wang SX, Yu SY. Investigation of Nanomanufacturing Process by Molecular Dynamics Simulation Based on Symplectic Algorithm. 机械工程学报, 2005, 41(4), 17–22.
- [7] Zhang K. The study on PML-FDTD and Boundary Connecting Conditions of Total-scattering Fields in 3-D Cylindrical Coordinates. 重庆邮电大学学报, 2003, 3, 21–26.
- [8] Xu ZX, Zhou DY, Deng ZC. Numerical Method Based on Hamilton System and Symplectic Algorithm to Differential Games. 应用数学和力学, 2006, 27(3), 305–310.
- [9] Sun Y, Xie J. Hamiltonian Symplectic Semi-analytical method and its application in anisoTropic electromagnetic waveguide. 计算力学学报, 2005, 22(6), 690–693.
- [10] Zhang PG. A Post-processing Algorithm for the Dynamic Analysis of DNA Elastic Slender Structure. 青岛大学学报, 2006, 21(3), 71–74.
- [11] Ritter G, Gallegos MT. A Bayesian approach to object identification in pattern recognition. 国际模式识别会议论文集, 2000, IEEE: 1082–1086.
- [12] Lovell BC, Bradley AP. The Multiscale Classifier. IEEE 模式分析与机器智能汇刊, 1996, 2(18), 124–137.
- [13] Dawi AHM, Chong TS, Fong SF. The Effects of Different Three–Dimensional Animated Visual Displays in Computer–Based Multimedia on Learners with Different Spatial Abilities. 第五届 IEEE 高级学习技术国际会议论文集. IEEE, 2005, ICALT’05, 798–801.
- [14] Tuzel O, Subbarao R, Meer P. Simultaneous Multiple 3D Motion Estimation via Mode Finding on Lie Groups. 第十届 IEEE–国际计算机视觉会议论文集. 模式分析与机器智能, 2005, 1, 18–25.
- [15] Fletcher PT, Lu CL, Joshi S. Statistics of Shape via Principal Geodesic Analysis on Lie Groups. 2003 年 IEEE 计算机学会计算机视觉与模式识别会议论文集. 医学成像汇刊, 2003, 1, 95–99.
- [16] Miasnikov AD, Haralick RM. Regression analysis and automorphic orbits in free groups of Rank2. 第十七届国际模式识别会议论文集. IEEE, 2004, ICPR’04, 180–183.
- [17] Bonmassar G, Schwartz EL. Lie Group, Space–Variant Fourier Analysis and the Exponential Chirp Transform. 1996 年计算机视觉与模式识别会议论文集. IEEE, 1996, CVPR’96, 492–496.
- [18] Yang L, Qin Z, Zhang XP. 分类器仿真算法及其应用. 西安交通大学学报, 2005, 39(12), 1311–1314.
- [19] Mitchell TM. 机器学习. 北京: 机械工业出版社, 2003.
- [20] He YH, Zhao L, Zou CR. 基于核最近特征的人脸识别分类器. 应用科学学报, 2006, 24(3), 227–231.
- [21] Squire DM, Caelli TM. 不变性特征. 通过偏离不变性刻画轮廓. 计算机视觉与图像理解, 2000, 77(3), 284–316.
- [22] Zhong WX, Ouyang HJ. 复合材料力学中的哈密顿系统与辛几何 – 平面应力问题. 应用数学和力学, 1992, 13(12), 1031–1035.
- [23] Ma ZJ. 物理学中的群论. 科学出版社, 2006.
- [24] Lai JH, Yan XH, Deng DG. 完成 Spectroface 人脸识别的分类器设计. 图像与图形学杂志, 2002, 7(5), 466–471.
- [25] Yu HB. 基于头部特征提取的人体检测与跟踪及其应用. 杭州: 浙江大学, 2007.
- [26] Wang P. 数据流上的分类算法研究. 上海: 复旦大学, 2007.
- [27] Xie YH. 人脸特征提取与分类器设计的若干问题研究. 南京: 南京理工大学, 2006.
- [28] Li L. 利用辛几何构造带仲裁的认证码. 吉林建筑工程学院学报, 2006, 23(4), 63–67.
- [29] Zhao Lih, Sun XH. 基于肤色的脸检测. 工程图学学报, 2005, 3, 84–88.

