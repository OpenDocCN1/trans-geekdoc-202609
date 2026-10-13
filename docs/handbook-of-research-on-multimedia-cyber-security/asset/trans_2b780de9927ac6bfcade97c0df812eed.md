

# 第 17 章

## 参考文献

MidiD.RulloA.MudgerikarA.BertinoE. (2017). Kalis—A system for knowledge-driven adaptable intrusion detection for the Internet of Things. *Proceedings 2017 IEEE 37th International Conference on Distributed Computing Systems (ICDCS)*. 10.1109/ICDCS.2017.104

ÖzçelikM.ChalabianlooN.GürG. (2017). Software-defined edge defense against IoT-based DDoS. *Proceedings 2017 IEEE International Conference on Computer and Information Technology (CIT)*. 10.1109/CIT.2017.61

Ray, P. P. (2018). A survey on Internet of Things architectures. *Journal of King Saud University-Computer and Information Sciences*, 30(3), 291–319. doi:10.1016/j.jksuci.2016.10.003

Raza, S., Wallgren, L., & Voigt, T. (2013). SVELTE: Real-time intrusion detection in the Internet of Things. *Ad Hoc Networks*, 11(8), 2661–2674. doi:10.1016/j.adhoc.2013.04.014

SedjelmaciH.SenouciS. M.Al-BahriM. (2016). A lightweight anomaly detection technique for low-resource IoT devices: A game-theoretic methodology. *Proceedings 2016 IEEE International Conference on Communications (ICC)*. 10.1109/ICC.2016.7510811

Shoemaker, A. (2017). How to Identify a Mirai-Style DDoS Attack. 2020. Retrieved from https://www.imperva.com/blog/author/andrewshoemaker/

Sterling, B. (2005). *Shaping things*.

SummervilleD. H.ZachK. M.ChenY. (2015). Ultra-lightweight deep packet anomaly detection for Internet of Things devices. *Proceedings 2015 IEEE 34th international performance computing and communications conference (IPCCC)*. 10.1109/PCCC.2015.7410342

Xia, F., Yang, L. T., Wang, L., & Vinel, A. (2012). Internet of things. *International Journal of Communication Systems*, 25(9), 1101–1102. doi:10.1002/dac.2417

## 作者

*   **Leandros Maglaras**  
    [![Orcid Image](i/orcid.svg)https://orcid.org/0000-0001-5360-9782](https://orcid.org/0000-0001-5360-9782)  
    德蒙福特大学，英国

*   **Helge Janicke**  
    网络安全合作研究中心，埃迪斯科文大学，澳大利亚

*   **Mohamed Amine Ferrag**  
    [![Orcid Image](i/orcid.svg)https://orcid.org/0000-0002-0632-3172](https://orcid.org/0000-0002-0632-3172)  
    盖尔马大学，阿尔及利亚

## 摘要

本研究从技术上分析了长度不超过 12 个字符的常用密码的最大组合数量。文中还给出了存储所有不超过 12 个字符的可能密码所需的最大存储空间，并将其与主流云存储服务商公布的存储成本以及一个国家的情报和国防预算进行了对比。作者证明，仅凭当前市面上可购买的商用组件，任何密码都有可能在几秒钟内被计算出来。研究结论指出，民族国家甚至合作的多个民族国家有可能已经购买了私人公民和企业的密码，这表明我们可能已经进入了一个密码不再是隐私合法防线的时代。

## 引言

随着关键国家基础设施越来越容易遭受网络攻击，其防护已成为任何组织乃至国家的重大议题。此外，工业控制系统与物联网（`IoT`）的协同效应应运而生，带来了新的安全挑战（Maglaras 等，2018），这使得基于安全工具、人员和流程的重叠防御策略的部署成为必要。传统安全机制是保护组织或国家边界的适当且有效的手段。防火墙架构、邮件扫描、`DPI`、`VPN`、`HIDS`、`NIDS` 均是组织减少恶意软件入侵其环境机会的成熟途径。作为补充措施，锁定未使用的端口、`USB` 设备，通过企业目录使用访问控制，以及强制执行最小权限访问，所有这些都能降低内部威胁。任何组织必须采取的基本但重要的安全措施之一是密码策略（Gupta 等，2018），以及其他防御机制（Jiang 等，2018；Almomani 等，2013）。

在不深究密码的历史或哲学定义，而纯粹专注于现代科学层面的密码定义方面，根据剑桥词典“商务英语”中的“Password”条目，在商业和计算术语中，它被定义为：“你在使用计算机、网站等时，用来证明你身份的秘密单词或字母和数字的组合：”（剑桥词典，2019）。显然，这并不准确，因为它排除了现在大多数企业密码策略中常见的特殊字符。因此，在本章中，当提到密码时，其定义将是“用户从现代计算软硬件可用字符集中选取的一组字符，用于认证目的”。密码固有许多变量，因为它们本身就是从我们各种形式的复杂语言中提取的，即使不代表一个可定义的单词。

围绕密码存在许多复杂而有趣的理论，这引发了大量讨论和有趣的内容，例如期刊文章“作为熵博弈的密码安全性”（Rass 等，2018），也催生了一些真正鼓舞人心的数学研究。此外，我们正见证着量子计算的出现所带来的“可能的艺术”的演进，这增进了我们对物理学的理解。量子计算为工业带来了以指数级提升的速度计算复杂问题的绝佳机遇。然而，人们早已推测，这种计算能力的巨大飞跃可能预示着密码及依赖复杂性的类似安全防御的消亡。这在论文“量子计算机的全球灾难性风险与安全启示”（Major 等，2015）中有很好的描述，作者也支持这一观点。然而，在本文中，作者质疑的是当下的可能性，仅利用当今人人可买到的现成商用设备。

### 图 1. 密码规则

![Figure978-1-7998-2701-6.ch017.f01](i/ch017.f01.png)

为了高效地探讨这一问题，本章作者希望在引入增加成功猜测概率的数学理论之前，先审视密码的最基本要素。此时，问一个合理的问题：“为什么我们不想增加找到匹配的概率？”答案大概是：我们想。然而，现代社会中的某些领域将机会和可能性视为应尽可能消除的“脏话”，例如情报界、医疗和金融部门。为此，本章旨在在合理约束和替代方案下，估算存储任何人正在使用的所有可能密码组合的成本。

在本章中，我们不会研究长度超过 12 个字符的密码，并将重点放在英国键盘配置上。在没有这些约束的情况下进行进一步研究很有趣，也值得后续跟进，但为了保持本章切合实际且易于理解，这些约束对于以最基本形式证明该理论似乎是合理的。

### 图 2. 密码与哈希函数

![Figure978-1-7998-2701-6.ch017.f02](i/ch017.f02.png)

