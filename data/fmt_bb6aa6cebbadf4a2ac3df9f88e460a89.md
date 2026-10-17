
此外，为了缓解无线传感器网络中消息的篡改和伪装，采用了哈希函数、数字签名和`MAC`（消息认证码）等传统方法。然而，为了保持数据的新鲜性并防御重放攻击，会在消息中附带时间戳（Wang, et al., 2006）。

## 表 4. 应对数据包丢弃和修改攻击的各种分层路由协议总结

| 协议 | 安全属性 | 缓解的攻击 |
| :--- | :--- | :--- |
| SLEACH (Islam, Islam, & Islam, 2007) | 完整性、真实性 | 重放/修改、选择性转发、陷阱 |
| F-LEACH (Zheng & Hu, 2009) | 保密性、完整性、数据新鲜性、真实性 | 重放/修改、Sybil攻击 |
| R-LEACH (Sundararajan & Arumugam, 2015) | 保密性、完整性、真实性 | 重放/修改、选择性转发、陷阱、Sybil攻击、蠕虫洞 |
| Sec-LEACH (Sharma & Jena, 2011) | 保密性、完整性、数据新鲜性、真实性 | 重放/修改、选择性转发、Sybil攻击 |
| SS-LEACH (Sharma & Jena, 2011) | 保密性、完整性、真实性 | 重放/修改、选择性转发、Sybil攻击 |
| SRPSN (Ouaifa, Mustapha, Salah-dinne, & Jalal, 2016) | 保密性、完整性、真实性 | 重放/修改、选择性转发 |
| LHA-SP (Oliveira, Wang, & Loureiro, 2005) | 保密性、真实性 | - |
| ESMR (Vijendran & Grpsy, 2014) | 保密性 | 重放/修改 |
| SRPBCG (Ouaifa, Mustapha, Salah-dinne, & Said, 2016) | 保密性、真实性 | 重放/修改 |
| M. Bohang et al. | 完整性、真实性 | 重放/修改 |
| SHEER (Ouaifa, Mustapha, Salah-dinne, & Jalal, 2016) | 保密性、完整性、数据新鲜性、真实性 | 重放/修改、选择性转发、Sybil攻击 |

## 针对传输层攻击的安全防护

该层极易受到洪水攻击、确认伪装和去同步攻击的影响。洪水攻击可以通过连接认证来防止。对于去同步攻击，需要对每种类型的网络数据包（例如，控制包和数据包）进行认证。头部或完整数据包认证可用于防止去同步攻击。在此，防火墙可用于保护网络免受洪水和去同步攻击。防火墙旨在为两个数据传输节点提供可靠、经过认证且安全的连接。文献中提出了AEGIS (Hossain & Raghunathan, 2010) 和 S_Firewall (Ma, Yi, Zhong, & Zhang, 2006) 两种防火墙，旨在提供节点间的安全数据传输并过滤掉虚假的入站和出站流量。此外，在(Hussain, et al., 2019)中，作者提出了一种名为SFADBE的基于AI的方法来应对无线传感器网络中的SYN洪水攻击。在此，也使用谜题算法来限制虚假连接的创建。在谜题算法中，如果任何用户打算建立连接，他/她在建立新连接之前必须解决一个谜题。为每个连接解决谜题需要时间；因此，对手将无法快速打开足够多的连接来压倒网络节点（Wang, et al., 2006）。最后，在(Almulhim & Zaman, 2018)中，作者提出了一种轻量级认证方案。该方案基于网络节点和BS之间的会话密钥协商。他们的方案特别能够保护网络免受中间人攻击和伪装攻击。

## 结论

本章详细阐述了无线传感器网络及其架构和关键应用。本章的主要目标是提供有关WSN安全问题的综合详细信息。根据这一目标，本章首先描述了WSN安全的主要和次要目标，并讨论了大多数损害和违反WSN安全的攻击。本章最后提供了一些用于保护WSN免受所讨论攻击的对策。

## 参考文献

- Almulhim, M., & Zaman, N. (2018). *Proposing secure and lightweight authentication scheme for IoT based E-health applications*. Paper presented at the 2018 20th International Conference on Advanced Communication Technology (ICACT).
- Almusaylim, Z. A., & Zaman, N. (2019). A review on smart home present state and challenges: Linked to context-awareness internet of things (IoT). *Wireless Networks, 25*(6), 3193–3204. doi:10.1007/s11276-018-1712-5
- Alsoufi, D., Elieithy, K. M., Abuzaghleh, T., & Nassar, A. (2012). *Security in wireless sensor networks- Improving the leap protocol*. Academic Press.
- Anwar, Zainal, Abdullah, & Qureshi. (2014). Security Issues and Attacks in Wireless Sensor Network. *World Applied Sciences Journal, 30*(10).
- Bekara, C., & Laurent, M. (2007). *Defending against nodes replication attacks on wireless sensor networks*. Paper presented at the SAR-SSI 2007: 2nd Conference on Security in Network Architectures and Information Systems.
- Brar, S., & Angurala, M. (2016). Review on grey-hole attack detection and prevention. *International Journal of Advance research. Ideas and Innovations in Technology, 2*(5), 1–4.
- Chaitanya, Ayyappa, & Ravindra. (2011). Analysis and Study of Denial of Service Attacks in Wireless Mobile Jammers. *International Journal of Computer Science and Telecommunications, 2*(5).
Chelli, K. (2015). 无线传感器网络中的安全问题：攻击与对策。*世界工程大会论文集*。
Choi, B. G., Cho, E. J., Kim, J. H., Hong, C. S., & Kim, J. H. (2009). *基于WSN中LQI的网格路由的水坑攻击检测机制*。论文发表于2009年国际信息联网会议。
Conti, Mancini, & Mei. (n.d.). 无线传感器网络中克隆攻击的分布式检测。*IEEE 可靠与安全计算学报*。
Deng & Chen (n.d.). *移动无线传感器网络中复制攻击的 mobility 辅助检测*。Academic Press。
Dr, G., & Padmavathi, D. S. (2009). 无线传感器网络中攻击、安全机制与挑战综述。*国际计算机科学与信息安全杂志*, 4(1).
Dr, G., & Padmavathi, M. D. S. (2009). 无线传感器网络中攻击、安全机制与挑战综述。*国际计算机科学与信息安全杂志*, 4(1).
Giri, D., Borah, S., & Pradhan, R. (2018). *检测无线传感器网络中虫洞攻击的方法与措施：综述*。收录于*通信、设备与网络进展* (第855–864页)。Springer。doi:10.1007/978-981-10-7901-6_92
Hossain, M. S., & Raghunathan, V. (2010). *Aegis: 一种轻量级无线传感器网络防火墙*。论文发表于分布式传感器系统国际会议。 10.1007/978-3-642-13651-1_19
Hussain, K., Hussain, S. J., Jhanjhi, N., & Humayun, M. (2019). *基于贝叶斯估计器的SYN泛洪攻击检测 (SFADBE) 用于 MANET*。论文发表于2019年国际计算机与信息科学会议 (ICCIS)。 10.1109/ICCISci.2019.8716416
Islam, J., Islam, M., & Islam, N. (2007). *A-sleach: 一种先进的太阳能感知 LEACH 协议，用于无线传感器网络中的节能路由*。论文发表于第六届国际网络会议 (ICN’07)。 10.1109/ICN.2007.14
Jordao, A., Torres, L. A. B., & Schwartz, W. R. (2018). 基于加速度计数据的人体活动识别的新方法。*信号、图像与视频处理*, 12(7), 1–8. doi:10.1007/s11760-018-1293-x
Karlov, C., Sastry, N., & Wagner, D. (2004). TinySec: 一种用于无线传感器网络的链路层安全架构。*第二届嵌入式网络传感器系统国际会议论文集*。 10.1145/1031495.1031515
Kaur, R., & Kumar, T. (2018). *使用 AODV 协议缓解无线传感器网络中的黑洞攻击和虫洞攻击*。论文发表于2018年 IEEE 智能能源电网工程国际会议 (SEGE)。 10.1109/SEGE.2018.8499473
Khalil, N., Abid, M. R., Benhaddou, D., & Gerndt, M. (2014). *面向物联网的无线传感器网络*。论文发表于智能传感器、传感器网络与信息处理 (ISSNIP)，2014年 IEEE 第九届国际会议。 10.1109/ISSNIP.2014.6827681
Khan, Saad, & Xiang. (2013). 无线传感器网络中节点复制攻击的检测与缓解：综述。*国际分布式传感器网络杂志*。
Kirar, V. P. S. (2014). 无线传感器网络中攻击与安全需求综述。*国际计算机、电气、自动化、控制与信息工程杂志*, 8(12), 2198–2203.
Kocakulak, M., & Butun, I. (2017). *面向物联网的无线传感器网络概述*。论文发表于2017年 IEEE 第七届年度计算与通信研讨会 (CCWC)。 10.1109/CCWC.2017.7868374
Lai, B., Kim, S., & Verbaauwede, I. (2002). *无线传感器网络的可扩展会话密钥构建协议*。论文发表于 IEEE 大规模实时与嵌入式系统研讨会 (LARTES)。
Lakshmi, Rao, Mohan, & Kumar. (2013). 使用安全数据包隐藏方法防止无线传感器网络中的干扰攻击。*先进计算机与通信工程研究国际杂志*, 2(9).
Law, Y. W., Palaniswami, M., HoeseL, L. V., Doumen, J., Hartel, P., & Havinga, P. (2009). 针对无线传感器网络 MAC 协议的节能链路层干扰攻击。*ACM 传感器网络学报*, 5(1), 6. doi:10.1145/1464420.1464426
Liu, J. K., Baek, J., Zhou, J., Yang, Y., & Wong, J. W. (2010). 用于无线传感器网络的高效在线/离线基于身份的签名。*国际信息安全杂志*, 9(4), 287–296. doi:10.1007/s10207-010-0109-y
Ma, J., Yi, P., Zhong, Y., & Zhang, S. (2006). *S_Firewall: 无线传感器网络中的防火墙*。论文发表于2006年国际无线通信、网络与移动计算会议。 10.1109/WiCOM.2006.280
Malan, D. J., Welsh, M., & Smith, M. D. (2004). *基于椭圆曲线密码学的 TinyOS 密钥分发公钥基础设施*。论文发表于2004年 IEEE 通信学会第一届传感器与自组通信和网络会议，2004。IEEE SECON 2004。 10.1109/SAHCN.2004.1381904
Malkani, Y., Keerio, A., Mahar, J., Memon, G., & Keerio, H. (2015). 无线传感器网络 (WSN) 中的定位、路由与数据汇聚。*信德大学研究杂志，44*(1).
Messai, M.-L. (2014). *无线传感器网络中攻击的分类*。论文发表于国际电信与应用大会。
Michal, M. (2013). *无线传感器网络的基站* (未发表文凭论文)。Masryk 大学。
Mishra, S., & Thakkar, H. (2012). WSN 特性及 WSN 中的数据聚合技术：综述。*国际工程创新技术杂志*, 1(4), 264–273.
Mptziopoulos, DKonstantopoulos, & Pantziou. (2009). *关于 WSN 中干扰攻击及对策的综述*。论文发表于 IEEE 通信综述与教程。
Mumtaz Qabulio, Y. (2015). 无线传感器网络中的节点复制攻击。* Mehran 大学工程与技术研究杂志，34*(4).
Niculescu, D., & Nath, B. (2003). 基于轨迹的数据包转发及其应用。*第九届移动计算与网络国际会议论文集*。
Oliveira, L. B., Wang, H. C., & Loureiro, A. A. (2005). *LHA-SP: 分层无线传感器网络的安全协议。* 论文发表于2005年 IFIP/IEEE 集成网络管理国际研讨会，2005。 10.1109/INM.2005.1440767
Ouafaa, I., Mustapha, E., Salah-dine, K., & Jalal, L. (2016). *无线传感器网络中安全分层路由协议的深入分析。* 论文发表于2016年工程与管理信息系统国际会议 (ICEMIS)。 10.1109/ICEMIS.2016.7745375
Ouafaa, I., Mustapha, E., Salah-dine, K., & Said, E. H. (2016). 无线传感器网络中的安全分层路由协议：比较分析。*软件工程及其应用国际杂志，10*(11), 95–108. doi:10.14257/ijisea.2016.10.11.08
Palacharla, S., Chandan, M., GnanaSuryaTeja, K., & Varshitha, G. (2018). 虫洞攻击：物联网 (IoT) 中的主要安全隐患。*工程与技术国际杂志，7*(3.27), 147–150.
Patil, H. K., & Chen, T. M. (2017). *无线传感器网络安全：物联网。* 收录于*计算机与信息安全手册* (第3版，第317–337页)。Elsevier。doi:10.1016/B978-0-12-803843-7.00018-1
Perrig, A., Szewczyk, R., Tygar, J. D., Wen, V., & Culler, D. E. (2002). SPINS: 传感器网络安全协议。*无线网络，8*(5), 521–534. doi:10.1023/A:1016598314198
Rashmi. (n.d.). A1, M. C. M. 使用高效局部化检测算法检测移动传感器网络中的节点复制攻击。*国际工程研究与应用杂志*。
Roosta, T. G. (2008). *泛在传感器网络的攻击与防御。* Academic Press。
Roychowdhury, S., & Patra, C. (2010). *自组路由中的地理自适应保真度与地理能耗感知路由。* 论文发表于国际会议。
Shaon, M. (2015). *一种计算智能方法用于检测无线传感器网络中的虫洞攻击。* Academic Press。
Sharma, S., & Jena, S. K. (2011). 无线传感器网络中安全分层路由协议综述。*2011年国际通信、计算与安全会议论文集。* 10.1145/1947940.1947972
Shikha. (2016). 无线传感器网络中节点定位的研究。*计算机科学与工程技术国际杂志，7*(3).
Singh, M. D. R. (2015). 无线传感器网络中的安全问题与服务拒绝攻击综述。*计算机科学与信息技术研究国际杂志，3*(1).

## 参考文献

Singh, R., Singh, J., & Singh, R. (2016). TBSD: A defend against Sybil attack in wireless sensor networks. *国际计算机科学与网络安全杂志*, 16(11), 90–99.
Stankovic, D. W. a. J. A. (2002). Denial of Service in Sensor Networks. *IEEE 计算机*, 35(10).
Sundararajan, R. K., & Arumugam, U. (2015). 用于缓解无线传感器网络中 LEACH 协议黑洞攻击的入侵检测算法. *传感器期刊*, 2015, 2015. doi:10.1155/2015/203814
