

## 9.2.5 基于机器学习的上行链路功率预测

本节根据文献[\[207\]](#backmatter-001.xhtml#b_9783110785944-010_ref_207)总结了基于机器学习的上行链路功率预测工作。面向能量的系统设计是针对静态和移动物联网传感器节点的一项重要优化任务，特别是对于资源高度受限的车辆，如移动机器人系统。对于基于4G/5G的蜂窝通信系统，上行链路数据传输的有效发射功率对整体系统功耗至关重要。遗憾的是，该信息通常隐藏在现成的调制解调器和移动终端中，因此无法用于绿色通信。此外，移动设备的动态发射功率控制行为在大多数成熟的仿真框架中并未显式建模。

为了弥补这一空白，我们提出了一种基于机器学习的新方法，用于根据可用的被动网络质量指标和应用层信息预测用于数据传输的上行链路发射功率。[图 9.15](#9783110785937_093138.xhtml#b_9783110785944-009_fig_015) 显示了所提解决方案的示意图。核心思想是利用基于`SDR`（软件定义无线电）的测量装置——能够同时确定上行链路发射功率 `P_TX` 和不同的网络上下文指标——以推导出一种基于机器学习的预测模型，该模型从上下文测量中推断 `P_TX`。然后，该模型可以部署到其他无法自行确定 `P_TX` 的平台上。

所需的机器学习模型源自在公共蜂窝网络中进行的驾驶测试的综合现场测量，并可进行参数化，以整合给定目标平台能够为预测过程提供的所有测量数据。[图 9.16](#9783110785937_093138.xhtml#b_9783110785944-009_fig_016) 显示了沿车辆轨迹的测量点路线图，该轨迹覆盖了城市、郊区和农村环境。总共在真实世界测量中获取了 6172 个数据样本。聚焦于平台的感知能力，我们考虑了四种不同的特征集变体。[表 9.3](#9783110785937_093138.xhtml#b_9783110785944-009_tab_003) 给出了特征集及其所含特征隐含影响因素的摘要。

![Fig. 9.16 Road map with locations of all data samples of the measurement campaign between two larger cities in Germany. Each blue point represents an intermediate status logging of all measured variables (cf. Table 9.3) during ongoing uplink transmissions. (Map: ©OpenStreetMap contributors, CC BY-SA). ©\[2018\] IEEE. Reprinted, with permission, from \[207\].](graphic/b_9783110785944-009_fig_016.png)

**图 9.16** 德国两座大城市之间测量活动的所有数据样本位置路线图。每个蓝点代表正在进行的上行链路传输期间所有测量变量的中间状态记录（参见表 9.3）。（地图：©OpenStreetMap 贡献者，CC BY-SA）。©\[2018\] IEEE. 经许可转载自 [\[207\]](#backmatter-001.xhtml#b_9783110785944-010_ref_207)。

对于实际预测任务，考虑了不同的回归模型：

*   **随机森林**，包含 64 棵树，最大深度为 32。
*   **深度学习**，包含三个全连接隐藏层，每层 64 个神经元，以及修正线性单元（`ReLU`）激活函数。
*   **岭回归**，包含 12 个模型参数（每个特征一个加上一个偏置项）。

10 折交叉验证的结果总结在[图 9.17](#9783110785937_093138.xhtml#b_9783110785944-009_fig_017)中。虽然特征集变体之间的差异相对较小，但可以观察到机器学习模型之间存在较大差异。随机森林模型表现最佳，平均绝对误差为 3.166 dB。还可以看到，不同交叉验证运行之间的标准差很小，这表明模型对未知和独立数据有良好的拟合度。

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

[1] D. J. Abadi 等. “Aurora: 数据流管理的新模型与架构”。载于：*The VLDB Journal – The Int. Journal on Very Large Data Bases* 12.2 (2003 年 8 月)，第 120–139 页（引用见第 21 页）。[→](#9783110785937_002446.xhtml#xref_d1990e2155)

[2] M. R. Ackermann, J. Blömer, and C. Sohler. “度量与非度量距离度量下的聚类”。载于：*ACM Transactions on Algorithms* 6.4 (2010)。早前见于 2008 年离散算法研讨会论文集，59:1–59:26（引用见第 201, 203, 204 页）。[a](#9783110785937_041148.xhtml#xref_d1990e49651), [b](#9783110785937_041148.xhtml#xref_d1990e49734), [c](#9783110785937_041148.xhtml#xref_d1990e50684), [d](#9783110785937_041148.xhtml#xref_d1990e50691)

[3] C. Adam-Bourdarios, G. Cowan, C. Germain, I. Guyon, B. Kégl, and D. Rousseau. “希格斯玻色子机器学习挑战赛”。载于：*Advances in Neural Information Processing Systems: Procs. of the Workshop on High-energy Physics and Machine Learning 2015*. 2015, pp. 19–55 (cit. on p. 250). [→](#9783110785937_066530.xhtml#xref_d1990e69623)

