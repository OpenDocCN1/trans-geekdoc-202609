
图9. 针对1分钟提前预测时域，测试集的预测与实际序列在整个检查时间段（a）、0至10,000 s之间（b）、20,000至30,000 s之间（c）以及40,000至50,000 s之间（d）。

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_28_2.png)

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_28_3.png)

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_28_4.png)

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_28_5.png)

图10. 针对10分钟提前预测时域，测试集的预测与实际序列在整个检查时间段（a）、0至1000 s之间（b）、2000至3000 s之间（c）以及4000至5000 s之间（d）。

### 3.2. 与其他预测模型的比较

为了全面评估拟议模型，与以下模型进行了比较；数据处理群方法神经网络（`GMDHNN`）[27]、回归神经网络（`GRNN`）[28]、回归树（`RTs`）[29]、相关向量机（`RVM`）[30]和支持向量回归（`SVR`）[31]。表3和表4分别给出了1分钟提前预测的误差指标上`GMDHNN`、`GRNN`和`RTs`、`RVM`和`SVR`的得分。相应地，表5和表6分别给出了10分钟提前预测的误差指标`MAE`、`RMSE`和`MARNE`上`GMDHNN`、`GRNN`和`RTs`、`RVM`和`SVR`的得分。在这些模型中，`SVR`和`GMDHNN`显示出与混合模型相当的结果。后者优于所有其他模型。可以注意到`GRNN`和`RTs`导致较高的误差，因此对于所研究的问题不推荐。

表3. 针对1分钟提前时域的群方法数据处理（`GMDH`）、回归神经网络（`GRNN`）和回归树（`RTs`）评估。

|  | `MAE` |  |  | `RMSE` |  |  | `MARNE (%)` |  |  |
|---|---|---|---|---|---|---|---|---|---|
|  | `GMDHNN` | `GRNN` | `RTs` | `GMDHNN` | `GRNN` | `RTs` | `GMDHNN` | `GRNN` | `RTs` |
| Case#1 | 0.3688 | 0.3846 | 0.4432 | 0.5689 | 0.5721 | 0.6331 | 2.3411 | 2.3869 | 3.1256 |
| Case#2 | 0.3701 | 0.3910 | 0.4509 | 0.7051 | 0.7644 | 0.8109 | 2.4578 | 2.4771 | 3.2672 |
| Case#3 | 0.3698 | 0.4256 | 0.4781 | 0.7189 | 0.7367 | 0.7992 | 2.5871 | 2.6225 | 3.4155 |
| Case#4 | 0.3944 | 0.4201 | 0.4541 | 0.8902 | 0.9012 | 1.1091 | 2.7112 | 2.9904 | 3.6203 |
| Case#5 | 0.1094 | 0.1388 | 0.1692 | 0.1481 | 0.1556 | 0.2012 | 0.6289 | 0.6552 | 0.7154 |

表4. 针对1分钟提前时域的相关向量机（`RVM`）和支持向量回归（`SVR`）评估。

|  | `MAE` |  | `RMSE` |  | `MARNE (%)` |  |
|---|---|---|---|---|---|---|
|  | `RVM` | `SVR` | `RVM` | `SVR` | `RVM` | `SVR` |
| Case#1 | 0.3721 | 0.3704 | 0.5614 | 0.5377 | 2.3482 | 2.3345 |
| Case#2 | 0.3933 | 0.3865 | 0.7597 | 0.7029 | 2.4754 | 2.3419 |
| Case#3 | 0.3885 | 0.3893 | 0.7408 | 0.6911 | 2.6172 | 2.5678 |
| Case#4 | 0.3821 | 0.3783 | 0.8928 | 0.8709 | 2.9232 | 2.6213 |
| Case#5 | 0.1277 | 0.1178 | 0.1542 | 0.1421 | 0.6524 | 0.5772 |

表5. 针对10分钟提前时域的`GMDH`、`GRNN`和`RTs`评估。

|  | `MAE` |  |  | `RMSE` |  |  | `MARNE (%)` |  |  |
|---|---|---|---|---|---|---|---|---|---|
|  | `GMDHNN` | `GRNN` | `RTs` | `GMDHNN` | `GRNN` | `RTs` | `GMDHNN` | `GRNN` | `RTs` |
| Case#1 | 0.4292 | 0.4525 | 0.5898 | 0.6258 | 0.6553 | 0.8093 | 4.2051 | 4.4326 | 5.7812 |
| Case#2 | 0.4302 | 0.5597 | 0.5901 | 0.6272 | 0.6715 | 0.8095 | 4.2149 | 4.5031 | 5.7812 |
| Case#3 | 0.4704 | 0.6927 | 0.6157 | 0.6862 | 0.7342 | 0.8461 | 4.6334 | 4.7862 | 6.0319 |
| Case#4 | 0.4601 | 0.6056 | 0.6108 | 0.6715 | 0.6989 | 0.8012 | 4.5130 | 4.6902 | 5.7568 |
| Case#5 | 0.1238 | 0.1624 | 0.1799 | 0.1601 | 0.1833 | 0.2109 | 1.2671 | 1.4884 | 1.6117 |

表6. 针对10分钟提前时域的`RVM`和`SVR`评估。

|  | `MAE` |  | `RMSE` |  | `MARNE (%)` |  |
|---|---|---|---|---|---|---|
|  | `RVM` | `SVR` | `RVM` | `SVR` | `RVM` | `SVR` |
| Case#1 | 0.4342 | 0.4298 | 0.6359 | 0.6268 | 4.2541 | 4.2206 |
| Case#2 | 0.4351 | 0.4307 | 0.6440 | 0.6268 | 4.2630 | 4.2198 |
| Case#3 | 0.5370 | 0.4681 | 0.8649 | 0.7529 | 5.2605 | 4.5365 |
| Case#4 | 0.4988 | 0.4644 | 0.7898 | 0.7459 | 5.1133 | 4.5301 |
| Case#5 | 0.1424 | 0.1308 | 0.2037 | 0.1654 | 1.5893 | 1.1276 |

## 4. 讨论与结论性意见

海上风力涡轮机安装持续引起研究兴趣，因为它们被认为是覆盖各种孤立负荷电力需求的有效机制。本研究强调在风速序列不呈现时间一致性、即数据序列中存在中断的限制下，开发一种有效的超短期风速预测方法。使用了实际测量数据来训练所开发的方法。开发、测试并应用了一种集成数据驱动的短期风速预测模型。“集成”指的是并行运行两个不同预测器的组合，预测由导致最低误差的预测器获得。拟议模型利用小波变换，并与相关文献中提出的其他模型进行比较。本研究的主要结论：

- 拟议的预测模型可有效用于1分钟和10分钟提前时域的风速预测。
- 外生变量（即风向和气温）降低了预测精度。最佳结果是使用`DWT`获得的。
- 最高误差出现在冬季日，尤其是在风速较高的情况下。
- 预测误差与风向之间没有相关性。
- 混合模型（`FFNN`和`ANFIS`的组合）在所有检查的数据集案例中都导致更好的预测。
- 拟议模型优于相关文献中提出的其他预测模型的准确性。

本论文的研究将进一步扩展，通过检查在风电场布局优化（`WLFO`）问题中结合尾流效应实施预测问题，使用特定的数学或数值模型。预测风速时间序列可以用作该问题的输入。通过估计未来风速值，`WLFO`可以修改为情景化问题，其中不同的风速预测可导致不同的`WLFO`解决方案，从而评估未来风速变化对优化问题输出的影响程度。

作者贡献：`I.P.P.`执行了研究并撰写了论文初稿。`C.M.`和`D.C.A.`设定了研究目标，为研究提供指导并修改了论文。

资助：本研究未获得外部资助。

利益冲突：作者声明无利益冲突。

## 参考文献

1. WindEurope. 欧洲海上风电关键趋势与统计 2018。可在线获取：https://windeurope.org/wp-content/uploads/files/about-wind/statistics/WindEurope-Annual-Offshore-Statistics-2018.pdf（访问于2019年3月27日）。
2. Snyder, B.; Kaiser, M.J. 欧洲和美国海上风电发展的比较：发展模式与驱动因素。Appl. Energy 2009, 86, 1845–1856. [CrossRef]
3. Soman, S.S.; Zareipour, H.; Malik, O.; Mandal, P. 不同时间范围的风电和风速预测方法的综述。In Proceedings of the 2010 North American Power Symposium, Arlington, TX, USA, 26–28 September 2010; pp. 1–8.
4. Jung, J.; Broadwater, R.P. 风速和功率预测的现状与未来进展。Renew. Sustain. Energy Rev. 2014, 31, 762–777. [CrossRef]
5. Okumus, I.; Dinler, A. 风能预测的现状及一种用于小时预测的混合方法。Energy Convers. Manag. 2016, 123, 362–371. [CrossRef]
6. Lei, M.; Shiyan, L.; Chuanwen, J.; Hongling, L.; Ya, Z. 风速和发电功率预测综述。Renew. Sustain. Energy Rev. 2009, 13, 915–920. [CrossRef]
7. Chang, W.Y. 风力预测方法文献综述。J. Power Energy Eng. 2014, 2, 161–168. [CrossRef]
8. Foley, A.M.; Leahy, P.G.; Marvuglia, A.; McKeogh, E.J. 风电预测的当前方法与进展。Renew. Energy 2012, 37, 1–8. [CrossRef]
9. Bhaskar, M.; Jain, A.; Srinath, N.V. 风速预测：现状。In Proceedings of the 2010 International Conference on Power System Technology, Hangzhou, China, 24–28 October 2010; pp. 1–7.
10. Murthal, D. 风电预测：综述。Int. J. Eng. Res. Gen. Sci. 2016, 4, 802–806.
11. Tascikaraoglu, A.; Uzunoglu, M. 短期风速和功率预测的组合方法综述。Renew. Sustain. Energy Rev. 2014, 34, 234–254. [CrossRef]
12. Sfetsos, A. 用于平均小时风速时间序列预测的一种新方法。Renew. Energy 2002, 27, 163–174. [CrossRef]
13. Başaran, Ü.; Filik, T. 基于埃斯基谢希尔多地测量的人工神经网络风速预测。Energy Procedia 2017, 107, 264–269.
14. More, A.; Deo, M.C. 用神经网络预测风。Mar. Struct. 2003, 16, 35–49. [CrossRef]
15. Li, G.; Shi, J. 关于三种人工神经网络在风速预测中的比较。Appl. Energy 2010, 87, 2313–2320. [CrossRef]
16. Zeng, J.W.; Qiao, W. 基于支持向量机的短期风电功率预测。In Proceedings of the 2011 IEEE/PES Power Systems Conference and Exposition, Phoenix, AZ, USA, 20–23 March 2011; pp. 1–8.
17. Zhou, J.Y.; Shi, J.; Li, G. 短期风速预测的支持向量机微调。Energy Convers. Manag. 2011, 52, 1990–1998. [CrossRef]
18. Fazelpour, F.; Tarashkar, N.; Rosen, M.A. 使用人工神经网络对德黑兰进行短期风速预测。Iran. Int. J. Energy Environ. Eng. 2016, 7, 377–390. [CrossRef]
19. Fortuna, L.; Guariso, G.; Nunnari, S. 统计模型对风速等级的提前一天预测。Int. J. Renew. Energy Res. 2016, 6, 1137–1145.
20. Fortuna, L.; Nunnari, S.; Guariso, G. 风速时间序列中的分形阶证据。In Proceedings of the 2014 International Conference on Fractional Differentiation and Its Applications, Catania, Italy, 23–25 June 2014; pp. 1–6.
21. Mallat, S. 多分辨率信号分解理论——小波表示。IEEE Trans. Pattern Anal. Mach. Intell. 1989, 11, 674–693. [CrossRef]
22. Amjady, N.; Keynia, F. 小波变换与神经进化算法结合的电力系统短期负荷预测。Energy 2009, 34, 46–57. [CrossRef]
23. Jang, J.S.R. `ANFIS`：基于自适应网络的模糊推理系统。IEEE Trans. Syst. Man Cybern. 1993, 23, 665–685. [CrossRef]
24. Graupe, P. 人工神经网络原理，第二版；World Scientific: Singapore, 2007.
25. Levenberg, K. 最小二乘法中某些非线性问题求解的一种方法。Q. J. Appl. Math. 1944, 2, 164–168. [CrossRef]
26. Michalides, C.; Loukogeorgaki, E.; Angelides, D.C. 监测连接系泊浮体模块的响应。In Proceedings of the 27th International Offshore and Polar Engineering, Anchorage, AK, USA, 30 June–5 July 2013; pp. 869–876, ISBN 978-1-880653-99-9.
27. Abdel-Aal, R.E.; Elhadidy, M.A.; Shaahid, S.M. 使用基于`GMDH`的溯因网络对平均小时风速时间序列进行建模和预测。Renew. Energy 2009, 34, 1686–1699. [CrossRef]
28. Kumar, G.; Malik, H. 基于广义回归神经网络的印度西部地区风速预测模型。Procedia Comput. Sci. 2016, 93, 26–32. [CrossRef]
29. Troncoso, A.; Salcedo-Sanz, S.; Casanova-Mateo, C.; Riquelme, J.C.; Prieto, L. 基于局部模型的回归树用于超短期风速预测。Renew. Energy 2015, 81, 589–598. [CrossRef]
30. Sun, G.; Chen, Y.; Wei, Z.; Li, X.; Cheung, K.W. 使用相关向量机进行日前风速预测。J. Appl. Math. 2014, 2014, 1–6. [CrossRef]
31. Botha, N.; van der Walt, C.M. 使用支持向量回归和特征选择进行风速预测。In Proceedings of the 2017 Pattern Recognition Association of South Africa and Robotics and Mechatronics, Bloemfontein, South Africa, 29 November–1 December 2017; pp. 181–186.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_31_0.png)

© 2019 作者保留。许可方 MDPI，瑞士巴塞尔。本文是一篇开放获取文章，根据知识共享署名（CC BY）许可的条款和条件分发（http://creativecommons.org/licenses/by/4.0/）。

# 多元时间卷积网络：多元时间序列预测的深度神经网络方法

Renzhuo Wan 1, Shuping Mei 1, Jun Wang 1, Min Liu 2 and Fan Yang 1,*

1 纳米光学材料与存储器件研究中心，武汉纺织大学电子电气工程学院，武汉 430200，中国

2 粉末冶金国家重点实验室，中南大学物理与电子学院，长沙 410083，中国

* 通讯作者：yangfan@wtu.edu.cn

收稿：7 July 2019；接受：5 August 2019；发表：7 August 2019
