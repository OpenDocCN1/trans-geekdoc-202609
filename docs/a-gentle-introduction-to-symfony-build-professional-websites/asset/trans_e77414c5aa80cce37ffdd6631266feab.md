

## 附录

## 附录 A

### 模型层内部 (Propel)

目前为止的讨论大多集中在构建页面以及处理请求和响应上。但 Web 应用程序的业务逻辑主要依赖于其数据模型。Symfony 的默认模型组件基于对象/关系映射层。Symfony 自带了两种最流行的 PHP ORM：Propel 和 Doctrine。在 symfony 应用程序中，您通过对象访问存储在数据库中的数据并对其进行修改；您从不直接操作数据库。这保持了高度的抽象性和可移植性。

本章解释了如何创建对象数据模型，以及在 Propel 中访问和修改数据的方式。它还演示了 Propel 在 Symfony 中的集成。

### 为什么使用 ORM 和抽象层？

数据库是关系型的。PHP 5 和 symfony 是面向对象的。为了在面向对象的上下文中最有效地访问数据库，需要一个将对象逻辑转换为关系逻辑的接口。如第 1 章所述，这个接口称为对象关系映射（ORM），它由提供数据访问并将业务规则封装在自身中的对象组成。

ORM 的主要好处是可重用性，它允许从应用程序的各个部分（甚至不同的应用程序）调用数据对象的方法。ORM 层还封装了数据逻辑——例如，根据论坛用户的贡献数量及其受欢迎程度计算用户评级。当页面需要显示此类用户评级时，它只需调用数据模型的一个方法，而无需担心计算细节。如果计算随后发生变化，您只需修改模型中的评级方法，其余应用程序保持不变。

使用对象代替记录、使用类代替表，还有另一个好处：它们允许您向对象添加新的访问器，而这些访问器不一定对应表中的某一列。例如，如果您有一个名为 client 的表，其中包含 first_name 和 last_name 两个字段，您可能希望只需一个 Name。在面向对象的世界中，只需向 Client 类添加一个新的访问器方法即可，如清单 8-1 所示。从应用程序的角度来看，Client 类的 FirstName、LastName 和 Name 属性之间没有区别。只有类本身可以确定哪些属性对应数据库列。

```
Listing 8-1 - Accessors Mask the Actual Table Structure in a Model Class

public function getName()
{
    return $this->getFirstName().' '.$this->getLastName();
}
```

所有重复的数据访问函数和数据本身的业务逻辑都可以保存在这样的对象中。假设您有一个 ShoppingCart 类，其中保存了 Items（即对象）。为了获取购物车的总金额以供结账，请编写一个自定义方法来封装实际计算，如清单 8-2 所示。

### 清单 8-2 - 访问器掩盖数据逻辑

```
public function getTotal()
{
    $total = 0;
    foreach ($this->getItems() as $item)
    {
        $total += $item->getPrice() * $item->getQuantity();
    }

    return $total;
}
```

在构建数据访问过程时，还需要考虑另一个重要点：数据库厂商使用不同的 SQL 语法变体。切换到另一个数据库管理系统（DBMS）迫使您重新编写为之前系统设计的部分 SQL 查询。如果您使用与数据库无关的语法构建查询，并将实际的 SQL 转换留给第三方组件，您可以无痛切换数据库系统。这就是数据库抽象层的目标。它强制您对查询使用特定语法，并承担符合 DBMS 特性和优化 SQL 代码的繁琐工作。

抽象层的主要好处是可移植性，因为它使得即使在项目中期也可以切换到另一个数据库。假设您需要为一个应用程序编写快速原型，但客户尚未决定哪种数据库系统最适合他的需求。例如，您可以先使用 SQLite 构建应用程序，并在客户准备好做出决定时切换到 MySQL、PostgreSQL 或 Oracle。只需更改配置文件中的一行，即可生效。

Symfony 将 Propel 或 Doctrine 用作 ORM，它们使用 PHP Data Objects 进行数据库抽象。这两个第三方组件（均由 Propel 和 Doctrine 团队开发）已无缝集成到 symfony 中，您可以将它们视为框架的一部分。本章中描述的它们的语法和约定已进行了调整，以便与 symfony 的语法和约定尽可能一致。

> 在 symfony 项目中，所有应用程序共享同一个模型。这就是项目级别的全部意义：将依赖共同业务规则的应用程序组合在一起。这就是模型独立于应用程序的原因，模型文件存储在项目根目录的 lib/model/ 目录中。

### Symfony 的数据库架构

为了创建 symfony 将使用的对象数据模型，您需要将数据库中的关系模型转换为对象数据模型。ORM 需要关系模型的描述来进行映射，这称为架构（schema）。在架构中，您定义表、它们的关系以及列的特性。

Symfony 对架构的语法使用 YAML 格式。schema.yml 文件必须位于 myproject/config/ 目录中。

> Symfony 还理解 Propel 的原生 XML 架构格式，如本章稍后“超越 schema.yml：schema.xml”节中所述。

### 架构示例

如何将数据库结构转换为架构？示例是理解它的最佳方式。假设您有一个包含两个表的博客数据库：blog_article 和 blog_comment，结构如图 8-1 所示。

### 图 8-1 - 博客数据库表结构

![](img/0f886a7f4cbcc3939be96e985ca35ff4_360_0.png)

相关的 schema.yml 文件应如清单 8-3 所示。

### 清单 8-3 - 示例 schema.yml

```
propel:
  blog_article:
    _attributes: { phpName: Article }
    id:
    title: varchar(255)
    content: longvarchar
    created_at: ~
  blog_comment:
    _attributes: { phpName: Comment }
    id: ~
    blog_article_id: ~
    author: varchar(255)
    content: longvarchar
    created_at: ~
```

请注意，数据库名称本身（blog）不会出现在 schema.yml 文件中。相反，数据库是在连接名称下描述的（本示例中为 propel）。这是因为实际连接设置可能取决于应用程序运行的环境。例如，当您在开发环境中运行应用程序时，将访问开发数据库（可能是 blog_dev），但与生产数据库具有相同的架构。连接设置将在本章稍后“数据库连接”节中描述的 databases.yml 文件中指定。架构不包含任何详细的连接设置，只包含一个连接名称，以保持数据库抽象。

### 基本架构语法

在 schema.yml 文件中，第一个键表示连接名称。它可以包含多个表，每个表都有一组列。根据 YAML 语法，键以冒号结尾，结构通过缩进显示（一个或多个空格，但没有制表符）。

表可以具有特殊属性，包括 phpName（将生成的类的名称）。如果您未为表提及 phpName，symfony 将根据表名的 camelCase 版本创建它。

> camelCase 约定从单词中删除下划线，并将内部单词的首字母大写。blog_article 和 blog_comment 的默认 camelCase 版本分别是 BlogArticle 和 BlogComment。此约定的名称来源于长单词内部大写字母的外观，类似于骆驼的驼峰。

表包含列。列值可以以三种不同的方式定义：

- 如果您未定义任何内容（YAML 中的 ~ 相当于 PHP 中的 null），symfony 将根据列名和本章稍后“空列”节中描述的若干约定，推断最佳属性。例如，清单 8-3 中的 id 列无需定义。Symfony 会将其设置为自动递增的整数，即表的主键。blog_comment 表中的 blog_article_id 将被理解为 blog_article 表的外键（以 _id 结尾的列被视为外键，相关表会根据列名的第一部分自动确定）。名为 created_at 的列会自动设置为时间戳类型。对于所有这些列，您无需指定任何类型。这就是 schema.yml 如此易于编写的原因之一。

- 如果您仅定义一个属性，则为列类型。Symfony 了解常见的列类型：boolean、integer、float、date、varchar(size)、longvarchar（例如，在 MySQL 中转换为 text）等等。对于超过 256 个字符的文本内容，您需要使用 longvarchar 类型，该类型没有大小限制（但在 MySQL 中不能超过 65KB）。

- 如果您需要定义其他列属性（如默认值、必填项等），应将列属性编写为一组 key: value。这种扩展架构语法将在本章稍后描述。

列也可以带有 phpName 属性，即名称的大写版本（Id、Title、Content 等），在大多数情况下不需要覆盖。

表还可以包含显式外键和索引，以及一些特定于数据库的结构定义。要了解更多信息，请参阅本章稍后的“扩展架构语法”节。

### 模型类

架构用于构建 ORM 层的模型类。为了节省执行时间，这些类是通过名为 propel:build-model 的命令行任务生成的。

```
Listing A-4
$ php symfony propel:build-model
```

> 构建模型后，您必须记得使用 php symfony cc 清除 symfony 的内部缓存，以便 symfony 找到您新创建的模型。

输入此命令将启动架构的分析，并在项目的 lib/model/om/ 目录中生成基础数据模型类：

- BaseArticle.php
- BaseArticlePeer.php
- BaseComment.php

