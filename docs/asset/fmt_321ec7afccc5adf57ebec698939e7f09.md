
![Fig. 9.15 Uplink power control of UE and its underlying system parameters are typically hidden to the application layers. However, this knowledge is crucial for predictions and estimations of the involved power consumption in energy-aware applications and system-level simulations. The proposed model derives this information from passive connectivity indicators. ©[2018] IEEE. Reprinted, with permission, from [207].](graphic/b_9783110785944-009_fig_015.png)

### 9.2.5 基于机器学习的上行链路功率预测

本节根据文献[\[207\]](#backmatter-001.xhtml#b_9783110785944-010_ref_207)总结了基于机器学习的上行链路功率预测工作。面向能量的系统设计是针对静态和移动物联网传感器节点的一项重要优化任务，特别是对于资源高度受限的车辆，如移动机器人系统。对于基于 4G/5G 的蜂窝通信系统，上行链路数据传输的有效发射功率对整体系统功耗至关重要。遗憾的是，该信息通常隐藏在现成的调制解调器和移动终端中，因此无法用于绿色通信。此外，移动设备的动态发射功率控制行为在大多数成熟的仿真框架中并未显式建模。

为了弥补这一空白，我们提出了一种基于机器学习的新方法，用于根据可用的被动网络质量指标和应用层信息预测用于数据传输的上行链路发射功率。图 9.15 显示了所提解决方案的示意图。核心思想是利用基于`SDR`（软件定义无线电）的测量装置——能够同时确定上行链路发射功率 `P_TX` 和不同的网络上下文指标——以推导出一种基于机器学习的预测模型，该模型从上下文测量中推断 `P_TX`。然后，该模型可以部署到其他无法自行确定 `P_TX` 的平台上。

所需的机器学习模型源自在公共蜂窝网络中进行的驾驶测试的综合现场测量，并可进行参数化，以整合给定目标平台能够为预测过程提供的所有测量数据。图 9.16 显示了沿车辆轨迹的测量点路线图，该轨迹覆盖了城市、郊区和农村环境。总共在真实世界测量中获取了 6172 个数据样本。聚焦于平台的感知能力，我们考虑了四种不同的特征集变体。表 9.3 给出了特征集及其所含特征隐含影响因素的摘要。

![Fig. 9.16 Road map with locations of all data samples of the measurement campaign between two larger cities in Germany. Each blue point represents an intermediate status logging of all measured variables (cf. Table 9.3) during ongoing uplink transmissions. (Map: ©OpenStreetMap contributors, CC BY-SA). ©\[2018\] IEEE. Reprinted, with permission, from \[207\].](graphic/b_9783110785944-009_fig_016.png)

**图 9.16** 德国两座大城市之间测量活动的所有数据样本位置路线图。每个蓝点代表正在进行的上行链路传输期间所有测量变量的中间状态记录（参见表 9.3）。（地图：©OpenStreetMap 贡献者，CC BY-SA）。©\[2018\] IEEE. 经许可转载自 [\[207\]](#backmatter-001.xhtml#b_9783110785944-010_ref_207)。

对于实际预测任务，考虑了不同的回归模型：

*   **随机森林**，包含 64 棵树，最大深度为 32。
*   **深度学习**，包含三个全连接隐藏层，每层 64 个神经元，以及修正线性单元（`ReLU`）激活函数。
*   **岭回归**，包含 12 个模型参数（每个特征一个加上一个偏置项）。

10 折交叉验证的结果总结在图 9.17 中。虽然特征集变体之间的差异相对较小，但可以观察到机器学习模型之间存在较大差异。随机森林模型表现最佳，平均绝对误差为 3.166 dB。还可以看到，不同交叉验证运行之间的标准差很小，这表明模型对未知和独立数据有良好的拟合度。

**表 9.3** 捕获的特征及其与基于全特征集 `F`、实用集 `P1`/`P2` 和仿真集 `S` 的应用专用预测模型的关联。©\[2018\] IEEE. 经许可转载自 [\[207\]](#backmatter-001.xhtml#b_9783110785944-010_ref_207)。

| 参数 | 模型 | 指示影响因素 |
| --- | --- | --- |
| 速度 | `F`, `P1`, `P2`, `S` | 快衰落造成的失真 |
| 上传大小 | `F`, `P1`, `P2`, `S` | TCP 慢启动的影响 |
| RSRP | `F`, `P1`, `P2`, `S` | 信号强度、距离 |
| RSRQ, SINR | `F`, `P1`, `P2` | 信号清晰度、干扰 |
| 数据速率 | `F`, `P1` | 信号强度、已分配资源块 `M` |
| RSSI | `F` | 信号强度、距离 |
| 频段 | `F` | 环境 [\[349\]](#backmatter-001.xhtml#b_9783110785944-010_ref_349) |
| 邻区数量（同频/异频） | `F` | 环境、小区密度、干扰 |
| 小区带宽 | `F` | 发射功率余量耗尽 |

![Fig. 9.17 Cross-validated error of trained prediction models for each feature subset (F, P1, P2, S) and each machine learning method (Random Forest, Deep Learning, Ridge Regression) in terms of Root Mean Squared Error (RMSE) (left) and Mean Absolute Error (MAE) (right). Lower is better. ©\[2018\] IEEE. Reprinted, with permission, from \[207\].](graphic/b_9783110785944-009_fig_017.png)

**图 9.17** 每个特征子集（`F`、`P1`、`P2`、`S`）和每种机器学习方法（随机森林、深度学习、岭回归）的训练预测模型的交叉验证误差，以均方根误差（`RMSE`）（左）和平均绝对误差（`MAE`）（右）表示。越低越好。©\[2018\] IEEE. 经许可转载自 [\[207\]](#backmatter-001.xhtml#b_9783110785944-010_ref_207)。

## 注释

# 参考文献

[1] D. J. Abadi 等. “Aurora: 数据流管理的新模型与架构”。载于：*The VLDB Journal – The Int. Journal on Very Large Data Bases* 12.2 (2003 年 8 月)，第 120–139 页（引用见第 21 页）。→

[2] M. R. Ackermann, J. Blömer, and C. Sohler. “度量与非度量距离度量下的聚类”。载于：*ACM Transactions on Algorithms* 6.4 (2010)。早前见于 2008 年离散算法研讨会论文集，59:1–59:26（引用见第 201, 203, 204 页）。a, b, c, d

[3] C. Adam-Bourdarios, G. Cowan, C. Germain, I. Guyon, B. Kégl, and D. Rousseau. “希格斯玻色子机器学习挑战赛”。载于：*Advances in Neural Information Processing Systems: Procs. of the Workshop on High-energy Physics and Machine Learning 2015*. 2015, pp. 19–55 (cit. on p. 250). →

# 参考文献

[4] A. Adiththan, S. Ramesh, and S. Samii. “Cloud-assisted control of ground vehicles using adaptive computation offloading techniques”. In: *Procs. of the Design, Automation and Test in Europe Conference 2018*. Mar. 2018, pp. 589–592 (cit. on p. 363). →

[5] P. K. Agarwal, R. Ben Avraham, H. Kaplan, and M. Sharir. “Computing the Discrete Fréchet Distance in Subquadratic Time”. In: *SIAM Journal on Computing* 43.2 (2014). Previously appeared in the Procs. of the Symposium on Discrete Algorithms 2013, pp. 429–449 (cit. on p. 199).

[6] P. K. Agarwal, S. Har-Peled, and K. R. Varadarajan. “Approximating extent measures of points”. In: *Journal of the Association for Computing Machinery* 51.4 (2004), pp. 606–635 (cit. on pp. 87, 88).

[7] P. K. Agarwal and R. Sharathkumar. “Streaming Algorithms for Extent Problems in High Dimensions”. In: *Algorithmica* 72.1 (2015), pp. 83–98 (cit. on p. 87).

[8] A. Agrawal, A. Jaiswal, C. Lee, and K. Roy. “X-SRAM: Enabling In-Memory Boolean Computations in CMOS Static Random Access Memories”. In: *IEEE Transactions on Circuits and Systems I: Regular Papers* 65.12 (2018) (cit. on p. 4). →

[9] R. Agrawal, A. Gupta, Y. Prabhu, and M. Varma. “Multi-label learning with millions of labels: Recommending advertiser bid phrases for web pages”. In: *Procs. of the Int. Conference on World Wide Web 2013*. 2013, pp. 13–24 (cit. on p. 272).

[10] B. Ahmadi, K. Kersting, and S. Natarajan. “Lifted Online Training of Relational Models with Stochastic Gradient Methods”. In: *Procs. of the European Conference on Machine Learning and Principles and Practice of Knowledge Discovery in Databases 2012*. Ed. by P. Flach, T. D. Bie, and N. Cristianini. Vol. 7523. Bristol, UK: Springer, Sept. 2012, pp. 585–600. url: [`link.springer.com/chapter/10.1007/978-3-642-33460-3_43`](http://link.springer.com/chapter/10.1007/978-3-642-33460-3_43) (cit. on p. 407). →

[11] R. Ahmed, B. Buchli, S. Draskovic, L. Sigrist, P. Kumar, and L. Thiele. “Optimal Power Management with Guaranteed Minimum Energy Utilization for Solar Energy Harvesting Systems”. In: *ACM Transactions on Embedded Computing Systems* 18.4 (2019), pp. 1–26 (cit. on p. 47). →

[12] H.-K. Ahn, H. Alt, M. Buchin, E. Oh, L. Scharf, and C. Wenk. “Middle curves based on discrete Fréchet distance”. In: *Computational Geometry: Theory and Applications* 89 (2020). Previously appeared in LATIN 2016, p. 101621 (cit. on pp. 197, 201, 202, 204, 205). a, b, c, d, e, f, g

[13] Y. Akhremtsev, P. Sanders, and C. Schulz. “High-Quality Shared-Memory Graph Partitioning”. In: *IEEE Transactions on Parallel and Distributed Systems* 31.11 (2020), pp. 2710–2722 (cit. on p. 152). →

[14] H. Alt and M. Godau. “Computing the Fréchet distance between two polygonal curves”. In: *Int. Journal of Computational Geometry and Applications* 5 (1995), pp. 75–91 (cit. on pp. 199, 211). a, b, c, d

[15] F. Álvaro Muñoz, J. Sánchez Peiró, and J. Benedí Ruiz. “Recognition of On-line Handwritten Mathematical Expressions Using 2D Stochastic Context-Free Grammars and Hidden Markov Models”. In: *Pattern Recognition Letters* (2014), pp. 58–67 (cit. on p. 162).

[16] M. R. Anderberg. *Cluster analysis for applications*. Academic Press, 1973 (cit. on pp. 218, 222). a, b

[17] H. Anderhub et al. “Design and operation of FACT - the first G-APD Cherenkov telescope”. In: *Journal of Instrumentation* 8.06 (June 2013), P06008. url: [`iopscience.iop.org/1748-0221/8/06/P06008/`](http://iopscience.iop.org/1748-0221/8/06/P06008/) (cit. on pp. 351, 352). a, b

[18] A. Andrae and T. Edler. “On Global Electricity Usage of Communication Technology: Trends to 2030”. In: *Challenges* 6.1 (2015), pp. 117–157 (cit. on p. 2). →

[19] S. I. Ao et al. “CLUSTAG: hierarchical clustering and graph methods for selecting tag SNPs”. In: *Bioinformatics* 21.8 (2005), pp. 1735–1736 (cit. on p. 216). →

[20] A. Arasu, S. Babu, and J. Widom. “The CQL Continuous Query Language: Semantic Foundations and Query Execution”. In: *The VLDB Journal – The Int. Journal on Very Large Data Bases* 15.2 (June 2006), pp. 121–142 (cit. on p. 21). →
