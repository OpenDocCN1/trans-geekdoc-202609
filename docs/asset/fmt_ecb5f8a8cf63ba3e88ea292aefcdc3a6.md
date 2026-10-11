
基于这一观察，选择梯度域算法对数变换参数的关键在于确保图像具有良好的细节表现力。因此，引入指数均值局部方差（EMLV）[23] 的均值作为图像细节的度量，记为 $M_{g}$：

$$M_{g} = \frac{1}{N} \sum_{i=1}^{N} \frac{1}{|\Omega|} \sum_{\Omega} |\nabla\vec{I_{i}}|^{\gamma} \quad (15)$$

其中 $\vec{I_{i}}$ 表示图像 $\vec{I}$ 的第 $i$ 个像素，$\Omega$ 是 $\vec{I_{i}}$ 的 $3 \times 3$ 邻域。$|\Omega|$ 表示 $\Omega$ 中的像素数量，$N$ 表示 $\vec{I}$ 中的总像素数。$|\nabla\vec{I_{i}}| = \sqrt{(\partial_{x}\vec{I_{i}})^{2} + (\partial_{y}\vec{I_{i}})^{2}}$，$\partial_{x}$ 表示关于 $x$ 方向的偏导数。$\gamma$ 决定了 $\vec{I}$ 梯度的敏感度，本文取 $\gamma$ 为 $0.5$。

图 6 展示了在不同图像中改变参数 `p` 后 `M_g` 的变化情况。随着参数 `p` 的增加，对数变换后图像的 `M_g` 值呈现单峰特性，即先增大后减小。进一步实验表明，当 `p` 较小时，图像亮度较低，且纹理细节丢失；而当 `p` 过高时，图像亮度和对比度均下降。因此，我们建议在变换后选择参数 `p` 以最大化 `M_g`，从而确保输入梯度信息的最大化。我们给出梯度域 TM 算法目标函数对应的优化问题：

$$
\begin{aligned}
p^{*} = \operatorname{arg\,max}_{p} & \frac{1}{N} \sum_{i=1}^{N} \frac{1}{|\Omega|} \sum_{\Omega} |\nabla\vec{I_{i}}|^{\gamma}, \\
s.t. \quad & \vec{I} = \log( (I \cdot 10^{p} + 1) / \log(I_{max} \cdot 10^{p} + 1)),
\end{aligned}
\quad (16)
$$

由于目标函数的单峰性，我们可以使用零阶优化方法（如黄金分割法）来计算 `p` 的最优值。

![](img/e4200cc4308edaf8913e513b0f96dbb6_370_0.png)

**图 6.** `M_8` 均值与 `p` 之间的关系。

## 4. 基于 DNN 的 TM 算法的 *AdaLogT* 方法

许多算法，例如基于 DNN 的 TM 算法，并不仅仅考虑图像亮度或梯度信息。DNN 算法是数据驱动的，它们通过大量样本学习 TM 过程的主要特征，这些特征包括但不限于图像亮度和梯度等。其某些卷积运算可能包含平均算子的功能，而另一些则可能包含差分算子的功能。因此，单一域的目标函数可能无法增强算法所需的所有信息。

在 Vinker [21] 中，提出了一种用于基于 DNN 的 TM 算法的对数归一化预处理方法。对于公式 (6) 和 (7)，以下两个问题需要进一步研究和讨论：

1. **归一化。** 当 `I_min = 0` 时，`\tilde{I}_{max} = 1`，但 `\tilde{I}_{min} = \frac{\log(e)}{\log(\lambda+e)} \neq 0`。换句话说，公式 (6) 并没有严格地将输入亮度映射到 `[0, 1]` 区间。如果我们修改公式 (6) 为：

$$\tilde{I} = \frac{\log(\lambda \cdot \frac{I}{I_{max}} + \epsilon) - \log(\epsilon)}{\log(\lambda + \epsilon) - \log(\epsilon)}, \quad (17)$$

则 `\tilde{I} \in [0, 1]`。在这种情况下 `e^{\frac{\lambda}{\epsilon - I_{max}}} = 10^p`，`\lambda` 的选择问题就转化为 `p` 的选择问题。

2. **计算复杂度。** 公式 (7) 使用 DIV2k [29] 数据集中 900 张 LDR 图像亮度直方图的均值作为参考。理想情况下，计算直方图均值时应使用分布间的距离，如地球搬运距离（EMD）[39]，但这计算成本很高。具体来说，Vinker 使用随机搜索方法 [40] 在 1 到 `1 × 10^9` 之间寻找合适的值，并使用了具有高度计算精度的浮点类型，这需要持续执行。根据图 2 中不同参数下映射曲线的变化，增加精度带来的增益较小，因为需要较大的参数变化才能对曲线产生显著影响。图 7 给出了 ACC 和 AdaLogT 运行时间的比较，显示 ACC 的计算复杂度远高于 AdaLogT。

利用第 3 节的分析，我们知道由于 DNN 同时包含亮度域和梯度域，相应的目标函数应具有联合域感知的形式：

$$
\begin{gathered}
p^{*} = \arg \min _{p} a \cdot\left(\left\|\vec{I}-\vec{T}\right\|_{F}^{2}+(1-a) \cdot\left\|\vec{s}(\vec{I})\right|\right. \\
\left.-\frac{1}{N} \sum_{i=1}^{N}\left|\frac{1}{\Omega} \sum_{\vec{\Omega}} \nabla \vec{I}_{i}\right|, \right. \\
s.t. \quad \vec{I} = \log \left(I \cdot 10^{p}+1\right) / \log \left(I_{\max } \cdot 10^{p}+1\right),
\end{gathered}
\quad (18)
$$

公式 (18) 集成了具有宽感知范围的图像亮度和梯度特征，可以通过逐步法等求解。与公式 (7) 相比，公式 (18) 的计算成本大大降低。

![](img/e4200cc4308edaf8913e513b0f96dbb6_371_0.png)

## 5. 实验结果与分析

实验中用于对比的最先进 TM 算法包括亮度域算法 Gu [28]、梯度域算法 Fattal [16] 以及深度神经网络算法 Vinker [21]。Gu [28] 和 Vinker [21] 的源代码获取自作者主页，我们使用程序的默认参数。此外，Vinker [21] 提供的网络预训练参数被用作默认值。Fattal [16] 算法由 `LuminanceHDR`（`https://qtipsui.sourceforge.net/`，accessed on 13 September 2022）实现，且 gamma 设置为 2.2。所有这些实验均在配备 Intel Xeon E5630 CPU、NVIDIA GeForce 2080Ti GPU 和 32 GB 内存的 HP Workstation Z680 上运行。为了充分考虑不同场景的差异，我们在大量 HDR 图像上进行了实验，并随机选择 20 张图像进行实验分析。

### 5.1. 亮度域算法

Gu [28] 提出的预处理方法为较亮的场景提供了更好的显示效果。然而，对于室内和室外的暗场景，会出现输出图像的背景亮度与实际场景不匹配以及整体对比度降低的问题。亮度感知的 AdaLogT 更好地考虑了不同场景的背景亮度，增强了主观视觉效果。图 8 展示了这两种方法的对比。基于 20 张 HDR 图像的结果进行了一项主观实验。我们邀请了十人评估实验结果，其中 6 名男性，4 名女性，六人的研究领域涉及图像处理。评分量表从 1（最差）到 10（最好），步长为 1。结果在三星 S32R750UEC 32 英寸（4096 × 2160）显示器上显示。与 Gu 方法的均值和标准差（6.84, 1.55）相比，我们的方法（7.40, 1.15）实现了 8% 的提升。

### 5.2. 梯度域算法

![](img/e4200cc4308edaf8913e513b0f96dbb6_372_0.png)

图 8. 不同预处理方法下亮度域色调映射（TM）算法结果的对比：(a) 辐射度图；(b) Gu [28]；(c) AdaLogT。

我们还选择了色调映射图像质量指数（TMQI）[41] 作为客观评估指标。TMQI 从多个角度评估图像。该方法测量色调映射结果的结构保真度和自然度分数。随后，它综合给出一个介于 0 到 1 之间的最终分数。TMQI 的值越大，表示 TM 算法实现的结果越好。使用散点图来可视化不同预处理方法在实验图像上的 TMQI 分数。如图 9 所示，AdaLogT 在大多数图像中取得了更好的结果。

![](img/e4200cc4308edaf8913e513b0f96dbb6_372_1.png)

图 9. 不同预处理方法下亮度域算法的 TMQI 最终分数。

表 2 列出了在采用 AdaLogT 前后 20 张实验图像的平均 TMQI 分数，其中最高分数以粗体表示。我们观察到 AdaLogT 提高了 TM 算法对不同场景的适应性。合适的曝光选择为图像显示带来了巨大优势，有效提高了 TMQI 的自然度分数，从而获得了更高的 TMQI 最终分数。

**表 2. 亮度域算法的平均 TMQI 分数。**

| 预处理 | 结构 | 自然度 | 最终分数 |
| :--- | :--- | :--- | :--- |
| Gu's | 0.8273 | 0.4098 | 0.8562 |
| **AdaLogT** | **0.8305** | **0.6346** | **0.8983** |

### 5.2. 梯度域算法

基于梯度域感知的 AdaLogT 方法的梯度域算法 [16] 在定量评估和客观评估中均取得了良好的结果。

图 10 展示了明亮和黑暗场景下色调映射结果的对比，其中第一列是 HDR 辐射度图，第二列是 LogT 下的色调映射结果，第三列是使用 AdaLogT 的色调映射结果。当输入图像较暗时，LogT 下的结果较暗，细节模糊甚至无法分辨。我们的方法校正了图像曝光，在细节保留和图像自然度之间实现了平衡。结果更好地保留了图像的结构和局部细节，视觉效果更符合人眼对场景的感知。在定量用户评估中，Fattal 方法和我们的方法得分分别为 (6.73, 1.13) 和 (7.16, 1.07)。

![](img/e4200cc4308edaf8913e513b0f96dbb6_373_0.png)

(a) (b) (c)

**图 10.** 不同预处理方法下梯度域 TM 算法结果的对比：(a) 辐射度图；(b) LogT；(c) AdaLogT。

图 11 是不同预处理方法下梯度域算法结果的散点图。我们的算法在绝大多数图像中取得了相同或更好的分数。表 3 列出了在 LogT 和 AdaLogT 预处理方法下的平均 TMQI 分数。梯度域目标函数关注图像细节和纹理，因此色调映射结果具有更好的视觉亮度和细节保留。因此，与 LogT 的结果相比，AdaLogT 的结果具有更高的 TMQI 结构分数，并在自然度指数上也取得了显著改进。

![](img/e4200cc4308edaf8913e513b0f96dbb6_374_0.png)

图 11. 不同预处理方法下梯度域算法的 TMQI 最终分数。

**表 3. 梯度域算法的平均 TMQI 分数。**

| 预处理 | 结构 | 自然度 | 最终分数 |
| :--- | :--- | :--- | :--- |
| LogT | 0.8104 | 0.2577 | 0.8072 |
| **AdaLogT** | **0.8647** | **0.5272** | **0.8879** |

### 5.3. 基于 DNN 的 TM 算法

Vinker [21] 通过构建生成对抗网络进行非配对数据训练，取得了良好的结果。与其提出的基于自适应曲线的压缩（ACC）相比，基于 DNN 的 TM 算法的目标函数综合考虑了图像亮度特征和梯度特征，提高了色调映射结果的主观和客观质量。ACC 使用 900 张图像直方图的平均值作为参数选择的主要目标。本文使用图像曝光、偏斜度和梯度先验信息，使结果具有相同甚至更好的显示效果，如图 12 所示。Vinker 方法和我们的方法的主观得分分别为 (7.11, 1.16) 和 (7.37, 1.06)。根据定量主观评估，我们在主观效果方面取得了一定的进步。

图 13 展示了两种预处理方法下每张实验图像的 TMQI 质量分数，表 4 列出了不同预处理方法下 TM 算法 [21] 的平均 TMQI 分数。对于具有复杂特征的基于 DNN 的算法，所提出的方法在大多数图像中优于 ACC 算法。此外，图像梯度的增强确保了 TM 算法结果具有更好的结构保持特性，从而获得了更高的 TMQI 结构和自然度分数。

**表 4. 基于 DNN 的 TM 算法的平均 TMQI 分数。**

| 预处理 | 结构 | 自然度 | 最终分数 |
| :--- | :--- | :--- | :--- |
| ACC | 0.8587 | 0.5398 | 0.8872 |
| **AdaLogT** | **0.8798** | **0.6383** | **0.9129** |

![](img/e4200cc4308edaf8913e513b0f96dbb6_375_0.png)

图 12. 不同预处理方法下基于 DNN 的 TM 算法结果的对比：(a) 辐射度图；(b) ACC [21]；(c) AdaLogT。

![](img/e4200cc4308edaf8913e513b0f96dbb6_375_1.png)

图 13. 不同预处理方法下基于 DNN 的 TM 算法的 TMQI 最终分数。

## 6. 结论

本文提出了一种自适应对数归一化变换 AdaLogT，用于 TM 算法，以补偿预处理造成的缺陷。基于对经典预处理方法的分析，引入参数 `p` 以获得适当的对数归一化曲线。最优参数 `p` 通过所提出的目标函数计算。考虑基于亮度域或梯度域的 TM 算法，分别构建了基于亮度域和梯度域特征的目标函数。此外，针对基于 DNN 的 TM 算法提出了联合域感知目标函数。所提出的预处理算法确保图像亮度符合人类视觉系统（HVS）对场景亮度的感知。实验中选择了先进的亮度域、梯度域和基于 DNN 的算法，并使用了不同的预处理方法。实验结合了主观定性评估和客观定量评估。结果表明，所提出的算法在 TMQI 质量分数下取得了最佳的主客观评分，这表明该方法提高了图像的主观效果和客观质量。后续工作包括改进最优参数 `p` 的优化方法，以及利用折叠凹函数进行更通用的色调映射预处理。

**作者贡献：** 概念构思，X.F. (Xuelai Fang) 和 X.F. (Xiangchu Feng)；监督，X.F. (Xiangchu Feng)；写作——初稿，X.F. (Xuelai Fang)；写作——审阅与编辑，X.F. (Xuelai Fang) 和 X.F. (Xiangchu Feng)。所有作者均已阅读并同意最终手稿的发布版本。

**资助：** 本工作得到国家自然科学基金资助，资助编号分别为 617272389 和 61972264。

**数据可用性声明：** 所有实验数据均来自公开可用的数据集。数据集的网址为：`https://vc.uwaterloo.ca/database/TMQI/TMQI-Database.html`, `https://pfsools.sourceforge.net/jdr_gallery.html`, 和 `https://qualinet.github.io/databases/image/tone-mapped-image-quality-database/` （访问日期：2022年10月21日）。

**致谢：** 我们谨向三位审稿人致以诚挚的谢意，感谢他们富有洞察力且宝贵的反馈，这帮助我们改进了我们的工作。

**利益冲突：** 作者声明无利益冲突。

## 参考文献

1. DiCarlo, J.M.; Wandell, B.A. Rendering high dynamic range images. *In Sensors and Camera Systems for Scientific, Industrial, and Digital Photography Applications*; SPIE: Bellingham, WA, USA, 2000; Volume 3965, pp. 392–401.

2. Reinhard, E.; Heidrich, W.; Debevec, P.; Pattanaik, S.; Ward, G.; Myszkowski, K. *High Dynamic Range Imaging: Acquisition, Display, and Image-Based Lighting*; Morgan Kaufmann: Burlington, MA, USA, 2010.

3. Elersten, G.; Mantikuu, R.K.; Unger, L. A comparative review of tone-mapping algorithms for high dynamic range video. In *Computer Graphics Forum*; Wiley Online Library: New York, NY, USA, 2017; Volume 36, pp. 565–592.

4. Gibbon, J. Sccar expectency theory and Weber’s law in animal timing. *Psychol. Rev.* **1977**, *84*, 279. [CrossRef]
