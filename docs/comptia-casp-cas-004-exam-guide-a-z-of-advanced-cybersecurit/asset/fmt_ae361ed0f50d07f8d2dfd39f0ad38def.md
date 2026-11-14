
## 核心概念定义

### XACML
`XACML` 代表 `extensible Access Control Markup Language`。它是一种用 `XML` 实现的声明式访问控制策略语言及处理模型，描述了如何解释策略。最新版本 2.0 于 2005 年 2 月 1 日由 `OASIS` 标准组织批准。计划中的版本 3.0 将为评估上下文和策略委托配置文件（管理策略配置文件）增加通用属性类别。

### SOAP
`SOAP` 即 `Simple Object Access Protocol`，是一种在计算机网络中实现 `Web Services` 交换结构化信息的协议规范；它依赖 `extensible Markup Language` 作为其消息格式，通常依赖其他 `Applications Layer` 协议进行消息协商和传输。`SOAP` 可以构成 `Web Services` 协议栈的基础层，提供一个基本的消息传递框架，在此基础上可以构建 `Web Services`。

### SPML
`SPML` 是由 `Organization for the Advancement of Structured Information Standards (OASIS)` 开发的基于 `XML` 的框架。它用于在合作组织之间交换用户、资源和服务配置信息。`SPML` 是服务配置请求集成和互操作的开放标准。其目标是允许组织安全、快速地为 `Web` 应用程序和服务建立用户界面，方法是让企业平台（如 `Web portals`、`application servers` 和 `service centers`）在组织内部和跨组织产生配置请求。

### SAML
`SAML` 是一种基于 `XML` 的标准，用于在安全域之间交换身份验证和授权数据，即在 `identity provider` 和 `service provider` 之间交换。`SAML` 是 `OASIS Security Services Technical Committee` 的成果。

---

## QUESTION 38
**Which of the following is the capability to correct flows in the existing functionality without affecting other components of the system?**

1.  `Manageability`
2.  `Reliability`
3.  `Maintainability`
4.  `Availability`

**Answer: C**

### Explanation
*   **Availability**：用于确保服务/资源始终可访问。
*   **Manageability**：是指管理系统的能力，以确保系统在可扩展性、可靠性、可用性、性能和安全性方面的持续健康。
*   **Maintainability**：是指在不影响系统其他组件的情况下，纠正现有功能中流程的能力。

选项 B 不正确。它不是一个有效选项。

---

## QUESTION 39
**Fill in the blank with the appropriate word. \_\_\_\_\_\_\_ encryption protects a file as it travels over protocols, such as `FTPS (SSL)`, `SFTP (SSH)`, and `HTTPS`.**

**Answer: Transport**

---

## QUESTION 40
**Interceptor is a pseudo proxy server that performs HTTP diagnostics; which of the following features are provided by HTTP Interceptor? (Each correct answer represents a complete solution. Choose all that apply.)**

1.  It controls cookies being sent and received.
2.  It allows to browse anonymously by withholding the `Referrer tag`, and `user agent`.
3.  It can view each entire `HTTP header`.
4.  It debugs `DOC`, `DOCX`, and `JPG` files.

**Answer: A, B, and C**

### Explanation
`HTTP diagnostics` 由 `HTTP Interceptor` 执行，它是一个伪代理服务器，还便于查看浏览器和互联网之间的双向通信。`HTTP Interceptor` 的各种功能如下：

*   查看每个完整的 `HTTP header`。
*   调试 `PHP`、`ASP`、`CGI`、`JavaScript` 和 `htaccess` 文件。
*   控制发送和接收的 `Cookies`。
*   找出站点可能使用的 `URL redirection` 类型。
*   通过隐藏 `Referrer tag` 和 `user agent` 实现匿名浏览。

---

## QUESTION 41
**Karan is concerned about internal security threats on the network he administers. He believes that he has taken every reasonable precaution against external threats, but is concerned that he may have gaps in his internal security. Which of the following is the most likely internal threat?**

1.  Employees not following security policy
2.  `Privilege Escalation`
3.  `SQL Injection`
4.  Employees selling sensitive data

**Answer: A**

### Explanation
员工可能无视策略，例如限制使用 `USB` 设备或从互联网下载程序的策略。这是最普遍的内部安全威胁。

---

## QUESTION 42
**Resource exhaustion includes all of the following except ….**

1.  Opening too many connections
2.  Allocating all system memory to a single application
3.  Overflowing a buffer with too much data
4.  Flooding a network with excessive packets

**Answer: C**

### Explanation
`Buffer overflow` 攻击与资源耗尽有关，但不是同一回事。原因是 `Buffer overflow` 基于程序员未检查数组边界，而不是耗尽资源。选项 A、B 和 D 不正确。这些都是资源耗尽的示例。

---

## QUESTION 43
**Which of the following security practices are included in the implementation phase of the Security Development Lifecycle (SDL)? (Select any two)**

1.  Establish design requirements
2.  Perform `static analysis`
3.  Use `approved tools`
4.  Execute incident response plan

**Answer: B and C**

### Explanation
在 `Security Development Lifecycle (SDL)` 过程的每个阶段都会执行安全实践。

---

## QUESTION 44
**How many levels of threats are faced by the SAN?**

1.  3
2.  7
3.  2
4.  5

**Answer: A**

### Explanation
存储区域网络传输和存储关键数据；通常这使得存储区域网络面临风险。`SAN` 面临三个不同级别的威胁，如下所示：

#### Level one
这些类型的威胁是无意的，可能导致停机和收入损失。但是，管理员可以防止这些威胁。

#### Level two
这些类型的威胁是使用现有设备的简单恶意攻击。

#### Level three
这些类型的威胁是大规模攻击，难以防范。这些威胁来自使用非常见设备的熟练攻击者。

---

## QUESTION 45
**Which of the following is a written document and is used in those cases where parties do not imply a legal commitment or in those situations where the parties are unable to create a legally enforceable agreement?**

1.  `Patent law`
2.  `Memorandum of understanding (MOU)`
3.  `Memorandum of agreement (MOA)`
4.  `Certification and Accreditation (COA or CnA)`

**Answer: B**

### Explanation
`Memorandum of understanding (MOU)` 是一份定义双边或多边协议的文档。该文档规定了当事方之间的意向一致性，代表了拟议的共同行动路线。`MOU` 通常用于当事方不承担法律承诺的情况，或当事方无法创建具有法律约束力的协议的情况。它是君子协定的适当替代品。

---

## QUESTION 47
**Which of the following statements are true about capability-based security?**

1.  It is a concept in the design of secure computing systems, which is one of the existing security models.
2.  It is a computer security model based on the `Actor model` of computation.
3.  It is a scheme used by some computers to control memory access.
4.  It is a concept in the design of secure computing systems.

**Answer: D**
