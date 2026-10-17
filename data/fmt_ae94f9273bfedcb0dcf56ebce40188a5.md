
表 10.1 中的云节点 in Table 10.1。因此，可以选择工作负载最小且电池电量较多的云节点来执行任务。云节点的状态根据平均工作负载标记为平衡、过载或欠载。如果工作负载大于平均工作负载与可容忍工作负载限制之和，则云节点的状态标记为过载。另一方面，如果工作负载介于平均工作负载与平均工作负载加可容忍工作负载限制之和之间，则认为该云节点处于平衡状态。标记完云节点的状态后，SGN 检查任务数量是否大于欠载云节点数量与平衡云节点数量之和，并将任务拆分为子任务。否则，任务不拆分为子任务。如果工作负载小于平均工作负载，则节点标记为欠载。SGN 仅将子任务分配给欠载和平衡的 MN。如果没有欠载和过载的 MN，SGN 会将剩余待执行任务的详细信息发送给其 I-MGS。能量约束分层任务调度 (ECHTS) 算法与 EDF 技术 13 进行了比较。根据以下指标评估算法的性能：

- **平均延迟**：测量每个客户端在获取请求服务时发生的平均延迟。
- **数据包投递率**：成功数据传输的节点数量之比。
- **能量消耗**：所有云网格节点消耗的平均能量。
- **吞吐量**：接收端获得的平均吞吐量。 [](#index_split_003.html#p211)

### 表 10.1 仿真参数

| 参数 | 值 |
| :--- | :--- |
| 网格节点数量 | 20 |
| 超级网格节点数量 | 10 |
| 区域大小 | 1000 × 1000 |
| Mac | 802.11 |
| 无线电范围 | 250 m |
| 仿真时间 | 50 sec |
| 服务发现协议 | SLP |
| 服务器应用 | SLPsa |
| 客户端应用 | SLPua |
| 速度 | 10 m/s |
| 客户端 | 4 |
| 请求负载 | 10 到 50 kb |
| 请求数量 | 1,2,3,4 和 5 |

#### 10.7.1 基于请求数量

请求数量从 1 变化到 5，负载为 10 kb。对于两个请求，将请求负载从 10 变化到 50 kb。

图 10.6 s 展示了 ECHTS 和 EDF 技术在不同速率场景下的延迟。我们可以得出结论，我们提出的 ECHTS 方法的延迟比 EDF 方法低 45%。

图 10.7 展示了 ECHTS 和 EDF 技术在不同速率场景下的投递率。我们可以得出结论，我们提出的 ECHTS 方法的投递率比 EDF 方法高 19%。

图 10.8 s 展示了 ECHTS 和 EDF 技术在不同速率场景下的吞吐量。我们可以得出结论，我们提出的 ECHTS 方法的吞吐量比 EDF 方法高 18%。

![Image 80](img/index-211_1.jpg)
![Image 81](img/index-211_2.jpg)
![Image 82](img/index-211_3.jpg)

**图 10.3** 请求 vs 延迟。
**图 10.4** 请求 vs 投递率。
**图 10.5** 请求 vs 吞吐量。

### 10.8 结论

在本章中，提出了一种用于云网格的强度受限分层任务调度算法，以降低小区节点的电力消耗。当小区节点移出传输范围时，任务将被重新调度。由于需要解决截止日期约束和设备异构性，调度至关重要。总体性能基于平均延迟（降低）、数据包投递率（提高）、公平性和带宽（略微提高）以及能量消耗（基于节点和流降低）进行估算。通过仿真，使用 NS-2 仿真器分析了性能指标。

![Image 83](img/index-212_1.jpg)
![Image 84](img/index-212_2.jpg)
![Image 85](img/index-212_3.jpg)

**图 10.6** 负载 vs 延迟。
**图 10.7** 负载 vs 投递率。
**图 10.8** 负载 vs 吞吐量。

### 参考文献

1. Rodriguez Juan Manuel, Alejandro Zunino, and Marcelo Campo “Cloud grid seas: simple energy-aware scheduler,” in Proceedings of the 3rd High-Performance Computing Symposium-39th JAIIO, 2010.
2. Ghosh, Preetam, Nirmalya Roy, Sajal K. Das, and Kalyan Basu “A game theory based pricing strategy for job allocation in cloud grids,” in Proceedings of the 18th International Parallel and Distributed Processing Symposium, p. 82. IEEE, 2004.
3. Li, Chunlin, and Layuan Li “Simultaneous optimization of application utility and consumed energy in cloud grid,” *Computing and Informatics*, 29.6 (2012): 1117–1140.
4. Ghosh, Preetam, et al. “A pricing strategy for job allocation in cloud grids using a non-cooperative bargaining theory framework,” *Journal of Parallel and Distributed Computing*, 65.11 (2005): 1366–1383.
5. Sim, Kwang Mong “A survey of bargaining models for grid resource allocation,” *ACM SIGecom Exchanges*, 5.5 (2006): 22–32.
6. Khan, Samee Ullah, and Cemal Ardil “Energy efficient resource allocation in distributed computing systems,” in International Conference on Distributed, High-Performance and Grid Computing, 2009.
7. Prosperi, Francesco, Mario Bambagini, Giorgio Buttazzo, Mauro Marinoni, and Gianluca Franchino. “Energy-aware algorithms for tasks and bandwidth co-allocation under real-time and redundancy constraints.” In Proceedings of 2012 IEEE 17th International Conference on Emerging Technologies & Factory Automation (ETFA 2012), pp. 1–8. IEEE, 2012.
8. Kim, Jong-Kook, Howard Jay Siegel, Anthony A. Maciejewski, and Rudolf Eigenmann. “Dynamic resource management in energy constrained heterogeneous computing systems using voltage scaling,” *IEEE Transactions on Parallel and Distributed Systems*, 19.11 (2008): 1445–1457.
9. Tekbiyik, Neyre, Tolga Girici, Elif Uysal-Biyikoglu, and Kemal Leblebicioglu. "Proportional fair resource allocation on an energy harvesting downlink-part II: algorithms,” arXiv preprint arXiv:1205.5153 (2012).
10. Malla, Samip, Birendra Ghimire, Mark C. Reed, and Harald Haas. “Energy efficient resource allocation in OFDMA networks using ant-colony optimization,” in International Symposium on Communications and Information Technologies (ISCIT), 2012, pp. 889–894, IEEE, 2012.
11. Li, Chunlin, and Layuan Li. “Energy constrained resource allocation optimization for cloud grids,” Elsevier, 2009.
12. Aziz, Abdul, and Hesham El-Rewini, *Power Efficient Scheduling Heuristics for Energy Conservation in Computational Grids*, Springer, 2011.
13. Doulamis, Nikolaos D., Anastasios D. Doulamis, Emmanouel A. Varvarigos, and Theodora A. Varvarigou. “Fair scheduling algorithms in grids,” *IEEE Transactions on Parallel and Distributed Systems*, 18.11 (2007): 1630–1648.
14. Singh Arjun, and Chakrabarti P. “Ant based resource discovery and mobility aware trust management for cloud grid systems,” in IACC IEEE 3rd International Conference, pp. 637–644, Feb 2013.

### 参考文献

[15.] Preetam Ghosh, and Sajal K. Das. “Mobility-aware cost-efficient job scheduling for single class grid jobs in a generic cloud grid architecture,” *Future Generation Computer Systems*, In Press, Corrected Proof, 2009.
[16.] Chunlin Li, and Layuan Li. “Energy constrained resource allocation optimization for cloud grids,” *Journal of Parallel and Distributed Computing* 70.3 (2010): 245–258.
[17.] W. X. Shen, C. C. Chan, E.W. C. Lo, and K. T. Chau. “Estimation of battery available capacity under variable discharge currents,” *Journal of Power Sources* 103.2 (2002): 180–187.
[18.] Ming-Chiao Chen, Jiann-Liang Chen, and Teng-Wen Chang. “Android/osgi-based vehicular network management system,” *Computer Communications*, In Press, Corrected Proof, 2010.
[19.] Ashish Agarwal, Douglas O. Norman, and Amar Gupta “Wireless grids: Approaches, architectures, and technical challenges,” *Working Chapters 4459–04*, Massachusetts Institute of Technology (MIT), Sloan School of Management, 2004.
[20.] 网络模拟器：`http://www.isi.edu/nsnam/ns`

![图片 86](img/index-215_1.jpg)

## 索引

**缩写**, 63
**BB–BC-cost**, 123
**准确**, 40, 64
**BC-cost**, 36
**参与者**, 78
**蜜蜂**, 37, 79, 105, 176, 177, 180
**采用**, 59
**生物地理优化 (BBO)**, 175, 176
**AI**, 146
**基于 AI**, 106
**Amazon**, 2, 4, 16, 34, 101
**分类**, 80, 103, 108
**分析**, 17, 56, 69, 92, 103, 105, 107
**客户端**, 2, 3, 5, 11, 34, 36, 38, 58, 79, 102, 111–114, 179–181, 104, 163, 195
**退火**, 121, 167–169, 179
**客户端/服务器**, 12
**蚂蚁**, 17, 34, 37, 59, 103, 139, 167, 170–172
**云微数据中心**, 121, 122, 129, 179, 188
**云**, 5, 75, 111, 112, 186, 187
**基于蚂蚁**, 188
**CloudSim**, 44, 129, 139, 140, 153, 156, 169, 173, 174, 177, 152, 153, 171
**蚁群优化 (ACO)**, 17, 139
**CloudStack**, 156
**架构**, 2, 7, 45, 56, 58, 59, 81, 91, 92, 96, 98, 106, 114, 138, 140, 141, 175, 189
**集群**, 149, 186
**聚类**, 60, 80
**系数**, 89
**人工神经网络 (ANN)**, 16, 20, 21, 24–26, 29, 30, 38–41, 45, 74, 80, 81, 91–93, 104, 107, 108, 124, 125, 127
**复杂性**, 13, 141
**核心**, 153, 188
**成本**, 5, 7, 8, 12, 16, 17, 19–23, 26, 34–44, 48–50, 56, 74, 77, 78, 96, 99–101, 104, 106, 107, 110, 113, 114, 122, 123, 127, 133, 140, 141, 146, 147, 155–156, 165, 168, 178–180, 187
**骨干**, 162
**后端**, 7
**背景**, 177

## 索引

## 反向传播

18–20, 38, 40, 104, 107

## 成本感知

34, 36, 38, 39, 45, 49
108, 124, 127, 142

## 基于成本

17

## 蝙蝠算法

92, 105, 109, 120, 123, 124, 126–129
133, 177, 178, 180

## COVID-19

30

## 蝙蝠算法-人工神经网络

120, 123, 127–130, 133
141–143, 145, 147, 148, 153, 166,
171–173, 175, 186, 188

## 蝙蝠

128, 177, 178

## 贝叶斯

105, 108

## 交叉

23, 41, 43, 85, 86, 174, 175

## BB-BC

16, 19, 21, 22, 25, 26, 29, 30, 36,
38–40, 42, 45, 46, 49

## 交叉/中心

21, 23

## 截断

186

## 数据集

18, 26, 36, 65, 74, 81, 106, 108,
122–125, 129, 142, 153
174, 178, 179

## 截止时间感知

17

## 启发式

16, 82, 83, 121, 142, 167, 171,
174, 178, 179

## 层次化

190, 193, 194, 196

## 处理

74, 103, 139, 142

## 高性能

35

## 证明

60

## 桌面

5, 8, 11–13

## 幻觉

5, 7

## 灾难

10

## 移民

175, 176

## 停机时间

6, 60

## 无限

7

## 无穷

60

## 经济

17

## 弹性

34, 100, 163

## 关键性能指标 (KPIs)

99, 100

## 能量感知

78, 141, 147, 154,
171, 178

## K-均值

60

## 能量受限

187, 194

## KNN

108, 110, 111

## 进化

18, 22, 23, 28, 42–44, 125, 174

## 基于 KNN

106

## 进化的

36, 37, 129, 139, 142

## 知识
