

28. 客户需要实现符合 PCI 和 HIPAA 监管的工作负载。在 Google Cloud 中实现此类控制的最佳方法是什么，对数据隔离提供严格要求，并在多个团队之间实现访问控制，同时减少管理成本？

-   A. 实施组织策略并使用集中式 SSO 为团队提供访问权限，创建文件夹并在其下方配置项目以隔离数据、测试（QA）和生产环境，并授予开发团队对这些项目的访问权限。

-   B. 在 Cloud Identity 中创建两个组织单元 (OUs)，根据需求向这些 OUs 分配用户，并创建多个 SAML 配置文件。

-   C. 创建三个 Google Cloud 组织。一个组织将托管 HIPAA 的项目，第二个组织托管 PCI 的项目，第三个组织托管其他项目。为每个组织配置用户和组，并为这三个组织设置 SSO。

-   D. 创建两个 Google Cloud 组织。一个组织将托管不需要严格数据和访问隔离的项目。从相同源向两个组织配置用户并使用 SSO。

29. 你正在实施 Google Cloud。你的身份信息从本地 Active Directory 同步到 Azure Active Directory。你的业务规则设置在 Azure 中。提供 Google Cloud 访问的最佳方法是什么？

-   A. 使用 Google Cloud Identity Sync 从本地 Active Directory 同步用户和组，并使用 Azure 创建 SSO。

-   B. 使用 Azure 将用户和组同步到 Cloud Identity。在 Azure 中创建另一个应用程序以为 Google Cloud 提供联合身份访问。

-   C. 使用 Google Cloud Identity Sync 从本地 Active Directory 同步用户和组，并使用 Active Directory 联邦服务 (ADFS) 提供 SSO。

-   D. 使用 Google Cloud Identity Sync 从本地 Active Directory 同步用户和组，使用 Azure 为 Cloud Identity 提供合作伙伴，并使用 Azure 提供 SSO。

30. 客户需要依赖其现有的用户目录，并在 Google Cloud 中开发解决方案时使用原生身份验证。他们希望利用现有的工具和功能，通过熟悉的界面获取有关用户活动的洞察。你应该采取什么行动来满足客户的需求？

-   A. 以客户目录为源，通过即时配置（Just-in-Time provisioning）将用户同步到 Cloud Identity。

-   B. 使用客户的用户目录将 Cloud Identity 配置为 SAML 2.0 服务提供程序。

-   C. 在 Cloud Identity 中为所有用户配置并强制执行两步验证 (2SV)。

-   D. 配置第三方身份提供程序（Okta 或 PingFederate）来管理身份验证。

31. 客户想将 Cloud Identity 作为其主要身份提供者。客户想使用其他 Cloud SaaS 产品进行 CRM、消息和工单管理。客户还希望通过单点登录 (SSO) 功能访问 Google Cloud 和非 Google 应用程序来提高员工体验。只有经过授权的人员才能访问这些应用程序。客户应该采取什么行动？

-   A. 从 Cloud Identity 中移除客户，为个人选择正确的许可证，并重新同步到 Google Cloud。

-   B. 配置第三方应用程序将身份验证和授权联合到 Google Cloud Identity 身份提供者。

-   C. 从第三方应用程序中移除个人，向 Cloud Identity 添加许可证并重新同步。

-   D. 将人物画像（personas）从 Cloud Identity 复制到域名。

32. 以下所有内容都是超级管理员账户的最佳实践，例外：

-   A. 创建一个专用的超级管理员账户并存储在保险箱中。仅在需要断急访问（break-glass access）时才使用此账户。

-   B. 将管理 Google Cloud 资源的权限委托给组织中的其他用户，以确保职责分工。

-   C. 确保超级管理员使用 SSO，以便其活动可以被监控。

-   D. 确保你有多个超级管理员。

33. 以下所有内容都是在 Google Cloud 组织中设置多因素身份验证 (MFA) 时的最佳实践，例外：

-   A. 所有用户都开启两步验证 (2SV)。

-   B. 不要开启 2SV，因为用户可能会被锁定。

-   C. 为用户留足够的时间进行注册。

-   D. 允许用户信任设备。

-   E. 允许通过远程访问进行安全。

34. 数据团队需要使用服务账户与 BigQuery 交互。他们的项目需要一个存储 BigQuery 数据的 Cloud Storage 存储桶。数据团队实现此点的正确方法是什么？

-   A. 授予数据团队每个成员对 Cloud Storage 存储桶和 BigQuery 数据集的访问权限。

-   B. 创建一个包含所有数据团队开发者的 Google 组，并授予该组 Cloud Storage 存储桶和 BigQuery 权限。

-   C. 创建一个包含所有数据开发人员的 Google 组，并分配服务账户用户（Service Account User）IAM 角色。

-   D. 创建一个包含所有开发者的 Google 组，分配服务账户管理员（Service Account Admin）IAM 角色并让开发者生成密钥。

35. 一个三层应用程序运行在 Google Cloud 上。应用程序的中间层运行在 Compute Engine 上，并访问 BigQuery 中的数据集。你应该如何授予访问权限？

-   A. 为应用程序创建一个服务账户，并在项目级别授予 BigQuery User 角色。

-   B. 为应用程序创建一个服务账户，并在数据集级别授予 BigQuery User 角色。

-   C. 为应用程序创建一个服务账户，并在数据集级别授予 BigQuery Admin 角色。

36. 一个云开发团队需要在本地开发中使用服务账户。你需要为团队提供这些服务账户的密钥。你希望遵循 Google 推荐的实践。你应该做什么？

-   A. 实施每日密钥轮换，每天生成新密钥并将其提交到源代码仓库。

-   B. 实施每日密钥轮换，并为开发者提供一个 Cloud Storage 存储桶，他们每天可以从那里下载新密钥。

-   C. 创建一个包含所有开发者的 Google 组，分配服务账户用户 IAM 角色，并让开发者生成自己的密钥。

-   D. 创建一个包含所有开发者的 Google 组，分配服务账户管理员 IAM 角色并让开发者生成自己的密钥。

37. 一个混合应用程序运行在 AWS 和 Google Cloud 上。AWS 上的应用程序需要查询 BigQuery。你如何安全地实现这种方法？

-   A. 为应用程序创建一个服务账户，并在数据集级别授予 BigQuery User 角色。管理 AWS 端的团队将拥有为应用程序配置的密钥的所有权。

-   B. 创建工作负载池（workload pool）和一个 AWS 身份提供者，并授予 AWS 账户对项目级别服务账户的身份充访问（impersonation access）。

-   C. 创建工作负载池和一个 AWS 身份提供者，并授予 AWS 账户对 BigQuery 数据集服务账户的身份充访问。

-   D. 创建工作负载池和一个 AWS 身份提供者，并授予 AWS 角色对 BigQuery 数据集的身份充访问。

38. 你可以实施一种控制，即 SRE 团队仅在情况出现时才访问 Google Cloud。你如何以最小权限原则实现这种方法？

-   A. 创建一个 SRE 组并在组织级别授予 SRE 组访问权限，条件为仅在上午 8:00 到下午 5:00 之间且来自本地 IP 范围。

-   B. 创建一个 SRE 组并在项目级别授予 SRE 组访问权限，条件为仅在上午 8:00 到下午 5:00 之间。

-   C. 创建一个 SRE 组；预先批准他们访问该组。让他们请求访问该组，说明访问 Google Cloud 项目所需的分钟数。

-   D. 创建一个 SRE 组并将用户加入该组。让他们请求访问 Google Cloud 项目所需的分钟数。

39. 一个 Google Cloud 客户想要实现职责分工。SRE 团队应该具有生成密钥的能力，但不应具有使用密钥对数据进行加密或解密的能力。实现此点的正确方法是什么？

-   A. 为 SRE 团队和应用程序的服务账户在生成的密钥授予 KMS Admin 角色。

-   B. 为 SRE 团队和应用程序的服务账户在使用的密钥上授予 KMS Admin 角色。

-   C. 为 SRE 团队授予项目级的 KMS Admin 角色，并为服务账户在生成的密钥授予 Cloud KMS 密钥加密解密者（Encrypter/Decrypter）角色。

