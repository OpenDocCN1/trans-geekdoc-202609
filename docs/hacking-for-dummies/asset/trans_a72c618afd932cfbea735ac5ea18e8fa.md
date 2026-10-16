
如果您希望在测试后休息，现在不是放松的时机。您的安全评估报告阶段是最关键的环节之一。最后一件事是进行测试、发现安全问题后就结束工作。请将时间和精力用于深入分析和记录您发现的问题，以确保安全漏洞被消除，从而提升信息安全性。报告是信息安全和风险管理所需的持续性审慎工作的重要组成部分。

报告包括对所有发现进行筛选，以确定哪些漏洞需要处理、哪些不重要。报告还包括向管理层或客户汇报发现的各类安全问题，并提供具体的改进建议。您共享已收集的信息，并指导其他相关方后续行动。报告也证明了在安全测试中投入的时间、精力和金钱被有效利用。

## Pulling the Results Together

当您拥有大量测试数据时——从您记录的屏幕截图和手动观察，到各类漏洞扫描器生成的详细报告——您该如何处理这些信息？您需要仔细审阅文档，挑出所有突出的区域。基于以下因素做出决策：

*   由评估工具给出的漏洞排名，通常基于 **Common Vulnerability Scoring System**。

*   您作为 IT/安全专业人员的知识（通常比工具提供的更有价值）。

*   漏洞的上下文及其对业务的影响。

![tip](images/tip.png)为了提供更多关于漏洞的信息，许多功能丰富的安全工具会为每个漏洞分配风险等级（基于整体风险），解释漏洞，给出可能的解决方案，并包含相关供应商网站链接、Common Vulnerabilities and Exposures 网站 (`https://cve.mitre.org`)、National Vulnerabilities Database (`https://nvd.nist.gov`)。为进一步研究，可参考供应商网站、其他支持站点和在线论坛，查看该漏洞是否影响您的系统和环境。总体业务风险是重点关注的对象。

在最终报告文档中，您可能希望按以下列表组织漏洞：

*   非技术性发现 

    *   社会工程学

    *   物理安全

    *   IT 与安全运营

*   技术性发现 

    *   网络基础设施

    *   防火墙规则集

    *   服务器和工作站

    *   数据库

    *   Web 应用

    *   移动应用

    *   移动设备

为更清晰地呈现，您可以在报告中为内部和外部安全漏洞、以及关键、高、中等优先级分别建立独立章节。最后提醒：最好在测试的规划阶段就确定具体的报告格式，这样从开始到交付结果的全过程，相关方都能保持一致。

## Prioritizing Vulnerabilities

发现的安全漏洞进行优先级排序至关重要，因为许多问题无法修复，或修复并不值得投入。您可能因技术原因无法消除某些漏洞，也可能因成本考虑无法负担消除其他漏洞。或者，业务本身对风险容忍度有特定要求。每种情况都不同。您需要判断修复的收益是否值得投入的时间和金钱。

例如，花费数周开发时间修复跨站脚本（XSS）和 SQL 注入漏洞可能非常值得，尤其是如果您因此受到第三方检查或失去潜在客户的影响。同样，对于普遍认为移动设备不存储敏感信息的假设，也需要仔细审视每个漏洞，评估业务风险，权衡是否值得修复。

![remember](images/remember.png)不可能——或者至少不值得——修复所有发现的漏洞。请仔细分析每个漏洞，确定最坏情况。例如，您的打印机 Web 界面可能存在跨站请求伪造（CSRF）漏洞，您需要评估其业务风险。或者，您可能会盲目相信网络上的所谓专家/黑客的意见，让他们决定您应集中精力的位置，尽管他们对您或您的业务一无所知。（这纯属玩笑。）另一个例子是，FTP 可能运行在大量内部服务器以及外部可访问系统上，您需要评估其业务风险。对于许多安全缺陷，您往往发现根本没有风险。

我发现，在安全——正如大多数生活领域一样——必须专注于高回报任务，否则会被琐事分散注意力，自我折磨，且难以实现自身目标。以下是一个快速的优先级排序方法，您可以根据自身需求进行微调。在发现每个漏洞时，请考虑以下两个主要因素：

*   **利用的可能性**：该漏洞被黑客、恶意用户、恶意软件或其他威胁利用的可能性有多大？

*   **利用的影响**：如果该漏洞被利用，会有多大的破坏性？

很多人往往跳过这些考量，假设每个发现的漏洞都必须修复。这是大错特错。仅凭发现漏洞就认为必须处理，而不考虑实际环境，会导致大量时间的、精力和金钱的浪费，甚至可能使长期安全评估计划走向失败。

![warning](images/warning.png)请注意，不要在相反方向过度偏移。表面上看似乎不严重的漏洞，若被利用仍可能给组织带来严重后果。务必深入挖掘，运用常识。

![tip](images/tip.png)使用高、中、低或 1 到 5 的评分（1 为最低优先级、5 为最高）等标准对每个漏洞进行排名。[Table 17-1](#c17.xhtml#c17-tbl-0001) 示例表格展示了各类别的样本漏洞。

[TABLE 17-1](#c17.xhtml#rc17-tbl-0001) Prioritizing Vulnerabilities

|  | **High Likelihood** | **Medium Likelihood** | **Low Likelihood** |
| --- | --- | --- | --- |
| **High impact** | Sensitive information stored on an unencrypted laptop | Tape backups taken offsite that aren’t encrypted and/or password-protected | No administrator password on an internal SQL Server system |
| **Medium impact** | Unencrypted emails containing sensitive information being sent | Missing Windows patch on an internal server that can be exploited with Metasploit | No passwords required on several Windows administrator accounts |
| **Low impact** | Outdated virus signatures on a securely segmented PC dedicated to Internet browsing | Employees or visitors gaining unauthorized network access | Weak encryption ciphers being used on a marketing website |

