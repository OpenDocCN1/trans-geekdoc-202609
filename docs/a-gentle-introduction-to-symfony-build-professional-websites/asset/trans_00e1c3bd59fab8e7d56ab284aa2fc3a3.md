

## 第 18 章 性能

如果您预期网站会吸引大量访客，那么在开发阶段，性能和优化问题应是主要考虑因素。请放心，性能一直是 symfony 核心开发者的首要关注点。

虽然加速开发过程带来的好处会产生一些开销，但 symfony 核心开发者始终意识到性能要求。因此，每个类和每个方法都经过了仔细检查和优化，以尽可能快地运行。基本开销（可以通过比较使用 symfony 和不使用 symfony 时显示“hello, world”消息所需的时间来衡量）非常小。因此，该框架具有可扩展性，并且对压力测试反应良好。作为最终证明，一些流量极高的网站（即拥有数百万活跃用户和大量会给服务器带来压力的 Ajax 交互的网站）使用 symfony，并对其性能非常满意。

当然，高流量网站通常有能力根据需要扩展服务器场和升级硬件。如果您没有资源这样做，或者想确保框架的全部功能始终可用，可以使用一些调整来进一步加速 symfony 应用程序。本章列出了框架各个层面推荐的性能优化，大多面向高级用户。其中一些在前面章节中已提及，但将它们汇总在一起会很有用。

## 调整服务器

一个优化良好的应用程序应该依赖于一个优化良好的服务器。您应该了解服务器性能的基础知识，以确保 symfony 外部没有瓶颈。以下是一些检查事项，以确保您的服务器没有不必要的缓慢。

在 `php.ini` 中将 `magic_quotes_gpc` 设置为 `true` 会减慢应用程序速度，因为它会要求 PHP 转义请求参数中的所有引号，但 symfony 之后会系统地取消转义它们，唯一后果是时间浪费——以及某些平台上的引号转义问题。因此，如果您可以访问 PHP 配置，请关闭此设置。

使用的 PHP 版本越新越好（PHP 5.3 比 PHP 5.2 快）。因此，请确保升级 PHP 版本以获取最新的性能改进。

62. http://sf.to.org/answers
63. http://sf.to.org/delicious
64. http://sf.to.org/dailymotion

对于生产服务器来说，使用 PHP 加速器（例如 APC、XCache 或 eAccelerator）几乎是必不可少的，因为它可以使 PHP 平均运行速度提高 50%，且没有任何权衡。请确保安装其中一个加速器扩展，以感受 PHP 的真实速度。

另一方面，请确保在生产服务器上禁用任何调试实用程序，例如 Xdebug 或 APD 扩展。

您可能会好奇 mod_rewrite 扩展造成的开销：它可以忽略不计。当然，使用重写规则加载图像比不使用重写规则加载图像要慢，但减速的程度比执行任何 PHP 语句要低几个数量级。

当一台服务器不够用时，您仍然可以添加另一台并使用负载均衡。只要 uploads/ 目录是共享的并且您使用数据库存储会话，symfony 项目在负载均衡架构中将能够无缝运行。

## 调整模型

在 symfony 中，模型层以是最慢的部分而闻名。如果基准测试显示您需要优化此层，以下是一些可能的改进。

## 优化 Propel 或 Doctrine 集成

初始化模型层（核心 ORM 类）需要一些时间，因为需要加载一些类并构建各种对象。然而，由于 symfony 集成这两个 ORM 的方式，这些初始化任务仅在操作实际需要模型时发生——并且尽可能晚。只有当生成的模型对象被自动加载时，ORM 类才会被初始化。这意味着不使用模型的页面不会受到模型层的惩罚。

如果您的整个应用程序不需要使用模型层，还可以通过在 settings.yml 中关闭整个层来保存 sfDatabaseManager 的初始化：

```
all:
  .settings:
    use_database: false
```

## Propel 增强功能

生成的模型类（在 lib/model/om/ 中）已经过优化——它们不包含注释，并且受益于自动加载系统。依赖自动加载而不是手动包含文件意味着只有在真正需要时才会加载类。因此，如果不需要某个模型类，自动加载类将节省执行时间，而使用 include 语句的替代方法则不会。至于注释，它们记录生成方法的用法，但会增加模型文件的长度——在慢速磁盘上会造成轻微开销。由于生成的方法名称非常明确，注释默认是关闭的。

这两个增强功能是 symfony 特有的，但您可以通过更改 propel.ini 文件中的两个设置来恢复 Propel 默认值，如下所示：

```
propel.builder.addIncludes = true     # Add include statements in generated classes
                                      # Instead of relying on the
autoloading system
propel.builder.addComments = true  # Add comments to generated classes
```

## 限制要水合的对象数量

当您使用 Peer 类的方法来检索对象时，您的查询会经过水合过程（即根据查询结果的行创建并填充对象）。例如，要使用 Propel 检索 article 表的所有行，您通常执行以下操作：

```
$articles = ArticlePeer::doSelect(new Criteria());
```

The resulting $articles 变量是 Article 类对象的数组。每个对象都必须被创建和初始化，这需要时间。这有一个主要后果：与直接数据库查询相反，Propel 查询的速度与它返回的结果数量成正比。这意味着您的模型方法应优化为仅返回特定数量的结果。当您不需要 Criteria 返回的所有结果时，应使用 `setLimit()` 和 `setOffset()` 方法进行限制。例如，如果您只需要特定查询的第 10 到 20 行，请按清单 18-1 的方式优化 Criteria。

*清单 18-1 - 限制 Criteria 返回的结果数量*

```
$c = new Criteria();
$c->setOffset(10); // Offset of the first record returned
$c->setLimit(10); // Number of records returned
$articles = ArticlePeer::doSelect($c);
```

可以使用分页器来实现自动化。sfPropelPager 对象会自动处理 Propel 查询的偏移量和限制，以仅水合给定页面所需的对象。

## 使用连接减少查询数量

在应用程序开发期间，您应该留意每个请求发出的数据库查询数量。Web 调试工具栏显示每个页面的查询数量，单击小数据库图标会显示这些查询的 SQL 代码。如果您看到查询数量异常上升，是时候考虑使用连接了。

在解释连接方法之前，让我们回顾一下在遍历对象数组并使用 Propel getter 方法检索相关类详细信息时会发生什么，如清单 18-2 所示。此示例假设您的架构描述了一个 article 表，其中包含指向 author 表的外键。

*清单 18-2 - 在循环中检索相关类的详细信息*

```
// In the action, with Propel
$this->articles = ArticlePeer::doSelect(new Criteria());
// Or with Doctrine
$this->articles = Doctrine::getTable('Article')->findAll();

// Database query issued by doSelect()
SELECT article.id, article.title, article.author_id, ...
FROM article

// In the template
<ul>
<?php foreach ($articles as $article): ?>
<li><?php echo $article->getTitle() ?>,

