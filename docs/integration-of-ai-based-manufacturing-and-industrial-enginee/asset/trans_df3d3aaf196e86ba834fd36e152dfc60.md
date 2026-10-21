

Gubbi J, et al (2013). 物联网（IoT）：愿景、架构要素与未来方向, Future Generation Computer Systems, 29(7): 1645–1660.

He D., Chan S., Guizani M. (2018). 移动边缘计算支持的物联网安全, IEEE Communications Magazine, 56(8): 56–61.

Sha K, Yang T, Wei W, Davari S (2020). 基于边缘计算的物联网安全设计综述, Digital Communications and Networks, 6(2): 195–202.

Kothandaraman D, Manickam M, Balasundaram A, Pradeep D, Arulmurugan A, Sivaraman AK, ... & Balakrishna R (2022). 面向高效物联网的去中心化链路故障预防路由（DLFPR）算法, Intelligent Automation & Soft Computing, 34(1), 132–156.

Kumar R, Rani S, Awadh MA (2022). 探索工业4.0中物联网的应用领域：综述、文献计量与内容分析, Sensors, 22(11): 4276.

Lehong H (2019). 物联网技术成熟度曲线, Stamford: Gartner Inc.

Lu R, Heung K, Lashkari A, Ghorbani AA (2017). 面向雾计算增强型物联网的轻量级隐私保护数据聚合方案, IEEE Access, 5: 3302–3312.

McSherry F, Talwar K (2007). 基于差分隐私的机制设计, Proceedings of 48th Annual IEEE Symposium on Foundations of Computer Science (FOCS'07).

Mehta P, Gupta R, Tanwar S (2020). 区块链愿景下的无人机网络：挑战、解决方案与比较, Computer Communications, 151: 518–538.

Michailidis ET, Vouyioukas D (2022). 无人机互联网中基于软件与硬件的认证机制综述, Drones, 6(2): 41.

Nia AM, Jha NK (2016). 物联网安全综合研究. IEEE Transactions on Emerging Topics in Computing, 5(4): 586–602.

Rachna R, Bhambri P, Chhabra Y (2022). 分布式聚类方法在WSN和IoT中的部署. In 物联网的云与雾计算平台 (pp. 85–98). Boca Raton, FL: Chapman and Hall/CRC.

Ranaweera P, Jurcut AD, Liyanage M (2021). 多接入边缘计算安全与隐私综述, IEEE Communications Surveys and Tutorials, 23(2): 1078–1124.

Rani S, Kataria A, Kumar S, Tiwari P (2023). 智慧医疗系统中安全IoMT应用的联邦学习：综合综述, Knowledge-Based Systems, 65(6), 110658.

Rani S, Kataria A, Sharma V, Ghosh S, Karar V, Lee K, Choi C (2021). 考虑网络犯罪的物联网安全威胁与纠正措施：综述, Wireless Communications and Mobile Computing, 2021: 1–30.

Ritu K, Bhambri P (2022). 软件工作量估算的CAD系统, 论文发表于International Conference on Technological Advancements in Computational Sciences, pp. 140–146. IEEE. DOI: 10.1109/ICTACS56270.2022.9988123.

Roman R, Lopez J, Mambo M (2018b). 移动边缘计算、雾计算与物联网：安全威胁与挑战的综述与分析, Future Generation Computer Systems, 78: 680–698.

Roman R, Rios R, Onieva J, Lopez J (2018a). 使用边缘技术的物联网免疫系统, IEEE Internet of Things Journal, 7(8), 1–8.

Sangwan YS, Lal S, Bhambri P, Kumar A, Dhanoa IS (2021). 社会数据安全与加密的进展：综述, NVEO-Natural Volatiles & Essential Oils Journal| NVEO, 8(4), 15353–15362.

Sharma N, Sultana HP, Singh R, Patil S (2019). 物联网应用中的安全哈希认证, Procedia Computer Science, 165: 328–335.

Sodanapalli S, et al. (2021). 边缘计算范式的最新进展：非常规计算的分类基准与标准, IJFC, 4(1): 37–51.

Sun X, Ng DWK, Ding Z, Xu Y, Zhong Z (2019). 无人机系统中的物理层安全：挑战与机遇, IEEE Wireless Communications, 26(5): 40–47.

Yuchang L, Bhagya NS, Kijun H (2021). 基于边缘计算的智慧城市环境中深度学习层分配的算法实现, Computers & Electrical Engineering, 89: 106909.

## 8 Phased.js：面向 AI 的自动化软件部署、资源供给与管理

P. Ushashree
Geethanjali工程技术学院，
印度海得拉巴

Archana Naik、Anurag Verma 和 Anshuman Priyadarshini
NITTE Meenakshi理工学院，印度班加罗尔

### 8.1 引言

人工智能（AI）在决策制定中非常有用，因为其应用意味着系统可以通过自动化过程模拟人脑的行为来完成任务（Shekhar, 2019）。在开发的早期阶段，程序员通常对后端服务器的运作过程一无所知。即使他们了解本地主机应用程序的开发，将其转换为生产构建应用程序也完全是另一回事。程序员在这里遇到的主要问题是“他们知道该做什么”，但“他们不知道怎么做”（Singh et al., 2021）。

我们拥有一系列技术，例如Amazon EC2和Google计算引擎（Shaik et al., 2018），这些技术为程序员使用的不同应用提供了许多配置和依赖。EC2有自己的管理面板，可以显示应用程序的状态，但除非仔细阅读相关文档，否则很难理解。因此，在从线上应用记录实时数据时，开发人员更常使用bash脚本将其记录到单个文件中（Karakostas, 2014）。

由于新学习者在技术部署中面临很高的学习曲线，他们在学习这些技术时遇到许多问题，无法准确确定要供应的资源（Huang et al., 2017）。在这方面，现在提出的主要想法是消除对特定应用或服务器的学习依赖。基础设施云中的应用部署自动化研究（Juve and Deelman, 2011）提供了关于如何使云服务的部署和管理自动化并确定研究领域的综述。

在当今世界，云计算正日益成为分布式系统的重要平台。Benson等人（2016）对云平台上的软件部署进行了综述。文中指出，多云平台的部署存在许多挑战，例如配置约束和依赖管理。同时也有许多应用自动化管理工具，每种工具各有其优势。

远程Web事件日志系统（RWELS）（Shah et al., 2008）：在当今世界，事件日志是应用部署者和维护者识别网站问题的重要数据来源。该方法提出了一种基于Web的客户端-服务器应用RWELS，用于在用户与网站交互时记录用户界面事件并将其存储在文本文件中。该日志系统无需用户交互和关注即可自动存储日志事件。RWELS易于配置，允许用户过滤事件日志。用户可以选择在网站的每个页面上记录某些事件。事件日志通过HTTP传输到服务器，在服务器上所有事件日志都以文本文件形式存储。应用程序上的用户会话日志可以以独特的方式记录。

Kikuchi（2015）提出了在云服务器上设计可扩展应用的架构设计和优势。该研究还揭示了负载均衡器和无状态客户端管理的有效使用。此外，它还探讨了微服务如何比单体应用更具可扩展性。

Toffetti等人（2017）提出了一种云原生应用的新颖架构，能够在云中实现可扩展且有弹性的自管理应用。当前方法存在固有的局限性，阻碍了应用实现自我维持和自我扩展，因为需要大量人工干预和手工编码。

Xu等人（2017）提出了一种使用Kubernetes日志的声明式云应用日志模型工具。该工具读取Kubernetes生成的日志并提供潜在建议。许多真实世界的Kubernetes问题被识别为潜在缺陷。

CELAR是一个自动化应用弹性平台，通过灵活管理可用资源的使用，使云开发者能够构建高效、高性能的服务（Giannakopoulos et al., 2014）。当用户数量激增时，为了满足他们的需求，服务提供商必须提供一个能够帮助他们快速部署应用的环境。在其他贡献中，Yu等人（2013）提出了一个私有云工具包，Yokoyama和Yoshioka（2012）介绍了一种将集群作为服务部署进行管理的方法，称为dodai-deploy。

Ocone等人（2019）提出了一项分析，重点研究了自动伸缩器应使用的伸缩策略。Canali和Lancellotti（2012）概述了云数据中心中的虚拟机及其自动分类。Lu等人（2013）提出了一种方法，通过调查服务的需求来描绘其连接、显示测试用例并掌握服务的关键特性。Durairajan和Sundararajan（2013）讨论了在云上部署可互操作服务管理的策略。

Deshmukh和Khandagale（2017）提出的工作对应用开发环境中的软件部署进行了研究。该环境涉及多次代码变更，以及在多个服务器上使用应用程序。

