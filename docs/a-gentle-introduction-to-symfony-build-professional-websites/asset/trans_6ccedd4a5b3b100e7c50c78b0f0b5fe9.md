

->select('a.title, count(*) as nb_comments')
->leftJoin('a.Comments')
->groupBy('a.id')
->fetchArray();
}
}

当你开始构建此类方法时，可能最终会为每个操作编写一个自定义方法，从而失去层分离的好处——更不用说你还会失去数据库独立性。

## 加速数据库

无论你是否使用 symfony，都有许多特定于数据库的优化技术可供应用。本节简要概述了最常见的数据库优化策略，但要充分发挥模型层的性能，需要具备良好的数据库引擎和管理知识。

> 请记住，web 调试工具栏显示页面中每个查询所耗费的时间，并且应该监控每一次调整，以判断其是否真正提升了性能。

表查询通常基于非主键列。为了提高此类查询的速度，你应该在数据库架构中定义索引。要添加单列索引，请向列定义中添加 index: true 属性，如清单 18-10 所示。

清单 18-10 - 在 config/schema.yml 中添加单列索引

```
# Propel schema
propel:
  article:
    id:
    author_id:
    title: { type: varchar(100), index: true }

# Doctrine schema
Article:
  columns:
    author_id: integer
    title: string(100)
  indexes:
    title:
      fields: [title]
```

你可以使用替代的 index: unique 语法来定义唯一索引，而不是经典索引。你也可以在 schema.yml 中定义多列索引（关于索引语法的更多详细信息，请参阅第 8 章）。你应该强烈考虑这样做，因为这通常是加速复杂查询的一个好方法。

在架构中添加索引后，你也应该在数据库本身中执行同样的操作，可以直接在数据库中执行 ADD INDEX 查询，或者调用 propel-build-all 命令（这不仅会重建表结构，还会删除所有现有数据）。

> 索引往往会使 SELECT 查询更快，但 INSERT、UPDATE 和 DELETE 查询会更慢。此外，数据库引擎每个查询只使用一个索引，并且根据内部启发式规则推断每个查询应使用的索引。添加索引在性能提升方面有时会令人失望，因此请务必衡量改进情况。

除非另有说明，symfony 中的每个请求都使用单个数据库连接，并在请求结束时关闭连接。你可以通过在 databases.yml 文件中设置 persistent: true 来启用持久数据库连接，以使用在查询之间保持打开的数据库连接池，如清单 18-11 所示。

清单 18-11 - 在 config/databases.yml 中启用持久数据库连接支持

```
prod:
  propel:
    class: sfPropelDatabase
    param:
      dsn: mysql:dbname=example;host=localhost
      username: username
      password: password
      persistent: true # Use persistent connections
```

这可能会也可能不会改善整体数据库性能，这取决于众多因素。关于此主题的文档在互联网上非常丰富。请务必在更改此设置前后对应用程序性能进行基准测试，以验证其价值。

### MySQL 特定提示

my.cnf 文件中的许多 MySQL 配置设置可能会改变数据库性能。请务必阅读关于此主题的在线文档 65。

65. http://dev.mysql.com/doc/refman/5.0/en/option-files.html

MySQL 提供的工具之一是慢查询日志。执行时间超过 long_query_time 秒的所有 SQL 语句（这是可在 my.cnf 中更改的设置）都会记录在一个文件中，该文件手动解读相当困难，但 mysqldumpslow 命令能够有用地对其进行总结。这是检测需要优化的查询的绝佳工具。

## 调整视图

根据你设计和实现视图层的方式，你可能会注意到微小的减速或加速。本节描述了替代方案及其权衡。

### 使用最快的代码片段

如果你不使用缓存系统，则需要注意 include_component() 比 include_partial() 稍慢，而 include_partial() 本身又比简单的 PHP include 稍慢。这是因为 symfony 实例化一个视图来包含局部，并实例化 sfComponent 类的对象来包含组件，这两者合计在包含文件所需之外增加了一些微小的开销。

然而，除非在模板中包含大量局部或组件，否则这种开销可以忽略不计。这可能发生在列表或表格中，以及每次在 foreach 语句内部调用 include_partial() 辅助函数时。当你注意到大量局部或组件包含对性能有显著影响时，你可以考虑缓存（参见第 12 章），如果缓存不是选项，则切换到简单的 include 语句。

至于插槽，性能差异是可感知的。设置和包含插槽所需的处理时间可以忽略不计——它相当于变量实例化。插槽始终在包含它们的模板中缓存。

### 加速路由过程

如第 9 章所述，模板中每次调用链接辅助函数都会请求路由系统将内部 URI 处理为外部 URL。这是通过在 URI 和 routing.yml 文件的模式之间查找匹配来完成的。symfony 的做法非常简单：它尝试用给定的 URI 匹配第一条规则，如果不奏效，则尝试下一条，以此类推。由于每次测试都涉及正则表达式，这相当耗时。

有一个简单的解决办法：使用规则名称而不是模块/动作对。这将告诉 symfony 使用哪条规则，路由系统就不会浪费时间尝试匹配所有先前的规则。

具体来说，请考虑在你的 routing.yml 文件中定义的以下路由规则：

```
article_by_id:
  url:   /article/:id
  param: { module: article, action: read }
```

然后，不要以这种方式输出超链接：

```
<?php echo link_to('my article', 'article/read?id='.$article->getId()) ?>
```

你应该使用最快的版本：

```
<?php echo link_to('my article', 'article_by_id', array('id' =>
$article->getId())) ?>
```

当页面包含几十个路由超链接时，差异开始变得明显。

### 跳过模板

通常，响应由一组标头和内容组成。但某些响应不需要内容。例如，某些 Ajax 交互只需要服务器提供的几个数据片段，以供 JavaScript 程序更新页面的不同部分。对于这种简短响应，仅传输一组标头速度更快。如第 11 章所讨论，操作可以只返回 JSON 标头。清单 18-12 复制了第 11 章中的一个示例。

清单 18-12 - 返回 JSON 标头的操作示例

```
public function executeRefresh()
{
  $output = '{"title":"My basic letter","name":"Mr Brown"}';
  $this->getResponse()->setHttpHeader("X-JSON", '('.$output.')');

  return sfView::HEADER_ONLY;
}
```

这跳过了模板和布局，响应可以立即发送。由于它仅包含标头，因此更轻量，传输给用户所需的时间更少。

第 6 章解释了另一种跳过模板的方法，即直接从操作返回内容文本。这打破了 MVC 分离，但可以大大提高操作的响应速度。请参阅清单 18-13 以查看示例。

清单 18-13 - 直接返回内容文本的操作示例

```
public function executeFastAction()
{
    return $this->renderText("<html><body>Hello, World!</body></html>");
}
```

## 调整缓存

第 12 章已经描述了如何缓存响应的部分内容或全部内容。响应缓存会带来重大的性能改进，应该是你首要考虑的优化事项之一。如果你想充分利用缓存系统，请继续阅读，因为本节揭示了一些你可能没有想到的技巧。

### 清除缓存的选择性部分

在应用程序开发过程中，你需要在各种情况下清除缓存：

- 当你创建新类时：将类添加到自动加载目录（项目 lib/ 文件夹之一）不足以让 symfony 在非开发环境中自动找到它。你必须清除自动加载配置缓存，以便 symfony 再次浏览 autoload.yml 文件的所有目录，并引用可自动加载类的位置（包括新类）。

- 当你在生产环境中更改配置时：配置仅在生产环境的第一个请求期间解析。后续请求使用缓存版本。因此，在生产环境中（或任何关闭调试的环境中）更改配置不会生效，直到你清除文件的缓存版本。

- 当你在启用模板缓存的环境中修改模板时：在生产环境中，有效的缓存模板始终用于替代现有模板，因此模板更改会被忽略，直到模板缓存被清除或过期。

- 当你使用 project:deploy 命令更新应用程序时：这种情况通常涵盖上述三种修改。

清除整个缓存的问题是，下一个请求处理时间会相当长，因为需要重新生成配置缓存。此外，未修改的模板也会从缓存中清除，失去之前请求的好处。

这意味着最好只清除真正需要重新生成的缓存文件。使用 cache:clear 任务的选项来定义要清除的缓存文件子集，如清单 18-14 所示。

清单 18-14 - 仅清除缓存的选择性部分

```
// Clear only the cache of the frontend application
$ php symfony cache:clear frontend

// Clear only the HTML cache of the frontend application
$ php symfony cache:clear frontend template
```

