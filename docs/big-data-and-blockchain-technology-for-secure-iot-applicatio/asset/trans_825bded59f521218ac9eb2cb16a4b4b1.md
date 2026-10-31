
最初，两个流媒体流表现出相似的行为（尽力而为），导致平均PSNR值相当。垂直黑线表示QoS-App在Floodlight控制器中下载并配置的点。如预期，在QoS-App配置后，交换机的行为会自动调整以识别流并分配不同的QoS策略。因此，h2–h7流量的PSNR水平优于h1–h8流。在此情况下，w-QoS的平均PSNR为26.54 dB，而w/o-QoS流的平均值为23.73 dB。

图中和实验中出现的一个明显下降表明，这种意外效应主要由该时期的快速运动场景引起。这些场景期间网络负载增加导致PSNR下降。

使用w-QoS时，平均SSIM为0.814，而w/o-QoS流媒体时为0.738。结果表明，控制器可以实时调整网络行为和数据流平衡以满足用户需求。

## 2.5 结论

本工作研究了SDN和NFV范式在物联网环境中带来的益处，并提出了一种专为物联网网络设计的SDN/NFV架构。实验评估了控制器在ITSCO 2018 – 物联网与智慧社区专题会议背景下动态管理网络行为的能力。基于Mininet的测试拓扑和视频流分析表明，Floodlight控制器能够实时修改不同流的QoS/QoE。因此，未来的研究挑战涉及在物联网环境中实现平衡并编排虚拟资源。此外，优化SDN/NFV架构中实时流媒体的算法也是一项重大挑战。

## 参考文献

- 1. R. Bruschi, P. Lago, G. Lamanna, C. Lombardo, and S. Mangialardi. 2016. OpenVolcano：一种面向雾计算的开源软件平台。在第28届国际电讯业务大会论文集，德国第2卷，第22–27页。
- 2. P. Bull, R. Austin, E. Popov, M. Sharma, and R. Watson. 2016. 基于流的物联网设备安全，使用SDN网关。在2016年IEEE第4届未来物联网与云国际会议（FiCloud’16）论文集。IEEE，奥地利维也纳，第157–163页。
- 3. R. Ranjan, D. Pandey, A. K. Rai, D. Gupta, P. Singh, P. R. Kumar, and S. N. Mohanty. 2023. 一种用于情感分类的流形级混合深度学习方法，采用自回归模型。《应用科学》，第13卷，第5期，第3091页。
- 4. S. Chakrabarty, D. W. Engels, and S. Thathapudi. 2015. 面向物联网的黑SDN。在2015年IEEE第12届移动自组织与传感器系统国际会议论文集。IEEE，美国德克萨斯州达拉斯，第190–198页。
- 5. H.-L. Chen and F. J. Lin. 2019. 基于Kubernetes使能的NFV MANO架构的可扩展物联网/M2M平台。在2019年物联网国际会议（iThings'19）及IEEE绿色计算与通信（GreenCom'19）与IEEE网络物理社会计算（CPSCom'19），以及IEEE智能数据（SmartData'19）论文集。IEEE，美国佐治亚州亚特兰大，第1106–1111页。
- 6. N. Arivazhagan, K. Somasundaram, G. B. Mohammad, P. R. Kumar, et al. 2022. 使用混合蛾群火焰优化与深度神经网络算法的云-健康物联网（IOHT）任务调度，用于电子医疗系统。《科学编程》，第2022卷，第1–12页。
- 7. J. H. Cox, J. Chung, S. Donovan, J. Ivey, R. J. Clark, G. Riley, and H. L. Owen. 2017. 推进软件定义网络：综述。《IEEE Access》，第5卷，第25487–25526页。
- 8. P. R. Kumar, G. B. Mohammad, and P. Dileep. 2021. 使用最小二乘法的实时心率监测系统。《罗马尼亚细胞生物学学会年刊》，第25卷，第6期，第16302–16308页。
- 9. S. Dawson-Haggerty, J. Ortiz, J. Trager, D. Culler, and R. H. Katz. 2012. 节能与“软件定义”建筑。《IEEE计算机设计与测试》，第29卷，第4期，第56–57页。
- 10. Y. Demiral and M. Demirci. 2018. 超visor对虚拟网络性能影响的研究。在2018年第26届信号处理与通信应用会议（SIU'18）论文集。IEEE，土耳其伊兹密尔，第1–4页。
- 11. G. B. Mohammad, Selvarajan Shitharth, and P. R. Kumar. 2021. 用于URL钓鱼检测的集成机器学习模型。《国际网格与分布式计算期刊》，第14卷，第1期，第513–529页。
- 12. S. Din, M. M. Rathore, A. Ahmad, A. Paul, and M. Khan. 2017. SDIoT：用于智能城市大数据分析的软件定义物联网。在2017年IEEE第42届局域网研讨会（LCN Workshops'17）论文集。IEEE，新加坡，第175–182页。
- 13. P. R. Kumar. 2018. 使用感应耦合的无线移动充电器。《新兴技术与创新研究期刊（JETIR）》，第5卷，第10期，第40–44页。
- 14. L. Galluccio, S. Milardo, G. Morabito, and S. Palazzo. 2015. SDN-WISE：无线传感器网络有状态SDN解决方案的设计、原型制作与实验。在2015年IEEE计算机通信会议（INFOCOM）。IEEE，中国香港，第513–521页。
- 15. S. Costanzo, L. Galluccio, G. Morabito, and S. Palazzo. 2012. 软件定义无线网络：释放SDN的潜力。在2012年欧洲软件定义网络研讨会（EWSDN）。IEEE，德国达姆施塔特，第1–6页。
- 16. T. Luo, H.-P. Tan, and T. Q. Quek. 2012. Sensor OpenFlow：实现软件定义无线传感器网络。《IEEE通信快报》，第16卷，第11期，第1896–1899页。
- 17. B. Shilpa, P. R. Kumar, and R. K. Jha. 2023. 密集室内LoRa网络中用于干扰缓解的扩频因子优化。*IEEE IAS Global Conference on Emerging Technologies (GlobConET)*, London, UK pp. 1–5。
- 18. P. Thubert, M. R. Palattella, and T. Engel. 2015. 6TiSCH集中调度：当SDN遇见物联网。在*IEEE通信与网络标准化会议论文集（CSCN15）*。东京，日本。
- 19. S. H. Yeganeh, A. Tootoonchian, and Y. Ganjali. 2013. 关于软件定义网络的可扩展性。*IEEE Communications Magazine*，第51卷，第2期，第136–141页。
- 20. A. Al-Fuqaha, M. Guizani, M. Mohammadi, M. Aledhari, and M. Ayyash. 2015. 物联网：使能技术、协议和应用综述。*IEEE Communications Surveys & Tutorials*，第17卷，第4期，第2347–2376页。
- 21. P. Berde, M. Gerola, J. Hart, Y. Higuchi, M. Kobayashi, T. Koide, B. Lantz, B. O'Connor, P. Radoslavov, W. Snow, et al. 2014. ONOS：迈向开放的分布式SDN操作系统。在*第三届软件定义网络热点主题研讨会论文集*。ACM，美国伊利诺伊州芝加哥，第1–6页。
- 22. J. Medved, R. Varga, A. Tkacik, and K. Gray. 2014. Opendaylight：迈向模型驱动的SDN控制器架构。在*2014年IEEE第15届世界无线、移动多媒体网络国际研讨会*。IEEE，澳大利亚新南威尔士州悉尼，第1–6页。
- 23. P. R. Kumar and B. Shilpa. 2023. 基于物联网的智能医疗系统，采用边缘智能计算。在S. Satpathy, S. N. Mohanty, and S. Potluri（编），*探索医疗保健中边缘智能的格局*。CRC Press：美国佛罗里达州博卡拉顿，第31–46页。
- 24. R. Mijumbi, J. Serrat, J.-L. Gorricho, N. Bouten, F. De Turck, and R. Boutaba. 2015. 网络功能虚拟化：现状与研究挑战。*IEEE Communications Surveys & Tutorials*，第18卷，第1期，第236–262页。
- 25. N. Pazos, M. Muller, M. Aeberli, and N. Ouerhani. 2015. ConnectOpen：物联网设备的自动集成。*2015 IEEE第2届物联网世界论坛*，意大利米兰，第640–644页。
- 26. M. Vögler, J. M. Schleicher, C. Inzinger, S. Nastic, S. Sehic, and S. Dustdar. 2015. LEONORE：资源受限物联网部署的大规模供给。*Proceedings - 9th IEEE International Symposium on Service-Oriented System Engineering, IEEE SOSE 2015*，美国加利福尼亚州旧金山，第30卷，第78–87页。
- 27. B.-S. P. Lin, F. J. Lin, and L.-P. Tung. 2016. 5G移动宽带在物联网、大数据、云和SDN发展中的作用。《Communications and Network》，第8卷，第1期，第9–21页。
- 28. B.-S. Paul Lin, Y.-B. Lin, L.-P. Tung, and F. J. Lin. 2018. 通过将SDN/NFV应用于5G和物联网探索网络软warization和虚拟化。《Transactions on Networks and Communications》，第6卷，第4期，第1–13页。
- 29. D. Sinh, L. Le, L. Tung, and B. P. Lin. 2017. 将SDN/NFV应用于5G和物联网的挑战。*第14届IEEE - VTS亚太无线通信研讨会（APWCS）*，韩国仁川。
- 30. D. Sinh, L. V. Le, B. S. P. Lin, and L. P. Tung. 2018. SDN/NFV：部署物联网网络基础设施的新方法。*2018年第27届无线与光通信会议*，第1–5页。
