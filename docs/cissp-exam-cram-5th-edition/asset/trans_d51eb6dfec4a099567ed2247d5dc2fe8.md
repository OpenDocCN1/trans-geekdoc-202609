

-   C. XACML
-   D. OpenID

20. 下列哪个不是SAML的角色？

-   A. 身份提供者
-   B. 资源所有者
-   C. 服务提供者
-   D. 主体

## 考试准备题答案

1. D. MAC是正确的，因为它使用安全标签和许可级别。A不正确，因为DAC使用ACL；B不正确，因为LBAC是基于格的访问控制，使用上限和下限；C不正确，因为RBAC根据组织的安全策略使用组织中的角色或任务。

2. A. CER越低越好，因此虹膜扫描，CER 3（答案A）是正确的。指纹，CER 4（答案B），键盘动态，CER 5（答案C），和语音识别，CER 6（答案D）是不正确的，因为它们具有较高的CER。CER基于I型错误和II型错误确定。

3. B. DAC的两个主要组成部分是文件和数据所有权以及访问权限和权限。在文件和数据所有权方面，系统中的每个对象必须有一个所有者。没有所有者的对象将处于无保护状态。访问权限和权限控制个人的访问权限。虽存在差异，但基本访问控制列表检查读取、写入和执行权限。答案A、C和D不正确。

4. B. 身份和访问管理的四个关键领域是识别、身份验证、授权和问责。安全官员正在审查日志以确保准确性，这是一种问责形式。因此，答案A、C和D不正确。

5. A. 认知密码在注册过程中、个人呼叫帮助台时以及个人请求需要身份验证的其他服务时被广泛使用。所有其他答案都不正确：一次性密码（答案B）与令牌相关，虚拟密码（答案C）是一种通行短语形式，问题未描述复杂密码（答案D）。

6. D. 自由访问控制（DAC）方法之所以这样命名，是因为访问控制留给所有者自行决定。这可以被视为类似于点对点计算机网络。所有其他答案都不正确：MAC模型（答案B）是静态的，基于预定义的访问特权列表，TACACS+（答案A）和RADIUS（答案C）都用于远程访问，并未恰当回答问题。

7. C. TACACS+支持两因素身份验证。所有其他答案都不正确：TACACS+提供超过单因素身份验证（答案A）；它是集中式而非分布式的访问控制系统（答案B）；虽然它提供问责（答案D），但它也提供授权。

8. C. ACL包含一个隐式拒绝所有语句。例如，如果ACL只有一条语句“Deny ICMP any, any”，则ICMP将被拒绝；然而，隐式拒绝所有将阻止所有其他流量。答案A和D不正确，因为ACL从上到下处理。答案B不正确，因为基于规则的访问控制和基于角色的访问控制并非同一事物。

9. C. RADIUS提供三种服务：身份验证、授权和问责。RADIUS便于集中用户管理，并将所有用户配置文件保存在所有远程服务共享的一个位置。答案A、B和D不正确，因为它们未完全回答问题。

10. B. 联合是多个企业（例如Facebook和Yahoo）之间可以达成的一种安排，它允许一个服务的订阅者使用相同的识别/身份验证凭据来访问第二个组织的资源。它与单点登录（SSO）不同，SSO用于单个组织内部。SSO的示例包括Kerberos和SESAME。答案A和C不正确，因为可传递信任是在父域和子域之间自动创建的双向关系，而不可传递信任不会超出其创建所基于的域。这两个术语都直接与Microsoft操作系统相关联。

**11. B.** 字典攻击针对可发音密码。暴力攻击（答案A）、混合攻击（答案C）和彩虹表（答案D）都用于针对任何包含A–Z、a–z、0–9和特殊字符组合的密码。

**12. C.** 存储密码的最佳方法是通过一种称为哈希的单向过程，Microsoft Windows和Linux等操作系统使用该过程。纯文本文件（答案A）很容易泄露。对称加密（答案B）将允许任何持有密钥的人轻松反转该过程。异或过程（答案D）只会模糊密码，而不会提供任何真正的保护。

**13. D.** 基于格的访问控制模型（LBAC）使用连接和相遇。LBAC被认为是一种复杂的方法，用于管理主体和对象之间的交互。答案A、B和C不正确，因为这些方法不使用连接和相遇。

**14. A.** 基于规则的访问控制用于防火墙和路由器。RBAC基于特定规则集，类似于路由器ACL。MAC（答案B）使用标签，非常适合高安全性环境。DAC（答案C）描述了自由控制，LBAC（答案D）是一种使用上界和下界的复杂方法。

**15. D.** 基于角色的访问控制（RBAC）允许将特定人员分配到具有特定权限的特定角色。它允许将访问权分配给组，并且在人员流动率高的环境中效果良好。答案A、B和C不符合该描述。

**16. D.** 在ABAC中，访问资源的权限基于组合属性的策略。所有其他答案都不正确：受限制的用户界面（答案A）根据用户的权限限制用户可以看到或做什么。MAC（答案B）是静态的，基于预定义的访问权限列表。DAC（答案C）是一种分布式模型。

17. C. IAL 3提供面对面身份验证。所有其他答案都不正确，因为IAL 3不提供多因素身份验证（答案A）、远程身份验证（答案B）或身份即服务（答案D）。

18. C. 请求方不是OAuth角色。答案A、B和D不正确，因为资源所有者、资源服务器和身份验证服务器都是有效角色。

19. C. XACML主要是一种ABAC访问控制策略语言，其中与用户、操作或资源关联的属性（数据位）是决定特定用户是否可以以特定方式访问特定资源的输入。答案A、B和D不正确，因为它们未完全回答问题。

20. B. 资源所有者不是SAML的角色之一。SAML中的角色包括身份提供者（答案A）、服务提供者（答案C）和主体（答案D）。

## 建议阅读和资源

**Zephyr分析：** www.cse.unr.edu/~bebis/CS790Q/Lect/Chapter_8.ppt

**集成物理安全和逻辑安全：** www.cisco.com/c/dam/en_us/solutions/industries/docs/gov/pl-security.pdf

**了解访问控制：** www.owasp.org/index.php/Access_Control_Cheat_Sheet

**生物识别性能指标：** www.biometric-solutions.com/index.php?story=performance_biometrics

**了解会话管理：** www.hackingarticles.in/beginner-guide-understand-cookies-session-management/

**凭据管理系统：** https://www.csoonline.com/article/2120384/what-is-iam-identity-and-access-management-explained.html

**生物识别方法比较：** https://www.recogtech.com/en/knowledge-base/5-common-biometric-techniques-compared

**联合身份管理（SAML与OAuth）：** fedtechmagazine.com/article/2020/01/federated-identity-management-saml-vs-oauth-perfcon

**系统账户访问审查：** www.isaca.org/resources/isaca-journal/issues/2019/volume-4/effective-user-access-reviews

**配置和取消配置：** www.identitymanagementinstitute.org/6-best-practices-for-managing-the-identity-lifecycle/

**基于属性的访问控制：** https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.sp.800-162.pdf

**RADIUS最佳实践：** msdn.microsoft.com/en-us/library/bb742489.aspx

