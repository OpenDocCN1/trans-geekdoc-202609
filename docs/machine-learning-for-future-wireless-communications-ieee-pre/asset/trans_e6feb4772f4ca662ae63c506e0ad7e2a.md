
26. Benjamin Sliwa, Daniel Behnke, Christoph Ide, and Christian Wietfeld. B.A.T.Mobile: 利用移动控制知识实现移动机器人网络高效路由。In *IEEE GLOBECOM 2016 无线网络、控制与无人自主车辆定位研讨会（Wi‐UAV）*，Washington D.C., USA, 2016年12月。

27. Benjamin Sliwa, Thomas Liebig, Robert Falkenberg, Johannes Pillmann, and Christian Wietfeld. 基于机器学习的上下文预测车对云通信，使用多层连接图用于即将到来的5G网络。In *2018 IEEE 第88届车辆技术会议（VTC‐Fall）*，Chicago, USA, 2018年8月a。

28. Benjamin Sliwa, Thomas Liebig, Robert Falkenberg, Johannes Pillmann, and Christian Wietfeld. 利用多指标上下文感知实现高效机器类型通信，用于作为移动传感器的汽车在即将到来的5G网络中。In *2018 IEEE 第87届车辆技术会议（VTC‐Spring）*，Porto, Portugal, 2018年6月b。最佳学生论文奖。

29. Benjamin Sliwa, Thomas Liebig, Robert Falkenberg, Johannes Pillmann, and Christian Wietfeld. 利用上下文感知通信实现车载传感器数据资源高效传输。In *第19届IEEE国际移动数据管理会议（MDM）*，Aalborg, Denmark, 2018年6月c。

30. Benjamin Sliwa, Johannes Pillmann, Maximilian Klaß, and Christian Wietfeld. 利用地图拓扑知识进行上下文预测多接口车对云通信。In *2018 IEEE 第88届车辆技术会议（VTC‐Fall）*，Chicago, USA, 2018年8月d。

31. Chaoming Song, Zehui Qu, Nicholas Blumm, and Albert‐László Barabási. 人类移动性可预测性的极限。Science, 327 (5968): 1018–1021, 2010. ISSN 0036‐8075. doi: 10.1126/science.1177170。

32. W. Vandenberghe, E. Vanhauwaert, S. Verbrugge, I. Moerman, and P. Demeester. 利用浮动车数据技术扩展交通监控系统的可行性。IET Intelligent Transport Systems, 6 (4): 347–354, 2012年12月。ISSN 1751‐956X. doi: 10.1049/iet‐its.2011.0221。

33. S. Wang, S. Kodagoda, L. Shi, and H. Wang. 陆地车辆道路地形分类：采用基于加速度的方法。IEEE Vehicular Technology Magazine, 12 (3): 34–41, 2017年9月。ISSN 1556‐6072. doi: 10.1109/MVT.2017.2656949。

34. X. Wang, X. Zheng, Q. Zhang, T. Wang, and D. Shen. 智能交通系统中的众包：工作现状与网络。IEEE Transactions on Intelligent Transportation Systems, 17 (6): 1596–1605, 2016年6月。ISSN 1524‐9050. doi: 10.1109/TITS.2015.2513086。

35. Christian Wietfeld, Christoph Ide, and Björn Dusza. 用于移动众包感知的资源高效无线通信。In *第51届ACM/EDAC/IEEE设计自动化会议（DAC）*，San Francisco, USA, 2014年6月。IEEE。

36. A. Zanella, N. Bui, A. Castellani, L. Vangelista, and M. Zorzi. 物联网在智慧城市中的应用。IEEE Internet of Things Journal, 1 (1): 22–32, 2014年2月。ISSN 2327‐4662. doi: 10.1109/JIOT.2014.2306328。

37. K. Zheng, Q. Zheng, P. Chatzimisios, W. Xiang, and Y. Zhou. 异构车联网：架构、挑战与解决方案综述。IEEE Communications Surveys Tutorials, 17 (4): 2377–2396, 2015年第四季度。ISSN 1553‐877X. doi: 10.1109/COMST.2015.2440103。

# 第二部分
## 传输智能与自适应基带处理

### 9 基于机器学习的自适应调制与编码设计
*Lin Zhang¹, and Zhiqiang Wu²*
¹*电子与信息技术学院，中山大学，广州，中国*
²*电气工程系，赖特州立大学，代顿，俄亥俄州，美国*

#### 9.1 引言与动机
自适应调制与编码（AMC）技术已广泛应用于有线和无线通信系统中，以适应信道条件的变化。AMC 方案可通过根据实时信道条件调整调制阶数和/或编码速率，帮助通信系统实现更高的频谱效率以及数据速率与可靠性之间的更好权衡。由于无线信道通常比有线信道变化更剧烈，大多数无线通信标准，如 Wi-Fi 标准 IEEE 802.11n 和 IEEE 802.11ac，建议采用 AMC 以提高频谱效率，从而满足用户需求。为了进一步提高频谱效率和可靠性，AMC 方案已与多输入多输出（MIMO）和正交频分复用（OFDM）相结合。由于可靠性增强，这些借助 AMC 的系统可在满足上层实时传输需求的同时降低开销和时延。

然而，由于无线信道的复杂运行场景和时变特性，在诸如基于 IEEE 802.11n 的无线网络等无线通信系统中，物理层配置/链路自适应在实践中难以实现。因此，最优的物理层配置在实践中很少实现（Iera et al., [2005](#c09.xhtml#c09-bib-0008)；Daniels et al., [2010](#c09.xhtml#c09-bib-0007)），导致 AMC 方案无法很好地适应信道状态，从而产生性能下降。

此外，当 AMC 方案与 MIMO 和 OFDM 相结合时，由于以下问题，对 OFDM 调制、卷积编码和 MIMO 处理的联合效应建模极具挑战性。首先，在实际系统中存在各种不完善因素，例如功率放大器的非线性失真、模数转换器（ADC）的量化误差以及非高斯加性噪声。在这种情况下，对完整电信系统的精确建模是困难的。其次，在通信系统设计中，通常将信号处理划分为多个独立模块，每个模块执行特定且孤立的功能。因此，联合优化这些组件会导致计算复杂性较高的系统（OShea and Hoydis, [2017](#c09.xhtml#c09-bib-0019)）。由于上述原因，现有的 AMC 实现要么因基于模型的近似而不够准确，要么因大尺寸查找表而繁琐（Peng et al., [2007](#c09.xhtml#c09-bib-0021)；Jensen et al., [2010](#c09.xhtml#c09-bib-0009)）。因此，为了节省计算开销并避免做出不切实际的近似，例如对非高斯分布的高斯近似，需要一种简洁的方法，使 AMC 方案能够使用假设尽可能少的数学模型运行。

另一方面，机器学习（ML），即“使用示例数据对性能标准进行优化的计算机编程”（Alpaydin, [2009](#c09.xhtml#c09-bib-0003)），具有利用统一非线性框架联合优化刚性模块化模块的潜力。因此，它可作为在无线信道上通信时具有特定硬件配置的借助 AMC 的无线系统的优化的良好候选方案。

基于这些考虑，本章将机器学习技术应用于借助 AMC 的无线系统，使其能够适应信道的波动。我们介绍并分析了 MIMO 和 OFDM 场景下两种类型的机器学习辅助 AMC 方案，其中通过调整调制阶数和编码速率来满足高数据速率和高可靠性之间的冲突需求。具体而言，考虑了监督学习方法和强化学习方法。

在此，我们首先概述机器学习辅助 AMC。

##### 9.1.1 机器学习辅助 AMC 概述
