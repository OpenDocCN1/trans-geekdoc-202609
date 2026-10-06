

# 图 7.72

Windows Azure Directory 单点登录

Windows Azure Active Directory

![](img/41a83208e6906a3732620203b836cea7_408_0.png)

为了让你更全面地了解在每个部署级别所面临的优点 (+) 和缺点 (-)，我们在表 7.4 中提供了一个总结。

# 表 7.4：Windows Azure Active Directory 集成

| WINDOWS AZURE DIRECTORY 账户 | WINDOWS AZURE DIRECTORY 账户 + DiRSync | WINDOWS AZURE DIRECTORY 账户 + DiRSync |
|---|---|---|
| + 无需额外配置。 | + 本地 Active Directory 是主源。 | + 本地 Active Directory 是主源。 |
| | + 用户拥有一对凭据。 | + 单点登录体验。 |
| | | + 双重身份（身份验证）。 |
| - 用户有两对凭据。 | - 无法登录云应用程序。 | - 必须在专用本地服务器上安装 DiRSync 工具。 |
| - 无法登录云应用程序。 | - 无法实现双重身份。 | - 必须在本地部署 AD FS 农场。 |
| - 无法实现双重身份。 | - 必须在专用本地服务器上安装 DiRSync 工具。 |

在本节中，我们向你介绍了 Windows Azure Directory，并展示了如何管理并将其集成到你的环境中。现在你应该对开始使用 WAAD 所需的重要术语和技术有了基本的了解。

# Workplace Join (工作场所加入) 概述

今天的公司面临着网络中各种设备带来的巨大问题。想象一下，一位顾问需要为一个 IT 项目工作。该公司的首席执行官使用 iPad 进行工作。营销人员需要在不同的设备（如平板电脑）上展示他们的产品。所有人在家里和办公室都使用自己的设备，而且没有为所有人提供一种标准设备。他们唯一的共同点是需要访问网络上的资源。

由于所有这些设备都需要访问公司网络和应用程序，因此提供一种安全且合规的方式来访问这些资源并管理设备和数据一直是一项挑战。到目前为止，你有两个选择：要么将设备加入 Active Directory（如果可能），要么不加入。对于访问数据和应用程序的用户以及管理设备的业务来说，这两种都有优缺点。Workplace Join 的诞生源于自带设备 (BYOD) 策略，该策略允许员工将个人设备带入工作场所使用。

# 什么是 Workplace Join？

Workplace Join 随 Windows Server 2012 R2 一起并集成到 Windows 8.1 中；它允许你的用户从任何地方访问应用程序和数据，而无需将任何设备加入域。此外，Workplace Join 为用户提供了所有公司资源的单点登录，而公司的管理员仍然可以控制他们如何访问这些资源。这种设备更紧密的集成也带来了一些风险，因此，微软使用了多因素身份验证，并在 Windows Server R2 的 Active Directory 联合身份验证服务 (AD FS) 中添加了一些功能来管理这些风险。

注册非常简单。根据你的设备，你可以可以通过 URL 注册，也可以配置计算机设置。在两种情况下，为了注册设备，你都必须提供用户主体名称 (UPN)，在许多公司中，它连接到用户的电子邮件地址。客户端设备然后从公司网络内部或外部（通过互联网）连接到公司的 Web 应用程序代理 (Web Application Proxy) 并验证用户。Web 应用程序代理是 Windows Server 2012 中的新功能，是远程访问服务的一部分，允许你为用户提供访问组织内部服务器上运行的应用程序。Web 应用程序代理的优势在于发布应用程序，并且此发布的源可以在任何设备上访问。如果凭据匹配，Windows Server 2012 R2 AD FS 中的一个新服务——设备注册服务 (DRS) 将在 Active Directory 中注册用户的设备。为了实现这一目的，Active Directory 中创建了一个新的对象类。这个新设备对象可以用于对你公司环境中的数据和资源提供条件条件和细粒度的访问。你可以将 Workplace Join 理解为“轻量版域加入”（见图 7.73）。

# 图 7-73 Workplace Join

# Windows Azure Active 身份验证

![](img/41a83208e6906a3732620203b836cea7_410_0.png)

订阅此新功能的用户不会将设备的完全控制交给管理员，但 Windows Server 2012 R2 域控制器管理员可以应用一组安全策略，并对机密数据进行有限擦除。这让管理员对公司数据的发生情况以及如何访问数据有着良好的控制。另一方面，用户仍然可以按照他们想要的方式使用设备，并轻松舒适地访问网络资源。

# 开始使用 Workplace Join

Workplace Join 是 Windows Server 2012 R2 和 Windows 8.1 的一部分，正因如此，我们想给你一个简短的介绍，让你了解 Workplace Join 是什么。关于这项新技术我们有很多可以聊的内容，但将超出本书的范围。

如果你想在实验室中玩玩 Workplace Join，TechNet 上有一份很好的分步指南，介绍了如何使用 Workplace Join 加入 iOS 设备和 Windows 设备。更多信息请参阅以下链接：http://technet.microsoft.com/en-us/Library/dn45241.aspx。

# 总结

