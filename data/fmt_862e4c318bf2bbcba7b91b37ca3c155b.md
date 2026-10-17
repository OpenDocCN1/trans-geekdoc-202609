
#### 15.6.2 人工智能（AI）与机器学习（ML）

过去几年，AI 和机器学习（特别是深度学习）技术的复兴取得了显著进展，AlphaGo 的成功和自动驾驶应用尤为突出。

当有广泛的数据规模可用于模型创建和参数调优时，这些技术表现良好并提供最佳的预测性能（Zhicheng, 2018）。

从网络安全的角度来看，将 AI 和深度学习应用于边缘计算 + IoT，以帮助评估各种网络活动、识别可能的风险和弱点以进行修复或补丁、并检测恶意攻击，也是一个巨大的机遇。

因此，网络安全爱好者的机遇也在人工智能和机器学习领域兴起。

#### 15.6.3 弱/轻量级 IoT 安全

在大多数情况下，为了在计算机上在保护和功耗之间找到平衡，我们只能寻找轻量级的方法和算法。包括认证（Lee et al., 2014；Xuanxia Yao, 2015）、密码学（Xuanxia Yao, 2015；Zhicheng, 2018）、访问控制和密钥交换（Raza et al., 2012），此类轻量级算法可以存在。

此类轻量级认证过程的一个常见示例是用于低速率和长距离 IoT 实现，其中基站和 IoT 模块使用简单得多、轻量得多的认证系统（802.11ah 或“WiFi HaLow”）协同工作。

#### 15.6.4 基于欺骗的网络防御

被动安全是传统网络防御策略（如加密、认证和访问控制）的主体，这意味着它们不主动追踪攻击者，而是旨在使攻击者更难入侵。用于增强单个机构网络防御能力的成功网络防御策略之一是基于欺骗的防御（Zhicheng, 2018）。

地址跳变、蜜罐和网络望远镜是常见的示例方法。欺骗和网络配置中任何意外的持续变化，理论上可能会迷惑攻击者，或将他们引向预先部署的蜜罐陷阱（La et al., 2016）。

专注于操纵的策略还将在企业网络上创建大量虚假凭证，使得网络犯罪分子无法以一组有效用户身份的集合形式获取网络访问权限。如果攻击者使用这些虚假密码，安全管理员可以识别并追踪他们。一旦被记录和文档化，攻击者行动的痕迹和档案可以被更深入地研究，以解释他们如何攻击目标设备以及他们使用的总体趋势。这种专业知识对于提高组织网络的安全性非常有帮助。蜜罐陷阱通常是物理或虚拟计算机，它们在安全管理员的密切监督和日志记录下，声称是实际系统。它们试图诱使攻击者采取有利于防御者的行动，或仅仅是在虚假目标上浪费时间和金钱（Zhicheng, 2018）。然而，这不是一条单行道，因为攻击者通过使用从可疑到看似正常的各种战术，也仍然希望避免被识别。

在保持大规模“边缘计算 + IoT”系统更安全方面，预计基于欺骗的网络安全战术将发挥更重要的作用。

#### 15.6.5 物联网下设备的隔离身份

如今，我们用于互联网连接的几乎所有设备都基于 IP（IPv4 或 IPv6）。就互联互通而言，这通过鼓励设备相互交互并获取内容和服务，提供了巨大的便利。这种丰富的互联互通也使得管理员通过远程设置或管理变得更加简单。

然而，缺点是它有效地暴露了所有设备，包括一些关键的工业控制系统（如智能电网），使其处于危险角色中：如果任何基本密码被窃取并冒充为合法用户，潜在的黑客仍可能获得访问权限。传统防火墙只能过滤少量流量，但它们通常采用基于边界的保护方法，防火墙过滤通常基于任意 IP。它也无法阻止内部攻击（Zhicheng, 2018）。

一个常见的例子是，主机标识协议（HIP）中使用的主机标识符可以作为一种不同于 IP 地址的身份识别和命名方案，用于物联网应用（Zhicheng, 2018）。物联网设备的链接需要使用主机标识而非 IP 地址，以实现这种覆盖层身份识别和命名方案。在两个实体能够相互通信之前，它们需要创建一个用于交换加密协议的绑定。如果不实施严格的安全协议，这将防止外部世界直接入侵敏感的物联网设备和网络。同样，一种独立于 IP 且受保护的身份识别和命名方案，在未来的“边缘计算 + 物联网”环境中将非常有用，特别是对于那些需要额外安全保护的敏感系统中资源匮乏的物联网设备。在这方面，我们假设将会有相当多的研究机会（Zhicheng, 2018）。

### 15.7 结论

对于几种潜在的物联网实现而言，向物联网（IoT）的范式转变以及边缘计算的出现提供了巨大的益处。但这也给网络安全带来了必要的挑战。在本报告中，我们识别并探讨了与这一愿景相关的五个网络安全问题和五个潜在的网络安全前景。“边缘计算 + 物联网”平台与不断发展的区块链和人工智能技术之间的某些融合发展，理论上可以创造许多有益的机会。

总体而言，我们得出的结论是：未来仍存在待解决的挑战，而机遇也在不断涌现，我们可以用有用且可持续的方式加以利用。

### 参考文献

*   Akhunzada, E. A. (2015). Securing software defined networks: taxonomy, requirements, and open issues. *IEEE Communications Magazine*, 53(4), 36–44.

*   Amoroso, E. 2006. Cyber *s*ecurity. New Jersey: Silicon Press.

*   Baldwin, D. A. 1997. The concept of security. Review of International Studies, 23(1), 5–26.

*   Bulakh A., Tuohy E., & Pernik P. 2016. Estonia’s developing level playing field for critical energy infrastructure protectors-a model for broader scale platforms?, *Energy Security: Operational Highlights*, 10: 4–10. Available on the Internet: [www.icds.ee/fileadmin/media/icds.ee/failid/no\_10\_20160410.pdf](http://www.icds.ee)

*   Buzan, B., Wæver, O., & De Wilde, J. 1998. Security: *a new framework for anal*ysis. Boulder, CO: Lynne Rienner Publishers.

*   Canongia, C., & Mandarino, R. 2014. Cybersecurity: the new challenge of the information society. In Crisis *management: concepts, methodologies, tools and applic*ations: 60–80. Hershey, PA: IGI Global. [`dx.doi.org/10.4018/978-1-4666-4707-7.ch003`](http://dx.doi.org/10.4018/978-1-4666-4707-7.ch003)

*   CID, D. (2016, June). Large CCTV Botnet leveraged in DDoS attacks. Retrieved from [`blog.sucuri.net/`](https://blog.sucuri.net): [`blog.sucuri.net/https://blog.sucuri.net/`](https://blog.sucuri.net): [`blog.sucuri.net/2016/06/large-cctv-botnet-leveraged-ddos-attacks.html`](https://blog.sucuri.net)

*   Council, E. (2008). The European Critical Infrastructures Directive. Council Directive 2008/114/EC. Available on the Internet: [`eurlex.europa.eu/legal-content/DA/ALL/?uri=CELEX:32008L0114`](http://eurlex.europa.eu).

*   Craigen, D. D.-T. (2014). Defining cybersecurity. *Technology Innovation Management Review*.

*   DHS. 2014. A glossary of common cybersecurity terminology. National Initiative for Cybersecurity Careers and Studies: Department of Homeland Security. October 1, 2014: [`niccs.us-cert.gov/glossary#letter\_c`](http://niccs.us-cert.gov)

*   Dong Wei, Y. L. et al. (2010). An integrated security system of protecting Smart Grid against cyber attacks. *Innovative Smart Grid Technologies (ISGT)*. DOI: [10.1109/ISGT.2010.5434767](https://doi.org/10.1109/ISGT.2010.5434767).

*   GAO-05-434. (2005). Critical Infrastructure Protection: Department of Homeland Security Faces Challenges in Fulfilling Cybersecurity Responsibilities. Retrieved from [www.gao.gov/: http://www.gao.gov/new.items/d05434.pdf](http://www.gao.gov)

*   Gibson, W. (2016). *Neuromancer*. UK: Orion. (Reissue of 1984 novel.)

*   Govindarasu, M. (2017). Cybersecurity of the Power Grid: A Growing Challenge. Retrieved from [www.usnews.com/](http://www.usnews.com): [www.usnews.com/https://www.usnews.com/](http://www.usnews.com): [www.usnews.com/news/national-news/articles/2017-02-24/cybersecurity-of-the-power- grid-a-growing-challenge](http://www.usnews.com)

*   ITU. 2009. Overview of cybersecurity.  Recommendation ITU-T X.1205. Geneva: International Telecommunication Union (ITU). [www.itu.int/rec/T-REC-X.1205-200804-I/en](https://www.itu.int)

*   Johnson, T. A. (2015). *Cybersecurity: Protecting critical infrastructures from cyber attack and cyber warfare*. CRC Press.

*   Julian Jang-Jaccard, S. N. (2014). A survey of emerging threats in cybersecurity. *Journal of Computer and System Sciences*, 80(5), 973–993.

*   Karpaviciute, Ieva. (2017). Securitization and Lithuania’s national security change. *Lithuanian Foreign Policy Review*, 36. [10.1515/lfpr-2017-0005](https://doi.org/10.1515/lfpr-2017-0005).

*   Keith Stouffer, J. F. (2013). *Guide to Industrial Control Systems (ICS) security*. Supervisory Control and Data Acquisition (SCADA) Systems, Distributed Control Systems (DCS), and Other Control System Configurations such as Programmable Logic Controllers (PLC).

*   Kemmerer, R. A. (2003). Cybersecurity. Proceedings of the 25th IEEE International Conference on Software Engineering: 705–715. [`dx.doi.org/10.1109/ICSE.2003.1201257`](http://dx.doi.org/10.1109/ICSE.2003.1201257)

*   Kizza*,* J. M. (2002). Computer network security and cyber ethics. Jefferson, NC: McFarland (reference from an article 2011).

*   La, Q. D. et al. (2016). Deceptive attack and defense game in honeypot-enabled networks for the Internet of Things. *IEEE Internet of Things Journal*, 3(6), 1025–1035.

*   Lal, S. et al. (2017). NFV: security threats and best practices. *IEEE Communications Magazine*, 55(8), 211–217.

*   Lee, J. et al. (2014). A lightweight authentication protocol for Internet of Things. International Symposium on Next-Generation Electronics (ISNE), Kwei-Shan, 1–2.

*   Lewis, J. A. (2006). Cybersecurity and critical infrastructure protection. Washington, DC: Center for Strategic and International Studies. [`csis.org/publication/cybersecurity-and-critical-infrastructure-pr...`](http://csis.org)

*   Limba, T., Plėta, T., Agafonov, K., & Damkus, M. (2017). Cyber security management model for critical infrastructure. *Entrepreneurship and Sustainability Issues* 4(4), 559–573.

*   McElhannon, J. P. (2018). Future edge cloud and edge computing for internet of things applications. *IEEE Internet of Things Journal*, 5(1), 439–449.

*   Moslehpour, K. J. (2016). Cyber security management: a review. *Business and Management Dynamics*, 16–39.

*   Oxford University, p. (2014, October 1). Oxford Online Dictionary. Retrieved from Oxford: Oxford University Press: [www.oxforddictionaries.com/definition/english/Cybersecurity](http://www.oxforddictionaries.com)

### 参考文献

*   Pan, J. 等 (2016)。HomeCloud：一种用于新型应用交付的边缘云框架与测试平台。第 23 届国际电信会议 (ICT)，塞萨洛尼基，1–6。

*   Raza, S. 等 (2012)。轻量级 IKEv2：一种适用于压缩 IPsec 和 IEEE 802.15.4 安全性的密钥管理解决方案。载于 IETF 智能对象安全研讨会论文集，第 23 卷。

*   Singer, P. W. (2014)。*网络安全：人人都需要知道的事*。牛津大学出版社。

*   Tikk, E. (2010)。全球网络安全——思考北约的定位。SAIS 国际事务评论 30(2)，105–119。[www.muse.jhu.edu/article/403442.](http://www.muse.jhu.edu)
