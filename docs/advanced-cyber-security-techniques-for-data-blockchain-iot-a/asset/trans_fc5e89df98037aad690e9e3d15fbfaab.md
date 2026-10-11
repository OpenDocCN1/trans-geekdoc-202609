
• 可以看出，`fwd_packet_length_mean` 与 `fwd_packet_length_std`、`fwd_packet_length_mean` 与 `fwd_packet_length_max`、`fwd_packet_length_std` 与 `fwd_packet_length_max`、`bck_packet_length_mean` 与 `bck_packet_length_max`、`bck_packet_length_std` 与 `bck_packet_length_max`、`fwd_packets` 与 `bck_packets`、`packet_length_var` 与 `packet_length_mean`、`packet_length_std` 与 `packet_length_mean`、`avg_fwd_seg_size` 与 `avg_packet_size`、`avg_bck_segment_size` 与 `avg_packet_size`、`min_seg_size_fwd` 与 `act_data_pkt_fwd` 存在中等正相关。

• 可以看出，`idle_std` 与 `active_min`、`fwd_IAT_min` 与 `fwd_IAT_std` 存在强负相关。

• 可以看出，`avg_bck_seg_size` 与 `avg_fwd_seg_size` 存在中等负相关。

从上述散点图观察中，我们可以推断：在这些具有负相关的特征变量中，只有对输出影响较大的特征才可能在进一步分析后被选中。

### 热力图

#### 图 7. 热力图：不同数值变量间相关性的可视化表示

![979-8-3693-9225-6.ch007.f07](image/979-8-3693-9225-6.ch007.f07.png)

生成热力图是为了对 78 个特征进行多变量分析，观察结果如下：

可以看出，少数变量表现出强正相关（由热力图的对角线指示），这些可能是具有潜在重要性的特征。此外，少数变量表现出弱正相关和弱负相关。举几个例子：

*   ▪ 前向数据包总数与前向数据包总长度之间存在弱负相关。
*   ▪ 前向数据包总长度与前向数据包长度均值之间存在弱正相关。
*   ▪ 前向数据包长度均值与后向数据包长度均值之间存在弱负相关。
*   ▪ 流字节数/秒与流 IAT 均值之间存在弱正相关。
*   ▪ 前向 IAT 总计与后向 IAT 均值之间存在弱正相关。
*   ▪ 后向 IAT 均值与后向数据包长度均值之间存在弱负相关。

由于这些特征表现出弱相关性，它们可能不包含太多信息，因此在这些特征对中只能选择一个。

## 特征选择

特征选择基于粒子群优化技术进行。初始化了 10 代。每个簇的适应度函数通过逻辑回归计算。

### 特征选择准确率（局部）

这些是第一次迭代中不同代的个体最优值。

#### 图 8. 特征选择准确率（局部）——第一次迭代中不同代获得的个体最优值

![979-8-3693-9225-6.ch007.f08](image/979-8-3693-9225-6.ch007.f08.png)

可以看出，不同簇中个体最优的最大准确率为 0.8421。

### 全局最优准确率

#### 图 9. 遍历所有代后获得的全局最优准确率

![979-8-3693-9225-6.ch007.f09](image/979-8-3693-9225-6.ch007.f09.png)

在遍历完所有 10 代并将当前代的所有个体最优值与其他所有代的个体最优值进行比较后，全局最优的准确率为 0.84217。

### 选定特征

基于上述特征选择方法，特征选择后，为降低数据集维度，选定的特征如下：

`Flow Duration`、`Total Backward Packets`、`Total Length of Fwd Packets`、`Fwd Packet Length Min`、`Fwd Packet Length Mean`、`Bwd Packet Length Min`、`Bwd Packet Length Mean`、`Bwd Packet Length Std`、`Flow Bytes/s`、`Flow Packets/s`、`Flow IAT Std`、`Flow IAT Max`、`Flow IAT Min`、`Fwd IAT Total`、`Fwd IAT Mean`、`Bwd IAT Total`、`Bwd IAT Mean`、`Bwd IAT Std`、`Fwd PSH Flags`、`Fwd URG Flags`、`Bwd Header Length`、`Min Packet Length`、`Max Packet Length`、`Packet Length Std`、`Packet Length Variance`、`FIN Flag Count`、`RST Flag Count`、`CWE Flag Count`、`ECE Flag Count`、`Down/Up Ratio`、`Average Packet Size`、`Avg Bwd Segment Size`、`Fwd Header Length.1`

在可用的 78 个特征中，共选定了 31 个特征。

### 数据平衡

从计数图（[图 5](#979-8-3693-9225-6.ch007.bits-pdf.xhtml#_idTextAnchor186)）可以看出，数据高度不平衡。这会导致训练模型偏向多数类，即良性。因此，必须对数据进行平衡以获得准确的结果。多数类使用随机欠采样（RUS）进行欠采样。随后使用自适应合成过采样（ADASYN）对少数类数据进行过采样。这些过程通过饼图可视化如下：

#### 图 10. 数据平衡输出：包含原始数据中类别比例、RUS 后获得的比例以及 ADASYN 后比例的饼图

![979-8-3693-9225-6.ch007.f10](image/979-8-3693-9225-6.ch007.f10.png)

### 分类

然后使用下表列出的分类器算法对平衡数据集进行训练和测试。评估指标（准确率、精确率、召回率、F1 分数以及训练和测试时间）也在表中列出。

#### 获得的评估指标

#### 图 11. 获得的评估指标——分类

![979-8-3693-9225-6.ch007.f11](image/979-8-3693-9225-6.ch007.f11.png)

下图展示了不同模型的准确率、精确率、F1 分数、召回率和测试时间。

#### 图 12. 获得的评估指标——分类的条形图，展示准确率、精确率、F1 分数、召回率和测试时间

![979-8-3693-9225-6.ch007.f12](image/979-8-3693-9225-6.ch007.f12.png)

可以看出，随机森林在准确率、精确率、F1 分数和召回率方面表现最佳。而决策树在考虑训练和测试时间时表现更好。高斯朴素贝叶斯尽管训练和测试耗时极少，但在其他指标上表现不佳。在所有 9 个模型中，AdaBoost 表现最差。

为了获得更深入的见解，为每个模型绘制了相关矩阵和 ROC 曲线。下图展示了决策树分类器的相关矩阵和 ROC 曲线。

#### 图 13. (a) 混淆矩阵：总结机器学习模型性能的矩阵——和 (b) ROC 曲线：展示分类模型性能的图表

![979-8-3693-9225-6.ch007.f13](image/979-8-3693-9225-6.ch007.f13.png)

决策树分类器的性能可通过混淆矩阵得到验证，该矩阵显示大量数值被正确检测（显示在对角线上）。ROC 曲线的推断如下：

高性能类别（AUC > 0.95）：良性、DoS GoldenEye、DoS Hulk、DoS Slowhttptest、DoS Slowloris、PortScan、SSH-Patator。

中等性能类别（AUC > 0.8）：DDoS、Infiltration。

低性能类别（AUC < 0.8）：Bot、暴力破解 Web 攻击、Heartbleed、XSS Web 攻击、SQL 注入 Web 攻击。

### 超参数调优

随后使用 Optuna 对模型进行超参数调优。获得的评估指标如下：

#### 获得的评估指标

#### 图 14. 获得的评估指标——超参数调优

![979-8-3693-9225-6.ch007.f14](image/979-8-3693-9225-6.ch007.f14.png)

可以看出，随机森林在所有评估指标方面仍然表现最佳。AdaBoost 和逻辑回归表现不佳。

### 集成学习

从调优后的模型中，选取随机森林、XGBoost、CatBoost 和 LightGBM 共 4 个模型，采用软投票技术进行集成。获得的评估指标如下。

#### 获得的评估指标
