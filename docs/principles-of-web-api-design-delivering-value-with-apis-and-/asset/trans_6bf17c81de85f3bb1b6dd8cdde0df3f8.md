

# 总结

微服务是独立部署的代码单元，通过组合构建构建式系统。转向微服务需要新技术的结合以及自上而下的组织支持。当组织对决策因素进行审慎反思后，其向微服务的转型可能会带来主要收益：降低多个团队之间的协调成本。

要警惕那些带来的收益无法超过其所需复杂性的技术趋势。微服务为某些组织带来了收益，但并非没有挑战。组织必须计算迁移到微服务的成本是否大于设计、构建和运行微服务的复杂度，以判断其复杂度是否超过了单一单体代码库的复杂度。

替代方案（如模块化单体和基于单元的架构）支持微服务的许多目标，但在减少协调和优化局部决策方面的支持程度各不相同。当产生疑问时，可以应用敏捷软件的“你以后不需要它”（YAGNI）原则，从模块化单体 API 开始，并在需要出现时将其分解为微服务。

# 第11 章

## 改进开发者体验

每个交付价值的有用 API 通常会有多个消费者。
这是一种自然的不对称，并且会随着时间的推移而增加。

> — Mark O’Neill

![](img/6a422bfe4f2691ab7de274bb6978b0eb_247_0.png)

图 11.1 完善 API 设计包括通过辅助库和命令行界面来改进开发者体验。

当团队考虑交付 API 时，主要关注的是必须构建的代码。他们关注诸如因素，如目标编程语言、辅助构建 API 的框架、持续集成与交付 (CI/CD) 流水线以及其他因素。所有这些决策都是重要的，它们仅涉及 API 提供者。它们并没有直接面对未来将使用该 API 的数十、上百或数千个 API 消费者。

作为 API 提供者，在设计和交付的所有工作中将 API 消费者放在首位是非常重要的。这一责任包括创建 Mock API 以帮助早期采用者尽早获得 API 设计反馈（图 11.1）。它还需要考虑是否提供辅助库和命令行界面，以缩短所有技能水平 API 消费者的集成时间。本章旨在解决这些问题，以扩大对集成 API 的众多当前及未来 API 消费者的影响。

# 创建 Mock API 实现

API 设计是模式与主观设计决策的混合。在 API 设计阶段合理的逻辑，对于集成 API 的开发者来说可能并不合理。API Mocking（ 模拟）是创建一个 API 设计的模拟版本。生成 API 设计的 Mock 版本有助于验证 API 设计将满足目标开发者的需求。

Mock 实现交付快速，因为它们缺乏生产就绪的代码。它们还跳过了后端数据库服务器和遗留系统。Mock API 在实现 API 设计的同时，返回静态响应或基于合成数据集的响应。

通过 Mock 实现，开发者能够在实现开始之前集成 API 的部分内容。因此，API 团队可以查看 API 设计是否缺少了关键功能。Mock 实现还帮助团队识别 API 设计中可能缺失的重要数据元素。

API 设计包含了妥协。一旦开发者开始与 API 集成，他们将对如何进行更改提供反馈。如果 API 设计是冻结的，这种更改必须等到 API 的新版本发布。通过与 Mock 实现进行集成，可以尽早识别这些问题区域，且更改成本要低得多。

另一个益处是，Mock 实现有助于加速交付过程。无需等待整个 API 完成编码，可以使用 Mock 实现为前端开发生成 API 集成代码。它们还可用于驱动自动化测试的创建。随着时间的推移，Mock 集成将被真实的 API取代，直到 Mock 不再需要并被完全移除。接口保持不变，但实现随时间被替换。同时，团队可以并行进行。

API Mock 实现主要有三种类型：静态 Mock、原型（prototype）和基于 README 的 Mock。每种都可以独立使用或结合使用，在交付之前探索 API 设计。Mock 也可用于搭建与生产环境隔离的本地或云学习环境。

# 静态 API Mock

在编写代码之前探索 API 设计的最简单方法之一是编写某些或所有预期请求和响应的静态版本。静态 Mock 通过基于 JSON 或 XML 文件捕捉 API 交互，这些文件可以与开发者和 API 设计评审者共享。它们提供了在编码前查看和改进的示例。

下面的 Mock 响应演示了使用 JSON:API 规范的 Shopping API 示例中的 Resource实例：

```json
{
  "data": {
    "type": "books",
    "id": "12345",
    "attributes": {
      "isbn": "978-0321834577",
      "title": "Implementing Domain-Driven Design",
      "description": "With Implementing Domain-Driven Design, Vaughn has made an important contribution not only to the literature of the Domain-Driven Design community, but also to the literature of the broader enterprise application architecture field."
    },
    "relationships": {
      "authors": {
        "data": [
          {"id": "765", "type": "authors"}
        ]
      }
    }
  },
  "included": [
    {
      "type": "authors",
      "id": "765",
      "fullName": "Vaughn",
      "links": {
        "self": "/authors/765",
        "authoredBooks": { "href": "/books?authorId=765" }
      }
    }
  ]
}
```

可以使用 Web 服务器（如 Apache）提供静态 Mock，允许前端开发者集成 Mock。

重要的是注意的是，静态 Mock 缺乏任何实现，因此 Mock 将将限于 GET 操作。然而，创建一个获取资源的 静态 Mock 是非常有用的、易于构建的并提供了机会。

# API 原型设计 (Prototypeing)

丢弃型原型比静态 Mock 能对 API 设计提供更佳的验证。与通常限于 GET 操作的静态 Mock 不同，API 原型能够支持所有类型的操作。

手动制作 API 原型需要更多精力。通常，团队会选择一种常用的语言和框架进行快速交付。Ruby、Python、PHP 和 Node.js 因为其开发便利和丰富的库成为热门选择。

团队可能希望选择不支持生产的语言和框架。这样做可以确保旨在丢弃的原型变成生产代码。

使用基于 API 描述（如 OpenAPI 规范）的 API Mock 工具允许团队跳过大部分或全部开发工作。这些工具为常见的增删改查（CRUD）操作生成临时数据。某些工具为实现生成代码，另一些动态创建 Mock API。

建议保持 API 原型简单。根据需要扩展原型，以深入需要进一步探索或可以鼓励并行开发的领域。

# 基于 README 的 Mock

基于 README 的 Mock 提供了一种无需编写代码的替代原型风格。创建一个 README 文件来演示如何使用 API 完成一个或多个预期结果。基于 README 的 Mock 通过共享使用 API 的意图，在实现开始之前验证 API 设计。

大多数基于 README 的 Mock 使用 Markdown，使得文本和示例易于生成并在浏览器中渲染。GitHub 和 GitLab 等工具具有内置的 Markdown 支持，尽管也可以使用静态网站生成工具如 Jekyll 或 Hugo。

下面是一个基于 README 的 Mock，演示了如何使用 JSON:API 媒体格式获取书籍详情，然后将其加入购物车：

- 1. 获取书籍详情

```http
GET /books/12345 HTTP/1.1
Accept: application/vnd.api+json

HTTP/1.1 200 OK
Content-Type: application/vnd.api+json
{
  "data": {
    "type": "books",
    "id": "12345",
    "attributes": {
      "isbn": "978-0321834577"
    }
  }
}
```

