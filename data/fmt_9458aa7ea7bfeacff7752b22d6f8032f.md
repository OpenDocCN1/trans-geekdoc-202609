
# 参考 P&O 和 INC MPPT 技术

参考 P&O 和 INC MPPT 技术，引用了来自 `MATLAB/SIMULINK` 模型的仿真结果。结果为使用不同 MPPT 技术的拟议系统的输出功率和电压。所有情况的热特征恒定为 `27°C`，但太阳辐照度如图 10.7 所示发生变化。图 10.8 展示了使用不同 MPPT 技术的拟议系统输出功率特性，图 10.9 展示了使用不同 MPPT 技术的拟议系统输出电压特性。

图 10.8 和图 10.9 演示了源自 MATLAB 仿真的每种 MPPT 算法的示意性效果。优于 P&O 的推荐算法是 INC MPPT 策略。在所有仿真结果中，INC 算法在汇聚速度和在 PSC 下跟踪真实 MPP 方面均优于 P&O。P&O 在 MPP 附近具有更快的稳定周期。为验证拟议工作的 MPPT 跟踪性能，开发了一个仿真，如图 10.4 所示。

![Figure 10.7 Irradiations pattern for PV module.](img/9780367720919_C010_007.jpg)

**图 10.7** 光伏组件的辐照度模式。

![Figure 10.8 Output power characteristics of proposed system using different MPPT techniques.](img/9780367720919_C010_008.jpg)

**图 10.8** 使用不同 MPPT 技术的拟议系统输出功率特性。

![Figure 10.9 Output voltage characteristics of proposed system using different MPPT techniques.](img/9780367720919_C010_009.jpg)

**图 10.9** 使用不同 MPPT 技术的拟议系统输出电压特性。

作为太阳能光伏源，采用 I-V 曲线法对各种 PSC 模式进行编程。为了将光伏源的输出提供给阻性负载，使用由 PWM 信号驱动的 DC-DC 升压变换器。升压变换器的规格在表 10.2 中描述。使用 `MATLAB/SIMULINK` 平台对 MPPT 技术进行仿真和实施以供评估。虚拟平台上的电压和电流传感器用于测试升压变换器的输入/输出电压和电流。使用 `MATLAB/SIMULATION` 编写的 PC 软件程序执行和监控所有评估实验。图 10.5 和 10.6 展示了带有局部阴影的光伏组件的 MPPT 控制器。DC-DC 功率变换器的转换速率约为 `0.112 V/ms`。此外，两种实验算法切换工作点所需的最大电压变化为最大值。作为输出结果，达到稳态所需的总过渡时间为 `0.01 秒`。因此，每次电压变化存在 `0.02 ms` 的延迟时间。实验算法单次迭代的执行过程如图 10.2（流程图）所示。算法在每次迭代开始时测量各个工作电压。然后修改每个 PWM 信号的占空比，使光伏阵列处于固定电压。由于转换速度的差异，我们将算法的净计算时间相加作为比较的执行时间。变换器的时间常数会对总体 MPPT 时间产生重大影响。

尽管传统 P&O 可以在 PSC 下精确提取 MPP，但复杂的计算使得实施困难。虽然测量可以简化，但随着处理时间的减少，精度会下降。此外，更简单的计算过程可能导致搜索结果卡在 MPP 处。为了解决这个问题，本章提出了一种基于 INC 的 MPPT 算法，在响应时间方面优于传统的基于 P&O 的 MPPT 技术。

## 10.6 结论

很明显，经过仿真后，两种 MPPT 算法都将在局部遮阴条件下采集到最大功率。这两种技术均非基于光伏，且都能在光照变化的情况下定位真实的最大功率点 (MPP)，而且电导增量法 (INC) 收敛至 MPP 的效果优于扰动观察法 (P&O)。此外，针对局部遮阴条件 (PSC)，INC 提供了比 P&O 更好的补救措施。INC 方法提升了所提系统的性能，并减少了跟踪过程。与 INC 算法相比，P&O 结构简单、易于实现，且在 MPP 周围具有快速响应特性。

## 参考文献

*   Abdelsalam, A.K.、Massoud, A.M.、Ahmed, S. 和 Enjeti, P.N.，2011。面向光伏微网的高性能自适应扰动观察 MPPT 技术。*IEEE Transactions on power electronics*，26(4)，pp.1010–1021。

*   Ahmad, R.、Murtaza, A.F. 和 Sher, H.A.，2019。太阳能应用中光伏阵列高效运行的功率跟踪技术——综述。*Renewable and Sustainable Energy Reviews*：*101*，pp.82–102。

*   Bansal, S.、Mago, J.、Gupta, D. 和 Jain, V.，2021。采用田口法对镍基+10WC 微波处理复合熔敷层的空化侵蚀行为进行参数优化与分析。*Surface Topography: Metrology and Properties*，9(1)，p.015011。

*   Bounechba, H.、Bouzid, A.、Nabti, K. 和 Benalla, H.，2014。光伏系统最大功率点跟踪器中扰动观察法与模糊逻辑的对比。*Energy Procedia*：*50*，pp.677–684。

*   Boukenoui, R.、Bradai, R.、Mellit, A.、Ghanes, M. 和 Salhi, H.，2015 年 11 月。面向微网独立光伏系统的 P&O、改进爬山法-FLC 和自适应 P&O-FLC MPPT 的比较分析。载于 *2015 International Conference on Renewable Energy Research and Applications (ICRERA)* (pp. 1095–1099)。IEEE。

*   De Brito, M.A.G.、Galotto, L.、Sampaio, L.P.、e Melo, G.D.A. 和 Canesin, C.A.，2012。光伏应用主要 MPPT 技术的评估。*IEEE Transactions on Industrial Electronics*：*60*(3)，pp.1156–1167。

*   Farayola, A.M.、Hasan, A.N. 和 Ali, A.，2018。采用粗糙高斯支持向量机和人工神经网络技术的高效光伏 MPPT 系统。*International Journal of Innovative Computing Information and Control (IJICIC)*：*14*(1)，pp.323–329。

*   Gil-Antonio, L.、Saldivar-Marquez, M.B. 和 Portillo-Rodriguez, O.，2016 年 6 月。光伏系统中的最大功率点跟踪技术：简要综述。载于 *2016 13th International Conference on Power Electronics (CIEP)* (pp. 317–322)。IEEE。

*   Gupta, A.、Chanana, S. 和 Thakur, T.，2014。采用最大功率点跟踪控制的无变压器光伏并网系统的电能质量改善。*International Journal of Sustainable Energy*：*33*(4)，pp.921–936。

*   Gupta, A.K. 和 Saxena, R.，2016 年 2 月。光伏应用中广泛使用的 MPPT 技术综述。载于 *2016 International Conference on Innovation and Challenges in Cyber Security (ICICCS-INBUSH)* (pp. 270–273)。IEEE。

*   Jaen, C.、Moyano, C.、Santacruz, X.、Pou, J. 和 Arias, A.，2008 年 9 月。光伏系统中使用的最大功率点跟踪控制技术概述。载于 *2008 15th IEEE International Conference on Electronics, Circuits and Systems* (pp. 1099–1102)。IEEE。

*   Karami, N.、Moubayed, N. 和 Outbib, R.，2017。不同 MPPT 技术的总体综述与分类。*Renewable and Sustainable Energy Reviews*：*68*，pp.1–18。

*   Khan, M.，2019。面向燃料电池系统的基于人工智能的最大功率点跟踪控制器 [J]。*European journal of electrical engineering*，21(3)，pp.297–302。

*   Khan, M.J.，2020。混合可再生能源系统优化技术近期趋势综述。*Archives of Computational Methods in Engineering*，pp.1–11。

*   Khan, M.J. 和 Mathew, L.，2020。可再生能源系统优化技术的比较研究。*Archives of Computational Methods in Engineering*：*27*(2)，pp.351–360。

*   Khan, M.J. 和 Mathew, L.，2017 年 10 月。面向变化环境条件下光伏系统的基于人工智能的最大功率点跟踪算法。载于 *2017 Recent Developments in Control, Automation & Power Engineering (RDCAPE)* (pp. 114–119)。IEEE。

*   Kumar, R.、Choudhary, A.、Koundal, G. 和 Yadav, A.S.A.，2017a。基于 Matlab 的光伏系统 MPPT 技术建模/仿真。*International Journal*：*7*(4)，178–187。

*   Kumar, R.、Choudhary, A. 和 Shimi, S.L.，2017b 年 8 月。基于 Buck-Boost 功率变换器的直流分流电机平滑启动器。载于 *2017 International Conference on Innovations in Control, Communication and Information Systems (ICICCI)* (pp. 1–8)。IEEE。

*   Masoum, M.A.、Dehbonei, H. 和 Fuchs, E.F.，2002。基于电压和电流最大功率点跟踪的光伏系统理论与实验分析。*IEEE Transactions on Energy Conversion*：*17*(4)，pp.514–522。

*   Palariya, A.A.K.、Choudhary, A. 和 Yadav, A.，2016。基于 Matlab/Simulink 的风能转换 MPPT 建模、控制与仿真。*Eng. J. Appl. Scopes*：*1*(2)，pp.9–13。

*   Rai, A.、Awasthi, B.、Singh, S. 和 Dwivedi, C.K.，2016。光伏系统最大功率点跟踪技术综述。*Int. J. Eng. Res*：*5*，pp.539–545。

*   Roshan, R.、Yadav, Y.、Umashankar, S.、Vijayakumar, D. 和 Kothari, D.P.，2013 年 4 月。基于 CUK 变换器的电导增量 MPPT 算法太阳能光伏系统建模与仿真。载于 *2013 International Conference on Energy Efficient Technologies for Sustainability* (pp. 584–589)。IEEE。

*   Saravanan, S. 和 Babu, N.R.，2016。光伏系统最大功率点跟踪算法——综述。*Renewable and Sustainable Energy Reviews*：*57*，pp.192–204。

# 11 采用遗传算法优化的深度回声状态网络预测能源消耗

V. Dinesh Reddy、Kurinchi Nilavan、G.R. Gangadharan 和 Ugo Fiore

DOI：[10.1201/9781003153405-11](https://doi.org/10.1201/9781003153405-11)

## 目录

*   11.1 简介
*   11.2 相关工作
*   11.3 采用遗传算法优化的深度回声状态网络
*   11.4 数据集描述与预处理
*   11.5 数据中心功耗数据集实验分析
*   11.6 单户家庭功耗数据集实验分析
*   11.7 性能评估
*   11.8 结论
*   参考文献

## 11.1 简介

住宅和商业建筑部门占能源消耗的大头，比例为 28%，2019 年约为 21 千万亿英热单位（根据美国能源信息管理局数据）。显然，鉴于技术发展，住宅能源消耗预计将在未来增长（Guneralp et al. 2017）。随着云计算、物联网技术和社交媒体应用的普及，数据中心在商业计算中发挥着重要作用（Reddy et al. 2018; Reddy et al. 2020）。信息通信技术领域的全球温室气体排放量约为 0.86 公吨碳排放量（指 0.86 亿吨），占全球 CO[2] 排放量的 2%（Malmodin et al. 2018）。

住宅能源消耗在很大程度上是一个未明确定义的能源汇，也是一个复杂的问题（Amber et al. 2018）。它与房屋大小、几何结构、住户行为、室内能源系统以及燃料价格和通货膨胀等宏观经济因素高度相关。在当今快速增长的数字经济中，消费者对更多数据和高带宽内容的需求正在推动数据中心业务的激增。由于经济、社会和环境问题，数据中心的高能耗正引起越来越多的关注。我们需要开发主动的方法来识别并阻止这些无声威胁的增长。这将减少能源支出并降低数据中心的低效率。

机器学习涉及构建模型或在以往系统行为示例中寻找趋势，且尽可能减少专家干预。在数据中心缺乏应用/系统级度量措施的情况下，我们可以使用各种机器学习方法来建模缺失信息（Lee et al. 2014; Hazelwood et al. 2018）。在工业和住宅建筑的能源使用建模方面，存在探索先进机器学习技术的机会。相关模型需要具备管理高维数据的能力、敏捷性和高预测准确性。深度学习是机器学习的一个新兴领域，它从多层表征中学习（Lecun et al. 2015; Schmidhuber 2015）。深度学习方法通过更深层的耦合层堆栈，利用多层抽象来检测所需的表征。

深度学习通过发现复杂结构，在高维数据处理方面取得了重大进展。它在信号处理、自然语言理解等许多领域解决复杂问题方面显示出极具前景的结果。本章介绍了一种用于预测能源消耗的、经遗传算法优化的改进深度回声状态网络（`GA-DeepESN`）。

## 11.2 相关工作

Gassar 等人（2019）利用多层人工神经网络、随机决策森林、梯度提升机和多元回归算法，为伦敦住宅建筑的电力和燃气使用量预测开发了数据驱动模型。研究表明，房屋特征、住户数量和家庭收入是能源和燃气消耗迄今为止最显著的预测因子。Kialashaki 等人（2013）利用多元回归和人工神经网络，为住宅部门提出了两种能源需求预测模型。条件需求分析（`CDA`）被用于（Aydinalp-Koksal and Ugursal 2008）以估算全国住宅能源使用水平。他们报告称，与 `CDA` 模型相比，神经网络模型最适合计算社会经济变量的影响。

Wong 等人（2010）提出了一种神经网络模型，考虑天气和建筑特征来预测办公楼的日用电量。该模型具有一个隐藏层，其均方根误差在 3% 到 5.6% 之间变化。Ekici 等人（2009）提出了一种利用人工神经网络基于多种因素（如绝缘层厚度、朝向和透明度比）分析建筑能源需求的方法。此外，他们还针对有无绝缘层的一维瞬态传导砖墙试验了有限差分法。Yu 等人（2010）提出了一种利用决策树方法预测和分类建筑能源使用强度（`EUI`）水平的模型。结果表明，该模型能够识别影响建筑 `EUI` 的重要因素，并准确分类 `EUI` 水平（准确率高达 93%）。然而，作者未提供关于建模建筑能源需求的见解。

Liu 等人（2019）详细讨论了 `ANN` 和支持向量机（`SVM`）模型，并展示了它们的结构和准确性对比。此外，他们提出了一种混合机器学习方法来估算建筑能源消耗。Jahani 等人（2020）采用基于遗传算法的数值矩匹配方法，估算大量独栋住宅数据集的用电量。Zhao 等人（2010）提出了一种带有高斯核的 `SVM` 方法的并行实现，以预测多栋建筑的能源消耗。Nishi 等人（2017）提出了一种监督机器学习方法，基于现代数据中心的功率变化趋势模型，按分钟粒度对数据进行聚类。Versick 等人（2013）描述了一种新颖的方法，依靠各种执行环境中软件生成的工作负载来估算计算机系统的能源使用量。他们为虚拟机开发了一种功率测量模型，该模型可自适应底层硬件以产生准确结果。

基于文献综述，我们观察到统计模型和正向工程模型需要固定的假设和算法近似。带有反向传播的神经网络及其变体并不总能找到最优解。回归模型试图根据多个自变量预测结果。然而，如果自变量不正确，模型的预测准确性就会降低。此外，逻辑回归要求每个数据点独立于其他数据点。如果观测值相互关联，模型会显得过分强调这些观测值的重要性。

## 11.3 经遗传算法优化的深度回声状态网络

在本节中，我们描述了我们提出的深度学习方法：一种用于预测能源消耗的经遗传算法优化的深度回声状态网络（`GA – DeepESN`）。`DeepESN` 结合了 `ESN` 的非线性时间序列建模能力和深度学习的高效学习能力（Gallicchio et al. 2017; Hu et al. 2020）。`DeepESN` 由一个输入层、若干堆叠的储备层和一个输出层组成。`DeepESN` 的超参数主要包括输入单元数 `k`、谱半径 `*ρ*` 和每个储备层的连接率 `*α*`，这与基本 `ESN` 类似。在本章中，为了获得优化的超参数，我们使用了遗传算法（`GA`）。

### 用于时间序列预测的 GA-DeepESN 模型
