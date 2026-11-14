

## 核心概念定义

### XACML
`XACML` 代表 `extensible Access Control Markup Language`（可扩展访问控制标记语言）。它是一种用 `XML` 实现的声明式访问控制策略语言及处理模型，描述了如何解释策略。最新版本 2.0 于 2005 年 2 月 1 日由 `OASIS` 标准组织批准。计划中的版本 3.0 将为评估上下文和策略委托配置文件（管理策略配置文件）增加通用属性类别。

### SOAP
`SOAP` 即 `Simple Object Access Protocol`（简单对象访问协议），是一种在计算机网络中实现 `Web Services`（Web 服务）交换结构化信息的协议规范；它依赖 `extensible Markup Language`（可扩展标记语言）作为其消息格式，通常依赖其他 `Applications Layer`（应用层）协议进行消息协商和传输。`SOAP` 可以构成 `Web Services` 协议栈的基础层，提供一个基本的消息传递框架，在此基础上可以构建 `Web Services`。

### SPML
`SPML` 是由 `Organization for the Advancement of Structured Information Standards (OASIS)`（结构化信息标准促进组织）开发的基于 `XML` 的框架。它用于在合作组织之间交换用户、资源和服务配置信息。`SPML` 是服务配置请求集成和互操作的开放标准。其目标是允许组织安全、快速地为 `Web` 应用程序和服务建立用户界面，方法是让企业平台（如 `Web portals`（Web 门户）、`application servers`（应用服务器）和 `service centers`（服务中心））在组织内部和跨组织产生配置请求。

### SAML
`SAML` 是一种基于 `XML` 的标准，用于在安全域之间交换身份验证和授权数据，即在 `identity provider`（身份提供者）和 `service provider`（服务提供者）之间交换。`SAML` 是 `OASIS Security Services Technical Committee`（OASIS 安全服务技术委员会）的成果。

---

## QUESTION 38
**以下哪项是指在不影响系统其他组件的情况下，纠正现有功能中流程的能力？**

1.  `Manageability`（可管理性）
2.  `Reliability`（可靠性）
3.  `Maintainability`（可维护性）
4.  `Availability`（可用性）

**答案：C**

### 解释
*   **Availability**（可用性）：用于确保服务/资源始终可访问。
*   **Manageability**（可管理性）：是指管理系统的能力，以确保系统在可扩展性、可靠性、可用性、性能和安全性方面的持续健康。
*   **Maintainability**（可维护性）：是指在不影响系统其他组件的情况下，纠正现有功能中流程的能力。

选项 B 不正确。它不是一个有效选项。

---

## QUESTION 39
**用适当的单词填空。\_\_\_\_\_\_\_ 加密可保护文件在通过 `FTPS (SSL)`、`SFTP (SSH)` 和 `HTTPS` 等协议传输时的安全。**

**答案：Transport（传输层）**

---

## QUESTION 40
**Interceptor 是一种执行 HTTP 诊断的伪代理服务器；以下哪些功能由 HTTP Interceptor 提供？（每个正确答案代表一个完整的解决方案。选择所有适用项。）**

1.  它控制发送和接收的 Cookie。
2.  它通过隐藏 `Referrer tag`（引用标签）和 `user agent`（用户代理）允许匿名浏览。
3.  它可以查看每个完整的 `HTTP header`（HTTP 头）。
4.  它调试 `DOC`、`DOCX` 和 `JPG` 文件。

**答案：A、B 和 C**

### 解释
`HTTP diagnostics`（HTTP 诊断）由 `HTTP Interceptor` 执行，它是一个伪代理服务器，还便于查看浏览器和互联网之间的双向通信。`HTTP Interceptor` 的各种功能如下：

*   查看每个完整的 `HTTP header`。
*   调试 `PHP`、`ASP`、`CGI`、`JavaScript` 和 `htaccess` 文件。
*   控制发送和接收的 `Cookies`。
*   找出站点可能使用的 `URL redirection`（URL 重定向）类型。
*   通过隐藏 `Referrer tag` 和 `user agent` 实现匿名浏览。

---

## QUESTION 41
**Karan 担心他管理的网络面临内部安全威胁。他认为他已采取一切合理预防措施抵御外部威胁，但担心内部安全可能存在漏洞。以下哪项是最可能的内部威胁？**

1.  员工不遵守安全策略
2.  `Privilege Escalation`（权限提升）
3.  `SQL Injection`（SQL 注入）
4.  员工出售敏感数据

**答案：A**

### 解释
员工可能无视策略，例如限制使用 `USB` 设备或从互联网下载程序的策略。这是最普遍的内部安全威胁。

---

## QUESTION 42
**资源耗尽包括以下所有情况，除了 …… 。**

1.  打开过多连接
2.  将所有系统内存分配给单个应用程序
3.  用过多数据溢出缓冲区
4.  用过量数据包淹没网络

**答案：C**

### 解释
`Buffer overflow`（缓冲区溢出）攻击与资源耗尽有关，但不是同一回事。原因是 `Buffer overflow` 基于程序员未检查数组边界，而不是耗尽资源。选项 A、B 和 D 不正确。这些都是资源耗尽的示例。

---

## QUESTION 43
**以下哪些安全实践包含在安全开发生命周期 (SDL) 的实施阶段？（选择任意两项）**

1.  建立设计要求
2.  执行 `static analysis`（静态分析）
3.  使用 `approved tools`（批准的工具）
4.  执行事件响应计划

**答案：B 和 C**

### 解释
在 `Security Development Lifecycle (SDL)`（安全开发生命周期）过程的每个阶段都会执行安全实践。

---

## QUESTION 44
**SAN 面临多少级别的威胁？**

1.  3
2.  7
3.  2
4.  5

**答案：A**

### 解释
存储区域网络传输和存储关键数据；通常这使得存储区域网络面临风险。`SAN` 面临三个不同级别的威胁，如下所示：

#### Level one（一级）
这些类型的威胁是无意的，可能导致停机和收入损失。但是，管理员可以防止这些威胁。

#### Level two（二级）
这些类型的威胁是使用现有设备的简单恶意攻击。

#### Level three（三级）
这些类型的威胁是大规模攻击，难以防范。这些威胁来自使用非常见设备的熟练攻击者。

---

## QUESTION 45
**以下哪项是书面文件，用于当事方不承担法律承诺的情况，或当事方无法创建具有法律约束力协议的情况？**

1.  `Patent law`（专利法）
2.  `Memorandum of understanding (MOU)`（谅解备忘录）
3.  `Memorandum of agreement (MOA)`（协议备忘录）
4.  `Certification and Accreditation (COA or CnA)`（认证和授权）

**答案：B**

### 解释
`Memorandum of understanding (MOU)`（谅解备忘录）是一份定义双边或多边协议的文档。该文档规定了当事方之间的意向一致性，代表了拟议的共同行动路线。`MOU` 通常用于当事方不承担法律承诺的情况，或当事方无法创建具有法律约束力的协议的情况。它是君子协定的适当替代品。

---

## QUESTION 47
**以下关于基于能力的安全性的陈述哪些是正确的？**

1.  它是安全计算系统设计中的一个概念，是现有安全模型之一。
2.  它是一种基于计算 `Actor model`（Actor 模型）的计算机安全模型。
3.  它是某些计算机用来控制内存访问的方案。
4.  它是安全计算系统设计中的一个概念。

**答案：D**

