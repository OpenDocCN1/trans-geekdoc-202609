
距离手术台较远，为希望与病理学家一起查看切片的外科医生造成了后勤障碍。此外，制作高质量病理切片的过程耗时且劳动密集。因此，病理学家在标本采集后 30–45 分钟才会致电手术室给出诊断。该过程的低效使外科医生与组织学数据隔绝，并限制了其用于指导手术决策的方式。

鉴于现代神经病ology工作流程中的挑战，人工智能在多个方面具有巨大潜力：(1) 验证是否采集到病变组织，(2) 协助组织学诊断，(3) 帮助界定无肉眼边界的肿瘤的手术终点，以及 (4) 在未来，预测可操作的和诊断性的分子标志物。在固定组织中，人工智能已应用于乳腺癌和结肠癌中上皮区与间质区的分类 [57]、坏死区与非坏死区的区分 [58]，以及高级别与低级别胶质瘤的区分 [59]。尽管如此，人工智能在辅助诊断方面的应用仅解决了神经病理学中建立诊断相关的挑战。在传统的组织学工作流程中，与组织运输和处理相关的许多障碍仍然存在。为了充分利用人工智能辅助病理诊断快速进步所带来的机遇，与快速组织学技术相结合是必不可少的。

## 快速组织学解读的方法

为此，已提出并在不同程度上验证了多种无切片组织学方法。MUSE、受激拉曼组织学（SRH）和光片显微镜是用于成像未处理或最小处理生物标本的最有前景的工具之一（图 7.6）。

虽然已提出众多无切片组织学技术，但只有 SRH 已被纳入在临床环境中用于脑肿瘤诊断的经验证的人工智能诊断流程。Hollon 等人改编了 Inception-V2 CNN，利用 SRH 图像诊断 10 种最常见的脑肿瘤，并将他们的软件部署在床旁 SRH 成像仪上。在 278 名患者的头对头临床试验中，Hollon 等人证明，利用 SRH 和 CNN 的自主诊断路径能够预测诊断，其性能不劣于对同一患者常规组织学切片进行解读的委员会认证神经病理学家 [61]。两个组的准确率约为 94%，有趣的是，两个组的错误完全不重叠（图 7.7）。因此，本研究的作者得出结论，SRH + CNN 路径可在病理资源不可用时作为脑肿瘤诊断的独立方法使用，也可在人员充足的中心作为提高神经病理学诊断准确性的方法。尽管作者将试验纳入限制在常见的脑肿瘤类型，但他们还提供了一种区分常见和不常见组织学类别的方法，以使系统适用于所有中枢神经系统肿瘤。该算法还被用于开发语义分割工具，能够描绘最可能含有病变组织的组织学图像区域（图 7.8）。作者还得出结论，鉴于其 CNN 用于分类脑肿瘤的特征，未来可为其他器官的肿瘤开发类似算法。

值得推测，在分类学习步骤之前进行基于人工智能的图像增强是否会提高后者的性能。

## 图 7.6

### (A) 紫外表面激发显微镜
![](img/ec668102bd6cbe5645156f246a7c2e8b_148_0.png)

### (B) 光片显微镜
![](img/ec668102bd6cbe5645156f246a7c2e8b_148_1.png)

### (C) 受激拉曼组织学
![](img/ec668102bd6cbe5645156f246a7c2e8b_148_2.png)

包括 (A) 紫外表面激发显微镜、(B) 光片显微镜和 (C) 受激拉曼组织学（SRH）的无切片组织学方法，均可在最小处理或未处理的组织上进行，以在无需常规病理科资源的情况下生成诊断性组织学图像。每种技术都依赖于光学而非物理切片成像组织，简化了生成诊断性组织学图像所需的工作流程。SRH 作为床旁组织学模式具有独特价值，因为生成组织学图像无需对组织进行染色、透明化或处理。在 SRH 中，新鲜标本可在床旁放入成像仪，通过相对简单的光谱带组合和重新着色快速创建虚拟 H&E 显微图像。为此，学术-工业合作产生了首台 FDA 注册的成像仪，目前已在美国多个手术室中使用。

> 经 Orringer DA, Camelo-Piragua S 许可改编，快速且无切片成像。Nature Biomedical Engineering, 2017;1(12):926–928. https://doi.org/10.1038/s41551-017-0172-z.

![](img/ec668102bd6cbe5645156f246a7c2e8b_149_0.png)

## 图 7.7

SRH 加 CNN 与常规 H&E 组织学的前瞻性临床试验。(A) 各医疗中心的真实类别预测概率按降序绘制，并标明正确（绿色）或错误（红色）分类。(B) 对照组和实验组的多类混淆矩阵。对照组，即传统 H&E 组织学加病理学家，错误主要为恶性胶质瘤的误分类（10/17）。胶质瘤在 SRH 加 CNN 组中的错误率最高（9/14）。常见肿瘤，包括室管膜瘤、髓母细胞瘤和毛细胞星形细胞瘤也被误分类，很可能是由于模型训练病例不足，导致与对照组相比平均类别准确率较低。随着更多 SRH 训练数据的增加，这些错误可能会得到改善。SRH，受激拉曼组织学；CNN，卷积神经网络（CNN）。

*经 Hollon TC 等许可改编，近实时术中脑肿瘤诊断使用受激拉曼组织学和深度神经网络。* Nature Medicine, 2020;26(1):52–58. https://doi.org/10.1038/s41591-019-0715-9.

![](img/ec668102bd6cbe5645156f246a7c2e8b_150_0.png)

## 图 7.8

语义分割。(A) 一名胶质母细胞瘤患者的标本 SRH 马赛克图像包含 (B) 致密肿瘤浸润、肿瘤-脑界面以及胶质增生的瘤周区域。马赛克中的图块被输入语义分割算法 (C)，该算法由卷积神经网络（CNN）分类，然后分配一个数值，以颜色（红绿蓝）表示给定区域包含肿瘤、非诊断性组织或非病变组织的可能性。分类器提供 10 个最常见脑肿瘤类别中类别成员的可能性 (D)。整个马赛克可为每个类别预测为热图，其中 3 个在此显示 (E)。SRH，受激拉曼组织学；CNN，卷积神经网络（CNN）。

*经 Hollon TC 等许可改编，近实时术中脑肿瘤诊断使用受激拉曼组织学和深度神经网络。Nature Medicine, 2020;26(1):52–58. https://doi.org/10.1038/s41591-019-0715-9.*

- [25] Perez L, Wang J. 深度学习中图像分类数据增强的有效性。ArXiv:171204621 Cs. Dec. 2017.
- [26] Ciompi F, et al. 卷积网络结直肠组织分类中染色标准化的重要性。In: 2017 IEEE 第14届生物医学成像国际研讨会（ISBI 2017）；2017. p. 160–3. https://doi.org/10.1109/ISBI.2017.7950492.
- [27] Janowczyk A, Basavanhally A, Madabhushi A. 使用稀疏自编码器进行染色标准化（StaNoSA）：数字病理学应用。Computerized Medical Imaging and Graphics 2017;57:50–61. https://doi.org/10.1016/j.compmedimag.2016.05.003.
- [28] Ruifrok AC, Johnston DA. 通过颜色解卷积对组织化学染色的定量。Analytical and Quantitative Cytology and Histology 2001;23(4):291–9.
- [29] Azevedo Tosta TA, de Faria PR, Neves LA, do Nascimento MZ. H&E 染色组织学图像的计算标准化：进展、挑战和未来潜力。Artificial Intelligence in Medicine 2019;95:118–32. https://doi.org/10.1016/j.artmed.2018.10.004.
- [30] Roy S, kumar Jain A, Lal S, Kini J. 关于组织病理学图像颜色标准化方法的研究。Micron 2018;114:42–61. https://doi.org/10.1016/j.micron.2018.07.005.
- [31] Bug D, et al. 使用深度卷积特征的基于上下文的组织学染色标准化。In: Deep learning in medical image analysis and multimodal learning for clinical decision support, Cham; 2017. p. 135–42. https://doi.org/10.1007/978-3-319-67558-9_16.
- [32] F. G. Zanjani, S. Zinger, and B. E. Bejnordi, “使用生成神经网络的组织病理学染色颜色标准化，”p. 16.
- [33] Chen X, Duan Y, Houthooft R, Schulman J, Sutskever I, Abbeel P. InfoGAN：通过信息最大化生成对抗网络的可解释表示学习。In: Lee DD, Sugiyama M, Luxburg UV, Guyon I, Garnett R, editors. Advances in neural information processing systems 29. Curran Associates, Inc.; 2016. p. 2172–80.
- [34] Kingma DP, Welling M. 自动编码变分贝叶斯。ArXiv:13126114 Cs Stat. May 2014.
- [35] Tellez D, et al. 定量评估计算病理学卷积神经网络中数据增强和染色颜色标准化的影响。Medical Image Analysis 2019;58:101544. https://doi.org/10.1016/j.media.2019.101544.
- [36] Rivenson Y, Liu T, Wei Z, Zhang Y, de Haan K, Ozcan A. PhaseStain：使用深度学习对无标记定量相位显微镜图像进行数字染色。Light: Science & Applications 2019;8(1):1–11. https://doi.org/10.1038/s41377-019-0129-y.
- [37] Combalia M, Perez-Anker J, Garcia-Herrera A. 通过深度学习的数字染色共聚焦显微镜。In: Proceedings of the 2nd international conference on medical imaging with deep learning (PMLR), 102; 2019. p. 121–9.
- [38] Borhani N, Bower AJ, Boppart SA, Psaltis D. 通过将深度神经网络应用于多模态多光子显微镜的数字染色。Biomedical Optics Express 2019;10(3):1339–50. https://doi.org/10.1364/BOE.10.001339.
- [39] Nygate YN et al. HoloStain：单个生物细胞的全息虚拟染色。p. 20.
- [40] Christiansen EM, et al. 计算机模拟标记：在未标记图像中预测荧光标记。Cell 2018;173(3):792–803. https://doi.org/10.1016/j.cell.2018.03.040. e19.
- [41] Rana A, Yauney G, Lowe A, Shah P. 使用生成对抗神经网络对前列腺核心活检 RGB 图像进行计算组织学染色和脱色。
