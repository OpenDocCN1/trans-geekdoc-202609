

![](img/e4200cc4308edaf8913e513b0f96dbb6_286_0.png)

## 表 7. UCF_CC_50 数据集上的计数误差。

| 方法 | MAE↓ | MSE | 参数量 (M) | 计算量 (G) |
| :--- | :--- | :--- | :--- | :--- |
| MCNN [15] | 377.6 | 509.1 | 0.133 | 15.801 |
| MSCNN [27] | 363.7 | 468.4 | 3.084 | 326.106 |
| SwitchCNN [26] | 318.1 | 439.2 | 15.108 | 185.450 |
| CP-CNN [28] | 295.8 | 320.9 | 17.137 | 287.254 |
| CSRNet [16] | 266.1 | 397.5 | 16.259 | 243.308 |
| SANet [29] | 258.4 | 334.9 | 1.146 | 55.725 |
| DUBNet [30] | 243.8 | 329.3 | 18.827 | 58.930 |
| MSDCNet (本文) | 206.9 | 271.3 | 9.560 | 181.635 |

### 4.6. UCF-QNRF 数据集上的实验结果

UCF-QNRF 数据集包含具有多种场景、视角和光照条件的密集人群图像，对于验证计数模型的鲁棒性至关重要。图 12 展示了由 MSDCNet 从 UCF-QNRF 数据集中生成的一些密度图。表 8 展示了 MSDCNet 与其他模型在 UCF-QNRF 数据集上计数误差的对比。实验结果表明，与其他模型相比，我们的模型在 UCF-QNRF 上取得了更高的计数准确率。与表现最佳的 DUBNet 相比，MSDCNet 的 MAE 降低了 4.2，MSE 降低了 9.6。此外，MSDCNet 在 UCF-QNRF 数据集上表现出优异的鲁棒性。

![](img/e4200cc4308edaf8913e513b0f96dbb6_287_0.png)

**图 12.** MSDCNet 从 UCF-QNRF 测试数据集中生成的一些密度图。

**表 8.** UCF-QNRF 数据集上的计数误差。

| 方法 | MAE↓ | MSE | 参数量 (M) | 计算量 (G) |
| :--- | :--- | :--- | :--- | :--- |
| SwitchCNN [26] | 228 | 445 | 15.108 | 1829.095 |
| RAZ-Net [31] | 116 | 195 | 24.465 | 4848.993 |
| TEDNet [17] | 113 | 188 | 8.863 | 4090.777 |
| DUBNet [30] | 105.6 | 180.5 | 18.827 | 581.231 |
| MSDCNet (本文) | 101.4 | 170.9 | 9.560 | 1791.465 |

### 4.7. 消融实验

为了验证提出的 MFENet、SPP 模块和空洞卷积层的有效性，进行了三项消融实验。在第一个实验中，移除了 MSDCNet 中的 MFENet，模型仅由前端和后端网络组成。该模型标记为 model-A，如图 13a 所示。在第二个实验中，保留了 MFENet，移除了前端中的三个 SPP 模块，并使用 VGG16 中原始的 2 × 2 最大池化层。该模型标记为 model-B，如图 13b 所示。在第三个实验中，将后端中的四个空洞卷积层替换为四个标准卷积层和一个池化层。该模型标记为 model-C，如图 13c 所示。这些模型在 UCF-QNRF 数据集上进行了训练和测试，实验结果如表 9 所示。

![](img/e4200cc4308edaf8913e513b0f96dbb6_288_0.png)

**表 9.** UCF-QNRF 数据集上的消融实验结果。

| 模型 | MAE | MSE |
| :--- | :--- | :--- |
| model-A (无 MFENet 的 MSDCNet) | 185.6 | 268.1 |
| model-B (无 SPP 模块的 MSDCNet) | 163.3 | 238.7 |
| model-C (无空洞卷积的 MSDCNet) | 117.1 | 185.5 |
| MSDCNet | 101.4 | 170.9 |

实验结果表明：

- 从两个实验模型和 MSDCNet 的计数误差可以看出，在移除 MFENet 和 SPP 后，MSDCNet 的计数准确率显著下降。在没有 MFENet 的情况下，model-A 的 MAE 增加了 84.2（约占 model-A MAE 的 45%），MSE 增加了 97.2（约占 model-A MSE 的 36%）。在没有 SPP 模块的情况下，model-B 的 MAE 增加了 61.9（约占 model-B MAE 的 38%），MSE 增加了 67.8（约占 model-B MSE 的 28%）。在没有空洞卷积层的情况下，model-C 的 MAE 增加了 15.7（约占 model-C MAE 的 13%），MSE 增加了 14.6（约占 model-C MSE 的 8%）。这些结果充分证明了我们的模型中 MFENet、SPP 模块和空洞卷积层的有效性。
- 从三个实验模型的计数误差可以看出，model-A 的计数误差高于 model-B 和 model-C，这表明与 SPP 模块和空洞卷积层相比，MFENet 对整个网络的计数准确率贡献更大。

## 5. 结论

本文提出的人群计数模型解决了人群分布不均和头部尺度变化等问题，在三个公开数据集上实现了高精度的计数和良好的鲁棒性。主干网络采用单列框架，简化了模型结构，同时保持了一定的深度以提取高层特征。在前端提出的 SPP 模块在池化过程中融合空间特征，帮助前端在不增加参数量的情况下以不同尺度提取特征。通过将一个多列子网 (MFENet) 连接到单列主干网络，我们在精度和复杂度之间取得了平衡的结果。仅通过增加 3.8% 的参数量，MFENet 就能感知图像尺度的剧烈变化并提取头部的多尺度特征。用作后端的连续空洞卷积层有效防止了过拟合，避免了头部特征的丢失，扩大了感受野，并提高了输出密度图的质量。

在 future 研究中，我们将调查背景和图像边缘的影响，并建立一个具有更高精度和更好鲁棒性的密集人群计数模型。

作者贡献：概念化，J.D.；方法论，J.D.、Z.Z. 和 T.W.；软件与验证，Z.Z. 和 T.W.；原始草稿撰写，Z.Z.；审阅与编辑，J.D.；监督，J.D. 所有作者已阅读并同意发布的手稿版本。

**资助：** 本工作得到国家自然科学基金（项目编号 NSFC-61671190）的资助。

**数据可用性声明：** 本研究中呈现的数据可应通信作者的要求获取。

**致谢：** 我们感谢李锦阳和张雨顺提出的宝贵意见和讨论。

**利益冲突：** 作者声明不存在利益冲突。

## 参考文献

- Zhang, J.; Liu, J.; Wang, G. 地铁站台人群计数的卷积神经网络. *Symmetry* **2021**, *13*, 703. [CrossRef]
- de Silva, E.M.K.; Kumarasinghe, P.; Idradjith, K.K.D.A.K.; Pushpakumara, T.V.; Vimukthi, R.D.Y.; de Zoyssa, K.; Gunawardana, K.; de Silva, S. 使用卷积神经网络进行野生亚洲象个体识别的可行性. *Mamm. Biol.* **2022**, *102*, 931–941. [CrossRef]
- Lu, W.G.; Tan, Z. 城市公共场所拥挤踩踏事故预防与处理研究：以韩国梨泰院踩踏事故为例. *China Emerg. Rescue* **2023**, *1*, 4–10.
- Gao, G.; Gao, Y.; Liu, Q.; Wang, Q.; Wang, G. 基于 CNN 的密度估计和人群计数：综述. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), Seattle, WA, USA, 14–19 June 2020.
- Zhao, R.; Dong, D.; Wang, Y.; Li, C.; Ma, Y.; Enriquez, M.F. 基于改进多列卷积神经网络的人群稳定性图像分析. *IEEE Trans. Intell. Transp. Syst.* **2021**, *23*, 5480–5489. [CrossRef]
- Chan, A.B.; Liang, Z.S.; Vasconcelos, N. 隐私保护的人群监控：无需人群模型或跟踪即可计数. In Proceedings of the 2008 IEEE Conference on Computer Vision and Pattern Recognition (CVPR), Anchorage, AK, USA, 23–28 June 2008.
- Chan, A.B.; Vasconcelos, N. 用于人群计数的贝叶斯泊松回归. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), San Francisco, CA, USA, 6 May 2010.
- Wan, H.L.; Wang, X.M.; Peng, Z.W.; Bai, Z.; Yang, X.; Sun, J. 基于新颖多尺度注意力机制的密集人群计数算法. *J. Electron. Imaging* **2022**, *44*, 1129–1136.
- Jiang, N.; Zhou, O.; Yu, F.H. 基于视觉的人群目标计数方法综述. *Laser Optoelectron. Prog.* **2021**, *58*, 43–59.
- Meng, B.; Chen, X.R.; Liu, Y.; Tai, R.; Xu, S.J. 基于多特征信息融合的人群密度估计方法. *Laser Optoelectron. Prog.* **2021**, *58*, 276–287.
- Wang, Y.; Zhang, W.; Huang, D.; Liu, Y.; Zhu, J. 具有多级监督路径的多尺度特征融合网络用于人群计数. *Expert Syst. Appl.* **2022**, *59*, 200–212. [CrossRef]
- Krizhevsky, A.; Sutskever, I.; Hinton, G.E. 使用深度卷积神经网络进行 ImageNet 分类. In Proceedings of the Neural Information Processing Systems (NIPS), Lake Tahoe, NV, USA, 3–8 December 2012.
- Szegedy, C.; Liu, W.; Jia, Y.; Sermanet, P.; Reed, S.; Anguelov, O.; Erhan, D.; Vanhoucke, V.; Rabinovich, A. 更深层的卷积. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), Columbus, OH, USA, 23–28 June 2014.
- Simonyan, K.; Zisserman, A. 用于大规模图像识别的非常深的卷积网络. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), Boston, MA, USA, 7–12 June 2015.
- Zhang, Y.; Zhou, D.; Chen, S.; Gao, S.; Ma, Y. 基于多列卷积神经网络的单图像人群计数. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), Las Vegas, NV, USA, 26 June–1 July 2016.
- Li, Y.; Zhang, C.; Chen, D. CSRNet: 用于理解高度拥挤场景的空洞卷积神经网络. In Proceedings of the 2018 IEEE/CVF Conference on Computer Vision, Salt Lake City, UT, USA, 18–23 June 2018; pp. 1091–1100.
- Jiang, X.L.; Xiao, Z.H.; Zhang, B.C.; Zhen, X.; Cao, X.; Doermann, D.; Shao, L. 基于网格编码器-解码器网络的人群计数和密度估计. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), Seattle, WA, USA, 14–19 June 2020.
- Yang, Y.; Li, G.; Wu, S.; Zu, L.; Huang, Q.; Sebe, N. 用于透视感知物体计数的反向感知网络. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), Seattle, WA, USA, 14–19 June 2020.
- Zhou, J.T.; Zhang, L.; Du, J.; Peng, X.; Fang, X.; Xiao, Z.; Zhu, H. 局部感知人群计数. *IEEE Trans. Pattern Anal. Mach. Intell.* **2022**, *44*, 3602–3613. [CrossRef] [PubMed]
- Song, Q.; Wang, K.; Jiang, Z.; Wang, Y.; Tai, Y.; Wang, C.; Li, J.; Huang, F.; Wu, Y. 重新思考人群中的计数和定位：纯基于点的框架. In Proceedings of the IEEE International Conference on Computer Vision (ICCV), Montreal, QC, Canada, 10–17 October 2021.
- Wan, S.; Liu, Z.; Chan, A.A. 用于人群计数和定位的广义损失函数. In Proceedings of the Computer Vision and Pattern Recognition, Online; 2021.
- Lin, H.; Ma, Z.; Hu, J.; R.R. 通过多面注意力增强人群计数. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), New Orleans, LA, USA, 19–24 June 2022.

