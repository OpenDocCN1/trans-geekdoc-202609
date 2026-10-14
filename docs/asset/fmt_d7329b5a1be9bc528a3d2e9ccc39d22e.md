
Segmentation is process of partition the image into different parts, also called regions or areas. Methods based on regions, intensity normalization, and partial volume medical images are segmented using level set segmentation algorithms to quantify delineated structures so that pertinent information can be extracted. Medical images those are visually ambiguous. Identifying data of interest and their boundaries exactly might help doctors in future investigations but it is also challenging due to tissue and organ architecture as well as noise. There are different types of segmentation techniques used in medical imaging especially to deals with intensity homogeneity. Intensity homogeneity is the common problem in medical imaging and can have an impact on segmentation accuracy. Edge-based and region-based models have been widely used in segmentation. Techniques that are deal with intensity inhomogeneity are regionbased methods, intensity normalization, partial volume segmentation and level set methods. Chan-Vese and active contour methods comes under level set category. Many medical pictures include haze or weak edges, especially in MRI brain imaging with extensive areas of blurring grey-white matter boundaries (Xiaoxia et al., 2017). Edge-based algorithms often use noisy images with weak edges. Image area is used instead of gradient information in region-based techniques (Naresh et al., 2010; Ge et al., 2012; Singh et al., 2019). In images with weak object boundaries, edge-based models perform better. This model can quickly figure out the boundaries of objects no matter how the level set is made. Active contour models may be parametric or geometric in nature. Their contours are made up of parameterized curves. The snake model is a popular parametric active contour model (Guo et al., 2013). Many active contour techniques assume that global intensity may be used to define a picture. Many people have come up with a truly global way to promote several contours to separate multiple-region images, like Chan and Vese (Sun et al., 2018). The Mumford-Shah function serves as the foundation for the CV model (Liu et al., 2012). A model is made from a picture. As a result, it works well for objects with weak or defined borders but not so well for pictures with inhomogeneous intensity. Many medical images have different levels of intensity because of flaws in the object or technical limitations (An et al., 2007; Krupinski, 2010; Modi et al., 2021). There are several solutions to the CV model’s flaws. For two models that are regionally comparable (Vese, 2002). Any region-based segmentation energy, according to Lankton and Tannenbaum (Hemalatha et al., 2018), can be recast locally. Active contour energy is being used to segment objects with variable statistics. However, they are CPU-intensive, which suggests an initial contour at the object’s edges. Zhang et al. (2010) and Li et al. (2020) provide region-based active contour models for dealing with intensity inhomogeneity. Local binary fitting (LBF) and regionscalable fitting (RSF) are the most frequently used models by Li et al. The LBF model makes use of local image data. The RSF model makes use of local intensity data. Both models may be used at the same time (Chuanjiang et al., 2012) (Figure 42.1).

```
![Figure 42.1 The segmentation outcomes](img/fig42_1_C.jpg)
```

Figure 42.1 The segmentation outcomes

## 相关工作

许多真实世界图像表现出强度异质性。在医学图像（如 X 光和 MRI（磁共振））中普遍存在（Vovk et al., 2007）。射频线圈或成像过程会产生不均匀强度的非 MRI 图像。相同组织的强度会随时间变化。在 CT 和超声图像中，非均匀束衰减会产生类似问题。新的 RSF 模型（Brox et al., 2009）研究了强度异质性对分割的影响。RSF 模型利用地理上波动的局部数据（Zhi et al., 2015; Koshki et al., 2021）。这是因为 RSF 模型可以利用局部区域信息（即局部强度均值）有效进行分割。一些最近的建议处理强度不均匀性的方式与被 RSF 模型所采用。然而，某些方法需要设置，这限制了其适用性。依赖初始轮廓位置是局部信息模型的主要缺陷，求解 EulerLagrange 方程减少了能量函数。这些模型包含局部和全局强度拟合能量（Wang et al., 2014）。两个模型的局部强度拟合项常被结合，以观察它们在不同位置对曲线创建的影响。在此情况下，全局强度信息占主导地位。轮廓被绘制到物体边界上，然后停止。利用局部图像对比度修改其权重（Wang et al., 2010; Memon et al., 2020）。在弱物体边界处，全局强度力会导致轮廓发散。需要更具辨识度的能量函数以提升模型性能。轮廓的发展由分歧性和拟合性控制。新引入了区域可扩展的分歧性和能量功能。虽然其对应词语描述强度，但该词区分背景和前景。能量通过水平集正则化计算。与常规区域和区域可扩展模型相比，它更好地管理强度不均匀性，因为其初始化更灵活。新模型优于旧模型。首先，新能量函数提供了适当的前景/背景分割。该方法同时保留局部和全局数据。现在轮廓更为敏感。这些照片突显了过程的准确性和持久性。Piovano 等人利用卷积加速分段平滑。它直接处理图像强度和空间变化。与 Chunming et al. (2009)建议的分段平滑模型不同，它更少依赖初始轮廓位置。另一方面，地质活动轮廓和 ChanVese 模型在此模型中结合。地质强度拟合（GIF）模型被创建。随后，出现了两个模型：全局 GIF 模型和局部 LGIF 模型。全局 GIF 模型用于图像大小均匀的图像。局部 LGIF 模型考虑强度不均匀性。新函数将利用全局和局部数据快速得到正确的响应。CV 模型提供全局数据。局部信息通过 Wan et al. (2018)的能量范式解释，使用拟合权重避免计算成本高且错误的分割。它在许多图像处理和计算机视觉应用中被广泛使用。活动轮廓模型和模糊 C-means（FCM）是两种著名的图像分割方法。医学图像分割仍然困难，因为存在噪声、对比度差和强度变化大。混合区域基于轮廓模型（HRBAC）也有效处理强度不均匀性（Liu et al., 2014; Xu et al., 2014）。该方法结合了全局和局部区域基于活动轮廓模型的优势。局部区域基于活动轮廓（LRBAC）和 GIF 也能处理强度不均匀性，但可能计算成本高或对初始化敏感。

## MR 图像分割

在医学成像中，噪声有时是普遍现象。严重噪声会显著降低图像的清晰度，遮蔽并阻碍观察图像中特定特征，这会影响分割效果（Figure 42.2）。

![Figure 42.2 左侧表示带噪声的 MRI 图像，右侧表示无噪声图像](img/fig42_2_B.jpg)

Figure 42.2 左侧表示带噪声的 MRI 图像，右侧表示无噪声图像

为了展示其对强度不均匀性的容忍性，使用偏置场效应对两张 MRI 脑部图像进行分割。由于分割平衡良好，图像质量得到了提升。在进行偏置校正后，可见若干低对比度区域（Figure 42.3）。

![Figure 42.3 真实医学图像用于测试该过程。列 1 包含原始图像和轮廓。列 2 包含最终轮廓。列 3 包含经过偏置校正的照片。列 4 包含估计的偏置场](img/fig42_3_C.jpg)

Figure 42.3 真实医学图像用于测试该过程。列 1 包含原始图像和轮廓。列 2 包含最终轮廓。列 3 包含经过偏置校正的照片。列 4 包含估计的偏置场

将该方法与 C-V 模型（Chan et al., 2001）、Li 的模型（Li et al., 2011）和 LGDF（Wang et al., 2009）进行比较。第一行展示了左心室超声图像，具有急性强度不均匀性和噪声问题（Figure 42.4）。左心室位于第二行。图像明显受噪声、高强度不均匀性和弱边界影响。第三行展示了心血管 CT 图像。C-V 模型利用全局强度均值来拟合图像，因此表现出不同程度的困难。Li 的模型利用局部强度均值，可能比 C-V 模型更好地分割强度不均匀的图像。LGDF 模型仅基于局部强度数据，无法量化偏置场。此外，该方法不仅预测偏置场以修正源图像的亮度不均匀，还更好地将图像分割为独立部分。

![Figure 42.4  替代方法进行比较。列 1 显示原始图像和初始轮廓。列 2 展示 C-V 模型。列 3：Li 的方法。列 4：LGDF 模型。列 5 - 在这种情况下，应遵循该方法](img/#ch42.xhtml#R_fig42_4)

该方法与 Chan-Vese（CV）（Wong et al., 2005）、RSF 和 LGIF（Kass et al., 2008）进行了比较。这些模型通常包含全局、局部和组合强度数据。为加速演化，对初始轮廓内外的二元函数值被应用于初始轮廓。以下子节包含不同实验图像的参数值。

## 发现

实验证明，自动分割方法无法为医学图像提供正确的分析。

# 43 电动减震器的设计与性能分析

Jenish R. P.^(⁴³)

计算机科学与工程系，旁遮普邦，印度

DOI: [10.1201/9781003471059-43](https://dx.doi.org/10.1201/9781003471059-43)

## 摘要

现代车辆在动力学方面已取得显著进展，这主要归功于传动系统产生的振动减小以及减震器的阻尼效果。然而，传统减震器的效果受到其固有机械结构的限制，通常将其限制在固定输出水平。值得注意的是，豪华汽车通过集成可变输出的减震器来优化舒适性和性能，从而与其他车型区分开来。本文深入探讨了一个具有普遍适用性的前沿概念：电动减震器，其可变输出适用于所有车辆类型。核心目标是揭示这一新型悬挂技术的潜力及其对车辆动力学的变革性影响。通过对电动减震器可变输出的研究，本文为不断发展的领域做出贡献，该领域有望重新定义车辆舒适性和操控性。将该概念应用于所有车辆，为实现更标准化和提升的驾驶体验开辟了道路，超越了豪华车辆的局限。通过对电动减震器可变输出的全面探索，本研究踏上了革命车辆动力学领域的旅程，承诺带来更优的乘坐质量和增强的操控性。

关键词：减震器、液压阀、bode 图、PID 控制器

## 引言

随着电动汽车（EVs）对环境条件产生的影响日益显著，汽车制造业正致力于打造既高效又耐用的车辆。电动汽车相较于传统内燃机，具有产生更小电机振动的独特优势。此外，其零部件数量的减少有助于降低整体车辆振动水平（www.audi-technology）。然而，车辆振动管理的一个关键方面仍未得到解决——前后车轮的行驶频率。车辆的整体动态，包括俯仰、倾斜、前束和后束角等参数，被精心调校以提升动态稳定性。冲击吸收器在提升稳定性方面发挥着至关重要的作用，它们对车辆平衡拥有显著控制权（Shams et al., 2007）。

通过在行驶过程中引入对减震器阻尼的可变性，有望增强稳定性并降低前后车轮的行驶频率。

“电动减震器”这一术语并不意味着电磁悬挂（www.motortrend.ca）。相反，本文探讨了利用频率响应方法来控制减震器的实现（www.popularmechanics.com）。

频率响应方法提供了一种强大的手段，用于调节这些关键悬挂部件的性能。

它是通过对这种基于频率的方法进行研究，本文旨在在电动汽车（EV）背景下解决减振器性能优化的挑战（`Tiwari et al., 2020`）。通过利用电动减振器的内在特性，这项研究旨在阐明提升车辆稳定性和提供更精细驾驶体验的道路（`Faheem et al., 2016`）（`Figure 43.1`）。

![Figure 43.1 Electric shock absorbers](img/fig43_1_B.jpg)

Figure 43.1 Electric shock absorbers

## 相关工作

使用可变输出电动减振器的想法是文献综述的主要议题。文章讨论了减振对舒适性和稳定性的重要性，尤其是在电动汽车中。文章强调了使用可调减振比的电动减振器以提升车辆动力学并减少振动。

电动减振器很重要。文章在评估的开头就讨论了减振器在现代汽车中的重要性，特别关注它们如何减少传动系统振动并改善驾乘质量。虽然可变输出减振器是高端汽车的特征，但文章指出传统减振器（固定输出）的局限性（`Fateh et al., 2009`）。

### 可变输出电动减振器的概念

本文提出了适用于各类汽车的可变输出电动减振器的设想。通过在行驶过程中调节阻尼比，这些电动减振器旨在提高稳定性并降低行驶频率（`Amar et al., 2011`）。

### 电动减振器的设计与控制

文献综述详细阐述了电动减振器的设计与控制方法。它描述了将传统减振器内置的阀门（shimequipped damping valve）替换为电机控制的旋转阀的方案。研究指出，通过旋转阀来调节阻尼比，可以调节前后轮的行驶频率并提升车辆动力学（`Guo et al., 2004`）。

频率响应技术被列为调节电动减振器阻尼比的有效策略。通过频率响应技术，可以使用频率响应图（Bode graphs）和 PID 控制器根据所需的行驶频率调节阻尼比。此外，`Gupta et al., 2006` 提到使用红外传感器来测量输入负载或扰动。

### 分析与仿真

研究利用 Simulink 和 MATLAB 对电动减振器模型进行理论分析与仿真。系统采用二阶方程表示，并为深入研究构建了若干子系统（`Hrovat et al., 1997`）。

### 结果与结论

分析结果在文献综述中展示，验证了该方法的有效性，通过展示阻尼频率随阀旋转的变化。

### 特性与结论

可变输出电动减振器提供了类似豪华车的阻尼控制功能。本文结论认为，通过电机控制的阀门动态调节悬挂，可以显著降低振动并提升车辆舒适性和稳定性（`Raman et al., 2017`）。
