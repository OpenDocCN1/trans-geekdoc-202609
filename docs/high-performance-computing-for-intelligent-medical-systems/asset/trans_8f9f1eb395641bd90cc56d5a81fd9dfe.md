

![](img/75406d5bb714dfd3e68fbbc717bd8f67_212_0.png)

图 8.15. 黑色 MB 和白色 MB 宛如棋盘。

仅针对黑色 MB 进行 MB 匹配。在找到黑色 MB 的 MV 后，计算白色 MB 的 MV。

- 在开始检查七个邻近 MB（左、左上、上、右上、右、下、右下、左下）时，同时使用时间上重合的 MB 数据作为预测器。

CSP 在 PSNR 方面与 FS 取得了可比的结果，同时通过利用八个邻近 MB 的信息，在时间和搜索点需求方面相较于其他几种现有 BMA 实现了显著改进。

## 8.10 结果与讨论

本章讨论了几种受自然现象概念启发并基于该概念的 BMA，并发现它们在 ME 领域也十分高效。本章未详细介绍的用于块匹配的自然启发型 SC 技术还有更多，例如：四步 GA-BMA (4SGA)、遗传菱形搜索 (GRPS)、模因 PSO-BMA、克隆 PSO-BMA、高效模糊搜索 (EFS)、动量导向 GRPS (MD-GRPS)、基于模式的 PSO-BMA、突变与单形集成 PSO-BMA、模拟退火 BMA 等。现有研究表明，用于 ME 的 SC 技术非常有效地解决了常规 BMA 在 ME 过程中的刚性问题。所有这些算法都利用动态初始速度、随机位置、早期检测、突变、交叉等生物学事件的概念，解决了局部最优和固定模式搜索的问题。

本文调查了各种已用作 ME BMA 的 SC 技术，并将其中许多应用于多个视频序列。其他研究报道的结果及实验获得的结果列于表 8.1 中。所需检查最佳匹配的平均搜索点数和平均 PSNR 值均显示在上述表中。总体结果和性能表明，SC 技术的应用极大地提升了 ME 过程，并将加速视频压缩过程。

| 序号 | BMAs | 计算复杂度 | PSNR | 方法论 |
|---|---|---|---|---|
| 1. | 用于 ME 的遗传算法 (GA-ME) [23–28] | 37.7 | 29.2 | – 基于达尔文的自然选择理论。<br>– 使用突变和交叉算子重新生成新种群。 |
| 2. | 四步 GA (4SGA) [32] | 26.5 | 32.32 | – 将四步搜索与 GA 合并，以在 ME 中兼得两者之长。 |
| 3. | 轻量级遗传算法 (LGSA) [34] | 18.1 | 29.64 | – 在繁殖阶段生成随机值。<br>– LGSA 跳过交叉操作。 |
| 4. | 块间/帧间模糊搜索 (IIFS) [35] | 10.2 | 26.82 | – 通过块间和帧间模糊预测确定当前 MB 的运动矢量。 |
| 5. | 高效模糊搜索 (EFS) [36] | 10.32 | 27.7 | – 此处利用候选 MB 与其邻近 MB 之间的相似性，并通过模糊推理确定当前 MB 的 MV。 |
| 6. | 遗传菱形模式搜索 (GRPS) [37–40] | 9.1 | 34.68 | – 该算法的工作方式使得 WF 在所有位置均最低。 |
| 7. | 克隆 PSO-BM (CPSO-BM) [41] | 8.2 | 34.51 | – 将基于 PSO 的 ME 与自然免疫系统的克隆特性相结合，以增加勘探优势。 |
| 8. | 动量导向 GRPS (MD-GRPS) [42] | 39.45 | 34.17 | – 该算法更新了称为改进权重函数 (Refined Weighting Function) 的 WF，用于建模 ME 过程中的搜索位置。 |
| 9. | PSO-BM (PSO-BM) [44, 48] | 21.96 | 27.1 | – 该 BMA 利用鸟群觅食特性寻找全局最小值。 |

## 表 8.1. (续)

| 序号 | BMAs | 计算复杂度 | PSNR | 方法论 |
|---|---|---|---|---|
| 10. | 模因 PSO-BM (MPSO-BM) [49] | 14.417 | 32.01 | – 使用动态惯性权重。 |
| 11. | 带有突变和单形法的 PSO (MSPSO) [50, 51] | 7.79 | 43.5 | – 合并了 PSO 的勘探特性和单形法的开发特性，以寻找最佳匹配 MB。 |
| 12. | 模拟退火 BMA (SAA) [52] | 10.38 | 35.512 | – 使用概率方法搜索并找到全局最小值。<br>– 它利用液体缓慢冷却形成纯晶体固体的概念。 |
| 13. | 差分进化 BMA (DE-BMA) [53] | 12.675 | 33.85 | – 实现了交叉、突变和选择操作。 |
| 14. | 基于人工蜂群的块匹配 (ABC-BMA) [54] | 11.57 | 33.265 | – 利用最近邻插值 (NNI) 计算适应度函数。 |
| 15. | 基于 PSO 的并行 ME 算法 (PSO-PME) [55] | 15.825 | 28.41 | – 在帧中为候选 MB 搜索最佳匹配 MB。<br>– 同时，对帧中的所有 MB 并行使用 PSO，并同步结果以修改 MV，从而利用 MB 之间的高相似性。 |
| 16. | 乐章搜索 BMA (HS-BMA) [56] | 12.35 | 34.01 | – 音乐调音是基于种群的乐章搜索算法与适应度近似方法相结合以找到最合适 MB 的关键。 |
| 17. | 基于猫群优化的 BMA (CSO-BMA) [58, 59] | 16.54 | 32.88 | – 它在搜索中不使用固定模式，同时还利用猫群优化 (CSO) 的全局搜索特性进行运动估计。 |
| 18. | 布谷鸟搜索 BMA (CSBMA) [60] | 6.95 | 33.4 | – 它融合了布谷鸟的繁殖能力和某些果蝇的 Lévy 飞行特性，以寻找最佳匹配。 |
| 19. | 基于 ABC-差分进化的 BM (ABC-DE) [61, 63] | 17.56 | 37.835 | – ABC 的食源生成与 DE 算法的突变和交叉操作相互交换。 |
| 20. | 乐章搜索与差分进化 (HS-DE for BM) [62, 63] | 5.312 | 36.85 | – 在乐章搜索中应用交叉算子。 |
| 21. | “确定性启动”-GA (GA Det) [64] | 13.26 | 32.51 | – GA 中使用的确定性起始种群是该 BMA 的背后理念。 |
| 22. | 增强型灰狼优化器 (EGWO-BMA) [65] | 9.21 | 30.43 | – 使用学习自动机测试目标函数是单模还是多模，并通过应用高斯分布进行开发。 |
| 23. | 棋盘搜索模式 BMA (CSP) [66] | 5.45 | 31.75 | – 当前 MB 的坐标（即 MV）通过八个邻近 MB 的 MV 进行预测。<br>– 不应用光栅扫描。<br>– 帧中的 MB 被分割为白色和黑色集合，并在每个集合中使用不同的搜索技术。 |

## 致谢

作者谨感谢 CVR 工程学院 IT 系为开展研究提供必要的设施。作者还要感谢 Nasima A Laskar 女士的持续激励，以及 NIT Silchar 在开展工作中提供的必要技术支持。

## 参考文献

- [1] Jain J 和 Jain A 1981 帧间图像编码中的位移测量及其应用 IEEE Trans. Commun. 29 1799–808
- [2] Chan M H, Yu Y B 和 Constantinides A G 1990 应用于视频编码的可变块大小块匹配运动补偿 Proc. IEEE ( Communications, Speech, and Vision ) pp 205–12
- [3] Koga T 1981 面向视频会议的运动补偿帧间编码 Proc. National Telecommunication Conf. ( New Orleans, LA ) G5.3.1–5
- [4] Li R, Zeng B 和 Liou M L 1994 一种用于块运动估计的新三步搜索算法 IEEE Trans. Circuits Syst. Video Technol. 4 438–42
- [5] Po L M 和 Ma W C 1996 一种用于快速块运动估计的新型四步搜索算法 IEEE Trans. Circuits Syst. Video Technol. 6 313–7
- [6] Zhu S 和 Ma K K A 2000 一种用于快速块匹配运动估计的新菱形搜索算法 IEEE Trans. Image Process. 9 287–90
- [7] Zhu C, Lin X 和 Chau L P 2002 用于快速块运动估计的基于六边形的搜索模式 IEEE Trans. Circuits Syst. Video Technol. 12 349–55
- [8] Cheung C H 和 Po L M 2002 一种用于快速块运动估计的新型十字菱形搜索算法 IEEE Trans. Circuits Syst. Video Technol. 12 1168–77
- [9] Jia H 和 Zhang L 2004 一种用于块运动估计的新型十字菱形搜索算法 Proc. IEEE Int. Conf. Acoustics, Speech, and Signal Processing pp iii-357–60
- [10] Cheung C-H 和 Lai-Man P A 2002 一种用于快速视频编码和视频会议应用的新型小十字菱形搜索算法 Proc. Conf. Image Process. pp 681–4
- [11] Choi W I, Jeon B 和 Jeong J 2003 针对可变运动块大小的改进菱形搜索快速运动估计 Proc. Int. Conf. Image Process. pp II-371–4
- [12] Barjatya A 2004 用于运动估计的块匹配算法 IEEE Trans. Evol. Comput 225–39
- [13] Cheung C-H 和 Po L-M 2005 用于快速块运动估计的新型十字菱形-六边形搜索算法 IEEE Trans. Multimedia 7 16–22
- [14] Hasada A, Sadek R 和 Mandour S 2010 一种带早期终止的缩减菱形搜索新算法，用于快速运动估计 Int. J. Video Image Process. Netw. Sec. ( IJVIPNS ) 10 14–22
- [15] Hsieh C H, Lu P C, Shyn J S 和 Lu E H 1990 基于块间相关性的运动估计算法 Electron. Lett. 26 276–7
- [16] Tsai J C, Hsieh C H, Weng S K 和 Lai M F 1998 使用相关搜索算法进行块匹配运动估计 Signal Process. Image Commun. 13 119–33
- [17] Alkanhal M, Turaga D 和 Chen T 1999 基于相关性的运动估计搜索算法 Picture Coding Symp. pp 99–102
- [18] Nie Y 和 Ma K K 2002 用于快速块匹配运动估计的自适应 rood 模式搜索 IEEE Trans. Image Process. 11 1442–9
- [19] Choudhury H A 和 Saikia M 2013 用于运动估计的块匹配算法比较研究 Proc. Int. Conf. Advanced Computer Science and Information Technology 73–8
- [20] Choudhury H A 和 Saikia M 2015 用于运动估计的块匹配算法：一项基于性能的研究 Lecture Series on Advances in Communication and Computing (Berlin: Springer) pp 149–60
- [21] Fister I Jr, Yang X S, Fister I, Brest J 和 Fister D 2013 面向优化的自然启发算法简述，arXiv 预印本 arXiv:1307.4186 178–87
- [22] Siddique N 和 Adeli H 2015 自然启发计算：概述与未来方向 Cogn. Comput. 7 706–14

