
我们在这两种场景中都发现了一些有趣的结果。例如，在简单树形拓扑中，具有线性核的支持向量机分类器在表 16.6 中的召回率达到了 100%。这是因为该模型在测试期间将所有合法网络流量预测为合法行为（假阴性案例为 0）。因此，它实现了完美的召回率。在带有 LASSO 的逻辑回归中，表 16.6 中也发现了类似的结论。我们还从表 16.7 中发现了另一种备选结果（更高的精确率）。在这种情况下，该模型在测试期间将所有恶意网络流量识别为恶意行为（假阳性案例减少到 0）。因此，其精确率极高。

## 16.6 相关工作

在接下来，我们回顾了与本研究密切相关的各种研究工作。

近期，已经有很多利用机器学习完成诸如增强基于 IP 的网络安全的任务 38–40。例如，Doshi 等人 38 将低成本的机器学习算法应用于家庭路由器中以防止 DoS 攻击，证明了它可以具有很高的准确率。He 等人 39 开发了基于统计的机器学习算法来缓解云中的 DoS 攻击，这导致了高准确率和有效的缓解。同样，Santos 等人 40 在基于 SDN 的网络中使用机器学习算法检测 DoS 攻击，以确保网络性能。

目前已有一些改进 `NDN` 安全的努力 [41–42]。例如，Afanasyev 等人 [41] 开发了四种不同的方案，以缓解 `NDN` 中不同效率水平的泛洪攻击。同样，Khelifi 等人 [42] 在基于 `NDN` 的车辆网络中利用 `blockchain` 来确保车辆环境中的缓存安全，并增强缓存存储器与消费者车辆之间的信任。此外，还有针对 `IoTSE` 的一些研究工作 [11, 43]。例如，Liang 等人 [11] 在 `IoTSE` 中应用了 `NDN`，并测试了在不同 `IoTSE` 场景下的数据传输性能，证实了 `NDN` 可以提高网络性能。同样，Cheng 等人 [43] 设计了一种具有跨数据集特征图的新型神经网络结构，以在图像分类中获得更好的性能。此外，还有针对 `IoTs` 中公共安全及相关应用的研究工作 [44–45]。例如，Zhu 等人 [44] 设计了一个 `IoT-gateway` 以提高大规模通信中的网络可靠性和网络容量利用率。同样，Thirumalai 等人 [45] 为云和 `IoT` 安全开发了一种高效的公钥安全方案。然而，这些现有工作在基于 `IP` 的网络中需要跟踪繁重且复杂的网络流量，并且在部署到机器学习模型时需要消耗更多的资源和时间。

此外，这些方法并不适用于 `IoTSE` 的特性，即 `IoTSE` 是数据驱动的结构而非位置驱动。在我们的研究中，我们针对 `IoTSE` 场景分两个步骤解决了该问题。首先，我们使用 `NDN` 作为网络通信协议，因为 `NDN` 是一种数据驱动的拉-推模型，与 `IoTSE` 匹配。由于不需要源地址和目的地址，`NDN` 中的网络流量记录量被减少了。其次，我们为机器学习简化了网络流量数据集。由于 `IoTSE` 具有静态且特定的任务概况，所有应用程序的数据包发送率应该在一个相对稳定的范围内。因此，如果数据包发送率超出 `profile` 中的范围，我们就能有效地检测出可疑数据包。我们还减小了数据集的大小，以降低训练过程的时间和资源成本。

## 16.7 结语

本章研究了基于 `NDN` 的 `IoTSE` 中兴趣泛洪攻击（IFA）的三种攻击场景。使用 `ns3` 作为评估平台，我们在小规模和大规模仿真中设计了两种不存在泛洪攻击策略的 `IFA` 场景，并利用了不同的链路配置。我们首先展示了 `IFA` 造成的损害严重性。然后，根据收集的成功 `IFA` 数据集，我们处理了数据集并将其简化为 `PIT` 相关数据集中的 `out-request` 和 `outer network interface`。最后，我们获得了一个具有两个特征的数据集：`packets` 和攻击标签。我们比较了八种 `ML` 模型以执行攻击检测，并得出结论：大多数 `ML` 模型可以有效检测基于包率的数据集中的此类攻击。然而，我们发现基于线性的 `ML` 模型在数据集容量大幅增加时，检测准确率较差。

## 致谢

本材料基于空军科学研究办公室的支持，奖励编号为 `FA9550-20-1-0418`。本材料中表达的任何观点、发现、结论或建议均为作者观点，并不一定反映美国空军的观点。

## 参考文献

*   J. Lin, W. Yu, N. Zhang, X. Yang, H. Zhang, and W. Zhao, “A survey on internet of things: Architecture, enabling technologies, security and privacy,” `Internet of Things`, vol. 4, no. 5, pp. 1125–1142.
*   H. Xu, W. Yu, D. Griffith, and N. Golmie, “A survey on industrial of things,” `IEEE Access`, vol. 6, pp. 738–759.
*   J. Zhang, D. Tao, “Empowering things with intelligence: a survey of progress, and opportunities,” `Internet of Things`, vol. 8, no. 10, pp. 7789.
*   F. Liang, C. Qian, W. Hatcher, “Search engine for vision, and opportunities,” `IEEE Access`, vol. 7, pp.
*   A. Abraham, W. Yu, D. Griffith, and N. Golmie, “A survey on industrial of things,” `IEEE Access`, vol. 6, pp.
*   M. Mayhew, C. Chen, G. Gervais, and R. Roaux, “Machine learning for neuro,” `Frontiers in Neuro`, vol. 8.
*   A. Afasyev, K. Park, F. Chen, and M. Shafique, “What’s in data?: Survey for current trends, challenges, and the road ahead,” `Proceedings of IEEE`.
*   S. Shann, B. Chen, K. Lu, and W. Yu, “A survey of deep learning: platforms, applications and,” `Computer Communication`, vol. 44, no. 3, pp. 63–74.
*   L. Zhang, X. Fu, Q. Yang, and W. Yang, “Towards data-driven communication,” `NDN`.
*   W. Lu, Y. Yang, F. Liang, and W. Yang, “A survey on big data market: pricing, trading and protection,” `IEEE Access`, vol. 6, pp. 15132–15154.
*   F. Liang, C. Gao, F. Liang, and K. Hua, “Towards efficient and intelligent internet of things,” `IEEE Access`, 2021.
*   H. Liang, L. Burgess, W. Liao, and C. Lu, “Deep learning assist iot search for disaster assessment,” 2021. [Online]: to published.
*   X. Yang, K. Lingshuang, L. Zhi, C. Yuling, L. Yanmiao, Z. Hongliang, G. Mingcheng, H. Haixia, and W. Chunhua, “Machine learning and deep learning methods for cybersecurity,” `IEEE Access`, vol. 6, pp. 35365–35381, 2018.
*   T. G. Dietterich, “Steps toward robust artificial intelligence,” `AI Magazine`, vol. 38, no. 3, pp. 3–24, 2017.
*   M. Capra, B. Bussolino, A. Marchisio, G. Masera, and M. Shafique, “Hardware and software optimizations for accelerating deep neural networks: Survey for current trends, challenges, and the road ahead,” `IEEE Access`, vol. 8, pp. 225134–225180, 2020.
*   J. M. Helm, A. M. Swiergosz, H. S. Haeberle, J. M. Karnuta, J. L. Schaffer, V. E. Krebs, A. I. Spitzer, and P. N. Ramkumar, “机器学习与人工智能：定义、应用与未来方向.” Current Reviews in Musculoskeletal Medicine, vol. 13, no. 1, p. 69, 2020.
*   N. Spring, R. Mahajan, and D. Wetherall, “使用 rocketfuel 测量 isp 拓扑,” ACM SIGCOMM Computer Communication Review, vol. 32, no. 4, pp. 133–145, 2002.
*   P. H. Swain and H. Hauska, “决策树分类器：设计与潜力,” IEEE Transactions on Geoscience Electronics, vol. 15, no. 3, pp. 142–147, 1977.
*   B. Scholkopf, K.-K. Sung, C. J. Burges, F. Girosi, P. Niyogi, T. Poggio, and V. Vapnik, “带有高斯核的支持向量机与径向基分类器的对比,” IEEE transactions on Signal Processing, vol. 45, no. 11, pp. 2758–2765, 1997.
*   C. Cortes and V. Vapnik, “支持向量机,” Machine learning, vol. 20, no. 3, pp. 273–297, 1995.
*   L. E. Peterson, “K-近邻,” Scholarpedia, vol. 4, no. 2, p. 1883, 2009.
*   T. K. Ho, “随机决策森林,” in Proceedings of 3rd international conference on document analysis and recognition, vol. 1. IEEE, 1995, pp. 278–282.
*   P. Geurts, D. Ernst, and L. Wehenkel, “极随机树,” Machine learning, vol. 63, no. 1, pp. 3–42, 2006.
*   L. Meier, S. Van De Geer, and P. Bu¨hlmann, “逻辑回归的组 lasso,” Journal of the Royal Statistical Society: Series B (Statistical Methodology), vol. 70, no. 1, pp. 53–71, 2008.
*   G. F. Riley and T. R. Henderson, “ns-3 网络仿真器,” in Modeling and tools for network simulation. Springer, 2010, pp. 15–34.
*   A. Afanasyev, I. Moiseenko, L. Zhang et al., “ndnsim: 用于 ns-3 的 Ndn 仿真器,” 2012.
*   F. Pedregosa, G. Varoquaux, A. Gramfort, V. Michel, B. Thirion, O. Grisel, M. Blondel, P. Prettenhofer, R. Weiss, D. Dubourg et al., “Scikit-learn: Python 机器学习,” the Journal of machine Learning research, vol. 12, pp. 2825–2830, 2011.
*   Y. Xin, Y. Li, W. Wang, W. Li, and X. Chen, “ndn 中一种新型兴趣洪泛攻击检测与防御方案,” in 2016 IEEE Global Communications Conference (GLOBECOM). IEEE, 2016, pp. 1–7.
*   F. Scarselli, M. Gori, A. C. Tsoi, M. Hagenbuchner, and G. Monfar- dini, “图神经网络模型,” IEEE transactions on neural networks, vol. 20, no. 1, pp. 61–80, 2008.
*   H. Xu, W. Yu, X. Liu, D. Griffith, and N. Golmie, “针对工业物联网的数据完整性攻击研究,” in 2020 IEEE Intl Conf on Dependable, Autonomic and Secure Computing, Intl Conf on Pervasive Intelligence and Computing, Intl Conf on Cloud and Big Data, Intl Conf on Cyber Science and Technology (DASC/PiCom/CBciTech), 2020, pp. 21–28.
*   H. Dai, Y. Wang, J. Fan, and B. Liu, “通过兴趣回溯缓解 ndn 中的 ddos 攻击,” in 2013 IEEE Conference on Computer Communications (INFOCOM).
*   P. Gasti, G. Tsudik, E. Uzun, and L. Zhang, “命名数据网络中的 dos 和 ddos,” in 2013 22nd International Conference on Computer Communication and Networks (ICCCN), pp. 1–7.
*   T. Zhi, H. Luo, and Y. Liu, “基于 gini 的 ndn 兴趣防御,” IEEE Communications Letters, vol. 22, no. 3, pp. 538–541.
*   A. Compagno, M. Conti, P. Gasti, and G. Tsudik, “Poseidon: 缓解命名数据网络中的兴趣洪泛 ddos 攻击,” in 38th annual IEEE conference on local networks, 2013, pp. 630–638.
*   R. Doshi, N. Apthorpe, and N. Feamster, “消费物联网设备的机器学习 ddos 检测,” in 2018 IEEE Security and Privacy Workshops (SPW), IEEE, 2018, pp. 29–35.
*   Z. He, T. Zhang, and R. B. Lee, “云端的机器学习 ddos 攻击,” in 2017 IEEE 4th International Conference on Cyber Security and Cloud (CSCloud), IEEE, 2017, pp. 114–120.
*   R. Santos, D. Souza, W. Santo, A. Ribeiro, and E. Moreno, “检测 sdn 中 ddos 攻击的机器学习算法,” Concurrency and Computation: Practice and Experience, vol. 32, no. 16, p. e5402, 2020.
*   A. Afanasyev, P. Mahadevan, I. Moiseenko, E. Uzun, and L. Zhang, “命名数据网络中的兴趣洪泛攻击与应对措施,” in 2013 IFIP Networking Conference, pp. 1–9.
*   H. Khelifi, S. Luo, B. Nour, H. Moungla, and S. H. Ahmed, “车载网络中基于声誉的 ndn 安全缓存,” in 2018 IEEE Conference on Standards for Communications and Networking (CSCN), IEEE, 2018, pp. 1–6.
*   G. Cheng, Z. Li, J. Han, X. Yao, and L. Guo, “用于高光谱图像分类的分层卷积特征,” IEEE Transactions on Geoscience and Remote Sensing, vol. 56, no. 11, pp. 6712–6722, 2018.
