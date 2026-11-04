

此外，Cortana 学习工具是安全且可扩展的。Cortana 无论数据的复杂性和大小如何，都能提供数据价值。最重要的是，Cortana 允许你与智能代理交互，从而以更自然、实用和有用的方式更接近你的消费者。Cortana Intelligence Suite 在多个领域都有帮助，包括制造业、金融服务、零售和医疗保健。

## Visualizing your data with Power BI

Power BI 由 Microsoft 提供，是一款基于云系统的强大服务。它涵盖了 Microsoft 的最新商业智能服务和工具。该服务帮助数据科学家从其组织的數據中构想和分享洞察。

Power BI 数据可视化课程由 edX 在线提供，是 Microsoft Professional Program Certificate in Data Science 的一部分。这项基于云的服务在数据科学专业人士中迅速流行。

Power BI 帮助你可视化和连接你的数据。在本课程中，学生学习如何连接、导入、转换和塑造数据以用于商业智能。此外，Power BI 课程还教你如何创建仪表板并在移动设备和网络上与业务用户共享。

## Managing your access on Azure’s Active Directory

Azure Active Directory (AD) 是一种广泛的访问和身份管理解决方案。它提供了一套广泛的设施，允许你监督对云和本地资源及应用程序的访问。这包括各种 Microsoft 在线服务，如 Office 365，以及众多非 Microsoft SaaS 应用程序。

Azure AD 的主要功能之一是你能够管理对其资源的访问。这些资源可以是目录外部的，如软件即服务（SaaS）应用程序、本地资源或 SharePoint 站点，以及 Azure 服务；也可以是目录内部的，如通过目录角色管理对象的权限。

# Chapter 11
## Getting Busy on IBM Bluemix

### IN THIS CHAPTER

![check](Image00001.jpg)**为人工智能区块链应用做准备**

![check](Image00001.jpg)**构建你的 IBM Fabric**

![check](Image00001.jpg)**创建智能合约**

![check](Image00001.jpg)**部署物联网解决方案**

在本章中，我向你介绍 IBM 的区块链计划，IBM 将其与其它的开创性技术合并，例如用于应用构建的完整平台即服务（PaaS）Bluemix，以及它的超级计算机 Watson。

区块链技术创造了近乎无摩擦的价值交换。人工智能加速了海量数据的分析。这两种能力的融合将是一场范式转变，影响我们做生意和保护我们连接的电子设备的方式。

如果你从事物联网（IoT）、医疗保健、仓储、运输或物流行业，你将从本章信息中受益。此外，如果你是企业家，想了解人工智能（AI）和区块链在可扩展应用平台上集成带来的新功能，本章适合你。

### Business Blockchain on Bluemix

IBM 现在提供与其实传统产品（如 IBM Bluemix）集成的区块链技术。Bluemix 是一种基于开放标准、云端的 PaaS，用于构建和管理应用程序。IBM 集成了来自 Hyperledger 的区块链堆栈，Hyperledger 是 Lynx 基金会的一部分，并正在建立区块链技术的最佳实践。

你需要为 IBM 区块链计划中的快速和根本性变化做好准备。该技术非常新颖，在 IBM 和 Hyperledger 内部仍处于孵化阶段。

Hyperledger 有多个不同的子项目正在开发中。截至本文撰写时，IBM 使用的是 Fabric，但它可能会将 Bluemix 开放给其他项目。Fabric 是开源的，并在 Hyperledger 内部积极开发中。它尚未完全准备好用于商业用途——截至本文撰写时，它仍处于孵化状态。

你可以通过使用 Hyperledger Fabric v0.6 在 Bluemix 上开始测试 Fabric。然而，IBM 警告不要直接在 Fabric v0.6 或任何更早版本上运行任何有价值的交易。

#### Your isolated environment

Bluemix 是 IBM 最新推出的云服务。它是基于 Cloud Foundry 的 IBM 开放云架构的实现，Cloud Foundry 是一个开源 PaaS。

Bluemix 使你能够快速轻松地构思应用程序、部署它们并管理它们。Bluemix 提供企业级服务，可以与应用程序集成，而无需知道如何安装或配置它们。

[图 11-1](#text00016.html#c11-fig-0001) 显示了 IBM 如何将区块链的不同方面与 IBM 系统关联。你可以在 [ `https://goo.gl/12Q6no` ](https://goo.gl/12Q6no) 了解更多信息。

![图 11-1：IBM Bluemix 和物联网如何与 IBM Watson 合并。](Image00027.jpg)

 [图 11-1：](#text00016.html#rc11-fig-0001)  IBM Bluemix 和物联网如何与 IBM Watson 合并。

IBM Bluemix 提供四项核心功能：

*   基于你的应用架构需求的计算基础设施
*   将应用部署到 Bluemix 公有云或专用云的能力
*   开发工具，如代码编辑器和管理器
*   在其服务部分访问第三方开源工具

Bluemix 为你构建应用提供了所需的一切。它现在也提供区块链基础设施用于测试。

他们提供了一项服务，用于将你的应用程序与 Bluemix 区块链集成。截至本文撰写时，有两种定价模式。免费账户为你测试想法提供了所需的一切。你获得四个节点和一个用于签署交易的证书颁发机构，以及一个带有日志、控制和 API 的仪表板。你还获得几个带有源代码的示例应用以供实验。

企业计划的价格为每月 $10,000，并提供比免费模式更高的安全性和速度。

#### Bluemix use cases

两个杰出的创业先驱正在使用 Bluemix 和 Hyperledger Fabric 集成：

*   **Wanxiang:** 中国最大的汽车零部件公司万向正在与 IBM 合作部署私有区块链。他们将产权嵌入到电动汽车等事物中。目标是降低消费者租赁设备的成本。万向将使用其区块链技术跟踪组件的使用寿命并翻新使用过的电池。Bluemix 将处理其他一切。
*   **KYCK!:** 金融科技（fintech）初创公司 KYCK! 正在利用 IBM 的区块链集成，以一种新颖的方式解决经纪商的“了解你的客户”（KYC）需求。这项费用对银行和其他金融服务来说是限制性和昂贵的。KYC 用于防止洗钱和非法贸易，并打击恐怖主义。KYCK! 正在构建视频会议和加密文档提交平台。它将允许经纪人与公司未曾亲自会面的客户合作并进行身份验证。

IBM 还构建了三个简单的 Chaincode 应用程序，让你可以在 IBM Blockchain 网络上进行操作：

*   **Marbles:** Marbles 是一个演示在两个用户之间转移弹珠的应用。它让你看到如何在区块链上移动资产。
*   **Commercial Paper:** Commercial Paper 是在 IBM Blockchain 上实现的区块链交易网络。你可以创建新的商业票据进行交易，买卖现有交易，并审计网络。
*   **Car Lease:** Car Lease 与 Marbles 演示非常相似。它旨在让你与资产进行交互。你可以创建、更新和转移。它还允许第三方查看历史记录。

### Watson’s Smart Blockchain
