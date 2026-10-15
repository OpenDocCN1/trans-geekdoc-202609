
IDS 和基础设施监控可以集中化，也称为无代理，或者可以是分布式的，也称为基于代理。在基于代理的配置中，会在被监控的设备上部署软件代理，并将数据发送到服务器，由服务器负责管理和显示。最常见的是基于 SNMP 的监控。两者都有优缺点。集中化或无代理系统的可扩展性不如基于代理的系统，且在检测时可能会出现过大的延迟。在基于代理的系统中，代理软件必须在每个被监控设备上安装和维护。有时会使用代理作为中间件，以提供一定的灵活性，并允许从一组被监控节点聚合监控数据，跨越网络边界到管理服务器，但这些方法也有局限性。虽然还有其他技术，但大多数 IDS 都与安全信息和事件管理系统（SIEM）协同工作。SIEM 整合多个来源的输出，并使用过滤器识别恶意活动。最有效的 IDS 最大化真实威胁的发现，使得漏检的攻击（即 false negatives）数量极少，同时最小化误报（即 false positives）。SolarWinds Security Event Manager® 是一个 SIEM 的示例（[Figure 11.2](#9781284211658_CH11_03.xhtml#c11-fig0002)）。

![FIGURE 11.2 SolarWinds Security Event Manger (SEM) ¶ © 2021 SolarWinds Worldwide, LLC. All rights reserved.](images/9781284236378_CH11_FIGF02.jpg)

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

