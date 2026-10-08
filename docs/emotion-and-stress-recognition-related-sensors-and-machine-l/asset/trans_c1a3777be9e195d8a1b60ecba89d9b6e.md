

# 表 6. 在300W 数据集上的平均误差。

| 方法 | 通用 (Common) | 挑战性 (Challenging) | 全集 (Fullset) |
|---|---|---|---|
| RCPR [43] | 6.18 | 17.26 | 7.58 |
| SDM [5] | 5.57 | 15.40 | 7.50 |
| LBF [58] | 4.95 | 11.98 | 6.32 |
| CSSF [59] | 4.73 | 9.98 | 5.76 |
| CSSF Practical [51] | 4.79 | 10.92 | 5.99 |
| RAR [59] | 4.12 | 8.35 | 4.94 |
| 3DDFA [23] | 6.15 | 10.59 | 7.01 |
| DeFA [57] | 5.37 | 9.38 | 6.10 |
| CFM [96] | 3.39 | 8.14 | 4.56 |
| 本方法 | 3.60 | 8.69 | 3.90 |

![](img/601340ca744b738277eef45ff127492a_130_0.png)

图 8. 来自 300W 数据集的关键点检测示例。

AFLW2000-3D 数据集的目标是在大型数据集上评估算法。在这个数据集上，我们将所提出的方法与表 7 所示的若干先进方法进行了比较。结果显示，我们的方法在 AFLW2000-3D 数据集上的误差为 4.04%。与 3DSTN [60] 相比，我们的方法成功降低了 AFLW2000-3D 数据集的误差 0.45%。第三优的结果是 DeFA [57]，误差率为 4.50%。我们的方法的关键点检测结果如图 9 所示。

![](img/601340ca744b738277eef45ff127492a_131_0.png)

**图 9.** 来自 AFLW2000-3D 数据集的关键点检测示例。

**表 7.** AFLW2000 数据集上的平均误差。

| 方法 | 误差 |
|---|---|
| ESRR [11] | 7.99 |
| RCPR [43] | 7.80 |
| MDM [61] | 6.41 |
| SDM [5] | 6.12 |
| 3DDFA [23] | 5.42 |
| 3DSTN [60] | 4.49 |
| Def [37] | 4.50 |
| 本方法 | 4.04 |

## 结论

在本文，我们提出了一种用于关键点检测的热图回归方法。我们采用 FC-DenseNets 通过显式卷积来提取稠密特征图。从合适的形状开始，检测到的形状在架构的最后阶段被精炼以匹配真值（ground-truth）形状。局部初始化通过聚合多尺度上下文信息被精心设计，以提高第一阶段的局部预测性能。我们所提出的方法在包括 LFW、HELEN、300W 和 AFLW2000-3D 在挑战性数据集上取得了优于或至少相当于先进方法的性能。

**作者贡献:** 本工作由所有作者共同完成。概念化：S.C.；方法：S.C., J-G.L.；软件、验证：S.C., J-G.L.；正式分析：J-G.L.；初稿准备：S.C.；审阅与编辑：S.C., H.-H.P.；可视化：S.C.；监督：H.-H.P.；资助：感谢忠安大学青年学者计划（CAYSS）、教育部（项目编号：NRF-283995，项目名称：利用视频大数据的人脸识别和姿态、照明和表情）以及贸易工业部（项目编号：P02597，高级培训计划）对本研究的支持。

**利益冲突:** 作者声明无利益冲突。

## 缩写

手稿中使用了以下缩写：

- 2D 二维
- 300W 三维
- AFLW 2000 标注关键点
- AUC 曲线下积
- CLM 约束局部模型
- CNN 卷积神经网络
- DCNN 深度卷积网络
- DSC 扩张空洞卷积
- FCNs 全卷积网络
- GPU 图形处理器
- LAI 局部初始化
- LPFW 野外标签脸部
- MME 归一化误差
- ReLU 修正线性单元

## 参考文献

1. Wu, Y.; Ji, Q. 关键点检测：综述。Int. J. Comput. Vis. 2017, 23–28.
2. Cornelho, A.; Lu, H.; Simón, M.; Cohen, J.; Guerrero, S. RGB、热成像及多模态脸识别综述：趋势与相关应用。IEEE Trans. Pattern Mach. 2016, 38, 1548–1558.
3. Wang, S. H.; Phillips, P.; Dong, Z.; Zhang, Y. 基于平稳小波变换的智能脸识别。Neurocomputing 2018, 37, 668–676.
4. Zhang, Y.; Zhou, X.; Phillips, P.; Liu, Q.; Wang, S. 基于生物识别、模糊支持机和分层分类的情绪识别。IEEE Access 2016, 8375–8388.
5. Xiong, X.; De la Torre, F. 监督检测及其在脸对齐的应用。In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, Portland, OR, 23–28 June 2013; 532–539.
6. Koppen, P.; Feng, Z.; Kitter, J.; Awais, M.; Wu, X.; Yin, H. 高斯混合脸模式检测。Pattern Recognition 2018, 74, 617–628.
7. Sinha, G.; Shakti, R.; Shankar, M. 人机交互。In Proceedings of the 2010 3rd International Conference on Engineering Methods and Technology, Goa, India, 19–21 November 2010; 1–4.
8. Bulat, A.; Timur. 我们解决 2D & 3D 脸对齐问题还有多远？以及包含230,000个关键点的数据集。Co 2017.
9. Zhang, H.; Li, Q.; Sun, Z.; Y. 结合数据驱动和模型驱动方法的鲁棒关键点检测。Inf. Forensics Sec. 2019, 13, 2409–2422.
10. Shi, H.; Wang, Z. 带偏移的改进堆叠沙漏网络用于鲁棒关键点检测。In Proceedings of the 2019 9th International Conference on Science and Technology (ICIST), Holistic, China, 2–5 August 2019; 58–64.
11. Cao, X.; Wei, Y.; Wen, F.; Sun, J. 基于显式形状回归的脸对齐。Int. J. Comput. Vis. 2014, 107, 177–190.
12. Luo, P.; Wang, X. 通过深度学习进行分层脸解析。In Proceedings of the 2012 IEEE Conference on Computer Vision and Pattern Recognition, RI, USA, 16–21 June 2012; 2480–2487.
13. Wu, W.; Wang, S. 用于脸对齐的回归线性变。In the IEEE Conference on Computer Vision and Pattern Recognition (CVPR) Workshops, Honolulu, HI, USA, 21-26 July 2017.
14. Fischer, P.; Dosovitskiy, A.; Brox, T. 卷积神经网络描述符匹配：与SIFT的比较。arXiv 2014, arXiv:1405.5769.

