

# 156 深度学习硬件架构

用于医疗设备中低功耗心电图（ECG）监测的输入触发计算复用技术 [15]。

综合结果显示，CORN 使基准架构的面积增加了 13%。可编程交叉条矩阵和存储计算复用信息的表是这些面积开销的主要来源。这些组件也带来了一些功耗开销，但远小于通过计算复用带来的功耗降低。例如，在准确率下降 1% 的数据分析基准测试中，CORN 将控制单元和内部连接的功耗增加了 0.29 mW（从基准的 0.10 mW 增加到 0.39 mW），这远小于乘法操作节省的 0.83 mW（从基准的 1.69 mW 减少到 CORN 的 0.87 mW）。

# 7.5 结论与展望

功耗一直是神经网络的一个重要关注问题。特别是实现新型机器学习技术的大网络比以前需要更多的计算和功耗。在本章中，我们展示了计算复用可以利用神经网络算术运算中的固有冗余来节省功耗。实验结果表明，所提出的计算复用设计可以集成到现有的 LSTM [16]、脉冲神经网络 [17] 和卷积神经网络模型中以进一步降低功耗。计算复用还可以消除高达 90% 的无效计算。其次，可以将计算复用与开发神经网络的映射 [18, 19] 和调度 [20] 方法相结合，以提升性能。评估 CORN 对可靠性 [22] 的影响以及定制基于 FPGA 的神经网络实现 [23] 是该领域的其他未来工作。

# 参考文献

- [1] A. Yazdansh, J. Park, H. Sharma, 等，“GPU 神经网络加速，”发表于 MICRO, pp. 482–493, 2015.
- [2] Y. Chen, J. Emer, V. Sze, 等，“Eyer: 用于卷积神经网络的高效数据流，”发表于 ISSCC, pp. 262–263, 2016.
- [3] T. Chen, Z. Du, N. Sun, 等，“Dian: 用于无处不在学习的小型高吞吐量加速器，”发表于 ASPLOS, pp. 269–284, 2014.
- [4] S. Sarwar, S. Venkataramani, A. Raghunathan, 等，“无乘法器神经元探索能效型计算，”发表于 DATE, pp. 145–150, 2016.
- [5] B. Reagen, P. Watmough, R. Adolf, 等，“Minerva: 低功耗高精度深度神经网络加速器，”发表于 ISCA, 2016.
- [6] Q. Zhang, T. Wang, Y. Tian, 等，“ApproxANN: 用于神经网络的近似计算框架，”发表于 DATE, pp. 701–706, 2015.
- [7] S. Venkataramani, A. Ranjan, K. Roy, 等，“AxNN: 通过近似计算的高效神经形态系统，”发表于 ISLPED, pp. 27–32, 2014.
- [8] A. Yasoubi, R. Hobaj, M. Modarresi, 等，“使用计算复用的神经网络高效加速器设计，”发表于 Computer Architecture Letters, 2016.
- [9] M. Modarresi, H. Nikounia, A. Jahangir, 等，“用于 DSP 应用的低功耗算术单元，”发表于 SoC, pp. 68–71, 2011.
- [10] K. Hegde, Y. J. Ru, Agrawal, 等，“UCNN: 通过权重重复利用深度神经网络中的计算复用，”发表于 ISCA, 2018.
- [11] Y. Lecun, L. Bottou, Y. Bengio, 等，“基于梯度的学习应用于文档识别，”发表于 IEEE, vol. 86, no. 11, pp. 2278, 1998.
- [12] M. Lichman，“机器学习库，”技术报告，加利福尼亚大学欧尔文分校，2013.
- [13] MIT 数据库，ecg.mit.edu, 2016.
- [14] D. Mackay，《信息理论、推理与算法》，英国：剑桥大学出版社，2003.
- [15] M. Modarresi 和 A. Yasoubi，“使用神经网络的低功耗 ECG图 分析，”发表于 Euromicro DSD, pp. 547–552, 2016.
- [16] Z. Que, T. Nugent, S. Liu, 等，“LSTM 的高效权重复用，”发表于 IEEE 第30届国际特定应用系统、架构和处理器会议 (ASAP), pp. 17–24, 2019.
- [17] H. Vu, A. Abdallah, 等，“低延迟神经形态系统，”发表于 Big Data and Smart Computing, 2019.
- [18] M. Hosseini, M. Resh, 等，“CNN 的能效映射，”发表于第13届 IEEE/ACM 网络上芯片研讨会, 2019.
- [19] Y. Meloni, G. Deriu, 等，“基于流的映射分布，”发表于第13届 IEEE/ACM 网络上芯片研讨会, 2019.
- [20] L. Wijen, S. Shabani, 等，“CNN 的自动调度，”发表于第19届嵌入式系统、建模与仿真国际会议, pp. 387–400, 2019.
- [21] M. Nikolic, M. Mahmoud, 等，“网络中无效计算表征，”发表于 Performance Analysis of Systems and Software, pp. 165–176, 2019.
- [22] I. Negaj, A. Alouani, 等，“CNN 的可靠性研究，”发表于第36届国际计算机设计会议, pp. 476–479, 2018.
- [23] Y. Shen, J. Ji, 等，“Argus: 一端到端的加速框架，”IEEE Micro, vol. 39, no. 5, pp. 17–25, 2019年9月–10月.
- [24] P. Capotondi, G. Deriu, 等，“在 Zynq SoC 上推理中利用 CPU-FPGA 协同效应，”ACM Transactions on Reconfigurable Technology and Systems, vol. 11, no. 3, pp. 1–23, 2018年12月.

