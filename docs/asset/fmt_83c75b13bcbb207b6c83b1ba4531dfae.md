
受保护子网的核心思想是一个网络可以拥有多个边界，这些边界可分为最外围边界、内部边界和最内层边界网络。在各个网络的门户处，防御层是叠加的，即如果一层被突破，威胁将在下一层得到阻止。最外围边界网络界定了外部网络与内部系统之间的分界点，以及内部代理系统。这里的过滤防火墙采取乐观（黑名单）的态度以提高效率，同时仍能阻止已知的攻击。流向内部边界网络的数据受内部网络架构和系统的约束，这些系统统称为 DMZ。内部边界网络通常只提供最基础的服务，如托管的 Web 服务器，以及代理系统，如 `bastion hosts` 和代理 DNS。由于该区域最易受攻击，通常会受到尝试访问内部网络的攻击，也可能是 DoS 或网站篡改。

受保护子网架构随后使用白名单（悲观）防火墙来隔离最内层网络的内部资产。换句话说，意图访问最内层网络内部系统的流量会在 DMZ 的代理系统中被拦截，然后再转发到内部系统。如图 11.1（参考链接）所示，此配置至少使用两组筛选路由器来创建 DMZ。外部路由器采用乐观 stance，即使用白名单 ACL，只有显式拒绝的连接才被阻止，其余连接默认允许。

内部路由器的设置是一种悲观的立场，即除非明确允许，否则所有连接都被显式拒绝。从外部连接（如互联网）发出的请求会经过外部路由器，转发到内部网络中的主机。在非安全区（DMZ）中，设置了 DNS 以向外部请求返回一个代理的 IP 地址，用于内部主机。该代理是一台堡垒主机，充当中继系统。当通信从外部路由器传递到代理时，代理可以检查通信内容，确保其符合常规且不含病毒或其他恶意软件，然后再转发到目标内部主机。代理将数据转发给目标主机的过程是通过内部 DNS 的中继查询实现的，而内部路由器仅允许代理这一条连接（除此以外的连接均被阻止），该 DNS 查询会返回目标主机的 IP 地址给代理。事务由代理将数据传递给目标主机完成，并在交付给请求的应用之前对数据进行额外检查。

如所示，筛选子网架构非常安全，但管理复杂，且处理开销大。

![FIGURE 11.1 Screened Subnet Architecture](img/9781284236378_CH11_FIGF01.jpg)

FIGURE 11.1 Screened Subnet Architecture

| Network Address Translation (NAT) || NAT 是一种将网络地址从一个转换为另一个的方式，例如在创建子网时使用。然而，该技术在网络安全中也可用于“隐藏”或保护内部 IP 地址不被外部网络看到。用于网络安全的这种技术称为 IP masquerading。 |
| --- | --- |
| LDAP || Lightweight Directory Access Protocol (LDAP) 常用于身份验证和授权。LDAP 使得应用程序能够与存储对象（更具体地说，是对象标识符）如计算机和用户、其权限以及密码的目录服务数据库进行通信。 |
| Ontology || 在某一知识领域（如网络安全威胁模式和分类）中，一组概念和类别的集合，属于本体论。 |

### 11.2.3 Ontology Based Architecture

本体论是一组与某一知识领域（如网络安全威胁向量）相关的概念和类别的集合。本体论通常由资源描述框架（RDF）或本体语言（OWL）等标记语言组成，用于表示概念之间的属性和关系。因此，本体论由可读的文档组成，也可以以三元组（主体-谓词-宾语）的形式存储在数据库中。三元组将数据存储为具有关系链接的对象网络，相较于数据仓库和数据挖掘，在分析数据（如实时识别或推断威胁）时具有某些速度优势。虽然基于本体的防御并非技术上的防火墙，但它们能够执行许多防火墙的筛选和监控功能。在传统的防火墙架构中，安全策略为给定的安全立场和特定平台预先定义。而在另一种情形中，使用安全策略本体已成为一种流行的方式，以解耦底层技术依赖关系。在这种方法中，安全策略规则通过图形用户界面创建，底层技术则自动生成相应的本体。

在关于安全事件和漏洞的研究中，Moreira 及其同事³ 提出了一种基于三层本体（操作层、战术层和战略层）的过滤与监控方法。由于本体由标记文档构成，它们可以在不同系统之间轻松共享。操作层由日常事务组成，受战术层控制，战术层包含控制资源访问的规则、用于信息存储和检索的技术、以及执行这些活动的人员。战略层关注指令和治理。采用 Moreira 等人的方法，安全策略本体可以基于常见漏洞和暴露（CVE）本体，该本体捕获并更新常见漏洞和事件，例如软件工程研究所的 CERT 报告的内容。安全本体的主要功能是定义一套标准、准则和行为，指导过滤与监控系统的努力。

网络安全策略本体的一个例子可能包括远程或本地访问的威胁、诸如 SQL 注入、缓冲区溢出等漏洞类型及其后果（包括严重程度和受影响的系统），以及是否已发布修复补丁等信息。该方法有助于在网关自动化执行网络策略，类似于应用层防火墙和监控系统。

随后会使用 Web 服务、代理框架或对象请求代理进行运行时的策略发现与强制。在其他情况下，安全策略可以通过在受控环境（沙箱）中运行应用程序来学习并生成，以发现其正常行为，随后监控应用程序是否偏离此行为；若偏离，则拦截执行（例如尝试进行被禁止的特权系统调用）。这种方法非常灵活，灵活性使得本体在移动网络和点对点（P2P）网络拓扑中尤为吸引人，因为设备可能随时加入或离开网络。

## 11.3 Cybermonitoring and Scanning Systems

各种活动监视器用于不同的技术和过程。例如，基础设施监视器（如 `Zabbix®`）有助于报告服务器和服务的功能状态，并识别网络流量、CPU 利用率等方面的异常。例如，网络利用率持续飙升会触发告警，提示管理员进行调查。其他监视器（如 `BlueStripe®`）用于跟踪应用程序和工作流中的事务失败。入侵检测系统（IDSs）则具有专门目的——在特定类型的安全 breach 尝试时发出警报。大多数 IDS 不仅用于检测入侵，还会通过执行预定义的操作（如丢弃和阻断连接、通过代理或备用服务器重新路由流量）来保护系统。

IDS 有多种类型。例如，网络 IDS（NIDS）监控网络流量以检测攻击，通过扫描已知的行为签名或异常行为（称为异常行为）来实现。NIDS 会将活动记录到文件中，并向网络管理员和状态仪表盘发送警报。一些 NIDS 专注于特定网络协议（如 HTTP/HTTPS），这些被称为协议基于 IDS（PIDS）。主机基于入侵检测系统（HIDS）在网络中的单个主机或设备上运行。HIDS 监控设备的入站和出站数据包，并在检测到 attempted intrusion 或其他恶意活动时向管理员报告错误和警报。许多 IDS 具备多种功能，称为混合 IDS，混合 IDS 将主机和服务器数据与网络活动结合，提供对 cyberinfrastructure 更全面、更细致的视图。

```
if (condVar > someVal) {console.log("xxx")}
```

IDS 和基础设施监控可以集中化，也称为无代理，或者可以是分布式的，也称为基于代理。在基于代理的配置中，会在被监控的设备上部署软件代理，并将数据发送到服务器，由服务器负责管理和显示。最常见的是基于 SNMP 的监控。两者都有优缺点。集中化或无代理系统的可扩展性不如基于代理的系统，且在检测时可能会出现过大的延迟。在基于代理的系统中，代理软件必须在每个被监控设备上安装和维护。有时会使用代理作为中间件，以提供一定的灵活性，并允许从一组被监控节点聚合监控数据，跨越网络边界到管理服务器，但这些方法也有局限性。虽然还有其他技术，但大多数 IDS 都与安全信息和事件管理系统（SIEM）协同工作。SIEM 整合多个来源的输出，并使用过滤器识别恶意活动。最有效的 IDS 最大化真实威胁的发现，使得漏检的攻击（即 false negatives）数量极少，同时最小化误报（即 false positives）。`SolarWinds Security Event Manager®` 是一个 SIEM 的示例（Figure 11.2）。

![FIGURE 11.2 SolarWinds Security Event Manger (SEM) ¶ © 2021 SolarWinds Worldwide, LLC. All rights reserved.](img/9781284236378_CH11_FIGF02.jpg)

FIGURE 11.2 SolarWinds Security Event Manger (SEM) ¶ © 2021 SolarWinds Worldwide, LLC. All rights reserved.

### 11.3.1 IDS Detection Methods

IDS 检测方法有多种，但通常可分为三类：基于签名、基于异常和基于启发式。基于签名的 IDS 通过以下方式检测攻击：(1) 使用已知攻击模式的数据库；(2) 一个能够从用户、网络数据包或软件行为模式中推断攻击的识别系统。由于基于签名的检测依赖于已知模式，因此保持签名数据库更新至关重要。即便如此，它们仍易受到新型（也称为生日攻击、首次攻击或零日攻击）或多态化攻击的影响，在这些攻击中，签名尚未被识别，或攻击签名在传播过程中不断变化。

基于异常（也称为行为）的 IDS 通过统计差异分析系统来检测攻击。统计差异分析涉及基于过去行为（相似或相同活动）建立的“正常”系统、应用或网络行为模型。系统通过推理判断某行为是否与模型不同，若是则生成警报并采取行动。例如，如果端口 80 保留用于 HTTP 协议，网络数据包的头部和负载应符合特定配置。IDS 会分析端口 80 上传输的负载（如负载的字节频率），这是判断正常负载的一个指标。异常检测器会捕获 incoming payload 并与模型进行一致性或差异性比较；若 payload 与正常预期的 payload 差异过大，则被标记为异常。基于异常的 IDS 的缺点是会产生较多的误报，因为其决策是概率性的，即基于统计预测什么是攻击，但这些可以通过机器学习随时间调整。

启发式 IDS 在签名和异常 IDS 的基础上进行扩展，使用在系统运行时训练的机器学习模型。它们与基于异常的 IDS 类似，但能够根据实时“学习”来调整预防措施。它们也类似于基于签名的 IDS，需要一个比较数据库，即机器学习实时将活动与“测试”数据库中已知的正常和异常用户、系统和网络行为进行比较。因此，启发式 IDS 能够适应不断变化的攻击模式，但也可能产生大量误报，需要仔细调优和平衡，否则合法用户的通信可能被干扰，后果严重。

| Signature Detection | Signature detection is used by malware and virus scanners as well as IDSs. This is the most widely used method of threat detection. It consists of analyzing files and software for a pattern (e.g., regex) that is maintained in a database. The method is ineffective for new attacks or polymorphic malware. |
|---|---|
| Behavioral Detection | Behavioral detection is also used by malware/virus scanners and IDSs. It focuses on predicted versus actual behaviors of software and/or communications. For example, if an application attempted to disable security controls, it would be detected using this scheme, which would trigger some action, such as generate an alert or notification, block the execution of the program, and/or reset security settings, and so forth. |
| Heuristic Detection | A heuristic analysis examines code or communications properties using a variety of techniques. Static analysis involves deconstructing or decompiling a suspected application and scanning the source code for dangerous commands or malicious statements. With dynamic analysis, applications are sandboxed, meaning isolated in a controlled partition or virtual machine. The method examines the commands as they are executed and looks for suspicious activities such as self-replication, overwriting files, changing checksums on files, and so forth. We will cover code analysis in more detail shortly. |

### 11.3.2 IDSs and IPSs

IDS 是被动的，而入侵防御系统（IPS）是主动的。需要注意的是，许多 IDS 同时也是 IPS，统称为 IDPS。IDS 本质上是带有基本过滤规则的通知系统，行动范围有限；而 IDPS 通常与其他系统和防火墙集成，以执行修正和恢复策略。例如，如果 IDPS 检测到攻击来源 IP 地址，它会相应地在路由器和防火墙的规则库中添加丢弃该 IP 的数据包的规则。IDPS 可集成的范围从简单的 SNMP 陷阱到高级的启发式，从而能够“智能地”通过启动适当的反措施来防御攻击。主机基础的入侵检测系统通常与网络 IDPS 协同工作，例如在攻击期间恢复被恶意修改的设置。

对 IDS 和 IPS 的共同挑战是尽量减少误报并避免误负。误报会产生噪声，干扰操作人员和管理员，甚至导致他们错过真正的攻击。此外，攻击者可能使用“ feint”（ diversion）策略，在主要攻击使用另一条路径或攻击面的同时制造干扰。误报可以通过在分层或环形配置中部署 IDS 和 IPS 来降低，这种配置为攻击创造多个障碍，必须逐一突破。

在主机层面，IDPS 识别主机上的可疑活动，例如操作系统文件的修改。主机系统 IDPS 监控代理拦截操作并发起执行操作，以控制哪些修改是合法的，并记录活动；如果有被认为是威胁的操作尝试，它会采取如阻止进程执行等措施。网络 IDPS 检查针对主机的入侵或攻击的网络流量特征。这些技术采用一种称为“抓包”的方法，检查入站和出站数据包。上述组件共同构成了通常称为统一威胁管理（UTM）系统的体系（`/path/to/xxx`目录）(Figure 11.3)。

![FIGURE 11.3 Unified Threat Management (UTM) System](img/9781284236378_CH11_FIGF03.jpg)

FIGURE 11.3 Unified Threat Management (UTM) System

尽管有这些层层防御，仍需考虑诸多挑战。首先，签名数据库会过时，系统在大规模签名数据库中逐行查找效率低下，可能导致严重延迟。另一个挑战是需要捕获、检查和处理的流量体积巨大。复杂的网络拓扑进一步加剧了这一问题，因此必须构建多层防御，这又带来了更大的复杂性和潜在的故障点，这些故障点可能被复杂性本身所掩盖。此外，由于存储限制，许多甚至大多数组织会对日志数据的量设置配额。最后，由于层层叠加，触发机制的设计可能变得极其复杂。例如，当多个 IDS 系统之间或之内出现告警冲突时，需要谁来调解或去冲突？这需要仔细架构并针对生态系统进行精细调优。

| UTM || A Unified Threat Management system, or UTM, represents the multilayered IDPS layers and infrastructure that are displayed, represented, and controlled from an executive layer or executive contours in a distributed configuration. |
| --- | --- |
| IDPS Alerting Systems || IDPS alerting systems typically combine lightweight Hidden Markov Models (HMMs) to “game” agent or sensor data using move and countermove. They employ incremental-learning algorithms, which start with pattern-matching algorithms prior to engaging heuristic and artificial immune algorithms. |

### 11.3.3 Code and Application Scanning

我们在多次讨论恶意软件和病毒扫描后，本节将讨论程序代码（应用）扫描。代码和应用扫描属于应用安全（AppSec）范畴。实现此类扫描的方法多种多样，通常相互配合使用。主要的扫描技术包括（1）静态应用安全测试（SAST），（2）集成应用安全测试（IAST），（3）软件组成分析（SCA），以及（4）动态应用安全测试（DAST）。这些方法共同用于检测未编译代码、外部库、开源组件以及运行时代码中的威胁或漏洞。
