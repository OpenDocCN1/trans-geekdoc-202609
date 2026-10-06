

# 第 124 页 第7 章 基于 REST 的 API 设计

![](img/6a422bfe4f2691ab7de274bb6978b0eb_158_0.png)

**图 7.12** 使用序列图来验证 API 设计是否满足之前建模的需求。

## 第 5 步：共享并收集反馈

最后一步是共享 API 设计，以获取直接团队、组织内的 API 架构师以及计划在 API 准备绪后立即集成的内部/外部团队的反馈。

一旦 API 正式发布并集成，API 设计就会被锁定，之后只能进行非破坏性的更改。可以添加新的端点，可能会向现有的资源表示中添加新字段，但重命名或修改现有端点会破坏现有的 API 消费者，导致客户不满，并可能引发客户流失。第一次做对至关重要。尽早共享 API 设计以获取反馈有助于避免发布后发生重大的设计变更。

API 的 Mock（模拟）实现也有助于探索 API 设计。因为阅读 API 文档只能对 API 有基本的了解，Mock 实现为开发者提供了一个使用模拟数据体验 API 如何运行的机会。目前开始出现一些工具，它们可以接受 OAS 等 API 描述格式，并在无需编写一行代码的情况下生成 Mock API 实现。

请参阅第 16 章“继续 API 设计之旅”，了解其他 API 全生命周期技术，这些技术有助于在 API 开发和部署后仍获得反馈。

## 选择表示格式

到目前为止，关于资源设计的讨论集中在资源名称和属性上。然而，API 资源的表示格式也需要确定。选择表示格式是重要的一步。

对于某些组织来说，首选表示格式已经作为 API 风格指南的一部分确定。在这种情况下，决策已经做出，无需采取进一步行动。但是，如果这是一个新的 API 产品、程序或平台，则需要投入更多工作来完成设计。

尽可能选择一种单一格式作为所有 API 提供的默认表示。使用单一格式可以确保开发者在与该组织及其未来的 API 集成时保持一致性。

随着时间的推移可能会添加额外的格式，允许在不破坏现有集成的情况下缓慢迁移到新格式。多格式方法需要使用 HTTP 让客户端指定所需的表示格式。内容协商（Content negotiation）在附录 I 中进行了讨论。

表 7.4 总结了可用的四类表示格式。每个类别都建立在前一个的基础上，为资源和消息格式提供了更多选项。然而，随着选项的增加，复杂度也随之增加。每个类别都进行了解释，并提供了一个示例。本章提供的示例可在 GitHub 工作库中找到。

4. https://bit.ly/design-examples

第7 章 基于 REST 的 API 设计

表 7.4 API 表示格式分类
| 类别 | 概述 |
| --- | --- |
| 资源序列化 (Resource Serialization) | 将资源表示为各种格式，例如 JSON、XML、Protocol Buffers 和 Apache Avro |
| 超媒体序列化 (Hypermedia Serialization) | 支持嵌入超媒体控件的序列化表示 |
| 超媒体消息 (Hypermedia Messaging) | 支持超媒体控件属性的通用格式 |
| 语义超媒体消息 (Semantic Hypermedia Messaging) | 支持超媒体字段映射的通用格式 |

## 资源序列化
资源序列化表示格式最为常见。它们直接将资源的属性及其值映射到所需的格式，通常是 JSON、XML 或 YAML。Protocol Buffers 和 Apache Avro 等二进制格式也越来越受到接受。

这些表示格式需要显式代码来处理资源与目标格式之间的序列化。这种映射逻辑可以通过代码生成器或硬编码来实现。格式化程序和表示库通常有助于管理目标格式与表示资源的对象或结构之间的映射。

无论如何处理序列化，解析和映射代码都是唯一的，因为它必须感知预期的字段和嵌套结构。列表 7.1 提供了一个使用 JSON 序列化表示 Book 资源的示例。

### 列表 7.1 使用 JSON 的序列化表示

```json
{
  "bookId": "12345",
  "isbn": "978-032183457",
  "title": "Implementing Domain-Driven Design",
  "description": "Vaughn 不仅对领域驱动设计社区文献，还对更广泛的企业应用领域做出了重要贡献。",
  "authors": [
    { "authorId": "765", "fullName": "Vaughn Vernon" }
  ]
}
```

+   5. https://developers.google.com/protocol-buffers/docs/proto3
6. https://avro.apache.org/docs/current

基于序列化的格式仅使用键值对提供资源的属性。

## 超媒体序列化
超媒体序列化类别与资源序列化类似，但增加了关于如何表示超媒体链接的规范。它还可能包含统一方式包含相关和/或嵌套资源（称为*嵌入资源*）的规范。

超文本语言（HAL）等格式允许以很少或没有更改扩展序列序列格式。这防止了在将基于序列化的 API 迁移到包含超媒体时破坏 API 客户端。列表 7.2 显示了一个基于 HAL 的表示示例。

### 列表 7.2 使用 HAL 的超媒体序列化

```json
{
  "bookId": "12345",
  "isbn": "978-032183457",
  "title": "Implementing Domain-Driven Design",
  "description": "Vaughn 不仅对领域驱动设计社区文献，还对更广泛的企业应用领域做出了重要贡献。",
  "links": {
    "self": { "href": "/books/12345" }
  },
  "embedded": {
    "authors": [
      {
        "authorId": "765",
        "fullName": "Vaughn Vernon",
        "_links": {
          "self": { "href": "/authors/765" }
        }
      }
    ]
  }
}
```

⁷. Mike Kelly,"JSON Hypertext Application Language" (2016),https://tools.ietf.org/html/draft-json-hal-08.

第7 章 基于 REST 的 API 设计

```json
  "links": {
    "self": { "href": "/authors/765" },
    "authoredBooks": { "href": "/books?authorId=765" }
  }
```

并不是所有的超媒体格式都提供相同的功能。Mike Amundsen 创建了这些因素的列表，称为 H-Factors⁸，支持对超媒体支持的水平和复杂性进行推理。

## 超媒体消息
超媒体消息格式与序列化的区别在于，它们提出了一种统一的基于消息的格式来捕捉资源属性、超媒体控件和嵌入资源。这使得对所有资源使用单一解析器比为每种资源类型编写唯一的映射代码来解析序列化格式变得简单。

虽然序列化和基于消息的格式之间的差异是微妙的，但考虑到团队将不再担心 JSON 或 XML 负载应该什么样。相反，他们将关注消息格式中的资源表示、关系和超媒体控件。不再需要开会来决定是否需要在 JSON 响应周围数据包装器！

超消息格式包括 JSON:API 和 Siren¹⁰ 这两种格式都提供了一种单一结构消息，足以包含复杂的资源表示和嵌入资源，并且都提供了超媒体控件支持。

Siren 的消息能力与 JSON:API 类似，但它还增加了有助于以最小定制工作创建 Web 用户界面的元数据。

JSON:API 是一种规范，消除了 API 风格指南中常见的设计选项决策。表示格式、何时使用不同的 HTTP 方法以及如何通过响应塑造和相关资源的预取来优化连接，只是 JSON:API 已经提供的决策之一。

列表 7.3 提供了一个 JSON:API 基于消息的表示示例。

+   8. http://amundsen.com/hypermedia/hfactor
9. https://jsonapi.org
10. https://github.com/kewinsiber/siren

