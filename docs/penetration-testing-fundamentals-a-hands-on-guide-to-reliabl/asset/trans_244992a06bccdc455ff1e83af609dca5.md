
测试，显然 PCI 标准正在接受测试；然而，可能还有其他标准也应被测试。

一旦这些概念得到解决，PCI DSS 采用了一个相当简单的三阶段方法，但每个阶段都有特定的要求。你可以在表 2-1 中看到这些要求的摘要。

### Table 2-1 PCI DSS Phases and Requirements
| Pre-Engagement | Actual Test | Post-Engagement |
|---|---|---|
| Scope | Application layer | Remediation |
| Documentation | Network layer | Retesting identified vulnerabilities |
| Rules of engagement | Segmentation | Cleaning up |
| Environment | How to handle cardholder data | Reporting |
| Success criteria | Post-exploitation |  |
| Pass vulnerability scans |  |  |

## NIST 800-115
国家标准与技术研究院是美国的一个组织，制定了许多标准，其中许多与网络安全相关。对渗透测试人员来说特别感兴趣的是 NIST 800-115，《信息安全测试与评估技术指南》。正如该标准标题所暗示的，它是测试的通用指南，而不仅仅是渗透测试。

该标准包含一些与渗透测试无关的项目，例如文档审查、日志审查和类似项目。这些问题更适合在安全审计中涵盖。应注意，进行审计先于渗透测试并指导其重点是完全合适的。

NIST 800-115 使用三个阶段：
- Planning
- Execution
- Post-Execution

这可能看起来像是一个相当简化的计划，但这些阶段各自都很健全且详细。我们将在以下各节中更详细地介绍每个阶段。

### Planning
规划是区分渗透测试与黑客攻击的项目之一。黑客攻击可能有计划也可能没有计划，如果有计划，计划可能非常灵活。然而，专业的渗透测试应像工程项目一样进行，这意味着详细的计划至关重要。

规划中要解决的第一个问题是确定目标。你到底想完成什么？“测试系统安全”这样模糊的答案是完全不够的。在规划渗透测试时，你的目标应具有军事般的精确度。一个好的示例目标可能是“针对 OWASP Top 10 漏洞测试电子商务服务器。”我们将在本章稍后详细介绍 OWASP；目前只需了解它是一个关注网络安全并发布 Top 10 漏洞列表的组织。

你目标的主要问题是它们必须具体到可衡量。模糊的目标很难衡量，通常也提供不了有意义的指导。与目标相关的是范围问题。说你要测试一切固然很美好，但在任何规模较大的网络中，这根本不可能。你需要选择一个既可管理又能有效解决安全问题的范围。做到这一点的方法是让过去的事件报告、漏洞扫描和安全审计来帮助你决定渗透测试的范围。

### Execution
测试的执行实际上分为三个子阶段。其中第一个是网络发现。你只是尝试找出目标网络上有什么。有许多工具，我们将在本书后面介绍，可以帮助你枚举整个网络。

在枚举网络之后，你需要识别漏洞。必须牢记，漏洞扫描不是渗透测试；然而，漏洞扫描是指导渗透测试的一种方式。换句话说，尝试利用一个对你试图进行的攻击并不脆弱的目标系统是不会取得任何成果的。在后面的章节中，你将看到各种可以帮助你识别漏洞的工具。表 2-2 来自 NIST 800-115 文档（在该文档中是表 4-1），描述了发现技术。

### Table 2-2 NIST 800-115 Discovery Techniques
| Technique | Capabilities |
|---|---|
| Network Discovery | Discovers active devices<br>Identifies communication paths and facilitates determination of network architectures |
| Network Port and Service Identification | Discovers active devices<br>Discovers open ports and associated services/applications |
| Vulnerability Scanning | Identifies hosts and open ports<br>Identifies known vulnerabilities (note: has high false positive rates)<br>Often provides advice on mitigating discovered vulnerabilities |
| Wireless Scanning | Identifies unauthorized wireless devices within range of the scanners<br>Discovers wireless signals outside of an organization's perimeter<br>Detects potential backdoors and other security violations |

最后，是时候尝试利用这些漏洞了。这是实际使用黑客技术的子阶段。在此阶段，你尝试各种技术来入侵目标系统。

实际的渗透测试，即攻击阶段，被划分为一个四步流程。步骤是 planning-discovery-attack-reporting。你可以在图 2-3 中看到这一点。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_51_0.png)

FIGURE 2-3 Pen Testing Steps.

之所以将其呈现为一个循环有两个原因。第一个原因是，如果之前进行过渗透测试，那么在当前测试中计划的一项内容就是测试之前渗透测试中发现的问题。实质上，检查这些问题是否已得到纠正。第二个原因将其呈现为循环是，在渗透测试过程中，你可能会执行一次攻击，审查结果，而这可能会引导你进行其他应执行的攻击。例如，如果你发现某个站点容易受到 SQL 注入攻击，那么测试跨站脚本攻击也是合理的。

### Post-Execution
Post-execution 不仅仅是一个涵盖实际攻击后你所做一切的笼统短语。此阶段与其它阶段一样关键。第一个目标是确保你没有留下任何开放的系统。如果你入侵了一个系统，在测试结束后，尽可能关闭该入侵点。

你还需要创建一个报告。该报告应相当详细，并应显示你所做的一切以及结果。如果一次入侵尝试失败，记录它与记录成功的入侵一样重要。此外，当你成功入侵系统时，你需要提供你是如何做到的细节。

报告中最重要的部分是补救措施。你的报告应记录目标网络如何修复你发现的漏洞。渗透测试的最终目标是在攻击者发现它们之前找到弱点并加以纠正。

NIST 800-115 非常详细，并讨论了你应尝试的具体攻击，例如密码破解、社会工程学、边界检查等。即使你不执行需要符合 NIST 800-115 的渗透测试，阅读该标准也是一个好主意。

## National Security Agency InfoSec Assessment Methodology (NSA-IAM)
国家安全局信息安全评估方法论（NSA-IAM）描述了三个总体阶段，每个阶段又细分为在该阶段进行的特定任务。

- Pre-Assessment
  - Determine and manage the customer's expectations
  - Gain an understanding of the organization's information criticality
  - Determine customer's goals and objectives
  - Determine the system boundaries
  - Coordinate with customer
  - Request documentation
- On-Site Assessment
  - Conduct opening meeting
  - Gather and validate system information (via interview, system demonstration, and document review)
  - Analyze assessment information
  - Develop initial recommendations
  - Present out-brief
- Post-Assessment
  - Additional review of documentation
  - Additional expertise (get help understanding what you learned)
  - Report coordination (and writing)

对于任何渗透测试人员来说，这个广泛概述中有许多值得注意的地方。请注意，在预评估阶段有一项内容是管理客户期望。有人雇佣你进行渗透测试。为了避免日后出现误解和不满，客户必须完全了解渗透测试会做什么，以及不会做什么。

此外，在预评估阶段，NSA-IAM 要求你了解目标网络的关键性以及客户的目标和目的。这是有针对性的渗透测试的一部分。我们已经讨论过，试图测试一切是不切实际的。通过了解哪些系统对该组织最关键，并了解客户的目标和目的，你可以有效地为渗透测试选择正确的目标。

我还想请你注意后评估阶段的一个具体项目。那就是获取专业知识来协助你。任何人都无法知道一切。如果你的渗透测试涉及你可能不具备专业知识的技术，那么你应该寻求一位是

