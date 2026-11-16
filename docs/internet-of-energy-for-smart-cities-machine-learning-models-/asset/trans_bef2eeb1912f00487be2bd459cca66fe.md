

![](img/617e854c2620a5a4bed0116cef33155a_185_0.png)

图 6.14 修改后的 IT-IAP 以突出相关的能量存储系统数据流和实体

## 6.6.2 IoE 硬件安全

对于某些指定的硬件组件，IEEE 引入了已识别的标准建议。例如 IEEE 1686 [41] 这类建议，介绍了智能电子设备（IED）应提供的功能和特性，并适配关键基础设施保护（CIP）计划，该标准也引入了此类建议。它还涉及与从 IED 进行的访问、操作、配置、固件修订和数据检索相关的安全程序。但是，该标准未涉及远程保护所指的电力系统保护（PSP）目的的通信。IEEE 1689 定义了保护串行监控控制与数据采集（SCADA）以及与远程终端单元或智能电子设备维护端口通信的通用要求。

此外，IEEE 1689 概述了为旧版控制系统追加安全性的要求，以最大限度地减少所需更改。IEEE P1711 是一种针对电力行业变电站通信中使用串行链路的加密协议的试用标准 [42]。该标准适用于 SCADA 系统，特别是 SCADA 主站与智能电子设备（IED）之间的通信。IEEE 1402 指南识别并讨论了在电力供应变电站建设、运行（自然灾害除外）和维护期间人为干预相关的安全问题 [43]。它还记录了减轻入侵的方法和设计。然而，如图 6.15 所述的 IEC 62351 标准族，描绘了安全电力系统的架构并标准化了其协议和组件。

## 6.7 结论

能源系统和应用中 IoT 技术的新兴采用被称为 IoE，它涉及将信息通信技术与涵盖发电、变换、存储、分配及终端设备消耗在内的不同能源或电力系统组件进行集成。图 6.16 显示了能源网络不同层级的 IoE 设计层和架构。ICT 的发展迅速增长，随之引入了相应的功能，云计算、雾计算或边缘计算以及区块链是基于互联网应用的现代解决方案。这些 ICT 技术可以为 IoE 实世界实现引入高效、可靠、安全和灵活的基础设施，从而定义了 IoE 架构。标准、建议和最佳实践是从互操作性、可扩展性、安全性和隐私等多种角度实现现代技术应用的最佳和高效设计与部署所需的重要文件。这些标准由国际协会和机构引入。

![](img/617e854c2620a5a4bed0116cef33155a_186_0.png)

图 6.15 IEC 62351 安全标准及其与 IEC TC57 标准的相互关系

| | 分散式能源发电 | 输电网络 | 能源量测量 | 终端消耗 |
|---|---|---|---|---|
| 应用级别 | IEC TS 62351（数据和通信安全）<br>IEC 61968（将应用集成到电力供应设施中）<br>IEC 61400-25（风力发电厂）<br>IEC 61850-7-420（分散式能源发电） | IEC 62443（安全）<br>IEC 61970（API 能源管理系统）<br>IEC TR 62325（ebIXML） | | ISO/IEC 14543-3-1（KNX） |
| 应用和传输级别 | IEC 61950（站所自动化）<br>3GPP | | IEC 62055（电表预付费）<br>IEC 62056（DLMS/COSEM）<br>EN 13757-2（M-BUS）<br>EN 13757（M-BUS）<br>ZigBee+ IEEE（2.4 GHz 802.15.4） | ISO/IEC 14543-3（KNX）<br>ISO 16484-5（BacNet）<br>EN 14908-x（LON） |
| 传输和通信媒介级别 | TCP/IP<br>IEC 60255（保护装置） | WiMax<br>CDMA<br>Ethernet | IEC 61334（PLC）<br>GPRS/GSM<br>DSL | ISO/IEC 14543-3-5 至 8（KNX）<br>BacNet/IP<br>LAN<br>W-LAN |

图 6.16 能源网络层级 IoE 设计架构

## 参考文献

- 1. J. R. 2008. 第三次工业革命. Engineering & Technology, vol. 3, pp. 26-27.
- 2. Y. R. Kaife, K. Mahmud, S. Morsalin, and G. E. Town. 2016. 迈向互联网能源. IEEE 国际电力系统技术会议 (POWERCON), pp. 1-6.
- 3. J. Cao and M. Yang. 2013. 能源互联网——迈向智能电网 2.0. 2013 年第 4 届网络与分布式计算国际会议 (ICNDC), pp. 105-110.
- 4. A. Q. Huang, et al. 2011. 未来可再生电能输送和管理 (FREEDM) 系统：能源互联网. Proceedings of the IEEE 99.1, pp. 133-148.
- 5. C. Block. 2016. 能源互联网，面向未来能源市场的 ICT. Available at: http://www.iese.fraunhofer.de/content/dam/iese/en/media center/documents/BDL_initiative_IoE_Us-IdE-Broschuere.tcm27-45653.pdf
- 6. Z. Liu. 2015. 全球能源互联. China Electric Power Press, Beijing.
- 7. R. Abe, R.H. Taoka, and D. McQuilkin. 2011. 数字电网：未来智能电网的通信电网. IEEE Transactions on Smart Grid 2.2, vol. 2, no. 2, pp. 399-410.
- 8. M. Moness and A. M. Moustafa. 2016. 风能转换系统的网络物理进展与挑战调查：能源互联网的前景. IEEE Internet of Things Journal, vol. 3, pp. 134-145.
- 9. M. A. Hannan, M. Faisal, P. J. Ker, L. H. Mun, K. Parvin, T. M. I. Mahlia, et al. 2018. 基于能源互联网的建筑能源管理系统综述：问题与建议. IEEE Access, vol. 6, pp. 38997-39014.
- 10. Z. Lyu, H. Wei, X. Bai, and C. Lian. 2020. 能源管理系统的微服务架构. IEEE Systems Journal, 14(4), 5061-5072, pp. 1-12.
- 11. J. A. Reddy and K. S. Swarup. 2003. 电力系统安全能源管理系统中的开放分布式客户端服务器模型. TENCON 2003. 亚太地区融合技术会议, vol. 3, pp. 981-985
- 12. E. Hossain, Z. Han, and H. V. Poor. 2012. 智能电网通信与网络. Cambridge University Press, Cambridge.
- 13. A. A. Munshi and Y. A. I. Mohamed. 2018. 智能电网大数据分析的数据湖 Lambda 架构. IEEE Access, vol. 6, pp. 40463-40471.
- 14. F. Ma, X. Luo, and E. Litvinov. 2016. ISO 新英格兰电力系统仿真中的云计算——经验与挑战. IEEE Transactions on Smart Grid, vol. 7, pp. 2596-2603.
- 15. M. Feng, L. Xiaochuan, Q. F. Q. Zhang, and E. Litvinov. 2015. 云计算：促进电力系统运行的创新 IT 范式. IEEE Power & Energy Society General Meeting, pp. 1-5.
- 16. D. Yang, H. Wei, Y. Zhu, P. Li, and J. Tan. 2019. 基于虚拟私有云的电力调度自动化系统——架构与应用. IEEE Transactions on Industrial Informatics, vol. 15, pp. 1756-1766.
- 17. D.J. Hammerstrom_. 2013. 太平洋西北地区智能电网演示交互协调信号. PNWD-4402 Rev X", Batelle—Pacific Northwest Division, Richland, WA, USA.
- 18. J. Haack, B. Akoyl, B. Carpenter, C. Tews, and L. Foglesong. 2013. Voltron TM：智能电网的代理平台. International Conference on Connected Vehicles and Expo (ICCVE), pp. 1367-1368.
- 19. J. Hagerman_. 2015. EERE 与建筑到电网集成. DOE Building Technologies Office, Washington.
- 20. F. Wurtz and B. Delinchant. 2017. “智能建筑”集成于“智能电网”中：利用物理模型和带有“人在回路”方法的优化实现能源转型的关键挑战. Comptes Rendus Physique, vol. 18, pp. 428-444.
- 21. S. Widergren, J. Fuller, C. Marinovici, and A. Somani. 2014. 居民交互控制演示. IEEE Innovative Smart Grid Technologies (ISGT) Conference, pp. 1-5.
- 22. D. Forfia, M. Knight, and R. Melton. 2016. 山顶视野：基于 GridWise 交互能源框架构建实践共同体. IEEE Power and Energy Magazine vol. 14, pp. 25-33.
- 23. M. H. Y. Moghadam and A. Leon-Garcia. 2018. 基于雾计算的交互能源管理系统能源互联网架构. IEEE Internet of Things Journal, vol. 5, pp. 1055-1069.
- 24. R. Fu, F. Gao, R. Zeng, J. Hu, Y. Luo, and L. Qu. 2017. 能源互联网的大数据和云计算平台. China International Electrical and Energy Conference (CIEEC), pp. 681-686.
- 25. J. Gedeon, J. Heuschkel, L. Wang, and M. Mühlhäuser. 2018. 雾计算：当前研究与未来挑战. 1. GI/ITG KuVS Fachgespräche Fog Computing, At Darmstadt, Germany.
- 26. K. Shahryari and A. Anvari-Moghaddam. 2017. 基于雾计算和云计算的能源互联网需求侧管理. IEEE International Conference on Internet of Things (iThings), pp. 931-936.
- 27. A. Miglani, N. Kumar, V. Chamola, and S. Zeadally. 2020. 能源互联网管理的区块链：综述、解决方案与挑战. Computer Communications, vol. 151, pp. 395-418.
- 28. K. Wang, X. Hu, H. Li, P. Li, D. Zeng, and S. Guo. 2017. 面向可持续性的能源互联网通信调查. IEEE Transactions on Sustainable Computing, vol. 2, pp. 231-254.
- 29. J. Wu and N. Tran. 2018. 区块链技术在可持续能源系统中的应用：概述. Sustainability Journal, MDPI, Sustainability, 10(9), 3067.
- 30. A. Annaswamy. 2013. IEEE 智能电网控制愿景：2030 年及以后路线图. IEEE Vision for Smart Grid Control: 2030 and Beyond Roadmap, pp. 1-12.
- 31. S. Lee, B. Kim, M. Oh, Y. Jeon, and S. Choi. 2013. 智能公用事业服务的 IEEE 802.15.4g 无线通信平台实现. IEEE 3rd International Conference on Consumer Electronics in Berlin (ICCE-Berlin), pp. 287-289.
- 32. B. K. Munj and S. K. Patra. 2013. IEEE 802.15.4 的 ZigBee 基带收发机系统 FPGA 实现. In Advances in Computing, Communication, and Control. Berlin, Heidelberg, Springer, pp. 465-474.
- 33. S. S. Lee, B. Kim, J. Y. Kim, S. Choi, and C. Kim. 2013. 面向智能电网和 CE 的基于 IEEE 802.15.4g SUN OFDM 的 RF CMOS 收发机. IEEE International Conference on Consumer Electronics (ICCE), pp. 520-521.
- 34. Y. Ma, A. Cherian, and D. Wobschall. 2017. 组合式 ISO/IEC/IEEE 21451-4 和 -2 数据采集模块. IEEE Sensors Applications Symposium (SAS), pp. 1-6.

