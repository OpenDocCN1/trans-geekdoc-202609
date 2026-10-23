
其中 G† 是矩阵 G 的 Moore-Penrose 广义逆。

## III. 系统设计

### A. 总体架构
CSI 基于定位系统的框架如图 2 所示。CSI Tools 首先采集 CSI 样本，然后对 CSI 进行预处理。之后使用 DTW 提取特征并输入 ELM 进行模型训练。测试集以相同方式处理以获得特征，然后得到测试结果。

![](img/bc94f492e7e471f80902b1c5ae1db01e_2_0.png)

Fig.2 定位系统的框架。

### B. 数据预处理
采集的原始 CSI 数据包含典型的误差，例如有用的信道状态信息和测量误差，以及由设备干扰或不确定性形成的某些异常值，这些异常值会干扰使用 CSI 进行定位。我们在每个子载波上应用滑动窗口的 Hampel 滤波器，以去除通常与相邻 CSI 测量值显著不同的异常值。此外，我们应用移动平均滤波器以去除高频噪声。

### C. 特征提取
DTW 是一种动态规划算法，用于计算两个时间序列的相似度，尤其是长度不同的序列。它主要应用于时序数据，例如孤立词语音识别、手势识别、数据挖掘和信息检索。在指纹定位中，指纹几乎总是基于单个数据，很少基于一段数据生成用于定位的指纹。DTW 计算不同参考点处的目标与不在环境中的目标之间的差异以获得指纹，有效地提取了数据的整体特征。

## IV. 评估

### A. 实验设置
我们在由两个 WiFi 设备（即 mini-pc）和一个商用无线接入点（即运行在 5.24 GHz 信道上的 TP-Link WDR5300 带天线）组成的 802.11n WiFi 网络中部署了系统。mini-pc 配备了用于测量 CSI 的 Intel WiFi Link 5300 卡和三个外部天线。为了评估我们的系统，我们在活动室中进行了实验。我们

表 I. 定位性能

| Method | Mean error |
| ELM | 1.1243m |
| BPNN | 1.3789m |
| SVM | 1.3345m |

我们采用 1 个 AP 和 2 个 MP 的方案以更好地覆盖感兴趣区域。我们在监控区域内均匀选择参考位置。区域被划分为 64 个单元，每个单元大小为 0.6 m*0.6 m。参考点设置在每个单元的中心，测试点随机散布在整个区域内。每个位置收集一百个数据包。

### B. 定位性能
我们使用平均距离误差作为性能指标。将我们的系统与其他两种机器学习方法进行比较的结果如表 I 所示。可以看出，我们的方法优于 SVM 和 BPNN，证明了 ELM 算法的有效性，并且使用 DTW 提取特征可以大大提高定位精度。

## V. 结论
在本文中，我们提出了一种基于 WiFi CSI 的无设备室内定位方法，使用两个常见的商用 WiFi 设备和一个接收设备收集 CSI 数据，对收集的 CSI 数据进行预处理，使用 DTW 提取特征，然后使用 ELM 模型进行定位。该方法在实验室环境中进行了评估，实验结果表明该方法优于 SVM 和 BPNN。在典型的室内环境中，平均距离误差为 1.12m。

## 致谢
本工作部分得到国家重点研发计划项目 2017YFB1401203、北京市重点研发计划项目 Z191100007519001 和佛山科技创新计划项目 BK20AF005 的支持。

## 参考文献
[1] Liu H, Darabi H, Banerjee P, et al. 无线室内定位技术与系统的综述[J]. IEEE Transactions on Systems, Man, and Cybernetics, Part C (Applications and Reviews), 2007, 37(6): 1067-1080.

[2] Gellersen H, Kortuem G, Schmidt A, et al. 使用 smart-its 的物理原型制作[J]. IEEE Pervasive computing, 2004, 3(3): 74-82.

[3] Harle R K, Hopper A. 部署和评估一个位置感知系统[C]//Proceedings of the 3rd international conference on Mobile systems, applications, and services. 2005: 219-232.

[4] Cai Q, Aggarwal J K. 跨多个同步视频流的室内场景中人体运动的自动跟踪[C]//Sixth International Conference on Computer Vision (IEEE Cat. No. 98CH36271). IEEE, 1998: 356-362.

[5] Gezici S, Tian Z, Giannakis G B, et al. 通过超宽带无线电进行定位：未来传感器网络定位方面的展望[J]. IEEE signal processing magazine, 2005, 22(4): 70-84.

[6] Li X, Li S, Zhang D, et al. Dynamic-music: 精确的无设备室内定位[C]//Proceedings of the 2016 ACM International Joint Conference on Pervasive and Ubiquitous Computing. 2016: 196-207.

[7] Li X, Zhang D, Lv Q, et al. IndoTrack: 基于商用 Wi-Fi 的无设备室内人体跟踪[C]. Proceedings of the ACM on Interactive, Mobile, Wearable and Ubiquitous Technologies, 2017, 1(3): 1-22.

[8] Qian K, Wu C, Yang Z, et al. Widar: 基于商用 Wi-Fi 的速度监测分米级被动跟踪[C]//Proceedings of the 18th ACM International Symposium on Mobile Ad Hoc Networking and Computing. 2017: 1-10.

[9] Haibin Bian. 基于 CSI 数据库的室内定位系统[D]. XIDIAN UNIVERSITY, 2017.

[10] Sanam T F, Godrich H. FuseLoc: 基于 CCA 的 WiFi 信号 CSI 相位和幅度的室内定位信息融合[C]//ICASSP 2019-2019 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP). IEEE, 2019: 7565-7569.

[11] Zhang J, Xiao W, Li Y. 数据与知识双驱动的大规模无设备定位集成[J]. IEEE Internet of Things Journal, 2020, 8(1): 320-331.

[12] Halperin D, Hu W, Sheth A, et al. 工具发布：使用信道状态信息采集 802.11n 轨迹[J]. ACM SIGCOMM Computer Communication Review, 2011, 41(1):53.

[13] Zhang J, Li Y, Xiao W. 利用时空信息在杂乱环境中进行无设备定位的集成多核学习[J]. IEEE Internet of Things Journal, 2020.

[14] Zhang J, Xiao W, Li Y, et al. 用于无设备定位的多层概率极限学习机[J]. Neurocomputing, 2020, 396: 383-393.

[15] Zhang J, Li Y, Xiao W, et al. 用于未知噪声建模的鲁棒极限学习机[J]. Journal of the Franklin Institute, 2020, 357(14): 9885-9908.
