
**图 4：**不同方法下非均匀照明合成的视觉示例。 (a) 我们提出的基于物理模型和领域知识的非均匀合成方法。 从左到右分别为良好照明的视网膜图像、平滑后的照明掩膜和合成视网膜图像。 不同颜色代表照明掩膜中的不同值。 (b) 基于随机噪声的传统非均匀照明合成方法。 从左到右分别为放大细节、我们的细节（上）和传统方法的细节（下）、用于模拟非均匀照明的随机噪声图，以及通过随机噪声合成的视网膜图像。 很明显，传统的合成方法忽略了视网膜图像的特征，这导致合成视网膜图像不完美。 相比之下，我们的方法生成了具有非均匀照明的逼真视网膜图像，尤其是在视杯区域。

我们使用 `TensorFlow` 在一台配备 Intel(R) `i7 6700` CPU、32GB RAM 和 NVIDIA GeForce GTX 1080Ti GPU 的 PC 上实现网络。 在训练期间，采用批量大小为 8。 滤波器权重通过 `Xavier` 初始化。 我们使用 `ADAM` 进行网络优化，并将学习率固定为 `1e^(-4)`。 我们在 `VGG-19` 网络的层 `relu5_4` 处计算感知损失。 权重 `λ` 经验性地设为 100。 `NEDRB` 和 `NuI-Go` 处理 256 × 256 大小的图像的运行时间分别为 0.088 s 和 0.34 s，这对于实际应用来说很快。

### 4.3 评估

在本节中，我们在视网膜图像增强和视网膜血管分割上进行实验。 比较方法包括最近的视网膜图像增强方法（SGF [4]）、传统图像增强方法（CLAHE [5]）和最先进的低光图像增强方法（LIME [17]）。 结果是通过使用公开可用的源代码并采用推荐的参数设置产生的。

#### 4.3.1 图像增强

我们在合成视网膜图像 **（Test A）** 和真实视网膜图像（即 Kaggle 糖尿病视网膜病变检测挑战赛 (KDRDC) 的测试集，包括在各种成像条件下拍摄的 53,576 张图像，记为 **Test B.**）上比较不同方法的图像增强性能。 合成和真实视网膜图像的视觉比较展示在 图 5 中。

如 图 5 所示，CLAHE [5] 和 SGF [4] 方法对非均匀照明区域几乎没有效果。 LIME [17] 提高了视网膜图像的亮度； 然而，由于泛化能力有限，结果中仍存在一些照明不良区域。 这样的结果可能导致临床误诊。 相比之下，我们的 NuI-Go 可以有效校正非均匀照明并保留视网膜图像的细节和自然外观。 更多关于合成和真实视网膜图像的视觉结果分别提供在 图 6 和 图 7 中。

![](img/p247-1.jpg)

**图 5：**视觉比较。 (a) 来自 **Test A** 的合成图像结果。 (b) 来自 **Test B** 的真实图像结果。 从左到右分别为输入、CLAHE [5] 的结果、LIME [17]、SGF [4] 和我们的 NuI-Go。

我们进一步使用全参考图像质量评估指标 PSNR 和 SSIM [48] 对 **Test A** 进行定量评估，因为相应的真实图像是可用的。 较高的 PSNR 值表示像素值方面的相似性。 较高的 SSIM 值表示结果在结构特性方面更接近真实值。 **Test** A 上的平均定量分数报告在 表 1 中。

如 表 1 所示，我们的 NuI-Go 在所有指标上均达到最佳性能。 此外，我们的方法在合成数据集上的平均定量分数方面比比较方法（CLAHE [5]、LIME [17]、SGF [4]）具有压倒性优势。 例如，我们的方法的平均 PSNR 值为 32.2668，而第二好的值（LIME [17] 的结果）仅为 16.3671。 对于平均 SSIM 值，其趋势与 PSNR 类似。 这样的结果表明所提出的非均匀照明去除方法的有效性。

对于 `Test B`，我们采用常用的无参考图像质量评估算法 `NIQE` [49] 来评估感知质量。`NIQE` 分数越小，表示感知质量越好。此外，我们还进行了一项用户研究，以提供关于主观质量的真实反馈。我们首先从 `Test B` 中随机选择 50 张图像，然后邀请 10 名具有图像增强专业知识的参与者对不同方法的处理结果进行 1 到 5 的排序，其中 1 为最差质量，5 为最佳质量。该用户研究重复进行五次。`NIQE` [49] 和用户研究的平均值如 Table 2 所示。

![](img/p248-1.jpg)

**Figure 6:** 合成视网膜图像的视觉对比。从左到右依次为 `Test A` 的输入、`CLAHE` [5]、`LIME` [17]、`SGF` [4] 和我们的 `NuI-Go` 的结果。红色框表示我们的结果。

![](img/p249-1.jpg)

**Figure 7:** 真实视网膜图像的视觉对比。从左到右依次为 `Test B` 的输入、`CLAHE` [5]、`LIME` [17]、`SGF` [4] 和我们的 `NuI-Go` 的结果。红色框表示我们的结果。

**Table 1:** 在 `Test A` 上以 `PSNR`（dB）和 `SSIM` 进行的定量评估。

![](img/p249-2.jpg)

*Note:* 对于每种情况，最佳结果以粗体显示。

**Table 2.** 在 `Test B` 上无参考 `NIQE` 分数和用户研究分数的平均值。

![](img/p250-1.jpg)

*Note:* 对于每种情况，最佳结果以粗体显示。

在 Table 2 中，我们的方法在无参考 `NIQE` [49] 和主观用户研究方面均取得了最佳性能。这些结果表明我们的方法可以推广到真实视网膜图像，并有效改善退化视网膜图像的视觉质量。此外，它还表明了我们非均匀光照合成方法的合理性。尽管我们的模型是在合成训练数据上训练的，但它对真实视网膜图像也很有用。

### 4.3.2 Retinal vessel segmentation

为了评估我们的方法在实际应用中的性能，我们使用在 `DRIVE` 数据集 [51] 上训练的最新 `CE-Net` [50]（训练用 20 张图像，测试用 20 张图像）作为基础视网膜血管分割模型。我们发现现有的血管分割数据集不包含非均匀或光照不良的视网膜图像。然而，非均匀光照视网膜图像在现实世界中无处不在。因此，我们采用前面提到的方法对 `DRIVE` 数据集 [51] 和 `STARE` 数据集 [52] 的测试集进行退化处理。测试数据未出现在训练集中。这两个数据集中的第一个人工标注被用作性能评估的真实标签。我们通过不同方法增强这些测试图像并将其输入 `CE-NET` [50]。最后，我们根据 [50] 中提及的公式测量平均准确率（`Acc`）和接收器操作特征曲线下面积（`AUC`）。首先，我们在 Fig. 8 中展示了我们的方法处理前后的若干样本结果及其对应的分割结果。其次，我们在 Table 3 中报告了 `Acc` 和 `AUC` 分数。

如 Fig. 8 所示，我们的方法可以有效揭示暗区域下的血管。因此，经过我们的方法处理的视网膜图像的血管可以被使用良好光照视网膜图像训练的 `CE-Net` [50] 轻松分割。因此，尽管视网膜图像分割算法在设计和训练过程中未考虑非均匀光照问题，我们的方法仍可作为有效的前处理步骤以进一步提高其性能。

**Table 3.** 在 `DRIVE` 数据集/`STARE` 数据集上以 `Acc` 和 `AUC` 进行的定量评估。

![](img/p251-1.jpg)

*Note:* 对于每种情况，最佳结果以粗体显示。

![](img/p251-2.jpg)

**Figure 8:** 视觉视网膜血管分割结果。(a) 来自退化的 `DRIVE` 数据集 [51] 和 `STARE` 数据集 [52] 的输入图像及其对应的分割结果。(b) 我们的增强结果及其对应的分割结果。分割结果由 `CE-Net` [50] 生成。

如 Table 3 所示，经过我们 `NuI-Go` 增强的结果在 `DRIVE` [51] 和 `STARE` [52] 数据集上取得了更好的分割性能。与退化图像（输入）相比，`Acc` 从 0.9508/0.9369 提高到 0.9543/0.9417，`AUC` 从 0.9329/0.7976 提高到 0.9756/0.9213。此外，有趣的是，一些增强算法会降低视网膜血管分割的性能，这在实际应用中是不期望的。为了证明我们的方法在真实视网膜图像上的鲁棒性，我们在 Fig. 9 中提供了真实视网膜图像的若干样本分割结果。很明显，经过我们的方法增强后，一些隐藏在暗处的视网膜血管得以恢复，从而可以被 `CE-Net` [50] 精确分割。Fig. 9 中的结果进一步证明了我们方法的有效性和鲁棒性。

#### 5. Conclusion

在本章中，我们主要介绍了视网膜图像的增强，并提出了一种基于深度学习的视网膜图像非均匀光照去除方法。在所提出的方法中，非均匀光照通过递归残差学习逐步去除，而视网膜图像的细节和颜色则通过局部和非局部特征的结合得以恢复。作为关键组件，我们将非局部单元引入编码器-解码器网络，有效地建模了上下文。此外，我们还提出了一种视网膜图像非均匀光照合成方法，这对深度网络的监督学习很有用。在合成和真实视网膜图像上的实验表明，所提出的方法优于现有的图像增强方法。此外，实验结果表明我们的方法可以有效提高视网膜血管分割。借助所提出的非均匀光照去除方法，眼科医生的诊断和视网膜疾病计算机辅助分析的性能可以得到改善。此外，所提出的视网膜图像合成方法可以推动基于深度学习的计算机辅助诊断的发展。

![](img/p253-1.jpg)

**Figure 9:** 真实视网膜图像的视觉视网膜血管分割结果。(a) 来自 `Test B` 的输入图像及其对应的分割结果。(b) 我们的增强结果及其对应的分割结果。分割结果由 `CE-Net` [50] 生成。红色框表示我们的结果。

### References

1. M. D. Abramoff, M. K. Garvin, and M. Sonka, “Retinal imaging and image analysis,” *IEEE Rev. Biomed. Eng*., vol. 3, pp. 169–208, 2010.

2. A. Hani and H. A. Nugroho, “Retinal vasculature enhancement using independent component analysis,” *J. Biomed. Sci. Eng*., vol. 2, no. 7, pp. 543–549, 2009.

3. M. Zhou, K. Jin, S. Wang, J. Ye, and D. Qiao, “Color retinal image enhancement based on luminosity and contrast adjustment,” *IEEE Trans. Biomed. Eng*., vol. 65, no. 3, pp. 521–527, 2018.

## 参考文献

4.J. Cheng, Z. Li, Z. Gu, H. Fu, D. Wong, and J. Liu, “Structure-preserving guided retinal image filtering and its application for optic disc analysis,” *IEEE Trans. Med. Imag*., vol. 37, no. 11, pp. 2536–2546, 2018.

5.K. Zuiderveld, *Contrast Limited Adaptive Histogram Equalization*, Academic Press, San Diego, 1995.

6.D. Coltuc, P. Bolon, and J. Chassery, “Exact histogram specification,” *IEEE Trans. Image Process*., vol. 15, no. 5, pp. 1143–1152, 2006.

7.H. Ibrahim and N. Kong, “Brightness preserving dynamic histogram equalization for image contrast enhancement,” *IEEE Trans. Consum. Electron*., vol. 53, no. 4, pp. 1752–1758, 2007.

8.J. Stark, “Adaptive image contrast enhancement using generalizations of histogram equalization,” *IEEE Trans. Image Process*., vol. 9, no. 5, pp. 889–896, 2000.

9.T. Celik and T. Tjahjadi, “Contextual and variational contrast enhancememt,” *IEEE Trans. Image Process*., vol. 20, no. 12, pp. 3431–3441, 2001.

10.C. Lee, C. Lee, and C. Kim, “Contrast enhancement based on layered difference representation of 2d histograms,” *IEEE Trans. Image Process*., vol. 22, no. 12, pp. 5372–5384, 2013.

11.C. Li, J. Guo, R. Cong, Y. Pang, and B. Wang, “Underwater image enhancement by dehazing with minimum information loss and histogram distribution prior,” *IEEE Trans. Image Process*., vol. 25, no. 12, pp. 5664–5677, 2016.GF

12.E. Lee, “The retinex theory of color vision,” *Scientific American*, vol. 237, no. 6, pp.108–128, 1977.

13.Y. Li and M. Brown, “Single image layer separation using relative smoothness,” in *Proc. IEEE Int. Conf. Comput. Vis. Pattern Rec. (CVPR)*, 2014, pp. 2752–2759.

14.C. Rother, M. Kiefei, L. Zhang, B. Scholkopf, and P. Gehler, “Recovering intrinsic images with a global sparsity prior on reflectance,” in *Advances in Neural Inf. Process. Sys*., 2011, pp. 765–773,.

15.S. Wang, J. Zheng, H. Hu, and B. Li, “Naturalness preserved enhancement algorithm for non-uniform illumination images,” *IEEE Trans. Image Process*., vol. 22, no. 9, pp. 3538–3548, 2013.

16.X. Fu, D. Zeng, Y. Huang, X. Zhang, and X. Ding, “A weighted variational model for simultaneous reflectance and illumination estimation,” in *Proc. IEEE Int. Conf. Comput. Vis. Pattern Rec. (CVPR)*, 2016, pp. 2782–2790.

17.X. Guo, Y. Li, and H. Ling, “LIME: Low-light image enhancement via illumination map estimation,” *IEEE Trans. Image Process*., vol. 26, no. 2, pp. 982–993, 2017.

18.M. Li, J. Liu, W. Yang, X. Sun, and Z. Guo, “Structure-revealing low-light image enhancement via robust retinex model,” *IEEE Trans. Image Process*., vol. 27, no. 6, pp. 2828–2841, 2018.

19.C. Li, C. Guo, J. Guo, P. Han, H. Fu, and R. Cong, “PDR-Net: Perception-inspired single image dehazing network with refinement,” *IEEE Trans. Image Multimedia*, vol. 22, no. 3, pp. 704–716, 2019.

20.H. Fu, J. Cheng, Y. Xu, D. Wong, J. Liu, and X. Cao, “Joint optica disc and cup segmentation based on multi-lable deep network and polar transformation,” *IEEE Trans. Med. Imag*., vol. 37, no. 7, pp. 1597–1605, 2018.

21.H. Fu, J. Cheng, Y. Xu, C. Zhang, D. Wong, J. Liu, and X. Cao, “Disc-aware ensemble network for glaucoma screen from fundus image,” *IEEE Trans. Med. Imag*., vol. 37, no. 11, pp. 2493–2501, 2018.
