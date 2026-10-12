
尽管 DevSecOps 提供了一种新颖的方法论来解决 DevOps 与网络安全之间的问题，并使安全在开发过程中成为每个人的工作，但从 DevOps 向 DevSecOps 的迁移之旅并不容易，它需要文化或思维模式的转变，需要建立新的治理、工作流和流程，并采用新技术。在此，实施 DevSecOps 的挑战主要分为以下两大领域。

### 13.4.1 技术挑战

软件开发是一个复杂的过程，可能会使用不同的编程语言、大型源代码仓库和杂乱的开源库及包。DevSecOps 需要能够支持所有这些。不幸的是，到目前为止，市场上可用的 DevSecOps 工具并不多。此外，许多 DevSecOps 工具尚不成熟，仍存在弱点，这可能会减缓 DevSecOps 工具的推广和广泛采用。更多细节将在下一节讨论。

### 13.4.2 人员/文化挑战

与技术挑战相比，最大的挑战来自人员。安全往往是事后诸葛亮，在软件开发生命周期中关联度差，因此人们通常缺乏足够的网络安全意识。此外，许多开发人员认为网络安全是专门的网络安全部门或团队的工作，而 DevSecOps 只是额外的工作。

2018 年，Threat Stack [6] 进行了一项调查，表明 52% 的公司为了满足业务截止日期或目标而削减了安全预算。该报告还考察了 DevSecOps 为何在大多数组织中未能成为现实的主要原因，即缺乏高级管理层的支持，他们热衷于业务交付而非网络安全。如果没有高级管理层的认可从上到下推广 DevSecOps，团队要广泛采用 DevSecOps 将会困难且缓慢。

### 13.5 DevSecOps 最佳实践

为了克服上述实施 DevSecOps 的挑战，并最终在公司建立 DevSecOps 文化，必须采用 DevSecOps 最佳实践，同时考虑新技术、新流程和思维模式的转变。

#### 13.5.1 技术创新

技术使 DevSecOps 流程得以正确执行，并确保安全缺陷在软件开发生命周期的早期阶段被发现，而不是在末期甚至在客户端才被发现。

##### 自动化安全 — 在持续交付中自动化安全测试

为了消除网络安全评估导致的 DevOps 流程瓶颈，自动化是关键解决方案。通过 `CI/CD` 流水线运行静态和动态安全分析，自动化安全源代码扫描和二进制扫描，从而加快安全代码交付。在集成开发环境（`IDE`）中集成安全工具将进一步帮助开发人员在编码阶段检测和修复漏洞，这比持续集成阶段更早。此外，部署前/后的审计和扫描使企业能够全面了解其风险状况。

##### 安全仪表盘 — 可视化技术安全债务

安全测试工具发现的安全问题或漏洞需要被报告、显示在仪表盘上，并对所有人可见。安全仪表盘可被视为对开发人员的反馈，以便在每个迭代开发过程中持续跟踪技术安全债务的改进情况。相关的安全问题分析和学习教程也能帮助开发人员以更高效的方式修复漏洞并减少技术安全债务。此外，可视化的安全仪表盘将有助于在开发团队的管理层（安全愿景与意识）和开发人员（在日常工作中轻松跟踪和修复安全问题）两方面建立 DevSecOps 文化。

##### 安全门禁 —— 在开发流水线中集成风险控制

需要在开发过程的不同阶段增加安全门禁，作为控制风险的检查点。可在安全门禁处设置多个条件，以满足特定的安全质量阈值（例如，零关键漏洞）。如果扫描结果未通过安全门禁的条件，流程将被阻断，直到开发人员修复相关漏洞以满足条件为止。安全门禁提供了一种方案，保证开发人员交付高质量、安全的代码，并将漏洞风险降至最低地投入生产环境。

##### 安全即代码

代码驱动的自动化配置管理工具（如 `Chef`、`Ansible` 和 `Puppet`）可利用通用模板轻松在数百台服务器上建立标准化配置，从而将黑客利用未修补服务器的风险降至最低。在此基础上，在制作 `Chef` cookbooks、`Ansible` playbooks 和 `Puppet` manifests 时应考虑网络安全，以确保基础设施配置管理自动化解决方案足够安全。

##### 新安全流程

DevSecOps 的最终目标之一是创建可重复的工作方式，以确保安全的透明度。例如，需要创建一个短小的、反馈驱动的、整体的基于模型的安全循环，以快速识别问题、迅速响应，并推动流程改进和文化变革。此外，还需要建立处理安全问题的机制和程序。例如，如何处理从源代码、开源包等中发现的安全问题；或如何像管理软件问题或业务任务一样管理安全问题。

#### 13.5.2 文化与思维模式的转变

改变人们习惯的工作方式极具挑战性，因此文化和思维模式的转变并不容易，通常需要数年才能实现。有许多不同的方法可以影响人们，最终使他们接受新的工作方式。

##### 持续的培训与教育

良好的培训确保标准得到正确实施，并让开发人员更快地获得所需知识。安全培训可通过多种渠道开展，如在线培训课程、工具、教程和咨询，学习媒介需要灵活且量身定制，以帮助开发人员轻松了解黑客行为、不同漏洞及其修复方案。

##### DevSecOps 推动者

DevSecOps 推动者是一个新角色，要求具备 DevOps 和网络安全两方面的合格专业经验。DevSecOps 推动者负责通过协调和连接开发团队与网络安全团队、在 `CI/CD` 流水线中自动化 DevSecOps 工具、跟踪安全问题，最终帮助团队从 DevOps 转型为 DevSecOps。

##### 业务参与

与 DevOps 类似，业务方是推动 DevSecOps 的利益相关者。在此基础上，业务方需要理解 DevSecOps 的价值，并最终提供全力支持以推行 DevSecOps 转型。

##### 安全演练与活动

组织安全活动，如安全编码竞赛、安全讲座、安全游戏等，将逐步改变人们的思维模式，并在开发团队中建立 DevSecOps 文化。

### 13.6 DevSecOps 工具

DevSecOps 工具的主要目的是帮助开发团队在软件开发生命周期（SDLC）的不同阶段发现并可视化安全漏洞。应用安全工具分为以下几类：

*   静态应用安全测试（SAST）工具
*   动态应用安全测试（DAST）工具
*   交互式应用安全测试（IAST）工具
*   软件成分分析（SCA）工具

#### 13.6.1 静态应用安全测试（SAST）工具

根据近期统计数据，超过 50% 的安全漏洞源于编码。开发人员通常更关注业务功能，因此往往忽视安全开发实践，且缺乏网络安全知识，这将导致源代码中存在潜在风险或漏洞。为了从一开始就将风险降至最低，需要在源代码层面实施安全测试方案。

静态应用安全测试（SAST）工具，也称为“白盒安全测试”工具，是一套旨在分析应用源代码、字节码和二进制代码的编码及设计条件的技术，这些条件表明存在安全漏洞。SAST 解决方案还能在不执行底层代码的情况下确保符合编码规范和标准，因此能在非运行状态下从“内向外”分析应用。以下是 SAST 的一些优缺点（图 13.2）：

![](img/p434.jpg)

**图 13.2.** SAST 10 维雷达图

**优点：**

*   准确锁定导致漏洞的代码位置。
*   原理易于理解，为开发人员所接受。

**缺点：**

*   准确性差、误报率高，因此需要额外投入资源来验证结果。
*   随着代码量增加，扫描速度变慢。

总体而言，SAST 易于理解，并能标记源代码问题以帮助开发人员轻松修复。然而，导致额外成本的高误报率是阻碍 SAST 广泛采用的主要问题。

市场上有几款流行的 SAST 商业产品 —— `Checkmarx`、`Fortify`、`IBM Appscan` 等。`Checkmarx` 是一种源代码分析解决方案，提供工具用于识别、跟踪和修复源代码中的技术和逻辑缺陷，如安全漏洞、合规性问题和业务逻辑问题。它支持大量编程语言和框架（即 `Java`、`JavaScript`、`.NET`、`ASP`、`C/C++`、`PHP`、`Spring`、`Node.js`），并可轻松集成到 `CI` 流水线中，连接源代码管理（SCM）系统，在签入/按计划时扫描源代码，以自动化漏洞扫描流程。`IBM AppScan` 是另一个 SAST 工具示例，可在源代码级别运行，检测可能的安全漏洞，如 OWASP Top 10 发布的漏洞，即 SQL 注入、XSS 等。

#### 13.6.2 动态应用安全测试（DAST）工具

动态应用安全测试（DAST），也称为黑盒测试（即从外向内测试），旨在检测应用在运行状态下表明存在安全漏洞的条件。在此基础上，DAST 可称为“行为测试”，因为问题不特定关联到某个代码模块，而是发生在使用过程中。DAST 一直被视为主要的应用安全技术和工具之一，主要用于发布到生产环境之前。

![](img/p436.jpg)

**图 13.3.** DAST 10 维雷达图

DAST（图 13.3）擅长发现外部可见的问题和漏洞，且仅需提供 URL 即可轻松运行。DAST 不依赖任何语言或平台。与 SAST 相比，扫描结果更准确，且无需花费大量精力进行验证。然而，DAST 的缺点是严重依赖专家编写安全用例，导致难以扩展。此外，它无法锁定漏洞来源的具体位置。由于其“攻击行为”特性，可能会向测试环境引入“脏数据”。

关于市场上流行的 DAST 工具 —— `IBM AppScan`、`AWVS` 和 `Web Inspect` 均为商业 DAST 产品，而 `OWASP ZAP` 是 OWASP 社区提供的开源 Web 安全工具，由志愿者维护。`OWASP ZAP` 功能足够且简单易用，它帮助开发团队在开发和测试应用程序时自动发现 Web 应用程序中的漏洞。你只需输入 URL 地址并点击“Attack（攻击）”按钮，几分钟内即可开始并获取结果。在“Alerts（警报）”部分，将显示 `OWASP ZAP` 检测到的每个单独漏洞，以及其名称、URL 地址、风险级别、可靠性和参数。此外，它还会显示问题的可能解决方案，以帮助开发人员消除 Web 应用程序的任何风险。总体而言，`OWASP ZAP` 是一款用于运行渗透测试以发现 Web 应用程序风险和漏洞的高级开源工具。

为了实现 DAST 流程自动化，`OWASP ZAP` 可以与 `Jenkins` 集成（参见图 13.4）。首先，需要在 `Jenkins` 实例上安装 `Jenkins OWASP ZAP` 插件。接下来，在 `Jenkins` 的“Configure System（系统配置）”部分配置该插件，例如主机地址和端口。配置完成后，需创建一个构建任务并提供相关配置信息。任务设置好后，`Jenkins` 将能够自动触发 `OWASP ZAP` 对 Web 应用程序运行渗透测试。最后，测试结果将生成并在 `Jenkins` 仪表盘向用户提供反馈。

#### 13.6.3 交互式应用安全测试（IAST）工具

IAST（交互式应用安全测试）是一项新兴技术，它通过自动化测试、人工测试人员或任何与应用程序功能进行“交互”的活动，在应用程序运行时分析其安全漏洞。它实时报告漏洞，这意味着不会给你的 `CI/CD` 流水线增加任何额外时间。IAST 在应用程序内部工作，这使其区别于 SAST 和 DAST。这种测试类型也不测试整个应用程序或代码库，而仅测试功能测试所覆盖的部分。

![](img/p437.jpg)

**图 13.4.** OWASP ZAP 由 Jenkins 自动触发以对 Web 应用程序运行渗透测试

![](img/p438.jpg)

**图 13.5.** IAST 10 维雷达图

IAST 的设计旨在结合 SAST 和 DAST 的优势（图 13.5）。IAST 在应用程序中安装一个 Agent，并实时执行所有分析以分析整个应用程序，例如所有代码、HTTP 请求和响应、控制流和数据流信息、配置信息、库、框架等。对如此大量信息的访问使 IAST 引擎能够比 SAST 或 DAST 产生更准确的结果。

市场上有几款 IAST 产品。`Contrast Security` 就是一款 IAST 工具，它以被动方式评估正在运行的应用程序的安全状况。它适用于在 `CI` 流水线中拥有完全自动化测试能力的团队。该解决方案的开发要求将 Agent 与被评估的应用程序集成。一旦设置完成，随着应用程序的使用，结果将反馈给管理服务器。

![](img/p439.jpg)

**图 13.6.** SAST、DAST 和 IAST 的对比

图 13.6 提供了 SAST、DAST 和 IAST 之间的对比。下方的表 13.1 给出了 SAST、DAST 和 IAST 的更多详细信息。

#### 13.6.4 软件成分分析工具

免费和开源软件允许用户和开发人员编辑、修改或重用软件的源代码。这使开发人员有机会更高效地开发软件。由于免费和开源软件通常由第三方开发和共享，存在潜在的安全风险，因此开发人员经常下载并使用未知的、有漏洞的开源组件和框架。

软件成分分析（SCA）是一种验证应用程序中使用的第三方库、框架、插件和组件潜在漏洞的技术。换句话说，所有非你和你的团队编写的代码，都应由 SCA 工具进行考量。不同于 DAST 和 IAST，SCA 工具不在应用程序运行时在应用程序内部运行安全扫描。相反，SCA 工具分析依赖项列表，将其与已知漏洞依赖项列表进行交叉引用，然后将匹配的依赖项作为发现结果报告。

**表 13.1.** SAST、DAST 和 IAST 的对比

![](img/p440.jpg)

2020 年，DevSecOps 社区调查 [[4]](#chap13.xhtml#rref4) 显示，开源安全风险迅速扩大，归因于开源组件或依赖项漏洞的泄露事件从 2017 年到 2018 年增加了 50% 以上。尽管自 2018 年以来开源组件相关的泄露事件持续下降，但仍频繁发生。

市场上有多款 SCA 产品。`Sonatype IQ Server` 和 `JFrog Xray` 均为商业产品，而 `OWASP Dependency-Check` 是 OWASP 社区提供的免费 SCA 工具。`Dependency-Check`（参见图 13.7）旨在检测项目依赖项中包含的公开披露漏洞。核心引擎包含一系列分析器，用于检查项目依赖项并收集有关依赖项的信息片段。它通过确定给定依赖项是否存在通用平台枚举（CPE）标识符来实现这一点。如果发现漏洞，它将生成一个报告，链接到相关的通用漏洞披露（CVE）条目。

为了实现安全问题扫描自动化，`Dependency-Check` 可以与 `Jenkins` 集成，以便自动触发并生成结果。首先，需要在 `Jenkins` 实例上安装 `Jenkins OWASP Dependency-Check` 插件及其相关依赖。接下来，在 `Jenkins` 的“Configure System（系统配置）”部分配置 `Dependency-Check` 插件。配置完成后，需创建一个构建任务，以便 `Jenkins` 能够自动触发 `OWASP Dependency-Check` 运行开源漏洞扫描。最后，测试结果将生成为 HTML 文件并显示出来。

![](img/p441.jpg)

**图 13.7.** OWASP Dependency-Check

### 13.7 案例研究：某银行的 DevSecOps 实施

In the previous sections, we discussed the importance of DevSecOps for fintech companies and detailed DevSecOps, including its current state, challenges, best practices, tools, etc. After understanding DevSecOps, you may be more interested in how to implement DevSecOps in a fintech company and what it takes to achieve this goal. In this section, we will take a large global bank (referred to as Bank B) as an example, using its DevSecOps transformation program as a case study to demonstrate how to implement DevSecOps and ultimately win the benefits of DevSecOps for development teams, while establishing a DevSecOps culture and mindset.

#### 13.7.1 Background

Bank B has been running an enterprise-level DevOps program for two years since 2016. It invested heavily in toolchains to automate processes and in agile training to change people's mindsets. "Double the release frequency, halve the business incidents" was used to measure the outcomes of application teams adopting DevOps. After 2 years of the DevOps program, the overall DevOps maturity of development teams improved to the expected level. Although some legacy applications remain difficult to adopt DevOps, most application teams improved during the DevOps transformation, accelerating delivery speed, developing higher-quality products, and saving costs, which greatly benefits their competitiveness in the financial market.
