
1. 保护系统和数据的保密性、完整性和可用性。

2. 确保只有合法的对象能够在系统上进行身份验证。

3. 防止对主体的未经授权访问。

4. 确保所有主体都经过身份验证。

6. 用户使用登录 ID 和密码进行登录。登录 ID 的作用是什么？

    1. 身份验证

    2. 授权

    3. 问责

    4. 标识

7. 账责（Accountability）要求以下所有项目中的一项除外。哪一项不是账责所必需的？

    1. 标识

    2. 身份验证

    3. 审计

    4. 授权

8. 你可以使用什么来防止用户在两个密码之间切换？

    1. 密码复杂性

    2. 密码历史记录

    3. 密码年龄

    4. 密码长度

9. 哪个选项最能体现口语短语（passphrase）的好处？

    1. 它很短。

    2. 它容易记住。

    3. 它包含一个字符集。

    4. 它很容易被破解。

10. 下列哪个是类型 2 身份验证因子的例子？

     1. 你拥有的东西

     2. 你是

     3. 你做的事

     4. 你知晓的事

11. 你的组织向员工发放设备。这些设备每 60 秒生成一次密码。组织内部的服务器在任何时刻都知道这个密码是什么。这个设备是什么类型？

     1. 同步令牌

     2. 异步令牌

     3. 智能卡

     4. 通用访问卡

12. 下列哪个选项提供基于主体的物理特征的身份验证？

     1. 账户 ID

     2. 生物特征

     3. 令牌

     4. PIN

13. 生物识别设备的 CER（等效误差率）指示什么？

     1. 它表明灵敏度过高。

     2. 它表明灵敏度过低。

     3. 它表明假拒率等于假接受率的点。

     4. 当足够高时，它表明生物识别设备高度准确。

14. 萝莉有用户账户，并以前使用生物识别系统登录。今天，生物识别系统未能识别她，导致她无法登录。这最好描述为什么？

     1. 假拒

     2. 假接受

     3. 跨错误

     4. 等误差

15. Kerberos 的主要目的是什么？

     1. 保密性

     2. 完整性

     3. 身份验证

     4. 问责

16. 哪个选项最适合支持联合身份管理（FIM）系统？

     1. Kerberos

     2. 超文本标记语言（HTML）

     3. 可扩展标记语言（XML）

     4. 安全断言标记语言（SAML）

17. 在 RADIUS 架构中，网络访问服务器（NAS）的功能是什么？

     1. 身份验证服务器

     2. 客户端

     3. AAA 服务器

     4. 防火墙

18. 哪个 AAA 协议基于 RADIUS 并支持移动 IP 和 VoIP？

     1. 分布式访问控制

     2. Diameter

     3. TACACS+

     4. TACACS

    *   请参考下面的情景回答问题 19 和 20。

    *   一名管理员在组织中工作了超过 10 年。他在这期间在不同的 IT 部门之间调动，并保留了他在每个职位任职期间获得的权限。最近，他的主管责备他对系统做出未经授权的更改。他再次做出未经授权的更改，导致出现意外故障。管理层决定终止他的雇佣合同。他第二天回到工作岗位清理办公桌和物品，在此期间他安装了一个恶意脚本，该脚本被设置为在下个月的第一天运行。该脚本会更改管理员密码、删除文件，并在数据中心的 100 多台服务器上关闭系统。

19. 在管理员任职期间，以下基本原则被违反了？

     1. 隐式拒绝

     2. 可用性丧失

     3. 防御特权

     4. 最小权限

20. 在任职期间，以下哪项可能发现了该用户账户的问题？

     1. 强身份验证的政策

     2. 多因素身份验证

     3. 日志记录

     4. 账户审查

Chapter 14  

Controlling and Monitoring Access

**THE CISSP EXAM TOPICS COVERED IN THIS CHAPTER INCLUDE:**

*   **![images](images/correction.png) Domain 5: Identity and Access Management ( IAM )** 

    *   5.4 Implement and manage authorization mechanisms 

        *   5.4.1 Role Based Access Control (RBAC)

        *   5.4.2 Rule-based access control

        *   5.4.3 Mandatory Access Control (MAC)

        *   5.4.4 Discretionary Access Control (DAC)

        *   5.4.5 Attribute Based Access Control (ABAC)

![images](images/clogo.jpg) Chapter 13, “Managing Identity and Authentication,” presented several important topics related to the Identity and Access Management (IAM) domain for the CISSP certification exam. This chapter builds on those topics and includes key information on some common access control models. It also includes information on how to prevent or mitigate access control attacks. Be sure to read and study the materials from each of these chapters to ensure complete coverage of the essential material for this domain.

## Comparing Access Control Models

Chapter 13 focused heavily on identification and authentication. After authenticating subjects, the next step is authorization. The method of authorizing subjects to access objects varies depending on the access control method used by the IT system.

### Comparing Permissions, Rights, and Privileges

When studying access control topics, you’ll often come across the terms *permissions*, *rights*, and *privileges*. Some people use these terms interchangeably, but they don’t always mean the same thing.

**Permissions** In general, permissions refer to the access granted for an object and determine what you can do with it. If you have read permission for a file, you’ll be able to open it and read it. You can grant user permissions to create, read, edit, or delete a file on a file server. Similarly, you can grant a user access rights to a file, so in this context, access rights and permissions are synonymous. For example, you may be granted read and execute permissions for an application file, which gives you the right to run the application. Additionally, you may be granted data rights within a database, allowing you to retrieve or update information in the database.

**Rights** A right primarily refers to the ability to take an action on an object. For example, a user might have the right to modify the system time on a computer or the right to restore backed-up data. This is a subtle distinction and not always stressed. However, you’ll rarely see the right to take action on a system referred to as a permission.

**Privileges** *Privileges* are the combination of rights and permissions. For example, an administrator for a computer will have full privileges, granting the administrator full rights and permissions on the computer. The administrator will be able to perform any actions and access any data on the computer.

### Understanding Authorization Mechanisms

Access control models use many different types of authorization mechanisms, or methods, to control who can access specific objects. Here’s a brief introduction to some common mechanisms and concepts.
