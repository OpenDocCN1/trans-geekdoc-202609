

# 9 风险

取决于你从哪里获取新闻，你可能并不完全意识到世界正处于持续的网络战争之中。NotPetya 是世界历史上单次最具影响力的网络战争行为，发生于 2017 年。在 NotPetya 之前，曾发起过一款名为 Petya 的勒索软件攻击。起初，NotPetya 看起来很相似。主要区别在于，NotPetya 没有支付赎金以恢复其破坏数据的选项。这种攻击被称为 *wiper* 攻击，因为其唯一目的是使计算机数据存储不可读，将其擦除。[Figure 9.1](#c09.xhtml#c9-fig-0001) 是从受灾最严重的组织之一——航运和物流公司马士基（Maersk）的角度出发，对该次攻击的时间线。该时间线的来源是马士基前 IAM 服务所有者（IAM‐SO），他发表了关于该事件从内部看是什么样子的故事（Ashton [2020](#c09.xhtml#c9-bib-0002））。IAM‐SO 是一位经验丰富、技术高超的网络安全专业人员，专注于身份项目。在他的叙述中，他对马士基并非攻击目标却遭受如此沉重打击表示惊讶。

马士基的航运业务陷入停顿，期间购买了新笔记本电脑，并为原先自动化的业务流程迅速建立了手动替代方案。他们开始为客户重新路由或存放滞留货物提供报销，仅此一项支出就估计高达数百万美元（Greenberg [2020](#c09.xhtml#c9-bib-0006），第 196–199 页）。马士基董事会主席将总损失估计为 3 亿美元。此次攻击的全球总成本估计为 100 亿美元，甚至这个数字被认为低估了对全球供应链的附带损害。该次攻击被归因于网络威胁情报供应商于 2014 年昵称为 *Sandworm* 的威胁行为者，因为他们发现一份 PowerPoint 文件，其中威胁行为者将其一个攻击行动命名为“arrakis02”。威胁情报分析师是科幻迷，显然命名该行动的威胁行为者也是。Arrakis 是一本名为《沙丘》（Dune）的流行科幻书籍中的一颗行星名称，而 Sandworm 是该书英雄用来驱逐入侵者离开 Arrakis 的一种强大动物物种。虽然《沙丘》中的其他角色也是候选者，并且可能参与了与威胁行为者更相似的活动，因为在《沙丘》中，Sandworm 站在善与恶的一方，但《沙丘》中 Sandworm 的毁灭性力量使其成为 NotPetya 创建者的恰当类比（Greenberg [2020](#c09.xhtml#c9-bib-0006），第 1–17 页）。

![Figure 9.1 Maersk NotPetya Timeline](images/c09f001.jpg)

[**Figure 9.1**](#c09.xhtml#R_c9-fig-0001) 马士基 NotPetya 时间线

Sandworm 最终被确认为俄罗斯总参谋部主情报局（GRU）特殊技术中心（GTsST）军事部队 74455 的成员（MITRE, n.d.）。该组织至少自 2009 年起活跃，其成员于 2020 年因包括 NotPetya 在内的多次攻击被美国法院起诉（Department of Justice [2020](#c09.xhtml#c9-bib-0005））。在 NotPetya 之前的两年里，Sandworm 两次瘫痪了乌克兰电网。Sandworm 将 NotPetya 恶意软件植入了一家乌克兰税务软件公司，该公司被乌克兰所有主要机构和公司使用，对其客户而言，这看起来像是一次常规软件更新。正如美国的每个人都知道自己在 9/11 事件发生时在哪里一样，乌克兰的每个人都知道自己在 2017 年 6 月 27 日在哪里（Perlroth [2021](#c09.xhtml#c9-bib-0009），第 xxi–xxiv 页）。

像许多擅长技术但不认为自己是目标的公司一样，马士基拥有一支技术高超且经验丰富的技术团队，并能快速获得技术供应商的紧急响应服务。但他们缺乏的是安全架构设计。尽管如此，一种安全架构确实存在。它包括具有已知被利用漏洞的旧版操作系统。最小权限原则未被遵守。该架构包括集中式应用程序服务账户，这些账户被全球多个应用程序使用，并且在操作系统级别也具有管理访问权限。用户在自己的桌面和笔记本电脑上被授予本地管理访问权限，因此当 NotPetya 发生时，它通常以管理权限运行。没有有效的安全监控。幸运的是，马士基此前一直在尝试云服务，并在攻击前几周将用户账户数据上传到了云端。因此，尽管他们办公室的所有系统和数据中心的服务器都无法运行，但他们仍然可以授予用户访问基于云的电子邮件和办公软件服务的权限。

NotPetya 的故事寓意在于，它打破了某些控制薄弱的人仍然告诉自己的神话：“我不是目标”（Spafford et al. [2022](#c09.xhtml#c9-bib-0010)，第 66–69 页）。现在，NotPetya 多年之后，每个人都应该清楚，关于网络安全风险，首先需要知道的是：你不必是目标也会遭到攻击。

## 9.1 风险类别

采购通常会以信息请求（RFI）的形式，将需求提交给提供类似解决方案的多个供应商。作为回应，供应商将描述其技术如何满足每项要求。满足大部分要求的供应商将被邀请提交建议书请求（RFP）。提交最具吸引力建议书的供应商将被邀请安装概念验证（POC）系统，以测试技术是否符合用户预期，并能与企业系统良好集成。

此外，当采购某样东西并签订合同时，无论是软件还是服务，安全要求都会包含在该合同中。这样可以确保，如果供应商未能满足网络安全要求，企业会有追索权。请注意，是采购经理将所有这些安全标准和程序纳入其采购流程。CISO 通过提供网络安全专业知识，促进安全的采购流程。

## 参考文献

1. Bayuk, J. (2007). *Stepping Through the InfoSec Program*. Information Systems Audit and Control Association, IT Governance Institute (ISACA ITGI).

2. Bayuk, J. (2010). *Enterprise Security for the Executive: Setting the Tone at the Top*. Praeger.

3. COSO (2013). *Internal Control – Integrated Framework: Executive Summary, Framework and Appendices, and Illustrative Tools for Assessing Effectiveness of a System of Internal Control*. Committee of Sponsoring Organizations of the Treadway Commission.

4. COSO (2017). *Enterprise risk management: Integrating with strategy and performance*. Committee of Sponsoring Organizations of the Treadway Commission.

5. NACD (2021). National Association of Corporate Directors. *Principles for Board Governance of Cyber Risk*, Insight Report. [https://www.nacdonline.org/insights/publications.cfm?ItemNumber=71795](https://www.nacdonline.org/insights/publications.cfm?ItemNumber=71795) (accessed 08 May 2023).

6. NACD (2023). National Association of Corporate Directors. *Cyber‐Risk Oversight,* Director's Handbook Series. [https://www.nacdonline.org/insights/publications.cfm?ItemNumber=74777](https://www.nacdonline.org/insights/publications.cfm?ItemNumber=74777) (accessed 08 May 2023).

