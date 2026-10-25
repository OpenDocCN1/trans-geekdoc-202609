

与另一个应用程序相比。这可能是因为前者的开发人员受过更好的培训，或更有效地实现了框架。此类反馈应在下一个发布周期中回传到 SDL 的早期阶段。

## 修复报告

应从本阶段开始准备并定期更新修复报告/仪表板。本报告的目的是在技术层面展示产品的安全态势和风险。

## 6.7 指标

在 SDL 的此阶段应收集以下指标（其中一些可能与我们之前讨论过的指标重叠）。

- 符合公司政策的百分比（已更新）
  - 第 3 阶段与第 4 阶段的合规百分比
- 使用静态分析工具有效测试的代码行数
- 通过静态分析工具发现的安全缺陷数量
- 通过静态分析工具发现的高风险缺陷数量
- 缺陷密度（每 1000 行代码的安全问题数）
- 通过静态分析、动态分析、手动代码审查、渗透测试和模糊测试发现的安全问题的数量和类型
  - 不同类型测试发现的安全问题的重叠部分
  - 不同类型测试发现结果的严重程度比较
  - 将发现结果映射到先前识别的威胁/风险
- 已修复的安全发现数量
  - 发现结果的严重程度
  - 修复发现结果所花费的时间（小时，近似值）
- 未解决发现结果的数量、类型和严重程度
- 符合安全测试计划的百分比
- 执行的安全测试用例数量
  - 安全测试用例执行中发现的结果数量
  - 执行的重新测试数量

## 6.8 总结

在讨论设计与开发（A4）阶段时，我们描述了成功执行测试用例的流程、通过自动化工具和手动审查进行适当代码审查的流程，以及在 SDL 此阶段进行的隐私验证和修复流程。本章中描述的最关键的流程和程序是那些能够有效高效地测试、调整和修复已知漏洞，并确保遵循安全编码策略的流程和程序，这些流程和程序在进入 SDL 的产品发布（A5）阶段之前提供了必要的安全和隐私漏洞防护。

## 章节快速检查

1. 以下哪项不是主要的缓解方法：
   a. 锁定环境
   b. 输入验证
   c. 为旧版代码使用弃用的库
   d. 输出验证

2. 防御性编码的要素包括以下所有内容，除了：
   a. 自定义加密函数以避免算法泄露
   b. 异常处理以避免程序终止
   c. 接口编码工作以避免面向 API 的攻击
   d. 加密敏捷性以使加密函数更强大

3. 静态分析可用于检查：
   a. 批准的函数/库调用、与逻辑相关的规则和语义检查，以及线程性能管理
   b. 语法、批准的函数/库调用和竞态条件
   c. 语法、批准的函数/库调用和内存管理
   d. 语法、批准的函数/库调用，以及与逻辑和调用相关的规则和语义检查

4. 自动化测试相对于手动代码审查具有以下优势，除了：
   a. 检测不安全或弃用的函数调用
   b. 识别混淆的例程
   c. 分析速度
   d. 集成到 IDE

## 练习

以下练习基于附录 A 中讨论的案例研究。这些练习旨在让您练习应用步骤并为 SDL 的 A4 阶段产出交付物。

此时，您已制定了管理计划和路线图，以在 Revvin’ Engines 实施 SDL。拥有一个稳健的系统和流程，能够为反映业务需求以及应用程序的安全性和非功能性需求的基于 API 的微服务系统产生安全的架构和设计，您就可以确信应用程序和基础设施能够抵御敌对的公共互联网。

当您进入开发活动时，您需要制定开发时、单元测试时、集成测试时和预发布测试时的安全计划和路线图，以确保应用程序足够安全，可以发布到生产环境。

1. 重新审视初始测试计划，并包含您认为应用程序测试所需的所有活动——包括手动和基于工具的测试。

2. 设计流程，将测试活动集成到开发管道中，以实现可自动化的测试任务自动化。确保所有测试结果都报告给守门人功能，如果未满足扫描策略，则该功能将使构建失败。

3. 为每个扫描工具或流程建立所需的扫描器策略，以确定触发适当安全事件的通过/失败限制。

4. 确定所有强制性测试流程所需的指标，并确定最合适的报告方法和机制。

## 参考文献

1. Kaner, C. (2008 年 4 月). “探索性测试教程,” 第 36 页. 检索自 http://www.kaner.com/pdfs/QAIEexploring.pdf

2. Chmielewski, M., Clift, N., Fonrobert, S., and Ostwald, T. (2007 年 11 月). “MSDN 杂志：在您的应用程序发布之前查找并修复漏洞.” 检索自 http://msdn.microsoft.com/en-us/magazine/cc163312.aspx

3. Microsoft Corporation. (2012). “操作指南：为托管代码 (.NET Framework 2.0) 执行安全代码审查.” 检索自 http://msdn.microsoft.com/en-us/library/ff649315.aspx

4. 同上。

5. Jackson, W. (2009 年 2 月). GCN—公共部门 IT 的技术、工具和策略：“静态与动态代码分析：优势与劣势.” 检索自 http://gcn.com/Articles/2009/02/09/Static-vs-dynamic-code-analysis.aspx?p=1

6. Cornell, D. (2008 年 1 月). OWASP 圣安东尼奥演示：“测试应用程序安全的静态分析技术.” 检索自 https://1library.net/document/y94orglq-static-analysis-techniques-testing-application-security-antonio-january.html

7. Jackson, W. (2009 年 2 月). GCN—公共部门 IT 的技术、工具和策略：“静态与动态代码分析：优势与劣势.” 检索自 http://gcn.com/Articles/2009/02/09/Static-vs-dynamic-code-analysis.aspx?p=1

8. Cornell, D. (2008 年 1 月). OWASP 圣安东尼奥演示：“测试应用程序安全的静态分析技术.” 检索自 https://1library.net/document/y94orglq-static-analysis-techniques-testing-application-security-antonio-january.html

9. Jackson, W. (2009 年 2 月). GCN—公共部门 IT 的技术、工具和策略：“静态与动态代码分析：优势与劣势.” 检索自 http://gcn.com/Articles/2009/02/09/Static-vs-dynamic-code-analysis.aspx?p=1

10. Cornell, D. (2008 年 1 月). OWASP 圣安东尼奥演示：“测试应用程序安全的静态分析技术.” 检索自 https://1library.net/document/y94orglq-static-analysis-techniques-testing-application-security-antonio-january.html

11. Jackson, W. (2009 年 2 月). GCN—公共部门 IT 的技术、工具和策略：“静态与动态代码分析：优势与劣势.” 检索自 http://gcn.com/Articles/2009/02/09/Static-vs-dynamic-code-analysis.aspx?p=1

12. Cornell, D. (2008 年 1 月). OWASP 圣安东尼奥演示：“测试应用程序安全的静态分析技术.” 检索自 https://1library.net/document/y94orglq-static-analysis-techniques-testing-application-security-antonio-january.html

13. 开放 Web 应用程序安全项目 (OWASP). (2012). “模糊测试.” 检索自 https://www.owasp.org/index.php/Fuzzing

14. R2Launch. (2012). “模糊测试.” 检索自 http://www.r2launch.nl/index.php/software-testing/fuzz

15. 开放 Web 应用程序安全项目 (OWASP). (2012). “测试指南简介.” 检索自 https://www.owasp.org/index.php/Testing_Guide_Introduction#Manual_Inspections_._26_Reviews

