
Bell Labs 估计（[图 26](#10-9781315365756_chapter-chap4.xhtml#fig4_26)）这种网络的 TCO 节省情况，该网络构建以在五年内支持 10 倍的流量增长，按单位容量计算约为 70%。超过一半的收益归因于大规模、高密度路由和光传输的进步，而超过 40% 的收益来自 SDN 自动化和网络优化。

这一数量级接近的供需经济变化证实，我们确实正处于一场技术革命之中，其驱动力是新型数字商品的动态联网（来自人和物体的新信息、数据、内容流），并导致经济转型。

## 未来从现在开始

尽管前述讨论听起来相当具有未来感，但网络这种雄心勃勃的转型已经开始。在此，我们介绍网络向“即时适应且弹性”范式转型的几个正在进行中的例子，涵盖标准化、开源计划、协作产业努力以及产品试验和发布：

• 网络设备厂商正在实施云编排和自动化系统以及 SDN 控制器，二者共同可以按需创建虚拟网络，以连接数据中心内的虚拟机，并通过安全隧道连接到其他数据中心和企业中的虚拟机。这种网络自动化作为虚拟机生命周期自动化的一部分进行管理，使得虚拟机的网络连接即使在从一台服务器迁移到另一台服务器时也能跟随其移动。

• IETF 的 NVO3 工作组正在增强数据面和控制面协议，以实现数据中心中的基于 IP 的网络虚拟化；例如，使用流行的 VXLAN 标记协议，以及用于承载虚拟网络信息的 BGP 扩展。

• 开放网络基金会（ONF）一直在开发和增强用于在 SDN 环境中编程交换机的 OpenFlow 协议，以及用于配置和初始化交换机的相关 OF-Config 协议。ONF 现在也在将 OpenFlow 扩展以解决光网络系统的控制问题。

• OpenDaylight 协作项目是创建具有标准化北向 API 的 SDN 控制器基础设施的产业倡议。控制器基础设施面向多厂商部署，并提供对网络的标准化的编程接口。

• 开放网络操作系统（ONOS）旨在构建面向运营商的 SDN 网络操作系统。它提供由相同控制器实例组成的分布式核心，以将设备和控制器实例故障与影响网络其余部分隔离，并提供基于意图的新编程抽象，从而允许应用程序请求服务而无需了解服务将如何执行的具体细节。

• NETCONF 协议用于管理网络元素及其配置，以及相关的 YANG 数据建模语言用于对其进行规范，正在获得越来越多的产业认可。大多数设备现在都有相应的 YANG 模型。此外，OpenDaylight 控制器大量使用 YANG。

• 400 Gb 相干光器件已由领先厂商集成，作为路由器和传输接口，以创建可调速率的大规模核心网络。太比特超通道系统已在实验室以及运营商现场试验中得到演示。

计算机行业发生的向云计算的根本性技术转变，现在正推动网络围绕相同的云计算范式进行转型，即即时适应性和弹性。

## 摘要

计算机行业发生的向云计算的根本性技术转变，现在正推动网络围绕相同的云计算范式进行转型，即即时适应性和弹性。这种转型要求网络结构能够根据动态服务需求进行调谐，以支持按需创建适用于任何应用程序或服务的“完美网络”的能力。我们所描述的未来可调谐网络结构将通过提供组装一组虚拟网络组件以形成具有任意全局-本地范围的定制虚拟网络的手段来实现这一点。

这些动态虚拟网络将由网络操作系统控制，该操作系统为网络应用提供网络的抽象全局视图，网络应用利用该抽象视图构建定制服务。抽象视图的实现得益于采用 SDN 驱动的关键控制平面功能的逻辑集中化。

新的网络应用将推动带宽市场的发展，以匹配按需容量的消费者和供应商。该市场将允许大型云提供商利用容量现货市场，通过现货市场获取的容量吸收峰值，从而提高平均利用率。

我们真正正处于 IP 和光网络的新时代的黎明，该时代连接边缘和集中式云，将构成商业和消费者生活转型以及新技术革命的基础。

## 参考文献

Bell, C. J., Hogarth, J. M. and Robbins, E., 2009. “美国家庭对电子银行的获取和使用，1989–2007”，*联邦储备公报* (http://www.federalreserve.gov/pubs/Bulletin/2009/articles/onlinebanking/default.htm#t1)。

Bell Labs Consulting, *美国实时竞价市场增长*。

Belobaba, Peter; Hernandez, Kari; Jenkins, Joe; Powell, Robert and Swelbar, William, “*1978–2010 年美国客运航空业生产率趋势*”，Transportation @ MIT Program, MIT Press, MIT, Cambridge, MA。

Bjorklund, M., 2010. “YANG — 网络配置协议（NETCONF）的数据建模语言”，*Rfc* 6020 (https://tools.ietf.org/html/rfc6020)。

Broeders, H., and Khanna, S., 2015. “数字时代银行的战略选择”，*洞察与出版物*, McKinsey & Company (http://www.mckinsey.com/insights/financial_services/strategic_choices_for_banks_in_the_digital_age)。

Brueckner, Jan K. and Spiller, Pablo T., 1994. “放松管制航空业中的交通密度经济”，*法律与经济学杂志*。

Chandrasekhar, S.; Liu, X.; Zhu, B. and Peckham, D. W., 2009. “在超大面积光纤上 7200 km 传输 1.2 Tb/s 24 载波无保护间隔相干 OFDM 超通道”，载于欧洲光通信会议（ECOC）2009 年会议论文集，9 月，论文 PD2.6。

eMarketer 2013, *程序化广告支出势将飙升：实时竞价预计将占程序化广告预算的最大份额* (http://www.emarketer.com/Article/Programmatic-Ad-Spend-Set-Soar/1010343)。

Enns, Rob, 2006. “NETCONF 配置协议”，*Rfc* 4741 (https://tools.ietf.org/html/rfc4741)。

Federal Reserve System 2013. *2013 年联邦储备支付研究”* (https://www.frbservices.org/files/communications/pdf/research/2013_payments_study_summary.pdf)。

FierceTelecom 2011. “XO 的 EoC 增长由有机增长和合作伙伴关系的混合驱动”，*FierceTelecom*, 5 月 3 日 (http://www.fiercetelecom.com/special-reports/competitive-carriers-hone-their-ethernet-over-copper-skills/xos-eoc-growth-driven-mi)。

Hao, Fang; Jansen, Arnold; Kodialam, Mualidhara N. and Lakshman, T. V., 2015. “IP 网络优化的路径计算”，*TechZine*Alcatel-Lucent, 六月。

Jain, S. et al, 2013. “B4：全球部署的软件定义广域网的经验”，Proceedings of the ACM SIGCOMM Conference, 2013。

Kenshoo 2013. *Kenshoo 新研究发现 Facebook 广告将付费搜索广告支出回报率提高 30%*, Press Release。

Martinez, German, 2009. *Gemalto, “移动金融服务”，幻灯片 2, Banking Channel Trend* (http://www.slideshare.net/daniel_b4e/evolucin-de-servicios-financieros-mviles-en-latinoamrica-2487277)。
