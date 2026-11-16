

![](img/1752b062af2760b8561f6faaf183b3d0_93_0.png)

**图 5.** 超分辨率计算结果。请注意，低分辨率模型为双立方插值，没有隐藏层。(a) 图像 #1（低分辨率），(b) 图像 #1（高分辨率），(c) 图像 #2（低分辨率），(d) 图像 #2（高分辨率），(e) 图像 #3（低分辨率）和 (f) 图像 #3（高分辨率）。

为了验证超分辨率模型的性能，图 5 展示了使用真实图像的超分辨率计算结果。如图所示，如果超分辨率模型具有更多隐藏层，则其性能更好，如图 5b、图 5d 和图 5f 所示。对于无隐藏层的超分辨率计算，本文采用双立方插值，如图 5a、图 5c 和图 5e 所示。最后，这些结果表明，我们针对自适应深度学习平台考虑的拉普诺夫控制算法可以根据队列积压大小信息产生不同的超分辨率性能。

## 新兴应用

如前所述，拉普诺夫优化框架旨在实现时效平均效用最大化，同时保持队列稳定性；且该理论具有可扩展性；因此广泛适用 [2]。因此，基于该算法存在许多应用，如下所示。

### 自适应视频流

Kim 等人 [3, 5] 设计了一种动态控制算法，用于无线视频网络中在发送缓冲区稳定性约束下实现时效平均流媒体质量（即峰值信噪比 (PSNR)）最大化。Koo 等人 [6, 7] 还提出了一种基于 HTTP 的动态自适应流媒体（DASH）新机制，用于在考虑电池状态、LTE 数据配额以及混合 LTE 和 WiFi 网络稳定性的前提下最大化视频流媒体质量。

### 网络

Neely 等人 [8] 提出了一种新型动态多跳路由算法，用于在受队列稳定性约束的无线自组织和传感器网络中进行节能数据/分组转发。

### 安全应用：监控监测

Mo 等人 [9] 为基于 CCTV 的分布式监控应用设计了一种深度学习框架。在该系统中，存在多个深度学习框架；且每个深度学习模型都有其自身配置。在此情况下，复杂性与性能之间存在权衡。因此，所提出的基于 CCTV 的监控算法根据系统中的队列积压自适应选择深度学习模型，以在 CCTV 队列稳定性约束下最大化识别性能。Kim 等人 [10] 还为基于 CCTV 的监控平台设计了一种新型面部识别深度学习框架。该系统不是拥有多个深度学习模型，而是具有一个学习系统（基于 OpenFace 开源软件库）并控制 CCTV 摄像机的采样率。最后，所提出的决策算法动态选择 CCTV 采样率，以在 CCTV 队列稳定性约束下最大化识别性能。

### 其他

[11] 说明了基于拉普诺夫优化的动态控制算法在动态强化学习策略设计中的应用。此外，[12, 13] 介绍了在股票市场定价和智能电网中使用拉普诺夫优化框架的自适应控制算法。

## 结论

本章介绍了一种动态控制决策算法，该算法受拉普诺夫优化理论启发，适用于效用/性能与延迟之间存在权衡的情况。因此，动态决策算法旨在实时深度学习平台中实现时效平均效用最大化（或惩罚最小化）。如前所述，基于拉普诺夫优化的算法具有可扩展性、与硬件/系统无关、可自配置且低复杂度。因此，它可应用于各种新兴应用，例如视频流、无线网络、安全应用和智能电网应用。

## 致谢

该工作得到韩国国家研究基金会（2019R1A2C4070663, 2019M3E4A1080391）的支持。J. Kim 为通信作者（电子邮件：joongheon@korea.ac.kr）。

## 参考文献

- 1. Kim D, Kwon J, Kim J. 基于拉普诺夫控制的稳定实时深度学习平台中低复杂度在线模型选择的奖励最大化。In: Proceedings of the IEEE International Conference on Systems, Man, and Cybernetics (SMC ‘18); 7–10 October, 2018; Miyazaki, Japan: IEEE; 2018. pp. 4363-4368
- 2. Neely M. 通信和排队系统中的随机网络优化。Vermont, USA: Morgan & Claypool; 2010
- 3. Kim J, Caire G, Molisch A. 面向设备到设备视频传输的质量感知流媒体与调度。IEEE/ACM Transactions on Networking. 2016;24:2319-2331. DOI: 10.1109/TNET.2015.2452272
- 4. Choi M, Kim J, Moon J. 面向联网车辆接收机设计中队列稳定字误差率最小化的自适应检测器选择。IEEE Transactions on Vehicular Technology. 2018;67:3635-3639. DOI: 10.1109/TVT.2017.2776327
- 5. Kim J, Meng F, Chen P, Egilmez H, Bethanabhotla D, Molisch A, 等人. 演示：面向设备到设备移动平台的自适应视频流。In: Proceedings of the ACM International Conference on Mobile Computing and Networking (MobiCom ‘13), 30 September–4 October, 2013; Miami, FL, USA: IEEE; 2013
- 6. Koo J, Yi J, Kim J, Hoque M, Choi S. REQUEST: 面向资源受限多宿主智能手机的基于 HTTP 的无缝动态自适应流媒体。In: Proceedings of the ACM International Conference on Multimedia (MM ‘17), 23–27 October, 2017; Mountain View, CA, USA: IEEE; 2017
- 7. Koo J, Yi J, Kim J, Hoque M, Choi S. 面向智能手机资源限制的 LTE/Wi-Fi 集成网络中无缝动态自适应流媒体。IEEE Transactions on Mobile Computing. 2019;18:1647-1660. DOI: 10.1109/TMC.2018.2863234
- 8. Neely M. 时变无线网络的能量最优控制。IEEE Transactions on Information Theory. 2006;52:2915-2934. DOI: 10.1109/TIT.2006.876219
- 9. Kim J, Mo YJ, Lee W, Nyang D. 监控应用中稳定并行深度学习架构的动态安全级别最大化。In: Proceedings of the IEEE Symposium on Privacy-Aware Computing (PAC ‘07); 1–3 August, 2017; Washington DC, USA: IEEE; 2017. pp. 192-193
- 10. Kim D, Kim J, Bang J. 基于拉普诺夫优化的可靠自适应面部识别框架。In: Proceedings of ACM Symposium on Operating Systems Principles (SOSP) AI Systems Workshop (AISys'17), 28 October, 2017; Shanghai, China: ACM; 2017
- 11. Neely M, Supittayapornpong S. 延迟约束无线调度的动态马尔可夫决策策略。IEEE Transactions on Automatic Control. 2013;58:1948-1961. DOI: 10.1109/TAC.2013.2256682
- 12. Neely M. 基于随机网络优化的股票市场交易。In: Proceedings of IEEE Conference on Decision and Control (CDC '10), 15–17 December, 2010; Atlanta, GA, USA: IEEE; 2010
- 13. Neely M, Tehrani A, Dimakis A. 面向延迟容忍消费者的可再生能源分配高效算法。In: Proceedings of IEEE International Conference on Smart Grid Communication (SmartGridComm '10), 4–6 October, 2010; Gaithersburg, MD, USA: IEEE; 2010

## 第 4 章

## 基于指数动量深度卷积神经网络的高光谱数据分类深度学习

Qi Yue^{1,2,3} and Caiwen Ma^1

^1 中国科学院西安光学精密机械研究所, 西安 710119, 中国
^2 中国科学院大学, 北京 100039, 中国
^3 西安邮电大学, 西安 710121, 中国

## 摘要

分类是高光谱遥感领域的热门话题。在过去几十年中，大量努力已集中在分类问题上。大多数现有研究和研究工作都遵循基于传统模式识别范式，该范式基于

> 引用：Qi Yue, Caiwen Ma, “基于指数动量深度卷积神经网络的高光谱数据分类深度学习”, Journal of Sensors, vol. 2016, Article ID 3150632, 8 页, 2016. https://doi.org/10.1155/2016/3150632. 版权：© 2016 作者。这是一篇在知识共享署名许可下分发的开放获取文章，该许可允许在任何媒介中不受限制地使用、分发和复制，前提是原始作品得到正确引用。

