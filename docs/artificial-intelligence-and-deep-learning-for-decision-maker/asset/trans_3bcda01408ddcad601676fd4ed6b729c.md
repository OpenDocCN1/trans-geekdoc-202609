
# IBM Watson Explorer 模块概述

本主题提供了 IBM Watson Explorer 模块的高级概述。它用于创建 360 度信息应用程序。它包括有关 `Explorer Engine` 的各种逻辑组件和功能的信息、它们之间的交互以及在探索企业信息时的安全性。

`Watson Explorer Engine` 提供模块化且灵活的架构。它与网络数据存储库和可通过网络访问的数据源进行交互。该架构简化了单一导航信息应用程序的创建。该应用程序可以轻松探索以各种格式存储且位于不同位置的内容。

它包括应用独有的格式。它还由网络存储库中发现的不同格式的组合组成。`Watson Explorer Engine` 通过创建文档索引来帮助探索存储库中的数据。从单个数据存储库创建文本索引有多种方法：

* 爬取存储库意味着从池中检索数据、元数据和安全信息。每当爬取存储库时遇到困难，`Watson Explorer` 支持服务器端应用程序将数据从数据存储库推送到 `Watson Explorer` 安装。
* 为了处理和增强检索到的数据，数据必须采用标准格式。数据应采用标准形式，例如与其链接的 `URL`、原始文件类型和权限信息。
* 创建数据的索引。

## 功能组件

下图显示了 `Watson Explorer Engine` 的各种功能组件、交互以及外部数据存储库：

![](OEBPS/images/fig_5.7.jpg)

图 5.7：Watson Explorer Engine 的各种功能组件、交互和外部数据存储库

上图显示了它们在应用程序的信息导航和搜索中的用途。下几节将详细介绍 `Watson Explorer Engine` 架构的组件：

![](OEBPS/images/fig_5.8.jpg)

图 5.8：Watson Explorer Engine 架构的组件

## 架构组件

以下要点描述了 `Watson Explorer Engine` 架构的组件：

### 连接器和爬取
`Watson Explorer Engine` 可以使用 `Universal Resource Locator` 访问和索引任何数据。`Watson Explorer Engine` 已提供连接器以定位和检索远程存储库中的数据。数据存储库中为每个数据项检索 `URLs`，并使用称为 `crawler` 的组件将其排队到 `Watson Explorer Engine`。`crawler` 从每个排队的 `URL` 检索数据并将其传递给相应的元数据。提取的数据用于使用另一个称为 `pull connectors` 的组件进行后续预处理。这些连接器负责从远程存储库检索 `URLs` 和数据。

爬取远程存储库数据的另一种方法是安装称为 `push connectors` 的服务器端组件。这些连接器直接将远程存储库中的数据排队。它们对于不提供合适的 API 或爬取不可能或不足的存储库非常有用。

### 转换和增强用于索引的数据
在通过 `URL` 识别数据并由 `crawler` 从远程存储库检索后，它会被移交给称为 `converters` 的一系列应用程序。这些 `converters` 用于规范化，并在需要时进行增强。`crawler` 检索到的数据根据相应存储库采用特定格式。因此，索引器有必要理解所有这些格式。这导致复杂性增加，并使其重点偏离索引。此外，还需要对索引器进行更改以启用对以前未见文档的索引。

索引应准确且快速，以便它可以纯粹专注于索引而不是转换。提取的数据应规范化并转换为 `Watson Explorer Engine` 内部使用的特定格式。它是通过使用称为 `conversion pipeline` 的连接器序列处理数据来执行的。

在 `conversion pipeline` 中，相应的 `converter` 将数据从一种格式转换为另一种格式，或在需要时执行增强，甚至在将其传递到下一个 `converter` 之前添加输入数据中的信息。可用的连接器组合有两种，例如：

* `Standard converters`：它们随 `Watson Explorer Engine` 一起提供。
* `Custom converters`：它们由 `Watson Explorer Engine` 编写，以提取和增强特定格式的数据。

每个 `converter` 由输入和输出类型组成。只有 `conversion pipeline` 中与初始输入数据和前一个 `converters` 的输出数据的特征和功能相匹配的 `converters` 才会激活。

`conversion pipeline` 还负责遵循预定义序列。它授权特定数据的增强过程，并遵循支持相同类型输入的其他 `converters` 的转换格式：

* `Watson Explorer Engine` 内部遵循的标准格式称为 `Vivisimo XML (VXML)`。它经过充分记录且由较少模式数据语法组成。
* 它由每个检索到的数据的多个属性组成。它负责保留与原始存储库关联的内容的元数据。
* 它可以将对应于单个 `URL` 的数据拆分为多个拆分，以提供原始数据结构和组成的 information。这有助于以不同的方式处理和索引数据。
* `Converters` 也可以用于仅为显示目的添加不可搜索的元数据。

### 索引数据
`Watson Explorer Applications` 使用索引进行数据探索和信息导航。查看每个远程存储库以提取特定信息是一项非常困难的工作。因此，需要同时探索多个索引。它提供了各种优势，例如：

* 改进了众多流程的优化，例如从远程存储库连接和获取数据、从输入数据标准化、增强和索引。这通过创建和更新特定索引提高了性能。
* 减少给定索引的大小。此功能有助于减少即时和基础设施存储需求。
* 减少访问索引内数据所需的时间和资源。

为满足 `Watson Explorer Engine` 的 `reliability, availability, and serviceability (RAS)` 要求，可以配置索引以使其在多个 `Watson Explorer Engine` 安装之间进行复制。它被称为 `distributed indexing`。

所有副本中的更新会通过关联数据存储库中的内容更改自动分发到其他模型。我们需要以事务方式执行索引同步，以加强所有索引副本之间成功且稳定的更新：

### 通过查询路由利用现有搜索应用程序
有可能将现有搜索应用程序的搜索结果与 `Watson Explorer` 的数据探索和导航功能相结合。该过程称为 `query routing`。它用于将探索查询导航到现有搜索应用程序以及由 `Watson Explorer Engine` 索引的内容。它有助于在 360 度信息应用程序中访问所有可用信息。
