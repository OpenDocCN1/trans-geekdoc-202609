


## 图 11.3.3 多模态框架.

### ECG 分类器

- 数据预处理
- 数据采样
- 特征提取

![](img/74778e0ca6379f5d5e4de83ac1ff23da_277_0.png)

### EEG 分类器

- 数据预处理
- 数据采样
- 特征提取

![](img/74778e0ca6379f5d5e4de83ac1ff23da_277_1.png)

### 决策融合

(多数投票)

- 数据预处理
- 数据采样
- 特征提取

![](img/74778e0ca6379f5d5e4de83ac1ff23da_277_2.png)

### 特征融合

(连接)

- 数据预处理
- 数据采样
- 特征提取

![](img/74778e0ca6379f5d5e4de83ac1ff23da_277_3.png)

### 基于计算机的行为分类器

- 数据预处理
- 数据采样
- 特征提取

## 表 11.16 使用决策融合检测恶意活动的平均结果

| 分类器 | 参与者数量 | 准确率 | 真正率 | 假正率 | F-度量 |
|---|---|---|---|---|---|
| SVM | 20 | 95.86 | 0.91 | 0.02 | 0.93 |
| Random Forest | 20 | 97.55 | 0.95 | 0.01 | 0.96 |
| k-NN | 20 | 95.83 | 0.92 | 0.02 | 0.93 |

行为指标可以成为检测和预测恶意用户行为及其实施内部威胁攻击意图的绝佳信息来源，此类攻击可能会对组织的数据和信息系统造成损害。

## 结论

本研究的目标是提出一种基于用户心理生理和计算机行为指标的新型内部威胁检测方法。我们的结果表明，EEG 和 ECG 信号在检测恶意活动方面具有良好的分辨率，如我们的信号检测模块所示。尽管硬件的可用性及其在现实世界工作环境中的适用性为该模块带来了一些挑战，但该模块可以在员工处理高度敏感信息的高度安全工作环境中使用。此外，随着可穿戴技术的最新进步，这一限制在不久的将来将不再存在。例如，大多数智能手表和健身追踪器都配备了可以记录 ECG 信号的传感器。同时，EEG 技术也在不断发展，最近推出了许多新设备，例如智能帽（SmartCap Tech, 2018）和心态智能耳机（kickstarter, 2018）。此外，我们分别提供了每个信号的性能，因此，基于可用性，组织可以随时选择使用符合其需求的任何信号。

非信号检测模块提供了最佳选择，因为它易于设置且不需要任何昂贵的硬件，可以使用基于视频的眼动追踪设备；此外，还有许多不需要复杂硬件且能实现良好准确性的眼动追踪系统的新实现（Gómez-Poveda & Gaudioso, 2016; Mazhar, Shah, Khan, & Tehami, 2015）。而且，鼠标移动和击键追踪器不需要任何硬件。单独评估每个心理生理行为指标然后将它们结合起来的原因是为了在设计中提供灵活性，因为如前所述，某些指标可能不可用。因此，我们提出的内部威胁检测框架可以是这些指标的组合，也可以是单一指标。它还可以与其他方法结合，这些方法使用用户在使用网络或组织计算机系统及资源时的活动行为，以提高检测准确性。

由于我们开展人体研究实验来评估我们的方法，在选择参与者时，我们在性别、年龄、教育水平和网络安全知识方面非常谨慎。我们尽力招募具有多样性的参与者，以代表现实世界的工作环境。然而，纳入教育和计算机技能较低的参与者将是有价值的。此外，我们的主要挑战是实验场景，主要是恶意场景。模拟现实世界的内部威胁场景是一项非常复杂的任务，因为它与用户的心理和行为方面相关。我们在实验环境中尝试模拟现实世界的工作环境，并在类似于现实世界内部攻击场景的条件下测试参与者。我们选择了涉及网络和应用程序级别的两种攻击，这两种攻击在内部人员实践中主要使用。有可能我们实际区分的是参与者正在执行的具体任务，而不是该任务是否恶意。为了以统计显著性解决这个问题，需要从更多任务中收集更多数据，并基于未包含在训练中的任务进行测试。

## 参考文献

Agrafioti, F., Hatzinakos, D., & Anderson, A. K. (2012). 用于情绪检测的 ECG 模式分析. IEEE Transactions on Affective Computing, 3, 102–115.

AlgoSec. (2014年4月16日). AlgoSec 调查：2014 年网络安全状况. Retrieved from www.algosec.com.

Almhehmedi, A., & El-Khatib, K. (2014). 关于使用生理信号监测进行内部威胁检测的可能性. 在《第七届信息与网络安全国际会议论文集》中（第 223 页）.

Altman, N. S. (1992). 核和最近邻非参数回归简介. The American Statistician, 46, 175–185.

Apperly, I. A., Samson, D., Chiavarino, C., & Humphreys, G. W. (2004). 额叶和颞顶叶对心理理论的贡献：来自语言和执行需求降低的错误信念任务的神经心理学证据. Journal of Cognitive Neuroscience, 16, 1773–1784.

Bajada, C. J., Haroon, H. A., Azadbakht, H., Parker, G. J., Ralph, M. A., & Cloutman, L. L. (2017). 颞叶中的纤维终止：其位置及相关功能. Cortex, 97, 277–290.

Bergadano, F., Gunetti, D., & Picardi, C. (2002). 通过击键动态进行用户身份验证. ACM Transactions on Information and System Security (TISSEC), 5, 367–397.

Borga, M. (2001). 典型相关：一个教程. 在线教程, 4, 5. http://people.imt.liu.se/magnus/cca.

Bowen, B. M., Salem, M. B., Keromytis, A. D., & Stolfo, S. J. (2010). 用于缓解内部威胁的监控技术. 在《网络安全中的内部威胁》中（第 197–217 页）. Springer, Boston, MA.

Breiman, L. (2001). 随机森林. Machine Learning, 45, 5–32.

CERT. (2014, 7). 美国网络犯罪状况调查. Retrieved from https://resources.sei.cmu.edu/asset_files/Presentation/2014_017_001_298322.pdf.

Cai, J., Liu, G., & Hao, M. (2009). 从 ECG 信号进行情绪识别的研究. 在 2009 年信息技术与计算机科学国际会议（ITCS 2009）中，1，（第 497–500 页）.

Cantoni, V., Galdi, C., Nappi, M., Porta, M., & Riccio, D. (2015). GANT：用于人类识别的注视分析技术. Pattern Recognition, 48, 1027–1038.

Chanel, G., Ansari-Asl, K., & Pun, T. (2007). 在情绪回忆范式中使用生理信号进行效价-唤醒度评估. 在 2007 年 IEEE 系统、人与控制论国际会议（ISIC）中（第 2662–2667 页）.

Chayer, C., & Freedman, M. (2001). 额叶功能. Current Neurology and Neuroscience Reports, 1, 547–552.

Cortes, C., & Vapnik, V. (1995). 支持向量网络. Machine Learning, 20, 273–297.

Cummings, A., Lewellen, T., McIntire, D., Moore, A. P., & Trzeciak, R. (2012). 内部威胁研究：涉及美国金融服务业欺诈的非法网络活动（编号 CMU/SEI-2012-SR-004）. 卡内基梅隆大学匹兹堡分校软件工程学院.

De Luca, A., Denzel, M., & Hussmann, H. (2009年7月). 看看我的眼睛！你能猜出我的密码吗？在第五届可用隐私与安全研讨会论文集中（第 1–12 页）.

Eberz, S., Rasmussen, K. B., Lenders, V., & Martinovic, I. (2015). 防止午餐时间攻击：使用眼动生物特征对抗内部威胁. 在 2015 年网络与分布式系统安全研讨会（NDSS）论文集中.

Electrical Geodesics Inc. (2017). 临床大地测学 EEG 系统 400. Retrieved from www.egi.com.

Emotiv, Inc. (2019). 情绪系统. Retrieved from https://www.emotiv.com/.

Fogassi, L., Ferrari, P. F., Gesierich, B., Rozzi, S., Chersi, F., & Rizzolatti, G. (2005). 顶叶：从动作组织到意图理解. Science, 308, 662–667.

Glasser, J., & Lindauer, B. (2013年5月). 弥合差距：生成内部威胁数据的务实方法. 在 2013 年 IEEE 安全与隐私研讨会中（第 98–104 页）. IEEE.

Goldberg, E. (2002). 执行大脑：额叶与文明心智. Oxford University Press, USA.

Gómez-Poveda, J., & Guadioso, E. (2016). 使用网络摄像头评估眼动追踪算法的时间稳定性. Expert Systems with Applications, 64, 69–83.

Greitzer, F. L., & Frincke, D. A. (2010). 将传统网络安全审计数据与心理社会数据相结合：走向内部威胁缓解的预测建模. 在《网络安全中的内部威胁》中（第 85–113 页）. Springer, Boston, MA.

