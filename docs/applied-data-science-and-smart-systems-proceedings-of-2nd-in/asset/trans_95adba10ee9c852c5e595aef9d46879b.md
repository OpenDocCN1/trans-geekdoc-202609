
-   [精确分类视网膜图像的决策，因为它揭示了图像内容的信息。每个阶段的图像均按照以下方程给出的左、右、上、下的标准进行计算。]

$$\operatorname{whiteregion} = e\left( cir_{i} \right) = e\sum_{i = 0}^{f} w_{\cdot j}x_{i} - w_{0j}$$

where the white region images have larger in the non-drowsy. The planned retina picture estimate decision as it reveals the information contained inside the picture information. The picture of every stage is calculated as the standard of the left, right, up, and down as given by the following equations.

$$\operatorname{blackregion} = e\left( cir_{j} \right) = e\sum_{j = 0}^{f} b_{\cdot i}y_{j} - b_{0i}$$

| Algorithm for HC |
| --- |
| Multi-stage range of R-curve |
| Step 1. || Circle Selection: Fit a circle to the locate of the person bend bi and bright pixels in The dark state |
| Step 2. || Select the bend lie in the environs of this circle for the point |
| Step 3. || Superior Selection: the bend into two categories: a) black, b) white |
| Step 4. || Calculate the close relative vessel-segment direction bθi For each bend bi |
| Step 5. || Examine each picture in steps of 90° |
| Step 6. || if circle/curve (s) exist then |
| Step 7. || if bi |
| Step 8. || is right then |
| Step 9. || if numerous then |
| Step 10. || choose r-bend with the least bend angle |
| Step 11. || else |
| Step 12. || choose r-bend |
| Step 13. || end if |
| Step 14. || end if |
| Step 15. || else |
| Step 16. || carry on |
| Step 17. || end |

### 结果与讨论

作为睡眠iness的度量，整个会话期间使用MATLAB程序测量了眼睛水平和眼睛睡眠的比例，仅用于数据目的。

### 数据集

该方法通过利用精心挑选的MRL眼部数据集来展示睡眠iness检测，该数据集是为高效分类任务而设计的专门子集。它包含了人眼的红外图像的多样化范围，包括在不同光照条件和不同成像设备下获得的低质量和高质量照片。该数据集非常适合评估多种特征或可训练的分类模型。为了便于算法比较，图像被分为多个类别，使其非常适合训练和测试分类算法。总体而言，数据集包含216张照片，其中194张描绘非睡眠状态的主体，22张描绘出现睡眠iness的个体。

### 性能指标

为全面评估拟议和现有算法的有效性，采用了多种性能指标。拟议算法的性能评估包括PSNR（峰值信噪比）、召回率、平均绝对误差（MAE）、精确率、执行时间、准确率和F分数。这些指标全面、深入地考察了算法在各个方面的表现，确保对其能力的稳健评估。

### 预处理

[Figure 28.5](#ch28.xhtml#fig28_5) 表示使用噪声抑制、锐化、对比度和亮度对右眼图像进行预处理后的PSNR结果图。[Figure 28.4](#ch28.xhtml#fig28_4) 展示了本工作中拟议预处理与对比的预处理图像对比。通过分析可知，在本工作中亮度在其他方法中提供了更好的预处理效果。

![Figure 28.4 Pre-processing using noise reduction, sharpness, contrast, brightness](images/fig28_4_C.jpg)

[Figure 28.4 Pre-processing using noise reduction, sharpness, contrast, brightness](#ch28.xhtml#R_fig28_4)

![Figure 28.5 Pre-processing result using noise reduction, sharpness, contrast, brightness](images/fig28_5_C.jpg)

[Figure 28.5 Pre-processing result using noise reduction, sharpness, contrast, brightness](#ch28.xhtml#R_fig28_5)

### 分割

[Figure 28.6](#ch28.xhtml#fig28_6) 展示了使用E\_GRUNS算法对右眼图像阈值1.5、1.6、1.8以及阈值1.7的分割比较。

![Figure 28.6 Segmentation comparisons for right eye image threshold 1.5, 1.6, 1.8 and image threshold 1.7 using E\_GRUNS algorithm](images/fig28_6_C.jpg)

[Figure 28.6 Segmentation comparisons for right eye image threshold 1.5, 1.6, 1.8 and image threshold 1.7 using E\_GRUNS algorithm](#ch28.xhtml#R_fig28_6)

### 分类器性能

基于HC结果，属性导向结论是为了获得更好的性能。在分割中，每个不同的图像属性集独立估计并测试，并计算结果。整体质量属性将由用于质量属性图像的描述数据集组成，并可根据图像的变化进行结果的灵活性。此外，更好的图像质量用于统计睡眠值，从而确定睡眠阶段，即睡眠、清醒、困倦阶段。HC算法的分类结果与现有NB、k‑NN和SVM技术进行比较。本章实现的HC算法在下一章将用于与其他现有技术的睡眠值比较。[Table 28.1](#ch28.xhtml#tab28_1) 展示分类性能分析。

[Table 28.1 Performance analysis of classification.](#ch28.xhtml#R_tab28_1)

| Classification algorithms || Pre. || Rec. || F-Sc. || Acc. || MAE || Execution time |
| --- | --- | --- | --- | --- | --- | --- |
| NB || 77.39 || 79.49 || 78.42 || 75.16 || 0.168 || 2084 |
| --- | --- | --- | --- | --- | --- | --- |
| SVM || 83.64 || 85.74 || 84.67 || 86.79 || 0.152 || 1831 |
| KNN || 87.07 || 89.17 || 88.1 || 89.32 || 0.139 || 1725 |
| Proposed HC || **89.65** || **91.75** || **90.68** || **90.12** || **0.109** || **1407** |

[Figure 28.7](#ch28.xhtml#fig28_7) 展示分类器的性能分析。观察结果表明，拟议的HC算法在精度、准确率、F‑score和召回率方面均优于其他分类算法。[Figure 28.8](#ch28.xhtml#fig28_8) 显示平均绝对误差。实验结果表明，拟议的HC算法的平均绝对误差最小，优于其他分类算法。[Figure 28.9](#ch28.xhtml#fig28_9) 展示执行时间。观察结果表明，拟议的HC算法的执行时间最短，优于其他分类算法。

![Figure 28.7 Performance analysis of classifiers](images/fig28_7_C.jpg)

[Figure 28.7 Performance analysis of classifiers](#ch28.xhtml#R_fig28_7)

![Figure 28.8 Mean absolute error](images/fig28_8_C.jpg)

[Figure 28.8 Mean absolute error](#ch28.xhtml#R_fig28_8)

 ![Figure 28.9  Execution time](images/fig28_9_C.jpg)

[Figure 28.9  Execution time](#ch28.xhtml#R_fig28_9)

## 结论

