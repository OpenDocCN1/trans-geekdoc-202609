
| U-Net | VGG11 | Jaccard Loss | 所有通道 + PH | 18 | 0.766 | 0.717 |
| U-Net | VGG11 | Jaccard Loss | RGB + Mapper | 7 | 0.794 | 0.571 |
| U-Net | VGG11 | Jaccard Loss | RGB, Slope, DEM + Mapper | 9 | 0.762 | 0.667 |
| U-Net | VGG11 | Jaccard Loss | 所有通道 + Mapper | 18 | 0.784 | 0.719 |
| U-Net | VGG11 | Jaccard Loss | RGB + PH + Mapper | 11 | 0.796 | 0.581 |
| U-Net | VGG11 | Jaccard Loss | RGB, Slope, DEM + PH | 13 | 0.791 | 0.643 |
| U-Net | VGG11 | Jaccard Loss | 所有通道 + PH + Mapper | 22 | 0.789 | 0.711 |
| U-Net | VGG11 | Jaccard Loss | 所有通道 + PH + Mapper | 23 | 0.771 | 0.713 |

## 21.6 讨论

从图 21.12 展示的分析中，可以在测试结果中观察到两个明显的趋势：

*   **水平趋势**：在所有案例中，测试集的 F1 分从左到右持续增加。这种向上趋势表明，加入 DEM、坡度、NIR 和 SNIR 等额外通道有效提升了地理对象的检测准确率。
*   **垂直趋势**：当从上到下观察结果时，F1 分保持不变。这种稳定性表明，虽然增加 DEM、坡度、NIR 和 SNIR 等通道可以提高准确率，但引入拉普拉斯滤波器和带有拓扑信息的额外层并未带来相应的检测准确率提升。

通过对测试集中选定的图像（经过 300 次训练后）进行深度分析，进一步获得了关于拓扑层有效性的见解，如图 21.13a、d、g、j 所示。在这些图像中，建模仅使用 RGB 数据进行，没有使用拉普拉斯滤波器和拓扑层等额外层，且没有包含 DEM、坡度、NIR 或 SNIR 等拓扑机器学习方法特征。通过对这些图像的仔细检查，出现了独特的模式，阐明了将拓扑层引入模型产生的细微影响。具有和不具有这些拓扑增强图像之间的对比，形象地展示了特定层如何与底层 RGB 数据相互作用，为拓扑信息在地理空间目标检测和表征中的潜力提供了新的光。

有了拓扑层，定位结果能够突出 RGB 图像中存在的精确循环，即使这些循环在掩码中是泛化的（图 21.13g）。相比之下，在缺少拓扑层的情况下，模型未能突出循环，而是仅仅尝试确认掩码结果（图 21.13a）。这一观察强调了包含拓扑层有助于对检测到的物体进行更精确的表示。

![](img/7c79e82750415aed3dd6b437e48a8d77_393_0.png)
![](img/7c79e82750415aed3dd6b437e48a8d77_393_1.png)
![](img/7c79e82750415aed3dd6b437e48a8d77_393_2.png)
![](img/7c79e82750415aed3dd6b437e48a8d77_393_3.png)
![](img/7c79e82750415aed3dd6b437e48a8d77_393_4.png)
![](img/7c79e82750415aed3dd6b437e48a8d77_393_5.png)
![](img/7c79e82750415aed3dd6b437e48a8d77_393_6.png)
![](img/7c79e82750415aed3dd6b437e48a8d77_393_7.png)
![](img/7c79e82750415aed3dd6b437e48a8d77_393_8.png)

图 21.12 每个 epoch 训练和测试结果的 F1 分数图表。(a) RGB, (b) 所有通道, (c) RGB+ 边缘, (d) RGB、坡度、DEM+ 边缘, (e) 所有通道+边缘, (g) RGB+PH, (h) RGB、坡度、DEM+PH, (i) 所有通道+ PH

![](img/7c79e82750415aed3dd6b437e48a8d77_394_0.png)

**图 21.12（续）。** 每个 epoch 训练和测试结果的 F1 分数图表。(j) RGB+Mapper, (k) RGB、坡度、DEM+Mapper, (l) 所有通道+Mapper。(m) RGB+PH+Mapper, (n) RGB、坡度、DEM+Mapper, (o) 所有通道 +PH+Mapper, (p) 所有通道 +PH+Mapper+Edge。

形状，特别是当物体具有内部空隙或洞时。分析说明了不同层和通道之间复杂的关系，强调了地理空间目标检测的复杂性。虽然某些额外的通道证明是有益的，但拓扑层尽管具有精炼物体形状的能力，并不一定意味着整体检测准确性的提高。

![](img/7c79e82750415aed3dd6b437e48a8d77_395_0.png)
(a)
![](img/7c79e82750415aed3dd6b437e48a8d77_395_1.png)
(b)
![](img/7c79e82750415aed3dd6b437e48a8d77_395_2.png)
(c)
![](img/7c79e82750415aed3dd6b437e48a8d77_395_3.png)
(d)

图 21.13 训练 300 个 epoch 后模型的 RGB 图像和预测结果。(a) RGB, (b) RGB、坡度、DEM, (c) 所有通道, (d) RGB、+边缘。

| RGB | Mask | 预测 |
|---|---|---|
| ![image](url) | ![image](url) | ![image](url) |
| (e) | | |
| ![image](url) | ![image](url) | ![image](url) |
| (f) | | |
| ![image](url) | ![image](url) | ![image](url) |
| (g) | | |
| ![image](url) | ![image](url) | ![image](url) |
| (h) | | |

图 21.13（续）训练 300 个 epoch 后模型的 RGB 图像和预测结果。(e) RGB、坡度、DEM+边缘, (f) 所有通道+边缘, (g) RGB+PH, (h) RGB、坡度、DEM+ PH。

![](img/7c79e82750415aed3dd6b437e48a8d77_397_0.png)
![](img/7c79e82750415aed3dd6b437e48a8d77_397_1.png)
![](img/7c79e82750415aed3dd6b437e48a8d77_397_2.png)
![](img/7c79e82750415aed3dd6b437e48a8d77_397_3.png)

图 21.13（续）训练 300 个 epoch 后模型的 RGB 图像和预测结果。(i) 所有通道+ PH, (j) RGB+Mapper, (k) RGB、坡度、DEM+ Mapper, (l) 所有通道+ Mapper。

![](img/7c79e82750415aed3dd6b437e48a8d77_398_0.png)
![](img/7c79e82750415aed3dd6b437e48a8d77_398_1.png)
![](img/7c79e82750415aed3dd6b437e48a8d77_398_2.png)
![](img/7c79e82750415aed3dd6b437e48a8d77_398_3.png)

图 21.13（续）训练 300 个 epoch 后模型的 RGB 图像和预测结果。(m) RGB+ PH+ Mapper, (n) RGB、坡度、DEM+ Mapper, (o) 所有通道+ PH+ Mapper, (p) 所有通道+ PH+ Mapper+ Edge。

## 结论

在本文中，我们通过利用包含拓扑信息的多通道图像研究了地理空间目标检测的潜在增强。核心假设是将拓扑信息集成到机器学习模型中可以显著提高检测准确性，引发了对输出敏感性和拓扑信息表示的研究。我们开发了一种基于拓扑的方法，并设计了将拓扑信息转换为多通道图像的算法。通过涉及 NIR、SWIR、DEM 和拓扑层的实验，我们探索了不同输入对地理空间性能的影响。

分析揭示了关于 F1 分数的两个趋势，反映了各种通道和检测准确性的影响。虽然集成 DEM、坡度和 NIR 等额外通道是有益的，但拓扑层尽管能够表示形状（特别是当物体包含空洞时），并没有带来改进。尽管拓扑层没有提高整体检测准确性，但它们有助于对检测到的物体进行更精确的表示，阐明了该领域的复杂性。本文对地理空间分析的持续讨论为拓扑信息在检测中的作用提供了新视角。虽然拓扑层没有直接转化为准确性的提高，但它们为研究开启了新途径，并强调了通道之间相互作用的重要性。未来的工作可能会进一步探索以优化检测技术。

## 参考文献

- Adams, H., Emerson, T., Kirby, M., Neville, R., Peterson, C., Cephtanova, S., Hanson, E., Motia, F., & Ziegelmeier, L. (2017). Persistence images: A vector representation of persistent homology. Journal of Machine Learning Research, 18, 1–35.
- Bai, M., & Urtasun, R. (2021). Deep watershed for instance segmentation. Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 5221–5229.
- Boya, D., Zhou, C., Xiao, F., & Lee, Y. J. (2019). Yolact: Real-time instance segmentation. Proceedings of the IEEE/CVF International Conference on Computer Vision, 9157–9166.
- Dubnik, P. (2015). Statistical topological object detection using persistence landscapes. Journal of Machine Learning Research, 16(1), 77–102.
- Cao, Y., Xu, J., Lin, S., Wei, W., & Sun, H. (2019). GCN: Non-local networks meet squeeze-excitation networks and beyond. Proceedings of the IEEE/CVF International Conference on Computer Vision, Seoul, South Korea.
- Chazal, F., & Michel, B. (2021). An introduction to topological data analysis: fundamental and practical aspects for scientists. Frontiers in Artificial Intelligence, 4, 1–28.
- Chen, K., Pang, J., Wang, J., Xiong, Y., Li, X., Sun, F., Feng, W., Liu, Z., Shi, J., & Yang, Y. (2019). Hybrid task cascade for instance segmentation. Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, 4974–4983.
- Chen, H., Sun, K., Tian, Z., Huang, Y., & Yan, Y. (2020). Blendmask: Top-down meets bottom-up for instance segmentation. Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, 875–881.
- Cheng, G., & Han, J. (2016). A survey on object detection in remote sensing images. ISPRS Journal of Photogrammetry and Remote Sensing. https://doi.org/10.1016/j.isprprs.2016.03.014.
- Girshick, R. (2015). Fast r-CNN. Proceedings of the IEEE Conference on Computer Vision, 1440–1448.
- Girshick, R., Donahue, J., Darrell, T., & Malik, J. (2014). Rich features for object detection and semantic segmentation. Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 260, 578–587.
- Hafiz, A. M., & Bhat, G. M. (2020). A survey on image datasets with varied attention: state of the art. International Journal of Multimedia Information Retrieval, 93, 171–189.
- He, K., Glockner, D., Ding, P., & Girshick, R. (2017). Mask r-CNN. Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 291–299.
- Helber, P., Bischke, B., Bengel, A., & Barth, D. (2019). Eurosat: A new dataset and deep benchmark for land and land cover classification. IEEE Journal of Selected Topics in Earth Observations and Remote Sensing, 12(6), 1067.
- Henzel, F., Moor, M., & Rieck, B. (2021). A survey of topological machine learning methods. Frontiers in Artificial Intelligence.
- Hoeser, T., Kuenzer, C. (2020). Object detection and image segmentation with deep learning over data data: A survey of recent trends. Remote Sensing, 12(10), 1667.
- Hoeser, T., Bachbauer, F., & Kuenzer, C. (2020). Object detection and image segmentation with deep learning over Earth observation data: a report–Part II. Applications. Remote Sensing, 12(18), 3053.
- LandSide-Sense. (2022). Retrieved 12 April 2022, from https://www.iarai.at/landside-sense/4-challenge/
- Li, K., Wang, G., Cheng, M., Lu, & Han, J. (2020). Object detection in remote sensing images: A survey. IEEE Transactions on Geoscience and Remote Sensing, 59, 96.
- Liu, W., Angelov, D., Erhan, D., Szegedy, C., Reed, S., Fu, Y., & Chen, A. (2016). SSD: Single shot detector. European Conference on Computer Vision, 21–37.
- Matzka, J., & Fitzjerason, M. (2017). Same graphs: generating datasets with varied attention and identical statistics through simulated annealing. Proceedings of the 2017 CHI Conference on Human Factors
