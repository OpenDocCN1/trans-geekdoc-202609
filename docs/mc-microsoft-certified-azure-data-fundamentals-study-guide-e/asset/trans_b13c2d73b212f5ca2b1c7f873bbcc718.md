

*自托管集成运行时* 用于在云数据存储与专用或本地网络中的数据存储之间运行数据移动活动。此集成运行时类型也用于触发托管在本地或 Azure 虚拟网络中的计算活动。自托管集成运行时要求在与专用或本地网络关联并连接到 ADF 中自托管集成运行时的一台或多台计算机上安装自托管集成运行时客户端应用程序。有关创建和配置自托管集成运行时的更多信息，请参阅 `https://docs.microsoft.com/en-us/azure/data-factory/create-self-hosted-integration-runtime?tabs=data-factory`。

*Azure-SSIS 集成运行时* 用于在 ADF 中执行旧版 SQL Server Integration Services (SSIS) 包。这允许用户将现有 SSIS 工作负载迁移到 Azure，而无需在 ADF 中完全重新构建其控制流和数据流。配置 Azure-SSIS 集成运行时后，用户可以利用它来驱动执行 SSIS 包活动。此活动将运行已部署的 SSIS 包。有关配置 Azure-SSIS 集成运行时的更多信息，请参阅 `https://docs.microsoft.com/en-us/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime`。

既然我们已经了解了 ADF 的核心组件，现在让我们深入了解如何通过 Azure 门户创建 ADF 实例以及如何浏览 Azure 数据工厂 Studio UI。

##### 部署 ADF 实例

以下步骤描述了如何通过 Azure 门户创建新的 Azure 数据工厂实例：

1. 登录到 `portal.azure.com` 并在页面顶部的搜索栏中搜索 *数据工厂*。单击数据工厂以转到 Azure 门户中的数据工厂页面。

2. 单击创建以开始选择 ADF 实例的配置选项。

3. *创建数据工厂* 页面包含六个选项卡，用于自定义工作区配置。让我们先探索基础选项卡中的选项。与其他服务一样，此选项卡要求您为实例选择 Azure 订阅、资源组、名称和区域。有一个选项可以选择旧版 ADF 版本，但建议使用最新版本。[图 5.16](#c05.xhtml#c05-fig-0016) 是此选项卡的完成示例。

![图 5.16 创建 ADF 实例：基础选项卡。](images/c05f016.png)

[图 5.16](#c05.xhtml#R_c05-fig-0016) 创建 ADF 实例：基础选项卡。

4. Git 配置选项卡允许您将 ADF 实例与现有的 Azure DevOps 或 GitHub 存储库集成。ADF 实体（如管道、活动、链接服务和数据集）在幕后作为 JSON 对象进行管理，可以与现有 CI/CD 存储库集成。如果您希望稍后配置 Git 管道或将 ADF 实体保存到数据工厂服务，请单击稍后配置 Git 复选框（请参阅 [图 5.17](#c05.xhtml#c05-fig-0017)）。

![图 5.17 创建 ADF 实例：Git 配置选项卡。](images/c05f017.png)

[图 5.17](#c05.xhtml#R_c05-fig-0017) 创建 ADF 实例：Git 配置选项卡。

5. 网络选项卡允许您为自动解析集成运行时以及您可能预配的任何自托管集成运行时定义网络规则。

6. 高级选项卡允许您为 Blob 和文件数据提供自己的加密密钥。默认情况下，数据使用 Microsoft 托管的密钥加密，但可以更改为客户托管的密钥，只要密钥存储在 Azure 密钥保管库中。

7. 标记选项卡允许您在 ADF 实例上放置标记。标记用于出于成本管理目的对资源进行分类。

8. 最后，查看 + 创建选项卡允许您查看设计过程中所做的配置选择。如果您对为 ADF 实例所做的选择感到满意，请单击创建按钮以开始部署实例。

ADF 实例部署完成后，返回数据工厂页面并单击新创建的工作区。单击概述页面中间的打开 Azure 数据工厂 Studio 按钮，以导航到 Azure 数据工厂 Studio 并在 ADF 生态系统中开始工作。[图 5.18](#c05.xhtml#c05-fig-0018) 是带有打开 Azure 数据工厂 Studio 按钮的概述页面示例。

![图 5.18 Azure 数据工厂概述页面](images/c05f018.png)

[图 5.18](#c05.xhtml#R_c05-fig-0018) Azure 数据工厂概述页面

单击打开 Azure 数据工厂 Studio 按钮将打开一个新的浏览器窗口，使用您的 Azure AD 凭据登录到 Azure 数据工厂 Studio。[图 5.19](#c05.xhtml#c05-fig-0019) 突出显示了 Azure 数据工厂 Studio 主页的主要功能。

![图 5.19 Azure 数据工厂 Studio 主页](images/c05f019.png)

[图 5.19](#c05.xhtml#R_c05-fig-0019) Azure 数据工厂 Studio 主页

##### 浏览 Azure 数据工厂 Studio

Azure 数据工厂 Studio 是创作 ADF 资源的中心工具。主页上有几个按钮，使用户能够非常快速地开始构建新工作流：

* 导入按钮，将用户导航到复制数据工具。此工具允许开发人员快速开始将数据从一个数据存储复制到另一个数据存储

* 编排按钮，将用户导航到创作页面，他们可以在其中开始构建管道

* 转换数据按钮，打开一个新页面，开发人员可以在其中构建映射数据流

* 配置 SSIS 按钮，将用户导航到一个新页面，他们可以在其中配置新的 Azure-SSIS 集成运行时

页面左侧有一个包含四个按钮的工具栏，包括一个主页按钮，该按钮将用户导航回 Azure 数据工厂 Studio 主页。以下列表描述了如何使用工具栏中的其他按钮来构建和管理 ADF 资源：

* 创作按钮打开创作页面，用户可以在其中构建和管理管道、数据集、映射数据流和 Power Query 活动。[图 5.20](#c05.xhtml#c05-fig-0020) 是创作页面的示例，其中包含一个从 Azure SQL 数据库将数据复制到 ADLS 的单活动管道。

![图 5.20 Azure 数据工厂 Studio 创作页面](images/c05f020.png)

[图 5.20](#c05.xhtml#R_c05-fig-0020) Azure 数据工厂 Studio 创作页面

* 监视按钮打开一个页面，该页面提供管道运行、触发器运行和集成运行时的性能指标。[图 5.21](#c05.xhtml#c05-fig-0021) 是监视页面的示例。

![图 5.21 Azure 数据工厂 Studio 监视页面](images/c05f021.png)

[图 5.21](#c05.xhtml#R_c05-fig-0021) Azure 数据工厂 Studio 监视页面

* 管理按钮打开一个页面（请参阅 [图 5.22](#c05.xhtml#c05-fig-0022)），允许您执行多项管理任务，例如此处列出的任务：

    * 创建或删除链接服务。

    * 创建或删除集成运行时。

    * 将 Azure Purview 帐户链接到元数据和数据血缘目录。

    * 将 ADF 实例连接到 Git 存储库。

    * 创建或删除管道触发器。

    * 配置客户托管的加密密钥并为 ADF 实例定义访问管理。

![图 5.22 Azure 数据工厂 Studio 管理页面](images/c05f022.png)

[图 5.22](#c05.xhtml#R_c05-fig-0022) Azure 数据工厂 Studio 管理页面

