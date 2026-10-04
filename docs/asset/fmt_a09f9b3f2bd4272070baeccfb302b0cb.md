
在这里，$t_0$ 和 $t_1$ 以训练迭代的比例表示。在我们的实验中，使用了以下值：$(t_0, t_1, \tau_1) = (0.5, 0.75, 0.0)$。结果显示退火提高了性能，线性与阶进退火之间的差异较小。

我们研究了散度惩罚函数的选择（带阶进退火），并比较了 $L_1$ 和 $L_2$。在这里，$L_1$ 允许稀疏位置具有高散度（因为梯度场中可能存在源或汇点），而 $L_2$ 提供了平均低值。正如预期的，结果显示 $L_1$ 惩罚具有优势。

此外，我们评估了第 5.2.1 节介绍的二阶监督方法。为此，我们使用 `DeepFit`$^{38}$（一种最近的用于估计法线和曲率的先进方法）估计平均曲率，并在训练期间将曲率作为真值信息引入。结果显示，惊讶的是，曲率监督没有提供任何收益。这是由于曲率估计依赖局部支持，可能会产生平滑或抖动值，导致训练不一致。

最后，我们研究了多频率初始化（带阶进退火和 $L_1$ 惩罚）的影响，并证明其持续优于所有其他消融。该变体在书中称为 `DiGS`，即带阶进退火和 `MFGI`（第 4 节）的散度 $L_1$ 惩罚。注意所有消融均在没有法线信息的情况下训练。

## 6.8 使用激活函数使用 `DiGS` 损失

我们的散度损失是通用的，适用于任何地方具有二阶导数的网络。注意，这意味着不能与 `ReLU` 激活使用，但我们可以使用平滑近似，例如 `SoftPlus` 激活函数（`IGR`$^9$ 使用）。

然而，我们的损失针对的是高频架构，如 `SIREN`。此类架构的缺点是高保真细节与虚影几何结构之间的权衡，特别是在没有法线向量监督的情况下。我们的损失对于缓解这种权衡特别有利。

我们尝试了我们的损失与 `SoftPlus` 配对，发现它没有提供性能提升，因为当 `SIREN` 在没有散度损失提升的情况下优于我们时，网络已经偏于低频率解决方案（$d_C$ 下降 0.99，$d_H$ 下降 6.34）。此外，我们实验了高斯激活，因为 `Ramasinghe` 和 `Lucy`$^{11}$ 建议其具有高性能和简单的优点。该实验在 `SRB` 数据集上进行，我们在那里训练了只有法线监督的 `INR`、带法线和散度监督的 `INR`，且散度项对于训练高斯激活监督是有益的。结果报告在表 6 中，显示散度项是有益的。在我们的实验中，我们注意到，与 `Ramasinghe` 和 `Lucy`$^{11}$ 的结果不同，这些 `INR` 对初始化和激活参数的选择非常敏感。

## 6.9. 局限性、实验设置和耗时

`DiGS` 主要受限于两个方面：(1) 捕捉非常细的结构，例如图 15 中的左侧沙发腿；以及 (2) 平滑效应，例如图 15 墙上的画。这是预期的，因为这些区域只包含极少数点，在没有法线向量信息的情况下，揭示底层表面更具挑战性。

**表 6. 高斯激活函数 `INR` 散度的影响。** 使用 Cameron $d_C$ 和 Hausdorff $d_H$ 距离在表面重建基准测试上的结果。对比了不同类型监督的高斯激活函数。

| | | Anchor | | Daratech | | | | |
|---|---|---|---|---|---|---|---|---|
| | GT | Scans | GT | Scans | | | |
| Loss | $d_C$ | $d_H$ | $d_C$ | $d_H$ | $d_C$ | $d_{\bar{C}}$ | $d_C$ | $d_H$ | $d_C$ | $d_{\bar{C}}$ |
| n | 0.278 | 5.399 | 0.333 | 7.754 | 0.136 | 2.418 | 0.338 | 7.240 | 0.111 | 1.770 |
| n + div | **0.230** | **4.394** | **0.262** | **7.061** | **0.125** | **1.156** | **0.237** | **3.791** | **0.105** | 1.795 |
| div | 0.3128 | 5.801 | 0.370 | 7.817 | 0.141 | 1.884 | 0.133 | 7.968 | 0.133 | **1.597** |

| | | | | Gargoyle | | | Lord Quas | | | | |
|---|---|---|---|---|---|---|---|---|---|---|---|
| | DC | | | Scans | | | GT | Scans | | | |
| Loss | $d_C$ | $d_H$ | $d_{\bar{C}}$ | $d_{\bar{H}}$ | $d_C$ | $d_H$ | $d_{\bar{C}}$ | $d_{\bar{H}}$ | $d_C$ | $d_H$ | $d_C$ | $d_{\bar{H}}$ |
| n | 0.396 | 7.042 | 0.160 | 2.858 | **0.186** | **4.015** | 0.125 | **0.982** | 0.139 | **0.944** | 0.098 | 0.981 |
| n + div | **0.262** | **3.630** | **0.134** | **2.469** | 0.257 | 4.122 | 0.119 | 1.080 | **0.131** | 3.369 | **0.093** | **0.876** |
| div | 0.280 | 4.136 | 0.155 | 3.219 | 0.308 | 5.170 | **0.179** | 1.779 | 0.257 | 3.915 | 0.168 | 1.730 |

**表 7. 迭代时间性能结果。** 标准 `SIREN`（不包含法线估计阶段时间）与 `DiGS` 的对比。结果以毫秒（ms）报告。

| 方法 | SIREN | IGR | DiGS |
|---|---|---|---|
| 时间 [ms] | 5.2 | 17.5 | 12.0 |
| 参数数量 | 66.5 K | 2.1 M | 66.5 K |

在 `SRB` 数据集$^{12}$上的表面重建实验是在 `PyTorch` 中实现的，并在单个 `Nvidia RTX 2080` 上进行了训练。我们方法的 2D 实验架构是一个带有正弦激活函数（`SIREN`）的 4 层 `MLP`，每层有 128 个节点。我们的方法没有为标准的 `SIREN` 方法增加参数。

注意，为了计算散度项，计算时间会有增加，这主要归因于计算（并反传播）梯度的梯度。在推理时，`SIREN` 和 `DiGS` 具有相同的时间计算性能。注意，训练标准 `SIREN` 需要一个预处理法线估计阶段。表 7 报告了 2D 重建网络的参数数量和计时性能。它显示了与 `SIREN` 相比，`DiGS` 的训练时间（每次迭代）有所增加，但与 `IGR` 相比，`DiGS` 更快且参数更少。

## 7. 结论

我们引入了 `DiGS`，这是一种扩展的散度引导形状隐式神经表示方法，适用于没有任何预处理的原始无向点云。此外，我们推导了一种几何引导的正弦表示网络初始化，同时保留了高频率。最后，我们证明了 `DiGS` 重建高保真形状的能力，但在平和平细特征重建方面存在某些局限。我们报告了与不使用法线监督的其他方法相比的最先进结果，并证明我们的方法与使用此类监督的方法相比具有竞争力。

# 用于无向点云的 `eDiGS` 隐式神经表示

所有现有方法（包括我们的方法）在处理缺失数据和细特征方面都面临困难。未来的工作可以探索使用局部相似性来更好地处理这些区域。点云密度也是表示能力重要因素，可以在此方向进行额外工作。

## 参考文献

1. Y. Ben-Shabat, C. Koneput, and S. Gould. `DiGS`: Divergence guided shape implicit representation for unoriented point clouds. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, pp. 19323-19332 (2022).
2. J. J. Park, P. Florence, R. Newcombe, and S. Love. `DeepS`: Learning signed distance functions for shape. In CVPR, pp. 165-174 (2019).
3. L. Mescher, M. Oechle, S. Niemeyer, and A. Geiger. Occupancy networks: Learning 3D reconstruction in space. In CVPR, pp. 4460-4470 (2019).
4. S. Peng, M. Niemeyer, L. Mescher, M. Polleys, and A. Geiger. Convolutional occupancy networks. In ECCV (2020).
5. Z. Chen and H. Zhang. Learning implicit fields for generative modeling. In CVPR, pp. 5939-5948 (2019).
6. M. Atzmon and Y. Lipman. `SAL`: Agnostic learning of shapes from raw data. In CVPR, pp. 2565-2574 (2020).
7. M. Atzmon and Y. Lipman. `SAL`: Agnostic learning with derivatives. In ICLR (2021).
8. D. Urbach, J. Lariv, Y. Ben-Shabat, and M. Lindenbaum. `DPist`: Comparing point clouds using density. In ECCV, pp. 545-560 (2020).
9. A. Gropp, J. Lariv, N. Haim, M. Atzmon, and Y. Lipman. Implicit geometric regularization for learning shapes. In ICML, Vol. 119, pp. 3789-3799. PMLR (2020).
10. V. Sitzmann, J. Martel, A. Bergman, D. Lindell, and G. Wettstein. Implicit neural representations with periodic activation. In NeurIPS, Vol. 33 (2020).
11. S. Ramasinghe and S. Lucey. Beyond periodicity: Towards a unifying framework for coordinate-`MLPs`. In European Conference on Vision, pp. 142-158 (2022).
12. M. Berger, J. A. Levine, L. G. Nonato, G. Taubin, and C. T. Silva. A benchmark for surface reconstruction, ACM Transactions on Graphics 32, 1–17 (2013).
13. F. Bogo, J. Romero, G. Pons-Moll, and M. J. Black. Dynamic `FAUST`: Registering human bodies in motion. In CVPR, pp. 6233–6242 (2017).
14. A. X. Chang, T. Funkhouser, G. Gubas, P. Hanrahan, Q. Huang, Z. Li, S. Savvarese, M. Savva, S. Song, H. Su et al., `ShapeNet`: An information-rich 3D model repository. arXiv preprint arXiv:1512.0312 (2015).
15. F. Cazals and G. Jiesen. Delaunay triangulation surface reconstruction. In Effective Computational Geometry for Curves and Surfaces, pp. 271–276. Springer (2006).
16. R. Kolluri, J. R. Shewchuk, and J. F. O’Brien. Spectral surface reconstruction from noisy point clouds. In Proceedings of the 2004 Eurographics/ACM SIGGRAPH symposium on Geometry Processing, pp. 11–21 (2004).
17. F. Bernardini, J. Mittleman, H. Rusmeier, C. Silva, and G. Taubin. The ball-pivoting algorithm for surface reconstruction, IEEE Transactions on Visualization and Computer Graphics 5, 349–359 (1999).
18. N. Ament, S. Choi, and R. K. Kolluri. The power crust, unions of balls, and the medial axis transform, Computational Geometry 19, 127–153 (2001).
19. T. Grouix, T. Schneider, C. Silva, D. Zorin, J. Bruna, and M. Aubry. A papier-maché approach to learning 3D surface generation. In CVPR, pp. 216–224 (2018).
20. F. Williams, D. Panzozzo. Deep Geometric Prior for surface reconstruction. In CVPR, pp. 10130–10339 (2019).
21. Y. Jiang, D. Ji, Z. Han. Implicit geometric regularization for learning shapes. In ICML, Vol. 119, pp. 3789-3799. PMLR (2020).
22. S. Peng, M. Niemeyer, L. Mescher, M. Polleys, and A. Geiger. Convolutional occupancy networks. In ECCV (2020).
23. Z. Chen and H. Zhang. Learning implicit fields for generative modeling. In CVPR, pp. 5939-5948 (2019).
24. M. Atzmon and Y. Lipman. `SAL`: Agnostic learning of shapes from raw data. In CVPR, pp. 2565-2574 (2020).
25. F. Cazals and G. Jiesen. Delaunay triangulation surface reconstruction. In Effective Computational Geometry for Curves and Surfaces, pp. 271–276. Springer (2006).
26. R. Kolluri, J. R. Shewchuk, and J. F. O’Brien. Spectral surface reconstruction from noisy point clouds. In Proceedings of the 2004 Eurographics/ACM SIGGRAPH symposium on Geometry Processing, pp. 11–21 (2004).
27. F. Bernardini, J. Mittleman, H. Rusmeier, C. Silva, and G. Taubin. The ball-pivoting algorithm for surface reconstruction, IEEE Transactions on Visualization and Computer Graphics 5, 349–359 (1999).
28. N. Ament, S. Choi, and R. K. Kolluri. The power crust, unions of balls, and the medial axis transform, Computational Geometry 19, 127–153 (2001).
29. T. Grouix, T. Schneider, C. Silva, D. Zorin, J. Bruna, and M. Aubry. A papier-maché approach to learning 3D surface generation. In CVPR, pp. 216–224 (2018).
30. F. Williams, D. Panzozzo. Deep Geometric Prior for surface reconstruction. In CVPR, pp. 10130–10339 (2019).
31. Y. Jiang, D. Ji, Z. Han. Implicit geometric regularization for learning shapes. In ICML, Vol. 119, pp. 3789-3799. PMLR (2020).
32. M. Berger, J. A. Levine, L. G. Nonato, G. Taubin, and C. T. Silva. A benchmark for surface reconstruction, ACM Transactions on Graphics 32, 1–17 (2013).
33. F. Bogo, J. Romero, G. Pons-Moll, and M. J. Black. Dynamic `FAUST`: Registering human bodies in motion. In CVPR, pp. 6233–6242 (2017).
34. A. X. Chang, T. Funkhouser, G. Gubas, P. Hanrahan, Q. Huang, Z. Li, S. Savvarese, M. Savva, S. Song, H. Su et al., `ShapeNet`: An information-rich 3D model repository. arXiv preprint arXiv:1512.0312 (2015).
35. F. Cazals and G. Jiesen. Delaunay triangulation surface reconstruction. In Effective Computational Geometry for Curves and Surfaces, pp. 271–276. Springer (2006).
36. R. Kolluri, J. R. Shewchuk, and J. F. O’Brien. Spectral surface reconstruction from noisy point clouds. In Proceedings of the 2004 Eurographics/ACM SIGGRAPH symposium on Geometry Processing, pp. 11–21 (2004).
37. F. Bernardini, J. Mittleman, H. Rusmeier, C. Silva, and G. Taubin. The ball-pivoting algorithm for surface reconstruction, IEEE Transactions on Visualization and Computer Graphics 5, 349–359 (1999).
38. N. Ament, S. Choi, and R. K. Kolluri. The power crust, unions of balls, and the medial axis transform, Computational Geometry 19, 127–153 (2001).

- 40. M. M. Bronstein, J. Bruna, Y. LeCun, A. Szlam, and P. Van-derggheynst. Geometric deep learning: Going beyond Euclidean data, *IEEE Signal Processing Magazine* **34**, 18–42 (2017).
- 41. W. E. Lorensen and H. E. Cline. Marching cubes: A high resolution 3D surface construction algorithm. In *SIGGRAPH*, Vol. 21, pp. 163–169. ACM, New York, USA (1987).
- 42. M. Kazhdan and H. Hoppe. Screened Poisson surface reconstruction, *ACM Transactions on Graphics* **32**, 1–13 (2013).

## 第 6 章

# 通过虚拟深度的合成图像改进单目 3D 物检测

Chenheng He* 和 Lei Zhang†
香港计算科学，
香港理工大学，香港
*csche@comp.polyu.edu.hk
†cslzhang@comp.polyu.edu.hk

利用几何特征是增强单目 3D 物检测的常用方法。然而，由于缺乏深度信息，它们的性能受到了了限制。为了解决这一局限性，可以使用外部深度估计器来预测深度，但这种方法会显著降低模型的效率和灵活性。我们没有依赖于深度估计器，而是提出了一种使用增强训练数据训练的深度感知检测器。具体而言，我们利用参考图像及其对应的深度图来训练一个高效的渲染模块，该模块可以合成各种具有虚拟深度的写实图像。通过从这些图像学习，检测器能够调整其特征以适应深度变化。此外，我们引入了一个辅助模块，引导网络从深度图像中学习更具信息的表示。这两个模块在训练后都会被移除，因此在最终部署期间不会产生额外的计算开销。

C. He 和 L. Zhang

## 1. 引言

3D 物检测在自动驾驶中起着至关重要的作用，因为它能够实现对 3D 空间中物体进行准确的检测和定位，确保自动车辆长距离行驶的安全导航。虽然高端 `LiDAR` 传感器由于能够直接感知周围视觉环境的深度而在自动驾驶中被广泛应用，但 `LiDAR` 也存在一些局限性。`LiDAR` 传感器可能昂贵，易受恶劣天气的影响，并且对小物体通常生成稀疏的点云（图 1(a)）。相比之下，摄像头提供了更具成本效益的解决方案，并提供高分辨率图像，这有助于穿透挑战性的天气条件，并为小物体提供更好的可见性（图 1(b)）。这使得单目检测成为自动驾驶系统一种非常有前景的解决方案。

尽管近年来单目 3D 物检测的研究取得了显著进展，但与基于 `LiDAR` 的检测相比，仍然存在性能差距。¹–8 这种差距归因于单目图像不准确的深度估计。从单张图像估计物体深度本身是具有挑战性的。目前的单目 3D 物检测可以分为两类：

![](img/33889d5baeb11b5b76258ce18177dcf2_214_0.png)

(a) (b)

图 1. (a) `LiDAR` 生成的点云通常导致稀疏表示，特别是对于远处的物体，这使得准确感知这些物体变得具有挑战性。(b) 相比之下，高分辨率图像为这些小物体提供了更好的感知质量。

# 通过合成图像改进单目 3D 物检测

分为两种方法：基于几何约束的方法$^{9–22}$ 和基于深度估计的方法$^{23–32}$。前者旨在根据透视变换预测各种几何特征，并通过在取视约束内拟合这些特征来检测物体。有效的几何特征在物体深度与 2D 图像特征之间建立了稳健的关系。例如，远处的物体倾向于看起来很小并位于图像的上部，而近处的物体则倾向于较大且位于图像的底部。通过从这些图像学习，检测器调整其特征以适应深度变化。此外，我们引入了一个辅助模块，引导网络从深度图像中学习更具信息的表示。这两个模块在训练后都会被移除，因此在最终部署期间不会产生额外的计算开销。

虽然几何约束可以暗示深度，但它们缺乏深度信息。通常，深度估计器在深度真值数据集上训练。深度估计器的密集深度预测为检测模型提供了丰富的上下文。

![](img/33889d5baeb11b5b76258ce18177dcf2_215_0.png)

图 2. (a) `3D-RPN` 的检测结果显示了不同尺度和位置的物体。(b) 相比之下，使用合成图像训练的模型可以更好地估计物体深度。

在本文研究中，我们提出了一种利用深度图像来增强 3D 物检测的新型框架。与其依赖深度估计器，我们提出了一种使用增强训练数据训练的深度感知检测器。具体而言，我们利用参考图像及其对应的深度图来训练一个高效的渲染模块，该模块可以合成各种具有虚拟深度的写实图像。通过从这些图像学习，检测器能够调整其特征以适应深度变化。此外，我们引入了一个辅助模块，引导网络从深度图像中学习更具信息的表示。这两个模块在训练后都会被移除，因此在最终部署期间不会产生额外的计算开销。

为了合成具有虚拟深度的图像，我们从传统的新视角合成方法中汲取灵感，并引入了一个高效的渲染模块。该模块利用深度来重建参考图像的 3D 场景，并从虚拟相机生成图像

![](img/33889d5baeb11b5b76258ce18177dcf2_216_0.png)

图 3. 参考图像（红色）及其对应的合成深度图像（黄色）示例，其深度分别为 -1、+1、+2、+3 和 +4 米。

真值边界框也会根据相机位移进行偏移，产生合成对作为增强数据。重要的是，检测模型从这些图像中学习具有挑战性。首先，使用的深度图像通常是稀疏的，导致合成图像包含许多空洞且语义有限。其次，由于校准误差，深度图像可能与相机图像完美匹配。物体边缘不匹配的深度像素会导致合成图像出现严重的扭变和伪影。为了解决这些问题，我们提出了一种多阶段渲染模型，从粗到精地生成高质量的合成图像。

此外，我们开发了一个与检测模型骨干协同工作的辅助模块。该辅助模块利用骨干特征进行深度估计，并通过像素级损失对其进行联合优化。通过这种方式，检测模型可以对场景几何获得更好的理解，并实现可靠的 3D 边界框预测：

- * 提出了一种新型数据增强策略，通过生成具有虚拟深度的图像来提高 3D 物检测的泛化能力。
- 提出了一个高效的渲染模块，从粗到精地合成图像。
- 开发了一个辅助模块，通过像素级深度估计任务联合优化检测特征，从而实现更准确的边界框推理。

## 2. 相关工作

**基于几何约束的单目检测：** 有效利用几何先验可以增强单目 3D 物检测的性能。`Brazil` 等人^{10} 引入了一种 2D–3D 锚点机制，利用 2D 图像特征进行 3D 边界框检测。`Mousavian` 等人^{11} 和 `Naiden` 等人^{12}

采用了 2D–3D 视角约束来稳定 3D 边界框预测。`Liu` 等^{13} 和 `Li` 等^{17} 提议基于一组关键点来估计 3D 边界框。`Qin` 等^{14} 和 `Zhou` 等^{15} 将检测任务分解为多个子任务，并在全局语文中进行优化。`Chen` 等^{16} 利用了物体与其遮挡邻居之间的空间约束，引入成对距离函数来调节边界框预测。`Ruddick` 等^{9} 使用 3D 空间中的正交变换将 2D 图像特征转换为俯瞰视图。`Zhang` 等^{38} 提出了针对正常物体和截断物体的解耦预测。`Chen` 等^{19} 提出了一种自监督框架，用于同时学习密集对应和几何结构。`Peng` 等^{21} 将物体重新定义为视觉表面深度和属性深度的组合。`Gu` 等^{22} 引入了单应性损失来探索场景中所有物体之间的相互关系。`Li` 等^{20} 对多个深度估计候选结果采用投影约束，并通过图匹配合并这些候选结果，以获得更准确的深度估计。

在本章中，我们证明了所提出的合成图像可以有效补充多种基于几何约束的检测器^{10,13,17}并通常提高它们的检测性能。

## 基于深度估计的单目检测：深度图像可以有效补偿 3D 图像的缺失。基于伪 `LiDAR` 方法^{26,27,33} 探索了将从单目输入的深度图像转换为伪 `LiDAR` 表征，从而利用点云检测器更好地捕捉物体结构。`Qian` 等^{28} 设计了一种软量化技术，将深度图像转换为点云检测器的体素输入，实现了端到端学习。`Ma` 等^{29} 对伪 `LiDAR` 表征进行了深入研究，并提出了一种基于坐标变换的 2D CNN 高效方案。除了伪 `LiDAR` 转换外，`Xu` 等^{23} 引入了一种多级融合算法，逐步聚合来自 RGB 和深度图像的特征。`Ding` 等^{25} 提出了一种深度感知模型，其中卷积感受野通过深度图像进行动态调整，以处理不同深度层面的图像内容。

# 通过合成图像改进单目 3D 物体检测

与上述在推理期间需要深度估计的方法不同，我们提出的框架仅在训练阶段利用深度信息，从而实现了更高效的检测过程。

**新视角合成**：新视角合成在视觉和图形社区已得到广泛探索。早期方法$^{39-42}$ 主要关注直接的图像到图像变换，以实现端到端的视角操控。随后的方法$^{34-37,43,44}$ 转向学习场景几何结构，例如点云、多平面图像或隐含表面。这些方法能够利用估计的 3D 表征生成高自由度的连续新视角。

在这项研究中，考虑到单目检测器对深度变化的敏感性，我们通过沿 *z 轴*（对应于深度方向）固定目标视角来合成图像。这种方法允许我们避免外推视角以及从未观测视角的处补全未知信息的需求。

## 3. 方法论

### 3.1. 总体学习框架

我们提出的学习框架如图 4 所示。它由三个主要部分组成：检测模块、渲染模块和辅助深度估计模块。渲染模块将 RGB 图像及其对应的稀疏深度图像作为输入，在不同的虚拟深度下生成一组合成图像。这些合成图像被用作增强数据来训练检测器。另一方面，深度估计模块通过深度预测任务与像素级损失联合优化，从而增强检测模型的骨干网络特征。训练后，渲染模块和辅助模块均被移除，仅部署学习到的检测器。在本章中，我们展示了该学习框架对各种现有单目检测器^{10,13,17,18}的适应性。我们通常将带有增强设计的检测模型称为 `AugMono3D`。随后的子节将详细介绍 `AugMono3D` 的每个组件和训练方案。

![](img/33889d5baeb11b5b76258ce18177dcf2_220_0.png)

图 4. 所提学习框架的概述。该框架包含一个检测模型、一个用于合成虚拟深度图像的渲染模块，以及一个用于转换骨干特征以密集深度预测的辅助深度模块。

# 通过合成图像改进单目 3D 物体检测

### 3.2. 合成虚拟深度图像数据增强

为了增强单目检测器区分物体深度的能力，我们通过生成具有虚拟深度的合成图像来增强训练数据。整体流水线如图 5 所示，我们利用深度信息进行虚拟视角合成，并利用内补网络填充具有缺失值的像素。

我们首先根据其对应深度图像 $D$ 的非零值将参考图像映射为 3D 点云。参考图像中每个位置 $(u, v)$ 的 3D 坐标计算如下：

```
