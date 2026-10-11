
在本文中，我们提出了一种基于最小二乘法的色调映射方法。我们的目的是在普通显示器上揭示真实场景的局部对比度。基于经典的 Retinex 模型，我们使用最小二乘法的中间权重进行光照估计，同时引入了边界感知权重以防止光晕伪影。细节层通过上述方法获得。使用权重的方法考虑了亮度强度和像素位置，这可以防止生成光晕伪影，同时确保光照信息的准确估计。应用了具有该参数的全局色调映射函数，以压缩获得的光照估计的动态范围。该函数通过拟合直方图均衡化的结果获得，不同的图像对应不同的参数值。该方法可以更有效地实现对不同图像的动态范围压缩。动态范围压缩后的细节层和光照层被融合以获得 LDR 图像。从主观和客观两个方面对 TMQI 数据集中的高动态范围场景进行了选择和比较分析。实验结果表明，暗区和亮区的细节均得以保留，且未出现光晕伪影。在提出的方法中，LDR 图像的 TMQI 得分为 0.893，MLWC 得分为 1.654；细节丰富度、结构保真度和视觉效果在某种程度上均优于其他方法。在本文中，我们专注于解决色调映射中光照估计和动态范围压缩的问题，未来我们将专注于使用色调映射进行视频处理。

### 作者贡献

- 概念化，L.Z.；方法论，L.Z. 和 J.W.；软件，G.L.；验证，L.Z.、G.L. 和 J.W.；形式分析，G.L.；调查，G.L.；资源，J.W.；数据整理，L.Z.；撰写——原稿准备，G.L.；撰写——审阅和编辑，J.W.；可视化，J.W.；监督，L.Z.；项目管理，L.Z. 和 J.W.；资金获取，L.Z.
- 所有作者均已阅读并同意发表的稿件版本。

### 资助

本研究由衢州科技计划项目（项目编号 2022K108）资助；中国黑龙江省自然科学基金（项目编号 YQ2022F014）；以及黑龙江省高等学校基本科学研究的基金资助项目（项目编号 2022KYYWF-C05）。

### 知情同意声明

不适用。

### 数据可用性声明

不适用。

### 致谢

作者感谢衢州科技计划项目（项目编号 2022K108）、中国黑龙江省自然科学基金（项目编号 YQ2022F014）以及黑龙江省高等学校基本科学研究的基金资助项目（项目编号 2022KYYWF-C05）。

### 利益冲突

作者声明没有利益冲突。

## 参考文献

1. Khan, I.R.; Aziz, W.; Shim, S.O. Tone Mapping Using Perceptual-quantizer and Image Histogram. *IEEE Access* **2020**, *12*, 12–15. [CrossRef]

2. Choi, H.H.; Kang, H.S.; Yun, B.J. A Perceptual Tone Mapping HDR Images Using Tone Mapping Operator and Chromatic Adaptation Transform. *Imaging Sci. Technol.* **2017**, *61*, 15–20. [CrossRef]

3. Khan, I.R.; Rahardhi, S.; Khan, M.M.; Movania, M.M.; Abed, F.A. Tone Mapping Technique Based on Histogram Using a Sensitivity Model of the Human Visual System. *IEEE Trans. Ind. Electron.* **2018**, *65*, 3469–3479. [CrossRef]

4. Hussein, A.; Mokrouai, A.; Mated, B. Revisited Histogram Equalization as HDR Images Tone Mapping Operators. *IEEE Comput. Soc.* **2017**, *15*, 144–149.

5. Chien, B.; Mokraoui, A.; Mated, B. Contrast Enhancement and Details Preservation of Tone Mapped High Dynamic Range Images. *Image Represent.* **2018**, *58*, 22–26.

6. Kai-Fu, Y.; Hui, L.; Huilin, L.; Chao-Yi, L.; Yong-Jie, L. An Adaptive Method for Image Dynamic Range Adjustment. *IEEE Trans. Circuits Syst. Video Technol.* **2019**, *29*, 15–18.

7. Hui, L.; Xixi, J.; Zhang, L. Clustering Based Content and Color Adaptive Tone Mapping. *Comput. Vis. Image Underst.* **2018**, *168*, 15–20.

8. Thai, B.G.; Mokrouai, A. HDR Image Tone Mapping Histogram Adjustment with Using an Optimized Contrast Parameter. In Proceedings of the International Symposium on Signal, Image, Video and Communications (SIVC), Rabat, Morocco, 27–30 November 2018; Volume 20, pp. 4378.

9. Fahim, M.A.N.I.; Jung, H.Y. Fast Single-Image HDR Tone Mapping by Avoiding Base Layer Extraction. *Sensors* **2020**, *20*, 4378. [CrossRef] [PubMed]

10. Gommatel, D.; Roumy, A.; Guillemot, C.; Roper, M.J.; Julien, L. Gradient-Based Tone Mapping for Rate-Distortion Optimized Backward-Compatible High Dynamic Range Compression. *IEEE Trans. Image Processing* **2017**, *15*, 12–18. [CrossRef] [PubMed]

11. Liang, Z.; Xu, J.; Zhang, D. A Hybrid H.10-l-layer Decomposition Model for Tone Mapping. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, Salt Lake City, UT, USA, 18–23 June 2018; pp. 4758–4766.

12. Rana, A.; Singh, H.; Valenzise, G.; Duxauß, F.; Komodakis, N.; Smolic, A. Deep Tone Mapping Operator for High Dynamic Range Images. *IEEE Trans. Image Processing* **2019**, *29*, 18–25. [CrossRef] [PubMed]

13. Hu, L.; Chen, H.; Allebach, J.P. Joint Multi-Scale Tone Mapping and Denoising for HDR Image Enhancement. In Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision, Waikoloa, HI, USA, 3–8 January 2022; Volume 26, pp. 729–738.

14. Yeganeh, H.; Wang, Z. Objective Quality Assessment of Tone-mapped Images. *IEEE Trans. Image Processing* **2012**, *22*, 657–667. [CrossRef] [PubMed]

15. Gu, B.; Li, W.; Zhu, M. Local Edge-preserving Multiscale Decomposition for High Dynamic Range Image Tone Mapping. *IEEE Trans. Image Processing* **2012**, *22*, 70–79.

16. Shibata, T.; Tanaka, M. Gradient-domain Image Reconstruction Framework with Intensity-range and Base-structure Constraints. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, Las Vegas, NV, USA, 27 June 2016; pp. 2745–2753.

17. Khosravi, M.; Gupta, N.; Marina, N. Perceptual Adaptation of Image Based on Chevreul–Mach Bands Visual Phenomenon. *IEEE Signal Process. Lett.* **2017**, *24*, 594–598. [CrossRef]

18. Mittal, A.; Soundararajan, R.; Bovik, A.C. Making a “completely blind” image quality analyzer. *IEEE Signal Process. Lett.* **2012**, *20*, 209–212. [CrossRef]

19. Mittal, A.; Moorthy, A.K.; Bovik, A.C. No-reference image quality assessment in the spatial domain. *IEEE Trans. Image Process.* **2012**, *21*, 4695–4708. [CrossRef] [PubMed]

**免责声明/出版商声明：** 所有出版物中包含的陈述、观点和数据仅属于个人作者和贡献者，不代表 MDPI 和/或编辑的观点。MDPI 和/或编辑对内容中提到的任何想法、方法、说明或产品造成的人员伤害或财产损失不承担责任。

# 三阶段色调映射算法

Lanfei Zhao $ ^{1} $, Ruiyang Sun $ ^{2} $ and Jun Wang $ ^{3,*} $

1. 黑龙江省高等教育测量控制技术与仪器重点实验室，哈尔滨理工大学，哈尔滨 150080，中国
2. 中国武术系，哈尔滨体育学院，哈尔滨 150008，中国
3. 信息工程学院，衢州职业技术学院，衢州 324000，中国

\* 通讯作者：145688@quzct.edu.cn；电话：+86-181-0570-1939

**摘要：** 本文提出了一种色调映射算法，用于将真实世界的亮度映射为显示亮度。我们的目的是在常规监视器上揭示真实场景的局部对比度。围绕这一目标，我们提出了一种三阶段算法来可视化高动态范围图像。高动态范围图像的所有像素被分为三组。在第一阶段，我们引入分段线性映射作为全局色调映射算子，以映射第一组像素的亮度，从而提供亮度的整体印象。在第二阶段，第二组像素的亮度由其邻域像素的加权平均值确定，这些邻域像素源自第一组像素。在第三阶段，第三组像素的亮度由其邻域像素的加权平均值确定，这些邻域像素源自第二组像素。在若干真实世界图像和TMQI数据库上的实验结果表明，与我们最接近的竞争性色调映射方法相比，我们的算法平均意见分数和色调映射图像质量指数得分分别高出约12%和9%，从而改善了真实场景的可见度。与现有的色调映射方法相比，我们的算法产生的结果视觉上引人入胜，且没有光晕伪影和细节丢失。

**关键词：** 高动态范围；色调映射；分段线性映射；局部对比度

## 1. 引言

真实世界场景涵盖广泛的亮度级别，其数量级约为 $ 10^{14} $ [1]。通过复杂的自适应过程，人类视觉系统逐渐适应超过九个数量级。现代图像传感器的动态范围远小于真实世界场景和人类视觉系统。然而，通过多重曝光成像 [2]，可以扩展图像场景的极限。因此，我们可以使用常规数码相机获取高动态范围（HDR）图像。

某些先进的常规显示器的对比度比高达 $ 10^{5} $ [3]，尽管某些高动态范围显示系统声称它们可以实现五个数量级 [4]。然而，显示系统的动态范围仍远小于真实世界场景。此外，高对比度显示器的价格对于家庭消费者来说是不可承受的。这一缺陷导致阴影和高光无法传达原始场景的外观。色调映射已被开发用于将HDR图像转换为低动态范围（LDR）图像，其动态范围与常规显示器兼容。有效的色调映射算法可以在常规显示器上清晰地显示黑暗和明亮像素。它还能够保留原始图像中的细节，并避免常见的伪影，如光晕、梯度反转或局部对比度丢失 [5]。

不幸的是，现有的色调映射算法存在某些图像质量下降的问题，*例如，* 细节丢失和不适当的整体亮度印象。为了解决HDR图像的渲染问题，我们提出了一种三阶段色调映射算法。主要思想是在保留真实场景局部对比度的同时，将真实世界的亮度映射为可显示的亮度。对于真实世界亮度的映射，先前的色调映射方法主要压缩高亮度 [6]。这样的色调曲线会导致全局对比度过度压缩。为了解决这个问题，我们提出了一种分段线性映射作为第一阶段，以确定亮度并增强色调映射图像的全局对比度。分段线性映射的每个段点是通过一个微小的亮度阈值选择的，重映射的亮度是通过亮度直方图的累积概率估计的。为了视觉细节保护，Ashikhmin [7] 专注于在压缩动态范围时保留局部对比度。然而，这种方法可能导致视觉细节保留性能不足。我们引入了另外两个阶段来确保局部对比度；这两个阶段都采用邻域像素的加权平均值来估计局部对比度。从每个阶段导出的光度通过回顾局部对比度表达式与前一个阶段相关联。在来自各种真实场景的辐射图上进行实验，结果表明所提出的算法可以生成令人愉悦的图像。

## 2. 相关工作

在早期的尝试中，全局色调映射设计了一条单一曲线来压缩动态范围，并旨在节省计算效率 [8]。Tumblin和Rushmeier [9] 构建了一个实用的通用框架，以匹配真实世界亮度和显示亮度。他们回顾了电影编码过程中对光的Sigmoid响应。使用这种幂律指标，他们创建了一个观察者模型，将世界亮度转换为感知亮度；同时，系数和指数由Stevens实验确定。Ward [10] 应用指定的乘数来关联显示器和真实场景中最小可辨差异。注意，此方法处理的是感知对比度，因此，它在明亮场景和黑暗场景中提供相同的对比度可见性。Larson等人 [11] 建议眼睛对区域亮度（即适应水平）而非绝对亮度敏感。为了估计适应水平，他们在\(10^{\circ}\)视角上对真实世界亮度进行了平均。应用带有线性上限的直方图均衡化来压缩动态范围，而限制区域对比度不能超过原始图像。Khan等人 [12] 提出了一种基于直方图的色调映射算法，以在LDR显示器上可视化HDR图像。该算法限制直方图中的像素计数，以解决由经典直方图均衡化引起的过度压缩和过度增强问题。

最近的色调映射研究专注于局部色调映射算子。Mayer等人 [13] 使用基于Retinex的自适应滤波器渲染真实世界图像。此滤波器通过两个并行过程处理亮度和色度。色度处理采用主成分分析，在压缩亮度时提供不受影响的色彩再现免疫性。Gu等人 [14] 开发了一种局部边缘保持（LEP）滤波器，并应用LEP滤波器基于Retinex模型将真实场景图像分解为几个细节层和一个基础层。Kuang等人 [15] 提出了一种有效的图像外观建模，基于iCAM框架在不同媒体中复现相同的视觉感知。该方法通过双边滤波器将图像分解为基础层和细节层。Com响应函数和杆细胞响应函数应用于基础层以压缩动态范围。对细节层应用幂函数调整以预测Stevens效应。Fattal等人 [5] 将亮度梯度作为局部指标，以保留细节并压缩动态范围。该工作试图衰减每个像素处的大幅度梯度，同时保持小幅度梯度不变。他们的作品还引入了高斯金字塔以避免光晕伪影。

近年来，提出了基于深度学习的色调映射算法以生成LDR图像。Rana等人 [16] 提出了一种快速、无参数、场景自适应的深度色调映射算子（DeepTMO），基于条件生成对抗网络。DeepTMO探索了四种可能的生成器-判别器架构设计组合，以专门解决HDR相关深度学习中的某些突出问题

诸如模糊、平铺图案和饱和度伪影等框架。Panetta等人[17]设计了一种基于深度学习的色调映射算子（TMO-Net），该方法提供了一种高效且无参数的解决方案，能够有效泛化到更广泛的HDR内容范围。Patel等人[18]提出了一种新颖的生成对抗网络，用于学习多种经典色调映射算子的组合。所提出的方法使用深度网络来保留由经典色调映射算子生成的最佳TMQI [19]分数的色调映射图像。

## 3. 算法

### 3.1. 全局亮度映射

我们应用由Reinhard提出的场景键值[20]来类比相机曝光。场景键值的近似值由以下公式给出：

![](img/e4200cc4308edaf8913e513b0f96dbb6_494_0.png)

其中 $M$ 是像素总数，$\delta$ 是一个小值，$\bar{L}$ 是世界亮度，$(x, y)$ 是像素位置，$L$ 是场景键值。缩放后的亮度计算如下：

![](img/e4200cc4308edaf8913e513b0f96dbb6_494_1.png)

其中 $a$ 是将对数平均世界亮度映射到合适值的键值，$a$ 通过Reinhard的工作[21]自适应估计。

我们发现，大量辐射度图的色调分布曲线呈现出相似的色调，部分展示在图1a中，该图取自一个名为“纪念教堂”的著名辐射度图。
