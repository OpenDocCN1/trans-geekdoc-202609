
如果你是第一次拿起这本书，我假设你正在开始在 Azure 上成为数据从业者的旅程。本书内容不仅能帮助你准备 DP-900 Microsoft Certified Azure Data Fundamentals 认证考试，还能让你广泛了解 Azure 中的数据解决方案。本书旨在帮助你了解在 Azure 中存储数据的不同方法，以及如何将原始数据转化为用于做出有价值商业决策的信息。虽然本次考试不会深入探讨本书中列出的产品的具体技术特性，但你需要对这些技术有广泛的了解，这将成为你如果选择深入学习每种技术的起点。

## Who Should Read This Book?

本书适合任何希望广泛了解 Azure 数据基础知识并准备 DP-900 考试的人。数据工程师、数据科学家和 DBA 等技术人员，如果在处理数据方面工作，将从 Azure 数据基础知识培训中获益匪浅。这将帮助他们将现有技能（无论是在本地数据解决方案还是其他云平台上的解决方案）转移到 Azure 职业生涯中。除了了解高度技术性的角色外，本书还可以帮助分析师和项目经理了解如何使用 Power BI 和其他 Azure 数据服务等技术来帮助他们完成工作。技术销售人员也会发现本书很有价值，因为他们将获得在销售讨论中所需的知识，而 Azure 数据服务对于赢得潜在客户的业务至关重要。

### What's Included in the Book?

本书包含六章以及补充信息：术语表、本简介、闪存卡以及简介之后的评估测试。章节组织如下：

*   [Chapter 1](#c01.xhtml)，“Core Data Concepts”，涵盖数据存储和分析技术的基础知识。它定义了不同类型的数据、数据处理模式和数据分析类别。

*   [Chapter 2](#c02.xhtml)，“Relational Databases in Azure”，涵盖 Azure 中的不同关系型数据库选项以及何时使用哪一个。这包括 SQL Server in a VM、Azure SQL Database 和 Azure SQL Managed Instance 等 IaaS 和 PaaS 产品。[Chapter 2](#c02.xhtml) 定义了在 Azure 中部署、迁移、保护、管理和查询关系型数据库的最佳实践。本章还包括 Azure 中可用的开源关系型数据库 PaaS 选项。

*   [Chapter 3](#c03.xhtml)，“Nonrelational Databases in Azure”，涵盖不同类型的 NoSQL 数据库以及如何使用 Azure Cosmos DB 实现它们。本章定义了不同的 Azure Cosmos DB API，并探讨了 Azure Cosmos DB 如何为 NoSQL 数据提供安全性、高可用性和一致性。

*   [Chapter 4](#c04.xhtml)，“File, Object, and Data Lake Storage”，探讨 Azure 存储中的文件和对象存储选项，包括 Azure Files、Azure Blob 存储和 Azure Data Lake Storage Gen2 (ADLS)。本章涵盖 Azure 存储服务的部署、安全性和管理选项。

*   [Chapter 5](#c05.xhtml)，“Modern Data Warehouses in Azure”，探讨分析工作负载使用的常见数据处理模式和功能。本章涵盖用于构建现代数据仓库的几个常见 Azure 服务，例如 Azure HDInsight、Azure Databricks、Azure Data Factory 和 Azure Synapse Analytics。

*   [Chapter 6](#c06.xhtml)，“Reporting with Power BI”，探讨 Power BI 的不同组件，例如 Power BI Desktop、Power BI 服务和 Power BI 报表生成器。本章涵盖 Power BI 工作流中使用的常见步骤以及交互式报表、分页报表和仪表板的不同方面。

每章开头都列出了该章涵盖的目标。本书并未按顺序涵盖目标，因此你不应对书中目标的一些奇怪顺序感到惊讶。在每章末尾，你将找到以下可用于准备考试的元素：

*   *Exam Essentials* — 本节总结了本章涵盖的最重要信息。你应该能够回答与此信息相关的问题。

*   *Review Questions* — 每章末尾都有复习问题。你应该回答这些问题，并将你的答案与问题后提供的答案进行核对。如果你无法正确回答至少 80% 的问题，请回头复习本章，或者至少复习那些似乎让你感到困难的部分。

为了从本书中获得最大收益，你应该从头到尾阅读每一章，然后使用章末元素检查你的记忆和理解。即使你已经熟悉某个主题，也应该浏览该章；Azure 数据服务足够复杂，完成一项任务通常有多种方法，因此即使你在某个领域已经很熟练，也可能会学到新东西。

### Recommended Home Lab Setup

DP-900 考试中有多个目标将要求你下载和安装不同的桌面工具。这些工具在各自的章节中有所描述，并附有下载位置和使用说明。

除了这些工具外，拥有 Microsoft Azure 订阅的访问权限也很重要。由于 Microsoft Azure 是基于云的产品，你只需要一台连接互联网的计算机即可设置免费的 Azure 订阅用于实验。你可以访问 `https://azure.microsoft.com/en-us/free` 并点击 *Start Free* 来创建免费的 Azure 订阅。你需要使用 Microsoft 帐户（例如 Hotmail、Live 或 Outlook 帐户）登录。Azure 网站将引导你完成免费订阅的注册过程。虽然你需要提供联系信息和信用卡号码，但除非你升级到付费订阅，否则 Microsoft 不会收取信用卡费用。

## Interactive Online Learning Environment and Test Bank

我们整理了一些非常出色的在线工具，帮助你通过 MC Microsoft Certified Azure Data Fundamentals 考试。随本学习指南提供的交互式在线学习环境提供了一个题库和学习工具，帮助你准备考试。使用这些工具，你可以大大提高第一次就通过考试的机会。

题库包括以下内容：

*   **Sample Tests**  本书和在线中提供了许多样例测试，包括你将在本简介末尾找到的评估测试，以及每章末尾的章节复习问题。此外，还有一个奖励练习考试。使用所有这些练习问题来测试你对材料的了解。在线题库可在多种设备上运行。

*   **Flashcards**  在线文本题库包含 100 多张专门编写的闪存卡，旨在让你吃力，所以如果你一开始没有轻松通过，不要气馁！它们的存在是为了确保你真正准备好参加考试。别担心——有了评估测试、复习问题、练习考试和闪存卡，当考试日到来时，你将准备充分！问题以数字闪存卡格式提供（一个问题后跟一个正确答案）。你可以使用闪存卡来巩固学习，并在考试前进行最后的考试准备。

*   **Other Study Tools**  本书中的关键术语及其定义的术语表可作为完全可搜索的 PDF 提供。

## DP-900 Exam Objectives
