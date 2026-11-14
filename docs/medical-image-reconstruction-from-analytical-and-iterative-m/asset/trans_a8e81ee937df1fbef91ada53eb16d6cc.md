

- 第三种方法是在投影器/后投影器对中建模更准确的成像几何和物理。该方法的目的是减少投影模型与测量数据之间的确定性差异。

- 第四种方法是使用正确的噪声模型来构建目标函数。作者个人认为，基于联合概率密度函数的噪声模型并不十分关键。你可以有一个不太准确的噪声模型（即，不太准确的联合概率密度函数），但必须拥有准确的方差。重要的是要加入正确的测量噪声方差来对数据进行加权。至于噪声是否严格符合高斯分布、严格符合泊松分布等，则不那么重要。

- 第五种方法是使用先验知识。如果投影数据由于测量不足和噪声等原因未能携带关于对象的足够信息，那么关于对象的先验知识可以补充更多关于对象的信息，并使迭代算法更加稳定。请注意，如果先验知识并不真实，它可能会误导算法收敛到一张错误的图像。

- 读者应当理解本章中成像方程组是如何建立的，以及迭代 ML-EM 算法是如何工作的。

## 问题

**问题 6.1** 某些迭代算法，例如 ART 和 OS-EM 算法，会非常频繁地更新图像。对于这些算法，数据子集的处理顺序很重要。在本题中，我们使用 ART 算法以图形方式求解下图所示的包含两个变量的线性方程组 {L1, L2, L3, L4}。初始估计解为 X0。分别使用两种不同的顺序求解该方程组：(a) L1 → L2 → L3 → L4 和 (b) L1 → L3 → L2 → L4，并比较它们在收敛速度方面的性能。

![](img/dd555effd38151c67af30d84800c554a_193_0.png)

**问题 6.2** 迭代 ML-EM 算法 \(x_j^{(k+1)} = x_j^{(k)} \frac{\sum_i a_{ij} \frac{p_i}{\sum_j a_{ij} x_j^{(k)}}}{\sum_i a_{ij}}\)，或迭代 OS-EM 算法，有许多修改版本。其中一个版本引入了新参数 \(h\)：

\(\begin{aligned} x_j^{(k+1)} = x_j^{(k)} \left( \frac{\sum_i a_{ij} \frac{p_i}{\sum_j a_{ij} x_j^{(k)}}}{\sum_i a_{ij}} \right)^h. \end{aligned}\)

该参数 \(h\) 通常取 1 到 5 之间的实数。使用该参数 \(h\) 的目的是增加迭代步长，使算法收敛得更快。如果参数 \(h\) 选在 0 到 1 之间，则会减小迭代步长。这个新算法是否满足本章例题 8 中研究过的总计数守恒性质？如果不再满足该性质，你可以始终用一个因子对新更新的图像进行缩放。找出这个缩放因子，使得每次迭代都守恒总计数。

**问题 6.3** 问题 6.2 中讨论的修改算法只能用于发射成像应用，因为线性方程是由发射测量的泊松方差加权的。可以针对透射测量开发一个类似的算法，以求出对象的衰减图，如下所示：

\(\begin{aligned} \mu_j^{(k+1)} = \mu_j^{(k)} \left( \frac{\sum_i a_{ij} N_0 e^{-\sum_j a_{ij} \mu_j^{(k)}} \frac{N_i}{N_i}}{\sum_i a_{ij}} \right)^h. \end{aligned}\)

其中，测量建模为 \(N_i = N_0 e^{-\sum} a_{ij} \mu_j\)。这里，我们不取对数并将这些非线性方程转换为线性方程，而是直接求解这个非线性方程组 \(N_i = N_0 e^{-\sum} a_{ij} \mu_j\)。使用泰勒展开将此算法转换为相应的加性更新形式。讨论参数 \(h\) 如何控制迭代步长，非线性方程如何加权，以及加权量是什么。

**问题 6.4** 我们已经知道，在迭代图像重建算法中，投影器应尽可能准确地建模成像系统。对于从实际成像系统获取的一组实测数据，有一种简单的方法可以验证投影器中的建模是否足够准确。该方法描述如下。运行迭代算法来重建图像。在算法收敛后，计算并显示每个视角的数据差异图像。差异图像是重建图像的投影与测量投影数据之间的差，或者是重建图像的投影与测量投影数据之间的比值。如果投影器准确地建模了成像系统，那么你在差异图像中看不到物体的阴影，只能看到随机噪声。使用计算机仿真验证此方法。

**问题 6.5** 在例题 7 中，eq. (6.135) 中选择了一个不良的贝叶斯约束 β(x<sub>1</sub> − x<sub>2</sub>)<sup>2</sup>。使用你选择的不同贝叶斯约束重做例题 7。例如，你可以选择最小范数约束。

## 参考文献

- [1] Bai C, Zeng GL, Gullberg GT, DiFilippo F, Miller S (1998) 基于迭代重建算法的几何点响应和衰减校正的逐层模糊模型. IEEE Trans Nucl Sci 45:2168–2173.

- [2] Barrett HH, Wilson DW, Tsui BMW (1994) EM 算法的噪声特性，I. 理论. Phys Med Biol 39:833–846.

- [3] Beekman F, Kamphuis C, Viergever M (1996) 使用完全三维迭代空间变散射响应补偿改进 SPECT 定量. IEEE Trans Med Imaging 15:491–499.

- [4] Byrne CL (1996) 用于从投影进行图像重建的块迭代方法. IEEE Trans Imaging Process 5:792–794.

- [5] Candès E, Romberg J, Tao T (2006) 鲁棒不确定性原理：从高度不完整的频率信息中精确重建信号. IEEE Trans Inf Theory 52:489–509.

- [6] Censor Y, Eggermont PPB, Forton D (1983) 不齐次系统中 Kaczmarz 方法的强松弛. Numer Math 41:83–92.

- [7] Chang L (1979) SPECT 中的衰减和不完全投影. IEEE Trans Nucl Sci 26:2780–2789.

- [8] Chen GH, Tang J, Hsieh YL (2009) MDCT 心脏成像中使用 PICCS 改善时间分辨率. Med Phys 36:2130–2135.

- [9] Chiao PC, Rogers WL, Fessler JA, Clinthorne NH, Hero AO (1994) 基于模型的带有边界侧信息或边界正则化的估计. IEEE Trans Med Imaging 13:227–234.

- [10] Dempster AP, Laird NM, Rubin DB (1977) 通过 EM 算法从不完全数据中进行最大似然估计. J Royal Stat Soc B 39:1–38.

- [11] DiBella E, Barclay A, Eisner R, Schafer R (1996) 迭代重建算法中基于旋转的方法比较. IEEE Trans Nucl Sci 43:3370–3376.

- [12] Donoho D (2006) 压缩感知. IEEE Trans Inf Theory 52:1289–1306.

- [13] Elbakri A, Fessler JA (2002) 多能 X 射线计算机断层扫描的统计图像重建. IEEE Trans Med Imaging 21:89–99.

- [14] Fessler J (1996) 隐式定义有偏估计量的均值和方差（如惩罚最大似然）：在断层扫描中的应用. IEEE Trans Image Process 5:493–506.

- [15] Fessler J, Hero A (1994) 空间交替广义期望最大化算法. IEEE Trans Signal Process 42:2664–2677.

- [16] Fessler JA, Rogers WL (1996) 惩罚似然图像重建的空间分辨率特性：空间不变断层扫描. IEEE Trans Imaging Process 5:1346–1358.

- [17] Frey EC, Ju ZW, Tsui BMW (1993) 用于 SPECT 成像中建模非对称空间变散射响应的快速投影器-后投影器对. IEEE Trans Nucl Sci 40:1192–1197.

- [18] Geman S, Geman D (1984) 随机松弛、吉布斯分布和图像的贝叶斯恢复. IEEE Trans Pattern Anal Mach Intell 6:721–741.

- [19] Gilbert P (1972) 从投影重建三维物体的迭代方法. J Theor Biol 36:105–117.

- [20] Gindi G, Lee M, Rangarajan A, Zubal IG (1991) 使用注册解剖图像作为先验进行功能图像的贝叶斯重建. In: Colchester ACF, Hawkes DJ (eds) Information Processing in Medical Imaging, Springer-Verlag, New York, 121–131.

- [21] Gordon R, Bender R, Herman GT (1970) 三维电子显微镜和 X 射线摄影的代数重建技术 (ART). J Theor Biol 29:471–481.

- [22] Hebert T, Leahy R (1992) 使用吉布斯先验从泊松数据进行基于统计的 MAP 图像重建. IEEE Trans Signal Process 40:2290–2303.

- [23] Herman GT (1980) 从投影进行图像重建：计算机断层扫描的基础. Academic Press, New York.

- [24] Hsieh YL, Zeng GL, Gullberg GT (1998) 使用带状函数计算更“自然”的像素以建模 SPECT 孔道器几何响应的投影空间图像重建. IEEE Trans Med Imaging 17:24–44.

- [25] Hudson HM, Larkin RS (1994) 使用有序投影数据子集加速图像重建. IEEE Trans Med Imaging 13:601–609.

- [26] Hwang DS, Zeng GL (2005) SPECT 透射测量的一种新的简单迭代重建算法. Med Phys 32:2312–2319.

- [27] Hwang DS, Zeng GL (2005) 使用更小的探测器箱大小减少 SPECT 中的噪声放大. IEEE Trans Nucl Sci 52:1417–1427.

- [28] Hwang DS, Zeng GL (2006) 使用更大步长的加速 ML-EM 算法的收敛性研究. Phys Med Biol 51:237–252.

- [29] Qi J (2003) 迭代图像估计的统一噪声分析. Phys Med Biol 48:3505–3519.

- [30] Kacmarz S (1937) 线性方程组的近似解. Bull Acad Polon Sci A 35:355–357.

- [31] King MA, Miller TR (1985) 核医学中非平稳时间维纳滤波器的应用. Eur J Nucl Med 10:458–461.

- [32] Lalush DS, Tsui BMW (1993) SPECT 中最大后验重建的广义吉布斯先验. Phys Med Biol 38:729–741.

- [33] Lalush DS, Tsui BMW (1994) 改进迭代滤波后投影算法的收敛性. Med Phys 21:1283–1286.

- [34] Lange K (1990) 带有吉布斯平滑的 EM 图像重建算法的收敛性. IEEE Trans Med Imaging 9:439–446.

- [35] Lange K, Carson R (1984) 发射和透射断层扫描的 EM 重建算法. J Comput Assist Tomogr 8:306–316.

- [36] Leng S, Tang J, Zambelli J, Nett B, Tolakanahalli R, Chen GH (2008) 高时间分辨率和无条纹的四维锥束计算机断层扫描. Phys Med Biol 53:5653–5673.

- [37] Lewitt R (1992) 迭代重建算法中图像表示的体素替代方案. Phys Med Biol 37:705–716.

- [38] Lewitt RM, Muehllehner G (1986) 基于最大似然估计 EM 算法的正电子发射断层扫描加速迭代重建. IEEE Trans Med Imaging 5:16–22.

- [39] Liang Z (1993) 通过迭代 FBP 方法在 SPECT 重建中补偿衰减、散射和探测器响应. Med Phys 20:1097–1106.

