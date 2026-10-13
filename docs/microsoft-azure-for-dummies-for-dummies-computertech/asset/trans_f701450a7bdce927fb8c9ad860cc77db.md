
![Remember](images/remember.png)除非你与微软签有企业协议（EA），否则你可以随时取消 Azure 订阅。但请注意，在微软允许你取消订阅之前，你需要删除所有资源。

# 第 2 章：探索 Azure 资源管理器

## 本章内容

- 了解 Azure 资源管理器
- 熟悉 Azure 区域
- 学习 Azure 管理工具

在本章中，我将带你一窥究竟，向你介绍构成 Microsoft Azure 公有云的后端服务。

乍一看，你可能会觉得即将讨论的 REST API 有点（也许不止一点）开发人员风格，超出了你的专业舒适区。请继续跟随我！我认为，无论专长为何，任何 Azure 专业人员都必须对 Azure 资源管理器架构有扎实的理解；毕竟，它是所有基于 Azure 服务的基础。

## 介绍 Azure 资源管理器

Azure 资源管理器（最常缩写为 ARM，发音同身体部位“arm”）是 Microsoft Azure 底层的部署和管理服务。你在 Azure 中采取的每一个操作，无论使用何种工具，都会调用 ARM REST API。Azure 门户只是一个 Web 前端，它抽象了 ARM REST API 的请求和响应。

“你问什么是 REST API，Tim？”你问得很好。我接下来回答这个问题。

### REST API

应用程序编程接口（API）是一种软件规范，允许与其他软件应用程序进行交互。例如，Twitter 发布其 API 规范，以允许软件开发人员利用 Twitter 服务用于他们自己的应用程序（获取推文、发布帖子等）。

表述性状态转移（REST）是一种软件开发方法论，它定义了基于 Web 的 API 如何通过使用超文本传输协议（HTTP）进行通信。

HTTP 有五种主要方法（也称为*操作*或*动词*），REST API 调用可以执行这些操作：

- `GET`：检索资源详细信息
- `POST`：创建新资源
- `PUT`：更新资源（替换现有资源）
- `PATCH`：增量更新资源（修改现有资源）
- `DELETE`：删除资源

![Technical stuff](images/technicalstuff.png)上述四种 HTTP 方法对应信息技术中的四种主要数据操作：创建、读取、更新和删除。因为我们 IT 从业者喜欢双关语和幽默梗，所以我们简称为 CRUD 操作。

嘿，此时不要被 HTTP 动词困住。我在此描述它们只是为了给你提供更完整的背景。

现在我将这些 REST API 知识与 Microsoft Azure 联系起来。ARM 的 REST API 从根本上定义了 Azure 产品和服务，并指定了如何在订阅中使用它们。

你在 Azure 中部署的每个单独工件都代表一个资源。因此，虚拟机 (VM)、Web 应用程序、数据库、存储帐户和密钥保管库在 ARM REST API 中被定义为离散的资源类型。

### 资源提供程序

在 ARM REST API 定义中，*资源提供程序* 是提供特定 Azure 产品的服务。Azure 资源提供程序的命名空间是分层排列的。

为了说明此命名空间，请考虑我的一个 Azure 存储帐户（名为 tlwstor270）的资源 ID：

```
/subscriptions/2fbf906e-1101-4bc0-b64f-adc44e462fff/resourceGroups/twtech/providers/Microsoft.Storage/storageAccounts/tlwstor270
```

首先，请注意正斜杠以及资源路径类似于统一资源标识符 (URI) 的方式。这是有意为之，因为所有 REST API 都是基于 Web 的，且专门使用 HTTP 或 HTTPS URI。你可以从左向右读取存储帐户资源 ID，以遍历 ARM REST API 命名空间：

- `subscriptions`：斜杠 (/) 下方的节点，即 ARM REST API 层级结构的顶级根节点。
- `2fb…`：托管我存储帐户的订阅的订阅 ID。
- `resourceGroups`：资源组命名空间。资源组是 Azure 中的主要部署单位。
- `twtech`：托管我存储帐户的资源组。
- `providers`：资源提供程序层级。
- `Microsoft.Storage`：管理 Azure 存储服务的资源提供程序（存储帐户只是其中一项服务）。
- `storageAccounts`：托管我存储帐户的资源组。
- `tlwstor270`：对实际存储帐户的引用。

![Tip](images/tip.png)如果你曾使用过 REST API，你可能想使用第三方产品（如 Postman ([`https://www.getpostman.com`](https://www.getpostman.com/))）来与 ARM REST API 交互。如果没有，请将浏览器指向 [`https://resources.azure.com`](https://resources.azure.com/)，使用你的订阅所有者帐户登录，并以图形方式浏览 ARM REST API 和你的 Azure 订阅资源。[图 2-1](#c02.xhtml#c02-fig-0001) 显示了该界面。

正如我之前提到的，我有一个名为 tlwstor270 的存储帐户，位于名为 `twtech` 的资源组中。以下是如何使用 Azure 资源浏览器“遍历树”：

1. **在左侧导航栏上，展开“订阅”，然后展开你的订阅。**

   在[图 2-1](#c02.xhtml#c02-fig-0001)中，我展开了我的订阅。

2. **展开 resourceGroups，然后展开你的目标资源组。** ![FIGURE 2-1: The Azure Resource Explorer allows you to view the ARM REST API directly.](images/9781119612148-fg0201.png)

   [图 2-1：](#c02.xhtml#rc02-fig-0001) Azure 资源浏览器允许你直接查看 ARM REST API。

3. **展开 providers，展开 Microsoft.Storage，然后选择你的存储帐户。**

4. **在主屏幕上，浏览定义你的存储帐户的 JavaScript 对象表示法 (JSON) 输出。**

   在[图 2-1](#c02.xhtml#c02-fig-0001)中，tlwstor270 存储帐户是我 `twtech` 资源组中唯一的资源，因此很容易在 JSON 输出中找到资源定义。请注意屏幕顶部对 HTTP 动词的引用：`GET`、`PUT`、`POST` 和 `DELETE`。

![Warning](images/warning.png)虽然 Azure 资源浏览器默认将你置于只读模式，但请注意界面顶部的“只读”按钮。如果你拥有足够的特权，你可以超越简单的 `GET` 请求，对 Azure 资源执行 `PUT`、`POST` 和 `DELETE` 操作，因此请小心！

### JSON

RESTful API 使用 JSON（通常发音为 *jay-sahn*）数据格式对所有请求和响应数据进行编码，ARM 当然也不例外。

Douglas Crockford 于 2001 年发明了 JSON，旨在以相对紧凑、人类可读的形式表示数据。JSON 文档是纯文本，可以在任何文本编辑器中打开。

![Tip](images/tip.png)如果你是 Azure 专业人员，我建议使用 Visual Studio Code 作为文本编辑器。

JSON 元素由逗号分隔的键/值对列表组成。请查看我之前讨论的 Azure 存储帐户的此 JSON 片段。注意通过查看少量代码就能了解该资源的大量信息。别担心现在还看不懂——你才刚刚开始！

```json
"sku": {
  "name": "Standard_LRS",
  "tier": "Standard"
},
"kind": "StorageV2",
"id": "/subscriptions/2fbf906e-1101/resourceGroups/twtech/providers/Microsoft.Storage/storageAccounts/tlwstor270",
"name": "tlwstor270",
"type": "Microsoft.Storage/storageAccounts",
"location": "northcentralus"
```

Azure 中的所有部署都以 JSON 格式记录。这些所谓的 ARM 模板使创建可靠、可重复的 Azure 环境变得更加容易。
