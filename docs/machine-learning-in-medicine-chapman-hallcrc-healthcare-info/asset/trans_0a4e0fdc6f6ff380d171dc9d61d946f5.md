

[12] Lee CS, Baughman DM, Lee AY. Deep Learning Is Effective for Classifying Normal versus Age-Related Macular Degeneration OCT Images. Ophthalmol Retina. 2017;1: 322–327. doi:10.1016/j.oret.2016.12.009

[13] Grassmann F, Mengelkamp J, Brandl C, Harsch S, Zimmermann ME, Linkhor B, et al. A Deep Learning Algorithm for Prediction of Age-Related Eye Disease Study Severity Scale for Age-Related Macular Degeneration from Color Fundus Photography. Ophthalmology. 2018;125: 1410–1420. doi:10.1016/j.ophtha.2018.02.037

[14] Tham Y-C, Li X, Wong TY, Qigley HA, Aung T, Cheng C-Y. Global prevalence of glaucoma and projections of glaucoma burden through 2040: a systematic review and meta-analysis. Ophthalmology. 2014;121: 2081–2090. doi:10.1016/j.ophtha.2014.05.013

[15] Li Z, He Y, Keel S, Meng W, Chang RT, He M. Efficacy of a Deep Learning System for Detecting Glaucomatous Optic Neuropathy Based on Color Fundus Photographs. Ophthalmology. 2018;125: 1199–1206. doi:10.1016/j.ophtha.2018.01.023

[16] Ting DSW, Pasquale LR, Peng L, Campbell JP, Lee AY, Raman R, et al. Artificial intelligence and deep learning in ophthalmology. Br J Ophthalmol. 2019;103: 167–175. doi:10.1136/bjophthalmol-2018-313173

[17] Fauw JD, Ledsam JR, Romero-Paredes B, Nikolov S, Tomasev N, Blackwell S, et al. Clinically applicable deep learning for diagnosis and referral in retinal disease. Nat Med. 2018;24: 1342–1350. doi:10.1038/s41591-018-0107-6

[18] Aggarwal P. Machine learning of retinal pathology in optical coherence tomography images. J Med Artif Intell. 2019;2. doi:10.21037/jmai.2019.08.01

[19] Damato B, Eleuteri A, Fisher AC, Coupland SE, Taktak AFG. Artificial Neural Networks Estimating Survival Probability after Treatment of Choroidal Melanoma. Ophthalmology. 2008;115: 1598–1607. doi:10.1016/j.ophtha.2008.01.032

# 第4章

## 基于细胞神经网络的热消融癌症治疗的热剂量建模

Jinao Zhang 和 Sunita Chauhan
*莫纳什大学*
*澳大利亚 Clayton*

Wa Cheung 和 Stuart K. Roberts
*Alfred 医院*
*澳大利亚 墨尔本*

### 目录

- 4.1 引言 28
- 4.2 软组织热剂量建模 30
- 4.3 细胞神经网络 31
  - 4.3.1 架构 31
  - 4.3.2 二维网格上的生物热传递的 CNN 表述 33
    - 4.3.2.1 二维规则网格 33
    - 4.3.2.2 二维不规则网格 34
  - 4.3.3 三维网格上的生物热传递的 CNN 表述 37
    - 4.3.3.1 三维规则网格 37
    - 4.3.3.2 三维不规则网格 38
  - 4.3.4 初始条件和边界条件 39
- 4.4 数值示例 39
  - 4.4.1 个体化热剂量计算 39
  - 4.4.2 高强度聚焦超声（HIFU）在肝肿瘤消融中的应用 41
- 4.5 讨论 45
- 4.6 结论 48
- 致谢 48
- 参考文献 48

### 4.1 引言

热消融疗法是一种癌症治疗方法，通过诱导温度变化引起细胞凝固坏死，从而原位杀死癌细胞。常用的热消融方法包括高热量（例如射频消融（RFA）、微波消融（MWA）、激光和高强度聚焦超声（HIFU）消融）和低热量（冷冻消融），其中 RFA 目前是最推荐的一线消融技术 [1]。在肝脏癌症的治疗中，热消融疗法允许在不进行手术的情况下治疗原发性（主要是肝细胞癌（HCC））和继发性肝脏肿瘤，并为不适合手术或不希望手术的患者提供了替代方案。小（<3 cm）肝脏肿瘤的热消融非常有效，几乎在所有患者中都实现了肿瘤完全坏死，并提供了与接受肝切除手术相似的生存结果 [2]。作为一线独立疗法或肝移植的桥梁疗法，它可以实现优异的长期总生存率和肿瘤特异性生存率 [3]。此外，热消融疗法中部署的方法通常是最小侵入性（如经皮 RFA）或非侵入性（如 HIFU），与手术相比，其相关并发症和死亡率更低。

为了协助热消融操作者提高患者安全性和提高消融准确性，计算机辅助治疗计划和分析变得日益重要，以提供计算机模拟分析和组织温度及热损伤的估计 [4]。为了使消融操作者能够立即可视化模拟结果以辅助治疗过程，数值计算需要实时解决方案。据报道，软组织温度和相关热剂量的实时计算和分析可以通过精确管理热能来产生期望的肿瘤热损伤，同时避免周围健康组织中的热斑和意外热损伤，从而有助于提高治疗的安全性和有效性 [5]。这不仅能够推动临床程序的技术进步，还能改善患者的实际预后。

然而，大多数传统数值方法 [6–8] 旨在准确近似软组织中生物热传递的特性，而未考虑快速计算的需求。例如，据报道，使用传统方法模拟热消融过程所消耗的计算时间从几分钟到几小时不等 [9]，这主要归因于模拟过程中每个时间步长都要求解非线性生物热传递。基于有限差分法（FDM）[10]，Schwenke 等人 [11] 和 Kalantzis 等人 [12] 研究了基于图形处理单元（GPU）的技术，用于快速模拟聚焦超声治疗。Zhang 等人 [13,14] 和 Mariappan 等人 [15] 提出了 GPU 加速的有限元方法，用于热消融中生物热传递的高速求解。He 和 Liu [16] 设计了一种交替方向显式方法，而 Carluccio 等人 [17] 开发了一种基于空间滤波器以减少计算时间的方法。其他方法，如快速显式动力学有限元算法 [18,19]、基于快速傅里叶变换的 FDM 算法 [20]、模型降阶方法 [21]、基于有限体积的多重网格方法 [22,23] 以及基于无网格点配法的动态模态分解方法 [24]，也被研究用于快速生物热传递分析。

最近，由于细胞神经网络（CNNs）具有单元集体且同时的计算活动，其在快速数值计算 [29] 方面备受关注，并被应用于生物力学领域 [25–28]。CNN 由 Chua 和 Yang [30] 开发，主要用于图像处理，如去噪、模式识别和特征提取 [31]（见综述论文 [32] 和书籍 [33]）。显而易见，CNN 解可以很好地近似许多非线性偏微分方程，包括反应扩散方程、Burgers’方程、Navier–Stokes方程和热方程 [34,35]。因此，各种非线性动态系统，包括机械振动系统 [36]、模式形成和波传播 [37]、微分方程 [29]、可变形模型 [38,39] 以及生物热传递问题 [40,41]，都通过 CNN 建模以实现高效且有效的求解。在本工作中，鉴于其计算特性，采用 CNN 高效求解生物热传递方程，用于生物软组织中的热剂量建模，为热消融癌症治疗提供计算机辅助规划和分析。本文提出了计算域上二维和三维规则及不规则网格的生物热传递方程的 CNN 表述，并采用所提出的 CNN 模型来预测软组织温度分布并估计相关的热剂量，通过肝脏肿瘤局部热消融的临床相关场景进行验证。

本文其余部分结构如下：第4.2节介绍软组织热剂量建模的基本控制方程，随后在第4.3节中介绍 CNN 架构以及二维和三维规则及不规则网格上的 CNN 表述。第4.4节展示了个体化热剂量估计的计算机模拟结果以及其在 HIFU 肝肿瘤消融中的应用。讨论在第4.5节中呈现，第4.6节总结了本工作。

### 4.2 软组织热剂量建模

当生物软组织在一定时间内达到特定温度时，会发生不可逆的细胞蛋白质变性和凝固坏死。尽管一些研究 [42,43] 假设凝固坏死区（病灶）近似为球形或椭球体等规则形状，但已表明病灶的范围与组织中获得的热剂量有关，热剂量是组织热暴露历史的度量。在本工作中，使用一个将病灶范围与组织温度为 $43^{\circ}$C 时的累积等效分钟数（CEM）的热暴露联系起来的热剂量经验度量 CEM$_{43}$ [44]，并认为 240 CEM$_{43}$ 时发生肿瘤坏死 [45]。数学上，CEM$_{43}$ 由 [44] 计算得出

$$\mathrm{CEM}_{43}=\int_{0}^{t} R^{(43-T(t))} d t \tag{4.1}$$

其中 $t$ 是热暴露持续时间，$T(t)$ 是局部组织温度，$R$ 是常数，其值为

$$R = \begin{cases} 0.25, & (T(t)<43^{\circ}\mathrm{C}) \\ 0.5, & (T(t)\geq43^{\circ}\mathrm{C}) \end{cases} \tag{4.2}$$

为了确定 $\mathrm{CEM}_{43}$ 的数量，必须计算并记录软组织温度场的时间演化（温度历史）。生物软组织中的热传递行为由

