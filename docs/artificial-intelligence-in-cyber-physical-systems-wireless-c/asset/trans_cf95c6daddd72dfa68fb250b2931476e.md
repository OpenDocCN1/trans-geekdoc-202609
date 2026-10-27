

## 参考文献

- [21] Qi, M., Zhou, Z., Liu, J., Cao, J., Wang, H., Yan, A., Wu, D., Zhang, H., and Tang, L., “Image De-noising Algorithm via Spatially Adaptive Bilateral Filtering.” Advanced Materials Research, 760–762, 1515–1518, 2013.
- [22] Zhang, M., and Gunturk, B., “Multiresolution Bilateral Filtering for Image De-noising.” IEEE Transactions on Image Processing, 17, 12, 2324–2333, 2008.
- [23] Ramananda, S., Lehmann, B., and Kraus, D., “Optimal parameters for bilateral filtering and SAS image de-noising,” 2011 International Symposium on Ocean Electronics, 2011.
- [24] Shi, H., “Determination of bilateral filter coefficients based on particle swarm optimization,” 2012 5th International Congress on Image and Signal Processing, 302–306, 2012.
- [25] Farooq, M., “Application of genetic algorithm & morphological operations for image segmentation,” International Journal of Advanced Research in Computer and Communication Engineering, 4, 3, 2015.
- [26] D. Bhattacharyya, K. Taihoon, “Brain Tumor Detection Using MRI Image Analysis,” Communications in Computer and Information Science, 151, 2011, 307–314.
- [27] M. H. Chowdhury, W. D. Little, “Image thresholding techniques,” IEEE Pacific Rim Conference on Communications, Computers and Signal Processing, Proceedings, 17–19 May 1995, 1995, 585–589.
- [28] P. K. Sahoo, S. Soltani, A. K. C. Wong, and Y. C. Chen, “A Survey of thresholding techniques,” Computer Vision, Graphics, and Image Processing (CVGIP), 41, 1988, 233–260.
- [29] M. Sezgin, B. Sankar, “Survey over image thresholding techniques and Quantitative performance evaluation,” Journal of Electronic Imaging, 13, 1, 2004, 146–165.
- [30] S. Xavierarockiaraj, K. Nithya, R. Maruni Devi, “Brain tumor Detection using Modified Histogram thresholding Quadrant approach,” Journal of Computer Applications, 5, 1, 2012, 21–25.
- [31] P. L. Lions, J. M. Morel, T. Coll, “Image selective smoothing and edge detection by nonlinear diffusion.” SIAM Journal on Numerical Analysis, 29, 1, 1992, pp. 182–193.
- [32] R. C. Gonzalez, R. E. Woods, “Digital Image Processing,” 3rd Edition, Pearson Education, 2007.
- [33] N. R. Pal, S. K. Pal, “A Review on Image Segmentation Techniques,” Pattern Recognition, 26, 9, 1993, 1277–1294.
- [34] W. X. Kang, Q. Q. Yang, R. R. Liang, “The Comparative Research on Image Segmentation Algorithms,” IEEE Conference on ETCS, 2009, 703–707.
- [35] R. C. Gonzalez, R. E. Woods, “Digital Image Processing,” 3rd Edition, Pearson Education, 2007.
- [36] S. Varshney, N. Rajpal, R. Purwar, “Comparative Study of Image Segmentation Techniques and Object Matching using Segmentation,” Proceedings of International Conference on Methods and Models in Computer Science, 2009, 1–6.
- [37] H. Zhang, J. E. Fritts, S. A. Goldman, “Image Segmentation Evaluation: A Survey of unsupervised methods,” Computer Vision and Image Understanding, 2008, 260–280.
- [38] Dzung L. Pham, Chenyang Xu, Jerry L. Prince, “A Survey of Current Methods in Medical Image Segmentation,” Technical Report JHU/ECE 99-01, Department of Electrical and Computer Engineering, 1998.
- [39] X. Jiang, R. Zhang and S. Nie, “Image Segmentation Based on PDEs Model: A Survey,” 2009 3rd International Conference on Bioinformatics and Biomedical Engineering, 2009, 1–4.
- [40] Damodaran, S. and R. Dhanasekaran, “Segmentation of cerebrospinal fluid and internal brain nuclei in brain magnetic resonance images,” International Review on Computers and Software, Vol. 8, 5, 2013, 1063–1071.
- [41] Chan, T. F., and L. A. Vese, “Active contours without edges.” IEEE Transactions on Image Processing: A Publication of the IEEE Signal Processing Society, 10, 266–277, 2001.
- [42] T. Zhang, Y. Xia and D. D. Feng, “A deformable segmentation algorithm for brain M.R. images,” 2012 Annual International Conference of the IEEE Engineering in Medicine and Biology Society, 2012, 3215–3218.
- [43] D. Mumford and J. Shah, “Optimal approximations by piecewise smooth functions and associated variation problems,” Communications on Pure and Applied Mathematics, 42, 577–685, 1989.
- [44] C. Tomasi and R. Manduchi, “Bilateral Filtering for Gray and Color Images,” Sixth International Conference on Computer Vision (IEEE Cat. No. 98CH36271), 1998, 839–846.
- [45] Rami Cohen, “The Chan-Vese Algorithm,” Computer Vision and Pattern Recognition, arXiv:1107.2782.
- [46] K. Babburu, K. Gurucharan, S. S. Kiran, P. Srujana, “PAPR Reduction Techniques, and Image Quality Assessment in Image-Based MMS VLC System,” I.T. in Industry, 9, 2, 2021.

| 章节 | 页码 |
| --- | ---: |
| 9.8.3 数据增强 | 163 |
| 9.8.3.1 数据增强技术 | 164 |
| 9.9 图像分类技术 | 164 |
| 9.9.1 SVM模型 | 165 |
| 9.9.2 决策树模型 | 165 |
| 9.9.3 k近邻模型 | 166 |
| 9.9.4 人工神经网络（ANN）模型 | 167 |
| 9.9.5 CNN模型 | 167 |
| 9.10 结论 | 168 |
| 参考文献 | 172 |

## 9.1 引言

这个世界包含数以百万计的生物。那么，人们如何区分它们呢？因此，有必要区分不同的事物、颜色、气味以及所有生物的生活方式。任何生物要执行任何行动，都必须具备辨别能力，以区分它们通过感觉器官从外部世界获得的不同输入。在日常的每一项任务中，从早晨开始，人类就能轻松地区分一个物体与另一个物体。本文所讨论的物体是指可以被看见和观察到的物理实体。它可以包括简单的物体，如你的汽车和电视。在被捕获的图像和视频中可以看到各种不同的物体。

如图9.1所示，目标检测是与图像分类、目标识别、目标分割或语义分割类似的计算机视觉任务。随着计算机视觉模型中深度学习算法的近期进展，上述任务变得日益重要，从而提升了性能并实现了实时应用场景。

如图9.2所示，图像分类实际上是为图像中的物体分配类别标签，然后识别物体的类别。图像分类基于图像特征进行工作。目标定位也是计算机视觉预处理任务之一，它在给定图像中的物体周围绘制边界框，从而识别感兴趣目标的位置。

物体的尺寸是对物体外观观察的一部分。在物体尺寸的众多用途中，尺寸可用于广泛的测量和估算。在这些情况下，可能需要复杂级别的图像处理来获得精确的尺寸。一些一般性任务包括以下内容：

1. 预测零件和产品的最小和最大尺寸
2. 估算金属零件的圆度和角度的精确尺寸，以确保准确装配。

目标检测和尺寸预测的任务涉及将简单、不可靠的低级测量/尺寸值转换为复杂、高级的尺寸描述/启发式信息。目标检测和目标识别在计算机视觉领域有着众多应用，并具有广泛的研究空间。其中一些应用包括自动驾驶汽车、监控系统以及图像/目标提取。物体尺寸预测构成了目标检测和识别的下一阶段。

![](img/56cfba5af06305175d6488aec4d55ab0_181_0.png)

**图9.1** 单个物体检测（台灯、沙发桌、桌子、花盆）。

![](img/56cfba5af06305175d6488aec4d55ab0_181_1.png)

**图9.2** 图像分类。

为了解物体的大小，图像分割可以帮助从图像中分割出所需区域，从而更容易识别其形状和大小。图像分割和目标检测是该实现的后续步骤。

