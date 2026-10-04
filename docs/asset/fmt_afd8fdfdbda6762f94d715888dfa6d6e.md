
## 3.6 TTAC 算法

我们在算法 1 中总结了 TTAC 的训练算法。为了在目标域进行有效聚类，我们分配了一个固定长度的内存空间，记为`C ∈ R^{N_c × N_s}`来存储最近的测试样本。在 sTTT 协议中，我们首先对每个测试样本进行即时预测，仅当积累了`N_B`个测试样本时才更新模型。TTAC 可以高效实现，例如使用两个设备，一个用于连续推理，另一个用于模型更新。

## 算法 1 TTAC++ 算法

**input**：一个新的测试批次`B^t = {x_i}_{i=t-N_B..(t+1)N_B}`。
**# 更新测试样本队列`C^t`。**
`C^t = C^{t-1} \ B^{t-N_c/N_B}, C^t = C ∪ B^t`
**for** 1 to `N_{iter}` **do**
  **for** `C^t`中的小批次`{x_i^t}_{i=1}^{N_c}` **do**
    # 生成弱增强和强增强样本
    `W(x_i^t)`
    # 获取预测后验和伪标签
    **通过方程 (10) 获取**`ŷ_i`。
    # 使用`W(x_i^t)`通过方程 (8) 更新全局和每个聚类的运行均值和协方差
    `μ^t, Σ^t, {μ_k^t, Σ_k^t}`
    # 根据方程 (2) 和 7 计算锚点聚类损失
    `L_ac + λ_1 L_ga`
    # 根据方程 (10) 计算自训练损失
    `L_st`
    # 对总损失进行一步梯度下降
    `L_ac + λ_1 L_ga + λ_2 L_st`

## 4. 实验

在本节中，我们首先对比了现有方法。然后我们对 TTAC 的组件进行了消融实验。最后在结尾提供了定性见解。

### 4.1. 数据集

我们在 ModelNet40 上评估 TTT，该数据集包含 943 个训练样本和 2468 个测试样本，并报告分类误差（%）。

### 4.2. 实验设置

**超参数。**我们在 ModelNet40 上使用 DGCNN。设置 BS = 64，LR = 0.001。

**TTT 协议。**我们根据两个因素对 TTT 进行分类。首先，训练期间是否必须更改训练目标，我们用 Y 和 N 表示允许训练。其次，测试数据是否是顺序的，我们用 O 表示顺序，M 表示非顺序。最后，假设强度从第一个到最后一个增加。

**对比方法。**我们对比了以下 TTT 方法：
- (TEST) 直接使用模型对目标域进行推理。
- (TTT-R)³ 在源域联合训练自监督任务和分类任务。
- (BN)³⁴ 通过流数据更新批统计。默认方法遵循 N-M 协议并可以适配 N-O 协议。
- (TENT)¹⁴ 通过最小化模型预测的熵来更新归一化参数。默认情况下，TENT 遵循 N-O 协议并可以适配 N-M 协议。
- (T3A)¹⁵ 使用流数据计算每个类别的目标表示，并使用更新的原型进行预测。T3A 默认遵循 N-O 协议。
- (SHOT)⁸ 冻结线性分类头，通过利用目标域的类别平衡假设和自标签来训练特定的特征提取模块。SHOT 默认遵循 N-M 协议，我们适配该协议。
- TTT++¹² 通过最小化均协方差之间的 F 范数，对齐离线计算的源域特征分布和目标域特征分布。TTT++ 遵循 Y-M 协议，我们适配 N-O（移除对比学习头）协议。我们提出了不带自训练的方法 TTAC，它只需要对目标域进行单次通过，不需要修改源训练目标。我们针对 Y-O、N-M 和 Y-M 协议改进了 TTAC；对于 Y-O 和 Y-M，加入了额外的对比学习分支¹²。我们将 TTAC 与 SHOT 中引入的额外多样性损失和熵最小化结合，记为 TTAC+SHOT。最后，我们提出了结合锚点聚类和自训练的模型 TTAC+ST，它在测试数据流上同时优化锚点聚类损失和自训练损失。

### 4.3. 损坏目标域上的 TTT

我们在表 1 中给出了 ModelNet40 数据集上的 TTT 结果。从结果中得出以下观察。

**sTTT (N-O) 协议。**我们首先分析在所提 sTT (N-O) 协议下的结果。我们的方法优于对比方法。

表 1. 不同 TTT 协议下的对比。Y/N 表示是否修改了源域训练目标。O/M 表示一次或多次 TTT。C10-C、C100-C 和 MN40-C 分别指 CIFAR10-C、CIFAR100-C 和 ModelNet40-C 数据集。所有数字均表示百分比错误率。

| 方法 | TTT 协议假设 | 强度 | C10-C | C100-C | MN40-C |
|---|---|---|---|---|---|
| TEST | | | 29.50 | 60.34 | 34.62 |
| BN³⁴ | N-O | 弱 | 15.49 | 43.38 | 26.53 |
| TENT¹⁴ | N-O | 弱 | 14.27 | 40.32 | 26.38 |
| T3¹⁵ | N-O | 弱 | 15.44 | 42.72 | 24.57 |
| SHOT⁸ | N-O | 弱 | 13.95 | 39.10 | 19.71 |
| TTT++¹² | N-O | 弱 | 13.66 | 40.32 | -- |
| TTAC (我们的方法) | N-O | 弱 | 10.94 | 36.64 | 22.30 |
| TTAC+SHOT (我们的方法) | N-O | 弱 | 10.99 | 36.39 | 19.21 |
| TTT++¹² | Y-O | 中等 | 13.00 | 35.23 | -- |
| TTAC (我们的方法) | Y-O | 中等 | 10.69 | 38.42 | -- |
| BN³⁴ | N-M | 中等 | 15.70 | 43.30 | 26.49 |
| TENT¹⁴ | N-M | 中等 | 12.60 | 36.30 | 21.23 |
| SHOT⁸ | N-M | 中等 | 14.70 | 38.10 | 15.99 |
| TTAC (我们的方法) | N-M | 中等 | **9.42** | 33.55 | 16.77 |
| TTAC+SHOT (我们的方法) | N-M | 中等 | **9.54** | **32.89** | **15.04** |
| TTT-R¹³ | Y-M | 强 | 14.30 | 40.40 | -- |
| TTT++¹² | Y-M | 强 | 9.80 | 34.10 | -- |
| TTAC (我们的方法) | Y-M | 强 | **8.52** | **30.57** | -- |

相比之前的最优方法（TTT++），我们的方法大幅领先，例如在 CIFAR10-C 和 CIFAR100-C 上观察到了 3% 的提升。我们进一步将 TTAC 与 SHOT 中的类别假设相结合（TTAC+SHOT）。我们的方法由于具有更强的假设，可以比单独的 TTAC 进一步提高性能，特别是在 ModelNet-40-C 数据集上。这一结果证明了 TTAC 与现有方法的兼容性。

**备选协议。**我们在 N-M、Y-O 和 Y-M 协议下比较了不同的方法。在 Y-O 协议下，TTT++¹² 通过引入对比学习分支修改了源域训练目标。³⁵ 为了与 TTT++ 进行比较，我们也包含了对比分支，并观察到了明显的改进。

**在合成到真实的适应中的 TTT。**VisDA-C 是一个大型合成到对象的分类基准数据集。在合成数据集上训练并在真实数据上测试的设置符合真实应用场景。在该数据集上，我们在 N-O、Y-O 和 Y-M 协议下使用我们的方法进行了实验，与其他方法在相应协议下进行对比，结果如表 3 所示。我们有以下观察结果：首先，在 Y-M 协议下，我们的方法（TTAC-O）优于除 TTT 外的所有方法。这表明 TTAC 能够部署在真实的 TTT 协议中。此外，可以使用整个目标数据进行训练，TTAC (Y-M) 大幅提升了 TTT。

表 3. VisDA 上的 TTT。竞争方法的数据继承自¹²

| 方法 | 平面 | 巴士 | 汽车 | 刀 | 人 | 植物 | 火车 | 卡车 | | | | |
|---|---|---|---|---|---|---|---|---|---|---|---|
| TEST | 56.52 | 88.71 | 62.77 | 30.56 | 81.88 | 99.03 | 17.53 | 95.85 | 51.66 | 77.86 | 20.44 |
| BN³⁴ | 44.38 | 56.98 | 33.24 | 55.28 | 37.45 | 66.60 | 16.55 | 59.02 | 43.55 | 60.72 | 31.07 | 82.98 |
| TENT¹⁴ | 13.43 | 77.98 | 20.17 | 48.15 | 21.72 | 82.45 | 12.37 | 35.78 | 21.06 | 76.41 | 34.11 | 98.93 |
| SHOT (N-M) | 5.73 | 13.64 | 23.33 | 42.69 | 7.93 | 86.99 | 19.17 | 19.97 | 11.63 | 11.09 | 15.06 | **43.26** |
| TFA (N-M)¹² | 28.25 | 32.03 | 33.67 | 64.77 | 20.49 | 56.63 | 22.52 | 36.30 | 24.84 | 35.20 | 25.31 | 64.24 |
| TTT++ (Y-M)¹² | 4.13 | 26.20 | 21.60 | **31.70** | 7.43 | 83.30 | 7.83 | 21.10 | 41.35 | **7.73** | **6.91** | 51.40 |
| TTAC (N-O) | 18.54 | 40.20 | 35.84 | 63.11 | 23.83 | 39.61 | 15.51 | 41.35 | 22.97 | 46.56 | 25.24 | 67.81 |
| TTAC (Y-O) | 7.19 | 29.99 | 22.52 | 56.58 | 8.14 | 18.41 | 8.25 | 22.28 | 10.18 | 23.98 | 13.55 | 67.02 |
| TTAC (Y-M) | **2.74** | 17.73 | **18.91** | 43.12 | **5.54** | **12.24** | **4.66** | **15.90** | **4.77** | 10.78 | 9.75 | 62.45 | **17.38** |

### 4.5. 消融实验

我们对 CIFAR10-C 数据集对单个组件进行了实验，包括锚点聚类、伪标签过滤、全局特征对齐以及与对比分支的兼容性¹²。对于锚点聚类，我们使用所有测试样本来更新聚类统计。对于伪标签过滤，我们通过预测伪标签来实现，然后将伪标签用于自训练。我们从表 4 中得出以下观察结果：在 N-O 和 N-M 协议下，引入锚点聚类或伪标签过滤均优于基线，例如在 N-O 下，锚点聚类从 29.15% 变为 14.32%，伪标签过滤从 29.15% 变为 15.00%。当锚点聚类与伪标签过滤相结合时，我们观察到性能显著提升。这是由于对目标域类别聚类的估计更准确，这种特征空间中的直接匹配可能比最小化交叉熵更好。最后，我们结合了所有组件，完整模型产生了最佳性能。当包含对比学习时，TTAC 取得了更好的结果。

### 4.6. sTT 下的额外分析

我们在图 2(a) 中展示了 sTT 协议下的累积误差。对于两个数据集，TTAC 从 TTT 早期就开始优于竞争方法。这种优势在整个 TTT 过程中持续。

**TTAC 特征的 TSNE 可视化。**我们通过 T-SNE³⁶ 可视化适应特征为 TTT 提供了定性结果。在图 2(b) 和 2(c) 中，我们比较了 TTT¹² 和 TTAC（我们的方法）学习的特征。我们观察到 TTAC 的类别分离更好，这意味着分类准确性的提高。

**无源测试训练。**TTT 旨在通过同步和顺序推理将模型适应到目标域。已经证明源域的一些轻量级信息（如统计量）将极大提高 TTT 的功效。然而，在更严格的情况下，

表 4. CIFAR10-C 数据集单个组件的消融实验。

| TTT 协议 | N-O | Y-O | N-M | Y-M |
|---|---|---|---|---|
| 锚点聚类 | — | ✓ | — | ✓ |
| 伪标签过滤 | — | — | ✓ | ✓ |
| 全局特征对齐 | — | — | KLD | KLD |
| 对比分支¹² | — | — | — | ✓ |
| 平均准确率 | 29.15 | 14.32 | 15.00 | 11.33 |
| 11.72 | 10.94 | 10.69 | 11.11 |
| 10.01 | 11.87 | 10.8 | 9.42 | 8.52 |

![](img/288_0.png)
![](img/288_1.png)

图 2. (a) 单次通过协议下的累积误差对比。(b) TTT 特征的 T-SNE 可视化。(c) TTAC 特征的 T-SNE 可视化。

表 5. CIFAR100-C 的无源 sTT。

| TEST | BN | TENT | T3A | SHOT | TTAC | TTAC+SHOT |
|---|---|---|---|---|---|---|
| 29.15 | 15.49 | 14.27 | 15.44 | 13.95 | 13.74 | 13.35 |

## 5. 结论

TTT 解决了即时领域适应的现实挑战。在这项工作中，我们首先受到 TTT 评估协议混乱的启发，并提出了两个关键标准，即识别源训练目标和顺序推理，以对现有方法分为四种 TTT 协议。在最真实的协议下（即 sTT），我们开发了 TTAC 方法将目标域特征与源域特征对齐。与批归一化和分类器更新不同，锚点聚类允许所有网络参数可训练，展示了更强的 TTT 能力。我们进一步提出了伪标签过滤和迭代更新方法分别改进锚点聚类并节省内存占用。在五个数据集上的实验验证了 TTAC 在 sTT 以及其他 TTT 协议下的有效性。

## 参考文献

1. A. Krizhevsky, I. Sutkeever, and G. E. Hinton. Imagenet with deep convolutional neural networks. In Advances in Neural Information Processing Systems (2012).
2. Z.-H. Zhou, A brief introduction to weakly supervised learning, National Science Review 5(1), 44–53 (08, 2018). ISSN 2009-5138.
3. J. Quiñero-Candela, M. Sugiyama, A. Schwaigh, and N. D. Lawrence, Dataset Shift in Machine Learning. Mit Press (2008).
4. S. Ben-David, J. Blitzer, K. Kramer, A. Kulesza, F. Pereira, and J. W. Vaughan, A theory of learning from different domains, Machine Learning 79(1-2), 151–175 (2010).
5. M. Wang and W. Deng, 深度视觉领域适应：综述, Neurocomputing 312, 135–153 (2018).
6. Y. Ganin and V. Lepitsky. 通过反向传播进行无监督领域适应. In International Conference on Machine Learning (2015).
7. K. Zhou, Z. Liu, Y. Qiao, T. Xiang, and C. C. Loy, 领域泛化：综述., IEEE transactions on Pattern Analysis and Machine Intelligence 45(4), 4396–4415 (2023年4).
8. J. Liang, D. Hu, and J. Feng. 我们需要访问源数据吗？无监督领域适应的源假设迁移. In International Conference on Machine Learning (2020).
9. J. N. Kundu, N. Venkat, R. V. Babu, 等. 通用无源领域适应. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (2020).
10. S. Yang, Y. Wang, J. de Weijer, L. Herranz, and S. Jui. 通用无源领域适应. In Proceedings of the IEEE/CVF International Conference on Computer Vision (2021).
11. H. Xia, H. Zhao, and Z. Di. 用于无源领域适应的自适应对抗网络. In Proceedings of the IEEE/CVF International Conference on Computer Vision (2021).
12. L. Yu, P. Kothari, B. van Delft, B. Bellot-Gurlet, T. Mordan, and A. Alati. TTT+: 监督测试时训练何时失败或成功？ In Advances in Neural Information Processing Systems (2021).
13. Y. Sun, X. Wang, Z. Liu, J. Miller, A. Afros, and M. Hardt. 针对分布偏移下泛化的自监督测试时训练. In International Conference on Machine Learning (2020).
14. D. Wang, E. Shelham, S. J. Olshausen, and T. Darrell. Tent: 通过熵最小化的全时自适应. In International Conference on Learning Representations (2021).
15. Y. Iwasawa and Y. Matsuo. 用于模型无关领域泛化的测试时分类器模块. In Advances in Neural Information Processing Systems (2021).
16. H. Tang, K. Chen, and K. Jia. 通过正则化深度聚类进行无监督领域适应. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (2020).
17. D.-H. Lee 等. 伪标签：一种用于深度神经网络的简单高效半监督学习方法. In Workshop on Challenges in Representation Learning, ICML (2013).
18. K. Sohn, D. Berthelot, N. Carlini, Z. Zhang, H. Zhang, C. A. Rafel, E. D. Cubuk, A. Kurakin, and C.-L. Li, Fixmatch: 通过一致性和置信度简化半监督学习, Advances in Neural Information Processing Systems (2020).
19. E. Tzeng, J. Hoffman, N. Zhang, K. Saenko, and T. Darrell, 深度领域混：最大化领域不变性, arXiv preprint arXiv:1412.3474 (2014).
20. A. Gretton, K. M. Borgwardt, M. J. Rasch, B. Schölkopf, and A. J. Smola. 内核双样本检验., Journal of Machine Learning Research, 13, 723–773 (2012).
21. B. Sun and K. Saenko. Deep coral: 用于深度领域适应的相关对齐. In European Conference on Computer Vision (2016).
22. W. Zellinger, T. Gruber, E. Lughofer, T. Natsch, and S. Saminger-Platz. 用于领域不变表示学习的中心差异 (cmd). In International Conference on Learning Representations (2016).
23. J. Hoffman, E. Tzeng, T. Park, J.-Y. Zhu, P. Isola, K. Saenko, A. Efros, and T. Darrell. 循环一致性领域适应. In International Conference on Machine Learning (2018).
24. J. Jiang and C. Zhai. 用于 NLP 领域适应的实例权重. In ACL (2007).
25. H. Yan, Y. Ding, P. Li, Q. Wang, Y. Xu, and W. Wu. 注意类别：用于无监督领域适应的加权平均差异. In Proceedings of the IEEE Conference on Computer Vision and Recognition (2017).
26. Q. Wang, O. Fink, L. Van, and D. Dai. 持续测试时领域适应. In Proceedings of the IEEE/CVF International Conference on Computer Vision (2022).
27. J. R. Hershey and P. A. Olsen. 高斯混合模型之间的 kullback-leibler 散度. In International Conference on Acoustics, Speech and Signal Processing (2007).
28. E. Arazo, D. Ortega, P. Albert, N. E’Connor, and K. McGuinness. 半监督学习中的伪标记和确认偏差. In Joint Conference on Neural Networks (2020).
29. B. Han, Q. Yao, X. Yu, G. Ni, H. Wu, I. Tsang, and M. Sugiyama. 协同教学：使用极稀标签训练深度神经网络. Advances in Neural Information Processing Systems (2018).
30. D. Li, Y. Wong, Q. Zhao, and M. S. Kankalli. 从噪声标签学习. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (2019).
31. D. Berthelot, N. Carlini, I. Goodfellow, N. Papernot, A. Oliver, and C. A. Raffel, Mixmatch: 半监督学习的整体性方法, Advances in Neural Information Processing Systems (2019).
32. E. D. Cubuk, B. Zoph, J. Shlens, and Q. V. Le, Randaugment: 减少搜索空间的实用自动数据增强, arXiv preprint arXiv:1909.3719 (2019).
33. Y. Wang, Y. Sun, Z. Liu, S. E. Sarma, M. M. Bronstein, and J. Solomon. 用于点云学习的动态图 cnn, ACM Transactions On Graphics (tag) (2019).
34. S. Ioffe and C. Szegedy. 批量归一化：通过减少内部偏移加速深度网络训练. In International Conference on Machine Learning (2015).
35. T. Chen, S. Kornblith, M. Norouzi, and G. Hinton. 用于视觉表示对比学习的简单框架. In International Conference on Machine Learning (2020).
36. L. van der Maaten and G. Hinton, 使用 t-SNE 可视化数据, Journal of Machine Learning Research 9, 2579–2605 (2008).

## 第 9 章

## 高效 3D 深度学习的算法-系统-硬件协同设计

Zhijian Liu*†, Haotian Tang*‡, Yujun Lin*§, and Song Han*¶
马萨诸塞理工学院 (MIT), Cambridge, MA, USA
†zhijian@mit.edu
‡kentang@mit.edu
§yujunlin@mit.edu
¶songhan@mit.edu

3D 点云深度学习因其广泛的应用如增强/混合现实、自动驾驶汽车/无人机和机器人而受到了广泛关注。尽管准确率很高，但 3D 点云深度学习模型的计算成本和稀疏性限制了它们在实时延迟敏感应用中的使用。在本章中，我们开发了用于 3D 深度学习的高效算法、系统和硬件，以克服 3D 点云数据的计算挑战（尤其是稀疏性），使其在更广泛的现实场景中更具适用性。从算法角度来看，我们引入了新颖的 3D 构建块（PVCNN 和 SPV-NAS）a，它们为点云数据定制，以减少稀疏和不规则的开销。在系统层面，我们开发了一个高性能库（TorchSparse）b，它可以在通常为密集和规则工作负载优化的通用硬件上处理稀疏和不规则的工作负载。此外，我们开发了一个专门的硬件加速器（PointAcc）c，它可以支持各种类型的点云深度学习原语，并缓解稀疏点云计算的内存瓶颈。

*表示贡献相等。

### 1. 引言

3D 点云提供了比 2D 图像更准确的 3D 环境描述，因为捕捉了物体在 3D 空间中的精确位置和形状。近年来，3D 传感器的可用性显著增加，大多数 L3+ 自动驾驶汽车配备了 LiDAR 扫描仪，最新的智能手机配备了 LiDAR 或飞行时间 (ToF) 传感器。这使得 3D 数据更容易获取，导致了其在现实应用中的日益普及，例如增强/混合现实、自动驾驶汽车/无人机和机器人。

与其他许多领域一样，神经网络已成为处理和分析 3D 点云数据的标准¹,² 深度神经网络的快速发展在该领域取得了突破性进展。从 nuScenes 排行榜上仅 30% 的平均精度 (mAP)³ 提高到了 75% 的 mAP⁴。虽然这是一项令人瞩目的成就，但它具有巨大的计算成本。例如，在 2019 年，最先进的 3D 点云分割模型（使用最先进的 3D 推理库时）⁵ 在桌面级 GPU 上每秒仅运行两帧 (FPS)。这很大程度上阻碍了这些模型在实际应用中的使用，特别是在低功耗边缘设备上，如手机和无人机。

稀疏性和不规则性是导致 3D 深度学习模型效率低下的主要因素。3D 点云通常表现出极高的空间稀疏性，超过 99.9% 的数据是空或无关的。这使得传统的 2D 稀疏算法/系统/硬件不再适用。此外，3D 点云具有不规则的邻域结构，点的邻居在内存中并不是连续存储的，导致了昂贵的结构化开销和随机内存访问。3D 点云的这些独特特性为开发高效且准确的 3D 点云深度学习模型带来了巨大挑战。

如图 1 所示，本章为 3D 深度学习设计了高效的算法、系统和硬件，克服了与 3D 点云数据相关的计算挑战。从算法角度来看，我们探索了新型 3D 构建块（PVCNN 和 SPVNAS），专门设计用于处理点云数据，同时最大限度地减少稀疏和不规则的开销。我们在系统级开发了高性能 GPU 库（TorchSparse），以在通用硬件上加速稀疏和不规则的工作负载。此外，我们还设计了一种特殊的硬件加速器（PointAcc），它支持多种类型的点云深度学习算子，并缓解了点云计算中的内存瓶颈。

### 2. 背景

3D 数据通常以点云的形式存在：

```
