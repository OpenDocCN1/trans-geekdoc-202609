
* Valverde, I.C., Castilla, L.H., Nuñez, D.F., Rodriguez-Senín, E., Ferreira, R.M. 2013. Development of new insulation panels based on textile recycled fibers. *Waste and Biomass Valorization*. 4, pp. 139–146.
* Volf, M., Diviš, J., Havlík, F. 2015. Thermal, moisture and biological behaviour of natural insulating materials. *Energy Procedia*. 78, pp. 1599–1604.
* Vololonirina, O., Coutand, M., Perrin, B. 2014. Characterization of hygrothermal properties of wood-based products – Impact of moisture content and temperature. *Construction and Building Materials*. 63, pp. 223–233.
* Wang, H., Chiang, P., Cai, Y., Li, C., Wang, X., Chen, T., Wei, S., Huang, Q. 2018. Application of wall and insulation materials on green building: A review. *Sustainability*. 10, 3331.
* Wang, J.C., Yan, P. Y. 2004. Influence of external thermal insulation compound system on the indoor temperature and humidity. *Low Temperature Architecture Technology*. 2, pp. 80–81.
* Wei, K.C., Lv, C.L., Chen, M.Z., Zhou, X.Y., Dai, Z.Y., Shen, D. 2015. Development and performance evaluation of a new thermal insulation material from rice straw using high frequency hot-pressing. *Energy and Buildings*. 87, pp. 116–122.
* Wiprächtiger, M., Haupt, M., Heeren, N., Waser, E., Hellweg, S. 2020. A framework for sustainable and circular system design: Development and application on thermal insulation materials. *Resources, Conservation and Recycling*. 154, 104631.
* Wu, S., Yan, T., Kuai, Z., Pan, W. 2020. Thermal conductivity enhancement on phase change materials for thermal energy storage: A review. *Energy Storage Materials*. 25, pp. 251–295.
* Xing, Q., Hao, X., Lin, Y., Tan, H., Yang, K. 2019. Experimental investigation on the thermal performance of a vertical greening system with green roof in wet and cold climates during winter. *Energy and Buildings*. 183, pp. 105–117.
* Xu, J.Y., Sugawara, R., Widyorini, R., Han, G.P., Kawai, S. 2004. Manufacture and properties of low-denstiy binderless particleboard from kenaf core. *Journal of Wood Science*. 50, pp. 62–67.
* Yu, Z.L., Yang, N., Zhou, L.C., Ma, Z.Y., Zhu, Y.B., Lu, Y.Y., Qin, B., Xing, W.Y., Ma, T., Li, S.C., Gao, H.L., Wu, H.A., Yu, S.H. 2018. Bioinspired polymeric woods. *Science Advances*. 4, 8, 7223.
* Zach, J., Hroudová, J., Brožovský, J., Krejza, Z., Gailius, A. 2013. Development of thermal insulating materials on natural base for thermal insulation systems. *Procedia Engineering*. 57, pp. 1288–1294.
* Zach, J., Korjenic, A., Petránek, V., Hroudová, J., Bednar, T. 2012. Performance evaluation and research of alternative thermal insulations based on sheep wool. *Energy and Buildings*. 49, pp. 246–253.
* Zhou, X.Y., Zheng, F., Li, H.G., Lu, C.L. 2010. An environment-friendly thermal insulation material from cotton stalk fibers. *Energy and Buildings*. 42, pp. 1070–1074.
* Zuo, J., Zhao, Z.Y. 2014. Green building research – current status and future agenda: A review. *Renewable and Sustainable Energy Reviews*. 30, pp. 271–281.

# 10 面向智慧城市绿色能源的光伏框架在局部阴影条件下的最大功率点跟踪技术

## 面向智慧城市的绿色能源

**Mohammad Junaid Khan 和 Anurag Choudhary**

DOI: [10.1201/9781003153405-10](https://doi.org/10.1201/9781003153405-10)

## 目录

* 10.1 简介
* 10.2 扰动观察法 MPPT 技术
* 10.3 电导增量法 MPPT 技术
* 10.4 拟议系统的仿真模型
* 10.5 结果与讨论
* 10.6 结论
* 参考文献

### 10.1 简介

由于技术进步，光伏 (PV) 框架近年来已成为最成功的可再生能源资源之一。光伏器件产生非线性特性。因此，光伏系统的主要挑战是在标准化和不断变化的气象条件下实现最大功率点跟踪 (MPPT) 技术。局部阴影条件 (PSC) 会在 P-V 曲线中引发多个峰值。本章针对面向智慧城市绿色能源的应用，在不同运行条件下对两种流行的 MPPT 算法——即电导增量法 (INC) 和扰动观察法 (P&O)——进行了比较研究。完整的光伏架构是利用建模/Simulink 配合升压变换器和 MPPT 算法构思设计的。在标准实验和各种气象条件下，通过观察这两种建议的 MPPT 解决方案在最大功率点附近的最大功率跟踪情况，对其效率进行了测试验证。

#### 光伏太阳能发电与 MPPT 技术

光伏太阳能发电是最具前景的可再生能源之一，它从太阳获取电力（Khan 2019）。它环保、使用安全，且维护需求极低。尽管如此，光伏系统仍存在若干缺点，例如在局部遮挡条件（PSC）下会影响光伏输出。因此，必须应用最大功率点跟踪（MPPT）技术，以在各种天气条件下最大化输出容量。MPPT 是一种算法，用于确保光伏系统框架始终以更高的效率运行（Boukenoui 2015）。在最大功率点（MPP）路径上，占空比会被增加或减小。当不同电池暴露在不同辐照度水平下时，称为局部遮挡条件（PSC），例如建筑物阴影、光伏电池积尘、局部多云、树木遮挡等（Saravanan, 2016）。尽管如此，某些 MPPT 算法可使光伏系统在变化的运行条件下仍保持高性能运行，因为大多数 MPPT 算法寻找的最大功率会导致提取功率损失。为了从光伏组件获取更多功率，本研究采用扰动观察法（P&O）和电导增量法（INC）算法作为 MPPT 控制器。光伏模型设计为以更高效率运行（Kumar et al. 2017a）。光伏组件的功率输出和电气效率与辐照度和温度呈线性相关。此外，本文对比了这两种 MPPT 技术，以考察其有效性、复杂性、MPP 周围的稳定时间及收敛性。

##### 历史方法

过去，曾采用不同方法确保光伏系统的高性能运行。近年来最受推崇且应用最广的方法之一是开路电压比例法（FOCV）。该方法发现，在最大功率点（MPP）处，光伏阵列电压与开路电压（Voc）成正比（Khan 2020）。这取决于太阳能电池的来源、制造工艺和天气条件（Palariya 2016）。通过关断功率变换器，通过计算 Voc 来得出 MPP 处的电压水平。近年来，多位研究者实现了短路电流（Isc）法。该方法的运作原理与 Voc 法类似。它利用光伏阵列在最大功率点的电流（Impp）与 Isc 之间的线性关系理论（Rai et al. 2016）。在 PSC 条件下，这两种方法并非必需。两者收敛速度均较低，且会经历暂时性功率损失。但在 PSC 下精度较低，且因 P-V 输出曲线特性和真实功率峰值无法辨识，导致无法在全功率下工作。

##### 纹波相关与基于 AI 的技术

另一种解决方案是采用纹波相关控制。该技术利用变换器开关产生的纹波来控制电流和电压中的最大功率。为获得全功率，利用了纹波电流或电压波形与功率之间的关系。该原理由 Gupta (2014) 阐述。该技术依赖于无局部极大值的 P-V 曲线，且输入电压始终为非零纹波之和。该技术的缺点是，由于局部极大值的存在，会发生错误的 MPP 跟踪。已有几项研究采用基于人工智能的技术（Khan 2019; Khan 2020），以稳健的方式克服上述缺点。尽管这些算法能在非线性特性下运行，但需要更多计算量（Farayola 2018; Kumar et al. 2017b）。尽管这种方法正成为最流行的方法，但也存在一些缺点，如结构模糊、难以实现，且实施需要详细且昂贵的计算（Farayola et al. 2018; Bansal et al. 2021; Khan 2017）。常用光伏系统的效率通常在 6% 到 16% 之间变化，其输出差异取决于所用设备（Jaen 2008; Roshan 2013; Farayola et al. 2018）。为获得高转换效率，主要有两种途径。第一种侧重于机械和电气（机电）仪器，也称为太阳跟踪器，旨在光伏组件运行期间支持其处于最佳位置。

![Figure 10.1 太阳能电池的 V-I 曲线是非线性的。](img/9780367720919_C010_001.jpg)

**图 10.1** 太阳能电池的 V-I 曲线是非线性的。

第二种完全基于电子系统，有助于调整光伏组件的电气特性，使光伏组件在最佳工作阶段运行。基本的太阳能电池 V-I 特性曲线呈非线性，如 图 10.1 所示。

基于遮挡、风速、太阳入射角等各种环境因素，光伏电池在局部遮挡条件下产生不同量的功率（Masoum 2002）。为从光伏系统获取最大功率，MPPT 技术配备了合适的控制器。为使光伏组件在最大功率下运行，MPPT 方法形式多样。然而，在瞬息万变的天气条件下，特定技术的输出取决于其跟踪能力。经典 MPPT 技术（Ahmad 2019; De Brito et al. 2013）包括电导增量法（InC）、短路与开路电压比例法、扰动观察法（P&O）、爬山法（HC）、自适应参考与恒定电压法，以及基于纹波相关控制（RCC）的 MPPT。由于算法复杂度较低，这些方法易于应用。然而，这些实现在 MPP 周围存在剧烈扰动，导致功率损失。相比之下，这些经典策略首先忽略了 PSC 导致的无法跟踪真实 MPP 的影响。

##### 章节结构

本章结构如下：第 10.2 节 描述 P&O MPPT 技术。第 10.3 节 介绍 INC MPPT 算法。第 10.4 节 定义仿真模型。第 10.5 节 显示结果与讨论。本章以 第 10.6 节 结束。

### 10.2 扰动观察法 MPPT 技术

P&O 是许多研究者研究的最简单、最常用的技术。它通过电压检测和光伏系统电流来运行。它检测电压、电流并计算功率（Khan 2020）。这将新功率与存储在存储器中的先前能量进行对比。如果功率大于实际功率输出，则当前电压将等同于之前的电压。由于差值大于零，电压朝乐观方向变化以达到 MPP。除非功率差小于零，否则电压将向下波动。直到实现高效光伏系统运行（Abdelsalam et al. 2011），该过程持续进行。如 图 10.2 所示，流程图演示了开发的 P&O 技术。

![Figure 10.2 P&O MPPT 流程图。](img/9780367720919_C010_002.jpg)

**图 10.2** P&O MPPT 流程图。

该方法的优点是复杂度低、易于开发且可靠性高。然而，在稳态运行下，它在 MPP 周围振荡的缺点会导致功率损失。

### 10.3 电导增量法 MPPT 技术

#### INC MPPT 技术

INC 是一种广泛使用的 MPPT 技术，它将瞬时电导（即 `I/V`）与增量电导（即 `dI/dV`）进行比较。它还基于光伏组件功率对电压的公式推导，从而实现零平衡（Gil-Antonio 2016）。当增量电导等同于即时电导但极性相反时，可从图 10.2 获得最大功率点（MPP）。为了达到 MPP，服务周期通过一个微小因子被延长或缩短（Gupta and Saxena 2016）。INC MPPT 算法的优势在于其实施简单，具有更高的跟踪速度和性能（Karami 2017）。

![Figure 10.3 Flowchart of INC MPPT technique.](img/9780367720919_C010_003.jpg)

**图 10.3** INC MPPT 技术流程图。

### 10.4 拟议系统的仿真模型

实施仿真旨在验证并评估两种方法在局部阴影条件（PSC）下的有效性，即 P&O 和 INC 两种 MPPT 算法的速度和精度，如图 10.3 所示。使用 `MATLAB / SIMULINK` 程序对上述 MPPT 算法进行建模和仿真。

#### 表 10.1：浙江金德太阳能技术 KD-P230 规格参数

| **序号** | **参数** | **数值** |
| :--- | :--- | :--- |
| 1. | 最大功率 | 226.78 |
| 2. | 每组件电池片数量 | 60 |
| 3. | 开路电压 | 36.3 |
| 4. | 短路电流 | 8.3 |
| 5. | 最大功率点电压 | 29 |
| 6. | 最大功率点电流 | 7.82 |
| 7. | 开路电压温度系数 | -0.33 |
| 8. | 短路电流温度系数 | 0.05 |
| 9. | 辐照度 | 变化 |
| 10. | 温度 (°C) | 27 |
| 11. | 组件并联串数 | 01 |
| 12. | 组件串联串数 | 03 |

#### 表 10.2：DC-DC 变换器规格参数

| **序号** | **参数** | **数值** |
| :--- | :--- | :--- |
| 1. | 电感 | 1mH |
| 2. | 电容 | 40 微法拉 |
| 3. | 阻性负载 | 15 欧姆 |
| 4. | 输入电阻 | 0.1 欧姆 |
| 5. | IGBT 数量 | 01 |
| 6. | 二极管数量 | 01 |
| 7. | 开关频率 | 11kH |
| 8. | 占空比 | 变化 |

浙江金德太阳能技术 KD-P230 光伏面板和升压 DC-DC 变换器的规格分别在表 10.1 和表 10.2 中讨论。图 10.4 展示了拟议工作的仿真模型，图 10.5 展示了 P&O MPPT 技术的子系统，图 10.6 展示了基于 INC 的 MPPT 技术子系统。

![Figure 10.4 Simulation model of proposed system.](img/9780367720919_C010_004.jpg)

**图 10.4** 拟议系统的仿真模型。

![Figure 10.5 Subsystem of P&O MPPT technique.](img/9780367720919_C010_005.jpg)

**图 10.5** P&O MPPT 技术的子系统。

![Figure 10.6 Subsystem of INC MPPT technique.](img/9780367720919_C010_006.jpg)

**图 10.6** INC MPPT 技术的子系统。

升压变换器用于匹配源和负载的阻抗。电路中使用占空比来控制功率。辐照度和温度是光伏系统的相应输入。在 `11 kHz` 的开关频率下，使用了脉宽调制（PWM）发生器，PWM 发生器提供三角波形，如 Bounechba (2014)所述。所有情况的仿真时间均为一秒。

### 10.5 结果与讨论
