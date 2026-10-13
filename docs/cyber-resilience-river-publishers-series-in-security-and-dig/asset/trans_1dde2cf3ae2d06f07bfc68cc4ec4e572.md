

此外，上述研究结果表明需要发生范式转变——从响应和恢复转向网络韧性。确实，最近构建能够在正常运行条件下有效抵御典型故障的响应和恢复企业系统的问题曾是首要任务之一。然而，在安全威胁空前增加的条件下，仅将重点放在确保响应和恢复上已不再足够。这需要一种构建企业网络韧性系统的新范式，该系统能够及时检测和预防网络攻击，并在发生网络攻击时“缓冲”冲击，降低破坏性影响的强度和性质，并将后果降至最低。此外，如有必要，这种“智能”防护体系应允许牺牲部分受保护基础设施的功能和组件，以实现业务恢复。

根据因诺波利斯大学的 `CSIRT` (`https://university.innopolis.ru/research/tib/csirtiu`) 数据，2018 年网络安全事件的平均流量为每天 **5700 万起事件**。关键安全事件的占比超过了 **18.7%**，即每五起事件中就有一起变得关键。这一动态与美国和欧盟领先的国际 `CERT/CSIRT` 进行的网络空间控制和网络安全威胁监测结果相关，也证实了著名网络攻击的调查结果：`STUXNET` (2010)、`Duqu` (2011)、`Flame` (2012)、`Wanna Cry` (2017)、`Industroyer` 和 `TRITON/TRISIS/HATMAN` (2018) 等。同时，未知且因此无法检测的网络攻击数量占可能总数的 **60% 到 40%**，这令人担忧。综上所述，所有这些表明，已知的网络安全、响应和恢复方法已不足以提供所需的网络韧性，也无法防止关键信息基础设施转入不可逆的灾难性状态。

上述情况构成了一个问题情境，其矛盾在于：在破坏性软件影响条件下，确保关键信息基础设施网络韧性的需求日益增长，而及时检测、预防和中和网络攻击的方法和手段却不完善。消除这一矛盾需要解决一个紧迫的科学技术问题——**在异构大规模网络攻击条件下组织信息基础设施的网络韧性**，该问题基于相似性理论、大数据收集与处理、流数据抽取、转换、加载 (`ETL`)、深度学习、语义和认知分析的新模型和方法。

## 研究与技术基础

自诞生以来，确保关键信息基础设施及相关信息的可靠性、响应、恢复和网络韧性问题，一直处于国内外领先研究人员的科学关注视野中。

我们这个时代的杰出科学家：`A. Turing`、`John von Neumann`、`M. Minsky`、`A. Church`、`S. Clini`、`D. Scott`、`Z. Manna`、`E. Dijkstra`、`C.A.R. Hoare`、`J. Backus`、`N. Wirth`、`D. Knut`、`R. Floyd`、`N. Chomsky`、`V. Tursky`、`A. A. Lyapunov`、`A. N. Kolmogorov`、`N. N. Moiseev`、`A. I. Maltsev`、`A. P. Ershov`、`V. M. Glushkov`、`A. A. Markov`，为软件工程作为一门科学学科的形成和发展做出了根本性贡献。他们奠定了理论和系统编程的基础，使得能够用数学严谨的方式研究可能的计算结构，研究可计算性质并建模可执行动作的计算抽象。领先的科学流派由此诞生，并通过将模型抽象自动综合为具体软件解决方案，在提高程序可靠性和持久性的方法发展方面做出了重大贡献。

例如，在俄罗斯，`俄罗斯科学院西伯利亚分院` (`RAS`) 在电路程序理论 (`A. P. Ershov`、`Yu. I. Yanov`、`V. E. Kotov`、`V. K. Sabelfeld`) 的发展、分析与应用验证的形成、程序正确性证明方法和变换综合 (`O. M. Ryakin`、`V. A. Nepomnyashchy`、`D. Ya. Levin`、`L. V. Chernobrod`)、算法基本性质和通用编程的研究 (`B. A. Trakhtenbrot`、`V. N. Kas’yanov`、`V. A. Evstigneev`)、抽象数据类型和指称语义的研究 (`V. N. Agafonov`、`A. V. Zamulin`、`Yu. L. Ershov`、`Yu. V. Sazonov`、`A. A. Voronkov`)、混合计算原理的发现和具体化编程的开创 (`A. P. Ershov`) 方面做出了重大贡献。

`莫斯科和圣彼得堡学术流派` 提出了基于知识程序自动综合 (`D. A. Pospelov`)、智能知识库和逻辑应用计算 (`L. N. Kuzin`、`V. E Wolfenhagen`)、智能编程 (`V. Strizhevsky`、`N. Ilinsky`)、可编程自动机综合 (`V. A. Gorbatov`)、程序生成器——`GENPAK` (`D. Ilyin`) 和智能任务求解器 (`Yu. Ya. Lyubarsky`、`E. I. Efimov`)、关联网络编程 (`G. S. Tseitin`)、可靠软件设计 (`V. V. Lipaev`)、基于形式规约的自动化软件测试 (`A. K. Petrenko`、`V. P. Ivannikov`)、超编程 (`E. A. Zhogolev`)、抽象程序综合 (`S. S. Lavrov`)、递归程序元模型综合 (`R. V. Freivald`)、问题环境中的元编程 (`V. V. Ivanischev`)、提高程序可靠性的主动方法 (`M. B. Ignatiev`、`V. V. Filchakov`、`A. A. Shtrik`、`L. G. Osovetsky`)、构建绝对可靠系统的方法 (`A. M. Polovko`)、符号建模方法论 (`Yu. G. Rostovtsev`) 等基本思想。

`圣彼得堡科学流派` 的科学家在算法 (`R. M. Yusupov`、`V. I. Sidorov`)、信息 (`Yu. G. Rostovtsev`、`B. A. Reznikov`、`S. P. Prisyazhnyuk`、`A. K. Dmitriev`)、技术 (`A. Ya. Maslov`、`V. Smagin`、`A. M. Polovko`)、软件 (`Yu. I. Ryzhikov`、`V. V. Kovalev`、`A. G. Lomako`、`V. I. Mironov`、`R. M. Yusupov`) 可靠性的概念形成和发展中发挥了重要作用。

`以 V. M. Glushkov 命名的乌克兰控制论研究所` 为代数 (`Yu. V. Kapitonova`、`A. A. Letichevsky`、`E. L. Yushchenko`) 和组合式编程 (`V. N. Redko`)、结构示意学、宏流水线计算和自动语法程序综合 (`V. M. Glushkov`、`E. L. Yushchenko`、`G. E. Tseitlin`)、生产性 `R-技术` 和多级设计、计算机系统生存性 (`A. G. Dodonov`) 奠定了基础。此外，为了证明程序的完备性、正确性和等价性，`V. M. Glushkov` 提出了一种算法代数系统工具。

`爱沙尼亚控制论研究所` 在可行的 `PRIZ` (`工程问题求解程序`) `系统` 中体现了程序自动综合的思想，并发展了概念编程和 `NUT 技术` 方向 (`E. H. Tyugu`、`M. Ya. Harf`、`G. E. Mints`、`M. I. Kahro`)。`拉脱维亚国立大学` 在归纳程序综合、符号测试、软件验证和调试的方法与工具领域取得了显著成果 (`Ya. M. Barzdin`、`Ya. Ya. Bichevsky`、`Yu. V. Borzov`、`A. A. Kalnins`)。

## 确保网络韧性的新任务

