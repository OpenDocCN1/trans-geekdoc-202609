
SQL injection attacks allow a malicious individual to directly perform SQL transactions against the underlying database, in violation of the isolation model shown in Figure 21.2.

In the example used earlier, a bank customer might enter an account number to gain access to a dynamic web application that retrieves current account details. The web application must use a SQL query to obtain that information, perhaps of the following form, where `<number>` is the account number provided by the user on the web form:

```
SELECT *
FROM transactions
WHERE account_number = '<number>'
```

There’s one more important fact you need to know: Databases will process multiple SQL statements at the same time, provided that you end each one with a semicolon.

If the web application doesn’t perform proper input validation, the user may be able to insert their own SQL code into the statement executed by the web server. For example, if the user’s account number is 145249, they could enter the following:

```
145249'; DELETE * FROM transactions WHERE 'a' = 'a
```

The web application would then obediently plug this into the `<number>` field in the earlier SQL statement, resulting in the following:

```
SELECT *
FROM transactions
WHERE account_number ='145249'; DELETE * FROM transactions WHERE 'a' = 'a'
```

Reformatting that command slightly, you get the following:

```
SELECT *
FROM transactions
WHERE account_number ='145249';
DELETE *
FROM transactions
WHERE 'a' = 'a'
```

这是一个有效的 SQL 事务，包含两条语句。第一条语句从数据库中检索所需信息。第二条语句删除数据库中存储的所有记录。Whoops！

### 防范 SQL 注入

你可以使用三种技术来保护你的 Web 应用免受 SQL 注入攻击：

**使用预处理语句** Web 应用的开发人员应利用预处理语句来限制应用执行任意代码的能力。预处理语句（包括参数化查询和存储过程）在数据库服务器上存储 SQL 语句，仅由拥有适当访问权限的数据库管理员和开发人员修改。Web 应用调用预处理语句时，只能传递参数，不能修改其底层结构。

**执行输入验证** 如前面在跨站脚本章节中所述，输入验证允许你限制用户在表单中提供的数据类型。在我们前一节提供的 SQL 注入示例中，移除输入中的单引号字符（`'`）将阻止此攻击的成功使用。最强、最安全的输入验证方式是白名单验证，开发人员指定预期输入的确切性质（例如，小于 1024 的整数或少于 20 个字符的字母数字字符串），代码在将其提交到数据库之前验证用户提供的输入是否符合预期模式。

**限制账户权限** Web 服务器使用的数据库账户应拥有尽可能小的权限集合。如果 Web 应用仅需检索数据，则应仅授予该权限。在示例中，如果账户仅拥有 `SELECT` 权限，则 `DELETE` 命令将失败。

### 勘察攻击

虽然恶意代码通常依赖于诱导用户打开或访问恶意软件，但其他攻击直接针对机器。执行勘察可以让攻击者发现弱点，以便直接用其攻击代码进行针对。为辅助此定位，攻击者工具开发人员创建了许多自动化工具来执行网络勘察。在以下章节中，我们将介绍三种自动化技术——IP 探测、端口扫描和漏洞扫描——并说明这些技术如何通过更具物理强度的“桶子潜水”（dumpster-diving）技术进行补充。

#### IP 探测

`IP 探测`（也称为`IP 扫描`或`ping 扫描`）通常是针对目标网络执行的第一种网络勘察技术。使用此技术，自动化工具简单尝试向范围内的每个地址发送 ping 请求。响应 ping 请求的系统会被记录以供进一步分析。未返回响应的地址被认为是未使用的，并被忽略。

IP 探测在当今互联网上极为普遍。事实上，如果你配置一个具有公共 IP 地址的系统并将其连接到互联网，开机后几小时内很可能收到至少一个 IP 探测。这种技术的广泛使用凸显了至少对外部用户禁用 ping 功能的强烈理由。

#### 端口扫描

在执行 IP 探测后，攻击者会得到网络中活动系统的列表。接下来的任务是选择一个或多个系统进行进一步攻击。攻击者通常有特定的目标类型；Web 服务器、文件服务器以及支持关键操作的其他服务器是理想目标。

为缩小搜索范围，攻击者使用`端口扫描`软件对网络中所有活动系统进行探测，确定每台机器上运行的公共服务。例如，如果攻击者想要目标是一台 Web 服务器，他们可能运行端口扫描以查找任何在端口 80（超文本传输协议 HTTP 的默认端口）上运行服务的系统。管理员应利用这些信息禁用系统上不必要的服务。这样可以减少系统的攻击面，使攻击者更难以找到立足点来发起攻击。

#### 漏洞扫描

第三种技术是`漏洞扫描`。一旦攻击者确定要目标的具体系统，他们需要发现该系统中的特定漏洞以便获得所需的访问权限。网络上有许多用于此目的的工具。其中一些更流行的工具包括 Nessus、OpenVAS、Qualys、Core Impact 和 Nexpose。这些包包含已知漏洞的数据库，并探测目标系统以查找安全弱点。随后，它们会生成非常吸引人的报告，详细列出所有已检测到的漏洞。从那时起，只需找到针对特定漏洞的脚本并对受害者发起攻击即可。

需要注意的是，漏洞扫描器是高度自动化的工具。它们可以用于针对特定系统发起攻击，但攻击者更可能使用一系列 IP 探测、端口扫描和漏洞扫描来缩小潜在受害者的列表。然而，入侵者通常会对整个网络运行漏洞扫描，以查找任何可被利用的弱点。

再次强调，及时更新操作系统到最新的安全补丁水平可以修复漏洞扫描器几乎报告的所有弱点。此外，明智的系统管理员会学会像敌人一样思考——在上级管理层的许可下，他们会在自己的网络上下载并运行这些漏洞扫描器，以查看可能向潜在攻击者揭示的安全漏洞。这使他们能够迅速集中资源，加固网络中最薄弱的环节。

### 伪装攻击

获得访问你本不应拥有的资源的最简单方式是冒充拥有适当访问权限的人。在离线世界，青少年常借用哥哥的驾照购买酒精，电脑安全世界也是如此。攻击者冒用合法用户和系统的身份，以获得第三方的信任。在以下章节中，我们将探讨两种常见的伪装攻击——IP 伪造和会话劫持。

#### IP 伪造

在`IP 伪造攻击`中，恶意个人只需重新配置其系统，使其拥有受信任系统的 IP 地址，然后尝试访问其他外部资源。这在许多缺乏适当过滤规则的网络中非常有效。系统管理员应在每个网络的边界处配置过滤器，确保数据包满足以下至少一个条件：

* 内部源 IP 地址的数据包不应从网络外部进入。

* 外部源 IP 地址的数据包不应从网络内部退出。

* 私有 IP 地址的数据包在任何方向通过路由器都不应传递（除非作为内部网络配置的一部分明确允许）。

这三条简单的过滤规则可以消除大多数 IP 伪造攻击，并大幅增强网络安全。

#### 会话劫持

会话劫持攻击发生在恶意个人拦截授权用户与资源之间的通信部分，然后使用劫持技术接管会话并假冒授权用户。以下列表包含了一些常见的劫持技术：

* 捕获客户端与服务器之间的认证细节，并使用这些细节假冒客户端身份

* 骗取客户端，使其认为攻击者的系统是服务器，作为中间人，当客户端建立与服务器的合法连接时，然后断开客户端的连接

* 使用未正确关闭连接的用户的 Cookie 数据访问 Web 应用程序

这些技术对最终用户可能产生灾难性的后果，必须通过管理控制（例如反重放身份验证技术）和应用控制（例如在合理的时间内过期 Cookie）来应对。

## 摘要

应用程序开发人员必须担心很多事情！随着黑客在工具和技术方面变得更加高明，由于其复杂性和多个漏洞点，应用层正 increasingly 成为攻击的焦点。

包括病毒、蠕虫、特洛伊木马和逻辑炸弹在内的恶意代码，利用应用程序和操作系统中的漏洞，或通过社交工程感染系统并获取其资源和机密信息。

应用程序本身也可能包含多种漏洞。缓冲区溢出攻击利用缺乏适当输入验证的代码来影响系统内存的内容。后门为前开发人员和恶意代码作者提供了绕过正常安全机制的能力。Rootkits 为攻击者提供了轻松进行特权提升攻击的方式。

许多应用程序正在向 Web 迁移，这创造了新的暴露和漏洞水平。跨站脚本攻击允许黑客欺骗用户向不安全的站点提供敏感信息。SQL 注入攻击允许绕过应用控制，直接访问和操作底层数据库。

侦察工具为攻击者提供了自动化工具，用于识别可能在后续被攻击的弱点系统。IP 探测、端口扫描和漏洞扫描都是自动化检测组织安全控制弱点的方式。伪装攻击使用隐蔽技术，允许冒充用户和系统。

## 考试要点

**理解病毒使用的传播技术。** 病毒使用四种主要传播技术——文件感染、服务注入、引导扇区感染和宏感染——来渗透系统并传播其恶意负载。你需要了解这些技术，以便有效保护网络中的系统免受恶意代码的侵害。

**了解防病毒软件包如何检测已知病毒。** 大多数防病毒程序使用基于签名的检测算法，查找已知病毒的特征模式。因此，定期更新病毒定义文件以保持对新出现的病毒的保护至关重要。基于行为的检测也在日益普及，防病毒软件会监控目标系统的异常活动，即使软件不匹配已知恶意软件签名，也会阻止或标记该活动以供调查。

**解释攻击者用于破坏密码安全的技术。** 密码是当今最常用的访问控制机制，你需要了解如何防范试图 undermine 其安全的攻击者。了解密码破解工具、字典攻击以及钓鱼等社交工程攻击（如 phishing）如何被用来击败密码安全。

**了解攻击者用于利用 poorly written software 的各种应用程序攻击类型。** 应用程序攻击是现代计算的最大威胁之一。攻击者利用缓冲区溢出、后门、时间检查到时间使用漏洞以及 Rootkits 来获得非法访问系统。安全专业人员必须清楚了解每种攻击及其相应的防护措施。

**了解常见的 Web 应用程序漏洞及其防护措施。** 随着许多应用程序向 Web 迁移，开发人员和安全专业人员必须了解该环境中的新型攻击以及如何防范它们。最常见的两个例子是跨站脚本（XSS）和 SQL 注入攻击。

**了解攻击者在发起网络攻击前使用的侦察技术。** 在发动攻击之前，攻击者会使用 IP 扫描来搜寻网络中活动的主机。这些主机随后会受到端口扫描和其他漏洞探测的攻击，以尝试 compromising 网络。你需要了解这些攻击，以便帮助保护你的网络，限制攻击者可能获取的信息量。

## 实验室作业

1. 病毒和蠕虫的主要区别是什么？

2. 攻击者如何构建彩虹表（rainbow table）？

3. 当防病毒软件包发现受感染文件时，可能会采取哪些操作？

4. 像 Tripwire 这样的数据完整性保障工具如何提供二次病毒检测能力？

## 复习题

1. 防范病毒攻击最常用的技术是什么？

   1. 签名检测  

   2. 启发式检测  

   3. 数据完整性保障  

   4. 自动重构  

2. 作为电子商务公司的安全管理员，你正在将新的 Web 服务器放入生产环境。应该使用哪个网络区域？

   1. Internet  

   2. DMZ  

   3. Intranet  

   4. Sandbox  

3. 哪种攻击依赖于两个事件之间的时间差异？

   1. Smurf  

   2. TOCTOU  

   3. Land  

   4. Fraggle  

4. 哪种技术最接近 APT（高级持续性威胁）攻击？

   1. Zero-day exploit  

   2. Social engineering  

   3. Trojan horse  

   4. SQL injection  

5. 哪种高级病毒技术会在每个系统感染时修改病毒的恶意代码？

   1. Polymorphism  

   2. Stealth  

   3. Encryption  

   4. Multipartitism  

6. 哪个工具可以解决用户忘记复杂密码的问题？

   1. LastPass  

   2. Crack  

   3. Shadow password files  

   4. Tripwire  

7. 哪种应用程序漏洞最直接地允许攻击者修改系统内存的内容？

   1. Rootkit  

   2. Back door  

   3. TOC/TOU  

   4. Buffer overflow  

8. 哪个密码最可能在字典攻击中被破解？

   1. mike  

   2. elppa  

   3. dayorange  

   4. fsas3alG  

9. 哪种技术可以限制彩虹表攻击的效果？

   1. Hashing  

   2. Salting  

   3. Digital signatures  

   4. Transport encryption  

10. 在 Web 表单中，哪个字符在处理用户输入时应特别小心？

    1. !  

    2. &  

    3. *  

    4. '  

11. 如果在 Web 表单中实现某种数据库技术，可以限制 SQL 注入攻击的潜在风险？

    1. Triggers  

    2. Stored procedures  

    3. Column encryption  

    4. Concurrency control  

12. 哪种侦察攻击能为攻击者提供系统上运行的服务信息？

    1. Session hijacking  

    2. Port scan  

    3. Dumpster diving  

    4. IP sweep  

13. 要在 Web 页面上使用跨站脚本攻击，需要满足什么条件？

    1. Reflected input  

    2. Database-driven content  

    3. .NET technology  

    4. CGI scripts  

14. 哪种病毒使用了多种传播技术，以最大化渗透系统的数量？

    1. Stealth virus  

    2. Companion virus  

    3. Polymorphic virus  

    4. Multipartite virus  

15. 对跨站脚本攻击而言，最有效的防御措施是什么？

    1. `限制账户权限`

    2. `输入验证`

    3. `用户认证`

    4. `加密`

16. `什么蠕虫是第一个导致设施重大物理损坏的？`

    1. `Stuxnet`

    2. `Code Red`

    3. `Melissa`

    4. `RTM`

17. `本的系统被恶意代码感染，该代码修改操作系统以允许恶意代码作者访问他的文件。攻击者使用了什么类型的漏洞？`

    1. `特权提升`

    2. `后门`

    3. `根 kit`

    4. `缓冲区溢出`

18. `Java 语言使用什么技术来降低 applets 带来的威胁？`

    1. `保密性`

    2. `加密`

    3. `隐蔽性`

    4. `沙箱`

19. `在跨站脚本（XSS）攻击中，常用的 HTML 标签是什么？`

    1. `<H1>`

    2. `<HEAD>`

    3. `<XSS>`

    4. `<SCRIPT>`

20. `在设计防火墙规则以防止 IP 伪造时，应遵循以下哪项原则？`

    1. `内部源 IP 地址的数据包不应从外部进入网络。`

    2. `内部源 IP 地址的数据包不应从内部退出网络。`

    3. `公共 IP 地址的数据包不应在任何方向通过路由器。`

    4. `外部源 IP 地址的数据包不应从外部进入网络。`

## Appendix A  

Answers to Review Questions

## Chapter 1: Security Governance Through Principles and Policies

1. `B. 安全的主要目标和宗旨是保密性、完整性和可用性，通常称为 CIA 三元组。`

2. `A. 漏洞和风险是基于它们对一个或多个 CIA 三元组原则的威胁进行评估的。`

3. `B. 可用性意味着授权主体能够及时且 uninterrupted（不间断）地获取对象。`

4. `C. 硬件破坏违反了可用性，可能也违反完整性。保密性的侵犯包括捕获网络流量、窃取密码文件、社会工程、端口扫描、肩窥、窃听和嗅探等。`

5. `C. 保密性的侵犯不仅限于直接的故意攻击。许多未经授权的敏感或机密信息泄露是由于人为错误、疏忽或无能造成的。`

6. `D. 披露不是 STRIDE 的组成部分。STRIDE 的元素包括伪造、篡改、否认、信息披露、拒绝服务和特权提升。`
