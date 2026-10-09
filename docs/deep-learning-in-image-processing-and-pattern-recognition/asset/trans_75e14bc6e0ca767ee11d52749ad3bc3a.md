
## 5.2. 梯度域算法

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

## 5.2. 梯度域算法

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

## 5.3. 基于 DNN 的 TM 算法

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

本文提出了一种自适应对数归一化变换 AdaLogT，用于 TM 算法，以补偿预处理造成的缺陷。基于对经典预处理方法的分析，引入参数 *p* 以获得适当的对数归一化曲线。最优参数 *p* 通过所提出的目标函数计算。考虑基于亮度域或梯度域的 TM 算法，分别构建了基于亮度域和梯度域特征的目标函数。此外，针对基于 DNN 的 TM 算法提出了联合域感知目标函数。所提出的预处理算法确保图像亮度符合人类视觉系统（HVS）对场景亮度的感知。实验中选择了先进的亮度域、梯度域和基于 DNN 的算法，并使用了不同的预处理方法。实验结合了主观定性评估和客观定量评估。结果表明，所提出的算法在 TMQI 质量分数下取得了最佳的主客观评分，这表明该方法提高了图像的主观效果和客观质量。后续工作包括改进最优参数 *p* 的优化方法，以及利用折叠凹函数进行更通用的色调映射预处理。

**作者贡献：** 概念构思，X.F. (Xuelai Fang) 和 X.F. (Xiangchu Feng)；监督，X.F. (Xiangchu Feng)；写作——初稿，X.F. (Xuelai Fang)；写作——审阅与编辑，X.F. (Xuelai Fang) 和 X.F. (Xiangchu Feng)。所有作者均已阅读并同意最终手稿的发布版本。

**资助：** 本工作得到国家自然科学基金资助，资助编号分别为 617272389 和 61972264。

**数据可用性声明：** 所有实验数据均来自公开可用的数据集。数据集的网址为：https://vc.uwaterloo.ca/database/TMQI/TMQI-Database.html, https://pfsools.sourceforge.net/jdr_gallery.html, 和 https://qualinet.github.io/databases/image/tone-mapped-image-quality-database/ （访问日期：2022年10月21日）。

**致谢：** 我们谨向三位审稿人致以诚挚的谢意，感谢他们富有洞察力且宝贵的反馈，这帮助我们改进了我们的工作。

**利益冲突：** 作者声明无利益冲突。

# 参考文献

1.  DiCarlo, J.M.; Wandell, B.A. Rendering high dynamic range images. *In Sensors and Camera Systems for Scientific, Industrial, and Digital Photography Applications*; SPIE: Bellingham, WA, USA, 2000; Volume 3965, pp. 392–401.
2.  Reinhard, E.; Heidrich, W.; Debevec, P.; Pattanaik, S.; Ward, G.; Myszkowski, K. *High Dynamic Range Imaging: Acquisition, Display, and Image-Based Lighting*; Morgan Kaufmann: Burlington, MA, USA, 2010.
3.  Elersten, G.; Mantikuu, R.K.; Unger, L. A comparative review of tone-mapping algorithms for high dynamic range video. In *Computer Graphics Forum*; Wiley Online Library: New York, NY, USA, 2017; Volume 36, pp. 565–592.
4.  Gibbon, J. Sccar expectency theory and Weber’s law in animal timing. *Psychol. Rev.* **1977**, *84*, 279. [CrossRef]
5.  Durand, F.; Dorsey, J. Fast bilateral filtering for the display of high-dynamic-range images. In *Proceedings of the 29th Annual Conference on Computer Graphics and Interactive Techniques*, San Antonio, TX, USA, 23–26 July 2002; pp. 257–266.
6.  Farbman, Z.; Fattal, R.; Lischinski, R.; Szeliski, R. Edge-preserving decompositions for multi-scale tone and detail manipulation. *ACM Trans. Graph. (TOG)* **2008**, *27*, 1–10. [CrossRef]
7.  Paris, S.; Hasinoff, S.W.; Kautil, J. Local laplacian filters: Edge-aware image processing with a laplacian pyramid. *ACM Trans. Graph.* **2011**, *30*, 68. [CrossRef]
8.  Liang, X.; Yu, J.; Zhang, F.; Cao, Z.; Zhang, L. A hybrid 11-to-layer decomposition model for tone mapping. In *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition*, Salt Lake City, UT, USA, 18–23 June 2018; pp. 4758–4766.
9.  Zhao, L.; Li, H.; Kuang, W.; Li, L.; C.X.; Li, Y. An adaptive method for image dynamic range adjustment. *IEEE Trans. Circuits Syst. Video Technol.* **2018**, *29*, 640–652. [CrossRef]
10.  Drago, F.; Myszkowski, K.; Annen, T.; Chiba, N. Adaptive logarithmic mapping for displaying high contrast scenes. In *In Computer Graphics Forum*; Wiley Online Library: New York, NY, USA, 2003; Volume 22, pp. 419–426.
11.  Zhao, L.; Li, G.; Wang, J. Tone Mapping Method Based on the Least Squares Method. *Electronics* **2022**, *12*, 31. [CrossRef]
12.  Zhao, L.; Sun, R.; Wang, J. Three-scale Tone Mapping Algorithm. *Electronics* **2022**, *11*, 4072. [CrossRef]
13.  Land, E.H. The retinex theory of color vision. *Sci. Am.* **1977**, *237*, 108–129. [CrossRef]
14.  Mantikuu, R.; Daly, S.; Keroskoy, L. Display adaptive tone mapping. In *ACM SIGGRAPH 2008 Papers—SIGGRAPH ’08*; ACM Press: New York, NY, USA, 2008; p. 1–10.
15.  Khan, I.R.; Rahaedia, S.; Khan, M.M.; Movania, M.M.; Abed, F. A tone-mapping technique based on histogram using a sensitivity model of the human visual system. *IEEE Trans. Ind. Electron.* **2017**, *65*, 3469–3479. [CrossRef]
16.  Fattal, R.; Lischinski, M.; Werman, M. High dynamic range compression. In *Proceedings of the 29th Annual Conference on Computer Graphics and Interactive Techniques*, San Antonio, TX, USA, 23–26 July 2002; pp. 249–256.
17.  Bhat, P.; Ziticik, C.L.; Cohen, M.; Curless, B. Gradient-domain optimization framework for image and video filtering. *ACM Trans. Graph. (TOG)* **2010**, *29*, 1–14. [CrossRef]
18.  Shibata, Y.; Tanaka, M.; Okutomi, M. Gradient-domain image reconstruction framework with intensity-range and base-structure constraints. In *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition*, Las Vegas, NV, USA, 27–30 June 2016; pp. 2745–2753.
19.  Rana, A.; Singh, P.; Valenzise, G.; Dufaux, F.; Komodakis, N.; Smolic, A. Deep tone mapping operator for high dynamic range images. *IEEE Trans. Image Process.* **2019**, *29*, 1285–1298. [CrossRef]

