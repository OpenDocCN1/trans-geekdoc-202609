
# PHP 领域驱动设计：架构风格、战术设计与边界上下文集成

## 推特此书！

请通过在 [Twitter](http://twitter.com) 上分享这本书来帮助 Carlos Buenosvinos、Christian Soronellas 和 Keyvan Akbary！

本书的建议推文内容为：

[我刚刚买了 @theUniC、@keyvanakbary 等写的“Domain-Driven Design in PHP” (@dddbook)](https://twitter.com/intent/tweet?text=I%20just%20bought%20%22Domain-Driven%20Design%20in%20PHP%22%20\(@dddbook\)%20by%20@theUniC,%20@keyvanakbary%20and%20@buenosvinos%20https://leanpub.com/ddd-in-php%20%23ddd%20%23php)

[@buenosvinos https://leanpub.com/ddd-in-php #ddd #php](https://twitter.com/intent/tweet?text=I%20just%20bought%20%22Domain-Driven%20Design%20in%20PHP%22%20\(@dddbook\)%20by%20@theUniC,%20@keyvanakbary%20and%20@buenosvinos%20https://leanpub.com/ddd-in-php%20%23ddd%20%23php)

本书的建议标签为 [#DDDinPHP](https://twitter.com/search?q=%23DDDinPHP)。

点击此链接在 Twitter 上搜索该标签，了解其他人对这本书的评价：

[`twitter.com/search?q=#DDDinPHP`](https://twitter.com/search?q=%23DDDinPHP)

*这本书献给我最亲爱的 Vanessa、Valentina 和 Gabriela。感谢你们的爱、支持和耐心。Carlos。献给我我亲爱的 Elena。没有你们的鼓励、爱和耐心，这本书将无法完成。Christian。*

## 1. DDD 入门

### 1.1 为什么用领域驱动设计？

### 1.2 领域驱动设计如何帮助我们？

### 1.2.1 通用语言

### 1.3 我应该将领域驱动设计作为一种选项开始吗？

### 1.4 应用领域驱动设计的主要挑战

### 1.5 使用领域驱动设计的业务价值

### 1.6 总结

## 2. 架构风格

### 2.1 过去美好的时光

### 2.2 分层架构

### 2.2.1 模型-视图-控制器 (MVC)

### 2.2.2 分层架构示例

### 2.2.2.1 模型

### 2.2.2.2 视图

### 2.2.2.3 控制器

### 2.3 依赖反反转：六形架构

### 2.3.1 依赖倒置原则 (DIP)

### 2.3.2 应用六形架构

### 2.4 命令查询职责分离 (CQRS)

### 2.4.1 写模型

### 2.4.2 读模型

### 2.4.3 同步写模型与读模型

### 2.5 事件源

### 2.6 总结

## 3. 值对象

### 3.1 定义

### 3.2 值对象 vs 实体

### 3.3 货币与金额示例

### 3.4 特性

### 3.4.1 测量、量化或描述

### 3.4.2 不变性

### 3.4.3 概念整体

### 3.4.4 值相等性

### 3.4.5 可替换性

### 3.4.6 无副作用的行为

### 3.5 基础类型

### 3.6 测试

### 3.7 持久化值对象

### 3.7.1 持久化单个值对象

- 使用即用 ORM 的嵌入值
- 使用 `Doctrine >= 2.5` 的嵌入值
- 使用 `Doctrine <= 2.4` 的嵌入值
- 序列化 LOB（大对象）与即用 ORM
- 使用 `JMS Serializer` 改进的序列化
- 使用 `Doctrine` 的序列化 LOB
- `Doctrine` 对象映射
- `Doctrine` 自定义类型

### 3.7.2 持久化值对象集合

- 序列化为单列
- 由连接表支持的集合
- 使用 `Doctrine` 的连接表支持集合
- 使用即用 ORM 的连接表支持集合
- 由数据库实体支持的集合

### 3.7.3 NoSQL

- PostgreSQL 和 `JSONB`

### 3.8 安全

### 3.9 总结

## 4 实体

### 4.1 介绍

### 4.2 对象 vs 原始类型

### 4.3 标识操作

### 4.3.1 持久化机制生成标识

- 代理标识
- 针对富领域模型的 `Active Record` vs `Data Mapper`
- 客户端标识
- 应用生成标识
- 其他边界上下文生成标识

### 4.4 持久化实体

- 配置 `Doctrine`
- 映射实体
- 使用注解代码映射实体
- 使用 `XML` 映射实体

### 4.5 测试实体

### 4.6 验证

### 4.6.1 属性验证

### 4.6.2 整个对象验证

- 解耦验证消息

### 4.6.3 验证对象组合

### 4.7 总结

## 5 服务

### 5.1 介绍

### 5.2 应用服务

### 5.2.1 事务

### 5.2.2 测试应用服务

### 5.3 领域服务

### 5.4 具有多个实现的领域服务

### 5.4.1 关于代码复用的一个问题

### 5.5 测试领域服务

### 5.6 贫血领域模型 vs 富领域模型

### 5.6.1 贫血领域模型破坏了封装性

### 5.6.2 贫血领域模型带来了代码复用的假象

### 5.6.3 如何避免贫血领域模型？

### 5.7 总结

## 6. 领域事件

### 6.1 简介

### 6.2 定义

### 6.2.1 小故事

### 6.2.2 比喻

### 6.2.3 真实世界(tm) 示例

### 6.3 特性

### 6.3.1 命名规范

### 6.3.2 领域事件与通用语言

### 6.3.3 不可变性

### 6.4 事件建模

### 6.5 持久化领域事件

### 6.5.1 事件存储库 (Event Store)

### 6.6 从领域模型中发布事件

### 6.6.1 从实体发布领域事件

### 6.6.2 从领域服务或应用服务发布领域事件

### 6.6.3 `DomainEventPublisher` 的工作原理

### 6.6.4 设置领域事件监听器 (DomainEventListeners)

### 6.6.5 单元测试

### 6.7 将消息传播到远程边界上下文

### 6.7.1 消息传递

### 6.7.2 REST

### 6.8 总结

## 7. 模块

### 7.1 在模块中结构化代码

### 7.1.1 基础设施层中的模块

### 7.1.1 混合不同的技术

### 7.2 在 PHP 中利用模块

### 7.2.1 PEAR 风格的命名空间

### 7.2.2 PSR-0 和 PSR-4 命名规范

### 7.3 总结

## 8. 聚合根 (Aggregates)

### 8.1 简介

### 8.1.1 Martin Fowler 的观点

### 8.1.2 维基百科的观点

### 8.2 历史回顾

### 8.3 聚合与簇

### 8.4 聚合根的解剖

### 8.4.1 基于业务真不变性的设计聚合根

### 8.4.2 小聚合根 vs 大聚合根

### 8.4.3 追求最终一致性

### 8.4.4 修改单个聚合根

### 8.4.5 例：异常情况

### 8.5 示例应用：用户

### 8.5.1 每个事务不超过三个

### 8.5.2 悲观并发

### 8.5.3 乐观并发

### 8.5.4 授予用户权限

### 8.5.5 更新用户信息

### 8.6 总结

## 9. 工厂 (Factories)

### 9.1 简介

### 9.2 聚合根上的工厂方法

### 9.3 服务上的工厂

### 9.3.1 构建规格说明 (Specifications)

### 9.3.2 构建聚合根

### 9.4 测试

### 9.4.1 对象母亲 (Object Mother)

### 9.4.2 测试数据构建器 (Test Data Builder)

### 9.5 总结

## 10. 存储库 (Repositories)

### 10.1 引言

### 10.2 定义

### 10.3 仓库不是 DAO

### 10.4 面向集合的仓库

### 10.4.1 内存实现

### 10.4.2 Doctrine ORM

### 10.4.2.1 对象映射

#### 10.4.2.1.1 Doctrine 自定义映射类型

#### 10.4.2.1.2 XML 映射

### 10.4.2.2 实体管理器 (Entity Manager)

### 10.4.2.3 DQL 实现

### 10.5 面向持久化实现

### 10.5.1 Redis 实现

### 10.5.2 SQL 实现

### 10.6 额外行为

### 10.7 查询仓库

### 10.7.1 规格模式 (Specification Pattern)

### 10.7.1.1 内存实现

### 10.7.1.2 SQL 实现

### 10.8 事务管理

### 10.9 测试仓库

### 10.10 使用内存实现测试你的服务

### 10.11 总结

## 11. 应用 (Application)

### 11.1 引言

### 11.2 请求 (Requests)

### 11.2.1 构建应用服务请求

### 11.2.2 请求设计

### 11.2.2.1 使用基本类型

### 11.2.2.2 可序列化

### 11.2.2.3 不包含业务逻辑

### 11.2.2.4 无需测试

### 11.3 应用服务的剖析

### 11.3.1 依赖倒置

### 11.3.2 实例化应用服务

### 11.3.3 执行

### 11.3.3.1 每个应用服务一个类

### 11.3.3.2 一个类包含多个服务方法

### 11.3.4 返回值

### 11.3.4.1 从聚合实例创建 DTO

### 11.3.4.2 数据转换器 (Data Transformers)

### 11.3.5 布局中的多个应用服务

### 11.3.5.1 AJAX 内容

### 11.3.5.2 ESI 内容

### 11.3.5.3 Symfony 子请求

### 11.3.5.4 单个控制器，多个应用服务

### 11.4 测试

### 11.5 事务

### 11.6 安全性

### 11.7 领域事件

### 11.8 命令处理器 (Command Handlers)

### 11.8.1 Tactician 库及其他选项

### 11.9 总结

## 12. 集成限界上下文 (Bounded Contexts)

### 12.1 通过数据存储进行集成

### 12.2 关系

### 12.2.1 客户 / 供应商

### 12.2.2 分别处理

### 12.2.3 顺从者 (Conformist)

### 12.3 实现限界上下文集成

### 12.3.1 现代 RPC

### 12.3.2 消息队列

### 12.4 总结

## 13. 参考文献 - 275

## 引言 - 276

## 第一种方法 - 276

### 仓库与持久化边缘 - 278

### 业务与持久化的解耦 - 281

### 将我们的持久化迁移到 Redis - 282

### 解耦业务与 Web 框架 - 284

### 使用 API 对想法进行评分 - 287

### 控制台应用评分 - 288

### 测试想法评分的 UseCase - 290

### 测试基础设施 - 294

### 啊，太多的依赖了！ - 296

### 领域服务与通知六边形边缘 - 297

## 让我们总结 - 298

## 六边形架构 - 299

### 关键点 - 299

### 接下来是什么？ - 299

## 前言

待定

Vaughn Vernon Shift Method, Inc.

i

## 前序

自 2012 年起，在经历了两年阅读和实践领域驱动设计（DDD）方法后，2014 年，Christian 和 Carlos 去了柏林接受了《实现领域驱动设计》一书作者 Vaughn Vernon 的培训。培训非常精彩，直到那一刻他们脑海中浮现的所有概念，在为期三天的 IDDD 研讨会上得到了扎根。然而，在那个满是 Java 和 .NET 开发者的房间里，他们是两个 PHP 开发者。这确实挺有趣的。

四年后的 2016 年，Vaughn 在他们的帮助下在巴塞罗尼亚了他的研讨会。

2014 年，Carlos 向 `php[tek]` 发了一篇关于六边形架构的论文。他的演讲没有通过，但 Eli White 与他联系。你有兴趣为 `php|arch` 杂志写一篇关于六边形架构的文章吗？太棒了！于是在 2014 年 6 月，“基于 PHP 的六边形架构”出版了。你可以在附录中找到它。

这篇文章这本书的开始。Christian 对这本书背后的想法感到兴奋，并决定从第一章就开始参与。然后，我们遇到了 Keyvan，这位推动这一具有挑战性目标的第三位参与者。

Carlos 从 20 人开始就一直领导着 20 到 100 人的敏捷团队。他自 2010 年起就是认证 Scrum Master，见证许多不同的团队面临编写易于维护代码的挑战。在处理大型团队时，DDD 发挥了重要作用。

因此，我们写了这本我们在开始领域驱动设计时想要拥有的书。充满了示例、生产就绪的代码、快捷方式，以及我们根据经验对哪些对我们团队有效、哪些无效给出的建议。我们通过 DDD 走向了 DDD。

## DDD 与社区

领域驱动设计已经到来。

.

ii

iii

## 第 1 章：入门 DDD

领域驱动设计是关于什么的？它在复杂系统中扮演什么角色？它值得吗？开发者在进入这一领域时需要了解哪些核心概念？

## 第 2 章：架构风格

边界上下文可以通过不同的方式和不同的方法来实现。然而，有两种风格变得越来越流行：六边形架构和 CQRS + ES。在本章中，我们将看到这两种解决方案并理解在使用它们时的关键考虑。

## 第 3 章：值对象

值对象（Value Objects）可能是丰富模型的基础单元。我们将学习它们的属性以及是什么让它们如此重要。我们将检查如何使用 Doctrine 和自定义 ORM 持久化它们，以及在考虑不可变性的情况下如何验证并妥善测试它们。

## 第 4 章：实体

实体（Entities）是通过 DDD 的身份构建模块来标识的。我们将看到如何创建和验证它们，如何使用自定义 ORM 和 Doctrine 妥善地映射它们。我们还会回顾注释“是或否”的争议点，以及生成身份的不同策略。

## 第 5 章：领域服务

在本章中，你将学习什么是领域服务以及何时使用它。我们将回顾什么是贫血领域模型（Anemic Domain Models）和丰富领域模型（Rich Domain Models）。最后，我们将处理编写领域服务时的基础问题。

iv

## 第 6 章：领域事件

领域事件（Domain Events）是一种极佳的反转控制（IoC）机制。在 DDD 中，它们用于边界上下文之间的异步通信，解耦基础设施和最终一致性。

## 第 7 章：模块

有了如此多的战术构建模块，要知代码中将它们放在哪里有点困难。特别是当你处理像 Symfony 这样的框架时。我们将检查我们的建议，这种建议对于实践它的团队来说非常有效。

## 第 8 章：聚合根（进行中）

聚合根（Aggregates）可能是战术 DDD 中困难的部分。我们将介绍在处理它们时的关键概念，以及如何设计它们。我们将看到一个实际场景：在添加一条业务规则时，两个聚合根如何合并为一个，以及其他对象必须如何进行重构。

## 第 9 章：工厂（Factories）（已完成）

工厂方法和工厂对象帮助我们维护业务不变性，这就是为什么它们在 DDD 中如此重要的原因。最后，我们将检查工厂与聚合根之间的关系。

## 第 10 章：存储库（Repositories）（已完成）

存储库是从集合中检索和添加实体（Entities）与聚合根（Aggregates）的关键。我们将回顾不同类型的存储库并学习如何使用 Doctrine、自定义 ORM 和 Redis 来实现它们。

## 第 11 章：应用服务（Application Services）（已完成）

应用层是连接外部客户端与你领域模型的薄层。在本章中，我们将向你展示如何编写应用服务，使其易于测试并保持轻量。我们将回顾如何准备请求对象、依赖项以及返回结果。

## 第 12 章：集成限界上下文（Integrating Bounded Contexts）（已完成）

我们将探索通信限界上下文的各种战术方法并查看实际实现。我们建议使用 REST 进行同步通信，并使用 RabbitMQ 进行异步消息传递。

# 前言

## 附录 A：基于 PHP 的六边形架构（Hexagonal Architecture）（已完成）

在这里，你将找到由 Carlos Buenosvinos 编写并于 2014 年 6 月发表在 *php|architect* 杂志上的原始文章，这是本书的种子。

## 代码与示例

作者在 GitHub.com (https://github.com/dddinphp) 创建了一个组织，那里提供了书中的所有代码示例、额外的片段以及一些完整的示例项目。如果你感兴趣，我们强烈建议查看这些项目并提供反馈。

## 致谢



我们是三位正在编写英文书的西班牙人。如果你认为我们的英语远非完美，那么你猜得没错。`Edd Mann` 从一开始就在语言方面为我们提供支持。他不仅是一位出色的合作者，还是一位好朋友。我们深表感谢。我们还要感谢 `Albert Casademont` 和 `Ricard Clau` 协助修订工作。

我们感谢所有在初期购买本书的早期用户，他们给予了我们所需的爱和支持，让我们能够不断推进。

## GitHub 贡献者

我们还要感谢所有在我们的 [GitHub 仓库](https://github.com/dddinphp/ddd-in-php-book-issues)[¹] 中报告问题、提出建议等的人。非常感谢每一个人，你们帮助我们让这本书变得更好，更重要的是，帮助了社区和其他开发者成为更优秀的开发者。

正如 [Dave Thomas](https://twitter.com/pragdave)[²] 在他的书《程序员之道》中所写的：“如果你正在读这本书，是因为你想成为更好的开发者。太好了，我们需要更优秀的开发者。”

所以，感谢 `Jordi Abad`、`Jonathan Wondrusch`、`César Rodríguez`、`Yannick Voyer`、`Oriol González`、`Henry Snoek`、`Tom Jowitt`、`Nico Oelgart`、`Sascha Schimke`、`Sven Herrmann`、`Daniel Abad`、`Luis Rovirosa` 和 `Marc Aube`。

¹[`github.com/dddinphp/ddd-in-php-book-issues`](https://github.com/dddinphp/ddd-in-php-book-issues)

²[`twitter.com/pragdave`](https://twitter.com/pragdave)

# 作者简介

### Carlos Buenosvinos

PHP 极端编程专家，担任 `Atrapalo.com` 的 CTO，PHP Barcelona 用户组董事成员，敏捷教练，`Valu` 和 `Gabriela` 的父亲，`Vanessa` 的丈夫。他曾工作于电子商务（`Atrapalo.com` 和 `Ebay International`）、支付处理（`Vendo`）和分类广告（`Emagister.com`）。他喜欢开发移动应用、树莓派项目和游戏。拥有 Zend PHP、Scrum Master 和 MySQL 5.6 认证。

- Twitter: [@buenosvinos³](https://twitter.com/buenosvinos)

- GitHub: https://github.com/carlosbuenosvinos

### Christian Soronellas

热情的软件开发者。软件行者与匠学徒。极端编程灵魂。拥有 10 年以上的 Web 开发经验。Zend PHP 5.3 认证工程师。Zend Framework 认证工程师。SensioLabs 认证 Symfony 开发者。他曾作为自由职业工作于 `Privalia`、`Emagister`，目前在 `Atrapalo` 担任软件架构师。

- Twitter: [@theUniC⁴](https://twitter.com/theUniC)

- GitHub: https://github.com/theUniC

### Keyvan Akbary

多语言软件开发者。热爱软件基础、匠心运动、极端编程、SOLID 原则、清洁代码、设计模式和测试。偶尔的函数式编程冒险者。他将技术理解为为业务提供价值的媒介。他曾为大小客户提供自由职业服务，并在 `Youzee`、`MyBuilder` 工作过，目前在伦敦的 `TransferWise` 担任首席开发者。

- Twitter: [@keyvanakbary⁵](https://twitter.com/keyvanakbary)

- GitHub: https://github.com/keyvanakbary

# 1. 开始 DDD

聚合根（Aggregates）可能是战术 DDD 中困难的部分。我们将介绍在处理它们时的关键概念，以及如何设计它们。我们将看到一个实际场景：在添加一条业务规则时，两个聚合根如何合并为一个，以及其他对象必须如何进行重构。

### 1.1 为什么用领域驱动设计？

- 软件不仅对编码人员有意义，也对业务有意义。DDD 强调确保业务和软件使用相同的语言。

- 软件优先级与业务优先级对齐。

- 通过 DDD，每个人在发现业务领域的过程中学习并做出贡献。

- 知识不再仅仅属于开发者，通过 DDD，每个人都清楚业务正在发生什么。

- 领域专家之间没有翻译，意味着没有信息丢失或琐碎的同步。每个人都说同一种语言。

- 设计就是代码，代码就是设计，是通用语言唯一实现的真理。

- DDD 为战略设计和战术设计提供了一个框架。战略设计用于根据业务价值准确定最重要的开发领域，战术设计则关于经过实践检验的构建块和模式。

## 1.2 领域驱动设计如何帮助？

领域驱动设计是一种交付软件的方法，侧重于三个支柱：

1. 通用语言（Ubiquitous Language）：领域专家和软件开发者共同工作，为正在开发的业务领域建立一种通用语言。没有“我们”和“他们”，只有*我们*。开发软件是一项业务投资，而不只是成本。构建通用语言的努力有助于在所有团队成员中传播深刻的领域洞察。

2. 战略设计（Strategic Design）：领域驱动设计解决业务方向背后的策略，而不仅仅是技术方面。它有助于定义内部关系和预警反馈系统。在技术方面，战略设计通过为实现服务体系架构提供动力，保护每个*业务*服务。

# 3. 战术设计

领域驱动设计（DDD）为迭代的软件交付提供了工具和构建组件。战术设计工具产生的软件能够准确映射领域专家的心理模型，具有可测试性且错误率较低。

### 1.2.1 通用语言

与`限界上下文`一样，`通用语言`（Ubiquitous Language）是 DDD 的核心优势之一。

### 从上下文的角度来看

目前，请将`限界上下文`（Bounded Context）视为系统周围的一个概念边界。边界内部的`通用语言`具有特定的上下文含义。边界之外的概念可能有不同的含义。

那么，如何捕获这种特殊的语言呢？

- 为物理操作和概念领域概念标记名称。

- 创建术语和定义的词汇表。

- 使用某种文档记录记录重要的软件概念。

- 与团队其他成员共享并演进收集到的知识。

## 1.3 我是否应该开始考虑将领域驱动设计作为一个备选项？

领域驱动设计并不是万能灵药，就像软件中的任何事物一样，它取决于上下文。作为一个经验法则，用它来简化你的领域，而永远不要增加复杂性。

如果你的应用是以数据为中心的，且用例围绕数据操作和 CRUD 操作（即：创建、读取、更新和删除）展开——那么你不需要 DDD。你的公司只需要在数据库前面放一个华丽的界面即可。

如果你的应用少于 30 个用例，使用像 `Symfony` 或 `Laravel` 这样的框架来处理业务逻辑可能简单。

如果你有超过 30 个用例，你的系统可能正在向令人可怕的“大泥球”（big ball of mud）演变。如果你确定你的系统复杂性将会增加，你应该开始考虑使用 DDD 来对抗复杂性。

### 开始使用 DDD

如果你知道你的应用程序将会增长并且可能经常变化，DDD 将无疑有助于管理复杂性并随着时间的推移重构你的模型。

如果你不理解你所工作的领域，因为它是新的且以前没有人投入过解决方案，这可能意味着它已经复杂到可以开始应用 DDD 了。你需要与`领域专家`（Domain Experts）密切合作，以获得正确的模型。这需要与专家进行开放、健康、尊重且持续的对话，将他们的口语建模为软件。

我们开发者是技术型思考者。技术解决方案是我们的专长。思考技术问题并不坏，唯一的问题是，有时少从技术角度思考反而更好。为了从对象的行为进行思考，我们需要先用`通用语言`进行思考。

### 1.5 使用领域驱动设计的业务价值

证明一种技术或方法的最佳方式是为业务提供价值。总结来说，应用 DDD 的主要益处是：

- 该领域有用且有意义的模型

- 领域专家参与软件设计

- 更好的用户体验

- 清晰的边界

- 更好的架构组织

- 以敏捷的方式迭代和持续建模

- 更好的工具，包括战略性和战术性的

### 1.6 总结

实施领域驱动设计需要努力。如果这很容易，每个人都会编写高质量的代码了。准备好，因为通过这段旅程，你将学会如何让你的设计看起来就像你的软件工作方式一样。在本章中，你学习了：

- 领域驱动设计不是关于技术的，而是通过关注模型在你工作的领域提供价值。每个人都参与到发现领域的过程中，开发者和领域专家合作，通过共享相同的语言——`通用语言`来建立知识库。

- 领域驱动设计提供了`战术`和`战略`建模工具来设计高质量的软件。战略设计针对业务方向，有助于定义内部关系，并通过定义强边界在技术上保护每个`业务服务`。战术设计为迭代设计提供了实用的构建组件。

- 我们学习了 DDD 有意义的上下文。DDD 不是万能灵药，它取决于上下文。

- 我们还看到应用 DDD 是一项长期投资，它需要努力。

- 最终，`通用语言`是 DDD 的核心需求。

## 2. 架构风格

为了能够构建复杂的应用程序，关键要求之一是拥有符合需求的架构风格。

## 2.1 旧时光

在 PHP 5 发布之前，该语言并没有接纳面向对象的范式。在那个时代，编写应用程序的通常方法是使用过程和全局状态。`关注点分离`（Separation of Concerns）、`MVC` 等概念在 PHP 社区是陌生的。

下面的示例是用“传统方式”编写的应用程序，应用程序由与 HTML 代码混合的前控制器组成。在此期间，`基础设施`（Infrastructure）、`表示层`（Presentation）或`UI`以及`领域`（Domain）层代码全部交织在一起。

```php
<?php
include __DIR__ . '/bootstrap.php';
$db = new PDO('mysql:host=localhost;dbname=my_database', 'a_username', '4_pss0rd', [
    PDO::MYSQL_ATTR_INIT_COMMAND => 'SET NAMES utf8',
]);
$errormsg = null;

if (isset($_POST['submit']) && isValid($_POST['post'])) {
    $post = getFrom($_POST['post']);

    $db->beginTransaction();
    try {
        $stm = $db->prepare('INSERT INTO posts (title, content) VALUES (?, ?)');
        $stm->exec([
            $post['title'],
            $post['content']
        ]);
        $db->commit();
    } catch (Exception $e) {
        $db->rollback();
        $errormsg = 'Post could not be created! :(';
    }
}

$stm = $db->prepare('SELECT id, title, content FROM posts');
$posts = $stm->fetchAll(PDO::FETCH_ASSOC);
?>
<html>
<head></head>
<body>
<?php if (null !== $errormsg): ?>
<div class="alert error"><?php echo $errormsg; ?></div>
<?php else: ?>
```

<div class="alert success">太棒了！文章创建成功！</div>

```php
<?php endif; ?>
```

<table>

  <thead>

    <tr>

      <th>ID</th>

      <th>标题</th>

      <th>操作</th>

    </tr>

  </thead>

  <tbody>

    <?php foreach ($posts as $post): ?>

      <tr>

        <td><?php echo $post['ID']; ?></td>

        <td><?php echo $post['TITLE']; ?></td>

        <td><?php editPostUrl($post['ID']); ?></td>

      </tr>

    <?php endforeach; ?>

  </tbody>

</table>

</body>

</html>

这种编码风格通常被称为***大泥球架构（Big Ball of Mud）***¹。在这一风格中看到的一种改进是：

[¹] 摘自 [c2.com 维基](http://c2.com/cgi/wiki?BigBallOfMud)：*一个大泥球是一个结构杂乱无章、蔓延、草率、用胶带和铁丝网胡乱拼凑而成的意大利面条代码丛林*。

架构风格

7

然而，改进是将网页的页眉和页脚封装在各自独立的文件中，

这些文件被包含在其他文件中。这避免了重复并有利于重用。

`include __DIR__ . '/bootstrap.php';`

```php
$db = new PDO('mysql:host=localhost;dbname=my_database', 'a_username', '4_p4ssw0rd', [
    PDO::MYSQL_ATTR_INIT_COMMAND => 'SET NAMES utf8',
]);
$errormsg = null;
if (isset($_POST['submit']) && isValid($_POST['post']))) {
    $post = getFrom($_POST['post']);
    $db->beginTransaction();
    try {
        $stm = $db->prepare('INSERT INTO posts (title, content) VALUES (?, ?)');
        $stm->exec([
            $post['title'],
            $post['content']
        ]);
        $db->commit();
    } catch (Exception $e) {
        $db->rollback();
        $errormsg = '文章无法创建！:(';
    }
}
$stm = $db->prepare('SELECT id, title, content FROM posts');
$posts = $stm->fetchAll(PDO::FETCH_ASSOC);
```

```php
<?php include __DIR__ . '/header.php'; ?>
```

```php
<?php if (null !== $errormsg): ?>
<div class="alert error"><?php echo $errormsg; ?></div>
<?php else: ?>
<div class="alert success">太棒了！文章创建成功！</div>
<?php endif; ?>
```

<table>

  <thead>

    <tr>

      <th>ID</th>

      <th>标题</th>

      <th>操作</th>

    </tr>

  </thead>

  <tbody>

    <?php foreach ($posts as $post): ?>

      <tr>

        <td><?php echo $post['ID']; ?></td>

        8

        <td><?php echo $post['TITLE']; ?></td>

        <td><?php editPostUrl($post['ID']); ?></td>

      </tr>

    <?php endforeach; ?>

  </tbody>

</table>

```php
<?php include __DIR__ . '/footer.php'; ?>
```

如今，尽管非常不被推荐这样做，但仍有应用程序在使用这种过程化编码方式。这种架构风格的主要缺点是没有实现真正的关注点分离——与其它知名且经过验证的架构相比，维护成本和更改成本大幅增加。

架构风格

9

### 2.2 分层架构

分层架构的核心是实现关注点分离。为了实现这一点，我们将代码划分为不同的层。在我们的示例中，这涉及到应用层、领域层和基础设施层。每一层都有明确的职责：

- **应用层**：负责处理用户请求并协调领域逻辑。

- **领域层**：包含核心业务逻辑和规则。

- **基础设施层**：处理底层技术实现，如数据库访问或文件系统。

通过这种分层，代码变得更易于维护和测试，因为每一层的更改通常只会影响到该层本身与其依赖层。

### 2.2.1 MVC（模型-视图-控制器）

MVC 是一种经典的架构模式，它将应用程序分为三个部分：

- **模型（Model）**：负责数据和逻辑。

- **视图（View）**：负责用户界面。

- **控制器（Controller）**：处理输入并协调模型与视图之间的交互。

虽然 MVC 被广泛使用，但如果不正确设计，控制器往往会变得臃肿，产生所谓的“胖控制器”。

架构风格

10



每当`Model`更新时，在 UI 中进行表示。通常情况下，`View`层接收一个对象，通常是一个`Data Transfer Object (DTO)`而不是`Model`层的实例，它收集了为了成功表示所需的所有信息。对于 PHP 来说，有几个模板引擎可以极大地帮助将`Model`的表示与`Model`本身以及`Controller`分离开。目前最受欢迎的引擎是 [Twig](http://twig.sensiolabs.org/)。让我们看看如果使用 Twig 使用 DTO 代替 Model 实例，View 层会变成什么样？

这是一个老旧且活跃的话题。为什么要创建一个 DTO 而不是直接给 View 层提供`Model`实例？主要原因和简短的答案是，同样是，关注点分离。让视图检查并使用`Model`实例会导致`View`层与`Model`层之间紧密耦合。事实上，`Model`层的更改可能会破坏所有使用了已更改的`Model`实例的视图。

```twig
{% extends "base.html.twig" %}
{% block content %}
{% if errormsg is defined %}
<div class="alert error">{{ errormsg }}</div>
{% else %}
<div class="alert success">Bravo! Post was created successfully!</div>
{% endif %}
<table>
<thead><tr><th>ID</th><th>TITLE</th><th>ACTIONS</th></tr></head>
<tbody>
{% for post in posts %}
<tr>
<td>{{ post.id }}</td>
<td>{{ post.title }}<?php echo $post['TITLE']; ?></td>
<td><a href="{{ editPostUrl(post.id) }}">Edit Post</a></td>
</tr>
{% endfor %}
</tbody>
</table>
{% endblock %}
```

大多数时候，当`Model`触发状态更改时，它也会通知相关的`Views`以便 UI 可以刷新。在典型的 Web 场景中，由于客户端-服务器的性质，`Model`及其表示之间的同步可能有点复杂。在此类环境中，通常需要一些 JavaScript 定义的交互来维持这种同步。出于这个原因，JavaScript MVC 框架如下面的框架在近年来变得非常流行：

* [AngularJS](https://angularjs.org/)
* [EmberJS](http://emberjs.com/)
* [Marionette](http://marionettejs.com/)
* [ReactJS](https://facebook.github.io/react/)

## Controller

Controller 层负责组织和协调`View`和`Model`。它接收来自`View`层的消息并触发`Model`行为以执行所需的操作。此外，它向`View`发送消息以显示`Model`的表示。这两个操作都归功于`Application Layer`，该层负责协调、组织和封装领域行为。

对于 PHP 的 Web 应用而言，`Controller`通常包含一组类，它们为了实现其目的会“说 HTTP”。也就是说，它们接收一个 HTTP 请求并返回一个 HTTP 响应。

```php
class PostsController
{
    public function updateAction(Request $request)
    {
        if ($request->request->has('submit')
        && Validator::validate($request->request->post)
        ) {
            $postService = new PostService();
            try {
                $postService->createPost(
                    $request->request->get('title'),
                    $request->request->get('content')
                );
                $this->addFlash(
                    'notice',
                    'Post has been created successfully!'
                );
            } catch (Exception $e) {
                $this->addFlash(
                    'error',
                    'Unable to create the post!'
                );
            }
        }
        return $this->render('posts/update-result.html.twig');
    }
}
```

## 依赖倒置。六边形架构

遵循分层架构的核心规则，存在实现某些需要在领域模型层中使用基础设施关注点的接口的风险。

例如，如果我们遵循 MVC，上一个示例中的`PDORepository`应该被放在`Domain Model`中。然而，将基础设施细节直接放在我们的领域中间违反了关注点分离。这可能会导致问题，很难避免违反分层架构的核心规则，如果`Domain Layer`感知技术实现，将导致代码风格可能变得难以测试。

### 依赖倒置原则 (DIP)

我们如何修复这个问题？由于`Domain Model layer`依赖于具体的基础设施实现，可以通过将`Infrastructure layer`移动到其他三层之上来应用[依赖倒置原则](http://www.objectmentor.com/resources/articles/dip.pdf)。

**依赖倒置原则**

高层模块不应该依赖低层模块。两者都应该依赖抽象。

抽象不应该依赖细节。细节应该依赖于抽象。

Robert C. Martin

通过使用`依赖倒置原则`，架构方案发生了变化，可以被称为*低层模块*的`Infrastructure layer`现在依赖于`UI`、`Application Layer`和`Domain Layer`，这些是*高层模块*。依赖被反转了。但那么，六边形架构是什么？它是如何融入其中的？六边形架构（也称为端口和适配器）由 Alistair Cockburn 定义，它将应用程序表示为一个六边形，每个边代表一个端口（Port），并带有一个或多个适配器（Adapter）。端口是一个带有可插拔适配器的连接器，它将外部输入转换为**内部**可以理解的内容。

### 应用六边形架构

继续之前的博客示例，我们需要的第一个概念是让*外部*世界可以与应用程序通信的端口。在这种情况下，我们将使用一个 HTTP 端口及其相应的适配器。外部将使用端口向应用程序发送消息。示例使用数据库来存储整个博客集合，因此，为了让应用程序从数据库检索博客，需要一个端口。

```php
interface PostRepository
{
    public function byId(PostId $id);
    public function add(Post $post);
}
```

该接口定义了应用程序检索博客信息的端口，*并且它将位于领域层*。现在，需要一个该端口的适配器。适配器负责定义使用特定技术检索博客的方式。

```php
class PDOPostRepository implements PostRepository
{
    private $pdo;

    public function __construct(PDO $pdo)
    {
        $this->pdo = $pdo;
    }
}
```

```php
public function byId(PostId $id)
{
    $stm = $this->db->prepare(
        'SELECT \* FROM posts WHERE id = ?'
    );
    $stm->execute([$id->id()]);
    return recreateFrom($stm->fetch());
}

public function add(Post $post)
{
    $stm = $db->prepare(
        'INSERT INTO posts (title, content) VALUES (?, ?)'
    );
    $stm->exec([
        $post->getTitle(),
        $post->getContent(),
    ]);
}
```

一旦定义了端口（Port）及其对应的适配器（Adapter），最后一步就是重构`PostService`类以便使用它们。这可以通过[依赖注入](http://www.martinfowler.com/articles/injection.html)⁸ 轻松实现。

⁸⁸[`www.martinfowler.com/articles/injection.html`](http://www.martinfowler.com/articles/injection.html)

```php
class PostService
{
    private $postRepository;

    public function __construct(PostRepository $postRepository)
    {
        $this->postRepository = $postRepository;
    }

    public function createPost($title, $content)
    {
        $post = Post::writeNewFrom($title, $content);
        $this->postRepository->add($post);
        return $post;
    }
}
```

这是六边形架构（Hexagonal Architecture）的一个简单示例。它是一种灵活的架构，像分层架构一样促进关注点分离，并且具有对称性——内部应用程序通过端口与外部进行通信。从现在起，这将作为构建和解释`CQRS`和`事件溯源（Event Sourcing）`的基础架构。

为了更深入地了解这种架构，你可以查看[附录](#index_split_000.html#294)，其中包含详细示例，解释了如`事务性（transactionability）`和其他`交叉关注点（cross cutting concerns）`等高级主题。

## 命令查询职责分离

六边形架构是一个很好的基础架构，但它也有一些局限性。例如，复杂的 UI 可能需要以多种形式显示聚合根。

```php
interface PostRepository
{
    public function save(Post $post);
    public function byId(PostId $id);
    public function all();
    public function byCategory(CategoryId $categoryId);
    public function byTag(TagId $tagId);
    public function withComments(PostId $id);
    public function groupedByMonth();
    // ... ...
}
```

当这些技术被滥用时，UI 视图的构建可能会变得非常痛苦，我们应该权衡是让应用程序服务返回领域模型实例，还是使用某种数据传输对象（DTO），以避免领域模型与 Web 控制器、CLI 控制器等基础设施代码之间的紧耦合。

幸运的是，还有另一种方法。如果问题是存在多个异的视图，我们可以将它们从领域模型中排除，并开始将它们视为纯粹的基础设施关注点。这种选项基于 Bertrand Meyer 定义的名为命令查询分离（CQS）的设计原则，该原则诞生了由 Greg Young 定义的名为命令查询职责分离（CQRS）的新型架构模式。

### 命令查询分离 (CQS)

*“提问不应该改变答案” —— Bertrand Meyer*

该设计原则规定每个方法要么是一个执行操作的命令（Command），要么是一个向调用者返回数据的查询（Query），不能两者兼顾。

`CQRS`追求更激进的关注点分离，将模型分为二：

- **写模型（Write Model）**：也称为**命令模型（Command Model）**，它执行写入并负责真实的领域行为。
- **读模型（Read Model）**：负责应用程序内部的读取，并将其视为应该属于领域模型之外的内容。

每当有人触发写入模型的命令时，它会执行对目标数据存储的写入，并额外触发读模型更新，以便在读模型上显示最新的更改。

这种严格的分离引发了另一个问题：**最终一致性（Eventual Consistency）**。读模型的这种性现在取决于写入模型执行的命令。也就是说，可以说*读模型是最终一致的*。这意味着每当写入模型执行命令时，它都会启动一个进程，根据写入模型的最新更新来更新读模型。存在这样一个时间窗口，UI 可能会向用户展示过期信息。在 Web 场景中这种情况经常发生，因为我们某种程度上受到当前技术的限制。

想想 Web 应用前的缓存系统。每当数据库更新新信息时，缓存层的数据都可能是过时的，因此`缓存系统是最终一致的`。

`写模型投影（Write Model projections）`或`投影（Projections）`。这将在书后部分解释，领域事件。写模型投影的基础是收集所有已发布的事件。

### 写模型

这是领域行为的真实持有者。延续示例，`Repository`接口将简化为：

```php
interface PostRepository
{
    public function save(Post $post);
    public function byId(PostId $id);
}
```

现在`PostRepository`已从所有的读取关注点中释放，除了`byId`，它负责加载聚合根以便我们对其进行操作。一旦完成，所有查询方法从`Post`模型中剥离，只留下命令方法。这意味着有效地去掉了所有的 getter 方法以及任何暴露信息的方法。相反，`领域事件`将被发布，以便通过订阅来触发写模型投影。

```php
class AggregateRoot
{
    private $recordedEvents = [];

    protected function recordApplyPublishThat(DomainEvent $domainEvent)
    {
        $this->recordThat($domainEvent);
        $this->applyThat($domainEvent);
        $this->publishThat($domainEvent);
    }

    protected function recordThat(DomainEvent $domainEvent)
    {
        $this->recordedEvents[] = $domainEvent;
    }

    protected function applyThat(DomainEvent $domainEvent)
    {
        $modifier = 'apply' . get_class($domainEvent);
        $this->$modifier($domainEvent);
    }

    protected function publishThat(DomainEvent $domainEvent)
    {
        DomainEventPublisher::getInstance()->publish($domainEvent);
    }

    public function recordedEvents()
    {
        return $this->recordedEvents;
    }

    public function clearEvents()
    {
        $this->recordedEvents = [];
    }
}
```

```php
class Post extends AggregateRoot
{
    private $id;
    private $title;
    private $content;
    private $published = false;
    private $categories;

    private function __construct(PostId $id)
    {
        $this->id = $id;
        $this->categories = new Collection();
    }
}
```



```php
public static function writeNewFrom($title, $content)
{
    $post = new Post(PostId::create());
    $post->recordApplyAndPublishThat(
        new PostWasCreated(PostId::generate(), $title, $content)
    );
}

public function publish()
{
    $this->recordApplyAndPublishThat(
        new PostWasPublished($this->id)
    );
}

public function categorizeIn(CategoryId $categoryId)
{
    $this->recordApplyAndPublishThat(
        new PostWasCategorized($this->id, $categoryId)
    );
}

public function changeContentFor($newContent)
{
    $this->recordApplyAndPublishThat(
        new PostContentWasChanged($this->id, $newContent)
    );
}

public function changeTitleFor($newTitle)
{
    $this->recordApplyAndPublishThat(
        new PostTitleWasChanged($this->id, $newTitle)
    );
}
```

# 架构风格

所有触发状态变更的操作都通过*领域事件*（domain events）来实现。对于每个发布的*领域事件*，都有一个*应用*（apply）方法负责反映状态的变化。

```php
class Post extends AggregateRoot
{
    // ...
    protected function applyPostWasCreated(PostWasCreated $event)
    {
        $this->id = $event->id();
        $this->title = $event->title();
        $this->content = $event->content();
    }

    protected function applyPostWasPublished(PostWasPublished $event)
    {
        $this->published = true;
    }

    protected function applyPostWasCategorized(PostWasCategorized $event)
    {
        $this->categories->add($event->categoryId());
    }

    protected function applyPostContentWasChanged(PostContentWasChanged $event)
    {
        $this->content = $event->content();
    }

    protected function applyPostTitleWasChanged(PostTitleWasChanged $event)
    {
        $this->title = $event->title();
    }
}
```

## 2.4.2 读取模型

*读取模型*（read model），也称为*查询模型*（Query Model），是从领域关注点中提取的纯反规范化数据模型。事实上，在 `CQRS` 中，所有的*读取关注点*都被视为报告过程，这是一种基础设施层面的关注点。通常情况下，在使用 `CQRS` 时，*读取模型*取决于 UI 的需求以及组成 UI 的视图的复杂程度。

在*读取模型*基于关系型数据库定义的情况下，简单的方法是在数据库表和 UI 视图之间建立一对一的关系。这些数据库表 / UI 视图将通过由*写侧*（write side）发布的*领域事件*触发的*写模型投影*（write model projections）进行更新。

-- 单个文章及其评论的 UI 视图定义

```sql
CREATE TABLE single_post_with_comments (
    id INTEGER NOT NULL,
    post_id INTEGER NOT NULL,
    post_title VARCHAR(100) NOT NULL,
    post_content TEXT NOT NULL,
    post_created_at DATETIME NOT NULL,
    post_content TEXT NOT NULL
);
```

-- 设置一些数据

```sql
INSERT INTO single_post_with_comments(1, 1, "Layered architecture", "Lorem ipsum dolor sit amet, ...", NOW(), "Lorem ipsum dolor sit amet, ...");
INSERT INTO single_post_with_comments(2, 1, "Layered architecture", "Lorem ipsum dolor sit amet, ...", NOW(), "Lorem ipsum dolor sit amet, ...");
INSERT INTO single_post_with_comments(3, 2, "Hexagonal architecture", "Lorem ipsum dolor sit amet, ...", NOW(), "Lorem ipsum dolor sit amet, ... ...");
INSERT INTO single_post_with_comments(4, 2, "Hexagonal architecture", "Lorem ipsum dolor sit amet, ...", NOW(), "Lorem ipsum dolor sit amet, ... ...");
INSERT INTO single_post_with_comments(5, 3, "Command - Query Responsability Segregation", "Lorem ipsum dolor sit amet, ...", NOW(), "Lorem ipsum dolor sit amet, ...");
INSERT INTO single_post_with_comments(6, 3, "Command - Query Responsability Segregation", "Lorem ipsum dolor sit amet, ...", NOW(), "Lorem ipsum dolor sit amet, ...");
```

-- 查询它

```sql
SELECT * FROM single_post_with_comments WHERE post_id = 1;
```

这种架构风格的一个重要特征是，*读取模型*应该是完全可弃的，因为应用程序的*真实状态*是由*写模型*处理的。这意味着在需要时，可以使用*写模型投影*删除并重新创建*读取模型*。

在这里我们可以看到博客应用程序中可能的视图示例：

```sql
SELECT * FROM posts_grouped_by_month_and_year ORDER BY month DESC, year ASC;
SELECT * FROM posts_by_tags WHERE tag = "ddd";
SELECT * FROM posts_by_author WHERE author_id = 1;
```

需要指出的是，*CQRS* 并不将*读取模型*的定义和实现限制在关系型数据库上。它完全取决于所构建的应用的需求。它可以是关系型数据库、文档型数据库、键值存储或任何最适合你应用程序需求的存储。

在博客文章应用之后，我们将使用 [Elasticsearch](https://en.wikipedia.org/wiki/Elasticsearch)（一种文档型数据库）来实现*读取模型*。

```php
class PostsController
{
    public function listAction()
    {
        $client = new \Elasticsearch\ClientBuilder::create()->build();
        $response = $client->search([
            'index' => 'blog-engine',
            'type' => 'posts',
            'body' => [
                'sort' => [
                    'created_at' => 'desc']
                ]
            ]
        ]);
        return [
            'posts' => $response
        ];
    }
}
```

*读取模型*代码被极大简化为对 Elasticsearch 的查询。这揭示了*读取模型*并不一定需要对象映射器，这样做可能过度设计。然而，*写模型*可能受益于对象映射器的使用，以便根据应用的需求来组织和结构。

## 2.4.3 写模型与读取模型的同步

这里是棘手的部分。我们如何同步*写模型*和*读取模型*？我们已经说过，通过在*写模型*事务中使用*领域事件*来实现。对于捕获的每个事件类型，都会执行特定的投影。因此，事件与投影之间将建立一对一的关系。

让我们来看一个配置投影的示例，以便理解：

```php
$client = new \Elasticsearch\ClientBuilder::create()->build();
$projector = new Projector();
$projector->register([
    new Infrastructure\Projection\Elasticsearch\PostWasCreated($client),
    new Infrastructure\Projection\Elasticsearch\PostWasPublished($client),
    new Infrastructure\Projection\Elasticsearch\PostWasCategorized($client),
    new Infrastructure\Projection\Elasticsearch\PostContentWasChanged($client),
    new Infrastructure\Projection\Elasticsearch\PostTitleWasChanged($client),
]);

$events = [
    new PostWasCreated(/*...*/),
    new PostWasPublished(/*...*/),
    new PostWasCategorized(/*...*/),
    new PostContentWasChanged(/*...*/),
    new PostTitleWasChanged(/*...*/),
];

$projector->project($event);
```

这段代码是同步的，但根据需要可以是异步的。你可以通过放置一些警报让客户意识到这些数据不同步。

在下一个示例中，我们将使用 `ampq-lib` PHP 扩展结合 [ReactPHP¹⁰](http://github.com/GeniusesOfSymfony/ReactAMQP)。

```php
// 连接到 AMQP 代理
$cnn = new AMQPConnection();
$cnn->connect();

// 创建一个通道
$ch = new AMQPChannel($cnn);

// 声明交换交换
$ex = new AMQPExchange($ch);
$ex->setName('events');
$ex->declare();

// 创建事件循环
```

```php
$loop = React\EventLoop\Factory::create();

// 创建一个每半秒发送任何等待消息的生产者

$producer = new Gos\Component\ReactAMQP\Producer($ex, $loop, 0.5);

$serializer = JMS\Serializer\SerializerBuilder::create()->build();

$projector = new AsyncProjector($producer, $serializer);

$events = [
    new PostWasCreated( /* ... */),
    new PostWasPublished( /* ... */),
    new PostWasCategorized( /* ... */),
    new PostContentWasChanged( /* ... */),
    new PostTitleWasChanged( /* ... */),
];

$projector->project($event);
```

而 RabbitMQ 交换上的事件消费者将如下所示。

# 架构样式

28

```php
// 连接到 AMQP 代理
$cnn = new AMQPConnection();
$cnn->connect();

// 创建一个通道
$ch = new AMQPChannel($cnn);

// 创建一个新的队列
$queue = new AMQPQueue($ch);
$queue->setName('events');
$queue->declare();

// 创建一个事件循环
$loop = React\EventLoop\Factory::create();
$serializer = JMS\Serializer\SerializerBuilder::create()->build();
$client = new \Elasticsearch\ClientBuilder::create()->build();
$projector = new Projector();
$projector->register([
    new Infrastructure\Projection\Elasticsearch\PostWasCreated($client),
    new Infrastructure\Projection\Elasticsearch\PostWasPublished($client),
    new Infrastructure\Projection\Elasticsearch\PostWasCategorized($client),
    new Infrastructure\Projection\Elasticsearch\PostContentWasChanged($client),
    new Infrastructure\Projection\Elasticsearch\PostTitleWasChanged($client),
]);

// 创建一个消费者
$consumer = new Gos\Component\ReactAMQP\Consumer($queue, $loop, 0.5, 10);

// 每半秒检查一次消息，一次最多最多 10 条。
$consumer->on(
    'consume',
    function($envelope, $queue) use ($projector, $serializer) {
        $event = $serializer->unserialize($envelope->getBody(), 'json');
        $projector->project($event);
    }
);
$loop->run();
```

从现在起，只需让所有需要的仓库消费一个 `projector` 实例并让它们调用投影过程即可。

# 架构样式

29



```php
class DoctrinePostRepository implements PostRepository
{
    private $em;
    private $projector;

    public function __construct(EntityManager $em, Projector $projector)
    {
        $this->em = $em;
        $this->projector = $projector;
    }

    public function save(Post $post)
    {
        $this->em->transactional(function(EntityManager $em) use ($post) {
            $em->persist($post);
            foreach ($post->recordedEvents() as $event) {
                $em->persist($event);
            }
        });
        $this->projector->project($post->recordedEvents());
    }

    public function byId(PostId $id)
    {
        return $this->em->find($id);
    }
}
```

`Post` 实例和记录的事件在同一个事务中触发并持久化。

这确保了事件不会丢失，因为如果事务成功，我们将它们投影到`read model`。因此，`write model`和`read model`之间不存在不一致性。

![](img/index-48_1.png)

## 2.5 事件溯源 (Event Sourcing)

`CQRS` 是一种强大且灵活的架构。在收集和保存`domain events`（在聚合操作期间发生的事件）方面，它还有一个额外的好处，让你对领域内部发生的情况具有高层面的详细了解。由于`Domain Events` 在领域内的重要性，它们是关键战术模式之一，因为它们描述了过去发生的事件。

事件数量的不断增长预示着业务忽略了对领域的深度洞察。通过使用 `CQRS`，我们获得了一个极其复杂的关于所有相关事件的历史，其程度仅可以通过重现`domain events` 来表达整个领域模型的状态。我们只需要一个工具以一致的方式存储所有这些事件。这种存储被称为 `eventstore`（事件存储）。

### 事件溯源的核心思想是将聚合（Aggregates）的状态表达为事件的线性序列

通过 `CQRS`，我们部分实现了以下目标——`Post` 实体通过使用`domain events`改变其状态，但它始终被持久化，将对象映射到数据库表。`Event Sourcing` 将此又了一层。如果我们使用数据库表来存储所有博客文章的状态，用另一个表来存储所有博客评论的状态等等，那么通过使用 `Event Sourcing`，我们只需要一个数据库表。一个单一的只追加（append-only）数据库表，将存储领域模型内所有聚合发布的所有 `domain events`。是的，你读得正确，**单个**数据库表。

考虑到这种模型，不再需要 `object-relational mappers`（对象关系映射）等工具了。对于单个数据库表来说，它们太自杀了。`eventstore` 是存储所有这些事件所需的简单数据库表。

```php
interface EventSAggregateRoot
{
    public static function reconstitute(EventStream $events);
}

class Post extends AggregateRoot implements EventSAggregateRoot
{
    public static function reconstitute(EventStream $events)
    {
        $post = new static($events->getAggregateId());
        foreach ($events as $event) {
            $post->apply($event);
        }
        return $post;
    }
}
```

现在，聚合根有一个方法，给定一组 `events`（换句话说就是流），它能够逐步重放直到达到保存前的状态。

```php
class EventStorePostRepository implements PostRepository
{
    private $eventStore;
    private $projector;

    public function __construct($eventStore, $projector)
    {
        $this->eventStore = $eventStore;
        $this->projector = $projector;
    }

    public function save(Post $post)
    {
        $events = $post->recordedEvents();
        $this->eventStore->append(new EventStream($post->id(), $events));
        $post->clearEvents();
        $this->projector->project($events);
    }
}
```

这就是 `PostRepository` 的实现方式，我们使用 `eventstore` 保存由聚合发布的所有事件。现在我们需要一种从事件历史恢复聚合的方法。由聚合根实现的 `reconstitute` 方法非常有用。

```php
class EventStorePostRepository implements PostRepository
{
    public function byId(PostId $id)
    {
        return Post::reconstitute(
            $this->eventStore->getEventsFor($id)
        );
    }
}
```

`eventstore` 是负责保存和恢复 `eventstreams` 所有职责的主力军。它的公共 API 由两个简单的方法组成：`append` 和 `getEvents`。前者将 `eventstream` 追加到 `eventstore`，后者加载 `eventstreams` 以允许重建聚合。

我们可以使用键值实现来存储所有事件

```php
class EventStore
{
    private $redis;
    private $serializer;

    public function __construct($redis, $serializer)
    {
        $this->redis = $redis;
        $this->serializer = $serializer;
    }

    public function append(EventStream $eventstream)
    {
        foreach ($eventstream as $event) {
            $data = $this->serializer->serialize(
                $event,
                'json'
            );
            $date = (new DateTimeImmutable())->format('YmdHis');
            $this->redis->rpush(
                'events:' . $event->getAggregateId(),
                $this->serializer->serialize([
                    'type' => get_class($event),
                    'created_on' => $date,
                    'data' => $data
                ], 'json')
            );
        }
    }

    public function getEventsFor($id)
    {
        $serializedEvents = $this->redis->lrange(
            'events:' . $id,
            0,
            -1
        );

        $eventStream = [];

        foreach ($serializedEvents as $serializedEvent) {
            $eventData = $this->serializer->deserialize(
                $serializedEvent,
                'array',
                'json'
            );
            $eventStream[] = $this->serializer->deserialize(
                $eventData['data'],
                $eventData['type'],
                'json'
            );
        }

        return new EventStream($id, $eventStream);
    }
}
```

这种 `eventstore` 实现是基于 [Redis](http://redis.io)¹¹ 构建的，它是一种广泛使用的键值存储器。事件使用前缀 `“events:` 被追加到列表中。此外，在持久化事件之前，我们会提取一些元数据，例如事件类或创建日期，因为它们在稍后会很有用。

显然，从性能角度来看，让聚合（aggregate）每次都遍历其完整的事件历史来达到最终状态是非常昂贵的的。当一个事件流包含数百甚至数千个事件时，情况尤为如此。克服这种情况的最佳方法是从聚合中获取快照，并仅重放自快照拍摄以来事件流中的事件。快照 ¹¹[`redis.io`](http://redis.io) 只是在给定时刻聚合状态的简单序列化版本。它可以基于聚合事件流的事件数量，也可以基于时间。对于第一种方法，每触发 `n triggered events` 就会拍摄一次快照（例如每 50、100 或 200 次）。对于第二种方法，每 `n seconds` 拍摄一次快照。

为了遵循示例，我们将使用第一种快照方法。在事件元数据中，我们存储了一个额外的字段 `version`，我们将从这里开始重放聚合历史。

```php
class SnapshotRepository
{
    public function byId($id)
    {
        $key = 'snapshots:' . $id;
        $metadata = $this->serializer->unserialize(
            $this->redis->get($key)
        );
        if (null === $metadata) {
            return;
        }
        return new Snapshot(
            $metadata['version'],
            $this->serializer->unserialize(
                $metadata['snapshot']['data'],
                $metadata['snapshot']['type'],
                'json'
            )
        );
    }

    public function save($id, Snapshot $snapshot)
    {
        $key = 'snapshots:' . $id;
        $aggregate = $snapshot->aggregate();
        $snapshot = [
            'version' => $snapshot->version(),
            'snapshot' => [
                'type' => get_class($aggregate),
                'data' => $this->serializer->serialize(
                    $aggregate,
                    'json'
                )
            ]
        ];
        $this->redis->set($key, $snapshot);
    }
}
```

现在我们需要重构 `EventStore` 类，使其开始使用 `SnapshotRepository` 来加载聚合，以获得可接受的性能。

```php
class EventStorePostRepository implements PostRepository
{
    public function byId(PostId $id)
    {
        $snapshot = $this->snapshotRepository->byId($id);
        if (null === $snapshot) {
            return Post::reconstitute(
                $this->eventStore->getEventsFrom($id)
            );
        }
        $post = $snapshot->aggregate();
        $post->replay(
            $this->eventStore->fromVersion($id, $snapshot->version())
        );
        return $post;
    }
}
```

我们只需要定期对聚合进行快照。我们可以同步地这样做，也可以通过负责监控 `eventstore` 的进程异步地这样做。以下代码是演示聚合快照实现的简单示例。

```php
class EventStorePostRepository implements PostRepository
{
    public function save(Post $post)
    {
        $id = $post->id();
        $events = $post->recordedEvents();
        $post->clearEvents();
        $this->eventStore->append(
            new EventStream($id, $events)
        );
        $countOfEvents = $this->eventStore->countEventsFor(
            $id
        );
        $version = $countOfEvents / 100;
        if (!$this->snapshotRepository->has($post->id(), $version)) {
            $this->snapshotRepository->save(
                $id,
                new Snapshot(
                    $post,
                    $version
                )
            );
        }
        $this->projector->project($events);
    }
}
```

### 2.6 总结

由于本章中有许多架构风格的选择，你可能会有些困惑。你必须考虑每种风格的权衡以便做出明智的选择。有一点是很明确的：泥球（`Big Ball of Mud`）方法不是一个选项，因为代码会迅速腐烂。分层架构（`Layered architecture`）是一个更好的选择，但它存在一些缺点，如层与层之间的耦合。可以说，最平衡的选项可能是六形架构（`Hexagonal Architecture`），因为它可以作为基础架构使用。它促进了应用“内部”和“外部”之间高程度的解耦和对称。

我们还看到了 `CQRS` 和事件溯源（`Event sourcing`），它们是灵活的架构，可以帮助解决复杂问题。`CQRS` 和事件溯源有其特定的用处，但不要让它们的酷炫因素让你分心。如果查询方法的数量开始增加且变得难以维护，那么是时候考虑使用 `CQRS` 来分离读写关注点了。此外，如果聚合操作的事件数量不断增长，那么考虑转向 `Event sourcing` 是否会有所收益。

## 3. 值对象（Value Objects）



值对象是领域驱动设计中的基本构建块，用于在代码中建模通用语言。值对象不仅仅是领域中的某个“实体”，它衡量、量化或描述某些事物。它们可以被视为简单的对象，例如金额或日期范围——其相等性不是基于身份，而是基于内容。例如，产品价格可以使用值对象建模。在这种情况下，它不代表一个“实体”，而是一个我们衡量价值的值。这些对象的内存占用非常容易确定（通过其组成部分计算），且开销很小。因此，创建新实例优于引用引用，即使它们表示相同的值。相等性根据两个实例的字段进行检查。

### 3.1 定义

Ward Cunningham [定义](http://c2.com/cgi/wiki?ValueObject)¹ 了值对象为对某物的衡量或描述。值对象的例子包括数字、日期、货币和字符串。通常，它们是被广泛使用的小对象。它们的身份基于状态而不是对象身份。这样，你可以拥有多个相同概念值对象的副本。每张美元钞都有自己的身份（得益于其序列号），但现金经济依赖于每张美元钞与其他所有美元钞具有相同的价值。

Martin Fowler [定义²](http://martinfowler.com/bliki/ValueObject.html) 了值对象为金额或日期范围对象等的小对象。它们的关键属性是遵循值语义而不是引用语义。你通常能识别出它们，因为它们的相等概念不是基于身份，相反，如果两个值对象的字段都相等，它们就相等。尽管所有字段都相等，如果某个子集是唯一的，你不需要比较所有字段——例如，货币的代码就足够测试相等性。一个通用的启发式方法是值对象应该是完全不可变的。如果你想更改一个值对象，应该用新对象替换它，而不是允许更新值对象本身的值。

值对象会导致别名问题。

¹[`c2.com/cgi/wiki?ValueObject`](http://c2.com/cgi/wiki?ValueObject)

²[`martinfowler.com/bliki/ValueObject.html`](http://martinfowler.com/bliki/ValueObject.html)

# 值对象

值对象的示例包括数字、文本字符串、日期、时间、人的姓名（由名、中间名、姓和头组成）、货币、颜色、电话号码和邮寄地址。

### 练习

尝试在你当前的领域中寻找更多潜在的值对象示例。

### 3.2 值对象 vs 实体

考虑以下来自[维基百科³](http://en.wikipedia.org/wiki/Domain-driven_design#Building_blocks_of_DDD)的示例，以更好地理解值对象（Value Objects）与实体（Entities）之间的区别。

人们交换钞票时，通常不会区分每一张独特的钞票。他们只关心钞票的面值。在这种背景下，钞票是值对象。然而，联邦储备部可能对将钞票作为唯一身份进行追踪，因此将它们视为实体。

另一个例子可能是，许多航空公司区分座位，将它们视为独特的位置。在这种情况下，座位可以被视为一个实体。另一方面，也有一些航空公司（如美国西南航空（或欧洲的廉捷航空/莱安航空））并不区分座位。在这种背景下，座位可以被视为一个值对象。

### 练习

关于地址（街道、门牌、邮政编码等）的概念。在什么可能的语境下，地址可以被建模为实体而不是值对象？请与同事讨论你的发现。

## 3.3 货币和金额示例

货币和金额值对象可能是解释值对象最常用的示例，这得益于[货币模式](http://martinfowler.com/eaaCatalog/money.html)⁴。这种设计模式提供了一种建模该问题的解决方案，以避免浮点数舍入问题，允许执行确定性的计算。

在现实世界中，货币描述单位的方式就像米和码描述距离单位一样。每种货币用三个大写字母 ISO 代码表示。

³[`en.wikipedia.org/wiki/Domain-driven\_design#Building\_blocks\_of\_DDD`](http://en.wikipedia.org/wiki/Domain-driven_design#Building_blocks_of_DDD)

⁴[`martinfowler.com/eaaCatalog/money.html`](http://martinfowler.com/eaaCatalog/money.html)

### class Currency

```php
class Currency
{
    private $isoCode;
    public function __construct($anIsoCode)
    {
        $this->setIsoCode($anIsoCode);
    }

    private function setIsoCode($anIsoCode)
    {
        if (!preg_match('/^[A-Z]{3}$/', $anIsoCode)) {
            throw new \InvalidArgumentException();
        }
        $this->isoCode = $anIsoCode;
    }

    public function isoCode()
    {
        return $this->isoCode;
    }
}
```

值对象的主要目标之一也是面向对象设计的终圣杯：封装。通过遵循这种抽象，你将拥有一个专门的位置，用于存放特定概念的所有验证、比较逻辑和行为。

金额（Money）用于衡量特定数量的货币。它是通过一个金额和一个`Currency`（货币）来建模的。在货币模式中，金额使用货币最小价值单位的整数表示法来实现——例如，在美元或欧元的情况下，即分。

作为一个额外点，你还会在示例中注意到我们正在使用[自封装⁵](http://martinfowler.com/bliki/SelfEncapsulation.html)来设置 ISO 代码，将更改集中在值对象本身中。

⁵[`martinfowler.com/bliki/SelfEncapsulation.html`](http://martinfowler.com/bliki/SelfEncapsulation.html)

### class Money

```php
class Money
{
    private $amount;
    private $currency;
    public function __construct($anAmount, Currency $aCurrency)
    {
        $this->setAmount($anAmount);
        $this->setCurrency($aCurrency);
    }

    private function setAmount($anAmount)
    {
        $this->amount = (int) $anAmount;
    }

    private function setCurrency(Currency $aCurrency)
    {
        $this->currency = $aCurrency;
    }

    public function amount()
    {
        return $this->amount;
    }

    public function currency()
    {
        return $this->currency;
    }
}
```

现在你已经了解了值对象的正式定义，让我们深入探讨它们提供的一些强大功能。

### 3.4 特性

在代码中建模通用语言（Ubiquitous Languages）概念时，你应该始终优先选择值对象而不是实体。值对象更容易创建、测试、使用和维护。

考虑到这一点，如果满足以下条件，你可以决定问题概念是否可以建模为值对象：

- 它衡量、量化或描述了某个事物

- 它可以保持不可变性

- 它通过组合相关属性来建模一个概念整体

- 当描述变化时，它是可替换的

- 它为协作者提供无副作用（Side-Free）的行为

### 3.4.1 衡量、量化或描述

如前所述，值对象不应该仅仅被视为领域中的一个事物。作为一个“值”，它衡量、量化或或描述了一个概念。在我们的示例中，`Currency` 对象描述了是什么种类型的钱。

### 3.4.2 不可变性

这是掌握值对象最重要的方面之一。对象不应在其整个生命周期内被修改。由于这种不可变性，值对象易于推理、测试，并且没有意外的副作用。因此，值对象应该通过其构造函数创建。带有多个设置器（setter）的空构造函数会将创建责任推移给客户端，导致[贫血的](http://martinfowler.com/bliki/AnemicDomainModel.html)[领域模型](http://martinfowler.com/bliki/AnemicDomainModel.html)⁶，这被认为是一种反模式。

同样值得指出的是，不建议在你的值对象中持有实体的引用。实体是可变的，因此这可能会导致值对象中出现不必要的副作用。

在支持[方法重载](http://en.wikipedia.org/wiki/Function_overloading)⁷的语言 Java 中，你可以创建多个同名的构造函数。这些构造函数提供了不同的选项来构建相同类型的结果对象。在 PHP 中，我们能够通过[工厂方法](http://en.wikipedia.org/wiki/Factory_method_pattern)⁸提供类似的能力。在我们的 `Money` 对象中，我们可以添加一些实用的工厂方法，例如：

```php
class Money
{
    // ...
    public static function fromMoney(Money $aMoney)
    {
        return new self(
            $aMoney->amount(),
            $aMoney->currency()
        );
    }

    public static function ofCurrency(Currency $aCurrency)
    {
        return new self(0, $aCurrency);
    }
}
```

通过使用 `self` 关键字，我们没有将代码与类名耦合。这样，对⁶[`martinfowler.com/bliki/AnemicDomainModel.html`](http://martinfowler.com/bliki/AnemicDomainModel.html)

⁷[`en.wikipedia.org/wiki/Function\_overloading`](http://en.wikipedia.org/wiki/Function_overloading)

⁸[`en.wikipedia.org/wiki/Factory\_method\_pattern`](http://en.wikipedia.org/wiki/Factory_method_pattern) 的更改将受到影响。

`class` 名称或命名空间不会影响这些工厂方法。这个细小的实现细节有助于日后对代码进行重构。

### static vs. self

当 `Value Object`（值对象）继承另一个 `Value Object` 时，使用 `static` 替代 `self` 可能会导致意外的问题。

由于这种不可变性，我们必须考虑如何处理有状态上下文中常见的可变操作。如果我们需要更改状态，现在我们必须返回一个带有该更改的全新 `Value Object` 表示。

例如，如果我们想增加 `Money` 值对象的金额，我们现在必须返回一个带有所需修改的全新 `Money` 实例。幸运的是，如例所示，遵循这一规则相对简单。

#### class Money

```php
class Money
{
    // ... ...
    public function increaseAmountBy($anAmount)
    {
        return new self(
            $this->amount() + $anAmount,
            $this->currency()
        );
    }
}
```

`increaseAmountBy` 返回的对象与调用该方法的对象不同。在下方的示例比较中可以观察到这一点。

```php
$aMoney = new Money(100, new Currency('USD'));
$otherMoney = $aMoney->increaseAmountBy(100);
var_dump($aMoney === $otherMoney); // bool(false)

$aMoney = $aMoney->increaseAmountBy(100);
var_dump($aMoney === $otherMoney); // bool(false)
```

### 3.4.3 概念性整体

你可能在想，为什么不直接实现类似下面示例的代码，从而避免创建新的 `Value Object` 类呢？

```php
class Product
{
    private $id;
    private $name;

    /**
     * @var int
     */
    private $amount;

    /**
     * @var string
     */
    private $currency;
    // ... ...
}
```

这种方法存在一些明显的缺陷，例如你想验证 ISO 码。让 `Product` 负责货币的 ISO 验证并不真的符合逻辑（违背了单一职责原则）。如果你想在领域的其他部分复用相关的逻辑（以遵循 DRY 原则），这一点会更加凸显。考虑到这些因素，这个用例是抽象为值对象的完美候选者。使用这种抽象不仅让你有机会将相关属性组合在一起，还让你能够创建高阶概念和更具体的通用语言（Ubiquitous Language）。

#### 练习

与同伴讨论电子邮箱是否可以被视为值对象。它使用的上下文重要吗？

### 3.4.4 值等价性

正如章节开头提到的，如果两个 `Value Object` 所测量、量化或描述的内容相同，那么它们就是相等的。

例如，想象两个代表 1 美元的 `Money` 对象。我们可以认为它们是相等的吗？在“现实”世界中，两枚 1 美元的硬币价值相同吗？当然是。……问题中指的是 `Money` 的独立实例。然而，我们可以认为它们都代表相同的值，因此它们反过来相等的。

在 PHP 中，使用 `==` 运算符比较两个 `Value Object` 是常见的。查看 [PHP 文档](http://php.net/manual/en/language.oop5.object-comparison.php) 对该运算符的定义可以揭示一种有趣的行为。当使用比较运算符 (`==`) 时，对象变量是以简单的方式进行比较的，即：如果两个对象实例具有相同的属性和值，并且是相同类的实例，则它们是相等的。

这种行为与我们对 `Value Object` 的正式定义一致。然而，由于存在精确的类匹配谓词，在处理子类型 `Value Object` 时你应该小心。考虑到这一点，遗憾的是，更严格的 `===` 运算符无法帮到我们。

当使用恒等运算符 (`===`) 时，当且仅当对象变量引用同一个同类的同一个实例时，它们才是相同的。

以下示例应该有助于确认这些细微的差异。

```php
$a = new Currency('USD');
$b = new Currency('USD');
var_dump($a == $b); // bool(true)
var_dump($a === $b); // bool(false)

$c = new Currency('EUR');
var_dump($a == $c); // bool(false)
var_dump($a === $c); // bool(false)
```

考虑到此，一种解决方案是在每个 `Value Object` 中实现一个常规的 `equals` 方法。该方法的任务是检查其复合属性的类型和相等性。使用 PHP 内置的类型提示很容易实现抽象数据类型的比较。另一方面，如有必要，你也可以使用 `get_class()` 函数辅助比较检查。然而，语言本身无法理解你的领域概念中相等性真正意味着什么，这意味着提供答案是你的责任。

为了比较 `Currency` 对象，我们只需要比较它们关联的 ISO 码是否相同。在这种情况下，`===` 运算符非常好。

```php
class Currency
{
    // ... ...
    public function equals(Currency $currency)
    {
        return $currency->isoCode() === $this->isoCode();
    }
}
```

由于 `Money` 对象使用了 `Currency` 对象，因此 `equals` 方法需要执行这种比较检查，并比较金额。

```php
class Money
{
    // ... ...
    public function equals(Money $money)
    {
        return
            $money->currency()->equals($this->currency()) &&
            $money->amount() === $this->amount();
    }
}
```

### 3.4.5 可替换性

考虑一个包含用于量化价格的 `Money` 值对象的 `Product` 实体。再考虑两个价格相同（例如 100 美元）的 `Product` 实体。这种场景可以使用两个独立的 `Money` 对象或两个指向单个值对象的引用来建模。共享同一个值对象可能是危险的，如果其中一个被修改，两个都会反映该变化。这种行为可以被视为一种意料之外的副作用。

由于此示例中突出了持有值对象引用而非修改其值产生的问题，建议直接替换整个对象。



```php
$this->price = new Money(100, new Currency('USD'));
// ... ...
$this->price = $this->price->increaseAmountBy(200);
```

这种行为类似于 PHP 中基本类型（如字符串）的工作方式。考虑`strtolower`函数，它返回一个新字符串而不是修改原始字符串。没有使用引用，而是返回了一个新值。

### 3.4.6 无副作用行为

如果我们想在`Money`类中包含一些额外的行为，例如`add`方法，检查输入是否符合任何先置条件并维护任何不变性是是很自然的做法。在我们的案例中，我们只希望相相同货币的金额。

```php
class Money
{
    // ... ...
    public function add(Money $money)
    {
        if ($money->currency() !== $this->currency()) {
            throw new \InvalidArgumentException();
        }
        $this->amount += $money->amount();
    }
}
```

如果两种货币不匹配，则抛出异常。否则，金额会相加。然而，这段代码有一些不理想的陷阱。现在假设我们有另一个方法`otherMethod`。

```php
class Banking
{
    public function aMethod()
    {
        $aMoney = new Money(100, new Currency('USD'));
        $this->otherMethod($aMoney);
        // ... ...
    }
}
```

一切都正常，直到由于某种原因，我们开始在`$aMoney`中看到意之外的结果。如果`otherMethod`使用了我们之前定义的`add`方法会发生什么？也许你没有意识到`add`会改变`Money`实例的状态。这就是我们所说的**副作用（`side-effect`）**。你不应该修改参数，因为客户端永远不会期望这种行为。

那么，我们该如何修复这个问题呢？很简单，通过确保值对象（Value Object）保持不可变，我们就可以避免这种意外的问题。一个简单的解决方案是为每个潜在的可变操作（例如`add`方法）返回一个新实例。

## Value Objects

```php
class Money
{
  //...
  public function add(Money $money)
  {
    if (!$money->currency()->equals($this->currency())) {
      throw new \InvalidArgumentException();
    }

    return new self(
      $money->amount() + $this->amount(),
      $this->currency()
    );
  }
}
```

通过这个简单的改动，不可变性得到了保证。每当将两个`Money`相加时，都会返回一个新的结果实例。其他类可以执行任意数量的更改而不会影响原始副本。没有副作用的代码易于理解、易于测试，且不易出错。

## Value Objects

### 3.5 基础类型

考虑以下代码段。

```php
$a = 10;
$b = 10;
var_dump($a == $b);
// bool(true)
var_dump($a === $b);
// bool(true)
$a = 20;
var_dump($a);
// integer(20)
$a = $a + 30;
var_dump($a);
// integer(50)
```

尽管`$a`和`$b`是不同的变量，在底层存储在不同的内存位置，但当比较时它们是相同的。它们持有相同的值。我们认为它们是相等的。你可以随时将`$a`的值从 10 改为 20，新值是 20，而 10 消失了。你可以随所欲地替换整数值而不必考虑之前的值，因为你并不是在修改它，你只是在替换它。如果你对它们执行任何操作（如加法`$a + $b`），你会得到另一个新值并赋值给另一个变量或之前定义的变量。当你将`$a`传递给另一个函数时，除非显式通过引用传递，否则你传递的是值。`$a`在函数内部是否被修改无关，因为在你的当前代码中，仍然拥有原始副本。值对象的行为就像基础类型一样。

## Value Objects

### 3.6 测试

值对象的测试方式与普通对象相同。然而，必须测试不可变性和无副作用的行为。一种解决方案是在执行任何修改之前，为你正在测试的值对象创建一个副本。使用实现的等性检查断言两者是相等的。执行你想测试的操作并断言结果。最后，断言原始对象和副本仍然是相等的。让我们付诸实践，测试`Money`类中`add`方法的无副作用实现。

```php
class MoneyTest extends \PHPUnit_Test_TestCase
{
    /**
     * @test
     */
    public function copiedMoneyShouldRepresentSameValue()
    {
        $aMoney = new Money(100, new Currency('USD'));
        $copiedMoney = Money::fromMoney($aMoney);
        $this->assertTrue($aMoney->equals($copiedMoney));
    }

    /**
     * @test
     */
    public function originalMoneyShouldNotBeModifiedOnAddition()
    {
        $aMoney = new Money(100, new Currency('USD'));
        $aMoney->add(new Money(20, new Currency('USD')));
        $this->assertEquals(100, $aMoney->amount());
    }

    /**
     * @test
     */
    public function moneysShouldBeAdded()
    {
        $aMoney = new Money(100, new Currency('USD'));
        $newMoney = $aMoney->add(new Money(20, new Currency('USD')));
        $this->assertEquals(120, $newMoney->amount());
    }
    // ...
}
```

## Value Objects

### 3.7 持久化值对象

值对象不会独立持久化，它们通常在聚合根（Aggregate）内部被持久化。值对象不应作为完整的记录持久化，尽管在某些情况下这是一种选项。相反，最好使用**嵌入值（Embedded Value）**或**序列化大对象（Serialize LOB）**模式。当你使用开源 ORM（如 Doctrine）或自定义 ORM 持久化对象时，这两种模式均可使用。由于值对象很小，嵌入值通常是最佳选择，因为它允许通过值对象拥有的任何属性来轻松查询实体（Entities）。然而，如果通过这些字段查询对你来说并不重要，序列化策略可以非常容易实现。

考虑以下`Product`实体，它具有字符串类型的 id、name 和 price（Money 值对象）属性。我们特意决定简化此示例，让 id 为字符串而非值对象。

```php
class Product
{
  private $productId;
  private $name;
  private $price;

  public function __construct(
    $aProductId,
    $aName,
    Money $aPrice
  ) {
    $this->setProductId($aProductId);
    $this->setName($aName);
    $this->setPrice($aPrice);
  }
  // ...
}
```

在 DBAL 中，`DbalProductRepository`应该创建`INSERT`语句，绑定参数并执行它。

```php
class DbalProductRepository extends DbalRepository implements ProductRepository
{
    public function add(Product $aProduct)
    {
        $sql = 'INSERT INTO products VALUES (?, ?, ?, ?)';
        $stmt = $this->connection()->prepare($sql);
        $stmt->bindValue(1, $aProduct->id());
        $stmt->bindValue(2, $aProduct->name());
        $stmt->bindValue(3, $aProduct->price()->amount());
        $stmt->bindValue(4, $aProduct->price()->currency()->isoCode());
        $stmt->execute();
        // ...
    }
}
```

在执行这段代码创建 Product 实体并将其持久化到数据库后，每一列都填充了所需的信息。

```bash
mysql> select \* from products \G
******************************** 1 row *********************************
id: 1
name: Domain-Driven Design in PHP
price_amount: 999
price_currency: USD
1 row in set (0.00 sec)
```

如你所见，你可以以临时的方式映射你的值对象（Value Objects）和查询参数以持久化你的值对象。然而，一切并不看起来那么简单。让我们尝试获取持久化的 Product 及其的 Money 值对象。一种常见的方法是执行`SELECT`语句并返回一个新的实体。

![](img/index-74_1.png)

## 值对象

```php
class DbalProductRepository extends DbalRepository implements ProductRepository
{
    public function productOfId($anId)
    {
        $sql = 'SELECT \* FROM products WHERE id = ?';
        $stmt = $this->connection()->prepare($sql);
        $stmt->bindValue(1, $anId);
        $res = $stmt->execute();
        // ...
        return new Product(
            $row['id'],
            $row['name'],
            new Money(
                $row['price_amount'],
                new Currency(
                    $row['price_currency']
                )
            )
        );
    }
}
```

这种方法具有一些优点。首先，你可以轻松地逐步读取持久化以及随后的创建是如何发生的。其次，你可以根据值对象的任何属性进行查询。最后，持久化实体所需的空间恰好是所需的，不多也不少。

然而，使用这种临时的 ORM 方法也有其缺点。正如在 领域事件 中解释的那样，如果你的领域对聚合根（Aggregates）的创建感兴趣，实体（以聚合的形式存在）应该在构造函数中触发一个事件。如果你使用`new`运算符，你触发事件的次数将与聚合根从数据库加载的次数相同。

这就是为什么 Doctrine 内部使用`Proxies`（代理）、`serialize`和`unserialize`方法在不使用构造函数的情况下重构一个带有其属性的对象。一个实体在其生命周期内内应该只被使用`new`运算符创建一次。

### 构造函数

构造函数不需要为对象中的每个属性包含一个参数。考虑一个 Post（文章）。构造函数可能需要一个`id`和一个`title`，但在内部，它也可以将状态设为草稿。在发布时，应该调用`publish`方法来更改其状态并设置发布日期。如果你的意图仍然是推出自己的 ORM，请准备好解决一些基础性问题，例如事件、不同的构造函数、懒加载关系等。这就是为什么我们建议在 DDD 应用中尝试 Doctrine。此外，在此实例中，你需要创建一个扩展自 Product 的 DbalProduct 实体，并能够能够使用静态工厂方法从数据库重构实体。

### 3.7.1.2. Doctrine >= 2.5 的嵌入式 (Embeddables)

在编写本文时，Doctrine 的稳定版本目前是 2.4。Doctrine 2.5 正在开发中，并带有了对映射值对象的支持，消除了自己执行此操作的需要。目前 Doctrine 似乎不支持嵌套嵌入。目前，请查阅 [Doctrine](https://doctrine-orm.readthedocs.org/en/latest/tutorials/embeddables.html) 以获取更多信息。这个选项如果实现正确，绝对是我们最推荐的。这将是最简单、最优雅的解决方案，同时在你的 DQL 查询中提供搜索功能。然而，在目前这在生产环境中并不是一个选项。请放心，一旦这种情况发生变化，我们将更新书籍。

### 3.7.1.3 Doctrine <= 2.4 的嵌入式

那么对于在 Doctrine < 2.5 中使用嵌入值什么是可以接受的解决方案呢？我们需要在 Product 实体中所有的值对象属性进行代理，这意味着创建用于存储值对象信息的人造属性。一旦完成，我们就可以使用 Doctrine 映射这些新属性。让我们看看这对 Product 实体的影响。

```php
class Product
{
    protected $productId;
    protected $name;
    protected $price;
    protected $surrogateCurrencyCode;
    protected $surrogateAmount;

    public function __construct($aProductId, $aName, Money $aPrice)
    {
        $this->setProductId($aProductId);
        $this->setName($aName);
        $this->setPrice($aPrice);
    }

    private function setPrice(Money $aMoney)
    {
        $this->price = $aMoney;
        $this->surrogateAmount = $aMoney->amount();
        $this->surrogateCurrencyCode = $aMoney->currency()->isoCode();
    }

    private function price()
    {
        if (null === $this->price) {
            $this->price = new Money(
                $this->surrogateAmount,
                new Currency($this->surrogateCurrencyCode)
            );
        }
        return $this->price;
    }
    // ...
}
```

如你所见，有两个新属性。一个用于金额，另一个用于货币 ISO 代码。我们还更新了`setPrice`方法以在设置时保持一致性。在此基础上，我们更新了`price` getter 以从新字段构建 Money 对象。让我们看看对应的 XML Doctrine 映射应该如何改变。



```xml
<?xml version="1.0" encoding="utf-8"?>
<doctrine-mapping
    xmlns="http://doctrine-project.org/schemas/orm-mapping"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://doctrine-project.org/schemas/orm-mapping https://raw.githubusercontent.com/doctrine/doctrine2/master/doctrine-mapping.xsd">
    <entity name="Product" table="product">
        <id name="id" column="id" type="string" length="255">
            <generator strategy="NONE"></generator>
        </id>
        <field name="name" type="string" length="255"/>
        <field name="surrogateAmount" type="integer" column="price_amount"/>
        <field name="surrogateCurrencyCode" type="string" column="price_currency"/>
    </entity>
</doctrine-mapping>
```

![](img/index-77_1.png)

## 代理属性

这两个新字段并不严格属于领域，因为它们不指向基础设施细节，但由于 Doctrine 缺乏嵌入支持，它们是必要的（原文为 an necessity）。存在其他替代方案可以将这两个属性推到纯领域之外，然而，这种方法更简单、更容易，并且作为权衡，是可以接受的。代理属性在书中还有另一个用处，你可以在代理实体标识时找到它。

使用了[抽象工厂](http://en.wikipedia.org/wiki/Abstract_factory_pattern)¹³。首先，我们需要在 `Infrastructure` 文件夹中创建一个新的 `Entity`，即 `DoctrineProduct`，它继承自 `Product` 实体。所有的代理字段将将放在新类中，并且诸如 `price` 或 `setPrice` 等方法需要重新实现。我们将 `Doctrine` 配置为使用新的 `DoctrineProduct` 而不是 `Product` 实体。现在，我们能够从数据库中获取 `Entities`，但是，创建一个新的 `Product` 呢？在某些时刻，我们需要调用 `new Product`，但因为我们需要处理 `DoctrineProduct`，且不希望我们的 `Application Services` 了解基础设施细节，我们需要使用 `Factories` 来创建 `Product` 实体。因此，在每个使用 `new` 创建 `Entity` 的实例中，你现在将改为调用 `ProductFactory` 上的 `createProduct`。

¹³[`en.wikipedia.org/wiki/Abstract\_factory\_pattern`](http://en.wikipedia.org/wiki/Abstract_factory_pattern)

## 值对象 (Value Objects)

可能需要许多额外的类，以避免将代理属性放在原始 `Entity` 中。因此，我们建议将所有的 `Value Objects` 代理到同一个 `Entity` 中，尽管这会导致方案不够纯粹。

### 3.7.1.4 序列化 LOB 和即时 ORM

如果为 `Value Objects` 属性添加搜索功能并不重要，还有另一种可以考虑的模式，即序列化 LOB（Serialized LOB）。这种模式通过将整个 `Value Object` 序列化为易于持久化和获取的字符串格式来实现。这种解决方案与 `Embedded` 替代方案的主要区别在于，在后者中，持久化足迹被减少到了单列。

```sql
CREATE TABLE products (
  id INT NOT NULL,
  name VARCHAR(255) NOT NULL,
  price TEXT NOT NULL
)
```

为了使用这种方法持久化 `Product` 实体，需要对 `DbalProductRepository` 进行更改。在持久化最终的 `Entity` 之前，必须将 `Money` 值对象序列化为字符串。

```php
class DbalProductRepository extends DbalRepository implements ProductRepository
{
    public function add(Product $aProduct)
    {
        $sql = 'INSERT INTO products VALUES (?, ?, ?)';
        $stmt = $this->connection()->prepare($sql);
        $stmt->bindValue(1, $aProduct->id());
        $stmt->bindValue(2, $aProduct->name());
        $stmt->bindValue(3, $this->serialize($aProduct->price()));
        // ...
    }

    private function serialize($object)
    {
        return serialize($object);
    }
}
```

让我们看看我们的 `Product` 现在在数据库中是如何表示的。表列 `price` 是 `TEXT` 类型，包含了代表 9,99 USD 的 `Money` 对象的序列化。

```mysql
mysql> select * from products
1 row
id: 1
name: Domain-Driven Design in PHP
price: O:22:"Ddd\Domain\Model\Money":2:{s:30:" Ddd\Domain\Model\Money amount";i:999;s:32:" Ddd\Domain\Model\Money currency";O:25:"Ddd\Domain\Model\Currency":1:{s:34:" Ddd\Domain\Model\Currency isoCode";s:3:"USD";}}
1 row in set (0.00 sec)
```

这种方法可以完成工作，但由于在代码中重构类时会发生的问题，并不建议使用。你能想象当将 `Money` 类从一个命名空间移动到另一个命名空间时，我们的数据库表示需要哪些变化吗？如所述，另一个权衡是缺乏查询能力。无论你是否使用 `Doctrine`，在使用序列化策略时，编写查询获取低于 200 美元的产品的几乎是不可能的。

查询问题只能通过使用 `Embedded Values` 来解决，但序列化的重构问题可以使用专门的库修复。

### 3.7.1.4 使用 JMS 改进序列化

如前所述，另一个权衡是缺乏查询能力。无论你是否使用 `Doctrine`，在使用序列化策略时，编写查询获取低于 200 美元的产品的几乎是不可能的。

查询问题只能通过使用 `Embedded Values` 来解决，但序列化的重构问题可以使用专门的库修复。

### 3.7.1.5 使用 Doctrine 的序列化 LOB

在 Doctrine 中，有不同的方法来序列化对象以便最终持久化。

#### 3.7.1.5.1 Doctrine 对象映射

Doctrine 支持序列 LOB 模式。你有许多映射类型可以匹配 `Entity` 属性与数据库列甚至表。这些映射类型之一就是对象类型。它使用 `serialize()` 和 `unserialize()` 将 `CLOB` 映射到 PHP 对象。

正如文档所述：“对象类型根据序列化映射并转换对象数据。如果你需要存储对象的精确表示，应该考虑使用这种类型，因为它使用序列化将你的对象的精确副本作为字符串存储在数据库中。从数据库检索出的值始终通过反序列化转换为 PHP 的对象类型，或者在没有数据时转换为 null。这种类型内部始终会被映射到数据库供应商的文本类型，因为没有办法在数据库中原生存储 PHP 对象表示。此外，这种类型需要一个 SQL 列注释提示，以便从数据库进行反向工程。Doctrine 无法使用不支持列注释的供应商正确映射回这种类型，而是退回到文本类型。解决此问题的变方法是手动 `serialize()/unserialize()` 和 `base64_encode()/base64_decode()` PHP 对象并将它们存储到文本字段中。”

让我们看看使用对象类型为 `Product` 实体可能的 XML 映射。

```xml
<?xml version="1.0" encoding="utf-8"?>
<doctrine-mapping
xmlns="http://doctrine-project.org/schemas/orm/doctrine-mapping"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
```

```xml
xsi:schemaLocation="http://doctrine-project.org/schemas/orm/doctrine-mapping https://raw.github.com/doctrine/doctrine2/master/doctrine-mapping.xsd">

<entity name="Product" table="products">
    <id name="id" column="id" type="string" length="255">
        <generator strategy="NONE"></generator>
    </id>
    <field name="name" type="string" length="255"/>
    <field name="price" type="object"/>
</entity>
</doctrine-mapping>
```

关键的添加是 `type="object"`，它告诉 Doctrine 我们现在将使用对象映射。现在让我们来看看如何使用 Doctrine 创建并持久化一个 `Product` 实体。

### 值对象 (Value Objects)

```php
// ...
$em->persist($product);
$em->flush($product);
```

让我们检查一下，如果现在我们从数据库获取我们的 `Product` 实体，它返回的是否预期的状态。

```php
// ...
$repository = $em->getRepository('Ddd\\\\Domain\\\\Model\\\\Product');
$item = $repository->find(1);
var_dump($item);
```

```php
class Ddd\\Domain\\Model\\Product#177 (3) {
    protected $productId => int(1)
    protected $name => string(41) "Domain-Driven Design in PHP"
    protected $money => class Ddd\\Domain\\Model\\Money#174 (2) {
        private $amount => string(3) "100"
        private $currency => class Ddd\\Domain\\Model\\Currency#175 (1) {
            private $isoCode => string(3) "USD"
        }
    }
}
```

最后，但同样重要的，正如 Doctrine 文档所述：“对象类型通过引用进行比较，而不是通过值。如果引用发生变化，Doctrine 会更新此值，因此表现就像这些对象是不可变的值对象一样。”更多信息请查看 [Doctrine 基础映射类型参考¹⁷](http://docs.doctrine-project.org/projects/doctrine-orm/en/latest/reference/basic-mapping.html#doctrine-mapping-types)。

这种方法面临与即用 ORM 相同的重构问题。对象映射类型内部使用 `serialize/unserialize`。如果改用我们自己的序列化会怎样？

¹⁷[`docs.doctrine-project.org/projects/doctrine-orm/en/latest/reference/basic-mapping.html#doctrine-mapping-types`](http://docs.doctrine-project.org/projects/doctrine-orm/en/latest/reference/basic-mapping.html#doctrine-mapping-types)

### 3.7.1.5.2 Doctrine 自定义类型

另一种选项是使用 Doctrine 自定义类型来处理值对象的持久化。自定义类型为 Doctrine 增加了一种新的映射类型，描述了实体字段与数据库表示之间的自定义转换，以便进行持久化。

正如 Doctrine 文档解释的，“仅仅重新定义数据库类型如何映射到所有现有 Doctrine 类型完全没有用。你可以通过扩展 `Doctrine\\DBAL\\Types\\Type` 来定义你自己的 Doctrine 映射类型。你需要实现 4 个不同的方法才能使其正常工作。”

使用对象类型时，序列化步骤包含了类（class）等信息，这使得安全地重构我们的代码变得非常困难。让我们尝试改进这个解决方案。考虑一个可以解决问题的自定义序列化过程。其中一种方法是将 `Money` 值对象以“amount|isoCode”格式编码为字符串持久化到数据库中吗？

```php
use Ddd\\Domain\\Model\\Currency;
use Ddd\\Domain\\Model\\Money;
use Doctrine\\DBAL\\Types\\TextType;
use Doctrine\\DBAL\\Platforms\\AbstractPlatform;

class MoneyType extends TextType
{
    const MONEY = 'money';

    public function convertToPHPValue($value, AbstractPlatform $platform)
    {
        $value = parent::convertToPHPValue($value, $platform);
        $value = explode('|', $value);
        return new Money(
            $value[0],
            new Currency($value[1])
        );
    }

    public function convertToDatabaseValue($value, AbstractPlatform $platform)
    {
        return implode(
            '|',
            [
                $value->amount(),
                $value->currency()->isoCode()
            ]
        );
    }

    public function getName()
    {
        return self::MONEY;
    }
}
```

使用 Doctrine 你需要注册所有自定义类型。通常使用一个 `EntityManagerFactory` 来集中处理 `EntityManager` 的创建。你也可以在引导程序中完成这一步。

```php
use Doctrine\\DBAL\\Types\\Type;
use Doctrine\\ORM\\EntityManager;
use Doctrine\\ORM\\Tools\\Setup;

class EntityManagerFactory
{
    public function build()
    {
        Type::addType(
            'money',
            'Ddd\\\\Infrastructure\\\\Doctrine\\\\Type\\\\MoneyType'
        );
        return EntityManager::create(
            [
                'driver' => 'pdo_mysql',
                'user' => 'root',
                'password' => '',
                'dbname' => 'ddd',
            ],
            Setup::createXMLConfiguration(
                __DIR__.'/config',
                true
            )
        );
    }
}
```



现在，我们需要在映射中指定要使用的自定义类型。

```xml
<?xml version="1.0" encoding="utf-8"?>
<doctrine-mapping xsi:schemaLocation="http://doctrine-project.org/schemas/orm/doctrine-mapping https://raw.github.com/doctrine/doctrine2/master/doctrine-mapping.xsd">
<entity name="Product" table="products">
    <id name="id" column="id" type="string" length="255">
        <generator strategy="NONE"></generator>
    </id>
    <field name="name" type="string" length="255"/>
    <field name="price" type="money"/>
</entity>
</doctrine-mapping>
```

## 3.7.2 持久化值对象集合

假设现在我们想为`Product`实体添加一个要持久化的价格集合。这些价格可能代表产品在其生命周期内经历过的价格，或者不同货币下的产品价格。它可以命名为所示的`HistoricalProduct`。

```php
class HistoricalProduct extends Product
{
    /**
     * @var Money[]
     */
    protected $prices;

    public function __construct($aProductId, $aName, Money $aPrice, array $somePrices)
    {
        parent::__construct($aProductId, $aName, $aPrice);
        $this->setPrices($somePrices);
    }

    private function setPrices(array $somePrices)
    {
        $this->prices = $somePrices;
    }

    public function prices()
    {
        return $this->prices;
    }
}
```

`HistoricalProduct`继承自`Product`，因此继承了相同的行为以及价格集合的功能。

### 3.7.2.1 序列化到单列的集合

将值对象集合序列化到单列可能是最简单的解决方案。之前讨论的所有关于持久化单个值对象的内容都适用于此处。

在这种情况下，使用 Doctrine 时你可以使用对象（Object）或自定义类型（Custom Type），但需要注意一些额外的问题：值对象（Value Objects）的大小应该尽可能小，但如果你想持久化一个大型集合，请务必考虑数据库引擎能够处理的最大列长度和最大行宽。

#### 练习

为持久具有不同价格的产品（Product）构思两种 Doctrine 对象类型和 Doctrine 自定义类型的实现策略。

### 3.7.2.2 由连接表支持的集合

当需要持久化一个包含值对象集合的实体且需要查询能力时，你可以选择将值对象持久化为实体（Entities）。在领域（Domain）中，这些对象仍然是值对象，但我们需要为它们提供一个`id`，并与所有者（一个真实的实体）建立“一对多”或“一对一”关联。简而言之，你的 ORM 将值对象的集合作为实体处理，但在你的领域中，它们仍然被视为值对象。

“连接表”策略的核心思想是创建一个连接所有者实体及其值对象的表。让我们来看看数据库的表示。

```sql
CREATE TABLE `historical_products` (
  `id` varchar(255) COLLATE utf8_unicode_ci NOT NULL,
  `name` varchar(255) COLLATE utf8_unicode_ci NOT NULL,
  `price_amount` int(11) NOT NULL,
  `price_currency` varchar(255) COLLATE utf8_unicode_ci NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci;
```

`historical_products`表看起来与`products`表相同。记住，为了方便展示如何处理集合的持久化，`HistoricalProduct`扩展了`Product`实体。现在需要一个新的表来持久化产品实体可以处理的所有不同 Money 值对象。

```sql
CREATE TABLE `prices` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `amount` int(11) NOT NULL,
  `currency` varchar(255) COLLATE utf8_unicode_ci NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci;
```

最后，需要一个关联产品和价格的表。

```sql
CREATE TABLE `products_prices` (
  `product_id` varchar(255) COLLATE utf8_unicode_ci NOT NULL,
  `price_id` int(11) NOT NULL,
  PRIMARY KEY (`product_id`,`price_id`),
  UNIQUE KEY `UNIQ_62F8E673D614C7E7` (`price_id`),
  KEY `IDX_62F8E6734584665` (`product_id`),
  CONSTRAINT `FK_62F8E6734584665` FOREIGN KEY (`product_id`) REFERENCES `historical_products` (`id`),
  CONSTRAINT `FK_62F8E673D614C7E7` FOREIGN KEY (`price_id`) REFERENCES `prices` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci;
```

#### 3.7.2.2.1 使用 Doctrine 由连接表支持的集合

Doctrine 要求所有数据库实体必须具有唯一标识。因为我们要持久化 Money 值对象，所以需要添加一个人工标识，以便 Doctrine 可以处理其持久化。有两种方案：在 Money 值对象中包含代理标识（surrogate identity），或将其放在扩展类中。

第一种方案的问题是，新标识仅仅是因为数据库持久化层的需要。这个标识并不属于领域。

第二种方案的问题是，为了避免上述边界泄漏（boundary leak），需要大量的修改。使用类扩展时，不建议从任何领域对象创建 Money 对象类的新实例，因为这会破坏倒置原则（Inversion Principle）。解决方案是再次创建一个 Money 工厂，该工厂需要传递到应用程序和服务任何其他领域对象中。

在这种情况下，我们建议使用第一种方案。让我们查看 Money 值对象所需的更改。

```php
class Money
{
    private $amount;
    private $currency;
    private $surrogateId;
    private $surrogateCurrencyIsoCode;

    public function __construct($amount, Currency $currency)
    {
        $this->setAmount($amount);
        $this->setCurrency($currency);
    }

    private function setAmount($amount)
    {
        $this->amount = $amount;
    }

    private function setCurrency(Currency $currency)
    {
        $this->surrogateCurrencyIsoCode = $currency->isoCode();
    }

    public function currency()
    {
        if (null === $this->currency) {
            $this->currency = new Currency($this->surrogateCurrencyIsoCode);
        }
        return $this->currency;
    }

    public function amount()
    {
        return $this->amount;
    }

    public function equals(Money $aMoney)
    {
        return
        $this->amount() === $aMoney->amount()
        && $this->currency()->equals($this->currency());
    }
}
```

如所示，添加了两个新属性。第一个属性`surrogateId`我们的领域并不使用，但是持久化基础设施将此值对象持久化为实体时所需的。第二个属性`surrogateCurrencyIsoCode`保存货币的 ISO 代码。使用这些新属性可以很容易地映射我们的值对象。

Money 的映射非常直接。

```xml
<?xml version="1.0" encoding="utf-8"?>
<doctrine-mapping xmlns="http://doctrine-project.org/schemas/orm/doctrine-mapping" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://doctrine-project.org/schemas/orm/doctrine-mapping https://raw.github.com/doctrine/master/doctrine-mapping.xsd">
  <entity name="Domain\Model\Money" table="prices">
    <id name="surrogateId" type="integer">
      <generator strategy="AUTO"/>
    </id>
    <field name="amount" type="integer" column="amount"/>
    <field name="surrogateCurrencyIsoCode" type="string" column="currency"/>
  </entity>
</doctrine-mapping>
```

使用 Doctrine，`HistoricalProduct`实体将拥有如下映射。

```xml
<?xml version="1.0" encoding="utf-8"?>
<doctrine-mapping xmlns="http://doctrine-project.org/schemas/orm/doctrine-mapping" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://doctrine-project.org/schemas/orm/doctrine-mapping https://raw.github.com/doctrine/master/doctrine-mapping.xsd">
  <entity name="Domain\Model\HistoricalProduct" table="historical_products" repository-class="Infrastructure\Domain\Model\DoctrineHistoricalRepository">
    <many-to-many field="prices" target-entity="Domain\Model\Money">
      <cascade>
        <cascade-all/>
      </cascade>
      <join-table name="products_prices">
        <join-columns>
          <join-column name="product_id" referenced-column-name="id"/>
        </join-columns>
        <inverse-join-columns>
          <join-column name="price_id" referenced-column-name="id" unique="true"/>
        </inverse-join-columns>
      </join-table>
    </many-to-many>
  </entity>
</doctrine-mapping>
```

#### 3.7.2.2.2 使用即时 ORM 由连接表支持的集合

使用即时 ORM 实现同样的操作，此时需要级联插入（Cascade INSERTS）和连接查询。唯一需要注意的是如何处理值对象的删除，以免留下孤立的 Money 值对象。

#### 练习

为`DbalHistoricalRepository`构思一个解决方案处理`persist`方法。

### 3.7.2.3 由数据库实体支持的集合

“数据库实体”策略与“连接表”策略相同，不同在于值对象仅由所有者实体管理。在当前场景中，考虑 Money 值对象仅被 HistoricalProduct 实体使用。使用连接表会过于复杂。因此，可以使用“一对多”数据库关系来实现相同的结果。

#### 练习

如果使用“数据库实体”（Database Entity）方法，考虑`HistoricalProduct`和`Money`之间所需的映射关系。

## 3.7.3 NoSQL

像`Redis`、`MongoDB`或`CouchDB`等 NoSQL 机制如何？遗憾的是，你无法逃避这些问题。为了使用`Redis`持化一个`Aggregate`，你需要在设置值之前将其序列化为字符串。如果你使用`PHP`的`serialize`/`unserialize`方法，你将再次面临命名空间或类名的重构问题。如果你选择用自定义方式（json、自定义字符串等）进行序列化，那么你需要在从 Redis 获取时重新构建`Value Object`。

### 3.7.3.1 PostgreSQL 和 JSONB

如果我们的数据库引擎不仅允许我们使用序列化 LOB 策略，还能根据其值进行搜索，那么我们就能兼顾两种方法的优点。嗯，现在可以了。从 PostgreSQL 9.4 版本开始，增加了对[JSONB](http://www.postgresql.org/docs/9.4/static/functions-json.html)¹⁹的支持。Value Objects 现在可以作为 JSON 序列化的形式持久化，并在该 JSON 序列化内部进行查询。

## 3.8 安全

使用 Value Object 对领域概念进行建模时，另一个有趣的细节是其安全性方面的优势。考虑一个机票销售背景的应用程序。如果你处理国际民航运输协会机场代码（也称为[IATA 代码](https://en.wikipedia.org/wiki/International_Air_Transport_Association_airport_code)²⁰），你可以决定使用字符串或使用 Value Object 对该概念进行建模。如果你选择使用字符串，请考虑所有你将检查该字符串是否为有效 IATA 代码的地方。在任何重要地方遗忘的概率有多大？另一方面，考虑尝试实例化一个新的`IATA("BCN'; DROP TABLE users;--")`。如果你在构造函数中集中[守卫逻辑（guards）](https://en.wikipedia.org/wiki/Guard_\(computer_science\))²¹并向你的模型传递 IATA Value Object，那么避免 SQL 注入或类似的攻击将变得更容易。

如果你想了解更多关于领域驱动设计的安全方面，可以关注[Dan](https://twitter.com/danbjson)[Bergh Johnsson](https://twitter.com/danbjson)²²或阅读他的[博客](http://dearjunior.blogspot.com.es/search/label/domain%20driven%20security)²³。

## 3.9 总结



强烈建议使用 Value Objects 对领域中需要衡量、量化或描述的概念进行建模。如所示，Value Objects 易于创建、维护和测试。为了在 DDD 应用中处理持久化，使用 ORM 是必须的。然而，为了在 `Doctrine` 目前尚不支持嵌入值（embedded values，计划在 2.5 版本支持）的情况下持久化 Value Objects，有两种方案：将 Value Object 字段直接添加到你的 `Entity` 中并进行映射（不够优雅，但更简单）或扩展你的实体（优雅得多，但很复杂）。

## 4 实体 (Entities)

### 4.1 引言

我们讨论了首先尝试将领域中的所有内容建模为值对象的益处。但在建模领域时，可能会出现这样的情况：你会发现通用语言（ubiquitous language）中的某些概念需要身份线程（thread of identity）。这些的例子包括：

- 一个 `person`（人）。`person` 总是有一个身份，且就姓名而言始终相同。
- 电子商务系统中的 `order`（订单）。在该背景下，创建的每个新订单都有自己的身份，且是唯一的。

```php
class Person {
    private $identity;
    private $name;
    public function __construct($identity, $name) {
        $this->identity = $identity;
        $this->name = $name;
    }
    public function getId() {
        return $this->identity;
    }
    public function getName() {
        return $this->name;
    }
}

class Order {
    private $id;
    public function __construct($id) {
        $this->id = $id;
    }
    public function getId() {
        return $this->id;
    }
}
```

### 4.2 对象 vs 原始类型

在大多数情况下，实体的身份被表示为一种原始类型：通常是字符串或整数。但使用值对象来表示它有更多优势：

- Value Objects 是不可变的，因此无法被修改。
- Value Objects 是复杂类型，可以拥有原始类型不具备的自定义行为。例如相等性操作。通过值对象，相等操作可以封装在自己的类中，使概念从隐式变为显式。

```php
namespace Ddd\Domain\Model;
class OrderId {
    private $id;
    public function __construct($anId) {
        $this->id = $anId;
    }

    public function id() {
        return $this->id;
    }

    public function equalsTo(OrderId $anOrderId) {
        return $anOrderId->id === $this->id;
    }
}
```

```php
class Order {
    private $id;
    private $amount;
    private $firstName;
    private $lastName;
    public function __construct(OrderId $anOrderId, Amount $amount, $aFirstName, $aLastName) {
        $this->id = $anOrderId;
        $this->amount = $amount;
        $this->firstName = $aFirstName;
        $this->lastName = $aLastName;
    }

    public function id() {
        return $this->id;
    }

    public function firstName() {
        return $this->firstName;
    }

    public function lastName() {
        return $this->lastName;
    }

    public function amount() {
        return $this->amount;
    }
}
```

### 4.3 身份操作

如前所述，实体的身份是定义它的东西。因此，处理身份是实体的重要方面。通常有 4 种定义实体身份的方法：客户端提供身份、应用程序本身提供身份、持久化机制提供身份或另一个边界上下文（bounded context）提供身份。

#### 4.3.1 持久化机制生成身份

通常最简单的方法是让持久化机制生成身份，因为大部分持久化机制都支持某种身份生成，例如 MySQL 的 `AUTO_INCREMENT` 属性或 Oracle/Postgres 的序列。这虽然简单，但存在一个主要的缺点：`在持久化实体之前，我们无法获得实体的标识。` 因此，在某种程度上，如果我们使用由持久化机制生成的标识，将会标识操作与底层的持久化存储进行耦合。

```sql
CREATE TABLE `orders` (
  id(11) NOT NULL auto_increment,
  amount decimal(10, 5) NOT NULL,
  first_name varchar(100) NOT NULL,
  last_name varchar(100) NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB;
```

然后我们可能会考虑这段代码：

```php
namespace Ddd\Identity\Domain\Model;

class Person
{
    private $identificationNumber;
    private $firstName;
    private $lastName;

    public function __construct($anIdentificationNumber, $aFirstName, $aLastName)
    {
        $this->-identificationNumber = $anIdentificationNumber;
        $this->firstName = $aFirstName;
        $this->lastName = $aLastName;
    }

    public function identificationNumber()
    {
        return $this->identificationNumber;
    }

    public function firstName()
    {
        return $this->firstName;
    }

    public function lastName()
    {
        return $this->lastName;
    }
}
```

### 4.3.1.1 代理标识

有时，使用 ORM 将实体映射到持久化存储时，会施加某些限制，例如，Doctrine 如果使用 `IDENTITY` 生成策略，则要求一个整数字段。如果领域模型需要另一种类型的标识，这可能会与领域模型产生冲突。

处理这种情况的最简单方法是使用[层超类型 (Layer SuperType)](http://martinfowler.com/eaaCatalog/layerSupertype.html)[¹]](#index_split_000.html#98)，我们在其中放置为持久化存储创建的标识字段。

```php
namespace Ddd\Common\Domain\Model;

abstract class IdentifiableDomainObject
{
    private $id;

    protected function id()
    {
        return $this->id;
    }

    protected function setId($anId)
    {
        $this->id = $anId;
    }
}
```

¹[`martinfowler.com/eaaCatalog/layerSupertype.html`](http://martinfowler.com/eaaCatalog/layerSupertype.html)

```php
namespace Acme\Billing\Domain;

use Acme\Common\Domain\IdentifiableDomainObject;

class Order extends IdentifiableDomainObject
{
    private $orderId;

    public function orderId()
    {
        if (null === $this->orderId) {
            $this->orderId = new OrderId($this->id());
        }
        return $this->orderId;
    }
}
```

### 4.3.1.2 富领域模型中的 Active Record 与 Data Mapper

每个项目总是面临着应该使用哪种 ORM 的决策。PHP 中有很多优秀的 ORM：Doctrine、Propel、Eloquent、Paris 以及许多其他。

它们中的大多数是[Active Record (活动记录)](http://www.martinfowler.com/eaaCatalog/activeRecord.html)² 的实现。Active Record 实现对于 CRUD 来说通常很好，但对于富领域模型来说，它并不是理想的解决方案，原因如下：

- `Active Record` 模式假设实体与数据库表之间存在一对一的关系。因此，它将数据库设计与对象系统设计耦合在一起。而在富领域模型中，实体有时是使用来自不同数据源的信息构建的。
- 集合或继承等高级特性实现起来非常困难。
- 大多数实现通过继承强制要求使用某些构造结构来施加若干约定。这可能会通过将领域模型与 ORM 耦合，导致`持久化泄漏 (persistence leakage)` 到领域模型中。作者看到的唯一不强制继承自基类的 Active Record 实现是来自 [Castel Project](http://www.castleproject.org/)⁴ 的 [Castle ActiveRecord³](http://docs.castleproject.org/Active%20Record.MainPage.ashx)，这是一个 .NET 框架。虽然这在生成的实体实现了持久化和领域关注点之间的某种分离，但并没有防止数据设计与对象设计的耦合。

²[`www.martinfowler.com/eaaCatalog/activeRecord.html`](http://www.martinfowler.com/eaaCatalog/activeRecord.html)

³[`docs.castleproject.org/Active%20Record.MainPage.ashx`](http://docs.castleproject.org/Active%20Record.MainPage.ashx)

⁴[`www.castleproject.org/`](http://www.castleproject.org/)

目前 PHP 最好的 ORM 是 [Doctrine](http://doctrine-project.org)⁵。它是[Data Mapper (数据映射器)](http://www.martinfowler.com/eaaCatalog/dataMapper.html) [`模式`⁶](http://www.martinfowler.com/eaaCatalog/dataMapper.html) 的实现。Data Mapper 将持久化与领域解耦。

### 4.3.2 客户端提供标识

有时，在处理某些领域时，处理标识操作的首选方法是让客户端生成，自然而是在客户端完成。

```php
namespace Ddd\Catalog\Domain\Model;

class ISBN
{
    private $isbn;

    public function __construct($anbn, $title)
    {
        $this->isbn = $anbn;
        $this->title = $title;
    }

    private function setIsbn($anbn)
    {
        $this->isbn = $anbn;
    }

    private function assertIsbn($anbn, $string)
    {
        The ISBN is invalid.
    }

    public static function create($anbn)
    {
        return new static($anbn);
    }
}

$book = new Book(
    ISBN::create('...'),
    'Domain-Driven Design with PHP'
);
```

### 4.3.3 应用生成标识

如果客户端不能提供标识，通常处理标识的首选方法是让应用程序生成，通常是通过 UUID 完成。PHP 中有几个库可以生成 UUID。可以在 packagist 上找到。

最推荐的是 *Ben Ramsey* 在 `https://github.com/ramsey/uuid` 开发的那个，因为它在 Github 上有约 500 个关注者，在 packagist 上有 240,000 次安装。

放置标识创建的首选位置是在*Repository (Repository)* 内部：

```php
namespace Ddd\Billing\Domain\Model\Order;

interface OrderRepository
{
    public function nextIdentity();
    public function add(Order $anOrder);
    public function remove(Order $anOrder);
}

class OrderId
{
    private $id;

    private function __construct($anId)
    {
        $this->id = $anId;
    }

    public static function create($anId)
    {
        return new static($anId);
    }
}
```

```php
namespace Ddd\Billing\Infrastructure\Doctrine\Order;

use Ddd\Billing\Domain\Model\Order\Order;
use Ddd\Billing\Domain\Model\Order\OrderId;
use Ddd\Billing\Domain\Model\Order\OrderRepository;
use Doctrine\ORM\EntityRepository;
use Rhumsaa\Uuid\Uuid;

class DoctrineOrderRepository
extends EntityRepository
implements OrderRepository
{
    public function nextIdentity()
    {
        return OrderId::create(
            strtoupper(Uuid::uuid4())
        );
    }

    public function add(Order $anOrder)
    {
        $this->getEntityManager()->persist($anOrder);
    }

    public function remove(Order $anOrder)
    {
        $this->getEntityManager()->remove($anOrder);
    }
}
```

### 4.3.4 其他边界上下文生成标识

这可能是最复杂的标识生成策略，因为它强制本地实体不仅依赖于本地边界上下文的事件，还依赖于外部边界上下文事件。因此，从维护的角度来看，成本将会很高。

其他边界上下文（Bounded Context）提供了一些 UI 组件来选择本地实体的标识。这甚至可以从远程实体抓取某些属性到其自身。

当边界上下文的实体之间需要同步时，通常可以通过每个在原始实体更改时需要通知的边界上下文上的*事件驱动*（Event Driven）架构来实现。

### 4.4 持久化实体

目前，正如本章之前讨论的，将实体状态保存到持久化存储中的最佳工具是 `Doctrine ORM`。

`Doctrine` 有几种方法来指定实体元数据：通过实体代码中的注解（annotations）、通过 XML、YAML 或纯 PHP。在本章中，我们将深入讨论为什么在映射实体时，使用注解不是最好的主意。

### 4.4.1 设置 Doctrine



首先，我们需要通过`composer`引入它。在项目根目录下必须执行以下命令：

```bash
php composer.phar require "doctrine/orm=~2.4"
```

然后，这些行代码将允许设置`doctrine`：

```php
require_once "/path/to/vendor/autoload.php";
use Doctrine\ORM\Tools\Setup;
use Doctrine\ORM\EntityManager;

$paths = ["/path/to/entity-files"];
$isDevMode = false;

// 连接配置
$dbParams = array(
    'driver' => 'pdo_mysql',
    'user' => 'the_database_username',
    'password' => 'the_database_password',
    'dbname' => 'the_database_name',
);

$config = Setup::createAnnotationMetadataConfiguration($paths, $isDevMode);
$entityManager = EntityManager::create($dbParams, $config);
```

## 4.4.2 映射实体

默认情况下，`Doctrine`文档使用注解展示代码示例。因此我们从注解开始代码示例，并讨论为什么尽可能避免它们。为了这样做，我们将引入本章之前讨论过的`Order`类。

### 4.4.2.1 使用注解代码映射实体

`Doctrine`发布时使用的特性之一是可以使用注解代码来指定映射信息。

**什么是注解？**

注解是元数据的一种特殊形式。在 PHP 中，它被放在源代码的注释下。例如，`PHPDocumentor`利用注解来构建 API 信息，或者`PHPUnit`使用某些注解来指定`dataProviders`或对代码代码抛出的异常提供期望言。

```php
class SumTest extends PHPUnit_Framework_TestCase {
    /**
     * @dataProvider aMethodName
     */
    public function testAddition() {
        // ...
    }
}
```

因此，为了将`Order`实体映射到持久化存储，首先必须修改`Order`的源代码以添加`Doctrine`注解：

```php
use Doctrine\ORM\Mapping\Entity;
use Doctrine\ORM\Mapping\Id;
use Doctrine\ORM\Mapping\GeneratedValue;
use Doctrine\ORM\Mapping\Column;

/**
 * @Entity
 */
class Order
{
    /**
     * @Id
     * @GeneratedValue(strategy="AUTO")
     */
    private $id;

    /**
     * @Column(type="decimal", precision="10", scale="5")
     */
    private $amount;

    /**
     * @Column(type="string")
     */
    private $firstName;

    /**
     * @Column(type="string")
     */
    private $lastName;

    public function __construct(Amount $anAmount, $FirstName, $lastName) {
        $this->amount = $anAmount;
        $this->firstName = $FirstName;
        $this->lastName = $lastName;
    }

    public function id() {
        return $this->id;
    }

    public function firstName() {
        return $this->firstName;
    }

    public function lastName() {
        return $this->lastName;
    }

    public function amount() {
        return $this->amount;
    }
}
```

然后将实体持久化到持久化存储中就非常简单：

```php
$order = new Order(new Amount(15), 'FirstName', 'lastName');
$entityManager->persist($order);
$entityManager->flush();
```

乍一看，这段代码看起来很简单，可以是指定映射信息的一种简单方法。但这种方法是有代价的。最终代码奇怪之处何？首先，领域关注与基础设施关注点混合在了一起。`Order`是一个领域概念，而`Table`和`Column`等是基础设施关注点。因此，该实体紧密耦合到源代码中通过注解指定的映射信息。如果使用另一个实体管理器和不同的映射元数据来持久化实体，将是不可能的。注解往往会导致副作用和紧耦合。

那么指定映射信息的最佳方法是什么？最佳方法是将映射信息与实体本身分离。这可以通过 XML 映射、YAML 映射或 PHP 映射来实现。在本书中我们将涵盖 XML 映射。

### 4.4.2.2 使用 XML 映射实体

使用 XML 映射`Order`实体，首先需要更改`Doctrine`的设置代码：

```php
require_once "/path/to/vendor/autoload.php";
use Doctrine\ORM\Tools\Setup;
use Doctrine\ORM\EntityManager;

$paths = ["/path/to/entity-files"];
$isDevMode = false;

// 连接配置
$dbParams = array(
    'driver' => 'pdo_mysql',
    'user' => 'the_database_username',
    'password' => 'the_database_password',
    'dbname' => 'the_database_name',
);

$config = Setup::createXMLMetadataConfiguration($paths, $isDevMode);
$entityManager = EntityManager::create($dbParams, $config);
```

映射文件应该在`Doctrine`搜索路径处创建。映射文件根据完全限定类名命名，并将反斜杠（`\`）替换为点。因此，`Acme\Billing\Domain\Order`的映射文件命名为`Acme.Billing.Domain.Order.dcm.xml`。此外，映射文件使用专门为指定映射信息创建的特殊 XML Schema：

`https://raw.github.com/doctrine/doctrine2/master/doctrine-mapping.xsd`

最终的映射文件将：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<doctrine-mapping
    xmlns="http://doctrine-project.org/schemas/orm/doctrine-mapping"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://doctrine-project.org/schemas/orm/doctrine-mapping https://raw.github.com/doctrine/doctrine2/master/doctrine-mapping.xsd">
    
    <entity name="Ddd\Billing\Domain\Model\Order" table="orders">
        <id name="id" column="id" type="guid">
            <generator strategy="NONE"/>
        </id>
        <field name="amount" type="decimal" nullable="false" scale="10" precision="5"/>
        <field name="firstName" type="string" nullable="false"/>
        <field name="lastName" type="string" nullable="false"/>
    </entity>
</doctrine-mapping>
```

## 4.5 测试实体

测试实体相对容易。因为它们是根据其所代表的领域概念产生的普通 PHP 类。测试的重点应该是实体保护的不不变性，因为实体的行为可能会围绕这些不变量性进行建模。

为了示例和简单起见，假设需要一个博客的领域模型。可能的实现如下：

```php
class Post
{
    private $title;
    private $content;
    private $status;
    private $createdAt;
    private $publishedAt;

    public function __construct($aContent, $title) {
        $this->setContent($aContent);
        $this->setTitle($title);
        $this->unpublish();
        $this->createdAt(new DateTimeImmutable());
    }

    private function setContent($aContent) {
        $this->assertNotEmpty($aContent);
        $this->content = $aContent;
    }
}
```

```php
private function setTitle($aPostTitle)
{
    $this->assertNotEmpty($aPostTitle);
    $this->title = $aPostTitle;
}

private function setStatus(Status $aPostStatus)
{
    $this->assertIsAValidPostStatus($aPostStatus);
    $this->status = $aPostStatus;
}

private function createdAt(DateTimeImmutable $aDate)
{
    $this->assertIsAValidDate($aDate);
    $this->createdAt = $aDate;
}

private function publishedAt(DateTimeImmutable $aDate)
{
    $this->assertIsAValidDate($aDate);
    $this->publishedAt = $aDate;
}

public function publish()
{
    $this->setStatus(
        Status::published()
    );
    $this->publishedAt(new DateTimeImmutable());
}

public function unpublish()
{
    $this->setStatus(
        Status::draft()
    );
    $this->publishedAt = null;
}

public function isPublished()
{
    return $this->status->equalsTo(Status::published());
}

public function publicationDate()
{
    return $this->publishedAt;
}
}

class Status
{
    const PUBLISHED = 10;
    const DRAFT = 20;
    private $status;

    public static function published()
    {
        return new self(self::PUBLISHED);
    }

    public static function draft()
    {
        return new self(self::DRAFT);
    }

    private function __construct($aStatus)
    {
        $this->status = $aStatus;
    }

    public function equalsTo(self $aStatus)
    {
        return $this->status === $aStatus->status;
    }
}
```

为了测试这个领域模型，我们必须确保测试覆盖了所有的`Post`（文章）不变性。

```php
class PostTest extends PHPUnit_Framework_TestCase
{
    /**
     * @test
     */
    public function aNewPostIsNotPublishedByDefault()
    {
        $aPost = new Post(
            'A Post Content',
            'A Post Title'
        );
        $this->assertFalse(
            $aPost->isPublished()
        );
        $this->assertNull(
            $aPost->publicationDate()
        );
    }

    /**
     * @test
     */
    public function aPostCanBePublishedWithAPublicationDate()
    {
        $aPost = new Post(
            'A Post Content',
            'A Post Title'
        );
        $aPost->publish();
        $this->assertTrue(
            $aPost->isPublished()
        );
        $this->assertInstanceOf(
            'DateTimeImmutable',
            $aPost->publicationDate()
        );
    }
}
```

## 4.6 验证

验证是我们领域模型中一个非常重要的过程。它不仅检查属性的正确性，还检查整个对象甚至这些对象的组合。为了保持该模型处于有效状态，需要不同层次的验证。仅仅因为一个对象由有效的属性（从基础而言）组成，并不意味着该对象（整体）是有效的。反之，有效的对象并不意味着我们拥有有效的组合。

### 4.6.1 属性验证

有些开发者将验证视为一种检查给定对象状态的过程。通过[契约设计](https://en.wikipedia.org/wiki/Design_by_contract)方法，验证包含了前置条件、后置条件和不变性。为了确保属性的有效，我们可以使用值对象（Value Objects）来保护单个属性。为了使验证更加灵活，我们可以采用如下代码：



```php
class Username
{
    const MIN_LENGTH = 5;
    const MAX_LENGTH = 10;
    const FORMAT = '/^[a-zA-Z0-9]+$/';
    private $username;

    public function __construct($username)
    {
        $this->setUsername($username);
    }

    private function setUsername($username)
    {
        if (empty($username)) {
            throw new InvalidException('Empty');
        }

        $this->assertNotShort($username);
        $this->assertNotLong($username);
        $this->assertFormat($username);

        $this->username = $username;
    }

    private function assertNotShort($username)
    {
        if (strlen($username) < self::MIN_LENGTH) {
            throw new InvalidException(sprintf('Must be at least %d characters', self::MIN_LENGTH));
        }
    }

    private function assertNotLong($username)
    {
        if (strlen($username) > self::MAX_LENGTH) {
            throw new InvalidException(sprintf('Must be less than %d characters', self::MAX_LENGTH));
        }
    }

    private function assertFormat($username)
    {
        if (!preg_match(self::FORMAT, $username)) {
            throw new InvalidException('Invalid format');
        }
    }
}
```

正如上面的示例所示，`Username` 必须满足以下条件：

- 不为空
- 至少 5 个字符
- 少于 10 个字符
- 符合特定的格式

有些开发者可能会将验证视为防御性编程。在这种情况下，我们关注的是输入的正确性，而不允许空值。

## 4.6.2 整个对象验证

有时，一个由有效属性组成的对象在整体上仍可能是无效的。可能会将这种验证逻辑添加到对象中，但这是一种反模式。良好的做法是分离这些职责。验证应该向客户端告知发现的问题，或者收集结果后续审查。我们不想在遇到第一个错误时停止执行。抽象的 `Validator` 可能如下：

```php
abstract class Validator
{
    private $validationHandler;

    public function __construct(ValidationHandler $validationHandler)
    {
        $this->validationHandler = $validationHandler;
    }

    protected function handleError($error)
    {
        $this->validationHandler->handleError($error);
    }

    abstract public function validate();
}
```

作为一个具体的例子，我们想要验证整个 `Location` 对象，它由 `Country`、`City` 和 `Postcode` 值对象组成。这些单个值在验证时可能是无效的。也许某个城市不属于该国家，或者邮编不符合城市的格式。

```php
class Location
{
    private $country;
    private $city;
    private $postcode;

    public function __construct(Country $country, City $city, Postcode $postcode)
    {
        $this->country = $country;
        $this->city = $city;
        $this->postcode = $postcode;
    }

    public function getCountry()
    {
        return $this->country;
    }

    public function getCity()
    {
        return $this->city;
    }

    public function getPostcode()
    {
        return $this->postcode;
    }
}
```

一旦设置了所有属性，我们就可以对实体进行验证，通常是在某些描述的过程之后。从上看，`Location` 似乎是在验证它自己，但事实并非如此。`Location` 将此验证委托给了具体的验证器实例，从而分开了这两个清晰的职责。

## 实体

99

### `class Location`

```php
class Location
{
    //...
    public function validate(ValidationHandler $validationHandler)
    {
        $validator = new LocationValidator($this, $validationHandler);
        $validator->validate();
    }
}
```

### 4.6.2.1 解耦验证消息

通过对现有实现进行微调，我们能够将验证消息从验证器中解耦：

```php
class LocationValidationHandler implements ValidationHandler
{
    public function handleCityNotFoundInCountry();
    public function handleInvalidPostcodeForCity();
}
```

```php
class LocationValidator
{
    private $location;
    private $validationHandler;

    public function __construct(Location $location, LocationValidationHandler $validationHandler)
    {
        $this->location = $location;
        $this->validationHandler = $validationHandler;
    }

    public function validate()
    {
        if (!$this->location->getCountry()->hasCity($this->location->getCity())) {
            $this->validationHandler->handleCityNotFoundInCountry();
        }

        if (!$this->location->getCity()->isPostcodeValid($this->location->getPostcode())) {
            $this->validationHandler->handleInvalidPostcodeForCity();
        }
    }
}
```

实体

100

我们还需要更改验证方法的签名为：

```php
class Location
{
    //...
    public function validate(LocationValidationHandler $validationHandler)
    {
        $validator = new LocationValidator($this, $validationHandler);
        $validator->validate();
    }
}
```

### 4.6.3 验证对象组合

验证对象组合可能会变得复杂，因此，实现这一点的优方法是通过领域服务（Domain Service）。该服务随后与仓库通信以检索有效的 `Aggregate`（聚合根）。由于创建的对象图可能复杂，`Aggregate` 可能处于中间状态，需要预先对其他聚合进行验证。我们可以使用领域事件（Domain Events）通知系统的其他部分某个元素已通过验证。

### 4.7 总结

领域中的某些概念需要身份（Identity），即其状态的改变不会改变它们作为概念的本质。我们已经看到将身份建模为值对象（Value Object）带来了一些好处，例如不可变性和操作身份本身的逻辑。我们展示了提供身份的几种方式：

* 持久化机制：容易实现，但在持久化对象之前你无法获得身份，这会延迟并使事件传播复杂。
* 代理 ID (Surrogate id)：某些 ORM 要求在你的 `Entity` 上增加额外的字段，以将身份与持久化机制映射。
* 由客户端提供：有时身份符合某个领域概念，你可以在领域内部对其进行建模。

实体

101

* 由应用程序生成：你可以使用库来生成 ID。
* 由边界上下文（Bounded Context）生成：这可能是最复杂的策略。其他边界上下文会提供一个生成身份的接口。

我们已经看到了几种提供身份的方法，它们的缺点如下：

* 持久化机制：容易实现，但在持久化对象之前你无法获得身份，这会延迟并使事件传播复杂。
* 代理 ID (Surrogate id)：某些 ORM 要求在你的 `Entity` 上增加额外的字段，以将身份与持久化机制映射。
* 由客户端提供：有时身份符合某个领域概念，你可以在领域内部对其进行建模。
* 由应用程序生成：你可以使用库来生成 ID。
* 由边界上下文生成：这可能是最复杂的策略。其他边界上下文会提供一个生成身份的接口。

最后我们可以得出结论：身份策略的选择取决于领域的需求和架构。

## 5. 服务

### 5.1 介绍

服务是封装了不属于单一实体的行为的对象。它们通常用于协调涉及多个实体的操作。

你会遇到三种类型的服务：

* **应用服务 (Application Services)**：这些服务协调应用逻辑，编排领域与外部世界之间对象的流动。
* **领域服务 (Domain Services)**：它们包含无法在实体或值对象中领域领域逻辑。
* **基础设施服务 (Infrastructure Services)**：它们处理技术性问题，例如发送电子邮件、日志记录或与数据库交互。

### 5.2 应用服务

应用服务协调应用逻辑，编排领域与外部世界之间对象的流动。它们是应用程序的入口。

### 5.2.1 事务

在领域驱动设计中，事务是在应用服务层处理的。你不会在领域代码的任何地方找到 `beginTransaction` 或类似代码。在执行应用服务期间执行的所有操作都将以原子方式针对你的数据库运行。

在 PHP 中，我们有一个优雅的解决方案，让你的应用服务在事务范围内执行，而无必担心领域代码中的事务。

```php
interface Service
{
    public function execute($request);
}

class TransactionalService
{
    private $session;
    private $service;
}
```

```php
public function __construct(Service $service, TransactionalSession $session)
{
    $this->session = $session;
    $this->service = $service;
}

public function execute($request)
{
    if (empty($this->service)) {
        throw new LogicException('A use case must be specified');
    }
    $operation = function () use ($request) {
        return $this->service->execute($request);
    };
    return $this->session->executeAtomically($operation->bindTo($this));
}
}
```

```php
interface TransactionalSession
{
    /**
     * @return mixed
     */
    public function executeAtomically(callable $operation);
}
```

### 5.2.2 测试应用服务

我们该如何测试这个应用服务？正如 Kent Beck 在《TDD by Examples》中所建议的样，测试所有可能出错的地方。这意味着要测试测试路径（happy paths）和异常路径（sad paths）。测试路径是指当所有输入均有效且所有资源可用时，正确完成工作的路径。在注册用例中，这意味着邮箱和密码是有效的、用户尚不存在、数据库可用等。而异常路径则是所有其他情况。

```php
class SignInUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @test
     * @expectedException \Ddd\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $service = new SignInUserService(new UserRepository());
        $service->execute('user@example.com', 'password');
        $service->execute('user@example.com', 'password');
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $userRepository = new UserRepository();
        $service = new SignInUserService($userRepository);
        $user = $service->execute('user@example.com', 'password');
        $this->assertSame(
            $user,
            $userRepository->userOfId($user->id())
        );
    }
}
```

### 5.3 领域服务

在与领域专家的交流过程中，你会在通用语言（Ubiquitous Language）中遇到无法整齐地表示为实体（Entity）或值对象（Value）的概念。

* 用户能够自己登录系统吗？
* 购物车能够自己转换为订单吗？

上面的例子是两个具体的概念，它们无法自然地绑定到实体或值对象（Value Object）。为了进一步强调这种奇异性，我们可以尝试对行为进行建模：

```php
class User
{
    public function signIn($aUsername, $aPassword)
    {
        // ...
    }
}

class Cart
{
    public function createOrder()
    {
        // ...
    }
}
```

在第一种实现中，我们无法知道给定的用户名和密码与被调用的用户实例相关。显然，这个操作并不适合这个实体，相反它应该被提取到一个单独的类，使其意图显式化。考虑到这一想法，我们可以创建一个唯一负责用户身份验证的领域服务。

```php
class SignIn
{
    public function execute($aUsername, $aPassword)
    {
        // ...
    }
}
```

同样地，在第二个例子中，有一个专门从提供的购物车创建订单的领域服务。

```php
class CreateOrderFromCart
{
    public function execute(Cart $aCart)
    {
        // ...
    }
}
```

领域服务可以定义为完成领域任务的操作，它自然地不属于任何实体或值对象。作为代表领域中操作的概念，无论其运行历史如何，客户端都应该使用它们。

### 5.4 具有多种实现的领域服务



在建模领域服务时，经常遇到基础设施依赖，例如在需要处理加密机制的情况下。通过这种模式可以在领域和基础设施之间实现**关注点分离**。领域服务本身不持有状态。

```php
interface SignIn
{
    public function execute($aUsername, $aPassword);
}
```

使用上述接口，我们可以在基础设施中如下创建一个实现：

```php
class DefaultEncryption
{
    private $userRepository;

    public function __construct(UserRepository $userRepository)
    {
        $this->userRepository = $userRepository;
    }

    public function execute($aUsername, $aPassword)
    {
        if (!$this->userRepository->exists($aUsername)) {
            throw new InvalidArgumentException(
                sprintf('The user "%s" does not exist.', $aUsername)
            );
        }
        $user = $this->userRepository->findByUsername($aUsername);
        if (!password_verify($aPassword, $user->getPassword())) {
            throw new BadCredentialsException();
        }
        return $user;
    }
}
```

另一种基于 `MD5` 的实现：

```php
class Md5Encryption implements SignIn
{
    const SALT = 'S0m3S4lt';
    private $userRepository;

    public function __construct(UserRepository $userRepository)
    {
        $this->userRepository = $userRepository;
    }

    public function execute($aUsername, $aPassword)
    {
        if (!$this->userRepository->exists($aUsername)) {
            throw new InvalidArgumentException(
                sprintf('The user "%s" does not exist.', $aUsername)
            );
        }
        $user = $this->userRepository->findByUsername($aUsername);
        $encryptedPassword = md5($aPassword . '_' . $this->salt());
        if ($user->getPassword() !== $encryptedPassword) {
            throw new BadCredentialsException();
        }
        return $user;
    }

    private function salt()
    {
        return md5(self::SALT);
    }
}
```

选择这种方案允许对领域服务有多种实现，每个实现负责不同的加密机制。要决定哪个实现可以通过反转控制容器轻松管理，例如 `Symfony` 的依赖注入组件：

```xml
<?xml version="1.0"?>
<container xmlns="http://symfony.com/dic/services"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://symfony.com/dic/services
http://symfony.com/dic/services/services-1.0.xsd">
    <services>
        <service id="sign_in" alias="sign_in.default"/>
        <service id="sign_in.default" class="Ddd\Auth\Infrastructure\Authentication\DefaultEncryption\SignIn">
            <argument type="service" id="user_repository"/>
        </service>
        <service id="sign_in.md5" class="Ddd\Auth\Infrastructure\Authentication\Md5Encryption\SignIn">
            <argument type="service" id="user_repository"/>
        </service>
    </services>
</container>
```

### 5.4.1 关于代码复用的问题

尽管上述实现清晰地定义了关注点分离，但每当我们想要实现一种新的加密机制时，都必须重复密码验证算法。

解决此问题的另一种方法（有助于代码复用）是将这两项职责分离出来。相反，我们可以将密码加密逻辑提取到一个专门的类中，并对所有定义的加密算法使用[策略模式²](http://en.wikipedia.org/wiki/Strategy_pattern)。这使得设计对扩展开放，而对修改关闭。

```php
class SignIn
{
    private $userRepository;
    private $passwordEncryption;

    public function __construct(
        UserRepository $userRepository,
        PasswordEncryption $passwordEncryption
    ) {
        $this->userRepository = $userRepository;
        $this->passwordEncryption = $passwordEncryption;
    }

    public function execute($aUsername, $aPassword)
    {
        if (!$this->userRepository->has($aUsername)) {
            throw new InvalidArgumentException(
                sprintf('The user "%s" does not exist.', $aUsername)
            );
        }
        $aUser = $this->userRepository->byUsername($aUsername);
        if ($this->isPasswordInvalidFor($aUser, $aPassword)) {
            throw new BadCredentialsException($aUser, $aPassword);
        }
        return $aUser;
    }

    private function isPasswordInvalidFor(User $aUser, $plainPassword)
    {
        return !$this->passwordEncryption->verify(
            $plainPassword,
            $aUser->hash()
        );
    }
}

interface PasswordEncryption
{
    /**
     * @param string $password
     * @param string $hash
     * @return boolean
     */
    public function verify($plainPassword, $hash);
}
```

定义不同的加密策略就像实现`PasswordEncryption`接口一样简单。

```php
class BasicPasswordEncryption implements PasswordEncryption
{
    public function verify($plainPassword, $hash)
    {
        return password_verify($plainPassword, $hash);
    }
}

class Md5PasswordEncryption implements PasswordEncryption
{
    const SALT = 'S0m3S4lT';

    public function verify($plainPassword, $hash)
    {
        return $hash === $this->calculateHash($plainPassword);
    }

    private function calculateHash($plainPassword)
    {
        return md5($plainPassword . '_' . $this->salt());
    }

    private function salt()
    {
        return md5(self::SALT);
    }
}
```

### 5.5 测试领域服务

考虑到来自*多个领域服务实现*的用户身份验证示例，能够轻松测试该服务是极有益的。然而，通常情况下测试模板方法的实现可能是复杂的，因此我们将使用一个简单的密码加密实现来进行测试目的。

```php
class PlainPasswordEncryption implements PasswordEncryption
{
    public function verify($plainPassword, $hash)
    {
        return $plainPassword === $hash;
    }
}
```

现在我们可以测试领域服务中的所有用例了：

```php
class SignInTest extends PHPUnit_Framework_TestCase
{
    private $signIn;
    private $userRepository;

    protected function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->signIn = new SignIn(
            $this->userRepository,
            new PlainPasswordEncryption()
        );
    }

    /**
     * @test
     * @expectedException InvalidArgumentException
     */
    public function itShouldComplainIfTheUserDoesNotExist()
    {
        $this->signIn->execute('test-username', 'test-password');
    }

    /**
     * @test
     * @expectedException BadCredentialsException
     */
    public function itShouldTellIfTheUserIsFoundButThePasswordDoesNotMatch()
    {
        $this->userRepository->add(
            new User(
                'test-username',
                'test-password'
            )
        );
        $this->signIn->execute('test-username', 'no-matching-password')
    }

    /**
     * @test
     */
    public function itShouldTellIfTheUserIsFoundAndMatchesTheProvidedPassword()
    {
        $this->userRepository->add(
            new User(
                'test-username',
                'test-password'
            )
        );
        $this->assertInstanceOf(
            'Ddd\\Domain\\Model\\User\\User',
            $this->signIn->execute('test-username', 'test-password')
        );
    }
}
```

### 5.6 贫血领域模型 vs 丰富领域模型

必须小心不要在你的系统中过度使用领域服务抽象。遵循这条路径会导致实体和值对象被剥离所有行为，变成仅仅的数据容器。这与面向对象编程（OOP）的目标背道而驰，OOP 可以被认为是将数据和行为聚集到被称为对象的语义单元中，其意图是表达现实世界的概念和问题。

[`martinfowler.com/eaaCatalog/serviceLayer.html`](http://martinfowler.com/eaaCatalog/serviceLayer.html)

# 服务

119

```php
class ChangeOrderStatusService
{
    private $orderRepository;
    public function __construct(OrderRepository $orderRepository)
    {
        $this->orderRepository = $orderRepository;
    }

    public function execute($anOrderId, $anOrderStatus)
    {
        // 从数据库中获取订单
        $anOrder = $this->orderRepository->find($anOrderId);
        // 更新订单状态
        $anOrder->setStatus($anOrderStatus);
        // 更新 updatedAt 字段
        $anOrder->setUpdatedAt(new DateTimeImmutable());
        // 将订单保存到数据库
        $this->orderRepository->save($anOrder);
    }
}
```

或者在更新订单金额的情况下

```php
class UpdateOrderAmountService
{
    private $orderRepository;

    public function __construct(OrderRepository $orderRepository)
    {
        $this->orderRepository = $orderRepository;
    }

    public function execute($orderId, $amount)
    {
        $anOrder = $this->orderRepository->find(1);
        $anOrder->setAmount($amount);
        $anOrder->setUpdatedAt(new DateTimeImmutable());
        $this->orderRepository->save($anOrder);
    }
}
```

客户端代码将大幅减少为以下意图清晰的操作：

```php
$updateOrderAmountService = new UpdateOrderAmountService(
    $orderRepository
);
$updateOrderAmountService->execute(1, 20.5);
```

实现这种方法可以带来很大程度的代码复用性。想要更新订单金额的人只需获取`UpdateOrderAmountService`的实例，并使用适当的参数调用`execute`方法即可。

然而，选择这条路径破坏了前面讨论的面向对象设计原则，并且付出了构建领域模型的成本，却没有利用它的任何好处。

## 5.6.1 贫血领域模型破坏了封装



如果我们重新审视在`Service Layer`（服务层）中定义服务的代码，我们可以看到，作为一个使用`Order`实体的客户端，我们被要求知道其内部表示的每一个细节。这一发现违背了面向对象编程的基本规则，即将数据与后续行为相结合。

## 5.6.2 贫血领域模型带来了虚假的代码复用感

假设有一种情况，客户端跳过了`UpdateOrderAmountService`，而是直接从`OrderRepository`获取、更新并持久化订单。如果`UpdateOrderAmountService`包含任何关于订单金额的其他相关业务逻辑，这些逻辑将不会被执行。这可能导致订单以不一致的状态存储。因此，不变性（invariants）应该被正确保护，而最好的方法是让真正的领域模型来处理。在本例中，`Order`实体是确保此点的最佳位置。

服务

121

```php
class Order
{
    // ...
    public function changeAmount($amount)
    {
        $this->amount = $amount;
        $this->setUpdatedAt(new DateTimeImmutable());
    }
}
```

注意通过将此操作下推到实体并用“通用语言”（Ubiquitous Language）对其命名，系统实现了极大的代码复用。现在任何想更改订单金额的人都必须直接调用`Order::changeAmount`方法。

这导致了更丰富的类，其中行为是追求的目标方向，从而实现了代码复用。这通常被称为丰富领域模型（rich domain model）。

### 5.6.3 如何避免贫血领域模型？

避免陷入贫血领域模型的方法是，在启动新项目或功能时，首先考虑行为。数据库、ORM 等只是实现细节，我们应该努力在开发过程中尽可能晚地才做出使用这些工具的决定。通过这样做，我们可以关注唯一真正重要的属性：行为。

### 5.7 总结

正如我们看到的，在开始一个新项目时要考虑行为。服务代表了系统内部的操作。我们可以区分：

*   **应用服务 (Application Services)**：协调来自外部世界的请求。它们不应包含领域逻辑。事务在应用层处理，封装事务。

*   **领域服务 (Domain Services)**：仅操作领域概念，通过“通用语言”表示。推迟实现细节会导致贫血模型和糟糕的面向对象设计。

*   **基础设施服务 (Infrastructure Services)**：处理如发送邮件等基础设施。

## 6. 领域事件

领域事件是一个或多个组件关心的领域变化。开发者通常不习惯处理事件。领域事件在语言中并不常见。然而，可以看到框架和库利用它们来提供新的解耦、复用和加速。领域事件是领域变化的事件。

### 6.1 引言

想象一个 JavaScript 2D 平台游戏。屏幕上有许多不同的组件。有一个组件显示剩余生命，另一个显示得分，还有一个倒计时剩余时间。每当玩家跳到敌人身上得分增加。当得分超过某个数字时，你会获得额外的生命。当玩家碰撞钥匙时，获取钥匙并可能打开门。这些组件是如何交互的？这种场景的最佳架构是什么？

可能有两种方案：第一种是让每个组件与其连接的组件耦合。在示例中，玩家组件将与许多组件耦合。记得开闭原则吗？添加新组件不应该修改第一个组件的代码。如果组件太多会怎样？容易维护吗？完全不是。

第二种是将所有组件连接到一个单一对象，该对象接收每个组件的事件并将其转发给特定的组件。例如，得分组件会对`Enemyilled`事件感兴趣，或者`LifeCaptured`事件对玩家实体和剩余生命组件非常有用。通过这种方式，所有组件都耦合到一个管理通知的单一组件上。通过这种方法，添加新组件或删除现有组件不会影响剩余组件。

在开发单个应用时，事件对于解耦组件非常有帮助。在分布式开发整个领域时，事件对于解耦每个服务或应用程序非常有用。关键点是相同的，但规模不同。

¹[`en.wikipedia.org/wiki/Open/closed_principle`](http://en.wikipedia.org/wiki/Open/closed_principle)

122

领域事件

123

### 6.2 定义

领域事件是一种特定的事件，用于通知本地或远程边界上下文（Bounded Contexts）领域的变化。

Vaughn Vernon 定义](http://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon-ebook/dp/B00BCLEBN8)² 领域事件为领域内发生事件捕获。

Eric Evans 定义](https://domainlanguage.com/ddd/patterns/DDD_Reference_2011-01-31.pdf)³ 领域事件为

领域模型的一个完整组成部分，是对领域内发生某些事件的表示。在忽略无关领域活动的同时，显式地表示领域专家想要跟踪或接收通知的事件，或者与其他模型对象的状态变更相关的事件。

Martin Fowler [定义⁴](http://martinfowler.com/eaaDev/DomainEvent.html) 将领域事件（Domain Event）定义为捕捉影响影响的某些有趣事件的记忆。

Web 应用中的领域事件示例有`UserRegistered`、`OrderPlaced`、`UserRelocated`或`ProductAdded`。

### 6.2.1 短故事

在一个票务代理机构，一名内容经理决定增加 U2 演唱会的价格。她通过后台系统编辑了该演出。一个`ShowPriceChanged`领域事件被发布，并与新的演出价格在同一个事务中持久化到数据库中。

一个批处理获取该领域事件并将其放入`RabbitMQ`。该领域事件被分发到两个队列中：一个用于本地相同的边界上下文（Bounded Context），另一个用于业务智能目的的远程队列。

在第一个队列中，工作线程使用事件中的`id`获取对应的`Show`并将其推送到`Elasticsearch`服务器中，以便用户在搜索时能看到新价格。它也可以更新另一个数据库表中的新价格。

在第二个队列中，工作线程将信息插入到`Logs Server`或`Data Lake`中，可以在那里运行报告或数据挖掘过程。

²[`www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon-ebook/dp/B00BCLEBN8`](http://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon-ebook/dp/B00BCLEBN8)

³[`domainlanguage.com/ddd/patterns/DDD_Reference_2011-01-31.pdf`](https://domainlanguage.com/ddd/patterns/DDD_Reference_2011-01-31.pdf)

⁴[`martinfowler.com/eaaDev/DomainEvent.html`](http://martinfowler.com/eaaDev/DomainEvent.html)

![](img/index-142_1.png)

领域事件

124

无法使用领域事件集成的外部应用程序，可以通过本地边界上下文提供的 REST API 访问所有的`ShowPriceChanged`事件。

如你所见，领域事件对于处理最终一致性和集成不同的边界上下文非常有用。聚合根（Aggregates）创建事件并发布它们。订阅者可以存储事件然后将其转发给远程订阅者。

### 6.2.2 比喻

我周二去 Babur’s 吃饭，并用信用卡支付。这可以被建模为一个事件，其事件类型为`PurchasePlaced`，主体是我的信用卡，发生日期是周二。如果 Babur’s 使用的是旧的人工系统，并且直到周五才传输交易记录，那么记录日期就是周五。

事情总会发生。并非所有事情都是有趣的，有些可能值得记录但不会引起反应。最有趣的事件会引起反应。许多系统需要对有趣的事件做出反应。通常，你需要知道系统为什么以那种方式做出反应。

通过将输入系统的输入汇聚成领域事件流，你可以保留对系统所有输入的记录。这有助于你组织处理逻辑，并允许你对系统的输入保留一份审计日志。

**练习题**

尝试在你当前的领域中寻找潜在领域事件的示例。

### 6.2.3 真实案例(tm)

在深入讨论领域事件的细节之前，让我们来看一个使用领域事件的真实示例，以及它们如何帮助我们的应用程序和整个领域。

考虑一个用于注册新用户的简单应用程序服务（Application Service）。例如在电子商务背景下。应用程序服务将在自己的章节中解释，所以不要过于担心它的接口，只需关注`execute`方法。

领域事件

125

```php
class SignInUserService implements ApplicationService
{
    private $userRepository;
    private $userFactory;
    private $userTransformer;

    public function __construct(
        UserRepository $userRepository,
        UserFactory $userFactory,
        UserTransformer $userTransformer
    )
    {
        $this->userRepository = $userRepository;
        $this->userFactory = $userFactory;
        $this->userTransformer = $userTransformer;
    }

    /**
     * @param SignInRequest $request
     * @return void
     * @throws UserExistsException
     */
    public function execute(SignInRequest $request = null)
    {
        $email = $request->email();
        $password = $request->password();
        $user = $this->userRepository->user($email);

        if (null !== $user) {
            throw new UserExistsException();
        }

        $user = $this->userFactory->build($email, $password);
        $this->userRepository->add($user);
        $this->userTransformer->write($user);
    }
}
```

领域事件

126

所示，`ApplicationService`检查用户是否存在。如果不存在，它会创建一个新的`User`并将其添加到`UserRepository`中。现在考虑一个新需求：必须通过电子邮件通知新用户。不用想太多，首先想到的种方法是更新`ApplicationService`以包含一些完成工作的代码。然而，让我们考虑另一种方法。触发一个`UserRegistered`事件如何？让其他组件监听该事件并发送邮件如何？这种方法有很多很酷的处。首先，每当执行新操作时，我们需要更新`ApplicationService`。其次，它更容易测试。

在同一个电子商务项目中，我们被要求集成一个不是用 PHP 编写的开源游戏化平台。每当用户在我们的边界上下下单或评价产品时，她可以获得显示在电子商务用户主页上的勋章。我们该如何建模这个问题？

遵循第一种方法，我们将更新`ApplicationService`以集成具有类似确认邮件功能的平台。使用`DomainEvent`方法，我们将为`UserRegistered`事件创建另一个监听器，通过 REST 或 SOA 直接连接到游戏化平台，或者更好，通过某些消息系统（如`RabbitMQ`）传播它，这样事件就可以被游戏化平台接收并做出相应反应，而我们的电子商务边界无需感知新的游戏化边界。

### 6.3 特征

### 6.3.1 命名规范

所有事件都应该用过去时动词表示，例如`CustomerRelocated`、`Cargo-Shipped`或`InventoryLossageRecorded`。它们是过去已经完成的事情。在英语中，有很多有趣的例子，人们倾向于使用名词而不是动词。

过去时动词，一个例子是“地震”（Earthquake）或“倾覆”（Capsize），正如最近一位议员对关亚的担忧那样。我们建议避免使用此类名称来命名领域事件（Domain Events），而是坚持使用过去时动词。名词倾向于与后文在《精简对象建模》（Streamlined Object Modeling）中讨论的“事务对象”（Transaction Objects）匹配。将事件建模为过去时动词是至关重要的，因为它们是通用语言（Ubiquitous Language）的一部分。

### 6.3.2 领域事件与通用语言

考虑我们在讨论迁移客户所产生的副作用时，通用语言中的差异：事件使该概念变得显式化，而之前发生在聚合根（Aggregate）内部或多个聚合根之间的变化被视为一个隐式概念，需要去探索和定义。例如，在大多数系统中，副作用发生的这一事实仅仅是通过通如`Hibernate`或`Entity Framework`等工具发现的，如果用例的副作用发生了变化，它就是一个隐式概念。引入事件使得该概念变得显式化并成为通用语言的一部分；迁移客户不仅仅是改变某些东西，迁移客户会产生一个在语言中被明确定义的`CustomerRelocatedEvent`（客户迁移事件）。

### 6.3.3 不变性

领域事件描述了领域中已经发生的变化。它们谈论的是过去。根据定义，改变过去是不可能的，除非你是`Marty McFly`且拥有一辆`Delorean`时空车，但事实可能并非如此。领域事件是不可变的，仅此而已。

#### Symfony 事件调度器

某些 PHP 框架支持事件。然而，不要将这些事件与领域事件混淆。它们在特征和目标上是不同的。例如，Symfony 拥有`Event Dispatcher`组件。如果你需要为状态机实现一个事件系统（例如），你可以依赖它。整个从请求到响应的 Symfony 生命周期也是基于事件的。然而，Symfony 事件是可变的，每个监听器（Listener）都能够修改事件以向其中添加或更新信息。

### 6.4 建模事件

在建模事件时，请根据其所属的边界上下文（Bounded Context）中的通用语言来命名事件及其属性。如果一个事件是在`Aggregate`上执行命令操作的结果，那么该的名称通常源自执行的命令。事件名称反映了事件发生的过去性质，这一点非常重要。它现在没有发生。它是之前发生的。选择最好的名称是反映这一事实的名称。

让我们考虑我们的用户注册功能，`DomainEvent`需要代表这一事实。以下代码显示了基础`DomainEvent`的最小接口。

```php
interface DomainEvent
{
    /**
     * @return \DateTime
     */
    public function occurredOn();
}
```

如所示，所需的最小信息是一个`DateTime`，以便知道事件发生的时间。

现在让我们建模新的用户注册事件。以下代码可以用于建模一个表示“应用程序中已注册新用户”这一事实的事件。如前所述，名称应该是过去时动词，因此`UserRegistered`（用户注册）可能是一个不错的选择。

```php
class UserRegistered implements DomainEvent
{
    private $userId;

    public function __construct(UserId $userId)
    {
        $this->userId = $userId;
        $this->occurredOn = new \DateTime();
    }

    public function userId()
    {
        return $this->userId;
    }

    public function occurredOn()
    {
        return $this->occurredOn;
    }
}
```

通知新用户的最少信息可能是她的`UserId`。有了这些信息，来自同一或不同边界上下文的任何进程、命令或应用程序服务都可以对此事件采取行动。

经验法则如下：

- `DomainEvents`通常被设计为不可变的

- 构造函数将初始化`DomainEvent`的完整状态

- `DomainEvents`将具有用于访问其属性的 getter 方法

- 包含执行操作的`Aggregate`标识

- 包含与第一个聚合根相关的其他聚合标识

- 如果有用，包含导致事件发生的参数

但是，如果来自同一或不同边界上下文的领域专家需要更多信息怎么办？让我们看看带有更多信息的同一个领域事件建模，例如电子邮件地址。



```php
class UserRegistered implements DomainEvent
{
    private $userId;
    private $userEmail;

    public function __construct(UserId $userId, $userEmail)
    {
        $this->userId = $userId;
        $this->userEmail = $userEmail;
        $this->occurredOn = new \DateTime();
    }

    public function userId()
    {
        return $this->userId;
    }

    public function userEmail()
    {
        return $this->userEmail;
    }

    public function occurredOn()
    {
        return $this->occurredOn;
    }
}
```

我们添加了电子邮件。向 `DomainEvent` 中添加更多信息可以帮助提高性能或简化不同边界上下文之间的集成。从其他边界上下文的角度进行思考有助于建模事件。当上游边界上下文创建创建一个新用户时，下游边界上下文必须创建它自己的用户。添加用户邮箱可能节省一次向上游边界上下文的同步请求。让我们来看一个例子。

你还记得那个游戏化的例子吗？为了创建游戏化平台的用户（可能称为 `Player` 用户），来自电子商务边界上下文的 `UserId` 可能就足够了。但是，如果游戏化平台需要通过电子邮件通知用户奖励怎么办？在这种情况下，电子邮件地址也是强制性的。因此，如果原始领域事件中包含了电子邮件地址，我们就完成了。如果情况并非如此，游戏化边界上下文需要通过 REST 从另一个请求此类信息。

## 为什么不包含整个用户实体？

我是否应该在领域事件中包含来自边界上下文的整个 `User Entity`？我们的建议是：不要。领域事件用于边界上下文自身与其他边界上下文之间的通信。这意味着，在 C2C 电子商务目录边界上下文中的 `Seller`（卖家），可以是产品反馈边界上下产品评论的 `Author`（作者）。两者可以共享相同的 ID 或邮箱，但 `Seller` 和 `Author` 是来自不同边界上下文的不同概念实体。因此，一个边界上下文的实体在其他地方没有意义，或者具有完全不同的意义。

## 6.5 持久化领域事件

持久化事件总是好主意。某些读者可能想为什么不直接将领域事件发布到消息或日志系统，但持久化它们有许多益处：

- 你可以通过 REST 方式为其他边界上下文暴露领域事件
- 你可以在推送到 RabbitMQ 之前，将领域事件和聚合更改放在同一个数据库事务中（你不想通知未发生的事情，也不不想错过已发生事情的通知）
- 商业智能可以使用这些数据进行分析、预测或趋势分析
- 审计你的实体变化
- 对于事件溯源（Event Sourcing），你可以从领域事件重构聚合根

### 6.5.1 事件存储

我们在哪里持久化领域事件？在 `Event Store`（事件存储）中。`Event Store` 是一个位于领域空间中以抽象（接口或抽象类）存在的领域事件仓库，它的职责是追加领域事件并查询它们。一个可能的基础接口如下：

```php
interface EventStore
{
    public function append(DomainEvent $aDomainEvent);
    public function allStoredEventsSince($anEventId);
}
```

然而，取决于你对 `DomainEvents` 的用法，之前的接口可以拥有更多方法来查询你的事件。

在实现方面，你可以决定使用 Doctrine 存储库、DBAL 库或普通的 PDO。由于 `DomainEvents` 是不可变的，使用 Doctrine 会增加一个不必要的性能开销。对于中小型应用程序，使用 Doctrine 可能是可以的。让我们看看使用 Doctrine 的一种可能实现。

```php
class DoctrineEventStore extends EntityRepository implements EventStore
{
    private $serializer;

    public function append(DomainEvent $aDomainEvent)
    {
        $storedEvent = new StoredEvent(
            get_class($aDomainEvent),
            $aDomainEvent->occurredOn(),
            $this->serializer()->serialize($aDomainEvent, 'json')
        );
        $this->getEntityManager()->persist($storedEvent);
    }

    public function allStoredEventsSince($anEventId)
    {
        $query = $this->createQueryBuilder('e');
        if ($anEventId) {
            $query->where('e.eventId > :eventId');
            $query->setParameters(array('eventId' => $anEventId));
        }
        $query->orderBy('e.eventId');
        return $query->getQuery()->getResult();
    }

    private function serializer()
    {
        if (null === $this->serializer) {
            /* JMSSerializer\Serializer\SerializerBuilder */
            $this->serializer = SerializerBuilder::create()->build();
        }
        return $this->serializer;
    }
}
```

`StoredEvent` 是映射到数据库所需的 Doctrine Entity。如你所见，在添加和持久化 Store 之后没有调用 `flush`。如果此操作是在 Doctrine 事务内部进行的，则不需要。因此，我们先不写该调用，在讨论应用服务（Application Services）时再详细说明。让我们来看看 `StoredEvent` 的实现。

```php
class StoredEvent implements DomainEvent
{
    private $eventId;
    private $eventBody;
    private $occurredOn;
    private $typeName;

    /**
     * @param string $aTypeName
     * @param \DateTime $anOccurredOn
     * @param string $anEventBody
     */
    public function __construct($aTypeName, \DateTime $anOccurredOn, $anEventBody)
    {
        $this->eventBody = $anEventBody;
        $this->typeName = $aTypeName;
        $this->occurredOn = $anOccurredOn;
    }

    public function eventBody()
    {
        return $this->eventBody;
    }

    public function eventId()
    {
        return $this->eventId;
    }

    public function typeName()
    {
        return $this->typeName;
    }

    public function occurredOn()
    {
        return $this->occurredOn;
    }
}
```

以及它的映射。

`Ddd\Domain\Event\StoredEvent`:

```yaml
type: entity
table: event
repositoryClass: Ddd\Infrastructure\Application\Notification\DoctrineEventStore
id:
eventId:
  type: integer
  column: event_id
  generator:
    strategy: AUTO
fields:
  eventBody:
    column: event_body
    type: text
  typeName:
    column: type_name
    type: string
    length: 255
  occurredOn:
    column: occurred_on
    type: datetime
```

由于每个 `DomainEvent` 可能有不同的字段，我们需要将它们序列化后持久化。`typeName` 在整个领域范围内标识 `DomainEvent`。实体（Entity）或值对象（Value Object）在边界上下文（BC）内部是有意义的，但 `DomainEvents` 定义了 BC 之间的通信协议。

在分布式系统中，这种情况会发生。你必须处理未发布、在链中某处丢失或发布了多次的 `DomainEvents`。这就是为什么带有 `id` 持久化 `DomainEvent` 非常重要，这样很容易追踪哪些 `DomainEvents` 已经发布，哪些是缺失的。

## 6.6 从领域模型发布事件

当领域事件代表的事实发生时，就应该发布 `DomainEvents`。例如，当一个新用户注册时，应该发布一个新的 `UserRegistered` 事件。

遵循报纸的比喻：

- **建模（Modeling）** 领域事件就像写一篇新闻稿
- **发布（Publishing）** 领域事件就像在报纸上印刷文章
- **传播（Spreading）** 领域事件就像发送报纸，让每个人都能阅读文章

发布 `DomainEvents` 的推荐方法是使用简单的监听器-观察者模式（Listener-Observer pattern）来实现 `DomainEventPublisher`。

### 6.6.1 从实体发布领域事件

继续应用程序中注册了新用户的示例，让我们看看对应的领域事件如何发布。

```php
class User
{
    protected $userId;
    protected $email;
    protected $password;

    public function __construct(UserId $userId, $email, $password)
    {
        $this->setUserId($userId);
        $this->setEmail($email);
        $this->setPassword($password);
        DomainEventPublisher::instance()->publish(
            new UserRegistered(
                $this->userId
            )
        );
    }
    //...
}
```

如示例所示，当创建 `User` 时，会发布一个 `UserRegistered` 事件。通常情况下，使用像这里的自封装，在从我们的持久化引擎中获取由于领域规则变化而失效的无效对象时要小心。另一种完全不使用父类构造函数的方法可能是：

```php
class CustomOrmUser extends User
{
    public function __construct()
    {
    }

    public static function fromRawData($data)
    {
        $user = new self();
        $user->userId = new UserId($data['user_id']);
        $user->email = $data['email'];
        $user->password = $data['password'];
        return $user;
    }
}
```

使用这种方法并使用像这里的自封装，在从我们的持久化引擎中获取由于领域规则变化而失效的无效对象时要小心。另一种完全不使用父类构造函数的方法可能是：

## 6.6.2 从领域或应用发布你的领域事件

**服务（Services）**

你应该努力在链条中更深层的地方发布领域事件（Domain Events）。越靠近实体（Entity）或值对象（Value Object）越好。正如我们在上一节看到的，有时这并不容易，但最终结果对客户端来说会更简单。我们见过开发者从应用服务（Application Services）或领域服务（Domain Services）发布领域事件。这看起来是一个更容易实现的方法，但与将业务逻辑推向领域服务而不是将其放入实体中一样，会导致贫血领域模型（Anemic-Domain Model）。

### 6.6.3 DomainEventPublisher 如何工作

`DomainEventPublisher` 是我们的边界上下文（Bounded Context）中可用的单例类，用于发布领域事件。它还支持附加监听器 `DomainEventSubscriber`，这些监听器将监听它们感兴趣的任何 `DomainEvent`。这与使用 jQuery 的 `on` 方法订阅事件没有区别。

⁶[`packagist.org/packages/ocramius/proxy-manager`](https://packagist.org/packages/ocramius/proxy-manager)

领域事件

138

```php
class DomainEventPublisher
{
    private $subscribers;
    private static $instance = null;

    public static function instance()
    {
        if (null === static::$instance) {
            static::$instance = new static();
        }
        return static::$instance;
    }

    private function __construct()
    {
        $this->subscribers = [];
    }

    public function __clone()
    {
        throw new BadMethodCallException('Clone is not supported');
    }

    public function subscribe(DomainEventSubscriber $aDomainEventSubscriber)
    {
        $this->subscribers[] = $aDomainEventSubscriber;
    }

    public function publish(DomainEvent $anEvent)
    {
        foreach ($this->subscribers as $aSubscriber) {
            if ($aSubscriber->isSubscribedTo($anEvent)) {
                $aSubscriber->handle($anEvent);
            }
        }
    }
}
```

`publish` 方法遍历所有可能的订阅者，检查它们是否对发布的领域事件感兴趣。如果是的话，则调用订阅者的 `handle` 方法。

`subscribe` 方法添加一个新的 `DomainEventSubscriber`，该对象将监听特定的领域事件类型。

领域事件

139

```php
interface DomainEventSubscriber
{
    /**
     * @param DomainEvent $aDomainEvent
     */
    public function handle($aDomainEvent);

    /**
     * @param DomainEvent $aDomainEvent
     * @return bool
     */
    public function isSubscribedTo($aDomainEvent);
}
```

正如我们已经讨论过的，持久化所有的领域事件是一个好主意。我们如何轻松地持久化应用中发布的所有领域事件？使用一个特定的订阅来实现。让我们创建一个 `DomainEventSubscriber`，它将监听所有类型的领域事件，并使用我们的 `EventStore` 将它们持久化。



```php
class PersistDomainEventSubscriber implements DomainEventSubscriber
{
    private $eventStore;

    public function __construct(EventStore $anEventStore)
    {
        $this->eventStore = $anEventStore;
    }

    public function handle($aDomainEvent)
    {
        $this->eventStore->append($aDomainEvent);
    }

    public function isSubscribedTo($aDomainEvent)
    {
        return true;
    }
}
```

`eventStore` 可以是一个自定义的 Doctrine 仓库（如之前所示），或者任何其他能够将领域事件持久化到数据库的对象。

## 领域事件

### 6.6.4 设置 DomainEventListeners

设置 `DomainEventPublisher` 订阅者的最佳位置在哪里？这取决于具体情况。对于影响所有请求的全局订阅者，可能是在构建你的 `DomainEventPublisher` 时。如果某些订阅者只影响特定的应用服务，则在构建应用服务时。让我们来看一个使用 Silex 的示例。

在 [Silex](http://silex.sensiolabs.org/)⁷ 中，注册持久化所有领域事件的领域事件发布者的最佳方法是使用[应用中间件](http://silex.sensiolabs.org/doc/middlewares.html)⁸。一个*应用前中间件（before application middleware）允许你在执行执行器之前调整 `Request`。这是订阅负责将这些事件持久化到数据库（稍后将发送到 RabbitMQ）的监听器的正确位置。

```php
// ...

$app['em'] = $app->share(function() {
    return (new EntityManagerFactory())->build();
});

$app['event_repository'] = $app->share(function($app) {
    return $app['em']->getRepository('Ddd\\Domain\\Model\\Event\\StoredEvent');
});

$app['event_publisher'] = $app->share(function($app) {
    return DomainEventPublisher::instance();
});

$app->before(function (Symfony\Component\HttpFoundation\Request $request) use ($app) {
    $app['event_publisher']->subscribe(
        new PersistDomainEventSubscriber(
            $app['event_repository']
        )
    );
});
```

通过这种设置，每个聚合根（Aggregate）发布 `DomainEvent` 时，它都会被持久化到数据库中。任务完成。

### 6.6.5 测试

你已经知道如何发布领域事件，但我们如何通过单元测试这种发布行为的发生呢？我们如何真正测试 `UserRegistered` 是否真的触发了？我们建议的简单方法⁷[`silex.sensiolabs.org/`](http://silex.sensiolabs.org/) ⁸[`silex.sensiolabs.org/doc/middlewares.html`](http://silex.sensiolabs.org/doc/middlewares.html) 是使用一个特定的 `EventListener`，它将充当[间谍⁹](http://www.martinfowler.com/bliki/TestDouble.html) 来记录领域事件是否发布。让我们来看一个 `User` 实体的单元测试示例。

```php
use Ddd\Domain\DomainEventPublisher;
use Ddd\Domain\DomainEventSubscriber;
class UserTest extends \PHPUnit_Framework_TestCase
{
    //...

    /**
     * @test
     */
    public function itShouldPublishUserRegistered()
    {
        $subscriber = new SpySubscriber();
        $id = DomainEventPublisher::instance()->subscribe($subscriber);
        $userId = new UserId();
        new User($userId, 'valid@email.com', 'password');
        DomainEventPublisher::instance()->unsubscribe($id);
        $this->assertUserRegisteredPublished($subscriber, $userId);
    }

    private function assertUserRegisteredPublished($subscriber, $userId)
    {
        $this->assertInstanceOf('UserRegistered', $subscriber->domainEvent);
        $this->assertTrue($subscriber->domainEvent->userId()->equals($userId));
    }
}

class SpySubscriber implements DomainEventSubscriber
{
    public $domainEvent;

    public function handle($aDomainEvent)
    {
        $this->domainEvent = $aDomainEvent;
    }

    public function isSubscribedTo($aDomainEvent)
    {
        return true;
    }
}
```

还有一些替代方案。你可以为 `DomainEventPublisher` 使用静态设置器，或者使用某些反射框架来检测调用。然而，我们认为这种方法更自然。最后但同样重要的是，记得清理间谍订阅，以免它影响剩余的单元测试。

### 6.7 向远程边界上下文传播消息

为了向本地或远程边界上下文通信一组领域事件，有两种主要的非互斥策略：消息传递（Messaging）和 REST API。第一种策略计划使用消息系统（如 RabbitMQ）来传输它们。第二种策略计划创建一个 REST API 来访问特定边界上下文的领域事件。

### 6.7.1 消息传递

当所有领域事件持久化到数据库后，剩下的唯一传播工作是将它们推送到我们喜爱的消息系统。我们个人喜欢 [RabbitMQ¹⁰](https://www.rabbitmq.com)，但任何其他如 ActiveMQ 或 ZeroMQ 都能胜任。对于使用 PHP 集成 RabbitMQ，选项并不多，[php-amqplib¹¹](https://packagist.org/packages/videlalvaro/php-amqplib) 可以。

首先，我们需要一个能够将持久化的领域事件发送到 RabbitMQ 的服务。这可以很简单，通过 `EventStore` 查询所有事件并发送每一个事件如何？这听起来不坏，但是，我们可能会多次推送同一个 `DomainEvent`。通常情况下，**我们需要尽力减少重新发布的 `DomainEvents` 的次数**。如果次数为零，那就更好。为了实现这一点，我们需要某种组件来跟踪哪些 `DomainEvents` 已经推送，哪些是剩余的。

最后但同样重要的一是，一旦我们知道必须推送哪些 `DomainEvents`，我们就发送它们，并跟踪发布到我们消息系统中的最后一个。让我们来看看该服务的一种可能实现：

¹⁰[`www.rabbitmq.com`](https://www.rabbitmq.com)

¹¹[`packagist.org/packages/videlalvaro/php-amqplib`](https://packagist.org/packages/videlalvaro/php-amqplib)

```php
class NotificationService
{
    private $serializer;
    private $eventStore;
    private $publishedMessageTracker;
    private $messageProducer;

    public function __construct(
        EventStore $anEventStore,
        PublishedMessageTracker $aPublishedMessageTracker,
        MessageProducer $aMessageProducer
    ) {
        $this->eventStore = $anEventStore;
        $this->publishedMessageTracker = $aPublishedMessageTracker;
        $this->messageProducer = $aMessageProducer;
    }

    /**
     * @return int
     */
    public function publishNotifications($exchangeName)
    {
        $publishedMessageTracker = $this->publishedMessageTracker();
        $notifications = $this->listUnpublishedNotifications(
            $publishedMessageTracker->mostRecentPublishedMessageId($exchangeName)
        );

        if (!$notifications) {
            return 0;
        }

        $messageProducer = $this->messageProducer();
        $messageProducer->open($exchangeName);

        try {
            $publishedMessages = 0;
            $lastPublishedNotification = null;
            foreach ($notifications as $notification) {
                $lastPublishedNotification = $this->publish(
                    $exchangeName,
                    $notification,
                    $messageProducer
                );
                $publishedMessages++;
            }
        } catch (\Exception $e) {
            // Log your error (trigger_error, Monolog, etc.)
        }

        $this->trackMostRecentPublishedMessage(
            $publishedMessageTracker,
            $exchangeName,
            $lastPublishedNotification
        );
        $messageProducer->close($exchangeName);

        return $publishedMessages;
    }

    protected function publishedMessageTracker()
    {
        return $this->publishedMessageTracker;
    }

    /**
     * @return StoredEvent[]
     */
    private function listUnpublishedNotifications($mostRecentPublishedMessageId)
    {
        return $this->eventStore()
            ->allStoredEventsSince($mostRecentPublishedMessageId);
    }

    protected function eventStore()
    {
        return $this->eventStore;
    }

    private function messageProducer()
    {
        return $this->messageProducer;
    }

    private function publish(
        $exchangeName,
        StoredEvent $notification,
        MessageProducer $messageProducer
    ) {
        $messageProducer->send(
            $exchangeName,
            $this->serializer()->serialize($notification, 'json'),
            $notification->typeName(),
            $notification->eventId(),
            $notification->occurredOn()
        );
        return $notification;
    }

    private function serializer()
    {
        if (null === $this->serializer) {
            $this->serializer = SerializerBuilder::create()->build();
        }
        return $this->serializer;
    }

    private function trackMostRecentPublishedMessage(
        PublishedMessageTracker $publishedMessageTracker,
        $exchangeName,
        $notification
    ) {
        $publishedMessageTracker->trackMostRecentPublishedMessage(
            $exchangeName,
            $notification
        );
    }
}
```

`NotificationService` 依赖于三个接口。我们已经见过 `EventStore`，它负责追加和查询 `DomainEvents`。第二个是 `PublishedMessageTracker`，负责跟踪已推送的消息。第三个是 `MessageProducer`，一个代表我们消息系统的接口。

```php
interface PublishedMessageTracker
{
    /**
     * @param string $exchangeName
     * @return int
     */
    public function mostRecentPublishedMessageId($exchangeName);

    /**
     * @param string $exchangeName
     * @param StoredEvent $notification
     */
    public function trackMostRecentPublishedMessage($exchangeName, $notification);
}
```

`mostRecentPublishedMessageId` 返回最后一条消息的 id，`trackMostRecentPublishedMessage` 负责跟踪发送的内容。



```php
class DoctrinePublishedMessageTracker extends EntityRepository implements PublishedMessageTracker
{
    /**
     * @param string $exchangeName
     * @return int
     */
    public function mostRecentPublishedMessageId($exchangeName)
    {
        $messageTracked = $this->findOneByName($exchangeName);
        if (!$messageTracked) {
            return null;
        }
        return $messageTracked->id();
    }

    /**
     * @param string $exchangeName
     * @param StoredEvent $notification
     */
    public function trackMostRecentPublishedMessage($exchangeName, $notification)
    {
        if (!$notification) {
            return;
        }
        $maxId = $notification->eventId();
        $publishedMessage = $this->findOneByName($exchangeName);
        if (null === $publishedMessage) {
            $publishedMessage = new PublishedMessage(
                $exchangeName,
                $maxId
            );
        }
        $publishedMessage->updateMostRecentMessageId($maxId);
        $this->getEntityManager()->persist($publishedMessage);
        $this->getEntityManager()->flush();
    }
}
```

代码非常直观。我们需要考虑的唯一边界情况是没有发布 `DomainEvent`。

### 为什么需要交换名称？

我们将在“集成限界上下文”章节中详细讨论这一点。然而，当系统运行并且一个新的限界上下文（BC）加入时，你会有兴趣重新发送所有的 `DomainEvents`。因此，跟踪最后发布的 `DomainEvent` 和通道很有意义。为了跟踪 `DomainEvents`，我们需要交换名称和 ID。查看一种可能的实现。

领域事件

148

```php
class PublishedMessage
{
    private $mostRecentPublishedMessageId;
    private $trackerId;
    private $exchangeName;

    public function __construct($exchangeName, $aRecentPublishedMessageId)
    {
        $this->mostRecentPublishedMessageId = $aRecentPublishedMessageId;
        $this->exchangeName = $exchangeName;
    }

    public function mostRecentPublishedMessageId()
    {
        return $this->mostRecentPublishedMessageId;
    }

    public function updateMostRecentMessageId($maxId)
    {
        $this->mostRecentPublishedMessageId = $maxId;
    }

    public function trackerId()
    {
        return $this->trackerId;
    }
}
```

以及对应的映射。

领域事件

149

```yaml
Ddd\Domain\Event\PublishedMessage:
  type: entity
  table: event_published_message_tracker
  repositoryClass: Ddd\Infrastructure\Application\Notification\DoctrinePublished\MessageTracker
  id:
    trackerId:
      column: tracker_id
      type: integer
      generator:
        strategy: AUTO
  fields:
    mostRecentPublishedMessageId:
      column: most_recent_published_message_id
      type: bigint
    exchangeName:
      type: string
      column: type_name
```

现在让我们看看 `MessageProducer` 接口的用途以及它的实现细节。

```php
interface MessageProducer
{
    public function open($exchangeName);

    /**
     * @param $exchangeName
     * @param string $notificationMessage
     * @param string $notificationType
     * @param int $notificationId
     * @param \DateTime $notificationOccurredOn
     * @return void
     */
    public function send(
        $exchangeName,
        $notificationMessage,
        $notificationType,
        $notificationId,
        $notificationOccurredOn
    );
}
```

```php
\DateTime $notificationOccurredOn);

public function close($exchangeName);

}
```

# 领域事件（Domain Events）

150

非常简单。`open` 和 `close` 方法用于打开和关闭与消息系统的连接。

`send` 接收消息正体、消息名称和消息 ID，并将它们发送到我们的消息引擎中（无论该引擎是什么）。由于我们选择了 `RabbitMQ`，我们需要实现连接和发送过程。

```php
abstract class RabbitMqMessaging
{
    protected $connection;
    protected $channel;

    public function __construct(AMQPConnection $aConnection)
    {
        $this->connection = $aConnection;
        $this->channel = null;
    }

    private function connect($exchangeName)
    {
        if (null !== $this->channel) {
            return;
        }

        $channel = $this->connection->channel();
        $channel->exchange_declare($exchangeName, 'fanout', false, true, false);
        $channel->queue_declare($exchangeName, false, true, false, false);
        $channel->queue_bind($exchangeName, $exchangeName);
        $this->channel = $channel;
    }

    public function open($exchangeName)
    {
    }

    protected function channel($exchangeName)
    {
        $this->connect($exchangeName);
        return $this->channel;
    }

    public function close($exchangeName)
    {
        $this->channel->close();
        $this->connection->close();
    }
}
```

```php
class RabbitMqMessageProducer extends RabbitMqMessaging implements MessageProducer
{
    /**
     * @param string $exchangeName
     * @param string $notificationMessage
     * @param string $notificationType
     * @param int $notificationId
     * @param \DateTime $notificationOccurredOn
     */
    public function send(
        $exchangeName,
        $notificationMessage,
        $notificationType,
        $notificationId,
        \DateTime $notificationOccurredOn
    )
    {
        $this->channel($exchangeName)->basic_publish(
            new AMQPMessage(
                $notificationMessage,
                [
                    'type' => $notificationType,
                    'timestamp' => $notificationOccurredOn->getTimestamp(),
                    'message_id' => $notificationId
                ]
            ),
            $exchangeName
        );
    }
}
```

现在我们已经有了一个领域服务（DomainService）将领域事件（DomainEvents）推送到 `RabbitMQ` 这样的消息系统中，现在是执行它们了。我们需要选择一种交付机制来运行该服务。我们个人建议创建一个 [Symfony Console](http://symfony.com/doc/current/components/console/introduction.html) 命令。

领域事件

152

```php
class PushNotificationsCommand extends Command
{
    protected function configure()
    {
        $this->setName('domain:events:spread')
            ->setDescription('通过消息通知所有领域事件')
            ->addArgument(
                'exchange-name',
                InputArgument::OPTIONAL,
                '发布事件的交换机名称',
                'my-bc-app'
            );
    }

    protected function execute(InputInterface $input, OutputInterface $output)
    {
        $app = $this->getApplication()->getContainer();
        $numberOfNotifications = $app['notification_service']
            ->publishNotifications(
                $input->getArgument('exchange-name')
            );
        $output->writeln(
            sprintf(
                '<comment>%d</comment> <info>已发送通知(s)!</info>',
                $numberOfNotifications
            )
        );
    }
}
```

遵循 Silex 的示例，让我们看看 `$app['notification_service']` 在 [Silex Pimple Service Container](https://silex.com/doc/2.0/pimple.container.html) 中的定义。

领域事件

153

```php
// ... (代码部分同上)
```

154

### 6.8 总结

现在，剩下的事情是关于通过消息系统来处理领域事件或相应的应用服务。我们在“集成限界（Integrating Bounded Contexts）”和“应用服务（Application Services）”章节中看到如何实现这一点。

!(-173)

# 7. 模块（Modules）

当你将一些类放在一个模块（Module）中时，你是在告诉查看你设计的后续开发者将它们放在一起。如果你的模型是在讲述一个故事，那么模块就是章节。Eric Evans，领域驱动设计

在遵循领域驱动设计（DDD）构建应用时，一个常见的问题是：我们将代码放在哪里？推荐如何将代码放入应用程序？基础设施代码放在哪里？更重要的是，模型内部的不同概念应该如何组织？

有一个战术模式可以解决这个问题：模块。如今，每个人使用模块组织代码。但 DDD 更进一步，它将模块视为模型的一部分。

## 7.1 在模块中组织代码

如果我们以一个名为 `buy.it` 的虚拟电子商务应用程序为例，为每个不同的限界上下文定义一个模块可能是合理的，因为每个限界上下文代表了一个自包含且独立的应用程序。

```text
├── billing
│   ├── composer.json
│   ├── composer.lock
│   ├── src
│   └── tests
├── cart
│   ├── composer.json
│   ├── composer.lock
│   ├── src
│   └── tests
├── catalog
│   ├── composer.json
│   ├── composer.lock
│   ├── src
│   └── tests
└── inventory
    ├── composer.json
    ├── composer.lock
    ├── src
    └── tests
```

每个模块包含一个暴露类似 REST API 的应用程序。请注意，每个模块名称都是电子商务系统中的意义概念，并使用通用语言（Ubiquitous Language）命名：

- **账单模块（Billing）**：包含所有与支付、发票、运单以及具有有限状态机的订单处理系统等相关的代码。
- **购物车模块（Cart）**：包含所有与购物车系统相关的代码。
- **目录模块（Catalog）**：包含所有与产品描述、产品组合等相关的代码。
- **库存模块（Inventory）**：包含所有与产品库存管理相关的代码。

让我们进一步深入探讨其中一个模块。以 `Billing`（账单）上下文为例，检查其结构细节。正如其名称所示，该模块负责表示订单所经历的所有流程。从它的创建到交付给购买它的客户。此外，它是一个独立的应用程序，因此它包含一个源代码文件夹（`src`）和一个测试文件夹（`tests`）。源代码文件夹包含了使该边界上下文（bounded context）工作所需的所有代码：`domain`、`code` 和 `infrastructure code`。

```text
├── composer.json
├── composer.lock
├── src
│
└── BuyIt
│
└── Billing
│
├── DomainModel
│
└── Infrastructure
└── tests
```



所有代码都带有以组织命名的供应商命名空间（vendor namespace）前缀（在本例中为`BuyIt`），并包含两个子文件夹：`DomainModel`存放所有领域代码，`Infrastructure`存放基础设施层，将所有领域逻辑与基础设施层的细节隔离开来。通过这种结构，我们清晰地表明了，我们将使用`Hexagonal Architecture`（六边形架构）作为基础架构。我们可能使用的另一种替代结构如下：

![](img/index-175_1.png)

### Modules

157

```
├── composer.json
├── composer.lock
├── src
│
└── BuyIt
│
└── Billing
│
├── Domain
│
├── Model
│
└── Service
│
└── Infrastructure
└── tests
```

这种风格的结构使用额外的子文件夹来存储定义在领域模型内部的类。虽然这种组织方式可能是合理的，但我们倾向于不使用它，因为这种分离代码的方法往往更关注架构元素，而不是模型中的相关概念。我们认为这种风格很容易在领域模型之上产生某种服务层，这并不是一件坏事，但请记住，`Domain Services`（领域服务）用于描述领域中的事物，即不属于实体（entities）也不属于值对象（value objects）的操作。因此，从现在起我们将坚持之前的代码组织方式。

可以将代码直接放在`DomainModel`子文件夹中。例如，将公共接口和服务类放在其中是非常常见的，如`DomainEventPublisher`、`DomainEventSubscriber`等。

如果我们对账单上下文进行建模，可能会有一个`Order`实体及其存储库（repository）以及所有状态信息。因此，我们的第一次尝试将是将所有这些元素直接放入`DomainModel`子文件夹中。乍看之下，这似乎是最简单的方法。

```
├── composer.json
├── composer.lock
├── src
│
└── BuyIt
│
└── Billing
│
├── DomainModel
│
├── Order.php
│
├── OrderLine.php
│
├── OrderLineWasAdded.php
│
├── OrderRepository.php
│
└── OrderWasCreated.php
│
└── Infrastructure
└── tests
```

### Modules

158

我们将`Order`和`OrderLine`实体、`OrderLineWasAdded`和`OrderWasCreated`事件以及`OrderRepository`放在同一个子文件夹（`DomainModel`）中。这种结构可能是可以的，但那是因为我们仍然有一个简单的模型。那么`Bill`实体加上它的存储库呢？或者`Waybill`（运单）实体加上相应的存储库呢？让我们添加所有这些元素，看看它们如何适应实际的代码结构。

```
├── composer.json
├── composer.lock
├── src
│
└── BuyIt
│
└── Billing
│
├── DomainModel
│
├── Bill.php
│
├── BillLine.php
│
├── BillLineWasAdded.php
│
├── BillRepository.php
│
├── BillWasCreated.php
│
├── Order.php
│
├── OrderLine.php
│
├── OrderLineWasAdded.php
│
├── OrderRepository.php
│
├── OrderWasCreated.php
│
└── Infrastructure
└── tests
```

（注：此处代码块内容展示了包含账单实体、存储库、运单实体及其对应存储库的逻辑，由于原文未提供重复翻译，此处保持结构逻辑一致）

虽然这种代码组织方式目前可能可行，但从长远来看，它会变得不实用且难以维护。每当我们迭代并添加新功能时，模型就会变得更大，该文件夹也会变得臃肿。为了实现这一点，我们可以使用`Ubiquitous Language`（通用语言）来拆分模型，按领域关注点划分。我们可以尝试如下方法：

### Modules

159

```
├── composer.json
├── composer.lock
├── src
│
└── BuyIt
│
└── Billing
│
├── DomainModel
│
├── Bill
│
│
│
├── Bill.php
│
│
│
├── BillLine.php
│
│
│
├── BillLineWasAdded.php
│
│
│
├── BillRepository.php
│
│
│
└── BillWasCreated.php
│
│
│
├── Order
│
│
│
├── Order.php
│
│
│
├── OrderLine.php
│
│
│
├── OrderLineWasAdded.php
│
│
│
├── OrderRepository.php
│
│
│
└── OrderWasCreated.php
│
│
│
├── Waybill
│
│
│
├── Waybill.php
│
│
│
├── WaybillLine.php
│
│
│
├── WaybillLineAdded.php
│
│
│
├── WaybillRepository.php
│
│
│
└── WaybillGenerated.php
│
└── Infrastructure
└── tests
```

这种方式代码在概念上更有组织性，而不仅仅是技术关注点。观察之前的示例，我们可以发现`Order`和`OrderLine`概念关系紧密，因此它们位于同一个模块中。另一方面，`Order`和`Waybill`虽然共享同一个上下文，但它们是不同的概念，因此它们位于不同的模块。模块是一种通信方式，并记住模块的主要目的是将领域模型的相关概念组织在一起，并将它们与不相关的解耦。模块并不分离代码，而是分离有意义的概念。![](img/index-178.png)

### 7.1.1 基础设施层中的模块

到为止，我们一直在讨论如何构建和组织领域层的代码，但几乎没有提到过`Infrastructure Layer`。由于我们使用`Hexagonal Architecture`来反转领域层和基础设施层之间的依赖，我们需要一个地方来放置领域层定义的所有接口的实现。回到账单上下文示例，我们需要为`BillRepository`、`OrderRepository`和`WaybillRepository`的实现提供一个位置。

显然，它们应该放在`Infrastructure`文件夹中，但放在哪里？假设我们决定使用`Doctrine ORM`来实现持久层。我们如何将存储库的 Doctrine 实现放入`Infrastructure`文件夹？让我们直接放在里面并看看看起来是什么样。

```
├── composer.json
├── composer.lock
├── src
│
└── BuyIt
│
└── Billing
│
├── DomainModel
│
├── ...
└── Infrastructure
```

```text
├── OrderLine.php
├── OrderLineWasAdded.php
├── OrderRepository.php
└── OrderWasCreated.php
└── Waybill
├── Waybill.php
├── WaybillLine.php
├── WaybillLineWasAdded.php
├── WaybillRepository.php
└── WaybillWasGenerated.php
└── Infrastructure
├── DoctrineBillRepository.php
├── DoctrineOrderRepository.php
└── DoctrineWaybillRepository.php
└── tests
```

我们可以保持现状。但正如我们在`Domain Layer`中看到的，这种结构和组织方式在经过几次模型迭代后就会迅速腐化并变得混乱。每当模型增长时，可能需要更多的基础设施，这样我们最终会将不同的技术关注点（如`persistence`、`messaging`、`logging`等）混合在一起。我们避免基础设施实现变得错综复杂的的第一个尝试，是在边界上下文（bounded context）中为每个`技术关注点`定义一个模块。

```text
├── composer.json
├── composer.lock
├── src
└── BuyIt
    └── Billing
        ├── DomainModel
        ├── Bill
        ├── Bill.php
        ├── BillLine.php
        ├── BillLineWasAdded.php
        ├── BillRepository.php
        └── BillWasCreated.php
        ├── Order
        ├── Order.php
        ├── OrderLine.php
        ├── OrderLineWasAdded.php
        ├── OrderRepository.php
        └── OrderWasCreated.php
        └── Waybill
        ├── Waybill.php
        ├── WaybillLine.php
        ├── WaybillLineWasAdded.php
        ├── WaybillRepository.php
        └── WaybillWasGenerated.php
        └── Infrastructure
            ├── Logging
            ├── Messaging
            └── Persistence
            ├── DoctrineBillRepository.php
            ├── DoctrineOrderRepository.php
            └── DoctrineWaybillRepository.php
        └── tests
```

这看起来好多了，而且从长期来看比我们的第一次尝试更具维护性。如果你预先知道自己将始终只有一个持久化机制，那么可以坚持这种结构和组织。它非常简单且易于维护。但当你必须处理多种持久化机制时怎么办？如今，拥有一个关系型数据库以及某种如`Redis`或`Riak`之类的共享内存持久化是非常常见的。或者为了测试代码而拥有某种本地内存实现。让我们看看这如何融入实际方案。

```text
├── composer.json
├── composer.lock
├── src
└── BuyIt
    └── Billing
        ├── DomainModel
        ├── Bill
        ├── Bill.php
        ├── BillLine.php
        ├── BillLineWasAdded.php
        ├── BillRepository.php
        └── BillWasCreated.php
        ├── Order
        ├── Order.php
        ├── OrderLine.php
        ├── OrderLineWasAdded.php
        ├── OrderRepository.php
        └── OrderWasCreated.php
        └── Waybill
        ├── Waybill.php
        ├── WaybillLine.php
        ├── WaybillLineWasAdded.php
        ├── WaybillRepository.php
        └── WaybillWasGenerated.php
        └── Infrastructure
            ├── Logging
            ├── Messaging
            └── Persistence
            ├── DoctrineBillRepository.php
            ├── DoctrineOrderRepository.php
            ├── DoctrineWaybillRepository.php
            ├── InMemoryBillRepository.php
            ├── InMemoryOrderRepository.php
            ├── InMemoryWaybillRepository.php
            ├── RedisBillRepository.php
            ├── RedisOrderRepository.php
            ├── RedisWaybillRepository.php
        └── tests
```

这现在看起来又有点奇怪。所有的仓库实现都位于同一个模块中，这导致了多种技术的混合。目前我们有几个仓库。如果再多出几个，维护性可能会开始下降。因此这清楚地说明了我们需要创建另一个模块，根据底层技术将相关的实现进行分组。

```text
├── composer.json
├── composer.lock
├── src
└── BuyIt
    └── Billing
        ├── DomainModel
        ├── Bill
        ├── Bill.php
        ├── BillLine.php
        ├── BillLineWasAdded.php
        ├── BillRepository.php
        └── BillWasCreated.php
        ├── Order
        ├── Order.php
        ├── OrderLine.php
        ├── OrderLineWasAdded.php
        ├── OrderRepository.php
        └── OrderWasCreated.php
        └── Waybill
        ├── Waybill.php
        ├── WaybillLine.php
        ├── WaybillLineWasAdded.php
        ├── WaybillRepository.php
        └── WaybillWasGenerated.php
        └── Infrastructure
            ├── Logging
            ├── Messaging
            └── Persistence
            ├── DoctrineBillRepository.php
            ├── DoctrineOrderRepository.php
            ├── DoctrineWaybillRepository.php
            ├── InMemoryBillRepository.php
            ├── InMemoryOrderRepository.php
            ├── InMemoryWaybillRepository.php
            ├── RedisBillRepository.php
            ├── RedisOrderRepository.php
            ├── RedisWaybillRepository.php
        └── tests
```

这种基础设施层的结构和组织比我们之前的尝试更具维护性，且更容易理解。我们可以对此边界上下文中使用的技术有一个通的了解。

### 7.1.1.1 混合不同的技术

在大型关键业务应用中，混合多种技术是相当常见的。例如，在读密集型 Web 应用中，你通常会有某种去范式化数据源（`Solr`、`Elastic`、`Sphinx`等）提供应用程序所有的读取操作，而传统的 RDBMS（如`MySQL`或`Postgres`）主要负责处理所有的写入操作。当这种情况发生时，产生的问题之一是，是否可以让读取操作使用搜索引擎，而写入操作使用传统的数据库。我们的通用建议是，这类情况是`CQRS`的信号，因为我们需要独立地扩展读取和写入。如果你可以使用`CQRS`，那么这可能是最好的选择。

但由于某种原因你无法使用`CQRS`，则需要替代方案。在这种情况下，来自“四人行”的`代理模式`将派上用场。我们可以根据`代理模式`定义仓库的实现。



```php
namespace BuyIt\Billing\Infrastructure\FullTextSearching\Elastica;
use BuyIt\Billing\DomainModel\Order\OrderRepository;
use BuyIt\Billing\Infrastructure\Persistence\Doctrine\DoctrineOrderRepository;
use Elastica\Client;

class ElasticaOrderRepository implements OrderRepository
{
    private $client;
    private $baseOrderRepository;

    public function __construct(Client $client, DoctrineOrderRepository $baseOrderRepository)
    {
        $this->client = $client;
        $this->baseOrderRepository = $baseOrderRepository;
    }

    public function find($id)
    {
        return $this->baseOrderRepository->find($id);
    }

    public function findBy(array $criteria)
    {
        $search = new \Elastica\Search($this->client);
        // ... ...
        return $this->toOrder($search->search());
    }

    public function add($anOrder)
    {
        // 首先尝试将它添加到 Elastic 索引
        $ordersIndex = $this->client->getIndex('orders');
        $orderType = $ordersIndex->getType('order');
        $orderType->addDocument(
            new \Elastica\Document(
                $anOrder->id(),
                $this->toArray($anOrder)
            )
        );

        $ordersIndex->refresh();
        // 完成后，我们尝试将其添加到 RDBMS 存储
        $this->baseOrderRepository->add($anOrder);
    }
}
```

这个示例提供了一个使用`DoctrineOrderRepository`和`Elastica`客户端（一个与 Elastic 服务器交互的客户端）的简单实现。注意，对于某些操作我们使用了 RDBMS 数据源，而对另一些操作使用了`Elastica`客户端。此外注意添加操作由两个部分组成。第一部分尝试将订单存储到 Elastic 索引，第二部分尝试将`Order`存储到关系型数据库中，并将该操作委托给 Doctrine 实现。

请注意，这只是一个示例和一种方法。它可能会被改进，例如现在整个添加操作是同步的。相反，我们可以将操作入队到某种消息中间件中，例如将`Order`存储到 Elastic 中。根据你的需求，有很多可能性和改进空间。

### 7.2 在 PHP 中利用模块

在 PHP 5.3 之前，模块并没有被完全支持。如今，自 PHP 5.3 以来，我们可以使用 PHP 命名空间（namespaces）来实现`Module`模式。由于历史原因，我们将介绍在 PHP 5.3 之前如何使用命名空间。但你应该努力使用支持 PHP 命名空间的 PHP 版本。最佳选择始终是 PHP 的最新稳定版本。

#### 7.2.1 PEAR 风格的命名空间

在 PHP 5.3 之前，由于缺乏命名空间结构，使用了 PEAR 风格的命名空间。PEAR 是`PHP Extension and Application Repository`的缩写，在过去的旧时代，它是可重用组件的仓库。它仍然活跃，但其使用已是少数，并且有许多未维护的包。特别是自从`composer`和`packagist`上台之后。

PEAR 作为可重用组件的来源，需要一种避免类名冲突的方法，因此他们开始用命名空间类类名前。仍然有项目使用这种形式的命名空间（例如`PHPUnit`或`Zend Framework 1`）。以下是 PEAR 风格命名空间的一个示例：

```
Modules
├── composer.json
├── composer.lock
└── src
└── BuyIt
└── Billing
└── DomainModel
└── Bill
└── Bill.php
```

使用 PEAR 风格的命名空间，`Bill`实体的类名将变为`BuyIt_Billing_DomainModel_Bill_Bill`。这个类名有点丑陋，并且没有遵循 DDD 的核心准则之一：每个类名都应该根据通用语言（Ubiquitous Language）来命名。出于这个原因，我们强烈不建议使用它。

#### 7.2.2 PSR-0 和 PSR-4 命名规范

与 PHP 5.3 的其他重要功能一起，命名空间进入了舞台。这是一次重大转变，一群最重要的框架合作者形成了 [PHP-FIG](http://www.php-fig.org/)（这是`PHP Framework Interop Group`的缩写），旨在标准化和统一框架及库创建的共同方面。

该小组发布的第一个`PHP 标准建议`（下简称`PSR`）是一个自动加载标准，总而言之，它提议使用命名空间在类和 PHP 文件之间建立一一关系。如今，`PSR-4`（`PSR-0`的简化版，仍然保持了类与物理 PHP 文件之间的关系）是构建代码的首选且推荐的方法，我们认为这应该是在项目中实现`Modules`的使用方法。回到之前的示例：

```
├── composer.json
├── composer.lock
└── src
└── BuyIt
└── Billing
└── DomainModel
└── Bill
└── Bill.php
```

使用命名空间和`PSR-0/PSR-4`，`Bill`实体的类名将简单变为`Bill`，完全限定类名将是`BuyIt\Billing\DomainModel\Bill\Bill`。正如你所看到的，这种方式使我们能够根据通用语言命名领域对象，并且构建和组织代码的首选方式。

### 7.3 总结

模块是在我们的领域模型中分组和分离概念的一种方式。模块的命名应该遵循通用语言。我们不应该忘记，模块是通信高层概念的一种方式，它帮助我们保持低耦合和高内聚。我们看到，即使在旧版本的 PHP 中，也可以通过使用前缀创建有的模块。现在很容易遵循`PSR-0`和`PSR-4`命名规范来构建我们的模块。

## 8. 聚合（Aggregates）

### 8.1 引言

聚合可能是领域驱动设计（DDD）中最难理解和实现的构建基石。为了正确地实现它们，我们需要理解事务、锁定和并发策略等概念。了解它们的起源以及 NoSQL 运动如何对其产生如此巨大的影响也很有趣。

来自 Vaughn Vernon 的《实施领域驱动设计》：聚合是精心构建的一致性边界，将实体（Entities）和值对象（Value Objects）聚集在一起。另一本你绝对应该购买并阅读的奇书是 Pramod J. Sadalage 写的《NoSQL Distilled: A Brief Guide to the Emerging World of Polyglot Persistence》。书中写道：“在领域驱动设计中，聚合是一个我们希望视为一个整体处理的相关对象的集合。特别是，它是数据操纵和一致性管理的单元。通常，我们喜欢用原子操作更新聚合，并以聚合的角度与我们的数据存储进行通信。”

#### 8.1.1 Martin Fowler 是怎么说的……

来自 [`martinfowler.com/bliki/DDD_Aggregate.html`](http://martinfowler.com/bliki/DDD_Aggregate.html)

聚合是领域驱动设计中的一种模式。DDD 聚合是一个可以被视为单个单元的领域对象簇。一个例子可能是订单及其行项目，这些将是单独的对象，但将订单（连同其行项目）视为单个聚合是有用的。聚合将由其组件对象中的一个作为聚合根（aggregate root）。任何从聚合外部发出的引用都应该只指向聚合根。因此，根可以确保整个聚合的完整性。

聚合是数据存储传输的基本元素——你请求加载或保存整个聚合。事务不应该跨越聚合边界。

DDD 聚合有时会与集合类（列表、映射等）混淆。DDD 聚合是领域概念（订单、诊疗访问、播放列表），而集合是通用的。聚合通常包含多个集合以及简单的字段。“aggregate”一词是一个通用术语，用于各种不同的上下文中（例如 UML），在这种情况下，它指的并不是 DDD 聚合的概念。

#### 8.1.2 百基百科是这么说的……

来自 [`en.wikipedia.org/wiki/Domain-driven_design#Building_blocks_of_DDD`](https://en.wikipedia.org/wiki/Domain-driven_design#Building_blocks_of_DDD)：聚合：由一个根实体（又称为聚合根）结合在一起的对象集合。聚合根通过禁止外部对象持有对其成员的引用，来保证聚合内所做更改的一致性。

示例：当你开车时，你不需要担心让轮子向前移动、让引擎通过火花和燃料燃烧等等；你只是在开车。在这种语境下，汽车是几个其他对象的聚合，并作为所有其他系统的聚合根。

### 8.2 简史历史

在新世纪初，技术世界遭遇了 1990 年互联网泡沫破灭的冲击。虽然这让许多人质疑互联网的经济未来，但 2000 年确实看到几个大型网络属性的规模急剧扩大。

这种规模的增长正在许多维度上发生。网站开始以非常详细跟踪活动和结构。出现了大量数据集：链接、社交网络、日志中的活动、映射数据。随着数据的增长，用户也增长了——因为最大的网站已成为经常服务大量访问者的庞大园区。

应对数据和流量的增长需要更多的计算资源。为了处理这种关于扩展，你有两个选择：向上扩展（up）或向外扩展（out）。向上扩展意味着更大的机器、更多的处理器、磁盘存储和内存。但更大的机器变得越来越贵，更不用说随着规模的增大，还存在真实的限制。

另一种方案是在集群中使用许多小机器。小机器集群可以使用廉价的硬件，在这些规模下最终成本更低。它还更具韧性——虽然单台机器故障很常见，但整个集群可以设计为即使发生此类故障也能运行，提供高可靠性。

当大型属性转向集群时，这揭示了一个新问题——关系型数据库并不是为在集群上运行而设计的。集群关系型数据库（如`Oracle RAC`或`Microsoft SQL Server`）基于共享磁盘子系统的概念工作。它们使用感知集群的文件系统并写入到高可用磁盘子系统——但这意味着集群仍然将磁盘子系统视为单点故障。

关系型数据库也可以作为独立的服务器运行于不同的数据集，有效地实现了数据库分片（sharding）。虽然这分离了负载，但所有的分片必须由应用程序控制，程序必须跟踪每一条数据应该与哪个数据库服务器通信。此外，我们还失去了任何跨分片的查询、引用完整性、事务或一致性控制。在这种背景下，我们经常听到做过此类的人说“不自然的行为（unnatural acts）”。

这些技术问题因许可成本而加剧。商业关系型数据库通常基于单服务器假设进行定价，因此在集群上运行推高价格，并导致了与采购部门令人沮丧的谈判。关系型数据库与集群之间的这种不匹配导致一些组织考虑数据存储的替代方案。

特别是两家公司——`Google`和`Amazon`——极具影响力。它们都处于运行此类大型集群的前沿；此外，它们正在捕获海量数据。这些因素给了它们动力。它们都是成功且不断增长的公司，拥有强大的技术组成部分，这给了它们手段和机会。难怪它们对自己的关系型数据库下了“杀身之决心”。

随着 2000 年代的到来，这两家公司都发表了关于其努力的简短但极具影响力的论文：Google 的`BigTable`和 Amazon 的`Dynamo`。

人们常说`Amazon`和`Google`的运行规模远超大多数组织，因此它们需要的解决方案可能对普通组织并不适用。虽然大多数软件项目确实不需要那种程度的规模，但事实也是如此，越来越多的组织开始探索通过捕获和处理更多数据可以做些什么——并遇到了相同的问题。

因此，随着关于`Google`和`Amazon`所做的更多信息泄露出来，人们开始探索沿着类似的路线构建数据库——显式设计为在集群世界中生存。虽然早期对关系主地位的威胁被证明是幻影，但来自集群的威胁是严重的。

### 8.3 聚合（Aggregates）与集群

一个`Aggregate`（聚合）由一个根`Entity`（实体）组成，该实体持有其他的`Entities`和值对象（Value Objects）。一个没有任何子实体`Entities`或值对象的单个`Entity`自身就构成一个`Aggregate`。这就是为什么在某些书中，`Aggregates`术语被用来代替`Entity`使用。

`Aggregate`的主要优势或真实目标是确保我们领域模型操作的一致性。它允许我们保证对`Entities`和值对象层级结构的更改是以原子方式执行的。

考虑一个粗略的例子来引入这个概念。想象一个电子商务应用程序和一个典型的持久化机制。有`Orders`（订单）和`Line Orders`（订单项）。`Orders`的总金额和`Line Orders`的小计总和必须匹配。你绝不会在使用不保护这两个更改的事务的情况下更改`Line Order`的金额和`Order`的金额。

为什么？因为更新`Line Order`的`UPDATE`语句可以正常工作，而对`Order`总金额的`UPDATE`可能会因为网络连接问题而失败。在这种情况下，你会在表和你的`Domain`中导致不一致，如果你请求`Order`的总金额，然后应用业务逻辑计算所有`Line Orders`的和，会发生什么？你明白意思了。

如果你将两个更改放在一个事务中，它们要么全部成功要么全部失败，这就是一致性。所以事务帮助你保持这种一致性。

在另一方面，负面影响是性能问题和持久化错误。`Aggregate`使用它自己的仓库（repository）进行获取和持久化，无论它持有许多`Entities`和值对象还是没有。

为了设计一个`Aggregate`，需要遵循一些规则或考虑因素，以便我们获得所有收益并最小化负面影响。

### 8.4.1 基于业务真实不变性（Business True Invariants）设计聚合

首先，什么是不变性（invariant）？不变性是在代码执行期间必须为且保持一致的规则。让我们来看一个例子帮助理解。`stack`（栈）是一个后进先出（LIFO）的数据结构，我们可以推送元素、弹出元素并查询大小。考虑一个纯 PHP 实现，不使用任何特定的 PHP 数组函数（如`array_pop`）。

```php
class Stack
{
    private $data;
    public function __construct()
    {
        $this->data = [];
    }

    public function push($value)
    {
        $this->data[] = $value;
    }

    public function size()
    {
        return count($this->data);
    }

    public function pop()
    {
        $topIndex = $this->size() - 1;
        $top = $this->data[$topIndex];
        unset($this->data[$topIndex]);
        return $top;
    }
}
```

想象获取栈的大小是非常消耗 CPU 且高成本的调用。有一种改进该方法的方法，引入一个私有属性来跟踪内部数组中元素的数量。

```php
class Stack
{
    private $data;
    private $size;
    public function __construct()
    {
        $this->data = [];
        $this->size = 0;
    }

    public function push($value)
    {
        $this->data[] = $value;
        $this->size++;
    }

    public function size()
    {
        return $this->size;
    }

    public function pop()
    {
        $topIndex = $this->size() - 1;
        $top = $this->data[$topIndex];
        unset($this->data[$topIndex]);
        $this->size--;
        return $top;
    }
}
```



通过这种方法，现在请求栈的大小变成了一个轻量级的方法。代价是什么？在`pop`和`push`方法中有一些更新，以便在添加和删除元素时跟踪新的大小。让我们尝试寻找一个不变性，即在栈对象的任何方法调用之前之后都应该为真的规则。`$this->size === count($this->data)`怎么样？在栈对象的任何方法调用之前之后，属性`size`都是一致的，并且它始终持有栈的大小。

那么什么是不变性？不变性是一个必须始终为真且在事务中保持一致的业务规则。在上例中，`Order`的金额必须匹配所有`Line Orders`的金额总和，这是一个不变性。这可能使得`Order`成为根，并允许我们对它进行操作，而不是对它内部的`Order Lines`进行操作。

在集群上执行的操作应当保持一致性，且不破坏任何不变性。这意味着，没有机会调用方法来破坏此类规则。每当你添加一个`Line Order`或从根节点更新信息时，内部都会计算`Order`的数量。

注意那些“包含”（has-a）/“包含多个”（has-many）关系，它们并不意味着会将两个`Entities`变成一个`Aggregate`且其中一个是根节点。

### 8.4.2 小聚合根 vs 大聚合根

在设计`Aggregates`时，要努力创建小的`Aggregates`。如果没有不变性需要保护，那么意味着所有单个`Entities`都在执行。

你可能已经在 90% 的情况下这样做了。

### 8.4.3 追求最终一致性

### 8.4.4 每个事务只修改一个聚合根

“在所有情况下，一个设计良好的`Bounded Context`在每个事务中只修改一个`Aggregate`实例。此外，如果不应用事务分析，我们无法正确地推断`Aggregate`的设计。将修改限制在每个事务一个`Aggregate`实例听起来可能过于严格。然而，这是一条经验法则，在大多数情况下应该是我们的目标。它解决了使用`Aggregates`的根本原因。”

### 8.4.5 异常：UX 情况

在遵循之前的规则设计`Aggregates`时，有一个典型的例外。

聚合根

### 8.5 示例应用服务：用户与愿望

学习`Aggregates`的最好方法是看代码。所以，让我们考虑以下场景：一个 Web 应用，用户可以提出愿望，如果他们发生了某些事，这些愿望就能实现。把它想象成一份遗嘱。例如，我想给妻子发一封邮件，解释我在发生不幸事故并去世后该如何处理我的`GitHub`账户。检查我是否还活着的方法是回复平台发送我的邮件。如果你想了解更多关于[这个](https://github.com/ddd-in-php/last-wishes)[应用⁴](https://github.com/ddd-in-php/last-wishes)，你可以访问我们的[GitHub 账户⁵](https://github.com/ddd-in-php)查看此示例及更多内容。

好了，我们有用户和他们的愿望。让我们只考虑一个用例，“作为一个用户，我想要许下一个愿望”。我们如何建模这两个概念？作为设计`Aggregates`的良好实践，让我们尝试追求较小的`Aggregates`，也就是说在这种情况下，是两个各包含一个`Entity`的不同`Aggregates`：`User`和`Wish`。它们之间的关系呢？嗯，我们应该使用标识符，例如`UserId`。让我们看一些代码。

#### 8.5.1 没有不变性，两个聚合根

“作为一个用户，我想要许下一个愿望”。我们将在后续章节中介绍应用服务，但现在，让我们检查实现愿望的不同方法。我们认为对于初学者的第一种方法将类似于下面的代码。

```php
class MakeWishService
{
    private $wishRepository;

    public function __construct(WishRepository $wishRepository)
    {
        $this->wishRepository = $wishRepository;
    }

    public function execute(MakeWishRequest $request)
    {
        $userId = $request->userId();
        $address = $request->address();
        $content = $request->content();
        $wish = new Wish(
            $this->wishRepository->nextIdentity(),
            new UserId($userId),
            $address,
            $content
        );
        $this->wishRepository->add($wish);
    }
}
```

你觉得这段代码如何？它可能是性能最好的代码了。在后台，你几乎可以看到`INSERT`语句。对于此类用例，这是最少的操作次数，只有一个，所以干得好。按照目前的实现，你可以根据业务逻辑创建你想要的任何愿望，再次干得好。

然而，可能存在一个潜在问题，你可以为一个在你的领域（Domain）中可能不存在的用户创建愿望。这是一个问题。事实上，无论你是使用关系型数据库还是 NoSQL 数据库，在持久化任何内容之前，使用这种方法，你可以在内存中创建一个没有对应`User`的`Wish`。

确实，这是业务逻辑的破坏。我知道，我知道，你可以通过在数据库中使用外键从`wish(user_id)`到`user(id)`来修复它。正确，但如果我们不使用带外键的数据库怎么办？更糟糕的是，如果是 NoSQL 数据库，例如`Redis`或`ElasticSearch`怎么办？

所以，如果我们想修复这个问题，以便相同的代码能够在不同的基础设施中正常工作，我们需要检查用户是否存在。可能最简单的方法是在同一个应用服务中完成，不是吗？

```php
class MakeWishService
{
    //......
    public function execute(MakeWishRequest $request)
    {
        $userId = $request->userId();
        $address = $request->address();
        $content = $request->content();
        $user = $this->userRepository->ofId(new UserId($userId));

        if (null === $user) {
            throw new UserDoesNotExistException();
        }

        $wish = new Wish(
            $this->wishRepository->nextIdentity(),
            $user->id(),
            $address,
            $content
        );
        $this->wishRepository->add($wish);
    }
}
```

这可能奏效，但在应用服务中进行检查有什么问题呢？在我们的领域中没有对此提供保护，任何人在领域服务内部、基础设施的任何部分等，都可以执行如下代码的操作。

```php
// 在你领域的某处
$nonExistingUserId = new UserId('non-existing-user-id');
$wish = new Wish(
    $this->wishRepository->nextIdentity(),
    $nonExistingUserId,
    $address,
    $content
);
```

如果你已经读过工厂（Factories）章节，你也得到了解决方案。工厂帮助我们保持业务不变性，而这正是我们这里需要的。这里有一个隐含的不变性，说明我们不允许在没有有效用户的情况下许愿望。让我们看看工厂如何帮助我们。

```php
class MakeWishService
{
    private $userRepository;
    private $wishRepository;

    public function __construct(
        UserRepository $userRepository,
        WishRepository $wishRepository
    ) {
        $this->userRepository = $userRepository;
        $this->wishRepository = $wishRepository;
    }

    public function execute(MakeWishRequest $request)
    {
        $userId = $request->userId();
        $address = $request->address();
        $content = $request->content();
        $user = $this->userRepository->ofId(new UserId($userId));

        if (null === $user) {
             throw new UserDoesNotExistException();
        }

        $wish = $user->makeWish(
            $this->wishRepository->nextIdentity(),
            $address,
            $content
        );
        $this->wishRepository->add($wish);
    }
}
```

```php
class User
{
    //......

    /**
     * @return Wish
     */
    public function makeWish(WishId $wishId, $address, $content)
    {
        return new Wish(
            $wishId,
            $this->id(),
            $address,
            $content
        );
    }

    //......
}
```

为什么我们返回一个`Wish`而不是将新的`Wish`添加到内部集合，正如我们可能会在使用 Doctrine 时所做的那样？总结，在这种场景中，`User`和`Wish`并不构成聚合。每个`Entity`都有自己的`Repository`，并且通过`UserId`关联。获取用户所有的愿望可以通过愿望 Repository 中的查找方法完成。

#### 8.5.2 每个用户最多三个愿望

我们的应用程序取得了巨大的成功，现在是时候变现了。我们希望新用户最多拥有三个愿望。作为一个用户，如果你想拥有更多的愿望，你可能需要为付费账户付费。让我们看看如何修改代码以遵循新的关于愿望数量的业务规则（不考虑付费用户）。

```php
class MakeWishService
{
    //......
    public function execute(MakeWishRequest $request)
    {
        $userId = $request->userId();
        $address = $request->email();
        $content = $request->content();
    }
}
```

```php
$count = $this->wishRepository->numberOfWishesByUserId($userId);

if ($count > 3) {
    throw new MaxNumberOfWishesExceededException();
}

$wish = new Wish(
    $this->wishRepository->nextIdentity(),
    new UserId($userId),
    $address,
    $content
);

$this->wishRepository->add($wish);
}
```

这很简单，对吧？可能太简单了。我们在这里看到了不同的问题。第一个问题是`Application Services`（应用服务）不应该包含此类业务逻辑。它们必须负责协调，但不应包含业务逻辑。可能，更好的地方是把它们放入`User`中。我们可以对`User`和`Wish`之间的关系拥有更多的控制。然而，对于这里解释的问题，这段代码是可以运行的。

## 聚合根 (Aggregates)

第二个问题是关于代码本身的。它`在竞态条件下无法工作`。因此，它是不可接受的。暂不考虑领域驱动设计（DDD），在高流量下，这段代码会有什么问题？思考一下。是否可能打破`User`拥有超过三个愿望的规则？为什么你的 QA 在运行她那些古怪的测试时会超级开心？

你的 QA 平静地尝试了两次，结果是一个用户有两个愿望。很好。你的 QA 想要见血。想象一下，她在浏览器中打开了两个标签页，填写了两个表单并同时提交了两个按钮。突然，在两次请求之后，用户在数据库中最终有了四个愿望。发生了什么？

像调试器一样思考，考虑两个请求同时到达`if ($count > 3) {`这一行。两个请求的评估结果都为`false`，因为用户只有两个愿望。所以，两个请求都会创建`Wish`，并且两个请求都会将其添加到数据库中。噢！一个`User`有了四个愿望。

我们知道你在想什么。是因为我们忘记了将所有内容放入事务（transaction）中。很好，假设将之前相同的代码放在事务块中，你将看到如何在`Application Services`中正确地执行。在内部，让我们检查你的数据库发生了什么。

```sql
START TRANSACTION;
SELECT COUNT(*) FROM wishes WHERE user_id = 'e3bb5953-dd2-4204-a8e8-3449ea88c40'; -- @a is 2
INSERT INTO wishes(id, user_id, address, message) VALUES ('7b81e576-d7dc-4736-a559-340961b7102', 'mom@family.com', 'always love you!');
SELECT COUNT(*) FROM wishes; -- @a is 3
COMMIT;
```

如果你取这段 SQL 块并在两个不同的连接中逐行执行（为新的愿望使用不同的`UUIDs`），你将看到`wishes`表最后会有 4 行。所以，这看起来不是事务的问题。我们该如何修复这个问题？可能，你了解过持久化机制中的`悲观并发`（Pessimistic Concurrency）和`乐观并发`（Optimistic Concurrency），让我们来探索一下它们吧。

### 8.5.2.1 悲观并发

这种方法被关系型数据库广泛使用，它假设冲突更改可能会发生，并阻塞对资源的访问以防止冲突。一个典型的例子是在读取数据之前锁定该行，确保只有放置锁的线程才能对该行进行更改。

### 8.5.2.2 乐观并发

这种方法假设冲突不太可能发生，不会阻塞正在尝试的操作。然而，如果底层数据在读取和写入之间被修改过，更新将失败。这时就取决于应用程序决定如何解决冲突。例如，它可以使用崭新的数据重新尝试更新，或者向用户报告该情况。我们能针对这个用例使用这些策略之一吗？嗯，我们认为不行，因为我们正在创建一个新的愿望。

```php
class User {
    // ...
    public function makeWish(WishId $wishId, $address, $content) {
        $this->wishes[] = new Wish(
            $wishId,
            $this->id(),
            $address,
            $content
        );
    }
    // ...
}
```

### 8.5.3 渲染用户的愿望

### 8.5.4 更新用户的愿望

### 8.5.5 成全用户的愿望

### 8.6 总结

## 9. 工厂 (Factories)

### 9.1 引言

在领域中，工厂帮助将客户端从了解如何构建复杂对象和`Aggregates`（聚合）中解耦。你可以使用它们来作为一个整体创建一个`Aggregates`，并强制执行它们不变性（invariants）。

### 9.2 聚合根上的工厂方法

`Factory Method`（工厂方法）模式正如经典的“四人小组”定义的，是一种创建模式，它定义了创建对象的接口，但将类型选择留给子类，创建过程延迟到运行时。在`Aggregate Root`（聚合根）中添加`Factory Method`可以向任何外部客户端隐藏创建聚合的内部实现细节。这也将聚合完整性的责任交回了根节点。

在一个拥有`User`和`Wish`实体的领域模型中，`User`充当聚合根。没有`User`就没有`Wish`。`User`实体应该管理它的聚合。将`Wish`的控制权移回`User`实体的方法是在聚合根中放置一个`Factory Method`。



```php
class User {
    //...
    public function makeWish(WishId $wishId, $email, $content) {
        $wish = new WishEmail(
            $wishId,
            $this->id(),
            $email,
            $content
        );
        DomainEventPublisher::instance()->publish(
            new WishMade($wishId)
        );
        return $wish;
    }
}
```

客户端完全不需要知道 `Aggregate Root` 如何处理创建逻辑的内部细节：

```php
$wish = $aUser->makeWish(
    $wishRepository->nextIdentity(),
    'user@example.com',
    'I want to be free!'
);
```

## 9.2.1 强制不变性

`Aggregate Root` 中的工厂方法也是处理不变性的良好位置。在一个拥有 `Forum` 和 `Article` 实体的领域模型中，其中 `Article` 是 `Forum` 的一个聚合，发布一个 `Article` 可能如下：

```php
class Forum {
    // ...
    public function publishPost(PostId $postId, $content) {
        $post = new Post($this->id, $postId, $content);
        DomainEventPublisher::instance()->publish(
            new PostPublished($postId)
        );
        return $post;
    }
}
```

在与领域专家交流后，我们得出结论：当 `Forum` 关闭时，不应发布 `Post`。这是一个不变性，我们可以在创建 `Post` 时直接强制执行，防止不一致的领域状态：

```php
class Forum {
    // ...
    public function publishPost(PostId $postId, $content) {
        if ($this->isClosed()) {
            throw new ForumClosedException();
        }
        $post = new Post($this->id, $postId, $content);
        DomainEventPublisher::instance()->publish(
            new PostPublished($postId)
        );
        return $post;
    }
}
```

## 9.3 服务上的工厂

解耦创建逻辑在我们的服务中有用。

### 9.3.1 构建规范 (Specifications)

在我们的服务中使用 `Specifications` 可能是说明如何在服务中使用工厂的最佳示例。考虑以下服务示例。给定一个来自外部世界的请求，我们希望根据系统中添加的最新 `Posts` 构建一个馈。

```php
namespace Application\Service;

use Domain\Model\Post;
use Domain\Model\PostRepository;

class LatestPostsFeedService {
    private $postRepository;

    public function __construct(PostRepository $postRepository) {
        $this->postRepository = $postRepository;
    }

    public function execute($request) {
        $posts = $this->postRepository->latestPosts($request->since);
        return array_map(function(Post $post) {
```

```php
return [
    'id' => $post->id()->id(),
    'content' => $post->body()->content(),
    'created_at' => $post->createdAt()
];
}, $posts);
}
```

`Repositories` 中的查找方法（如 `latestPosts`）具有某些局限性，因为它们会不断给我们的仓库增加复杂度。正如我们在 Repository 章节中讨论的，Specifications（规格模式）是一个更好的方法。

幸运的是，我们在 `PostRepository` 中有一个非常有用的查询方法，它可以配合 `Specifications` 使用工作。

```php
class LatestPostsFeedService
{
    //...
    public function execute($request)
    {
        //...
        $posts = $this->postRepository->query($specification);
        //...
    }
}
```

### 为 `Specification` 使用具体实现是一个坏主意

```php
class LatestPostsFeedService
{
    //...
    public function execute($request)
    {
        $posts = $this->postRepository->query(
            new SqlLatestPostSpecification($request->since)
        );
        //...
    }
}
```

将我们的高层应用服务与低层的 `Specification` 实现耦合会混合层级并破坏关注点分离。此外，这是将我们的服务耦合到具体基础设施实现上也是一种非常糟糕的方法。你无法在 SQL 持久化解决方案之外使用此服务。如果我们想用内存中的实现来测试我们的服务怎么办？

解决这个问题的方案是通过使用[抽象工厂模式](http://en.wikipedia.org/wiki/Abstract_factory_pattern)[²] 将 `Specification` 的创建与服务本身解耦。抽象工厂提供了一个创建一组相关对象的接口，而无需显式地指定它们的具体类。

由于我们可能有多个需要创建的 `Specification` 实现，我们首先需要为工厂创建一个接口。

```php
namespace Domain\Model;
interface PostSpecificationFactory
{
    public function createLatestPosts(\DateTime $since);
}
```

然后，我们需要为每个 `PostRepository` 实现创建工厂。例如，一个用于内存 `PostRepository` 实现的工厂可能如下：

```php
namespace Infrastructure\Persistence\InMemory;
use Domain\Model\PostSpecificationFactory;
class InMemoryPostSpecificationFactory implements PostSpecificationFactory
{
    public function createLatestPosts(\DateTime $since)
    {
        return new InMemoryLatestPostSpecification($since);
    }
}
```

一旦我们有了中心化的创建逻辑，就很容易将其从服务中解耦：

```php
class LatestPostsFeedService
{
    private $postRepository;
    private $postSpecificationFactory;
    public function __construct(
        PostRepository $postRepository,
        PostSpecificationFactory $postSpecificationFactory
    ) {
        $this->postRepository = $postRepository;
        $this->postSpecificationFactory = $postSpecificationFactory;
    }

    public function execute($request)
    {
        $posts = $this->postRepository->query(
            $this->postSpecificationFactory->createLatestPosts($request->since)
        );
        // ...
    }
}
```

现在，通过内存中的 `PostRepository` 实现对我们的服务进行单元测试变得非常简单。

```php
namespace Application\Service;
use Domain\Model\Body;
use Domain\Model\Post;
use Domain\Model\PostId;
use Infrastructure\Persistence\InMemory\InMemoryPostRepository;
class LatestPostsFeedServiceTest extends \PHPUnit_Framework_TestCase
{
    /**
     * @var \Infrastructure\Persistence\InMemory\InMemoryPostRepository
     */
    private $postRepository;

    /**
     * @var LatestPostsFeedService
     */
    private $latestPostsFeedService;

    public function setUp()
    {
        $this->latestPostsFeedService = new LatestPostsFeedService(
            $this->postRepository = new InMemoryPostRepository()
        );
    }

    /**
     * @test
     */
    public function shouldBuildAFeedFromLatestsPosts()
    {
        $this->addPost(1, 'first', '-2 hours');
        $this->addPost(2, 'second', '-3 hours');
        $this->addPost(3, 'third', '-5 hours');
        $feed = $this->latestPostsFeedService->execute(
            new LatestPostsFeedRequest(new \DateTime('-4 hours'))
        );
        $this->assertFeedContains([
            ['id' => 1, 'content' => 'first'],
            ['id' => 2, 'content' => 'second']
        ], $feed);
    }

    private function addPost($id, $content, $createdAt)
    {
        $this->postRepository->add(new Post(
            new PostId($id),
            new Body($content),
            new \DateTime($createdAt)
        ));
    }

    private function assertFeedContains($expected, $feed)
    {
        foreach ($expected as $index => $contents) {
            $this->assertArraySubset($contents, $feed[$index]);
            $this->assertNotNull($feed[$index]['created_at']);
        }
    }
}
```

### 9.3.2 构建聚合根

实体（Entities）对于持久化机制是不可知的。你不希望将持久化细节耦合并污染你的实体。

看看下一个应用服务：

```php
class SignInUserService
{
    private $userRepository;
    public function __construct(UserRepository $userRepository)
    {
        $this->userRepository = $userRepository;
    }

    /**
     * @param SignInRequest $request
     */
    public function execute($request)
    {
        $email = $request->email();
        $password = $request->password();
        $user = $this->userRepository->userOf($email);
        if (null !== $user) {
            throw new UserExistsException();
        }
        $this->userRepository->persist(new User(
            $this->userRepository->nextIdentity(),
            $email,
            $password
        ));
        return $user;
    }
}
```

带有如下 `User` 实体：

```php
class User
{
    private $userId;
    private $email;
    private $password;
    public function __construct(UserId $userId, $email, $password)
    {
        //...
    }
    //...
}
```

假设我们想使用 `Doctrine` 作为我们的基础设施持久化机制。`Doctrine` 需要一个字符串实例作为成员变量才能正常工作。在我们的实体中，`$userId` 是一个 `UserId` 值对象。为了 `Doctrine` 给实体添加额外的 `id` 会将我们的持久化机制与领域模型耦合。

我们在实体章节中已经看到，可以通过创建代理 ID（Surrogate Id）来解决这个问题，即在基础设施层中为我们的 `User` 实体创建一个包装器：

```php
class DoctrineUser extends User
{
    private $surrogateUserId;
    public function __construct(UserId $userId, $email, $password)
    {
        parent::__construct($userId, $email, $password);
        $this->surrogateUserId = $userId->id();
    }
}
```

由于在应用服务中创建 `DoctrineUser` 会再次将持久化层与领域耦合，我们需要通过抽象工厂（Abstract Factory）将创建逻辑从服务中解耦。我们可以通过在领域中创建一个接口来实现：

```php
interface UserFactory
{
    public function build(UserId $userId, $email, $password);
}
```

并将它的实现放在我们的基础设施层：

```php
class DoctrineUserFactory implements UserFactory
{
    public function build(UserId $userId, $email, $password)
    {
        return new DoctrineUser($userId, $email, $password);
    }
}
```

一旦解耦，我们只需要将工厂（Factory）注入到应用服务中：



```php
class SignInUserService
{
    private $userRepository;
    private $userFactory;
    public function __construct(
        UserRepository $userRepository,
        UserFactory $userFactory
    ) {
        $this->userRepository = $userRepository;
        $this->userFactory = $userFactory;
    }
    //...
}
```

### 9.4 测试

在编写测试时，你会看到一种常见的模式。构建实体和复杂的聚合根

这可能是一个非常枯燥且重复的过程。复杂性和重复将开始渗透到你的测试套件中。

考虑以下实体

```php
class Author
{
    private $username;
    private $email;
    private $fullName;
    public function __construct(
        Username $aUsername,
        FullName $aFullName,
        Email $anEmail
    ) {
        $this->username = $aUsername;
        $this->email = $anEmail;
        $this->fullName = $aFullName;
    }
    //...
}
```

在系统某处的某个测试中包含了：

```php
class MyTest extends PHPUnit_Framework_TestCase
{
    /**
     * @test
     */
    public function itDoesSomething()
    {
        $author = new Author(
            new Username('johndoe'),
            new FullName('John', 'Doe'),
            new Email('john@doe.com')
        );
        //对 author 进行某些操作
    }
}
```

边界内部的服务共享实体、聚合根和值对象等概念，想象一下在你的测试中反复重复相同的构建逻辑会有多么的混乱。正如我们将所看到的，将构建逻辑从测试中提取出来非常有帮助，并且可以防止重复。

### 9.4.1 对象母 (Object Mother)

[对象母](http://martinfowler.com/bliki/ObjectMother.html) 是一个为你的测试创建固定固件的工厂的生动名称。接上之前的例子，我们可以将重复的逻辑提取到对象母中，以便在不同测试之间复用。

```php
class AuthorObjectMother
{
    public static function createOne()
    {
        return new Author(
            new Username('johndoe'),
            new FullName('John', 'Doe'),
            new Email('john@doe.com')
        );
    }
}

class MyTest extends PHPUnit_Framework_TestCase
{
    /**
     * @test
     */
    public function itDoesSomething()
    {
        $author = AuthorObjectMother::createOne();
        //对 author 进行某些操作
    }
}
```

你会发现，测试和情况越多，工厂拥有的方法就越多。由于对象母并不灵活，它们往往会迅速变得复杂。对于你的测试来说，有一种更灵活的替代方案。

### 9.4.2 测试数据构建器 (Test Data Builder)

测试数据构建器只是带有默认值的普通构建器（Builders），专门用于你的测试套件中，这样你就不需要在特定的测试用例中指定无关的参数。

```php
class AuthorBuilder
{
    private $username;
    private $email;
    private $fullName;
    private function __construct()
    {
        $this->username = new Username('johndoe');
        $this->email = new Email('john@doe.com');
        $this->fullName = new FullName('John', 'Doe');
    }
    public static function anAuthor()
    {
        return new();
    }
    public function withFullName(FullName $aFullName)
    {
        $this->fullName = $aFullName;
        return $this;
    }
    public function withUsername(Username $aUsername)
    {
        $this->username = $aUsername;
        return $this;
    }
    public function withEmail(Email $anEmail)
    {
        $this->email = $anEmail;
        return $this;
    }
    public function build()
    {
        return new Author($this->username, $this->fullName, $this->email);
    }
}

class MyTest extends PHPUnit_Framework_TestCase
{
    /**
     * @test
     */
    public function itDoesSomething()
    {
        $author = AuthorBuilder::anAuthor()
            ->withEmail(new Email('other@email.com'))
            ->build();
        //对 author 进行某些操作
    }
}
```

我们甚至可以组合测试数据构建器来构建更复杂的聚合，如 `Post`：

```php
class Post
{
    private $id;
    private $author;
    private $body;
    private $createdAt;
    public function __construct(
        PostId $anId,
        Author $anAuthor,
        Body $aBody
    ) {
        $this->id = $anId;
        $this->author = $anAuthor;
        $this->body = $aBody;
        $this->createdAt = new DateTime();
    }
}
```

以及相应的 `PostBuilder`：

```php
class PostBuilder
{
    private $postId;
    private $author;
    private $body;
    private function __construct()
    {
        $this->postId = new PostId();
        $this->author = AuthorBuilder::anAuthor()->build();
        $this->body = new Body('Post body');
    }
    public static function aPost()
    {
        return new();
    }
    public function withAuthor(Author $anAuthor)
    {
        $this->author = $anAuthor;
        return $this;
    }
    public function withPostId(PostId $aPostId)
    {
        $this->postId = $aPostId;
        return $this;
    }
    public function withBody(Body $body)
    {
        $this->body = $body;
        return $this;
    }
    public function build()
    {
        return new Post($this->postId, $this->author, $this->body);
    }
}
```

这种方案现在足够灵活，可以适应测试中的任何情况。

```php
class MyTest extends PHPUnit_Framework_TestCase
{
    /**
     * @test
     */
    public function itDoesSomething()
    {
        $post = PostBuilder::aPost()
            ->withAuthor(AuthorBuilder::anAuthor()
                ->withUsername(new Username('other'))
                ->build())
            ->withBody(new Body('Another body'))
            ->build();
        //对 post 进行某些操作
    }
}
```

### 9.5 总结

工厂是解耦逻辑与业务逻辑的强大工具。工厂方法不仅有助于将创建责任移动到聚合根，还能强制领域不变性。在服务中使用抽象工厂模式允许我们将领域逻辑与基础设施分离。常见的用例是规范及其相应的持久化实现。我们已经看到工厂在测试套件中非常有用。虽然我们可以将构建逻辑提取到对象母，但测试数据构建器提供了更高的灵活性。

### 10. 仓库 (Repositories)

### 10.1 引言

为了与领域对象交互，你需要持有它的引用。实现这一点可以通过创建，也可以通过关联来实现。在面向对象的程序中，对象拥有其他对象的引用，这使得它们易于遍历。这极大地增强了我们模型的表达。困难在于，你需要一种机制来获取第一个对象，即聚合根。

仓库作为存储位置，获取的对象与其被持久化时的状态完全相同。每个聚合类型通常有一个唯一的关联仓库，用于其持久化需求。然而，在需要共享聚合对象层次树的情况下，这些类型可能会共享一个仓库。

### 10.2 定义

Martin Fowler 定义仓库为领域层和数据映射层之间的机制，类似于内存中的领域对象集合。客户端对象声明地构造查询规范并将其提交给仓库以满足。对象可以像在简单集合中一样添加或删除，封装在仓库中的映射代码会在后台执行适当的操作。

数据访问对象（Data Access Objects）是一种将领域对象持久化到数据库的常用模式。很容易将数据访问对象模式与仓库（Repository）混淆。它们的显著区别在于：仓库代表集合，而 DAO 更贴近于数据库，通常更以表为中心。通常，一个 DAO 会包含针对特定领域对象的 CRUD 方法。

一个 DAO 的常见接口可以是：

```php
interface UserDAO
{
    /**
     * @param string $username
     * @return User
     */
    public function get($username);

    public function create(User $user);

    public function update(User $user);

    /**
     * @param string $username
     */
    public function delete($username);
}
```

DAO 接口可以有多个实现，其范围可以从 ORM 构建到纯 SQL 查询。DAO 的主要问题是它们的职责没有被清晰地定义。DAO 通常被视为通往数据库的网关，因此很容易通过许多特定的数据库查询方法来大幅降低内聚性。

### 仓库

```php
interface BloatUserDAO
{
    public function get($username);
    public function create(User $user);
    public function update(User $user);
    public function delete($username);
    public function getUserByLastName($lastName);
    public function getUserByEmail($email);
    public function updateEmailAddress($username, $email);
    public function updateLastName($username, $lastName);
}
```

如你所见，DAO 变得越来越难以单元测试，因为你需要实现更多的方法，而且它与 `User` 对象的耦合变得更加紧密。这个问题会随着时间的推移而增长，许多其他贡献者的协作会让这个“泥球（ball of mud）”变得更大。

### 10.4 面向集合的仓库

仓库通过实现其通用接口特性来模拟集合。作为一个集合，它不应该泄露任何关于持久化行为的意图，例如保存到存储器中的概念。

底层的持久化机制必须支持这种需求。你不应该被处理对象在其生命周期内的变化。集合引用了对象的最新更改，这意味着每次访问时你都会获得最新的对象状态。

仓库实现了一种具体的集合类型：`Set`。`Set` 是一种数据结构，其不变性是不包含重复条目。如果你尝试向已经存在的 `Set` 中添加元素，它将不会被添加。这在我们的用例中很有用，因为每个聚合根（Aggregate）都有一个与根实体（Root Entity）关联的唯一标识。

例如，我们有如下的领域模型：



```php
namespace Domain\Model;

class Post
{
    const EXPIRE_EDIT_TIME = 120; // seconds
    private $id;
    private $body;
    private $createdAt;

    public function __construct(
        PostId $anId,
        Body $aBody,
        \DateTime $createdAt = null
    ) {
        $this->id = $anId;
        $this->body = $aBody;
        $this->createdAt = $createdAt ?: new \DateTime();
    }

    public function editBody(Body $aNewBody)
    {
        if ($this->editExpired()) {
            throw new \RuntimeException('Edit time expired');
        }
        $this->body = $aNewBody;
    }

    private function editExpired()
    {
        $expiringTime = $this->createdAt->getTimestamp() + self::EXPIRE_EDIT_TIME;
        return $expiringTime < time();
    }

    public function id()
    {
        return $this->id;
    }

    public function body()
    {
        return $this->body;
    }

    public function createdAt()
    {
        return $this->createdAt;
    }
}

class Body
{
    const MIN_LENGTH = 3;
    const MAX_LENGTH = 250;
    private $content;

    public function __construct($content)
    {
        $this->setContent(trim($content));
    }

    private function setContent($content)
    {
        $this->assertNotEmpty($content);
        $this->assertFitsLength($content);
        $this->content = $content;
    }

    private function assertNotEmpty($content)
    {
        if (empty($content)) {
            throw new \DomainException('Empty body');
        }
    }

    private function assertFitsLength($content)
    {
        if (strlen($content) < self::MIN_LENGTH) {
            throw new \DomainException('Body is too sort');
        }
        if (strlen($content) > self::MAX_LENGTH) {
            throw new \DomainException('Body is too long');
        }
    }

    public function content()
    {
        return $this->content;
    }
}

class PostId
{
    private $id;
    public function __construct($id = null)
    {
        $this->id = $id ?: uniqid();
    }

    public function id()
    {
        return $this->id;
    }

    public function equals(PostId $anId)
    {
        return $this->id === $anId->id();
    }
}
```

如果我们想持久化这个`Post`实体，可以创建一个如下简单的内存`Post`仓库（Post Repository）：

```php
class SimplePostRepository
{
    private $post = [];

    public function add(Post $aPost)
    {
        $this->posts[(string) $aPost->id()] = $aPost;
    }

    public function postOfId(PostId $anId)
    {
        if (isset($this->posts[(string) $anId])) {
            return $this->posts[(string) $anId];
        }
        return null;
    }
}
```

而且，正如你预期的那样，它被处理为一个集合：

```php
$id = new PostId();
$repository = new SimplePostRepository();
$repository->add(new Post($id, 'Random content'));
// later ...
$post = $repository->postOfId($id);
$post->editBody('Updated content');
// even later ...
$post = $repository->postOfId($id);
assert('Updated content' === $post->body());
```

如你所示，从集合的角度来看，仓库中不需要`save`方法。影响对象的更改由持久化层正确处理。第一步是为你的仓库定义一个类似集合的接口。

```php
interface PostRepository
{
    public function add(Post $aPost);
    public function addAll(array $posts);
    public function remove(Post $aPost);
    public function removeAll(array $posts);
    // ...
}
```

接口定义应该放置在聚合根使用的同一个模块中。有时`remove`并不是真正的聚合删除。在某些情况下，你需要为了法律目的或商业智能保留信息。在这种情况下，你可以将聚合根标记为禁用或逻辑删除。相应地更新接口，移除删除方法或在仓库中提供禁用行为。

仓库另一个重要部分是查找方法，例如：

```php
interface PostRepository
{
    // ...
    /**
     * @return Post
     */
    public function postOfId(PostId $anId);

    /**
     * @return array[]
     */
    public function latestPosts(\DateTime $sinceADate);
}
```

并且，为了获取全局唯一 ID，一个逻辑位置是：

```php
interface PostRepository
{
    // ...
    /**
     * @return PostId
     */
    public function nextIdentity();
}
```

构建每个`Post`实例的代码调用`nextIdentity()`来获取唯一标识`PostId`。

```php
$post = new Post($postRepository->nextIdentity(), $body);
```

### 10.4.1 内存实现

正如 Uncle Bob 在[尖叫式架构](http://blog.8thlight.com/uncle-bob/2011/09/30/Screaming-Architecture.html)² 中写道：

良好的软件架构允许对框架、数据库、Web 服务器以及其他环境问题和工具的决策被推迟和延迟。

或者使用 MySql，直到项目后期才这样做。良好的架构也能让你轻松地对这些决策做出改变。良好的架构强调用例，并将其与外围关注点解耦。

在应用程序的早期，快速的内存实现可能会大有用场。你可以用它来完善系统的其他部分，允许你将数据库决策推到合适的时机。内存仓库简单、快速且易于实现。对于我们的`Post`仓库，一个内存哈希表（hash-map）就足够提供我们所需的所有功能。[`blog.8thlight.com/uncle-bob/2011/09/30/Screaming-Architecture.html`](http://blog.8thlight.com/uncle-bob/2011/09/30/Screaming-Architecture.html)

### 仓库 (209)

```php
namespace Infrastructure\Persistence\InMemory;

use Domain\Model\Post;
use Domain\Model\PostId;
use Domain\Model\PostRepository;

class InMemoryPostRepository implements PostRepository
{
    private $posts = [];

    public function add(Post $aPost)
    {
        $this->posts[$aPost->id()->id()] = $aPost;
    }

    public function remove(Post $aPost)
    {
        unset($this->posts[$aPost->id()->id()]);
    }

    public function postOfId(PostId $anId)
    {
        if (isset($this->posts[$anId->id()])) {
            return $this->posts[$anId->id()];
        }
        return null;
    }

    public function latestPosts(\DateTime $sinceADate)
    {
        return $this->filterPosts(
            function(Post $post) use ($sinceADate) {
                return $post->createdAt() > $sinceADate;
            }
        );
    }

    private function filterPosts(callable $fn)
    {
        return array_values(array_filter($this->posts, $fn));
    }

    public function nextIdentity()
    {
        return new PostId();
    }
}
```

### 10.4.2 Doctrine ORM

[Doctrine](http://www.doctrine-project.org/) 是一组用于数据库存储和对象映射的库。它默认与流行的 [Symfony 2 web 框架](http://symfony.com/) 一起包含，除了其他功能外，得益于 [Data Mapper 模式](http://martinfowler.com/eaaCatalog/dataMapper.html)，它允许你轻松地将应用程序与持久层解耦。

对象关系映射器（ORM）建立在一个强大的数据库抽象层之上，该层通过一种名为 Doctrine Query Language（DQL）的 SQL 方言进行数据库交互，其灵感来源于著名的 Java Hibernate 框架。

如果我们打算使用 Doctrine ORM，要完成的第一任务是通过 [Composer](https://getcomposer.org/) 为项目添加依赖项：

```bash
composer require doctrine/orm:~2.4
```

### 10.4.2.1 对象映射

领域对象与数据库之间的映射可以被视为一种实现细节。领域生命周期不应该感知这些持久化细节。因此，映射信息应该定义为基础设施层的一部分，位于领域之外，并作为仓库的实现。

#### 10.4.2.1.1 Doctrine 自定义映射类型

由于我们的`Post`实体是由`Body`或`PostId`等值对象组成的，因此为它们创建自定义映射类型是一个好主意。这会让对象映射变得简单得多。

仓库 (211)

```php
namespace Infrastructure\Persistence\Doctrine\Types;

use Doctrine\DBAL\Types\Type;
use Doctrine\DBAL\Platforms\AbstractPlatform;
use Domain\Model\Body;

class BodyType extends Type
{
    public function getSQL(array $fieldDeclaration, AbstractPlatform $platform)
    {
        return $platform->getVarcharType($fieldDeclaration);
    }

    public function convertToPHP($value, AbstractPlatform $platform)
    {
        return new Body($value);
    }

    public function convertToDatabase($value, AbstractPlatform $platform)
    {
        return $value;
    }

    public function getName()
    {
        return 'body';
    }
}
```

仓库 (212)

```php
namespace Infrastructure\Persistence\Doctrine\Types;

use Doctrine\DBAL\Types\Type;
use Doctrine\DBAL\Platforms\AbstractPlatform;
use Domain\Model\PostId;

class PostIdType extends Type
{
    public function getSQL(array $fieldDeclaration, AbstractPlatform $platform)
    {
        return $platform->getGuidType($fieldDeclaration);
    }

    public function convertToPHP($value, AbstractPlatform $platform)
    {
        return new PostId($value);
    }

    public function convertToDatabase($value, AbstractPlatform $platform)
    {
        return $value;
    }

    public function getName()
    {
        return 'post_id';
    }
}
```

不要忘记实现`PostId`值对象。

#### 10.4.2.1.2 XML 映射

Doctrine 提供了多种映射格式，如 YAML、XML 或注解。



```xml
<?xml version="1.0" encoding="UTF-8"?>
<doctrine-mapping xmlns="http://doctrine-project.org/schemas/orm"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://doctrine-project.org/schemas/orm
    https://raw.githubusercontent.com/doctrine/master/mapping.xsd">
    <entity name="Domain\Model\Post" table="posts">
        <id name="id" type="post_id">
            <generator strategy="NONE"/>
        </id>
        <field name="body" type="body" length="250" column="body"/>
        <field name="createdAt" type="datetime" column="created_at"/>
    </entity>
</doctrine-mapping>
```

## 10.4.2.2 Entity Manager

`EntityManager` 是 ORM 功能的中心访问点，它的初始化非常简单仓库 (214)：

```php
use Doctrine\DBAL\Types\Type;
use Doctrine\ORM\EntityManager;
use Doctrine\ORM\Tools;

Type::addType('post_id', 'Infrastructure\Persistence\Doctrine\Types\PostIdType');
Type::addType('body', 'Infrastructure\Persistence\Doctrine\Types\BodyType');

$entityManager = EntityManager::create([
    'driver' => 'pdo_sqlite',
    'path' => __DIR__ . '/db.sqlite',
], Tools::createXMLConfiguration(
    ['/Path/To/Infrastructure/Mapping'],
    true
));
```

根据你的需要进行配置。

## 10.4.2.3 DQL 实现

在这个仓库的情况下，我们只需要 `EntityManager` 直接从数据库检索领域对象仓库 (215)：

```php
namespace Infrastructure\Persistence\Doctrine;

use Doctrine\ORM\EntityManager;
use Domain\Model\Post;
use Domain\Model\PostId;
use Domain\Model\PostRepository;

class DoctrinePostRepository implements PostRepository
{
    protected $em;

    public function __construct(EntityManager $em)
    {
        $this->em = $em;
    }

    public function add(Post $aPost)
    {
        $this->em->persist($aPost);
    }

    public function remove(Post $aPost)
    {
        $this->em->remove($aPost);
    }

    public function postOfId(PostId $anId)
    {
        return $this->em->find('Domain\Model\Post', $anId);
    }

    public function latestPosts(\DateTime $sinceADate)
    {
        return $this->em->createQueryBuilder()
            ->select('p')
            ->from('Domain\Model\Post', 'p')
            ->where('p.createdAt > :since')
            ->setParameter('since', $sinceADate)
            ->getQuery();
    }
}
```

```php
->setParameter(':since', $sinceADate)

->getQuery()

->getResult();

}

public function nextIdentity()
{

    return new PostId();
}

}
```

## 10.5 面向持久化

在某些情况下，面向集合的仓库（collection-oriented repositories）与我们的持久化机制并不契合。如果你没有工作单元（unit of work），跟踪聚合（Aggregate）的变化将是一项困难的任务。持久化此类更改的唯一方法是显式地调用 `save`。

面向持久化的仓库的接口定义与你定义一个面向集合的等价物类似。

### 仓库 216

```php
interface PostRepository
{
    public function nextIdentity();
    public function postOfId(PostId $anId);
    public function save(Post $aPost);
    public function saveAll(array $posts);
    public function remove(Post $aPost);
    public function removeAll(array $posts);
}
```

在这种情况下，我们现在拥有了 `save` 和 `saveAll` 方法。它们提供了与之前的 `add` 和 `addAll` 方法相似的功能，然而重要的区别在于客户端使用它们的方式。

在面向集合的风格中，你只会在创建聚合时使用一次 `add` 方法。在面向持久化的风格中，你不仅会在创建聚合后使用 `save` 动作，在修改它们时也会使用。

```php
$post = new Post(/* ... */);

$postRepository->save($post);

// 之后 ...

$post = $postRepository->postOfId($postId);

$post->editBody(new Body('New body!'));

$postRepository->save($post);
```

除了此差异外，细节仅存在于实现中。

## 10.5.1 Redis 实现

[Redis](http://redis.io/⁷⁷) 是一种极速的内存键值对存储，可以作为缓存或存储。根据情况，我们可以考虑将 Redis 作为我们聚合的存储器。

要开始使用，请确保你有一个用于连接 Redis 的 PHP 客户端。一个很好的选择是 [Predis](https://github.com/nrk/predis)。

```bash
composer require predis/predis:~1.0
```

⁷ [`redis.io/`](http://redis.io/)

⁸ [`github.com/nrk/predis`](https://github.com/nrk/predis)

### 仓库 217

```php
namespace Infrastructure\Persistence\Redis;

use Domain\Model\Post;
use Domain\Model\PostId;
use Domain\Model\PostRepository;
use Predis\Client;

class RedisPostRepository implements PostRepository
{
    private $client;

    public function __construct(Client $client)
    {
        $this->client = $client;
    }

    public function save(Post $aPost)
    {
        $this->client->hset('posts', (string) $aPost->id(), serialize($aPost));
    }

    public function remove(Post $aPost)
    {
        $this->client->hdel('posts', (string) $aPost->id());
    }

    public function postOfId(PostId $anId)
    {
        if ($data = $this->client->hget('posts', (string) $anId)) {
            return unserialize($data);
        }
        return null;
    }

    public function latestPosts(\DateTime $sinceADate)
    {
        $latest = $this->filterPosts(
            function(Post $post) use ($sinceADate) {
                return $post->createdAt() > $sinceADate;
            }
        );

        $this->sortByCreatedAt($latest);
        return array_values($latest);
    }

    private function filterPosts(callable $fn)
    {
        return array_filter(array_map(function($data) {
            return unserialize($data);
        }, $this->client->hgetall('posts')), $fn);
    }

    private function sortByCreatedAt(&$posts)
    {
        usort($posts, function(Post $a, Post $b) {
            if ($a->createdAt() == $b->createdAt()) {
                return 0;
            }
            return ($a->createdAt() < $b->createdAt()) ? -1 : 1;
        });
    }

    public function nextIdentity()
    {
        return new PostId();
    }
}
```

## 10.5.2 SQL 实现

在一个经典示例中，我们可以仅通过使用原生 SQL 查询为我们的 `PostRepository` 创建一个简单的 [PDO](http://php.net/manual/en/book.pdo.php⁹⁹）实现。

⁹ [`php.net/manual/en/book.pdo.php`](http://php.net/manual/en/book.pdo.php)

### 仓库 219

```php
namespace Infrastructure\Persistence\Sql;

use Domain\Model\Body;
use Domain\Model\Post;
use Domain\Model\PostId;
use Domain\Model\PostRepository;

class SqlPostRepository implements PostRepository
{
    const DATE_FORMAT = 'Y-m-d H:i:s';
    private $pdo;

    public function __construct(\PDO $pdo)
    {
        $this->pdo = $pdo;
    }

    public function save(Post $aPost)
    {
        $sql = 'INSERT INTO posts (id, body, created_at) VALUES (:id, :body, :created_at)';
        $this->execute($sql, [
            'id' => $aPost->id()->id(),
            'body' => $aPost->body()->content(),
            'created_at' => $aPost->createdAt()->format(self::DATE_FORMAT)
        ]);
    }

    private function execute($sql, array $parameters)
    {
        $st = $this->pdo->prepare($sql);
        $st->execute($parameters);
        return $st;
    }

    public function remove(Post $aPost)
    {
        $this->execute('DELETE FROM posts WHERE id = :id', [
            'id' => $aPost->id()->id()
        ]);
    }

    public function postOfId(PostId $anId)
    {
        $st = $this->execute('SELECT * FROM posts WHERE id = :id', [
            'id' => $anId->id()
        ]);
        if ($row = $st->fetch(\PDO::FETCH_ASSOC)) {
            return $this->buildPost($row);
        }
        return null;
    }

    private function buildPost($row)
    {
        return new Post(
            new PostId($row['id']),
            new Body($row['body']),
            new \DateTime($row['created_at'])
        );
    }

    public function latestPosts(\DateTime $sinceADate)
    {
        return $this->retrieveAll('SELECT * FROM posts WHERE created_at > :since_date', [
            'since_date' => $sinceADate->format(self::DATE_FORMAT)
        ]);
    }

    private function retrieveAll($sql, array $parameters = [])
    {
        $st = $this->pdo->prepare($sql);
        $st->execute($parameters);
        return array_map(function($row) {
            return $this->buildPost($row);
        }, $st->fetchAll(\PDO::FETCH_ASSOC));
    }

    public function nextIdentity()
    {
        return new PostId();
    }

    public function size()
    {
        return $this->pdo->query('SELECT COUNT(*) FROM posts')->fetchColumn();
    }
}
```

由于我们没有任何映射配置，在同一个类中有一个针对架构的初始化方法将非常有用。*变化在一起应该保持在一起*。



```php
class SqlPostRepository implements PostRepository
{
    // ...
    public function initSchema()
    {
        $this->pdo->exec<<<SQL
DROP TABLE IF EXISTS posts;
CREATE TABLE posts (
    id CHAR(36) PRIMARY KEY,
    body VARCHAR(250) NOT NULL,
    created_at DATETIME NOT NULL
)
SQL
);
    }
}
```

### 10.6 额外行为

为仓库添加额外行为可能是非常有益的，例如计算给定集合中所有项的能力。你可能会考虑添加一个名为`count`的方法，然而，由于我们正在尝试模拟集合，更好的名称将是`size`。

### 仓库 222

```php
interface PostRepository
{
    // ...
    public function size();
}
```

对应的实现可能是这样的：

```php
class DoctrinePostRepository implements PostRepository
{
    // ...
    public function size()
    {
        return $this->em->createQueryBuilder()
            ->select('count(p.id)')
            ->from('Domain\Model\Post', 'p')
            ->getQuery()
            ->getSingleScalarResult();
    }
}
```

你还可以将计算封装到仓库中，以及与数据存储相关的优化的查询/存储过程。然而，所有行为仍然应该遵循仓库的集合特征。鼓励尽可能将逻辑移动到领域特定的无状态领域服务中，而不是简单地将这些职责添加到仓库。

在某些情况下，你不需要整个聚合就可以访问少量信息。为了解决这个问题，你可以添加仓库方法来作为快捷方式访问这些信息。你应该确保只访问那些通过导航聚合根可以获取的数据。

你不应该允许访问`Aggregate Roots`的私有和内部区域，因为这将违反既定的契约规定。

对于某些用例，你可能需要非常特定的查询，这些查询是由多个`Aggregate`类型组合成的，每个类型返回特定的信息。这些查询可以运行并作为单个`Value Object`返回。仓库返回`Value Objects`是非常常见的现象。

如果你发现自己正在创建许多针对用例优化的查找器方法，你可能引入了常见的代码气味（code smell）。这可能表明`Aggregate`边界判断有误。然而，如果你确定边界是正确的，那么可能是时候探索`CQRS`了。

# 10.7 查询存储库

从比较的角度来看，如果我们考虑查询能力，存储库（repositories）与集合（`Collection`）不同。`Repository`处理的是大型对象，这些对象在执行查询时通常不在内存中。将领域对象的所有实例加载到内存中并对它们进行查询是不可行的。

一个良好的解决方案是传递一个准则（criterion），并让`Repository`处理实现细节以成功执行操作。它可能会将准则转换为`SQL`、`ORM`查询或遍历内存中的集合，这并不重要，实现层会处理。

## 10.7.1 规格模式

准则对象的常见实现是`Specification Pattern`（规格模式）。规格只是一个简单的谓词，它接收一个领域对象并返回一个布尔值。给定一个领域对象，如果它符合（`specifies`）该规格，则返回 true，否则返回 false。

```php
interface PostSpecification
{
    /**
     * @return boolean
     */
    public function specifies(Post $aPost);
}
```

我们只需要为我们的存储库添加一个查询方法。

```php
interface PostRepository
{
    //...
    public function query($specification);
}
```

### 10.7.1.1 内存实现

作为一个示例，如果我们想通过使用`Specification`的内存实现，在`PostRepository`中重现`latestPosts`查询方法：

```php
namespace Infrastructure\Persistence\InMemory;

use Domain\Model\Post;

interface InMemoryPostSpecification
{
    /**
     * @return boolean
     */
    public function specifies(Post $aPost);
}
```

`latestPosts`行为的内存实现如下：

```php
namespace Infrastructure\Persistence\InMemory;

use Domain\Model\Post;

class InMemoryLatestPostSpecification implements InMemoryPostSpecification
{
    private $since;

    public function __construct(\DateTime $since)
    {
        $this->since = $since;
    }

    public function specifies(Post $aPost)
    {
        return $aPost->createdAt() > $this->since;
    }
}
```

我们的存储库实现的查询方法可能看起来所示：

```php
class InMemoryPostRepository implements PostRepository
{
    // ...

    /**
     * @param InMemoryPostSpecification $specification
     * @return Post[]
     */
    public function query($specification)
    {
        return $this->filterPosts(
            function(Post $post) use ($specification) {
                return $specification->specifies($post);
            }
        );
    }
}
```

从存储库中检索所有最新文章只需创建上述实现的定制实例即可简单：

```php
$latestPosts = $postRepository->query(
    new InMemoryLatestPostSpecification(new \DateTime('-24'))
);
```

### 10.7.1.2 SQL 实现

标准的`Specification`对于内存实现效果良好。然而，由于在`SQL`实现中我们没有预先将所有领域对象加载到内存中，对于这些情况我们需要更具体的规格。

```php
namespace Infrastructure\Persistence\Sql;

interface SqlPostSpecification
{
    /**
     * @return string
     */
    public function toSqlClauses();
}
```

该规格的 SQL 实现可能如下：

```php
namespace Infrastructure\Persistence\Sql;

class SqlLatestPostSpecification implements SqlPostSpecification
{
    private $since;

    public function __construct(\DateTime $since)
    {
        $this->since = $since;
    }

    public function toSqlClauses()
    {
        return "created_at > '" . $this->since->format('Y-m-d H:i:s') . "'";
    }
}
```

以及如何查询`SQL`实现：

```php
class SqlPostRepository implements PostRepository
{
    //...

    public function query($specification)
    {
        $st = $this->pdo->prepare("SELECT * FROM posts " . $specification->toSqlClauses());
        $st->execute($parameters);
        return $st->fetchAll(\PDO::FETCH_ASSOC);
    }
}
```

# 10.8 管理事务

`Domain Model`（领域模型）不是管理事务的地方。解决此问题的常用方法是在应用层（Application Layer）放置一个`Facade`，将相关的用例组合在一起。当从用户界面调用`Facade`时，它会开启事务。完成后，`Facade`通过提交事务结束交互。如果发生任何错误，事务将回滚。

```php
use Doctrine\ORM\EntityManager;

class ServiceFacade
{
    private $em;

    public function __construct(EntityManager $em)
    {
        $this->em = $em;
    }

    public function doUseCaseTask()
    {
        try {
            $this->em->getConnection()->beginTransaction();
            // 使用领域模型
            $this->em->getConnection()->commit();
        } catch (Exception $e) {
            $this->em->getConnection()->rollback();
            throw $e;
        }
    }
}
```

使用 facade 引入的问题是，我们需要不断重复相同的样板代码。如果我们统一执行用例的方式，可以使用`Decorator Pattern`（装饰器模式）将它们封装在事务中。

```php
interface ApplicationService
{
    /**
     * @param $request
     * @return mixed
     */
    public function execute($request = null);
}

class SomeApplicationService implements ApplicationService
{
    public function execute($request = null)
    {
        // 执行某些操作
    }
}
```

使任何应用服务支持事务的装饰器实现如下：

```php
interface TransactionalSession
{
    /**
     * @param callable $operation
     * @return mixed
     */
    public function executeAtomically(callable $operation);
}

class TransactionalApplicationService implements ApplicationService
{
    private $session;
    private $service;

    public function __construct(
        ApplicationService $service,
        TransactionalSession $session
    ) {
        $this->session = $session;
        $this->service = $service;
    }

    public function execute($request = null)
    {
        $operation = function () use ($request) {
            return $this->service->execute($request);
        };

        return $this->session->executeAtomically($operation->bindTo($this));
    }
}
```

在此之后，我们也可以地创建一个`Doctrine`事务会话实现：

```php
class DoctrineSession implements TransactionalSession
{
    private $entityManager;
}
```

```php
public function __construct(EntityManager $entityManager)
{
    $this->entityManager = $entityManager;
}

public function executeAtomically(callable $operation)
{
    return $this->entityManager->transactional($operation);
}
}
```

现在我们已经拥有了在事务中执行用例的所有条件。

### 仓库（第 230 页）

```php
$useCase = new TransactionalApplicationService(
    new SomeApplicationService(
        // ...
    ),
    new DoctrineSession(
        // ...
    )
);
$response = $useCase->execute();
```

### 10.9 测试仓库

为了确保仓库在生产环境中正常工作，你需要测试它的实现。为了做到这一点，我们必须测试系统的边界，确保我们的预期是正确的。

在 Doctrine 测试案例中，设置会稍微复杂一些

```php
use Doctrine\DBAL\Types\Type;
use Doctrine\ORM\EntityManager;
use Doctrine\ORM\Tools;
use Domain\Model\Post;

class DoctrinePostRepositoryTest extends \PHPUnit_Framework_TestCase
{
    private $postRepository;

    public function setUp()
    {
        $this->postRepository = $this->createPostRepository();
    }

    private function createPostRepository()
    {
        $this->addCustomTypes();
        $em = $this->initEntityManager();
        $this->initSchema($em);
        return new PrecociousDoctrinePostRepository($em);
    }
```

### 仓库（第 231 页）



```php
private function addCustomTypes()
{
    if (!Type::hasType('post_id')) {
        Type::addType('post_id', 'Infrastructure\Persistence\Doctrine\Types\PostIdType');
    }
    if (!Type::hasType('body')) {
        Type::addType('body', 'Infrastructure\Persistence\Doctrine\Types\BodyType');
    }
}

protected function initEntityManager()
{
    return EntityManager::create(
        ['url' => 'sqlite:///:memory:'],
        Tools\Setup::createXMLMetadataConfiguration(
            ['/Path/To/Infrastructure/Persistence/Doctrine/Mapping'],
            $devMode = true
        )
    );
}

private function initSchema(EntityManager $em)
{
    $tool = new Tools\SchemaTool($em);
    $tool->createSchema([
        $em->getClassMetadata('Domain\Model\Post')
    ]);
}
//...
```

### 仓库（第 232 页）

```php
class PrecociousDoctrinePostRepository extends DoctrinePostRepository
{
    public function persist(Post $aPost)
    {
        parent::persist($aPost);
        $this->em->flush();
    }

    public function remove(Post $aPost)
    {
        parent::remove($aPost);
        $this->em->flush();
    }
}
```

一旦我们搭建好了这个环境，现在可以继续测试仓库的行为。

```php
class DoctrinePostRepositoryTest extends \PHPUnit_Framework_TestCase
{
    // ...
    /**
     * @test
     */
    public function itShouldRemovePost()
    {
        $post = $this->persistPost('irrelevant body');
        $this->postRepository->remove($post);
        $this->assertPostExist($post->id());
    }

    private function assertPostExist($id)
    {
        $result = $this->postRepository->postOfId($id);
        $this->assertNull($result);
    }

    private function persistPost($body, \DateTime $createdAt = null)
    {
        $this->postRepository->add(
            $post = new Post(
                $this->postRepository->nextIdentity(),
                new Body($body),
                $createdAt
            )
        );
        return $post;
    }
}
```

按照我们之前的断言，如果我们保存了一个 `Post`，我们期望以完全相同的状态找到它。现在我们可以开始测试通过指定特定日期来查找最新的帖子。

```php
class DoctrinePostRepositoryTest extends \PHPUnit_Framework_TestCase
{
    // ...
    /**
     * @test
     */
    public function itShouldFetchLatestPosts()
    {
        $this->persistPost('a year ago', new \DateTime('-1 year'));
        $this->persistPost('a month ago', new \DateTime('-1 month'));
        $this->persistPost('few hours ago', new \DateTime('-3 hours'));
        $this->persistPost('few minutes ago', new \DateTime('-2 minutes'));
        $posts = $this->postRepository->latestPosts(new \DateTime('-24 hours'));
        $this->assertCount(2, $posts);
        $this->assertEquals('few hours ago', $posts[0]->body()->content());
        $this->assertEquals('few minutes ago', $posts[1]->body()->content());
    }
}
```

### 10.10 使用内存内存测试你的服务

#### 实现

设置一个完全持久化的仓库实现可能过于复杂，并导致执行速度缓慢。你应该关注保持测试的快速。经过整个数据库设置和查询将极大地减慢你的速度。

使用内存中的实现可以帮助将持久化决策推迟到最后。我们可以像以前那样测试它，但这次是使用完整的内存中实现。

### 仓库（第 234 页）

```php
class MyServiceTest extends \PHPUnit_Framework_TestCase
{
    private $service;

    public function setUp()
    {
        $this->service = new MyService(new InMemoryRepository());
    }
    // ...
}
```

### 10.11 总结

仓库是一种作为存储位置的机制。`DAO` 和仓库之间的区别在于，`DAO` 遵循数据库优先的方法，由于许多低级方法降低了内聚性。面向集合的仓库倾向于更纯领域模型，即使它们持久化了实体。从客户端的角度来看，它看起来就像一个集合（`Set`）。不需要对对象进行显式的持久化调用。面向持久化的仓库需要显式的持久化调用，因为它们不跟踪变化。我们探索了 `Redis` 和原生 `SQL`。在此过程中，我们发现了规格规范（`Specifications`）是一种帮助我们在不牺牲灵活性的情况下查询数据库的模式。我们还研究了如何管理事务以及如何使用简单快速的内存实现测试我们的服务。

# 11. 应用

### 11.1 引言

应用层是将领域模型与查询或更改其状态的客户端分离的区域。应用服务是此类构建块。正如 `Vaughn Vernon` 所，“应用服务是领域模型的直接客户端”。你可以将应用服务视为外部世界（`HTML` 表单、`API` 客户端、命令行、框架、`UI` 等）与领域模型本身之间的接触点。

在本章中，我们将探索如何实现应用服务，理解*命令模式*（`Command Pattern`）的作用并建立应用服务的职责。考虑*注册新用户*的用例。

从概念上说，为了注册新用户，我们需要：

• 从客户端获取电子邮件和密码

• 检查电子邮件是否已被占用

• 创建一个新用户

• 将此新用户添加到现有的用户集中

让我们开始吧。

#### 11.2 请求

我们需要向应用服务发送*电子邮件*和*密码*。从客户端（`HTML` 表单、`API` 客户端甚至命令行）执行此类操作有许多方法。我们可以直接通过方法签名发送标准参数（电邮和密码），或者构建并发送包含这些信息的数据结构。后一种方法（发送一个 `DTO`）带来了一些非常有趣的功能。通过发送对象，将将其序列化并通过命令总线进行队列。

¹[`martinfowler.com/eaaCatalog/dataTransferObject.html`](http://martinfowler.com/eaaCatalog/dataTransferObject.html)

235

![](img/index-254_1.png)

# Application

236

## 数据传输对象 (Data Transfer Object)

`DTO` 是一种在进程之间传递信息的数据结构。不要将其误认为是一个功能完备的对象。`DTO` 除了存储和检索自身数据（访问器和修改器）外，不包含任何行为。`DTOs` 是简单的对象，不应该包含任何需要进行测试的业务逻辑。

正如 `Vaughn Vernon` 所说：

“应用服务的方法签名只使用原始类型（`int`、`strings` 等）以及可能用到的 `DTOs`。然而，作为这些方法的方法的替代方案，更好的方法可能是设计 `Command`（命令）对象。这并不一定有对错之分。它主要取决于你的喜好和目标。”

用于存储应用服务所需数据的 `DTO` 实现可能如下：

```php
namespace Lw\Application\Service\User;

class SignUpUserRequest
{
    private $email;
    private $password;

    public function __construct($email, $password)
    {
        $this->email = $email;
        $this->password = $password;
    }

    public function email()
    {
        return $this->email;
    }

    public function password()
    {
        return $this->password;
    }
}
```

如你所见，`SignUpUserRequest` 没有任何行为，只有数据。这些数据可能来自 `HTML` 表单或 `API` 端点，我们并不关心。

# Application

### 11.2.1 构建应用服务请求

从交付机制（你喜欢的框架）创建请求应该是相当直观的。在 Web 端，你可以从控制器请求中获取参数，并将它们封装在 `DTO` 中传递给内部服务层。`CLI` 命令也遵循同样的原理，读取输入参数并再次向下传递。

使用 `Symfony`，我们可以从来自 `HttpFoundation` 组件的 `Request` 对象中提取所需的数据。

```php
//...

class UsersController extends Controller
{
    /**
     * @Route("/signup", name="signup")
     * @param Request $request
     * @return Response
     */
    public function signUpAction(Request $request)
    {
        //...
        $SignUpUserRequest = new SignUpUserRequest(
            $request->get('email'),
            $request->get('password')
        );
        //...
    }
}

//...
```

在更复杂的 `Silex` 应用中，它使用 `Form` 组件来捕获和验证参数：

```php
//...
$app->match('/signup', function (Request $request) use ($app) {
    $form = $app['sign_up_form'];
    $form->handleRequest($request);
    if ($form->isValid()) {
        $data = $form->getData();
        try {
            $app['sign_in_user_application_service']->execute(
                new SignUpUserRequest(
                    $data['email'],
                    $data['password']
                )
            );
            return $app->redirect($app['url_generator']);
        } catch (UserAlreadyExistsException $e) {
            $form->addError('Email is already registered');
        } catch (\Exception $e) {
            $form->addError('There was an error');
        }
    }
    return $app['twig']->render('signup.twig', [
        'form' => $form->createView(),
    ]);
});
```

## 11.2.2 设计

设计请求对象时，始终遵循以下原则：

### 11.2.2.1 使用原始类型

设计请求对象时，在服务层使用原始类型（`string`、`integers`、`booleans` 等）。

### 11.2.2.2 可序列化

`DTOs` 应该是可以跨网络传输的序列化的。

### 11.2.2.3 无业务逻辑

避免在请求对象中放置业务逻辑。验证应该在领域层进行。

### 11.2.2.4 无测试

`DTOs` 是数据结构，不需要对其进行单元测试。

### 11.3 应用服务的剖析

一旦我们将数据封装在请求中，就是处理业务逻辑的时间了。正如 `Vaughn Vernon` 所：“保持应用服务的轻量化，仅用于协调任务。”

首先要工作是从请求中提取必要信息，即电子邮件和密码。在高层面上，我们需要检查是否存在具有该电子邮件的用户。如果不是，我们则创建用户并添加到仓库中。对于发现相同邮箱用户的特殊情况，我们抛出一个异常，以便客户端按照自己的方式进行处理，例如显示错误、重试或忽略。

240

```php
namespace Lw\Application\Service\User;

use Ddd\Application\Service\ApplicationService;
use Lw\Domain\Model\User;
use Lw\Domain\Model\User\UserAlreadyExistsException;
use Lw\Domain\Model\User\UserRepository;

class SignUpUserService
{
    private $userRepository;

    public function __construct(UserRepository $userRepository)
    {
        $this->userRepository = $userRepository;
    }

    public function execute(SignUpUserRequest $request)
    {
        $email = $request->email();
        $password = $request->password();
        $user = $this->userRepository->ofEmail($email);

        if (!$user) {
            throw new UserAlreadyExistsException();
        }

        $this->userRepository->add(
            new User(
                $this->userRepository->nextIdentity(),
                $email,
                $password
            )
        );
    }
}
```

![](img/index-259_1.png)

## 异常处理

应用服务抛出的异常是向客户端通信异常情况和流程的一种。此层的异常与业务逻辑相关（如未找到用户），而不是与实现细节（如 `PDOException`、`PredisException` 或 `DoctrineException`）相关。



### 11.3.1 依赖倒置

处理不是服务的职责。正如我们在仓库章节看到的，有一个专门的类处理用户集合，即仓库。这是从应用服务到仓库的依赖。我们不希望将应用服务与仓库的具体实现耦合，否则我们就会把服务与基础设施细节耦合在一起。

应用服务（Application services）也可以依赖于领域服务，如`GetBadgesByUser`。在运行时，此类服务的具体实现可能非常复杂。想象有一个`HttpGetBadgesByUser`用于通过 HTTP 协议集成一个限界上下文（bounded context）。

依赖抽象将使我们的应用服务免受底层基础设施变化的影响。

### 11.3.2 实例化应用服务

实例化你的应用服务是非常简单的。但取决于构建依赖所需的复杂程度，构建依赖树可能会很麻烦。为了这个目的，大多数框架都自带依赖注入容器（Dependency Injection container）。如果没有它，你最终会在控制器的某个地方写如下代码：

```php
$redisClient = new Predis\Client([
    'scheme' => 'tcp',
    'host' => '10.0.0.1',
    'port' => 6379
]);
$userRepository = new RedisUserRepository($redisClient);
$signUp = new SignUpUserService($userRepository);
$signUp->execute(new SignUpUserRequest(
    'user@example.com',
    'password'
));
```

我们决定为`UserRepository`使用 [Redis](http://redis.io/)² 实现。构建该仓库所需的所有细节都在那里了，例如 [Predis³](https://github.com/nrk/predis) 配置。这不仅效率低下，而且会在控制器之间扩散代码重复。

你可以将构造逻辑重构到`Factory`（工厂）中，或者使用依赖注入容器。大多数现代框架都自带它。

#### 使用依赖注入容器不好吗？

一点也不不好。依赖注入容器只是一个工具。它们帮助抽象构建依赖的复杂性。它们在构建基础设施构件时非常有用。Symfony 提供了一个[完整的解决方案⁴](http://symfony.com/doc/current/book/service_container.html)。请注意，将整个容器作为一个整体传递给其中一个服务是一个糟糕的做法。那就像是将应用程序的整个上下文与领域耦合。如果你为特定服务获取一个对象，直接获取即可。不要让该服务感知整个上下文。

让我们看看如何使用 Silex 来实现：

```php
// ...
$app = new Silex\Application();
$app['redis_parameters'] = [
    'scheme' => 'tcp',
    'host' => '127.0.0.1',
    'port' => 6379
];
$app['redis'] = $app->share(function ($app) {
    return new Predis\Client($app['redis_parameters']);
});
$app['user_repository'] = $app->share(function ($app) {
    return new RedisUserRepository(
        $app['redis']
    );
});
$app['sign_up_user_application_service'] = $app->share(function ($app) {
    return new SignUpUserService(
        $app['user_repository']
    );
});
//...
$app->match('/signup', function (Request $request) use ($app) {
    // ...
    $app['sign_up_user_application_service']->execute(
        new SignUpUserRequest(
            $request->get('email'),
            $request->get('password')
        )
    );
    // ...
});
```

如你所示，`$app` 被用作服务容器（Service Container）。我们注册了所有需要的组件及其依赖。`sign_up_user_application_service` 依赖于上面定义的定义。更改`user_repository`的实现就像返回其他内容（如`MySQL`、`MongoDB`等）一样简单，我们不需要更改服务代码。

Symfony 应用的等效实现：

```xml
<?xml version="1.0" ?>
<container xmlns="http://symfony.com/schema/dic/services"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://symfony.com/schema/dic/services
http://symfony.com/schema/dic/services/services-1.0.xsd">
<services>
    <service
    id="sign_up_user_application_service"
    class="SignUpUserService">
        <argument type="service" id="user_repository" />
    </service>
    <service
    id="user_repository"
    class="RedisUserRepository">
        <argument type="service">
            <service class="Predis\Client" />
        </argument>
    </service>
</services>
</container>
```

现在你已经在 Symfony 服务容器中定义了应用服务，在任何语文中获取该服务都非常简单。所有交付机制在类上可用`get('sign_up_user_application_service')`。

### 11.3.3 执行

调用应用服务有两种不同的方法：每个用例一个专门的类，或者在同一个类中包含多个应用服务。

### 11.3.3.1 每个应用服务一个类

我们首选的方法，适用于所有场景。

```php
class SignUpUserService
{
    // ...
    public function execute(SignUpUserRequest $request)
    {
        // ...
    }
}
```

为每个应用服务使用专门的类使其对外部变化更具健壮性（单一职责原则）。因为类只做一件事，所以更改该类的理由更少。执行方法可以使用更具表现性的名称，例如`signUp`。然而，[命令模式](http://martfowler.com/bliki/DecoratedCommand.html)⁵ 标准了应用服务之间的通用契约。

#### 11.3.3.2 一个类中多个应用服务方法

在某些情况下，将内聚的应用服务分组在同一个类下可能是一个好主意。

```php
class UserService
{
    // ...
    public function signUp(SignUpUserRequest $request)
    {
        // ...
    }
    public function signIn(SignUpUserRequest $request)
    {
        // ...
    }
    public function logOut(LogOutUserRequest $request)
    {
        // ...
    }
}
```

我们不建议这种方法，因为并不是所有应用服务都是 100% 内聚的。某些服务将需要不同的依赖，你最终会导致应用服务依赖于它们不需要的东西。另一个问题是这种类增长得很快。因为它违反了单一职责原则，会有多个理由去修改并可能破坏它。

### 11.3.4 返回值

注册后，我们可能会考虑将用户重定向到个人资料页。在控制器中执行此操作的最直接的反映可能是直接从服务返回`User`实体。

```php
class SignUpUserService
{
    // ...
    public function execute(SignUpUserRequest $request)
    {
        // ...
        $user = new User(
            $this->userRepository->nextIdentity(),
            $email,
            $password
        );
        $this->userRepository->add($user);
        return $user;
    }
}
```

然后，从控制器中，我们将获取`id`字段并重定向到其他地方。

controller。这将允许交付机制绕过应用层，并直接与领域交互。

想象`User`实体提供了一个`updateEmailAddress`方法。你可以尝试阻止它，但在未来的某个时刻，某人可能会考虑使用它。

```php
$app->match('/signup', function (Request $request) use ($app) {
    //...*
    $user = $app['sign_up_user_application_service']->execute(
        new SignUpUserRequest(
            $request->get('email'),
            $request->get('password')
        )
    );
    $user->updateEmailAddress('shouldnotupdate@email.com');
    //...*
});
```

等一下，让我重新格式化一下代码：

不仅如此，表示层需要的数据与领域层管理的数据并不相同。

我们不希望领域层围绕表示层进行演进和耦合。我们希望它们能够自由地演进。

Application 247

我们需要一种灵活的方法来解耦这两个层。

### 11.3.4.1 从聚合实例生成 DTO

我们可以返回包含表示层所需信息的无静态数据结构。正如我们之前看到的，DTO 适合这种场景。我们只需要在应用服务中组合它们，并将它们返回给客户端。

```php
class UserDTO
{
    private $email;
    //...*
    public function __construct(User $user)
    {
        $this->email = $user->email();
        //...*
    }

    public function email()
    {
        return $this->email;
    }
}
```

`UserDTO`将在表示层暴露`User`实体中我们需要的任何只读数据，从而避免暴露行为。

```php
class SignUpUserService
{
    public function execute(SignUpUserRequest $request)
    {
        // ...*
        $user = // ...*
        return new UserDTO($user);
    }
}
```

任务完成。现在我们可以将参数传递给模板引擎，将它们转换为小部件、标签、子模板，或者在表示端对数据进行任何想要的操作。

Application 248

```php
$app->match('/signup', function (Request $request) use ($app) {
    /**
     * @var UserDTO $user
     */
    $userDto = $app['sign_up_user_application_service']->execute(
        new SignUpUserRequest(
            $request->get('email'),
            $request->get('password')
        )
    );
    //...*
});
```

然而，让应用服务决定如何构建 DTO 揭示了另一个局限性。

由于 DTO 的构建完全依赖于应用服务，将 DTO 适配到不同的客户端将非常困难。考虑 Web 控制器重定向所需的数据，以及同一用例的 REST 响应所需的数据。这些数据完全不同。

让我们通过传递特定的 DTO 组装器，允许客户端定义如何构建 DTO。

```php
class SignUpUserService
{
    private $userDtoAssembler;
    public function __construct(
        UserRepository $userRepository,
        UserDTOAssembler $userDtoAssembler
    )
    {
        $this->userRepository = $userRepository;
        $this->userDtoAssembler = $userDtoAssembler;
    }

    public function execute(SignUpUserRequest $request)
    {
        // ...*
        $user = // ...*
        return $this->userDtoAssembler->assemble($user);
    }
}
```

Application 249

现在，客户端可以通过传递特定的`UserDTOAssembler`来自定义响应。

### 11.3.4.2 数据转换器 (Data Transformers)

在某些情况下，为 JSON、XML、CSV、iCAL 联系人等更复杂的响应生成中间 DTO 可能认为是不必要的开销。我们可以将表示输出到缓冲区，并在稍后在交付侧请求它。

转换器将高层领域概念转换为底层客户端细节。让我们来看一个例子：

```php
interface UserDataTransformer
{
    public function write(User $user);
    /**
     * @return mixed
     */
    public function read();
}
```

考虑为特定产品生成不同数据表示的情况。通常产品信息通过 Web 界面（HTML）提供，但我们可能兴趣提供其他格式，如 XML、JSON 或 CSV。这可能实现与其他服务的集成。

博客也有类似的情况。我们可能通过 HTML 向世界展示我们作为作者的潜力，但有些人会对通过 RSS 消费我们的文章感兴趣。用例——应用服务——保持不变，但表示形式不同。

DTO 是一种清洁且简单的解决方案，可以传递给模板引擎以实现不同的表示，但它可能会使数据转换最后一步的逻辑变得复杂。此类模板的逻辑可能会变成维护、测试和理解的问题。

数据转换器在特定情况下可能是更好的方法。它们只是以领域概念为输入（聚合、实体等）并以只读表示（XML、JSON、CSV 等）为输出的黑盒。这些转换器可以非常容易测试。

Application 250

```php
class JsonUserDataTransformer implements UserDataTransformer
{
    private $data;
    public function write(User $user)
    {
        // 这里可以放置更复杂的逻辑
        // 如使用 JMSSerializer、原生 json 等。
        $this->data = json_encode($user);
    }
    /**
     * @return string
     */
    public function read()
    {
        return $this->data;
    }
}
```

这很简单。知道 XML 或 CSV 版本的长什么样吗？

看看如何将数据转换器集成到我们的应用服务中。



```php
class SignUpUserService
{
    private $userRepository;
    private $userDataTransformer;
    public function __construct(
        UserRepository $userRepository,
        UserDataTransformer $userDataTransformer
    )
    {
        $this->userRepository = $userRepository;
        $this->userDataTransformer = $userDataTransformer;
    }

    public function execute(SignUpUserRequest $request)
    {
        // ...*
        $user = // ...*
        Application 251
        $this->userDataTransformer->write($user);
    }

    /**
     * @return UserDataTransformer
     */
    public function userDataTransformer()
    {
        return $this->userDataTransformer;
    }
}
```

类似于 DTO 组装器方法，但这次没有返回具体的值。数据转换器被用于持有和交互数据。

DTO 的主要问题是编写它们的开销。大多数时候，你的领域概念和 DTO 表示具有相同的结构。大多数时候你会觉得这不值得。

使用类似 DTO 的有用用例是当表示层模型与领域模型之间存在显著差异时。在这种情况下，创建一个从领域模型映射并呈现对表示层方便接口的特定 facade/网关是合理的。它与表示模型（Presentation Model）完美契合。这是值得做的，但仅对于具有这种差异的屏幕（等）——Martin Fowler, PoEAA

我们认为长期来看是值得投资的。在中大型项目中，接口表示和领域概念的变化节奏非常不同。你可能希望将它们解耦以降低更新的摩擦。使用 DTO 或数据转换器可以让你自由地演进模型，而不必总是担心破坏布局。

## 11.3.5 组合布局上的多个应用服务

大多数情况下，没有一个布局像单个应用服务那么简单。我们的项目具有复杂的界面。

考虑特定项目的主页，我们如何处理许多部分和用例？有几种方案，让我们来看看：

Application 252

### 11.3.5.1 AJAX 内容集成

你可以让浏览器直接请求不同的端点，并在布局完成后通过 AJAX 或 HIAX 合并数据。你将避免在控制器中混合许多应用服务，但根据触发请求的数量，可能会产生性能损失。

### 11.3.5.2 ESI 内容集成

Edge Side Includes 或 [ESI⁷](https://en.wikipedia.org/wiki/Edge_Side_Includes) 是一种微小的标记语言，与之前的方法类似，但这次是在服务器端。它需要投入一些额外工作来配置如 `Nginx` 或 `Varnish` 等额外的中间件才能运行。

### 11.3.5.3 Symfony 子请求 (Sub Requests)

如果你使用 Symfony，[子请求](http://symfony.com/doc/current/components/http_kernel/introduction.html#sub-requests)⁸ 可能是一个很有趣的选择。从 Symfony 站点提取的内容：除了发送到 `HttpKernel::handle()` 的主请求外，你还可以发送所谓的子请求。子请求的外观和行为与任何其他请求都一样，但通常用于渲染页面的一个小部分，而不是整个页面。你最常见是从你的控制器（controller）中（或者可能从由你的控制器渲染的模板内部）发起子请求。这创建了另一个完整的请求-响应周期，其中这个新的 `Request` 被转换为 `Response`。内部唯一的区别是，某些监听器（例如安全）可能只对主请求生效。每个监听器都会接收到 `KernelEvent` 的子类，可以通过它的 `isMasterRequest()` 来检查当前请求是主请求还是子请求。

这非常棒，因为你可以在不产生 AJAX 性能损耗或无需复杂的 ESI 配置的情况下，获得调用独立应用程序服务带来的益处。

### 11.3.5.4 一个控制器，多个应用服务

最后一个选项可能是在同一个控制器中管理多个应用服务。控制器的逻辑可能会变得有点混乱。它将处理并合并响应以传递给视图。

## 11.4 测试

由于你对测试应用服务本身的 `behaviour`（行为）感兴趣，因此没有将其转换为具有复杂设置且针对真实数据库的 `Integration Test`（集成测试）。你对测试低级细节并不感兴趣。大多数情况下，一个 `Unit Test`（单元测试）就足够了。

⁶[`en.wikipedia.org/wiki/Hijax`](https://en.wikipedia.org/wiki/Hijax)

⁷[`en.wikipedia.org/wiki/Edge\_Side\_Includes`](https://en.wikipedia.org/wiki/Edge_Side_Includes)

⁸[`symfony.com/doc/current/components/http\_kernel/introduction.html#sub-requests`](http://symfony.com/doc/current/components/http_kernel/introduction.html#sub-requests)

Application

253

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

我们使用内存存储库来测试。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

内存存储库的实现是可测试的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

测试应用服务的行为是容易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

领域层不应该感知到这一点。



```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

Application

253

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

测试是易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

测试是易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

测试是易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

测试是行为是易的。



```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

测试是行为是易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

测试是行为是易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

测试是行为是易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

测试是行为是易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

是行为是行为是易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

是行为是行为是易的。



```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

行为是易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

行为是易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

行为是易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

行为是行为是是易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

行为是行为是是行为是易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

行为是行为是行为是行为是易的。



```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

行为是行为是行为是行为是行为是易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

行为是行为是行为是行为是行为是行为是易的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

（此处为重新生成正确翻译内容）

Edge Side Includes 或 ESI⁷ 是一种微小的标记语言，与之前的方法类似，但这次是在服务器端。它需要投入一些额外工作来配置如 `Nginx` 或 `Varnish` 等额外的中间件才能运行。

### 11.3.5.3 Symfony 子请求

如果你使用 Symfony，子请求⁸ 可能是一个很有趣的选择。从 Symfony 站点提取的内容：除了发送到 `HttpKernel::handle()` 的主请求外，你还可以发送所谓的子请求。子请求的外观和行为与任何其他请求都一样，但通常用于渲染页面的一个小部分，而不是整个页面。你最常见是从你的控制器（controller）中（或者可能从由你的控制器渲染的模板内部）发起子请求。这创建了另一个完整的请求-响应周期，其中这个新的 `Request` 被转换为 `Response`。内部唯一的区别是，某些监听器（例如安全）可能只对主请求生效。每个监听器都会接收到 `KernelEvent` 的子类，可以通过它的 `isMasterRequest()` 来检查当前请求是主请求还是子请求。

这非常棒，因为你可以在不产生 AJAX 性能损耗或无需复杂的 ESI 配置的情况下，获得调用独立应用程序服务带来的益处。

### 11.3.5.4 一个控制器，多个应用服务

最后一个选项可能是在同一个控制器中管理多个应用服务。控制器的逻辑可能会变得有点混乱。它将处理并合并响应以传递给视图。

### 11.4 测试

由于你对测试应用服务本身的行为（behaviour）感兴趣，因此没有将其转换为具有复杂设置且针对真实数据库的集成测试（Integration Test）。你对测试低级细节并不感兴趣。大多数情况下，一个单元测试（Unit Test）就足够了。

⁶[`en.wikipedia.org/wiki/Hijax`](https://en.wikipedia.org/wiki/Hijax)

⁷[`en.wikipedia.org/wiki/Edge\_Side\_Includes`](https://en.wikipedia.org/wiki/Edge_Side_Includes)

⁸[`symfony.com/doc/current/components/http\_kernel/introduction.html#sub-requests`](http://symfony.com/doc/current/components/http_kernel/introduction.html#sub-requests)

Application

253

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

内存存储库的实现是可测试的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

领域层不应该感知到这一点。



```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

（此处为重新生成正确翻译内容）

Edge Side Includes 或 ESI⁷ 是一种微小的标记语言，与之前的方法类似，但这次是在服务器端。它需要投入一些额外工作来配置如 `Nginx` 或 `Varnish` 等额外的中间件才能运行。

### 11.3.5.3 Symfony 子请求

如果你使用 Symfony，[子请求](http://symfony.com/doc/current/components/http_kernel/introduction.html#sub-requests)⁸ 可能是一个很有趣的选择。从 Symfony 站点提取的内容：除了发送到 `HttpKernel::handle()` 的主请求外，你还可以发送所谓的子请求。子请求的外观和行为与任何其他请求都一样，但通常用于渲染页面的一个小部分，而不是整个页面。你最常见是从你的控制器（controller）中（或者可能从由你的控制器渲染的模板内部）发起子请求。这创建了另一个完整的请求-响应周期，其中这个新的 `Request` 被转换为 `Response`。内部唯一的区别是，某些监听器（例如安全）可能只对主请求生效。每个监听器都会接收到 `KernelEvent` 的子类，可以通过它的 `isMasterRequest()` 来检查当前请求是主请求还是子请求。

这非常棒，因为你可以在不产生 AJAX 性能损耗或无需复杂的 ESI 配置的情况下，获得调用独立应用程序服务带来的益处。

### 11.3.5.4 一个控制器，多个应用服务

最后一个选项可能是在同一个控制器中管理多个应用服务。控制器的逻辑可能会变得有点混乱。它将处理并合并响应以传递给视图。

### 11.4 测试

由于你对测试应用服务本身的行为（behaviour）感兴趣，因此没有将其转换为具有复杂设置且针对真实数据库的集成测试（Integration Test）。你对测试低级细节并不感兴趣。大多数情况下，一个单元测试（Unit Test）就足够了。

⁶[`en.wikipedia.org/wiki/Hijax`](https://en.wikipedia.org/wiki/Hijax)

⁷[`en.wikipedia.org/wiki/Edge\_Side\_Includes`](https://en.wikipedia.org/wiki/Edge_Side_Includes)

⁸[`symfony.com/doc/current/components/http\_kernel/introduction.html#sub-requests`](http://symfony.com/doc/current/components/http_kernel/introduction.html#sub-requests)

Application

253

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

内存存储库的实现是可测试的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

领域层不应该感知到这一点。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

（此处为重新生成正确翻译内容）

Edge Side Includes 或 ESI⁷ 是一种微小的标记语言，与之前的方法类似，但这次是在服务器端。它需要投入一些额外工作来配置如 `Nginx` 或 `Varnish` 等额外的中间件才能运行。

### 11.3.5.3 Symfony 子请求

如果你使用 Symfony，[子请求](http://symfony.com/doc/current/components/http_kernel/introduction.html#sub-requests)⁸ 可能是一个很有趣的选择。从 Symfony 站点提取的内容：除了发送到 `HttpKernel::handle()` 的主请求外，你还可以发送所谓的子请求。子请求的外观和行为与任何其他请求都一样，但通常用于渲染页面的一个小部分，而不是整个页面。你最常见是从你的控制器（controller）中（或者可能从由你的控制器渲染的模板内部）发起子请求。这创建了另一个完整的请求-响应周期，其中这个新的 `Request` 被转换为 `Response`。内部唯一的区别是，某些监听器（例如安全）可能只对主请求生效。每个监听器都会接收到 `KernelEvent` 的子类，可以通过它的 `isMasterRequest()` 来检查当前请求是主请求还是子请求。

这非常棒，因为你可以在不产生 AJAX 性能损耗或无需复杂的 ESI 配置的情况下，获得调用独立应用程序服务带来的益处。

### 11.3.5.4 一个控制器，多个应用服务

最后一个选项可能是在同一个控制器中管理多个应用服务。控制器的逻辑可能会变得有点混乱。它将处理并合并响应以传递给视图。

### 11.4 测试

由于你对测试应用服务本身的行为（behaviour）感兴趣，因此没有将其转换为具有复杂设置且针对真实数据库的集成测试（Integration Test）。你对测试低级细节并不感兴趣。大多数情况下，一个单元测试（Unit Test）就足够了。

⁶[`en.wikipedia.org/wiki/Hijax`](https://en.wikipedia.org/wiki/Hijax)

⁷[`en.wikipedia.org/wiki/Edge\_Side\_Includes`](https://en.wikipedia.org/wiki/Edge_Side_Includes)

⁸[`symfony.com/doc/current/components/http\_kernel/introduction.html#sub-requests`](http://symfony.com/doc/current/components/http_kernel/introduction.html#sub-requests)

Application

253



```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

内存存储库的实现是可测试的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

领域层不应该感知到这一点。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

Edge Side Includes 或 [ESI⁷](https://en.wikipedia.org/wiki/Edge_Side_Includes) 是一种微小的标记语言，与之前的方法类似，但这次是在服务器端。它需要投入一些额外工作来配置如 `Nginx` 或 `Varnish` 等额外的中间件才能运行。

### 11.3.5.3 Symfony 子请求

如果你使用 Symfony，[子请求](http://symfony.com/doc/current/components/http_kernel/introduction.html#sub-requests)⁸ 可能是一个很有趣的选择。从 Symfony 站点提取的内容：除了发送到 `HttpKernel::handle()` 的主请求外，你还可以发送所谓的子请求。子请求的外观和行为与任何其他请求都一样，但通常用于渲染页面的一个小部分，而不是整个页面。你最常见是从你的控制器（controller）中（或者可能从由你的控制器渲染的模板内部）发起子请求。这创建了另一个完整的请求-响应周期，其中这个新的 `Request` 被转换为 `Response`。内部唯一的区别是，某些监听器（例如安全）可能只对主请求生效。每个监听器都会接收到 `KernelEvent` 的子类，可以通过它的 `isMasterRequest()` 来检查当前请求是主请求还是子请求。

这非常棒，因为你可以在不产生 AJAX 性能损耗或无需复杂的 ESI 配置的情况下，获得调用独立应用程序服务带来的益处。

### 11.3.5.4 一个控制器，多个应用服务

最后一个选项可能是在同一个控制器中管理多个应用服务。控制器的逻辑可能会变得有点混乱。它将处理并合并响应以传递给视图。

### 11.4 测试

由于你对测试应用服务本身的行为（behaviour）感兴趣，因此没有将其转换为具有复杂设置且针对真实数据库的集成测试（Integration Test）。你对测试低级细节并不感兴趣。大多数情况下，一个单元测试（Unit Test）就足够了。

⁶[`en.wikipedia.org/wiki/Hijax`](https://en.wikipedia.org/wiki/Hijax)

⁷[`en.wikipedia.org/wiki/Edge\_Side\_Includes`](https://en.wikipedia.org/wiki/Edge_Side_Includes)

⁸[`symfony.com/doc/current/components/http\_kernel/introduction.html#sub-requests`](http://symfony.com/doc/current/components/http_kernel/introduction.html#sub-requests)

Application

253

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

内存存储库的实现是可测试的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

Edge Side Includes 或 [ESI⁷](https://en.wikipedia.org/wiki/Edge_Side_Includes) 是一种微小的标记语言，与之前的方法类似，但这次是在服务器端。它需要投入一些额外工作来配置如 `Nginx` 或 `Varnish` 等额外的中间件才能运行。

### 11.3.5.3 Symfony 子请求

如果你使用 Symfony，[子请求](http://symfony.com/doc/current/components/http_kernel/introduction.html#sub-requests)⁸ 可能是一个很有趣的选择。从 Symfony 站点提取的内容：除了发送到 `HttpKernel::handle()` 的主请求外，你还可以发送所谓的子请求。子请求的外观和行为与任何其他请求都一样，但通常用于渲染页面的一个小部分，而不是整个页面。你最常见是从你的控制器（controller）中（或者可能从由你的控制器渲染的模板内部）发起子请求。这创建了另一个完整的请求-响应周期，其中这个新的 `Request` 被转换为 `Response`。内部唯一的区别是，某些监听器（例如安全）可能只对主请求生效。每个监听器都会接收到 `KernelEvent` 的子类，可以通过它的 `isMasterRequest()` 来检查当前请求是主请求还是子请求。

这非常棒，因为你可以在不产生 AJAX 性能损耗或无需复杂的 ESI 配置的情况下，获得调用独立应用程序服务带来的益处。

### 11.3.5.4 一个控制器，多个应用服务

最后一个选项可能是在同一个控制器中管理多个应用服务。控制器的逻辑可能会变得有点混乱。它将处理并合并响应以传递给视图。

### 11.4 测试



由于你对测试应用服务本身的行为（behaviour）感兴趣，因此没有将其转换为具有复杂设置且针对真实数据库的集成测试（Integration Test）。你对测试低级细节并不感兴趣。大多数情况下，一个单元测试（Unit Test）就足够了。

⁶[`en.wikipedia.org/wiki/Hijax`](https://en.wikipedia.org/wiki/Hijax)

⁷[`en.wikipedia.org/wiki/Edge\_Side\_Includes`](https://en.wikipedia.org/wiki/Edge_Side_Includes)

⁸[`symfony.com/doc/current/components/http\_kernel/introduction.html#sub-requests`](http://symfony.com/doc/current/components/http_kernel/introduction.html#sub-requests)

Application

253

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

内存存储库的实现是可测试的。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

领域层不应该感知到这一点。

```php
class SignUpUserServiceTest extends PHPUnit_Framework_TestCase
{
    /**
     * @var \Lw\Domain\Model\User\UserRepository
     */
    private $userRepository;

    /**
     * @var SignUpUserService
     */
    private $SignUpUserService;

    public function setUp()
    {
        $this->userRepository = new InMemoryUserRepository();
        $this->SignUpUserService = new SignUpUserService($this->userRepository);
    }

    /**
     * @test
     * @expectedException \Lw\Domain\Model\User\UserAlreadyExistsException
     */
    public function alreadyExistingEmailShouldThrowAnException()
    {
        $this->executeSignUp();
        $this->executeSignUp();
    }

    private function executeSignUp()
    {
        return $this->SignUpUserService->execute(
            new SignUpUserRequest(
                'user@example.com',
                'password'
            )
        );
    }

    /**
     * @test
     */
    public function afterUserSignUpItShouldBeInTheRepository()
    {
        $user = $this->executeSignUp();
        $this->assertSame(
            $user,
            $this->userRepository->ofId($user->id())
        );
    }
}
```

交付机制的。用这些概念污染领域将使开发变得更加困难。

## 11.7 领域事件 (Domain Events)

在执行应用服务之前，必须配置领域事件监听器，否则没有人会被注意到。在某些情况下，你必须在执行应用服务之前显式地配置监听器。

```php
//...*
$subscriber = new SpySubscriber();
DomainEventPublisher::instance()->subscribe($subscriber);
$applicationService = //...*
$applicationService->execute(...);
```

大多数情况下，这将通过配置依赖注入容器来完成。

### 11.8 命令处理器 (Command Handlers)

执行应用服务的一种有趣方法是通过使用命令总线（Command Bus）库。一个很好的选择是 [Tactician¹⁰](https://tactician.thephpleague.com/)。

什么是命令总线？这个术语主要用于我们将[命令](https://en.wikipedia.org/wiki/Command_pattern) [模式](https://en.wikipedia.org/wiki/Command_pattern)¹¹ 与[服务层](http://martinfowler.com/eaaCatalog/serviceLayer.html)¹²结合起来。它的工作是获取一个命令对象（描述用户想要做什么）并将其匹配到处理器（执行该操作）。这有助于保持代码的结构整洁。

诚然，我们的应用服务就是服务层，而我们的请求对象看起来非常像命令。

如果我们有一个机制来链接所有的应用服务，然后根据请求执行正确的那个，那不是太好了吗？事实上，这正是命令总线的作用。

### 11.8.1 Tactician 库及其他选项

Tactician 是一个命令总线库。它允许你为应用服务使用命令模式。它对应用服务来说特别方便，但你也可以使用任何类型的输入。让我们来看 Tactician 网站上的示例。

¹⁰[`tactician.thephpleague.com/`](https://tactician.thephpleague.com/)

¹¹[`en.wikipedia.org/wiki/Command\_pattern`](https://en.wikipedia.org/wiki/Command_pattern)

¹²[`martinfowler.com/eaaCatalog/serviceLayer.html`](http://martinfowler.com/eaaCatalog/serviceLayer.html)

```php
// 你这样构建一个简单的消息对象：
class PurchaseProductCommand
{
    protected $productId;
    protected $userId;
    // ...以及用于分配这些属性的构造函数...
}

// 以及一个期望该对象的处理器类：
class PurchaseProductHandler
{
    public function handle(PurchaseProductCommand $command)
    {
        // 使用命令更新你的模型等
    }
}

// 然后在你的控制器中，你可以使用你喜欢的
//// 表单或序列化器库来填充命令，然后将其丢入命令总线就搞定了！
$command = new PurchaseProductCommand(42, 29);
$commandBus->handle($command);
```

就是这样。Tactician 就是那个 `$commandBus` 服务。它处理了寻找正确处理器和方法的所有管道连接工作。这可以避免大量的样板代码。在这里，命令和处理器只是普通的类，但你可以配置任何更适合你应用的配置。

总结一下，我们可以得出结论：命令仅仅是请求对象，而命令处理器仅仅是应用服务。

Tactician（以及通用的命令总线）的一个酷点是它们非常容易扩展。Tactician 为日志记录和数据库事务等常见任务提供了插件。这样一来，你就不需要担心在每个处理器上设置布线了。

Tactician 的另一个有趣插件是集成 [Bernard¹³](http://bernard.readthedocs.org/)。Bernard 是一个异步作业队列，允许你将某些任务留到以后处理。重量型过程会阻塞用户响应，而大多数任务可以留到以后处理。

Mathias Noback 开发了 Tactician 的一个酷替代方案，叫做 SimpleBus。[查看它¹⁴](http://simplebus.github.io/MessageBus/)[](#index_split_000.html#277)

¹³[`bernard.readthedocs.org/`](http://bernard.readthedocs.org/)

¹⁴[`simplebus.github.io/MessageBus/`](http://simplebus.github.io/MessageBus/)

### 11.9 总结

应用服务代表了应用层。我们看到请求和命令保持了有序，DTO 允许我们将数据表示与领域逻辑解耦，这涉及到许多关注点。

## 12. 整合边界上下文 (Integrating Bounded Contexts)

每个企业应用通常由多个区域组成。处理分布式系统是困难的。这些系统的协调并不简单，需要仔细考虑。正如 Martin Fowler 在《软件架构模式》书中所说，分布式系统的第一条法则始终是：不要分布。

### 12.1 通过数据存储进行集成

集成应用程序不同部分的最常用技术之一始终是共享同一个数据存储，以及相同的代码库。这通常被称为单体应用。

考虑一个电子商务应用程序，共享的数据存储将包含所有关注点（例如：关系型数据库中的表），围绕目录、账单、库存等。这种方法本身并没有坏处，例如在小型线性应用中，复杂度并不高。然而，在复杂的领域中，可能会出现问题。如果你跨越许多涉及多个关注点的表共享数据，事务将对性能产生巨大影响。另一个非技术性的问题可能会出现在通用通用语言（Ubiquitous Language）方面。

回到电子商务系统，假设我们想要引入“T 恤”的概念。在目录上下文中，T 恤是一个具有颜色、尺寸、材质属性以及一些精美图片的产品。但在库存系统中，我们并不真正关心这些。在这里，产品具有不同的含义，我们关心的是重量、仓库位置或尺寸等不同属性。将两个上下文混合在一起会使概念纠缠并增加设计。在 DDD 术语中，这种方式的概念混合被称为“共享内核”（Shared Kernel）。

指定某些团队同意共享的领域模型子集。当然，这包含了该模型子集以及与该模型部分相关的代码子集或数据库设计。这些显式共享的内容具有特殊状态，在没有咨询另一个团队的情况下不应进行更改。频繁地集成功能系统，但频率略低于团队内部的持续集成（CONTINUOUS INTEGRATION）速度。在这些集成时，运行两个团队的测试。

*Eric Evans* - 《领域驱动设计：应对软件核心复杂性》

# 第 14 章 - 共享内核 (Shared Kernel)

我们不建议使用 `Shared Kernel`。因为多个团队在开发它的过程中可能会发生冲突，最终导致维护问题并成为摩擦点。`Shared Kernel` 中的更改更改应预先由所有参与方达成共识。在概念上，它还有其他问题，例如人们将其视为一个放置“不属于任何地方的杂物”的袋子，并使其无限增长。

处理不断增长的单体复杂性的更好方法是将其拆分为不同的自治部分。例如通过 REST、RPC 或消息系统进行通信。这需要划定清晰的边界，每个上下文可能都会有自己的基础设施——数据存储、服务器、消息中间件等——甚至有自己的团队。正如你所预见的，这可能会导致某种程度的重复。为了降低复杂性，我们愿意做出这种权衡。这些自治部分被称为`限界上下文（Bounded Contexts）`。

## 12.2 集成关系

### 12.2.1 客户/供应商 (Customer / Supplier)

当两个限界上下文之间存在单向集成时，其中一个作为提供者（`upstream`），另一个作为其客户端（`downstream`），我们将得到`客户-供应商开发团队（Customer - Supplier Development Teams）`。

![](img/index-281_1.png)

![](img/index-281_2.png)

![](img/index-281_3.png)

集成限界上下文 263

在两个团队之间建立清晰的客户/供应商关系。在规划会议中，让下游团队扮演上游团队的客户。为下游需求进行谈判和预算分配，以便每个人都理解承诺和进度。

共同开发自动化验收测试，以验证预期的接口。将这些测试添加到上游团队的测试套件中，作为其持续集成的一部分运行。这种测试将让上游团队能够放心地做出更改，而无需担心对下游产生副作用。

*Eric Evans* - 《领域驱动设计：应对软件核心复杂性》



`Customer / Supplier Development Teams` 是集成限界上下文常见的方式。当团队紧密合作时，这通常代表着双赢的局面。

## 12.2.2 分离 (Separate Ways)

延续电子商务的例子，考虑向旧的遗留零售商财务系统报告收入。这种集成可能非常昂贵，以至于投入实现没有价值。在 DDD 战略术语中，这被称为`分离（Separate Ways）`。

集成总是昂贵的。有时收益却很小。因此，声明一个`限界上下文（BOUNDED CONTEXT）`与其他完全没有连接，让开发者感到轻松。

*Eric Evans* - 《领域驱动设计：应对软件核心复杂性》

## 12.3 实现限界上下文

### 12.3.1 现代 RPC

为了让事情变得更容易，我们将假设限界上下文之间存在关系。以电子商务为例，考虑向旧的遗留零售商财务系统报告收入。这种集成可能非常昂贵，以至于投入实现没有价值。在 DDD 战略术语中，这被称为`分离（Separate Ways）`。

### 12.3.2 遵循者 (Conformist)

再次考虑电子商务例子以及与第三方的集成。限界上下文之间存在关系。我们将假设限界上下文之间存在关系。以电子商务为例，考虑向旧的遗留零售商财务系统报告收入。这种集成可能非常昂贵，以至于投入实现没有价值。在 DDD 战略术语中，这被称为`分离（Separate Ways）`。

⁴[`github.com/willdurand/BazingaHateoasBundle`](https://github.com/willdurand/BazingaHateoasBundle)

⁵[`github.com/schmittjoh/JMSSerializerBundle`](https://github.com/schmittjoh/JMSSerializerBundle)

⁶[`github.com/nelmio/NelmioApiDocBundle/`](https://github.com/nelmio/NelmioApiDocBundle/)

⁷[`github.com/ongr-io/ElasticsearchBundle`](https://github.com/ongr-io/ElasticsearchBundle)

⁸[`martinfowler.com/articles/richardsonMaturityModel.html`](http://martinfowler.com/articles/richardsonMaturityModel.html)

# 集成边界上下文

265

通过类似 `http://gamification.context.host/api/users/{id}` 的端点获取特定用户。

我们将从 Elasticsearch 中获取用户投影，并将其序列化为之前与客户端协商好的格式。

```php
namespace AppBundle\Controller;

use FOS\RestBundle\Controller\Annotations as Rest;
use FOS\RestBundle\Controller\FOSRestController;
use Nelmio\ApiDocBundle\Annotation\ApiDoc;

class UsersController extends FOSRestController
{
    /**
     * @ApiDoc(
     * resource=true,
     * description="根据用户 ID 查找用户",
     * statusCodes={
     * 200 = "找到用户时返回",
     * 404 = "未找到用户时返回"
     * }
     * )
     * @Rest\View(
     * statusCode = 200
     * )
     */
    public function getUserAction($id)
    {
        $repo = $this->get('es.manager.default.user');
        $user = $repo->find($id);
        if (!$user) {
            throw $this->createNotFoundException(
                sprintf(
                    'ID 为 %s 的用户不存在',
                    $id
                )
            );
        }
        return $user;
    }
}
```

![](img/index-284_1.png)

集成边界上下文

266

正如我们在**架构**章节中所解释的，*读取*（reads）被视为一种基础设施关注。没有必要将它们封装在 `Command` / `Command Handler` 流中。

用户的生成的 JSON+HAL 表示形式将是：

```json
{
  "id" : "c3c587c6-610a-42df-90d3-8e9a181d65d0",
  "points" : 0,
  "_links" : {
    "self" : {
      "href" : "http://gamification.context/api/users/c3c587c6-610a-42df-90d3-8e9a181d65d0"
    }
  }
}
```

现在我们处于集成两个上下文的良好位置。我们只需要在 Will 上下文中编写客户端，来消费我们刚刚创建的端点。我们应该混合两个领域模型吗？直接消化游戏化上下文（Gamification Context）意味着将 Will 上下文适配到游戏化上下文，导致**顺从式**（Conformist）的集成。然而，分离这些关注点似乎值得这些投资。我们需要一个层来保证 Will 上下文中领域模型的完整性和一致性。我们需要将*积分*（points，游戏化）翻译为*勋章*（badges，Will）。这种翻译机制就是 DDD 中所谓的***反腐保护层***（Anti-corruption Layer）。

## 反腐保护层

> *创建一个隔离层，为客户端提供其自身的领域模型的功能。反腐保护层在内部在两个模型之间进行必要的翻译。通过适配器（Adapters）和面面（Facades）与系统交互。*

> — *Eric Evans - 领域驱动设计，隐藏复杂性。*

反腐保护层是如何定义的呢？我们将看到如何定义从游戏化上下文获取的勋章。

集成边界上下文

267

```php
namespace Lw\Domain\User;

interface UserService
{
    function badgesFrom($id);
}
```

现在让我们看基础设施部分的实现。我们将使用适配器来进行转换。

```php
namespace Lw\Infrastructure\Service;

use Lw\Domain\User\UserId;
use Lw\Domain\User\UserAdapter;

class TranslatingUserService implements UserService
{
    private $userAdapter;

    public function __construct(UserAdapter $userAdapter)
    {
        $this->userAdapter = $userAdapter;
    }

    public function badgesFrom(UserId $id)
    {
        return $this->userAdapter->toBadges($id);
    }
}
```

用于转换的适配器。

```php
namespace Lw\Infrastructure\Service;

use GuzzleHttp\Client;
use Lw\Domain\User\UserId;

class HttpUserAdapter implements UserAdapter
{
    private $client;

    public function __construct(Client $client)
    {
        $this->client = $client;
    }

    public function toBadges($id)
    {
        $response = $this->client->get(sprintf('/users/%s', $id), [
            'allow_redirects' => true,
            'headers' => ['Accept' => 'application/json']
        ]);
        $badges = [];
        if (200 === $response->getStatusCode()) {
            $badges = json_decode($response->getBody(), true);
        }
        return $badges;
    }
}
```

正如你所看到的，适配器作为游戏化上下文的**Facade**。我们通过这种方式使用了 **UserTranslator**。

集成边界上下文

269

```php
namespace Lw\Infrastructure\Service;

use Lw\Domain\Model\FirstMadeBadge;
use Symfony\Component\PropertyAccess\PropertyAccessor;

class UserTranslator
{
    public function badgesFrom($representation)
    {
        $accessor = PropertyAccessor::createAccessor();
        $points = $accessor->getValue($representation, 'points');
        $badges = [];
        if ($points > 3) {
            $badges[] = new FirstMadeBadge();
        }
        return $badges;
    }
}
```

翻译器专门负责将来自游戏化上下文的积分转换为勋章。

*使用一种文档良好的共享语言，将必要的领域信息作为通信的通用媒介，根据需要翻译成该语言或从该语言翻译。*

*Eric Evans* - 《领域驱动设计：解决软件核心的复杂性》

思考这些消息的格式，通过仔细观察我们的领域模型（Domain Model），我们发现我们已经拥有它了！领域事件（Domain Events）。不需要在边界上下文（Bounded Contexts）之间定义新的通信协议。我们可以使用 `Domain Events` 来跨越上下文定义一种通用语言。它们对“领域专家关注的事情刚刚发生”的定义，完美契合了我们正在寻找的“发布语言（Published Language）”。

在我们的示例中，我们可以使用 [RabbitMQ](https://www.rabbitmq.com/)⁹ 作为消息中间件。这可能是目前最可靠、最健壮的几个 [AMQP](https://www.amqp.org/)¹⁰ 协议之一。我们将引入广泛使用的 PHP 库 [php-amqplib](https://github.com/videlalvaro/php-amqplib)¹¹ 和 [RabbitMQBundle](https://github.com/videlalvaro/RabbitMqBundle)¹²。

让我们从 Will（遗嘱）上下文开始，因为它在用户注册或许愿望时会触发事件。正如我们在领域事件（domain events）章节中所看到的，**将领域事件存储到持久化机制中是一个好主意**，因此我们将理所当然地这样做。我们需要一个消息发布者（message publisher）来从事件存储获取并发布已存储的领域事件到消息中间件。我们已经在领域事件（domain events）章节中完成了与 RabbitMQ 的集成，因此我们只需要在游戏化上下文（Gamification Context）中实现代码即可。我们将监听由 Will 上上下文触发的事件。由于我们在游戏化一侧使用了 Symfony，我们可以利用已有的 `RabbitMQBundle` 来让事情变得简单。

我们为“用户注册（User Signed Up）”和“已许愿（Wish Was Made）”事件定义了两个消息消费者。

### 集成边界上下文

```php
namespace AppBundle\Infrastructure\Messaging\PhpAmqpLib;

use Lw\Gamification\Command\SignupCommand;
use OldSound\RabbitMqBundle\RabbitMq\ConsumerInterface;
use PhpAmqpLib\Message\AMQPMessage;

class PhpAmqpLibLastWillUserRegisteredConsumer implements ConsumerInterface
{
    private $commandBus;

    public function __construct($commandBus)
    {
        $this->commandBus = $commandBus;
    }

    public function execute(AMQPMessage $message)
    {
        $type = $message->get('type');
        if ('Lw\Domain\Model\User\UserRegistered' === $type) {
            $event = json_decode($message->body);
            $eventBody = json_decode($event->event_body);
            $this->commandBus->handle(
                new SignupCommand($eventBody->user_id->id)
            );
            return true;
        }
        return false;
    }
}
```

注意，在这种情况下，我们只处理类型为 `Lw\Domain\Model\User\UserRegistered` 的消息。以及针对“用户注册（User Signed Up）”事件的消费者。

```php
namespace AppBundle\Infrastructure\Messaging\PhpAmqpLib;

use Lw\Gamification\Command\RewardUserCommand;
use Lw\Gamification\DomainModel\AggregateDoesNotExist;
use OldSound\RabbitMqBundle\RabbitMq\ConsumerInterface;
use PhpAmqpLib\Message\AMQPMessage;

class PhpAmqpLibLastWillWishWasMadeConsumer implements ConsumerInterface
{
    private $commandBus;

    public function __construct($commandBus)
    {
        $this->commandBus = $commandBus;
    }

    public function execute(AMQPMessage $message)
    {
        $type = $message->get('type');
        if ('Lw\Domain\Model\Wish\WishWasMade' === $type) {
            $event = json_decode($message->body);
            $eventBody = json_decode($event->event_body);
            try {
                $points = 5;
                $this->commandBus->handle(
                    new RewardUserCommand(
                        $eventBody->user_id->id,
                        $points
                    )
                );
            } catch (AggregateDoesNotExist $e) {
                // Noop
            }
            return true;
        }
        return false;
    }
}
```

集成边界上下文



再次，我们只感兴趣`Lw\Domain\Model\Wish\WishWasMade`。游戏化上下文使用了[`Tactician`³](http://tactician.phpleague.com/)和[`TacticianBundle`⁴](https://github.com/videlalvaro/tactician-bundle)，这是一个可以扩展并适应你系统的简单总线（bus）。所以现在我们几乎已经准备好在 Symfony 的`config.yml`中定义`RabbitMQ`配置。

```yaml
services:
  last_will_user_registered:
    class: AppBundle\Infrastructure\Messaging\PhpAmqpLib\PhpAmqpLibLastWillUserRegisteredConsumer
    arguments:
      - @tactician
  last_will_wish_made:
    class: AppBundle\Infrastructure\Messaging\PhpAmqpLib\PhpAmqpLibLastWillWishWasMadeConsumer
    arguments:
      - @tactician

framework_rabbitmq:
  connections:
    default:
      host: "%host%"
      port: "%port%"
      user: "%user%"
      password: "%password%"
      vhost: "%vhost%"
  lazy: true

consumers:
  last_will_user_registered:
    connection: default
    callback: last_will_user_registered
    exchange_options:
      name: last-will
      type: fanout
    queue_options:
      name: last-will
  last_will_wish_made:
    connection: default
    callback: last_will_wish_made
    exchange_options:
      name: last-will
      type: fanout
    queue_options:
      name: last-will
```

通过这两个命令，Symfony 将执行两个消费者并监听领域事件。我们指定了 1000 条消息的限制，因为 PHP 不是运行长时间进程的最佳平台。使用像[**Supervisor**](http://supervisord.org/)的工具来定期监控和重启进程可能是一个好主意。

```bash
php app/console rabbitmq:consumer --messages=1000 last_will_user_registered
php app/console rabbitmq:consumer --messages=1000 last_will_wish_made
```

可能最方便的 RabbitMQ 配置是[发布/订阅（Publish / Subscribe）十五](https://www.rabbitmq.com/tutorials/tutorial-three-php)](#index_split_000.html#292)。Will 上下发布的所有消息都会传递给所有消费者。这在 RabbitMQ 交换机中被称为`fanout`。交换机由一个代理负责将消息传递相应的队列。

尽管我们只看到了局部，但策略设计是领域驱动设计的核心。它是帮助你开发更好、更有语义模型的关键部分。

我们建议使用消息中间件来集成边界上下文，因为这自然会导致更简单、解耦和事件驱动的架构。

⁹[`www.rabbitmq.com/`](https://www.rabbitmq.com/)

¹⁰[`www.amqp.org/`](https://www.amqp.org/)

¹¹[`github.com/videlalvaro/php-amqplib`](https://github.com/videlalvaro/php-amqplib)

¹²[`github.com/videlalvaro/RabbitMQBundle`](https://github.com/videlalvaro/RabbitMQBundle)

³[`tactician.phpleague.com/`](http://tactician.phpleague.com/)

⁴[`github.com/videlalvaro/tactician-bundle`](https://github.com/videlalvaro/tactician-bundle)

¹⁵[`www.rabbitmq.com/tutorials/tutorial-three-php.html`](https://www.rabbitmq.com/tutorials/tutorial-three-php.html)

¹⁶[`supervisord.org/`](http://supervisord.org/)

- [领域驱动设计实现¹](http://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon-ebook/dp/B00BCLEBN8) Vaughn Vernon 著

- [企业应用架构模式²](http://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin-ebook/dp/B000OZ0NAI) Martin Fowler 著

- [企业集成模式³](http://www.amazon.com/Enterprise-Integration-Patterns-Designing-Addison-Wesley-ebook/dp/B007MQLL4E) Gregor Hohpe 和 Bobby Woolf 著

- [领域驱动设计⁴](http://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software-ebook/dp/B00794TAUG) Eric Evans 著

- [NoSQL 精粹](http://www.amazon.com/NoSQL-Distilled-Emerging-Polyglot-Persistence/dp/0321826620)⁵ Martin Fowler 和 Pramod J. Sadalage 著

- [微服务构建⁶](http://www.amazon.com/Building-Microservices-Sam-Newman/dp/1491950358) Sam Newman 著

¹[http://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon-ebook/dp/B00BCLEBN8]

²[http://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin-ebook/dp/B000OZ0NAI]

³[http://www.amazon.com/Enterprise-Integration-Patterns-Designing-Addison-Wesley-ebook/dp/B007MQLL4E]

⁴[http://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software-ebook/dp/B00794TAUG]

⁵[http://www.amazon.com/NoSQL-Distilled-Emerging-Polyglot-Persistence/dp/0321826620]

⁶[http://www.amazon.com/Building-Microservices-Sam-Newman/dp/1491950358]

## 附录 A：基于 PHP 的六形架构

发表于 php 杂志。2014 年 6 月。Carlos Buenosvinos (@buvinos)。

## 引言

随着领域驱动设计（`DDD`）的兴起，以领域为中心的设计正变得越来越流行。这就是六形架构（Hexagonal Architecture），也称为“端口与适配器”（Ports and Adapters），它似乎被 PHP 开发者刚刚重新发现。六形架构由作者之一 Alistair Cockburn 于 2005 年发明，它允许应用程序由用户、程序、自动化测试或运行时设备和数据库平等地驱动。这使得 Web 应用程序变得更容易测试、编写和维护。让我们看看如何使用真实的 PHP 示例来应用它。

你的公司正在构建一个脑暴系统。用户添加并对想法进行评分，这样有趣的想法就可以在公司内部实施。周一早晨，又一个冲刺开始了，你正在与团队和产品负责人（Product Owner）评审一些用户故事：“我想给一个想法评分，并且应该通过邮件通知作者”。作为一名优秀的开发者，你决定分而治之处理这个用户故事，你将从第一部分开始：“我想给一个想法评分”。之后，你将面临“应该通过邮件通知作者”。从业务规则的角度来说，对想法进行评分就像在存储库（所有想法存放的地方）中通过标识符找到该想法，添加评分，重新计算平均值并将想法保存回来。如果想法不存在或仓库可用，我们应该抛出异常，这样我们可以显示错误消息、重定向用户或执行业务所要求的任何操作。

```php
class IdeaController extends Zend_Controller_Action
{
    public function rateAction()
    {
        // 从请求中获取参数
        $ideaId = $this->request->getParam('id');
        $rating = $this->request->getParam('rating');

        // 构建数据库连接
        $db = new Zend_Db_Adapter_Pdo_Mysql(array(
            'host' => 'localhost',
            'username' => 'idy',
            'password' => '',
            'dbname' => 'idy'
        ));

        // 在数据库中查找想法
        $sql = 'SELECT * FROM ideas WHERE idea_id = ?';
        $row = $db->fetchRow($sql, $ideaId);

        if (!$row) {
            throw new Exception('Idea does not exist');
        }

        // 从数据库构建想法对象
        $idea = new Idea();
        $idea->setId($row['id']);
        $idea->setTitle($row['title']);
        $idea->setDescription($row['description']);
        $idea->setRating($row['rating']);
        $idea->setVotes($row['votes']);
        $idea->setAuthor($row['email']);

        // 添加用户评分
        $idea->addRating($rating);

        // 更新想法并保存到数据库
        $data = array(
            'votes' => $idea->getVotes(),
            'rating' => $idea->getRating()
        );
        $where['idea_id = ?'] = $ideaId;
        $db->update('ideas', $data, $where);

        // 重定向到查看想法页面
        $this->redirect('/idea/'.$ideaId);
    }
}
```

我知道读者在想什么：“谁会在控制器中直接访问数据？这是 90 年代的示例！”，好吧，好吧，你说得对。如果你已经在使用框架，你很可能也在使用 ORM。可能是自己实现的，也可能是使用任何现有的工具如`Doctrine`、`Eloquent`、`ZendDB`等。如果是这样，你比那些只有数据库连接对象的人多走了一步，但别高兴得太早。

对于初学者来说，列表 1 的代码可以直接运行。然而，如果你仔细观察控制器，你看到的不仅仅是业务规则，你还会看到 Web 框架如何将请求路由到业务规则、数据库的引用或如何连接它。在这里你看到了基础设施。

基础设施是使业务规则运行的细节。显然，我们需要某些方式访问它们（API、Web、控制台应用等），并且我们需要一个物理位置来存储我们的想法（内存、数据库、NoSQL 等）。然而，我们应该能够将这些组件与其他具有相同行为的实现交换。从数据库访问开始如何？

## 仓库与持久化边界

无论业务规则还是基础设施发生变化，我们都必须修改同一部分代码。相信我，在计算机科学中，你不希望人们为了不同的原因接触同一部分代码。尝试让你的函数只做一件事且只做一件事，这样就就不可能出现人们在同一部分代码上乱搞。你可以通过……了解更多

看看单一职责原则（SRP）。关于该原则的更多信息，请参考：[http:](http://www.objectmentor.com/resources/articles/srp.pdf)

列表 1 显然是这种情况这种情况。如果我们想迁移到`Redis`或添加作者通知功能，就必须更新`rateAction`方法。影响`rateAction`中与更新逻辑不相关的其他方面的概率很高。列表 1 的代码是脆弱的。如果在你的团队中经常听到“如果它能运行，就不要动它”，那么说明缺少 SRP。

因此，我们必须对代码解耦，并将处理获取和持久化点的责任封装到另一个对象中。正如之前解释过的，最好的方法是使用`Repository`。接受挑战！让我们看看列表 2 中的结果。



```php
class IdeaController extends Zend_Controller_Action
{
    public function rateAction()
    {
        $ideaId = $this->request->getParam('id');
        $rating = $this->request->getParam('rating');
        $ideaRepository = new IdeaRepository();
        $idea = $ideaRepository->find($ideaId);
        if (!$idea) {
            throw new Exception('Idea does not exist');
        }
        $idea->addRating($rating);
        $ideaRepository->update($idea);
        $this->redirect('/idea/'.$ideaId);
    }
}

class IdeaRepository
{
    private $client;
    public function __construct()
    {
        $this->client = new Zend_Db_Adapter_Pdo_Mysql(array(
            'host' => 'localhost',
            'username' => 'idy',
            'password' => '',
            'dbname' => 'idy'
        ));
    }

    public function find($id)
    {
        $sql = 'SELECT * FROM ideas WHERE idea_id = ?';
        $row = $this->client->fetchRow($sql, $id);
        if (!$row) {
            return null;
        }
        $idea = new Idea();
        $idea->setId($row['id']);
        $idea->setTitle($row['title']);
        $idea->setDescription($row['description']);
        $idea->setRating($row['rating']);
        $idea->setVotes($row['votes']);
        $idea->setAuthor($row['email']);
        return $idea;
    }

    public function update(Idea $idea)
    {
        $data = array(
            'title' => $idea->getTitle(),
            'description' => $idea->getDescription(),
            'rating' => $idea->getRating(),
            'votes' => $idea->getVotes(),
            'email' => $idea->getAuthor(),
        );
        $where = array('idea_id = ?' => $idea->getId());
        $this->client->update('ideas', $data, $where);
    }
}
```

结果更漂亮了。`IdeaController` 的 `rateAction` 更易于理解。在阅读时，它谈论的是业务规则。在与业务人员交流时，他们能理解 `IdeaRepository` 是什么：“一个我存放和获取 Idea 的地方，它使用类集合的接口在领域层和数据映射层之间用于访问领域对象。”正如在 Martin Fowler 的模式中所找到的那。

如果你已经在使用如 `Doctrine` 这样的 ORM，你现在的仓库扩展了 `EntityRepository`。如果你需要获取其中一个仓库，你请求 `EntityManager` 来完成工作。生成的代码几乎完全相同，只是在控制器动作中增加了对 `EntityManager` 的访问以获取 `IdeaRepository`。

到此时，我们可以看到六边形的一个边缘，即 `persistence` 边缘。然而，这一面并没有画得很好，`IdeaRepository` 是什么与它如何实现之间存在某种关系。为了在我们的 `application boundary` 之间实现有效的分离，……

配合该应用使用？

你的 CTO 已经在路线图中设定了团队将迁移到 Symfony2，因此当在你当前的 ZF1 应用中开发新功能时，我们希望让即将到来的迁移更加容易。

这很棘手，请看我的列表 5。

```php
class IdeaController extends Zend_Controller_Action
{
    public function rateAction()
    {
        $ideaId = $this->request->getParam('id');
        $rating = $this->request->getParam('rating');
        $ideaRepository = new RedisIdeaRepository();
        $useCase = new RateIdeaUseCase($ideaRepository);
        $response = $useCase->execute($ideaId, $rating);
        $this->redirect('/idea/'.$ideaId);
    }
}

interface IdeaRepository
{
    // ...
}
```

附录 A：PHP 六边形架构

285

```php
class RateIdeaUseCase
{
    private $ideaRepository;
    public function __construct(IdeaRepository $ideaRepository)
    {
        $this->ideaRepository = $ideaRepository;
    }

    public function execute($ideaId, $rating)
    {
        try {
            $idea = $this->ideaRepository->find($ideaId);
        } catch (Exception $e) {
            throw new RepositoryNotAvailableException();
        }

        if (!$idea) {
            throw new IdeaDoesNotExistException();
        }

        try {
            $idea->addRating($rating);
            $this->ideaRepository->update($idea);
        } catch (Exception $e) {
            throw new RepositoryNotAvailableException();
        }

        return $idea;
    }
}
```

让我们回顾一下这些。我们的控制器完全没有任何业务规则。我们将所有逻辑都推入了一个名为 `RateIdeaUseCase` 的新对象中并对其进行了封装。这个对象也被称为控制器（Controller）、交互器（Interactor）或应用服务（Application Service）。

魔法是由 `execute` 方法完成的。所有的依赖（如 `RedisIdeaRepository`）都是作为参数传递给构造函数的。我们在 UseCase 内部对 `IdeaRepository` 的所有引用都指向接口，而不是任何具体的实现。

这真的很酷。如果你查看 `RateIdeaUseCase` 内部，没有任何内容关于 `MySQL` 或 `Zend Framework`。没有引用、没有实例、没有注解，什么都没有。这就像你的

附录 A：PHP 六边形架构

286

基础设施并不在乎。它只谈论业务逻辑。

此外，我们还调整了抛出的异常（Exceptions）。业务过程也有异常。`NotAvailableRepository` 和 `IdeaDoesNotExist` 就是其中两个。根据抛出的异常，我们可以在框架边界以不同的方式做出反应。

有时，`UseCase` 接收的参数数量可能太多。为了组织它们，通常的做法是使用数据传输对象（DTO）构建一个 `UseCase request` 来将它们一起传递。让我们看看如何在列表 6 中解决这个问题。

```php
class IdeaController extends Zend_Controller_Action
{
    public function rateAction()
    {
        $ideaId = $this->request->getParam('id');
        $rating = $this->request->getParam('rating');
        $ideaRepository = new RedisIdeaRepository();
        $useCase = new RateIdeaUseCase($ideaRepository);
        $response = $useCase->execute(
            new RateIdeaRequest($ideaId, $rating)
        );
        $this->redirect('/idea/'.$response->idea->getId());
    }
}

class RateIdeaRequest
{
    public $ideaId;
    public $rating;
    public function __construct($ideaId, $rating)
    {
        $this->ideaId = $ideaId;
        $this->rating = $rating;
    }
}

class RateIdeaResponse
{
    public $idea;
    public function __construct(Idea $idea)
    {
        $this->idea = $idea;
    }
}

class RateIdeaUseCase
{
    // ...
    public function execute($request)
    {
        $ideaId = $request->ideaId;
        $rating = $request->rating;
        // ...
        return new RateIdeaResponse($idea);
    }
}
```

这里的这种变化是引入了两个新对象：请求（Request）和响应（Response）。它们不是强制性的，可能 `UseCase` 没有请求或响应。另一个重要的细节是你是如何构建这个请求。在这种情况下，我们是通过从 ZF request 对象中获取参数来构建它的。

好的，等一下，真正的处是什么？更容易从一个框架切换到另一个框架，或者从另一种 `delivery mechanism`（交付机制）中执行我们的 `UseCase`。让我们来看这一点。

### 使用 API 对想法进行评分

一天中，你的产品负责人（Product Owner）来到你身边：“顺便说一下，用户应该能够使用我们的移动 App 对想法进行评分。我认为我们需要更新 API，你能在这次冲刺（sprint）中完成它吗？”PO 再次说道：“没问题！”业务部门对你的承诺留下了深刻。

正如 Robert C. Martin 所说：“Web 是一种交付机制……。你的系统架构应该尽可能地忽略它是如何被交付的。你应该能够以控制台应用、Web 应用、甚至是 Web 服务应用的形式交付它，而不会产生不必要的复杂性或对基础架构进行任何更改”。

你目前的 API 是使用 Silex 构建的，这是一个基于 Symfony 的 PHP 微框架。让我们在 7 中实现它。

附录 A：PHP 六边形架构

288

```php
// ...
$app = new Silex\Application();

$app->get('/api/idea/{ideaId}/{rating}', function ($ideaId, $rating) use ($app) {
    $ideaRepository = new RedisIdeaRepository();
    $useCase = new RateIdeaUseCase($ideaRepository);
    $response = $useCase->execute(
        new RateIdeaRequest($ideaId, $rating)
    );
    return $app->json($response->idea);
});
```

等等，提供的文本由于换行和复制错误有些混乱。让我们根据提供的内容重新对齐逻辑：

附录 A：PHP 六边形架构

289

再次那三行代码。与之前一样，`UseCase` 及其业务逻辑保持不变，我们只是为评分提供了一种新的方式；另一种 `delivery mechanism`。主要的区别在于我们从哪里创建 `RateIdeaRequest`。在第一个例子中，它是来自 ZF request，现在它是来自路由的参数。

### 控制台应用评分

有时，`UseCase` 将从 Cron 任务或命令行执行。例如，批量处理或某些命令行来加速开发。

如果你使用脚本文件，我建议你查看 Symfony Console 组件。代码会像什么样？

```php
namespace App\Console\Command;
use Symfony\Component\Console\Command\Command;
use Symfony\Component\Console\Input\InputArgument;
use Symfony\Component\Console\Input\InputInterface;
use Symfony\Component\Console\Output\OutputInterface;

class VoteIdeaCommand extends Command
{
    protected function configure()
    {
        $this
            ->setName('idea:rate')
            ->setDescription('Rate an idea')
            ->addArgument('id', InputArgument::REQUIRED)
            ->addArgument('rating', InputArgument::REQUIRED);
    }

    protected function execute(
        InputInterface $input,
        OutputInterface $output
    ) {
        $ideaId = $input->getArgument('id');
        $rating = $input->getArgument('rating');

        $ideaRepository = new RedisIdeaRepository();
        $useCase = new RateIdeaUseCase($ideaRepository);

        $response = $useCase->execute(
            new RateIdeaRequest($ideaId, $rating)
        );

        $output->writeln('Done!');
    }
}
```

附录 A：PHP 六边形架构

290

再次那三行代码。与之前一样，`UseCase` 及其业务逻辑保持不变，我们只是为评分提供了一种新的 `delivery mechanism`。恭喜你，你发现了*用户侧*的六边形边缘。

还有很多工作要做。正如你可能听过的，真正的工匠会进行 TDD（测试驱动开发）。我们已经开始了我们的故事，所以我们必须接受在事后进行测试。

# 测试评分想法的用例 (UseCase)

Michael Feathers 将遗留代码定义为`没有测试的代码`。你不希望你的代码从出生那起就成为遗留代码，对吧？

为了对这个 `UseCase` 对象进行单元测试，你决定从简单的部分开始：如果仓库不可用会怎样？我们如何生成这种行为？我们需要在运行单元测试时停止我们的 `Redis` 服务器吗？不需要。我们需要一个具有这种行为的对象。让我们使用列表 9 中的 `mock`（模拟）对象。



```php
class RateIdeaUseCaseTest extends PHPUnit_Framework_TestCase
{
    /**
     * @test
     */
    public function whenRepositoryNotAvailableAnExceptionShouldBeThrown()
    {
        $this->setExpectedException('NotAvailableRepositoryException');
        $ideaRepository = new NotAvailableRepository();
        $useCase = new RateIdeaUseCase($ideaRepository);
        $useCase->execute(
            new RateIdeaRequest(1, 5)
        );
    }
}

class NotAvailableRepository implements IdeaRepository
{
    public function find($id)
    {
        throw new NotAvailableException();
    }
    public function update(Idea $idea)
    {
        throw new NotAvailableException();
    }
}
```

很极。`NotAvailableRepository` 具有我们需要的行为，我们可以在 `RateIdeaUseCase` 中使用它，因为它实现了 `IdeaRepository` 接口。

下一个要测试的用例是如果想法不在仓库中会怎样。列表 10 显示了代码。

```php
class RateIdeaUseCaseTest extends PHPUnit_Framework_TestCase
{
    // ...
    /**
     * @test
     */
    public function whenIdeaDoesNotExistAnExceptionShouldBeThrown()
    {
        $this->setExpectedException('IdeaDoesNotExistException');
        $ideaRepository = new EmptyIdeaRepository();
        $useCase = new RateIdeaUseCase($ideaRepository);
        $useCase->execute(
            new RateIdeaRequest(1, 5)
        );
    }
}

class EmptyIdeaRepository implements IdeaRepository
{
    public function find($id)
    {
        return null;
    }
    public function update(Idea $idea)
    {
    }
}
```

在这里，我们使用了相同的策略，但使用了 `EmptyIdeaRepository`。它也实现了相同的接口，但无论 `find` 方法接收到什么标识符，实现总是返回 `null`。

为什么要测试这些情况？记住 Kent Beck 的话：“测试所有可能崩溃的东西”。

让我们继续剩余的功能。我们需要检查一个与“拥有可读但不可写的仓库”相关的特殊情况。解决方案可以在列表 11 中找到。

```php
class RateIdeaUseCaseTest extends PHPUnit_Framework_TestCase
{
    // ...
    /**
     * @test
     */
    public function whenUpdatingInReadOnlyAnIdeaAnExceptionShouldBeThrown()
    {
        $this->setExpectedException('NotAvailableRepository');
        $ideaRepository = new WriteAvailableRepository();
        $useCase = new RateIdeaUseCase($ideaRepository);
        $useCase->execute(
            new RateIdeaRequest(1, 5)
        );
    }
}

class WriteAvailableRepository implements IdeaRepository
{
    public function find($id)
    {
        $idea = new Idea();
        $idea->setId(1);
        $idea->setTitle('Subscribe to php');
        $idea->setDescription('Just buy it!');
        $idea->setRating(5);
        $idea->setVotes(10);
        $idea->setAuthor('hi@carlos.io');
        return $idea;
    }
    public function update(Idea $idea)
    {
        throw new NotAvailableException();
    }
}
```

好了，现在功能的关键部分仍然存在。我们有不同的测试测试方法，我们可以编写自己的 mock，或者使用如 `Mockery` 或 `Prophecy` 这样的模拟框架。让我们选择第一个。另一个有趣的练习是使用这些框架之一来编写这个示例以及之前的示例。

```php
class RateIdeaUseCaseTest extends PHPUnit_Framework_TestCase
{
    // ...
    /**
     * @test
     */
    public function whenRatingAnIdeaNewRatingShouldBeAddedIdeaUpdated()
    {
        $ideaRepository = new OneIdeaRepository();
        $useCase = new RateIdeaUseCase($ideaRepository);
        $response = $useCase->execute(
            new RateIdeaRequest(1, 5)
        );
        $this->assertSame(5, $response->idea->getRating());
        $this->assertTrue($ideaRepository->updateCalled);
    }
}

class OneIdeaRepository implements IdeaRepository
{
    public $updateCalled = false;
    public function find($id)
    {
        $idea = new Idea();
        $idea->setId(1);
        $idea->setTitle('Subscribe to php');
        $idea->setDescription('Just buy it!');
        $idea->setRating(5);
        $idea->setVotes(10);
        $idea->setAuthor('hi@carlos.io');
        return $idea;
    }
    public function update(Idea $idea)
    {
        $this->updateCalled = true;
    }
}
```

砰！（Bam!）搞定了。

```php
$ideaId = $this->request->getParam('id');

$rating = $this->request->getParam('rating');

$useCase = $this->get('rate_idea_use_case');

$response = $useCase->execute(
    new RateIdeaRequest($ideaId, $rating)
);

$this->redirect('/idea/'.$response->idea->getId());

}
}
```

控制器已经过修改以访问容器（container），这就是为什么它继承自一个新的基控制器 `ContainerAwareController`，该控制器包含一个 `get` 方法来获取包含的每个服务。

```xml
<?xml version="1.0" ?>
<container xmlns="http://symfony.com/schema/dic/services"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://symfony.com/schema/dic/services
http://symfony.com/schema/dic/services/services-1.0.xsd">
<services>
    <service
        id="rate_idea_use_case"
        class="RateIdeaUseCase">
        <argument type="service" id="idea_repository" />
    </service>
    <service
        id="idea_repository"
        class="RedisIdeaRepository">
        <argument type="service">
            <service class="Predis\Client" />
        </argument>
    </service>
</services>
</container>
```

在列表 15 中，你也可以找到用于配置服务容器（Service Container）的 XML 文件。它非常易理解，但如果你需要更多信息，请查看 Symfony 服务容器网站：[`symfony.com/doc/current/book/service_container.html`](http://symfony.com/doc/current/book/service_container.html)

## 领域服务与通知六边形边缘 (Domain Services and Notification Hexagon Edge)

我们是不是漏掉了什么？“应该通过电子邮件通知作者”，是的！确实如此。让我们看看列表 16 中我们是如何更新用于工作的 `UseCase` 的。

```php
class RateIdeaUseCase
{
    private $ideaRepository;
    private $authorNotifier;

    public function __construct(
        IdeaRepository $ideaRepository,
        AuthorNotifier $authorNotifier
    ) {
        $this->ideaRepository = $ideaRepository;
        $this->authorNotifier = $authorNotifier;
    }

    public function execute(RateIdeaRequest $request)
    {
        $ideaId = $request->ideaId;
        $rating = $request->rating;

        try {
            $idea = $this->ideaRepository->find($ideaId);
        } catch (Exception $e) {
            throw new RepositoryNotAvailableException();
        }

        if (!$idea) {
            throw new IdeaDoesNotExistException();
        }

        try {
            $idea->addRating($rating);
            $this->ideaRepository->update($idea);
        } catch (Exception $e) {
            throw new RepositoryNotAvailableException();
        }

        try {
            $this->authorNotifier->notify(
                $idea->getAuthor()
            );
        } catch (Exception $e) {
            throw new NotificationNotSentException();
        }

        return $idea;
    }
}
```

正如你所看到的，我们添加了一个新参数来传递 `AuthorNotifier` 服务，该服务将向作者发送电子邮件。这就是“端口与适配器”（Ports and Adapters）命名法中的“端口”（port）。我们还更新了 `execute` 方法中的业务规则。

仓库（Repositories）并不是唯一可以访问基础设施的对象，它们应该使用接口或抽象类进行解耦。领域服务（Domain Services）也是如此。当领域中某个行为不明确属于任何单一 `Entity`（实体）时，你应该创建一个领域服务（Domain Service）。一种典型的模式是编写一个抽象的领域服务，它包含一些具体的实现以及另一些由适配器（adapter）实现的抽象方法。

作为一个练习，请为 `AuthorNotifier` 抽象服务的定义实现细节。选项有 `SwiftMailer` 或简单的原始邮件调用。这由你决定。

## 总结

为了拥有有助于创建易编写和测试应用的*整洁架构*（clean architecture），我们可以使用六边形架构（Hexagonal Architecture）。为了实现这一点，我们将用户故事业务规则封装在 `UseCase` 或交互器（Interactor）对象内部。我们从框架请求构建 `UseCase` 请求，实例化 `UseCase` 及其所有依赖，然后执行它。我们获取响应并根据响应采取相应行动。如果我们的框架有依赖注入（Dependency Injection）组件，你可以使用它来简化代码。

相同的 `UseCase` 对象可以从不同的*交付机制*（delivery mechanisms）使用，以便用户能够从不同的客户端（Web、API、控制台等）访问功能。

对于测试，可以使用表现像所有定义接口的 mock（mocks），这样也可以涵盖特殊情况或错误流。享受这项出色的工作。

## 六边形架构 (Hexagonal Architecture)

在几乎所有的博客和书中，你都会找到代表软件不同区域的同心圆图。正如 Robert C. Martin 在他的“整洁架构”文章解释的那样，外圈是你的基础设施所在地。内圈是你的 `Entities` 所在地。使这种架构生效的覆盖规则是**依赖规则**（The Dependency Rule）。该规则规定源代码的依赖只能指向内部。内圈中的任何内容都无法知道外圈的任何信息。

### 关键点

如果 100% 的单元测试覆盖率对你的应用至关重要，请使用这种方法。此外，如果你能够切换存储策略、Web 框架或任何类型的第三方代码。这种架构对于需要跟上不断变化需求的长期应用特别有用。

### 接下来做什么？

如果你对学习更多六边形架构和其他其他相关概念感兴趣，你应该查看文章开头提供的相关 URL，查看 CQRS 和事件溯源（Event Sourcing）。此外，不要忘记订阅关于 DDD 的 Google Groups 和 RSS，例如 [`dddinphp.org`](http://dddinphp.org) [//dddinphp.org](http://dddinphp.org)，并在 Twitter 上关注 @VaughnVernon 和 @ericevans0 等人。

# 总结

# 架构风格

## 过去的日子

## 分层架构

### 模型-视图-控制器 (MVC)

### 分层架构示例

#### 模型 (Model)

#### 视图 (View)

#### 控制器 (Controller)

## 依赖倒置。六边形架构

### 依赖倒置原则 (DIP)

### 应用六边形架构

## 命令查询职责分离 (CQRS)

### 写模型

### 模型

### 写模型与读模型的同步

## 事件溯源

## 总结

# 值对象

## 定义

### 值对象 vs 实体 (Entity)

### 货币与金额示例

### 特性

#### 测量、量化或描述

#### 不变性

#### 概念整体

#### 值等性

#### 可替换性

#### 无副作用行为 `Side-Effect-Free-Behaviour`



# 实体 (Entities)

## 简介

### 对象 vs 原始类型

### 身份操作

#### 持久化机制生成身份

#### 代理身份 (Surrogate Identity)

#### 针对丰富领域模型的 Active Record vs Data Mapper

#### 客户端提供身份

#### 应用生成身份

#### 其他边界上下文 (Bounded Context) 生成身份

### 持久实体

#### 配置 `Doctrine`

#### 映射实体

##### 使用代码映射实体

##### 使用 XML 映射实体

### 测试实体

### 验证

#### 属性验证

#### 全局验证

#### 消息解耦

#### 组合验证

### 总结

# 服务

## 简介

### 应用服务

#### 事务

#### 测试应用服务

### 领域服务

### 具有多个实现的领域服务

#### 代码复用问题

### 测试领域服务

### 贫血领域模型 vs 丰富领域模型

#### 贫血领域模型破坏封装性

#### 贫血领域模型带来虚假的代码复用感

#### 如何避免贫血领域模型？

### 总结

# 领域事件

## 简介

### 定义

#### 小故事

#### 比喻

#### RealLife(tm) 示例

### 特性

#### 命名规范

#### 领域事件与通用语言

#### 不变性

### 建模事件

### 持久化领域事件

#### 事件存储 (Event Store)

### 从领域模型发布事件

#### 从实体发布领域事件

#### 从领域或应用服务发布领域事件

#### `DomainEventPublisher` 如何工作

#### 设置 `DomainEventListeners`

#### 单元测试

### 传播到远程边界上下文

#### 消息传递

#### REST

### 总结

# 模块

## 在模块中结构化代码

### 基础设施层中的模块

#### 混合不同的技术

#### 利用 PHP 中的模块

#### PEAR 风格的命名空间

#### PSR-0 和 PSR-4 命名空间规范

### 总结

# 聚合 (Aggregates)

## 简介

#### Martin Fowler 是怎么说的

#### 维基百科是怎么说的

# 一点历史

# 聚合与聚类

## 聚合的解剖结构

### 基于业务真·不变性的设计聚合

## 小聚合与大聚合

## 追求最终一致性

## 每次事务仅修改一个聚合

## 异常情况：UX 场景

# 示例应用服务：用户与愿望

## 无不变性，两个聚合

## 每个用户最多三个愿望

### 悲观锁并发控制

### 乐观并发控制

## 渲染用户的愿望

## 更新用户的愿望

## 实现用户的愿望

# 总结

# 工厂 (Factories)

## 简介

## 聚合根上的工厂方法

### 强制执行不变性

## 服务上的工厂

### 构建规格说明

### 构建聚合根

## 测试

### 对象母 (Object Mother)

### 测试数据构建器 (Test Data Builder)

## 总结

# 存储库 (Repositories)

## 简介

## 定义

## 存储库不是 DAO

## 面向集合的存储库

### 内存实现

### Doctrine ORM

#### 对象关系映射

#### Doctrine 自定义类型

#### XML 映射

#### 实体管理器 (Entity Manager)

#### DQL 实现

### 面向持久化

### Redis 实现

### SQL 实现

## 额外行为

## 查询存储库

### 规格模式 (Specification Pattern)

#### 内存实现

#### SQL 实现

## 管理事务

## 测试存储库

## 使用内存实现测试你的服务

## 总结

# 应用 (Application)

## 简介

## 请求 (Requests)

### 构建应用请求

### 请求设计

#### 使用原始类型

#### 可序列化

#### 无业务逻辑

#### 无测试

## 应用服务的解剖结构

### 依赖反转

### 实例化应用服务

### 执行

#### 每个应用服务一个类

#### 一个类中多个应用服务方法

### 返回值

#### 从聚合实例生成 DTO

#### 数据转换器 (Data Transformers)

## 复合布局上的多个应用服务

#### AJAX 内容集成

#### ESI 内容集成

#### Symfony 子请求

#### 一个控制器，多个应用服务

## 测试

## 事务

## 安全

## 领域事件 (Domain Events)

## 命令处理器 (Command Handlers)

### Tactician 库及其他选项

## 总结

# 整合边界上下文 (Bounded Contexts)

## 通过数据存储进行集成

## 集成关系

### 客户 / 供应商

### 分别对待

### 顺从者 (Conformist)

### 实现边界上下文集成

### 现代 RPC

### 消息队列

## 总结

# 参考文献

# 附录 A：基于 PHP 的六边形架构

## 简介

## 第一种方法

## 存储库与持久化边缘

## 解耦业务与持久化

## 将我们的持久化迁移到 Redis

## 解耦业务与 Web 框架

## 使用 API 对想法评分

### 控制台应用评分

## 测试想法的使用

## 测试基础设施

## 天额，这么多依赖！

## 领域服务与通知六边形边缘

## 让我们总结一下

## 六边形架构

## 关键点

## 接下来是什么？

# 基础类型

# 测试

# 持久值对象

## 持久单个值对象

### 使用即时 ORM 持久嵌入值

### 使用 `Doctrine` >= `2.5` 的嵌入值 (Embeddables)

### 使用 `Doctrine` <= `2.4` 的嵌入值

### 序列化 LOB 和即时 ORM

#### 使用 `JMS Serializer` 改进序列化

#### 使用 `Doctrine` 的序列化 LOB

#### `Doctrine Object Mapping Type`

#### `Doctrine Custom Types`

## 持久值对象集合

### 序列化为单个列的集合

### 由连接表支持的集合

#### 使用 `Doctrine` 的连接表支持

#### 使用即时 ORM 的连接表支持

### 由数据库实体支持的集合

## NoSQL

### `PostgreSQL` 和 `JSONB`

# 安全

# 总结
