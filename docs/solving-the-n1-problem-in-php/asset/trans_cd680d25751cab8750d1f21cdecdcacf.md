

# 8. 常见问题

## 我可以将单次查询（Single-Query）与查询合并（Query-and-Stitch）结合吗？

在某些情况下，将单次查询方法与查询合并方法结合可能是合理的。你可以用单次查询处理所有的“一对一”关系，然后使用查询合并方法处理所有的“一对多”关系。这样做通过将所有“一对一”查询合并到根查询中，减少了总的查询次数。在我们之前的示例中，这意味着三个 Post（文章）、Author（作者）和 Summary（摘要）的查询将合并为一个查询，只剩下 Comment（评论）和 Tag（标签）查询。

在性能极其重要的情况下，我支持结合这些方法。但我推测，通过消除代码库中的 N+1 问题，我们大幅提升了性能，以至于更大的担忧变成了一致性问题。混合使用方法，或者在某些情况下使用一种方法而在其他情况下使用另一种方法，意味着代码库的不一致。这反过来会降低开发者的理解能力并误导他们的预期。

因此，我倾向于在整个代码库中使用查询合并方法，即使这意味着在某些地方增加了一两次额外的查询。当然，一旦这些额外的查询从想象中或预测的性能担忧变为实际且可衡量的性能问题，我很乐意使用单次查询解决方案来解决这些问题。

一如既往，你自己的需求和偏好应该是使用何种方法以及何时使用的最终决定因素。

## 我可以使用 Select 代替 IN() 运算符吗？

在查询合并解决方案中，我们创建了一个带引号的、逗号分隔的值列表，指示要从数据库检索的标识或外键。然后，我们使用 `IN()` 运算符配合值列表来获取构建关联所需的行行。

虽然很容易想象出 `IN()` 运算符存在的问题，但我自己很少遇到 `IN()` 实际上成为问题的情况。某些数据库可能会限制 `IN()` 元素的数量或长度，或者限制整个查询字符串的长度，但在实践中，我发现这些限制并不重要。只要 `IN()` 条件引用的是索引列，我就发现很少或没有性能相关的问题。

然而，在某些情况下，`IN()` 运算符仍然是一个可衡量的性能问题。你只有通过对较慢的查询运行 `EXPLAIN`（或等效命令），并发现查询计划对 `IN()` 并不是最优的，才能判断这一点。

在这种情况下，用对子查询的 `JOIN` 替换 `IN()`，以提供检索所需的相关值。例如，获取 Post 实体的根集合和关联的 Comment 实体集合可能看起来如下所示：

```php
<?php
// 获取按顺序索引的 post 实体
$stmt = 'SELECT *
FROM posts
ORDER BY datetime DESC
LIMIT 10';
$sth = $pdo->prepare($stmt);
$sth->execute();
$post_entities = $sth->fetchAll(PDO::FETCH_CLASS, 'Post');

// 获取所有文章的所有评论
$stm = "SELECT *
FROM comments
JOIN (
SELECT post_id
FROM posts
ORDER BY datetime DESC
LIMIT 10
) AS posts ON posts.post_id = comments.post_id";
$sth = $pdo->prepare($stmt);
$sth->execute();
$comment_entities = $sth->fetchAll(PDO::FETCH_CLASS, 'Comment');
?>
```

在这种情况下，我们删除了 `WHERE ... IN()` 和 `post_id` 值的字面量列表。然后我们用一个对子查询的 `JOIN` 来替换它，该子查询与我们创建根集合时使用的 `SELECT` 相同（除了子查询仅返回主键外）。

如果我们真的想得聪明一点，可以创建一个包含根集合中 `post_id` 值的临时表。然后我们可以 `JOIN` 临时表而不是子查询。当我们在事务中多次使用同一个子查询时，这可能有用。

## 我应该在查询合并时使用事务（Transaction）吗？

通过查询合并，我们对数据库进行了多次调用。然而，数据库中的数据在这些调用之间可能会发生。例如，假设我们获取了 Post 集合的行，紧接着其中一个文章的行值被更改了（例如 `author_id`）。之后任何 `JOIN posts` 或以其他方式向可用数据提供相同 `author_id` 列表的查询，都可能不一致并导致意外结果。

出于这个原因，在某些情况下在事务内部执行查询合并可能是明智的。这样做有助于在将结果合并的多个查询之间保持一致的状态。

事务有不同级别的隔离性，不同的数据库有它们的默认设置。我建议使用 `READ COMMITTED` 级别，如果你发现由于隔离不足导致错误或不一致，则升级到 `REPEATABLE READ`。

> 事务和事务隔离涉及与表锁和行锁相关的性能考虑。务必咨询你的数据库文档以获取特定细节。你可能需要在一致性和性能之间进行权衡。

例如，使用 PDO 配合 MySQL 或 PostgreSQL，代码可能如下：

```php
<?php
// 开启事务
$pdo->exec('SET TRANSACTION ISOLATION LEVEL REPEATABLE READ');
$pdo->beginTransaction();
// 选择所有数据 ...
// 结束事务
$pdo->commit();
// 将数据合并为实体
?>
```

注意，我们在一个代码块中完成所有数据选择，然后结束事务，在此之后才合并我们的实体。这是因为我们希望在事务中花费的时间尽可能短。通常情况下，事务越长意味着性能越慢。

> http://en.wikipedia.org/wiki/Isolation_(database_systems)

## 我可以直接用 ORM 吗？

到这里，一些读者在考虑引入诸如 Doctrine、Propel 或 PHP 中提供的其他 ORM 系统是否是明智的。毕竟，ORM 本身就使用了单次查询和查询合并技术，因此使用 ORM 可以自动处理掉我们在解决 N+1 问题时需要自己编写的大量代码。

我对 ORM 态度复杂。在与 Jeff Moore一起为 Solar 开发了一套健壮的 ORM 系统后，我完全熟悉使用它们的权衡。它们在应用程序开发的早期通常是巨大的助力。但在边缘情况下，它们会被揭示为不透明、低效或不可预测，因此需要你对它们在不同情况下的特殊性有良好的了解。

ORM 几乎总是要求你学习特殊的惯用法来构建查询。这些惯用法可能与某种类 SQL 的语言绑定，也可能与各种类中的特定一组方法和信息属性绑定，或者二者兼有。我觉得这种修改后的工作方式为将 ORM 引入现有应用程序带来了显著的阻碍。即使你的数据库逻辑拆分得很好，你也必须重写每一个数据库交互以符合 ORM 的查询惯用法。这需要花费时间和精力的，而这些精力可能花在其他地方更好。

即使引入了 ORM，你可能无法完全免受 N+1 问题的影响。如果 ORM 在循环中懒加载记录，而你又没有预加载所需的数据，情况尤为如此。你需要关注 ORM 内部是如何工作的，以避免最终陷入你正试图解决的问题中。

总的来说，我认为 ORM 的权衡高度取决于上下文。在不知道你的具体情况的情况下，我无法提供提供通用的建议，除非说一句“谨慎行”。

http://solarphp.com
http://www.procata.com

# 附录

## SQL Schema

以下 SQLite 表表示了一个简单的博客应用程序的数据结构。
表以复数实体命名：posts、comments 等。每个主键列都是自动递增的，并以单数实体命名并带有 `*_id`：post_id、comment_id 等。

`summaries` 表没有 `summary_id` 列，因为每一行与 posts 是直接一对一的。`posts_tags` 表是一张关联表，映射 posts 和 tags 之间的多多关系。

这些表被剥离以显示数据的本质，不应作为真实应用程序的基础。

```
CREATE TABLE authors (
    author_id INTEGER PRIMARY KEY AUTOINCREMENT,
    name VARCHAR(255)
);
CREATE TABLE comments (
    comment_id INTEGER PRIMARY KEY AUTOINCREMENT,
    post_id INTEGER,
    datetime DATETIME,
    name VARCHAR(255),
    email VARCHAR(255),
    website VARCHAR(255),
    body TEXT
);
CREATE TABLE posts (
    post_id INTEGER PRIMARY KEY AUTOINCREMENT,
    author_id INTEGER,
    datetime DATETIME,
    title VARCHAR(255),
    body TEXT
);
CREATE TABLE posts_tags (
```

