
![Tip](images/tip.png)虽然你是使用 Azure CLI 创建此应用服务 Web 应用，但你也可以使用 Azure 门户、PowerShell、软件开发工具包 (SDK) 或 Azure REST API。由于 Microsoft 对 Azure 门户进行了大量更新，你最好主要专注于 Azure CLI 或 PowerShell，以获得更稳定、更熟悉的部署环境。

2. **使用 Azure CLI 创建新的资源组。**

    使用你自己的资源组名称和位置。我使用的是：

    `az group create --name containerApp --location "East US 2"`

3. **创建应用服务计划为 Web 应用提供支持。**

    应用服务计划定义托管 Web 应用程序的底层计算层 (VM)。在此，你将使用 B1 VM 实例大小创建一个基于 Linux 的服务计划：

    `az appservice plan create --name myAppServicePlan --resource-group containerApp --sku B1 --is-linux`

4. **定义 Web 应用。**

    我将我的应用命名为 go-container-704 以使名称全局唯一，并从 Docker Hub 拉取了 `microsoft/azure-appservices-go-quickstart` 容器映像。你可以通过访问 [`https://hub.docker.com/r/microsoft/azure-appservices-go-quickstart/`](https://hub.docker.com/r/microsoft/azure-appservices-go-quickstart/) 来检查该容器。

    `az webapp create --resource-group containerApp --plan myAppServicePlan --name go-container-704 --deployment-container-image-name microsoft/azure-appservices-go-quickstart`

    ![Tip](images/tip.png)你可以通过访问 [`https://hub.docker.com/r/microsoft/azure-appservices-go-quickstart`](https://hub.docker.com/r/microsoft/azure-appservices-go-quickstart) 来检查该容器。

5. **浏览到该应用。**

    项目的 URL 格式为 http:// http://<*app\_name*\>.azurewebsites.net/hello。使用该地址（替换为你自己的应用名称）。

6. **验证你是否看到** [**图** **6-9**](#c06.xhtml#c06-fig-0009) **中所示的简单 `Hello, world!` 消息。**

    你的新容器支持的应用出现在 Azure 门户的“应用服务”边栏选项卡中。

    ![图 6-9：由 Docker 容器提供支持的新 Azure Web 应用。](images/9781119612148-fg0609.png)

    [图 6-9：](#c06.xhtml#rc06-fig-0009) 由 Docker 容器提供支持的新 Azure Web 应用。

7. **清理环境。**

    因为你将此测试 Web 应用存储在其自己的资源组中，所以清理起来非常轻松。运行最后一条 Azure CLI 命令，并确认你的选择：

    `az group delete --name containerApp`

# 第 3 部分：将平台资源部署到 Microsoft Azure

## 本部分内容……

*   部署和配置应用服务应用
*   通过使用 Azure WebJobs、Functions 和 Logic Apps 理解 Azure 中的“无服务器计算”
*   描述 Azure 中的关系型和非关系型数据库选项
*   亲身体验 Azure SQL 数据库和 Cosmos DB

# 第 7 章：部署和配置 Azure 应用服务应用

## 本章内容

*   **了解 Azure 应用服务家族成员**
*   **部署应用服务 Web 应用**
*   **配置你的 Web 应用**
*   **启用遥测**

作为 Microsoft Azure 解决方案顾问，我的乐趣之一就是看着客户在发现 Azure 平台即服务 (PaaS) 资源的强大功能和敏捷性时的表情；Azure 应用服务首当其冲。

Azure 应用服务让你能够专注于业务线应用程序，而无需管理 VM 基础设施。应用服务提供超大规模，并与存储帐户和 Azure SQL 数据库等其他 Azure 产品无缝集成。

在本章结束时，你将了解应用服务在 Azure 产品组合中的地位。你还将能够熟练创建和配置应用服务 Web 应用。当然，特定的编程语言超出了本书的范围，因此我将重点放在应用服务的操作方法和原理上，而将代码库留给你和你的团队。

## 介绍 Azure 应用服务

简而言之，应用服务是一种基于超文本传输协议 (HTTP) 的 Web 应用程序托管服务。可以把它想象成 GoDaddy，但功能强大得多。其理念是：如果你愿意放弃对应用底层基础设施的完全控制（这正是 Azure 虚拟机的用途），你将获得以下回报：

*   全球复制和地域可用性
*   动态自动缩放
*   原生集成到持续集成/持续部署管道中

是的，应用服务在底层使用虚拟机 (VM)，但你永远不必担心维护它们；Microsoft 会为你处理这些。相反，你几乎完全专注于你的源代码和应用程序。

本章几乎完全专注于 Web 应用，但在 [第 8 章](#c08.xhtml) 中你将了解其他应用服务家族成员。

### Web 应用

静态或动态 *Web 应用程序* 是应用服务中最常用的选项。你托管的 Web 应用可以链接到云端或本地数据库、API Web 服务和内容分发网络。

### API 应用

*应用程序编程接口* (API) 是一种机制，它通过使用 HTTP 请求和响应为你的应用程序提供编程（非交互式）访问——一种称为表述性状态传递 (REST) 的编程范式。如今，Microsoft 支持来自应用服务和 API 管理服务的 API 应用。

### 移动应用

*移动应用* 为 iOS 或 Android 应用程序提供后端。Azure 移动应用提供了大多数智能手机用户已习惯期望的功能，作为他们使用的移动应用的一部分，例如社交媒体登录、推送通知和脱机数据同步。

### 逻辑应用

*逻辑应用* 为开发人员提供了一种构建业务工作流的方法，而无需了解不同服务中所有底层 API。例如，你可以创建一个逻辑应用，每当有人在 Twitter 上提及你公司的名称时触发。然后此应用可能会执行多个操作，例如在你销售部门的 Slack 频道中发布通知消息，或在你的客户关系管理数据库中创建一条记录。

### 函数应用

*函数应用* 允许开发人员在特定时间运行特定代码，而无需担心底层基础设施。这就是为什么函数应用被称为 *无服务器* 应用程序，或 *代码即服务 (CaaS)* 解决方案。我的一位咨询客户拥有一个函数应用，每当用户在其网站上创建新帐户时，该应用就会向潜在客户发送确认电子邮件。

函数应用支持 C#、F# 和 Java 编程语言。

![Remember](images/remember.png)逻辑应用和函数应用均基于触发器运行。此触发器可以是手动执行命令、时间计划，或是在 Azure 内部或外部发生的离散操作。

### 应用服务逻辑组件

[图 7-1](#c07.xhtml#c07-fig-0001) 显示了构成应用服务的组件。应用服务 Web 应用由关联的应用服务计划提供支持。此计划是一个抽象层；你可以控制为应用程序提供支持所需的虚拟计算量，并动态地垂直缩放以满足你的性能要求和预算需求。

![图 7-1：应用服务所需和可选组件。](images/9781119612148-fg0701.png)

[图 7-1：](#c07.xhtml#rc07-fig-0001) 应用服务所需和可选组件。

在 [图 7-1](#c07.xhtml#c07-fig-0001) 中，应用服务计划是唯一必需的组件。你可以通过将应用与以下任何一项集成来扩展其功能：

*   **存储帐户：** 应用服务计划具有持久性存储，但许多开发人员喜欢使用灵活的存储帐户以获取额外空间。
