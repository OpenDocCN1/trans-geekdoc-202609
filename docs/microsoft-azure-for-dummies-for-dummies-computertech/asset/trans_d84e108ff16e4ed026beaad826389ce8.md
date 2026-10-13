

## Azure Function App 组件

*   单个 **Function App（A）** 包含一个或多个 Functions。
*   在 Function App 的运行空间中运行的每个 Function 都存储在此处 **(B)**。
*   **Function Proxy（C）** 允许你为单个 Function App 中的所有 Functions 提供单个 API 端点，供其他 Azure 或非 Azure API 服务使用。
*   **Function Apps** 支持 **部署槽位 (D)**；它们的用途与 App Service Web 应用的部署槽位相同，并支持槽位交换。
*   **Function App Settings（E）** 是指定 Function App、Function 或 Proxy 设置的位置，具体取决于上下文。

## 先决条件：创建 Images Blob 容器

在创建 Function 之前，你应该创建此网站上传示例所需的 `images` Blob 容器。如果你已安装 **Azure Storage Explorer**，请继续！如果没有，请参阅 [第 3 章](#c03.xhtml) 了解安装详情。

![图 8-4：设计 Function App 用户界面的人没有注意到 Azure 门户其余部分的行为方式。](images/9781119612148-fg0804.png)

**[图 8-4：](#c08.xhtml#rc08-fig-0004)** 设计 Function App 用户界面的人没有注意到 Azure 门户其余部分的行为方式。

![记住](images/remember.png) **Azure Storage Explorer** 是一款免费的跨平台桌面应用程序，让处理 Azure 存储帐户变得轻而易举。请访问 [`https://azure.microsoft.com/en-us/features/storage-explorer/`](https://azure.microsoft.com/en-us/features/storage-explorer/) 获取该工具。

请遵循以下步骤为新 Function 创建 Blob 容器：

1.  **打开 Azure Storage Explorer，并向你的 Azure 订阅进行身份验证。**
2.  **展开你为 Function App 创建的存储帐户，右键单击 Blob 容器，然后从快捷菜单中选择“创建 Blob 容器”。**
    Azure 将创建该容器，并将光标置于其旁边，准备好供你命名新对象。
3.  **将容器命名为 `images`，然后按 Enter 键确认。**

## 创建 Function

很好。你快完成了。现在你需要创建一个 Function。请遵循以下步骤：

1.  **在 Azure 门户中打开你的 Function App。**
2.  **在“Functions”行中，单击加号。**
    右侧的详细信息窗格将引导你完成 Function 向导，第一步是选择开发环境。
3.  **选择“In-Portal”作为你的开发环境，然后单击“继续”。**
    Visual Studio 和 Visual Studio Code 都原生支持编写 Functions。
4.  **在“创建 Function”窗格中，单击“更多模板”，然后单击“完成并查看模板”。**
    我在 [图 8-5](#c08.xhtml#c08-fig-0005) 中展示了这一点。

    ![图 8-5：在 Azure 门户中创建 Function。](images/9781119612148-fg0805.png)

    **[图 8-5：](#c08.xhtml#rc08-fig-0005)** 在 Azure 门户中创建 Function。
5.  **单击“查看模板”以查看 Azure Function 触发器库。**
6.  **在库中，选择“Azure Blob 存储触发器”。**
    系统可能会提示你安装 Azure Storage 扩展；单击“安装”，并等待过程完成。
7.  **完成“新建 Function”边栏选项卡。**
    完成以下字段：
    *   **名称：** 我将我的命名为 `BlobUploadFx`。这是包含在 Function App 内部的 Function 的名称。名称应简短且具有描述性。
    *   **Azure Blob 存储触发器路径：** 此设置很重要。你需要保留 `{name}` 部分，因为它是一个代表任何上传 Blob 的变量。路径应如下所示：
        `images/{name}`
    *   **存储帐户连接：** 单击“新建”，然后选择你的 Function 的存储帐户。
8.  **完成后单击“创建”。**

当你在 Function App 的左侧菜单中选择你的 Function 时，可以看到你的初学者 C# 源代码。对于此示例，代码应如下所示：

```csharp
public static void Run(Stream myBlob, string name, ILogger log)
{
    log.LogInformation($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
}
```

此代码的意思是“当 Function 被触发时，将 Blob 的名称和大小写入控制台日志。”此示例很简单，以便你可以专注于 Functions 的工作原理，而不会陷入编程语言语义的泥沼中。

新 Function 包含以下三个设置边栏选项卡：

*   **集成：** 此边栏选项卡用于编辑触发器、输入和输出。
*   **管理：** 此边栏选项卡用于禁用、启用或删除 Function，以及定义授权 API 访问 Function 的主机密钥。
*   **监视：** 在此处，你可以查看成功和失败的 Function 执行，并可选择从 Function 访问 Application Insights 遥测数据。

## 测试

测试你的 Function 只需执行以下步骤：

1.  **在 Azure Storage Explorer 中，将图像文件上传到 `images` 容器。**
    为此，请选择该容器，然后单击 Storage Explorer 工具栏上的“上传”。你可以上传单个文件或整个文件夹。
    从技术上讲，你可以上传任何文件，无论是否为图像，因为所有文件都被视为 Blob。
2.  **在 Azure 门户中，选择你的 Function App，切换到“日志”视图，并观察输出。**
    [图 8-6](#c08.xhtml#c08-fig-0006) 显示了测试的输出。

![图 8-6：我们的 Azure Function 运行中。](images/9781119612148-fg0806.png)

**[图 8-6：](#c08.xhtml#rc08-fig-0006)** 我们的 Azure Function 运行中。

## 配置 Function App 设置

在讨论 Logic Apps 之前，我想确保你了解如何调整 Function App 设置。例如，你可能想要从消耗计划定价切换到 App Service 计划定价，反之亦然。或者你可能想要测试不同的运行时环境。

我在浏览 Function App 配置边栏选项卡时感到困难，主要是因为它们与 Azure 门户其余部分的 UI 完全不同。我认为某些设置控件所在位置也存在一些冗余。为了方便起见，以下是 Function App 中每个设置边栏选项卡的主要功能摘要：

![记住](images/remember.png) 你需要处于 Function App 作用域（导航 UI 中 Functions 的上方）。你可以在 [图 8-7](#c08.xhtml#c08-fig-0007) 中看到此约定。

*   **概述：** 使用此边栏选项卡停止、启动和重启 Function App。你还可以下载所有站点内容，以便在本地集成开发环境中使用。
*   **平台功能：** 大多数 Function App 设置类别都位于此边栏选项卡中。
*   **Function App Settings：** 从此边栏选项卡，你可以查看使用配额并管理主机密钥。
*   **配置，应用程序设置：** 此边栏选项卡用于管理应用程序键/值对设置和数据库连接字符串。
*   **配置，常规设置：** 此边栏选项卡用于配置体系结构；FTP 状态、HTTP 版本；远程调试。

![图 8-7：理解 Function App 与其所包含的 Functions 之间的关系。](images/9781119612148-fg0807.png)

**[图 8-7：](#c08.xhtml#rc08-fig-0007)** 理解 Function App 与其所包含的 Functions 之间的关系。

## 使用 Azure Logic Apps 构建工作流

假设你公司的市场部门希望在现有或潜在客户在 Twitter 上提及公司官方账号时收到通知。如果没有 Logic Apps，你的开发人员将不得不注册 Twitter 开发人员帐户和 API 密钥，随后他们需要深入研究 Twitter API，以了解如何将 Twitter 与公司通知平台集成。

相反，你的开发人员可以配置一个 Logic App，使其在特定的 Twitter 推文上触发，并向 Outlook 邮箱发送电子邮件，而无需了解 Twitter 或 Office 365 API。[图 8-8](#c08.xhtml#c08-fig-0008) 显示了此 Logic App 的工作流。

