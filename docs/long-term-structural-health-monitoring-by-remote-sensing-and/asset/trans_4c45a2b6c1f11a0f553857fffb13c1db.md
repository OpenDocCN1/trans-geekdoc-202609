

## 5.3 未来研究机会

尽管本研究提出了各种机器学习方法，以在小位移数据和不可预测 EOCs 存在的情况下发展经典的 SAR 辅助 SHM，且这些方法能够呈现可靠和正确的结果，我们也为进一步的研究提出了一些建议。

### 5.3.1 基于生成对抗网络的数据增强

在本书中，基于马尔可夫链蒙特卡洛概念的概率算法已被用于扩展小位移点。由于 Goodfellow 等人（2014）提出生成对抗网络（GANs），深度学习发生了革命性变革，建议通过各种 GANs（Creswell 等人，2018）扩展数据增强过程。

### 5.3.2 新型机器学习算法下的数据归一化

本书已验证，无论数据和结构的类型如何，EOCs 在现实世界的长期 SHM 项目中都是不可避免的。在此基础上，实施数据归一化以减轻或消除 EOCs 对基于 SHM 的特征的所有影响至关重要。在本工作中，已尝试借助深层和浅层 DAEs 开发各种基于 DNN 的数据归一化算法。尽管一些机器学习算法（如无监督教师－学生学习、迁移学习和在线学习）已被纳入以提出这些算法，但仍有可能利用更多新颖的机器学习概念。因此，建议通过利用一些高级机器学习算法（如集成学习（Dietterich 2000）、半监督学习（Schwenker and Trentin 2014）、主动学习（Settles 2012）、字典学习（Daneshvar 等人，2023）、元学习（Entezami 等人，2023a）、多任务学习（Entezami 等人，2023b）、混合学习（Sarmadi 等人，2023）、经验学习（Entezami 等人，2022）以及基于稀疏、去噪、堆叠和变分配置的新型 DAEs（Charte 等人，2018；Dong 等人，2018）来扩展数据归一化程序。

另一方面，本书中提出的数据归一化技术需要一些超参数，这使它们成为数据归一化的参数化算法。为避免在超参数优化问题上遇到困难和挑战，建议利用一些新机器学习概念（如无监督特征选择（Solorio-Fernández 等人，2020）和特征加权（Niño-Adan 等人，2021））开发非参数数据归一化方法。

### 5.3.3 面向实时 SHM 的增强在线学习

尽管所提出的在线混合学习为实时 SHM 开辟了新方法论，但决策取决于一个关于停止在线学习阶段的假阳性错误率的预定义值。为增强该方法论，建议使用用于在线学习阶段停止条件的新性能评估指标来开发更稳健的算法。

### 5.3.4 损伤定位

除了早期损伤检测问题之外，SHM 中另一个重要挑战是定位结构的损伤区域（Entezami 等人，2018；Heravi 等人，2022）。在这方面，提出损伤定位框架将非常合适。基于接触式感知技术的无监督损伤定位的主要局限之一是安装足够传感器以测量合适信息的限制（Entezami 和 Shariatmadar，2019；Entezami 等人，2022）。遥感技术和 InSAR 技术的一大优点是为测量位移/变形数据提供分布式目标点，这些点可以作为虚拟接触式传感器（Behkamal 等人，2023a, b）。因此，建议利用遥感技术获取的信息，提出用于定位损伤区域的无监督学习方法。

## References

Behkamal B, Entezami A, De Michele C, Arslan AN (2023a) 基于机器学习技术的遥感有限结构位移热效应消除。Remote Sens 15(12):3095. https://doi.org/10.3390/rs15123095

Behkamal B, Entezami A, De Michele C, Arslan AN (2023b) 基于混合感知和受监督回归模型的长跨桥梁温度效应研究。Remote Sens 15(14):3503. https://doi.org/10.3390/rs15143503

Charte D, Charte F, García S, del Jesus MJ, Herrera F (2018) 非线性特征融合自编码器实用教程：分类学、模型、软件和指南。Inf Fusion 44:78–96. https://doi.org/10.1016/j.inffus.2017.12.007

Creswell A, White T, Dumoulin V, Arulkumaran K, Sengupta B, Bharath AA (2018) 生成对抗网络：概述。IEEE Signal Process Mag 35(1):53–65. https://doi.org/10.1109/MSP.2017.2765202

Daneshvar MH, Sarmadi H, Yuen K-V (2023) 用于在不同测量周期下消除环境影响的局部无监督混合学习方法。Meas 208:112465. https://doi.org/10.1016/j.measurement.2023.112465

Dietterich TG (2000) 机器学习中的集成方法。载于：多分类器系统。Springer, Berlin, pp 1–15

Dong G, Liao G, Liu H, Kuang G (2018) 自编码器及其变体综述：基于合成孔径雷达图像目标识别的比较视角。IEEE Geosci Remote Sens Mag 6(3):44–68. https://doi.org/10.1109/MGRS.2018.2853555

Entezami A, Shariatmadar H (2019) 基于特征提取和多变量距离相关性方法的新型混合算法，在环境激励和非平稳振动信号下进行损伤定位。Struct Health Monit 18(2):347–375. https://doi.org/10.1177/14771475217854372

Entezami A, Shariatmadar H, Karamodin A (2018) 基于新型统计模式识别方法的环境和运行可变性下的数据驱动损伤诊断。Struct Health Monit 18(5–6):1416–1443. https://doi.org/10.1177/1475921718800306

Entezami A, Shariatmadar H, Mariani S (2020) 用于来自稠密传感器网络的大规模振动数据的结构健康监测快速无监督学习方法。Struct Health Monit 19(6):1685–1710. https://doi.org/10.1177/1475921719894186

Entezami A, Shariatmadar H, De Michele C (2022) 短期和长期结构健康监测的非参数经验机器学习。Struct Health Monit 21(6):2700–2718. https://doi.org/10.1177/14759217211069842

Entezami A, Sarmadi H, Behkamal B (2023a) 基于无监督元学习的大量和缺失数据下混凝土和钢桥的长期健康监测。Eng Struct 279:115616. https://doi.org/10.1016/j.engstruct.2023.115616

Entezami A, Sarmadi H, Behkamal B, De Michele C (2023b) 基于创新多任务无监督学习方法的严重环境可变性下桥梁持续健康监测。Struct Infrastruct Eng In Press 1–19. https://doi.org/10.1080/15732479.2023.2166538

Goodfellow I, Pouget-Abadie J, Mirza M, Xu B, Warde-Farley D, Ozair S, Courville A, Bengio Y (2014) 生成对抗网络。Adv Neural Inf Process Syst 27

Heravi MA, Tavakkoli SM, Entezami A (2022) 基于自回归损伤特征概率密度函数和快速距离相关性方法的结构健康监测。J Vib Control 28(19–20):2786–2802. https://doi.org/10.1177/1077546321020198

Niño-Adan I, Manjarres D, Landa-Torres I, Portillo E (2021) 特征加权方法：综述。Expert Syst Appl 184:115424. https://doi.org/10.1016/j.eswa.2021.115424

Sarmadi H, Entezami A, Magalhães F (2023) 基于创新混合特征加权–选择算法和自然最近邻搜索的连续动态监测无监督数据归一化。Struct Health Monit Press. https://doi.org/10.1177/147592172231166116

Schwenker F, Trentin E (2014) 模式分类与聚类：半监督学习方法综述。Pattern Recog Lett 37:4–14. https://doi.org/10.1016/j.patrec.2013.10.017

Settles B (2012) 主动学习。morgan & claypool, San Rafael, California, United States

Solorio-Fernández S, Carrasco-Ochoa JA, Martínez-Trinidad JF (2020) 无监督特征选择方法综述。Artif Intell Rev 53(2):907–948. https://doi.org/10.1007/s10462-019-09682-y

