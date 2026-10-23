
## 7. 结论

本文研究了在自动化雷达分类中处理原始 GBSAR 数据的潜力和益处，这对于在能见度受限的环境中进行监测和目标检测的工业应用尤其有用，该方法可以节省 considerable 的资源和时间。这与标准做法不同，并且本文将其与在重建图像上应用分类算法的标准做法进行了对比。测试设置围绕基于 FMCW 的 GBSAR 系统开发，该系统使用低成本组件设计并构建。所开发的 GBSAR 用于一系列测量，这些测量对由不同材料制成的多个物体进行，最终目的是实现一个完整的 GBSAR 雷达系统，该系统具有嵌入式计算机控制，能够对这些物体进行分类。

为分类目的，对两种 GBSAR 物体识别深度学习方法进行了详细分析和比较。第一种方法是基于重建 GBSAR 图像的更常规的 SAR 分类方法，而第二种方法则基本上在原始（未处理）数据上进行分类。对两种方法的多种不同的深度学习架构进行了训练、测试和比较。其中包括基于全连接层和 LSTM 网络的两个基线，计算机视觉中流行的两个标准卷积神经网络架构——ResNet18 和 MobileNetV3，以及 ResNet18 网络的修改变体，使其适用于处理原始 GBSAR 数据。该修改包括防止在水平维度上对输入进行子采样，这是由于 GBSAR 数据的性质导致该维度通常很小。该修改是我们关于深度学习模型设计的主要贡献。通过实验验证了该贡献，结果显示在原始数据上获得最佳结果的是修改版 ResNet18。此外，计算机视觉中常见的作为数据增强程序的颜色抖动实践被扩展到原始 GBSAR 数据的分类中，并显示出一致的、尽管很小的改进。此外，还表明基于原始数据的分类优于基于重建图像的分类。这部分是预期的，因为 SAR 图像重建算法必然会引入某些近似，从而负面影响所记录数据的完整性。除了更好的分类性能外，原始数据分类本质上更快，因为它避免了图像重建的需要，因此更适合嵌入式计算机实现，从而为各种应用场景打开了可能性。另一方面，它限制了人眼视觉确认并禁用了雷达图像与光学图像相结合的方法。然而，考虑到主要关注点是嵌入式系统中的应用，这并不是严重的阻碍。

尽管本研究显示了该概念的适用性，但它使用的是相对较小的数据集，以便专注于方法之间的比较。使用更大数据集、更多类别和更一般的问题表述可能会导致更强大更有用的模型。另一个方向是寻求更高效网络的改进以及在资源有限的嵌入式计算机中的实现。考虑到这一点，为了未来研究的潜在使用，我们生成并公开发布了这些原始 GBSAR 数据和重建雷达图像的数据集，我们打算随着时间的推移对其进行更新。

**作者贡献：** 概念化，M.K.、F.T.、D.B. 和 M.B.；方法，M.K.、F.T.、D.B. 和 M.B.；软件，M.K. 和 F.T.；验证，M.K.、F.T.、D.B. 和 M.B.；形式分析，M.K. 和 F.T.；调查，M.K. 和 F.T.；资源，M.B.；数据整理，M.K. 和 F.T.；撰写——初稿准备，M.K. 和 F.T.；撰写——审阅和编辑，D.B. 和 M.B.；可视化，M.K. 和 F.T.；监督，D.B. 和 M.B.；项目管理，M.B.；资金获取，M.B. 所有作者均已阅读并同意发表的稿件版本。

**资助：** 本工作部分由克罗地亚科学基金会（HRZZ）在项目编号 IP-2019-04-1064 下资助。

**数据可用性声明：** 本研究中使用的 RealSAR 数据集（RAW 和 IMG）可公开获取：https://data.mendeley.com/datasets/m458grc688/draft?a=ff342b09-dd03-4d09-a169-560af2f87773（访问于 2022 年 11 月 1 日）。

**利益冲突：** 作者声明无利益冲突。

## 缩写

本文中使用了以下缩写：

| 缩写 | 含义 |
|---|---|
| SAR | 合成孔径雷达 |
| GBSAR | 地基合成孔径雷达 |
| CNN | 卷积神经网络 |
| FMCW | 频率调制连续波 |
| FFT | 快速傅里叶变换 |
| IFFT | 逆快速傅里叶变换 |
| RPi | 微型计算机树莓派 4B |
| VCO | 电压控制振荡器 |
| SNR | 信号与噪声比 |
| AP | 平均精度 |
| mAP | 平均平均精度 |

## 参考文献

1. Copernicus Space Component Mission Management Team. Sentinel 高层运营计划 (HLOP)。可在网上获取：https://sentinels.copernicus.eu/documents/247904/685154/Sentinel+HLOP+--+Issue+3.1.++16+Dec+2021.pdf（访问于 2022 年 7 月 23 日）。
2. Liu, B.; He, K.; Han, M.; Hu, X.; Ma, G.; Wu, M. 无人机和 GB-SAR 在中国西南 Zhonghaicun 滑坡机制研究和监测中的应用. Remote Sens. 2021, 13, 1653. [CrossRef]
3. Izumi, Y.; Zou, L.; Kikuta, K.; Sato, M. 山区地基 SAR 中异常大气相位屏补偿. In Proceedings of the IGARSS 2019—2019 IEEE 国际地质与遥感研讨会, Yokohama, Japan, 28 July–2 August 2019; pp. 2030–2033. [CrossRef]
4. Chet, K.V.; Siong, L.C.; Hsin, W.H.H.; Wei, L.L.; Guey, C.W.; Yam, C.M.; Sze, L.T.; Kit, C.Y. 用于地表形变监测的 Ku 波段地基 SAR 实验. In Proceedings of the 2015 IEEE 5th Asia-Pacific Conference on Synthetic Aperture Radar (APSAR), Singapore, 1–4 September 2015; pp. 641–644. [CrossRef]
5. Ma, Z.; Mei, G.; Prezioso, E.; Zhang, Z.; Xu, N. 基于时序位移数据的斜坡形变预测的图卷积网络深度学习方法. Neural Comput. Appl. 2021, 33, 14441–14457. [CrossRef]
6. Tarchi, D.; Antonello, G.; Casagli, N.; Farina, P.; Fortuny-Guasch, J.; Guerri, L.; Leva, D. 地基 SAR 干涉测量在斜坡破坏早期预警中的应用：Cortenova 岩石滑坡（意大利）. In Landslides: Risk Analysis and Sustainable Disaster Management; Sassa, K., Fukuoka, H., Wang, F., Wang, G., Eds.; Springer: Berlin/Heidelberg, Germany, 2005; pp. 337–342. [CrossRef]
7. Martinez-Vazquez, A.; Fortuny-Guasch, J. 用于雪崩识别的 GB-SAR 处理器. IEEE Trans. Geosci. Remote Sens. 2008, 46, 3948–3956. [CrossRef]
8. Miccinesi, L.; Consumi, T.; Beni, A.; Pieraccini, M. 用于桥梁测试/监测的 W 波段 MIMO GB-SAR. Electronics 2021, 10, 2261. [CrossRef]
9. Qiu, Z.; Jiao, M.; Jiang, T.; Zhou, L. GB-InSAR 方法的大坝结构形变监测. IEEE Access 2020, 8, 123287–123296. [CrossRef]
10. Du, S.; Feng, G.; Wang, J.; Feng, S.; Malekian, R.; Li, Z. 露天矿斜坡形变的新机器学习预测模型：现场数据评估. Energies 2019, 12, 1288. [CrossRef]
11. Kang, M.K.; Kim, K.E.; Cho, S.J.; Lee, H.; Lee, J.H. C 波段极化 GB-SAR 图像数据的 Wishart 监督分类结果. In Proceedings of the 2011 IEEE International Geoscience and Remote Sensing Symposium, Vancouver, BC, Canada, 24–29 July 2011; pp. 459–462. [CrossRef]
12. Feng, S.J; Ji, K.; Zhang, L.; Ma, X.; Kuang, G. 基于 ASC 部件模型和深度学习算法集成的 SAR 目标分类. IEEE J. Sel. Top. Appl. Earth Obs. Remote Sens. 2021, 14, 10213–10225. [CrossRef]
13. Liu, H.; Li, S. 用于 SAR 图像目标识别的稀疏表示与支持向量机决策融合. Neurocomputing 2013, 113, 97–104. [CrossRef]
14. Huang, Z.; Pan, Z.; Lei, B. 具有有限标记数据的 SAR 目标分类的深度卷积神经网络迁移学习. Remote Sens. 2017, 9, 907. [CrossRef]
15. Chen, S.; Wang, H.; Xu, F.; Jin, Y.Q. 用于 SAR 图像的目标分类的深度卷积网络. IEEE Trans. Geosci. Remote Sens. 2016, 54, 4806–4817. [CrossRef]
