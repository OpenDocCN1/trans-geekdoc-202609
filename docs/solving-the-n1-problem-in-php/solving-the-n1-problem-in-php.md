
# PHP 中的 N+1 问题求解

## 在 Twitter 上推文这本书！

请通过在 Twitter 上传播这本书来帮助 Paul M. Jones！

本书建议的标签（hashtag）为 `#sn1php`。

点击此链接在 Twitter 上搜索该标签，了解其他人对这本书的评价：

https://twitter.com/search?q=#sn1php

## Paul M. Jones 的其他著作

# 1. 引言

## 缓慢的报告脚本

该网页加载需要三个小时。请仔细体会一下：三个小时。支持页面的后台代码是一个用 PHP 编写的报告脚本，试图从 200 万行数据库记录中构建 40,000 个实体对象。有时页面根本无法加载。至少客户端可以知道它什么时候失败了，因为浏览器窗口会弹出一个巨大的、丑陋的错误。不幸的是，那也发生在三小时左右。客户理所地感到非常沮丧。

我被分配去排查这个问题。事实证明，原因并不是数据库没有优化。不是返回的行数太多。甚至不是构建的对象数量。

不，原因在于报告脚本发出的查询数量。高频的查询反过来是脚本组装实体对象的方式导致的。我说“高频”时，指的是二十万万零一次查询。这 200,000 多次查询用于构建每个根实体以及其五个关联集合和实体。难怪脚本要花三个小时才完成！

在发现这一点后，我能够应用书中介绍的“查询及缝合”（query-and-stitch）技术来重构实体对象的组装方式。在经过几天的重构后，我成功将加载时间从 3 多小时缩短到不到 6 分钟。这是 30 倍的提升，而且按照典型标准来说，尽管依然很快，但对客户来说要接受得多。（随后的重构进一步缩短了加载时间。）

导致这个“缓慢的报告脚本”性能糟糕的原因有一个名字：N+1 问题。这个问题有各种别名，例如“1+N 问题”、“N+1 查询”、“SELECT N+1”等，但它们指的都是同一件事。

## 引言

虽然我在《PHP 遗留应用现代化》（Modernizing Legacy Applications in PHP）¹中多次提到 N+1 问题，但我并没有直接给出解决方案。本书弥补了这一缺陷。在这里，我们将讨论 N+1 问题的细节：

- 什么是 N+1 问题，
- 如何在你的应用程序中诊断并发现问题，
- 为什么会出现这个问题，以及
- 如何在你的代码库中解决这个问题。

## 示例应用程序

虽然我无法展示“缓慢报告脚本”本身来进行对比检查，但我可以采取次优方案，展示一个通用示例。在书中，我们将使用来自简易博客系统的假设代码作为主体。在此过程中，我们将使用附录中描述的 SQL 和 PHP 结构。

这是一个遗留应用示例，因此没有使用 ORM。（不同的 ORM 实现有自己的 N+1 缓解策略，我们在这里无法讨论。）

在没有 ORM 的情况下，这个假设的应用使用 `PDO`² 进行数据库抽象。并不是所有的遗留代码都使用 `PDO`，但关于 N+1 的原理（包括问题和解决方案）适用于所有的数据库连接库。这些包括 `mysqli`³、`mysqli*`，以及我们自己的数据库抽象层。

在获取查询时，我们的应用程序尽可能使用 `PDO::FETCH_CLASS`* 模式。这导致 `PDO` 返回一个指定实体类的数组实例，每个实例的属性已填充了来自该行的数据。在其他系统中，你可能会单独从数据库查询创建类；我们使用 `FETCH_CLASS` 主要是为了减少示例代码量。（实体类本身是带有公共属性的普通 PHP 对象）

最后，简易代码库使用普通的 PHP 数组处理实体集合。更复杂的系统可能会使用通用类属性，但关于集合的 N+1 原理仍然是一致的。

> ¹https://github.com/mlphp
> ²http://php.net/PDO
> ³http://php.net/mysql
> ⁴http://php.net/mysqli
> ⁵http://php.net/manual/pdostatement.fetch.php

## 定义 N+1 问题

### 通过示例说明问题

通过示例来描述 N+1 问题是最简单的。假设我们的简易博客应用需要显示一个包含 10 篇最新博客文章的页面，以及每篇文章文章的所有评论。

首先，应用程序以数组形式获取 `Post` 实体的根集合：

```php
<?php
$stm = 'SELECT *
FROM posts
ORDER BY datetime DESC
LIMIT 10';
$sth = $pdo->prepare($stm);
$sth->execute();
$posts = $sth->fetchAll(PDO::FETCH_CLASS, 'Post');
?>
```

到目前为止良好：应用程序已执行了一个查询来构建 `Post` 实体的根集合。接下来，应用程序收集每个实体上的 `Comment` 实体：

```php
<?php
// 准备一个语句来选择评论
$stm = 'SELECT *
FROM comments
WHERE post_id = :post_id';
$sth = $pdo->prepare($stm);
foreach ($posts as $post) {
  $sth->execute(array('post_id' => $post->post_id));
  $post->comments = $sth->fetchAll(PDO::FETCH_CLASS, 'Comment');
}
?>
```

应用程序为每个文章执行了十次查询。通过此，我们到达了 N+1 问题的核心。

### 问题定义

N+1 问题表现为如下：

对于根集合中的每个实体，应用程序都会执行一个额外的查询来获取关联。

在上面的示例中，应用程序总共执行了 11 次查询来构建 10 个实体及其 `Comment` 集合：

- 一个获取根集合实体的查询（这是 N+1 中的 "1"）
- 为根集合中的每个实体执行的十次获取的查询（这是 N+1 中的 "N"，其中 "N" 等于根集合中的实体数量）。

### 性能影响

N+1 有两个性能影响：

1. 查询数量随着根集合中实体数量的增加而增加。
2. 查询数量随着每个根实体所需的关联数量而增加。

这意味着随着根实体和关联数量的线性增加，查询数量会按这两个者的倍数增长。每次增加的查询都会降低应用程序的响应速度。

# 3. 诊断 N+1 问题

有两种方法可以诊断代码库中的 N+1 问题。两种方法都需要调查，并且不容易自动化。

## 代码库检查

首先，我们可以手动检查代码库，寻找循环内部执行的查询。这听起来可能很难，因为循环与查询可能隔得很远。例如，这个循环看起来大部分无害：

```php
<?php
foreach ($posts as $post) {
    $helper->doSomething($post);
}
?>
```

进一步检查，如果 `doSomething()` 方法（或它调用的任何方法）向数据库发出查询，那么我们就遇到了 N+1 问题。由于这样，可能无法立即看出问题在代码库中的来源。

> 真正棘手的是代码库调用了数据库的存储过程，而存储过程本身是 N+1 问题的根源。在这种情况下，我们还需要审查存储过程代码。

## 日志/分析检查

或者，我们可以从问题的另一个端开始，审查数据库查询日志（或应用程序级查询分析器）以寻找查询中的模式。在对应用程序和底层数据有一定了解的情况下，这更容易实现，但在简单情况下，即使没有详细的应用知识，也应该是显而易见的。模式识别是这种方法成功的关键。

### N 次评论查询和 1 次帖子查询

```
SELECT * FROM posts ORDER BY date DESC LIMIT 10;
SELECT * FROM comments WHERE comments.post_id = 936;
SELECT * FROM comments WHERE comments.post_id = 935;
SELECT * FROM comments WHERE comments.post_id = 934;
SELECT * FROM comments WHERE comments.post_id = 933;
SELECT * FROM comments WHERE comments.post_id = 932;
SELECT * FROM comments WHERE comments.post_id = 931;
SELECT * FROM comments WHERE comments.post_id = 929;
SELECT * FROM comments WHERE comments.post_id = 927;
```

如果应用程序检索两个或多个关系的数据，这种模式可能没那么明显。在“慢速报告脚本”的情况下，应用程序为每个根实体检索了五个关联实体，日志看起来如下……

### 按根实体批处理的查询

```
SELECT * FROM root_table WHERE;
SELECT * FROM rel1 WHERE rel1.root_id = 10324 ...;
SELECT * FROM rel2 WHERE rel2.root_id = 10324 ...;
SELECT * FROM rel3 WHERE rel3.root_id = 10324 ...;
SELECT * FROM rel4 WHERE rel4.root_id = 10324 ...;
SELECT * FROM rel5 WHERE rel5.root_id = 10324 ...;
SELECT * FROM rel1 WHERE rel1.root_id = 10325 ...;
SELECT * FROM rel2 WHERE rel2.root_id = 10325 ...;
SELECT * FROM rel3 WHERE rel3.root_id = 10325 ...;
SELECT * FROM rel4 WHERE rel4.root_id = 10325 ...;
SELECT * FROM rel5 WHERE rel5.root_id = 10325 ...;
SELECT * FROM rel1 WHERE rel1.root_id = 10326 ...;
SELECT * FROM rel2 WHERE rel2.root_id = 10326 ...;
SELECT * FROM rel3 WHERE rel3.root_id = 10326 ...;
SELECT * FROM rel4 WHERE rel4.root_id = 10326 ...;
SELECT * FROM rel5 WHERE rel5.root_id = 10326 ...;
```

……依此类，每个根实体都有 5 次相关查询。如你所见，该模式以五行为一组进行重复，每行对应一个 `rel1` 到 `rel5`。

### 按关系批处理的查询

```
SELECT * FROM root_table WHERE ... ;
SELECT * FROM rel1.root_id = 10324 ...;
SELECT * FROM rel1.root_id = 10325 ...;
SELECT * FROM rel1.root_id = 10326 ...;

SELECT * FROM rel2.root_id = 10324 ...;
SELECT * FROM rel2.root_id = 10325 ...;
SELECT * FROM rel2.root_id = 10326 ...;

SELECT * FROM rel3.root_id = 10324 ...;
SELECT * FROM rel3.root_id = 10325 ...;
SELECT * FROM rel3.root_id = 10326 ...;

SELECT * FROM rel4.root_id = 10324 ...;
SELECT * FROM rel4.root_id = 10325 ...;
SELECT * FROM rel4.root_id = 10326 ...;

SELECT * FROM rel4.root_id = 10324 ...;
SELECT * FROM rel4.root_id = 10325 ...;
SELECT * FROM rel4.root_id = 10326 ...;

SELECT * FROM rel5.root_id = 10324 ...;
SELECT * FROM rel5.root_id = 10325 ...;
SELECT * FROM rel5.root_id = 10326 ...
```

遗憾的是，即使我们识别出了模式，也很难发现代码库的哪部分导致了问题。我们需要在代码库中搜索与日志中显示的 SQL 字符串类似的字符串。

> 如果你的数据库抽象层具有一个保留回溯轨迹的查询分析器，这样你就能知道查询的源头，那就再好不过了（Aura.Sql¹ 就是这样一个包）。即使没有，你也可以通过在你选择的某一点启动分析器，然后在稍后的一点停止分析器（并记录或转储其输出）来缩小可能的位置。

¹https://github.com/auraph/Aura.Sql

## 更容易的查询检查

如果我们有大量非平凡的根实体（超过 100 个左右），那么审查查询日志或配置文件将是一项繁重的工作。如果可能，请尝试将数据集减少到更易于管理的程度，以便日志相对较短。至少，减少数据集将缩短最初生成日志所需的时间。

在“慢速报告脚本”的情况下，运行脚本并获取日志需要三个小时，而日志本身将会有数十万行。这将导致非常缓慢的“修改-测试”迭代周期。意识到这一点后，我将数据集从 200 万行减少到仅 2000 行；结果是脚本只需要构建 40 个根实体而不是 40,000 个。这样做的好处是缩短了脚本运行和生成查询日志的时间，同时也减少了日志中的行数。这意味着只需要查看 201 行相关的日志，而不是 200,001 行。

# 4. 为什么会出现 N+1 问题？

为什么会出现 N+1 问题呢？在修复了几个代码库中的问题并与这些代码库的一些原始开发者交流后，我得出的结论：问题源于一种 **CRUD 式**的开发者思维。

## CRUD 是问题所在

我们都知道 CRUD 这个缩写：创建（Create）、读取（Read）、更新（Update）、删除（Delete）。这里的关键在于，CRUD 主要应用于单个实体：检索单个实体、编辑和删除单个实体。

这种一次处理一个的方法对于大多数数据库交互都是很有用的。它导致了如 `RowDataGateway` 和 `ActiveRecord`? 等模式的使用。在这些模式中，重点在于如何构建单个实体（通常带有它的关联关系）。

对单个实体的关注是 N+1 问题的根源。在这种思维下，开发者将构建多个实体的集合视为构建实体的变体。开发者只是对集合中的每个实体循环一次单实体的创建过程。实体集合本质上是事后考虑的。因为它们不是主要关注点，开发者自然会倾向于使用“循环内查询”，这正是 N+1 问题的标志。

## B 是答案

那么，解决 N+1 问题的关键在于开发者思维的转变。我们不应该以 CRUD 的方式思考，而应该以 BREAD 的：浏览（Browse）、读取（Read）、编辑（Edit）、添加（Add）和删除（Delete）。

虽然“R-E-A-D”部分直接对应“C-R-U-D”，但请注意，第一个字母代表的是实体的集合。

通过首先考虑实体的集合而不是只考虑单个实体，开发者开始考虑不同的方法。如 `TableGateway`³、`Table`⁴ 甚至 `DataMapper`⁵ 等模式将集合视为一等公民来处理。在将实体集合视为一等关注后，构建单个实体（即只包含单个实体的实体）就变得相对容易。

如果我们能高效地构建实体集合，那么构建单个实体也是高效的。反之则并非如此，正如我们在示例中所看到的那样。

³https://martinfowler.com/eaa/eaaCatalog/tableDataGateway.html
⁴https://martinfowler.com/eaa/eaaCatalog/tableModule.html
⁵https://martinfowler.com/eaa/eaaCatalog/dataMapper.html

# 5. 使用单个查询解决 N+1

解决 N+1 问题的一种方法是在一次查询中检索所有根实体的数据以及所有关联的数据：

- 发处一个查询，将所有必要的表连接到单个结果集中。
- 在 PHP 循环中将每行结果转换为实体对象。

这种方法在直觉上很有吸引力，因为无论根实体或关联的数量有多少，它只产生一个查询。虽然它对于“一对”关系效果良好，但通常对于“一对多”关系并不适用。尽管如此，为了完整性起见，它仍然值得讨论。

## 处理“多对一”关系

假设我们的博客应用程序需要展示10 篇最新的博客帖子及其作者。在 N+1 的情况下，相关代码可能如下。

### 原始的 N+1 代码

```php
<?php
// 获取最新的帖子
$stmt = 'SELECT *
FROM posts
ORDER BY datetime DESC
LIMIT 10';
$stmt = $pdo->prepare($stmt);
$stmt->execute();
$posts = $stmt->fetchAll(PDO::FETCH_CLASS, 'Post');

// 获取每个帖子的作者
$stmt = 'SELECT *
FROM authors
WHERE author_id = :author_id'
$stmt = $pdo->prepare($stmt);
foreach ($posts as $post) {
    $stmt->execute(array('author_id' => $post->author_id));
    $post->author = $stmt->fetchObject('Author');
}
?>
```

与任何 N+1 情况一样，这会为根实体集合发布 1 次查询，然后为每个关联发布 1 次查询。在这种情况下，如果有 10 个 `Post` 实体，就意味着总共会有 11 次查询。



> 作为一个额外的问题，请注意该代码为每个 `Post` 创建了一个新的 `Author` 实体。如果所有 `Post` 实体都属于同一个 `Author`，意味着存在十份 `Author` 数据的副本，且其中任何一个都不是权威的。对一个 `Post` 的 `Author` 的更改不会反映在另一个帖子上本应是相同的 `Author` 上。我们将在下文的单查询解决方案中解决这个问题。

## 转换为单查询

由于这是一个“多对一”查询（每个 `Post` 仅属于一个 `Author`），我们可以考虑使用单查询方法来消除 N+1 问题。首先，我们获取包含所有 `Post` 和 `Author` 数据的一行记录：

```php
<?php
// 获取带有作者的最新帖子
$stmt = 'SELECT
    posts.post_id AS post__post_id,
    posts.author_id AS post__author_id,
    posts.datetime AS post__datetime,
    posts.title AS post__title,
    posts.body AS post__body,
    authors.author_id AS author__author_id,
    authors.name AS author__name
FROM posts
JOIN authors ON authors.author_id = posts.author_id
ORDER BY datetime DESC
LIMIT 10';
$stmt = $pdo->prepare($stmt);
$stmt->execute();
$rows = $stmt->fetchAll(PDO::FETCH_ASSOC);
?>
```

关于这段代码的几点注意事项：

- 我们不再使用 `SELECT *`。我们必须处理具有相同列名（在本例中为 `author_id`）的表之间的命名冲突，同时确保我们获取了构建相关实体所需的所有数据。在这里，我们通过为每个列名加上带有目标实体名称的别缀，并使用两个下划线作为分隔符来实现。
- 我们为“对一”关系添加了 `JOIN` 子句，在本例中连接到作者表。
- 我们使用 `PDO::FETCH_ASSOC` 获取模式而不是 `PDO::FETCH_CLASS`。这返回的是一个数组数组，而不是对象实例数组。因为每行代表了两个实体的数据（一个 `Post` 和一个 `Author`），所以没有一个类适用于该行数据。因此，我们必须从行数据自己创建对象实例。

数据库返回的结果集看起来如下：

### 带有 Post 和作者的结果行

| post_id | title | author_id | name |
| --- | --- | --- | --- |
| 1 | Post #1 | 1 | Author #1 |
| 2 | Post #2 | 2 | Author #2 |
| 3 | Post #3 | 2 | Author #2 |
| 4 | Post #4 | 1 | Author #1 |
| 5 | Post #5 | 2 | Author #2 |
| 6 | Post #6 | 1 | Author #1 |
| 7 | Post #7 | 1 | Author #1 |
| 8 | Post #8 | 2 | Author #2 |
| 9 | Post #9 | 2 | Author #2 |
| 10 | Post #10 | 1 | Author #1 |

现在我们有了结果，通过循环来创建我们的实体对象。

```php
<?php
$authors = array();
$posts = array();
foreach ($rows as $row) {

    // 创建 post 实体
    $post = new Post();
    $post->post_id = $row['post_post_id'];
    $post->author_id = $row['post_author_id'];
    $post->datetime = $row['post_datetime'];
    $post->title = $row['post_title'];
    $post->body = $row['post_body'];

    // 作者是否存在？
    $author_id = (isset($authors[$author_id])) {
        // 使用已有的作者实体
        $author = $authors[$author_id];
    } else {
        // 创建并保留新的作者实体
        $author = new Author();
```

```php
$author->author_id = $author_id;
$author->name = $row['__name__'];
$authors[$author_id] = $author;
}

// 关联作者实体
$post->author = $author;

// 在集合中保留 post
$posts[] = $post;
```
```

关于对象创建代码的说明：

- 这种方法显然比允许 `PDO` 为我们创建实体实例的代码行数要多。在一种不那么简单的情况下，实体构造函数可能会接收一个数据数组并填充自己，或者会有某种类型的实体工厂或构建器来处理这些工作。无论如何，这种方法的性能保证优于发布 11 次查询来创建 `Post` 实体及其关联的 `Author` 实体。
- 该解决方案在 `Post` 实体之间使用了唯一的 `Author` 关联，与 N+1 代码不同。虽然不是严格的 N+1 问题，但它解决了多个对象表示同一个作者的问题。

至此，解决方案就完成了。添加“一对一”关系来构建关联实体同样简单。我们会添加另一个 `JOIN` 子句，相应地为所选列名设置别名，然后在实体创建流中从行中提取它们，在此过程中跟踪唯一的实体。

## 处理“一对一”关系

在单查询方法下，这些关系非常直观。我们只需要一个普通的 `JOIN`，不需要对唯一实体进行任何跟踪。

假设博客应用程序需要展示 `Post` 实体列表，以及跟踪视图次数和评论数量的 `Summary` 数据。检索和创建代码看起来如下所示：

```php
<?php
// 获取带有作者的最新帖子
$stm = 'SELECT
    posts.post_id AS post__post_id,
    posts.author_id AS post__author_id,
    posts.datetime AS post__datetime,
    posts.title AS post__title,
    posts.body AS post__body,
    summaries.post_id AS summary__post_id,
    summaries.view_count AS summary__view_count,
    summaries.comment_count AS summary__comment_count
FROM posts
JOIN summaries ON posts.post_id = posts.post_id
ORDER BY datetime DESC
LIMIT 10';
$sth = $pdo->prepare($stm);
$sth->execute();
$rows = $sth->fetchAll(PDO::FETCH_ASSOC);

// 创建带有 summaries 的 posts
$posts = array();
foreach ($rows as $row) {
    // 创建 post 实体
    $post = new Post();
    $post->post_id = $row['post_post_id'];
    $post->author_id = $row['post_author_id'];
    $post->datetime = $row['post_datetime'];
    $post->title = $row['post_title'];
    $post->body = $row['post_body'];

    // 关联 summary
    $post->summary = new Summary();
    $post->summary->post_id = $row['summary__post_id'];
    $post->summary->view_count = $row['summary__view_count'];
    $post->summary->comment_count = $row['summary__comment_count'];

    // 在集合中保留 post
    $posts[] = $post;
}
?>
```

我们可以看到，这很简单。结合“多对一”和“一对一”，单查询解决方案的主要优势在于我们能够通过一次查询获取根实体及其关联实体的数据。合并后的检索代码看起来如下：

```php
<?php
$stm = 'SELECT
    posts.post_id AS post_id,
    posts.author_id AS author_id,
    posts.datetime AS post__datetime,
    posts.title AS post__title,
    posts.body AS post__body,
    authors.author_id AS author__author_id,
    authors.name AS author__name,
    summaries.post_id AS summary__post_id,
    summaries.view_count AS summary__view_count,
    summaries.comment_count AS summary__comment_count
FROM posts
JOIN authors ON authors.author_id = posts.author_id
JOIN summaries ON summaries.post_id = posts.post_id
ORDER BY datetime
LIMIT 10';
$stm = $pdo->prepare($stm);
$stm->execute();
$rows = $stm->fetchAll(PDO::FETCH_ASSOC);
```

当我们获取结果时，通过构建构建逻辑来处理每一行：

```php
<?php
$authors = array();
$posts = array();
foreach ($rows as $row) {

    // 创建 post 实体
    $post = new Post();
    $post->post_id = $row['post_id'];
    $post->author_id = $row['author_id'];
    $post->datetime = $row['post__datetime'];
    $post->title = $row['post__title'];
    $post->body = $row['post__body'];

    // 作者是否存在？
    $author_id = $row['author__author_id'];
    if (isset($authors[$author_id])) {
        // 使用已有的作者实体
        $author = $authors[$author_id];
    } else {
        // 创建并保留新的作者实体
        $author = new Author();
        $author->id = $author_id;
        $author->name = $row['author__name'];
        $authors[$author_id] = $author;
    }

    // 关联作者实体
    $post->author = $author;

    // 关联 summary
    $post->summary = new Summary();
    $post->summary->post_id = $row['summary__post_id'];
    $post->summary->view_count = $row['summary__view_count'];
    $post->summary->comment_count = $row['summary__comment_count'];

    // 在集合中保留 post
    $posts[] = $post;
}
?>
```

## 处理“一对多”关系

遗憾的是，单查询解决方案对于大多数“一对多”和“多对多”情况几乎完全是不适用的。让我们来看看之前的“帖子与评论”示例，找出为什么如此。我们将首先获取所有的 `Post` 实体（而不仅仅是 10 个）以及它们的所有评论：

```php
<?php
$stmt = 'SELECT
    posts.post_id AS post__post_id,
    posts.author_id AS post__author_id,
    posts.datetime AS post__datetime,
    posts.title AS post__title,
    posts.body AS post__body,
    comments.id AS comment__comment_id,
    comments.name AS comment__name,
    comments.email AS comment__email,
    comments.website AS comment__website,
    comments.body AS comment__body
FROM posts
LEFT JOIN comments ON comments.post_id = posts.post_id';
$stmt = $pdo->prepare($stmt);
$stmt->execute();
$rows = $stmt->fetchAll(PDO::FETCH_ASSOC);
?>
```

关于这段代码需要注意的几点：

- 对于“一对一”，我们不再使用 `SELECT *`；仍然需要对相似的列名进行解构。
- 对于“一对多”关系，我们添加了 `LEFT JOIN` 子句，在本例中是连接 `comments` 表。（我们使用 `LEFT JOIN` 是以防某些帖子没有评论）。
- 同样对于“一对一”，我们使用 `PDO::FETCH_ASSOC` 模式而不是 `PDO::FETCH_CLASS`，并且我们必须自己创建对象实例。

结果集将会非常大，并且包含大量重复内容。如果系统中有 50 个 `Post` 实体，每个 `Post` 关联了 5 个 `Comment` 实体，这意味着结果集中将有 250 行。它看起来像这样：

### 使用单查询解决 N+1 问题

#### 带有评论和重复帖子的结果行

| post_id | title | comment_id | body |
|---|---|---|---|
| 1 | Post #1 | 1 | Comment #1 on post #1 |
| 1 | Post #1 | 2 | Comment #2 on post #1 |
| 1 | Post #1 | 3 | Comment #3 on post #1 |
| 1 | Post #1 | 4 | Comment #4 on post #1 |
| 1 | Post #1 | 5 | Comment #5 on post #1 |
| 2 | Post #2 | 6 | Comment #1 on post #2 |
| 2 | Post #2 | 7 | Comment #2 on post #2 |
| 2 | Post #2 | 8 | Comment #3 on post #2 |
| 2 | Post #2 | 9 | Comment #4 on post #2 |
| 2 | Post #2 | 10 | Comment #5 on post #2 |
| 10 | Post #10 | 246 | Comment #1 on post #10 |
| 10 | Post #10 | 247 | Comment #2 on post #10 |
| 10 | Post #10 | 248 | Comment #3 on post #10 |
| 10 | Post #10 | 249 | Comment #4 on post #10 |
| 10 | Post #10 | 250 | Comment #5 on post #10 |

由于结果集中的这些重复，我们需要遍历结果集并提取出不同的 `Posts`。同时，我们需要保留与每个 `Post` 关联的多个 `Comment` 实体。实现此操作的代码如下：



在循环结束时，我们将拥有一个包含所有 Post 实体及其所有关联 Comment 实体的 `$posts` 集合。

## 单查询在处理“一对多”关系时失效

虽然单查询解决方案看起来可能是解决应用于“一对多”关系的 N+1 问题的办法，但它存在一些主要的缺点。

首先，没有合理的方法可以添加按我们所需方式工作的 `LIMIT` 子句。这是因为 `LIMIT` 应用于返回的行数，而不是所代表的实体数量。这种区别虽然微妙但非常重要。

如果我们在上面的查询中添加 `LIMIT 10`，我们实际上会得到 10 行。但这些行并不一定代表 10 个 `Post` 实体（至少除非每个 `Post` 只有一个评论）。即使是对 `FROM` 和 `JOIN` 子句进行子查询变体，并在子查询中使用 `LIMIT` 子句，在“一对多”关系中也无法按照我们想要的方式工作。

事实证明，在单查询解决方案中强制执行“一对多”关系的 `LIMIT` 的唯一方法是在 PHP 循环代码中计数实体。可以说，这是一种次优方法。

其次，如果有两个或多个“一对多”关系，构建查询并解析结果集以创建实体将变得困难得多。重复问题会呈指数级变得棘手，我们需要跟踪每个关联实体的存在。此外，结果集的大小也会成为问题，无论是列数（因为每行都包含每个实体的所有列）还是行数（因为每行都会重复每个实体的每个数据元素，乘以关系的数量）。

总体而言，单查询解决方案可能适用于“一对一”关系，但完全不适用于任何数量的“一对多”关系。

# 6. 使用 Query-And-Stitch 解决 N+1

单查询解决方案的替代方案是易于实施的，并且在任何数量的关联中更具可扩展性。这种替代方案被称为“查询与缝合”（query-and-stitch）。

查询与缝合的方法如下：

- 1. 为根实体集合发布一次查询。
- 2. 为每个关联额外发布一次查询，以获取所有根实体的所有关联实体。
- 3. 使用 PHP 循环将关联实体缝合到根实体中。

## 查询与缝合中的权衡

这里的关键在于我们为每个关系发布一次额外查询，而不是每个根实体发布一次。因此，查询数量的增加是线性的而不是指数级的。

例如，如果根集合中有 10 个实体和 2 个关联：

- 在 N+1 下，我们将发布 21 次查询（根集合 1 次，每个关联 10 次）。
- 使用单查询解决方案，我们可能通过一次查询检索数据，但处理结果集的成本太高。
- 使用查询与缝合，我们总共发布 3 次查询（根集合 1 次，每个关联 1 次）。添加第三个关联将产生 4 次查询。

查询与缝合方法代表了 N+1 和单查询之间的有效权衡，适用于“一对一”和“一对多”关系。

## 处理“一对多”关系

以下是使用查询与缝合技术重写的之前的帖子-评论示例。获取主 `Post` 实体的查询是相同的，但请注意我们随后创建了一个基于 `post_id` 的根集合（即而不是顺序键）。

```php
<?php

// 获取顺序索引的实体

$stmt = 'SELECT

FROM posts

ORDER BY datetime DESC

LIMIT 10';

$stmt = $pdo->prepare($stmt);

$stmt->execute();

$post_entities = $stmt->fetchAll(PDO::FETCH_CLASS, 'Post');

// 根据主键值重索引实体

$posts = array();

foreach ($post_entities as $post) {

    $post_id = $post->post_id;

    $posts[$post_id] = $post;

}

?>
```

现在我们有了根据标识值键索引的 `Post` 实体集合，我们通过一次查询获取整个 `$posts` 集合的所有 `Comment` 实体。

## 使用 Query-Stitch 解决 N+1

```php
<?php

// 创建一个用逗号分隔的引号 post_id 值列表

$quoted_post_ids = [];

foreach (array_keys($posts) as $post_id) {

    $quoted_post_ids[] = $pdo->quote($post_id);

}

$quoted_post_ids = implode(',', $quoted_post_ids);

// 获取所有帖子的评论

$stmt = "SELECT 

FROM comments

WHERE post_id IN ($quoted_post_ids)";

$stmt = $pdo->prepare($stmt);

$stmt->execute();

$comment_entities = $stmt->fetchAll(PDO::FETCH_CLASS, 'Comment');

?>
```

> 评论-编码功能会创建一个用逗号分隔的 `post_id` 值列表，用于 `IN` 子句。通常情况下，我们更倾向于使用占位符绑定（placeholder binding），但遗憾的是 `PDO` 不绑定数组。此外，`quote()` 不会将数组转换为引号且逗号分隔的值。因此，我们必须创建带引号的逗号分隔的值集。（某些数据库访问库可以绑定数组作为逗号分隔的值，例如 `AuraSql`。如果你正在使用其中一种，那就再棒了。）

最后，我们将 `Comment` 条目提交到 `Post` 实体的根集合中。由于 `$posts` 集合是以 `post_id` 值作为键的，很容易将每个 `Comment` 匹配到每个 `Post`。

```php
<?php

foreach ($comment_entities as $comment) {

    $post_id = $comment->post_id;

    $comment_id = $comment->comment_id;

    $posts[$post_id]->comments[$comment_id] = $comment;

}

?>
```

搞定：我们总共使用了两次查询和两个循环，就创建了带有关联 `Comment` 集合的 `Post` 实体根集合。

尽管我们仍然使用了循环，但重要的区别在于我们没有在循环内部使用查询。与在循环内部运行查询相比，将关联实体缝合（stitch）到根集合中的循环快得多。

https://github.com/aurasphp/AuraSql

## 使用 Query-And-Stitch 解决 N+1

## 处理“多对多”关系

我们也可以关联多对多关系中的实体。例如，如果我们需要为每个 `Post` 关联一个多对多关系的 `Tag` 集合，我们可以这样操作：

```php
<?php

// 通过 `posts_tags` 关联表获取所有标签

$stmt = "SELECT

    posts_tags.post_id AS post_id,

    tags.*

FROM tags

JOIN posts_tags ON posts_tags.tag_id = tags.tag_id

WHERE posts_tags.post_id IN ({$quoted_post_ids})";

$stmt = $pdo->prepare();

$stmt->execute();

$tag_entities = $stmt->fetchAll(PDO::FETCH_CLASS, 'Tag');

// 将标签缝合到 posts 中

foreach ($tag_entities as $tag) {

    $post_id = $tag->post_id;

    $tag_id = $tag->tag_id;

    $posts[$post_id]->tags[$tag_id] = $tag;

}

?>
```

> 注意，我们没有捕获关联表映射数据本身。对于这一点，我们需要另一个查询和另一个实体来保留数据。

使用 query-and-stitch 技术，我们总共发出了 3 次查询，并总共使用了 4 次循环，来获取根实体 ID 并缝合两个关联（评论和标签）。在 N+1 的情况下，PHP 代码中将只使用一个循环，但我们将总共发出 21 次查询。多个 PHP 循环的性能实际上可以保证优于 21 次查询的性能。

## 处理“多对一”关系

如果我们想添加一个“多对一”关系（有时称为“属于”（belongs-to）关联），query-and-stitch 逻辑会稍微复杂一些。我们需要构建一个唯一关联实体的集合，然后将关联实体缝合到根集合中。在这种情况下，我们不希望为每个关联实体创建多个副本，每个实体由相同的底层数据库行表示。

例如，如果每个 `Post` 都属于一个 `Author`，我们需要先收集唯一的 `Author` 实体，然后将它们缝合到 `Post` 集合中。如果一个 `Author` 关联了多个 `Post` 实体，通过一个 `Post` 修改 `Author` 数据将反映在所有具有相同 `Author` 的其他 `Post` 实体中。

```php
<?php

// 从 posts 集合中获取唯一的 author_id 值

$quoted_author_ids = array();

foreach ($posts as $post) {

    $quoted_author_ids[] = $pdo->quote($post->author_id);

}

$quoted_author_ids = implode(',', array_unique($quoted_author_ids));

// 将所有作者获取到 posts 集合

$stmt = "SELECT *

FROM authors

WHERE author_id IN ($quoted_author_ids)";

$stmt = $pdo->prepare();

$stmt->execute();

$author_entities = $stmt->fetchAll(PDO::FETCH_CLASS, 'Author');

// 根据标识值对所有作者集合建立键

$authors = array();

foreach ($author_entities as $author) {

    $author_id = $author->author_id;

    $authors[$author_id] = $author;

}

// 将 Author 实体缝合到 posts

foreach ($posts as $post) {

    $author_id = $post->author_id;

    $post->author = $authors[$author_id];

}

?>
```

`Author` 是我们为每个 `Post` 添加的第三个关联（两个是 `Comment` 和 `Tag` 关联）。这样做，我们只添加了 1 次查询，总共 4 次。在这种情况下，有两个额外的循环，一个用于创建 `Author` 集合，另一个将每个 `Author` 缝合到其关联的 `Post`。

## 处理“一对一”关系

添加“一对一”关系是最容易处理的情况。我们再增加一次查询和一次循环，来获取根集合的所有关联，并将它们缝合到根集合中。在这种情况下，我们不需要跟踪唯一性，只需要获取根集合的所有关联并缝合到根集合中。让我们说我们需要建立键值：

```php
<?php

// 获取根集合的所有 summaries

$stmt = "SELECT *

FROM summaries

WHERE post_id IN ($quoted_post_ids)";

$stmt = $pdo->prepare();

$stmt->execute();

$summary_entities = $stmt->fetchAll(PDO::FETCH_CLASS, 'Summary');

// 根据标识值对 summaries 建立键

$summaries = array();

foreach ($summary_entities as $summary) {

    $post_id = $summary->post_id;

    $summaries[$post_id] = $summary;

}

// 将 summaries 缝合到 posts

foreach ($posts as $post) {

    $post_id = $post->post_id;

    $post->summary = $summaries[$post_id];

}

?>
```

`Summary` 是我们为每个 `Post` 添加的第四个关联。

## 性能影响

让我们汇总查询和循环次数：

- 总共 5 次查询：1 次用于根集合，每个关联各 1 次
- 总共 9 次循环：
  - 1 次为 `Post` 集合建立键
  - 1 次分别为 `Author` 和 `Summary` 集合建立键
  - 1 次创建 `post_id` 的引号分隔值
  - 1 次将 `Comment`、`Tag`、`Author` 和 `Summary` 关联缝合到根集合

相比之下，具有 10 个 `Post` 实体的 N+1 情况将只有一个循环，但将发出 41 次查询。query-and-stitch 解决方案的代码量更多，但由于查询减少，性能要更好。

# 7. 重构代码库以移除 N1 问题

现在我们已经讨论了解决 N1 问题的方案，可以开始从代码库中移除它们。我们不需要重写整个应用程序；相反，我们可以通过重构逐步改进代码库。

## 前提条件

在开始之前，我们应该准备好一些前提条件。

最重要的是我们要对应用程序拥有某些测试，至少是对我们要修改的部分。这些测试将帮助我们确保移除 N1 问题时所做的更改不会破坏应用程序。这些不需要是单元测试，表征测试（Characterization tests）即可。至少要与 QA 团队建立良好关系，并将他们的验收测试应用于你的更改。

如果我们没有使用修订版本控制系统（如 `Git`），现在是开始的好时机。我们应该在单独的分支中工作，而不是在主开发分支中。在我们确认更改工作正常后再进行合并。

我们需要能够在短的迭代循环中诊断并解决我们的数据库交互循环。这意味着我们需要访问数据库本身（即使只是本地副本），并带有一组用于查询测试的数据数据集。当然，这还需要一套可运行的应用程序安装。

## 流程

解决 N+1 问题的通用流程如下：

- 1. 诊断是否存在 N+1 问题，并发现其在代码库中的位置。
- 2. 确定 N+1 代码的性质：
    - 如果根集合和关联关系都是一起构建的，我们应该能够对代码进行原地重构。
    - 反之，如果根集合是在一个位置构建的，而关联是在另一个位置构建的，我们必须修改不同位置的代码，或者将其收集到一个单一位置。
- 3. 一旦解决了 N+1 问题，对应用程序进行测试或抽检，以确保其运行正常。
- 4. 提交更改，将其推送到中央仓库，并通知 QA（质量保证）。
- 5. 诊断是否仍存在其他 N+1 问题，并重新开始该流程。

由于我们已经涵盖了 N+1 问题的诊断和发现技术，现在可以继续确定所发现的 N+1 代码的性质。

## 单一位置中的 N+1

这是最容易解决的 N+1 变。在这种情况下，实体的根集合和所有关联都在单个函数、方法或类中构建。它看起来类似于我们之前的帖子和评论示例，我们可以直接对现有代码应用单查询解决方案和/或“查询并缝合”（query-and-stitch）方案。

## 跨分离位置的 N+1

这是更困难的 N+1 变体，在现代化的代码库中很常见。在这里，实体的根集合在代码库中的一个位置构建，但关联在另一个独立的位置构建。

例如，如果我们的业务逻辑构建了一个 `Post` 实体集合……

## 重构代码库以消除 N+1 问题

`/path/to/posts_controller.php`

```php
<?php

$stmt = 'SELECT * FROM posts ORDER BY datetime DESC LIMIT 10';

$sth = $pdo->prepare($stmt);

$sth->execute();

$posts = $sth->fetchAll(PDO::FETCH_CLASS, 'Post');

?>
```



并且我们的表现层遍历 `Post` 实体以显示 `Comment` 集合……

`/path/to/templates/show_posts.php`

```php
<?php

foreach ($posts as $post) {

  // 显示帖子，...

  $stmt = "SELECT * FROM comments WHERE post_id = :post_id LIMIT 10";

  $sth = $pdo->prepare(array('post_id' => $post->post_id));

  $sth->execute();

  $comments = $sth->fetchAll(PDO::FETCH_CLASS, 'Comment');

  foreach ($comments as $comment) {

    // 显示每个评论

  }

}

?>
```

那么我们必须处理这些分离位置中的代码。（这是遗留代码库中 N+1 的经典示例。）

## 内联嵌入“查询并缝合”逻辑

由于“1”和“N”位于不同的位置，即使在关联是单个实体的情况下，我们也无法应用单查询解决方案。我们需要在分离的位置中内联嵌入“查询并缝合”逻辑。

首先，我们更改构建根集合的代码，使其根据 `Post` 的标识值对集合进行键化处理。（这看起来应该熟悉；它取自关于查询并缝合的章节.）

`/path/to/posts_controller.php`

```php
<?php

$stm = 'SELECT * FROM posts ORDER BY datetime DESC LIMIT 10';

$stm = $pdo->prepare($stm);

$stm->execute();

$post_entities = $stm->fetchAll(PDO::FETCH_CLASS, 'Post');

$posts = array();

foreach ($post_entities as $post) {

    $post_id = $post->post_id;

    $posts[$post_id] = $post;

}

?>
```

然后，在构建关联的分离位置中，我们内联应用“查询并缝合”方法。（这看起来应该熟悉。）

`/path/to/templates/show_posts.php`

```php
<?php

$quoted_post_ids = [];

foreach (array_keys($posts) as $post_id) {

    $quoted_post_ids[] = $pdo->quote($post_id);

}

$quoted_post_ids = implode(',', $quoted_post_ids);

// 获取所有帖子的评论并缝合到帖子中

$stm = "SELECT * FROM comments WHERE post_id IN ($quoted_post_ids)";

$stm = $pdo->prepare($stm)->execute();

$comment_entities = $stm->fetchAll(PDO::FETCH_CLASS, 'Comment');

foreach ($comment_entities as $comment) {

    $post_id = $comment->post_id;

    $comment_id = $comment->comment_id;

    $posts[$post_id]->comments[$comment_id] = $comment;

}

// 重构后的表现逻辑

foreach ($posts as $post) {

    // 显示帖子，然后...

    foreach ($post->comments as $comment) {

        // 显示每个评论

    }

}

?>
```

## 统一“查询并缝合”逻辑

内联方法对于遗留代码库是可行的，但它很混乱。如果我们有一个分层良好的现代代码库，那么最好将分离的关联构建逻辑提取到适当层中。这到目前为止是首选的方法。

例如，假设我们有一个 `PostsMapper` 和 `CommentsMapper`：

### Mapper 类

```php
<?php

class PostsMapper

{

    protected $pdo;

    public function fetchRecentPosts()

    {

        $stm = 'SELECT * FROM posts ORDER BY datetime DESC LIMIT 10';

        $sth = $this->pdo->prepare($stm);

        $sth->execute();

        $posts = $sth->fetchAll(PDO::FETCH_CLASS, 'Post');

        return $posts;

    }

}

class CommentsMapper

{

    protected $pdo;

    public function fetchCommentsForPost($post_id)

    {

        $stm = 'SELECT * FROM comments WHERE post_id = :post_id';

        $sth = $this->pdo->prepare($stm);

        $sth->execute(array('post_id' => $post_id));

        $comments = $sth->fetchAll(PDO::FETCH_CLASS, 'Comment');

        return $comments;

    }

}

?>
```

## 重构代码库以消除 N+1 问题

我们的 N+1 表现逻辑可能看起来如下：

`/path/to/templates/show_posts.php`

```php
foreach ($posts as $post) {

    // 显示帖子，然后...

    foreach ($post->comments as $comment) {

        // 显示每个评论

    }

}
```

使用“查询并缝合”的一种方法是将将其放在 `CommentsMapper` 中。

`CommentsMapper.php`

```php
<?php

class CommentsMapper {

    public function fetchIntoPosts($posts) {

        $quoted_post_ids = [];

        foreach (array_keys($posts) as $post_id) {

            $quoted_post_ids[] = $pdo->quote($post_id);

        }

        $quoted_post_ids = implode(',', $quoted_post_ids);

        // 获取所有帖子的评论

        $stmt = "SELECT * FROM comments WHERE post_id IN ($quoted_post_ids)";

        $stmt = $pdo->prepare($stmt)->execute();

        $comment_entities = $stm->fetchAll(PDO::FETCH_CLASS, 'Comment');

        // 缝合到帖子

        foreach ($comment_entities as $comment) {

            $post_id = $comment->post_id;

            $comment_id = $comment->comment_id;

            $posts[$post_id]->comments[$comment_id] = $comment;

        }

    }

}

?>
```

（不需要返回 `$posts`，因为 `$posts` 是按引用传递的。）

然后表现逻辑可以变成这样：

`/path/to/templates/show_posts.php`

```php
<?php

$comments_mapper->fetchIntoPosts($posts);

foreach ($posts as $post) {

    // 显示帖子

    foreach ($post->comments as $comment) {

        // 显示每个评论

    }

}

?>
```

通过这种方式，我们解决了 N+1 问题。然而，我们仍然存在层分离问题。作为进一步的重构，我们可能希望在领域层中统一“查询并缝合”逻辑，并以更好的方式构建 `Post` 实体集合。

# 8. 常见问题

## 我可以将单次查询（Single-Query）与查询合并（Query-and-Stitch）结合吗？

在某些情况下，将单次查询方法与查询合并方法结合可能是合理的。你可以用单次查询处理所有的“一对一”关系，然后使用查询合并方法处理所有的“一对多”关系。这样做通过将所有“一对一”查询合并到根查询中，减少了总的查询次数。在我们之前的示例中，这意味着三个 `Post`（文章）、`Author`（作者）和 `Summary`（摘要）的查询将合并为一个查询，只剩下 `Comment`（评论）和 `Tag`（标签）查询。

在性能极其重要的情况下，我支持结合这些方法。但我推测，通过消除代码库中的 N+1 问题，我们大幅提升了性能，以至于更大的担忧变成了一致性问题。混合使用方法，或者在某些情况下使用一种方法而在其他情况下使用另一种方法，意味着代码库的不一致。这反过来会降低开发者的理解能力并误导他们的预期。

因此，我倾向于在整个代码库中使用查询合并方法，即使这意味着在某些地方增加了一两次额外的查询。当然，一旦这些额外的查询从想象中或预测的性能担忧变为实际且可衡量的性能问题，我很乐意使用单次查询解决方案来解决这些问题。

一如既往，你自己的需求和偏好应该是使用何种方法以及何时使用的最终决定因素。

## 我可以使用 Select 代替 IN() 运算符吗？

在查询合并解决方案中，我们创建了一个带引号的、逗号分隔的值列表，指示要从数据库检索的标识或外键。然后，我们使用 `IN()` 运算符配合值列表来获取构建关联所需的行行。

虽然很容易想象出 `IN()` 运算符存在的问题，但我自己很少遇到 `IN()` 实际上成为问题的情况。某些数据库可能会限制 `IN()` 元素的数量或长度，或者限制整个查询字符串的长度，但在实践中，我发现这些限制并不重要。只要 `IN()` 条件引用的是索引列，我就发现很少或没有性能相关的问题。

然而，在某些情况下，`IN()` 运算符仍然是一个可衡量的性能问题。你只有通过对较慢的查询运行 `EXPLAIN`（或等效命令），并发现查询计划对 `IN()` 并不是最优的，才能判断这一点。

在这种情况下，用对子查询的 `JOIN` 替换 `IN()`，以提供检索所需的相关值。例如，获取 `Post` 实体的根集合和关联的 `Comment` 实体集合可能看起来如下所示：

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

通过查询合并，我们对数据库进行了多次调用。然而，数据库中的数据在这些调用之间可能会发生。例如，假设我们获取了 `Post` 集合的行，紧接着其中一个文章的行值被更改了（例如 `author_id`）。之后任何 `JOIN posts` 或以其他方式向可用数据提供相同 `author_id` 列表的查询，都可能不一致并导致意外结果。

出于这个原因，在某些情况下在事务内部执行查询合并可能是明智的。这样做有助于在将结果合并的多个查询之间保持一致的状态。

事务有不同级别的隔离性，不同的数据库有它们的默认设置。我建议使用 `READ COMMITTED` 级别，如果你发现由于隔离不足导致错误或不一致，则升级到 `REPEATABLE READ`。

> 事务和事务隔离涉及与表锁和行锁相关的性能考虑。务必咨询你的数据库文档以获取特定细节。你可能需要在一致性和性能之间进行权衡。

例如，使用 `PDO` 配合 `MySQL` 或 `PostgreSQL`，代码可能如下：

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

到这里，一些读者在考虑引入诸如 `Doctrine`、`Propel` 或 `PHP` 中提供的其他 ORM 系统是否是明智的。毕竟，ORM 本身就使用了单次查询和查询合并技术，因此使用 ORM 可以自动处理掉我们在解决 N+1 问题时需要自己编写的大量代码。

我对 ORM 态度复杂。在与 `Jeff Moore` 一起为 `Solar` 开发了一套健壮的 ORM 系统后，我完全熟悉使用它们的权衡。它们在应用程序开发的早期通常是巨大的助力。但在边缘情况下，它们会被揭示为不透明、低效或不可预测，因此需要你对它们在不同情况下的特殊性有良好的了解。

ORM 几乎总是要求你学习特殊的惯用法来构建查询。这些惯用法可能与某种类 SQL 的语言绑定，也可能与各种类中的特定一组方法和信息属性绑定，或者二者兼有。我觉得这种修改后的工作方式为将 ORM 引入现有应用程序带来了显著的阻碍。即使你的数据库逻辑拆分得很好，你也必须重写每一个数据库交互以符合 ORM 的查询惯用法。这需要花费时间和精力的，而这些精力可能花在其他地方更好。

即使引入了 ORM，你可能无法完全免受 N+1 问题的影响。如果 ORM 在循环中懒加载记录，而你又没有预加载所需的数据，情况尤为如此。你需要关注 ORM 内部是如何工作的，以避免最终陷入你正试图解决的问题中。

总的来说，我认为 ORM 的权衡高度取决于上下文。在不知道你的具体情况的情况下，我无法提供提供通用的建议，除非说一句“谨慎行”。

http://solarphp.com
http://www.procata.com

# 附录

## SQL Schema

以下 `SQLite` 表表示了一个简单的博客应用程序的数据结构。
表以复数实体命名：`posts`、`comments` 等。每个主键列都是自动递增的，并以单数实体命名并带有 `*_id`：`post_id`、`comment_id` 等。

`summaries` 表没有 `summary_id` 列，因为每一行与 `posts` 是直接一对一的。`posts_tags` 表是一张关联表，映射 `posts` 和 `tags` 之间的多多关系。

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



## 附录

40

```sql
CREATE TABLE posts_tags (
id INTEGER PRIMARY KEY AUTOINCREMENT,
post_id INTEGER,
tag_id INTEGER);
```

```sql
CREATE TABLE summaries (
post_id INTEGER,
view_count INTEGER,
comment_count INTEGER);
```

```sql
CREATE TABLE tags (
tag_id INTEGER PRIMARY KEY AUTOINCREMENT,
name VARCHAR(255));
```

### PHP 类

以下 PHP 类代表了一个简易博客应用程序中的实体。这些类经过了刻意简化，以展示类的核心内容，不应作为实际应用程序的基础。特别，这些类使用了公共属性来避免编写样板的 getter 和 setter 方法；这样做是为了减少展示的代码量，而不是表示这良好的实践。

```php
<?php
class Author {
    /** 数据库列 */
    public $author_id;
    public $name;
}
```

```php
class Comment {
    /** 数据库列 */
    public $comment_id;
    public $post_id;
    public $datetime;
    public $name;
    public $email;
    public $website;
    public $body;
}
```

```php
class Post {
    /** 数据库列 */
    public $post_id;
    public $author_id;
    public $datetime;
    public $title;
    public $body;
    /** 关联 */
    public $author;
    public $comments;
    public $summary;
    public $tags;
}
class Summary {
  /** 数据库列 */
  public $post_id;
  public $view_count;
  public $comment_count;
}
class Tag {
  /** 数据库列 */
  public $tag_id;
  public $name;
}
```

## 版后记

### Leanpub 格式设置

|  |  |
|---|---|
| 每一节后强制分页 | 否 |
| 在 PDF 中以脚注形式显示链接 | 是 |
| 字体大小 | 12pt |
| 正文字体 | Linux Libertine |
| 标题字体 | Open Sans |
| 代码字体 | Source Code Pro |
| 代码字体大小 | 10pt |
| 页面尺寸 | US Letter |
| 段落样式 | 无缩进 |
| 在代码示例中显示行号 | 是 |
| 章节和节标题 | 左对齐 |
| 目录 | 部分、章节和节；显示点 |
| 章节编号 | 对部分和章节进行编号 |
| 场景分隔符显示为 | 横线 |
| 表格 | 默认 |
| 旁注 | 白色；显示边框 |
| 图注 | **粗体** |
| 在章节页显示页码 | 否 |

## 关于作者

Paul M. Jones 是一位国际认可的 PHP 专家，他曾在各种机构（企业、军事、非营利、教育、医疗等）中担任过从初级开发人员到工程副总裁的所有职位。他在 `paul-m-jones.com` 运营专业博客，并是各种 PHP 大会的定期演讲者。

Paul 最新的开源项目是 Aura for PHP¹。此前，他是 Solar Framework² 背后的架构师，也是 Savant 模板系统的创建者³。他是 Zend Framework¹DB、DB、Table 和 View 组件的创始贡献者，并编写了一系列关于动态框架性能⁶的权威基准测试⁵。

Paul 是 PEAR 项目⁷的首批成员之一。他是 PHP 框架互操作小组⁸的投票成员，在该小组制定了 PSR-1⁹“编码标准”和 PSR-2¹⁰“编码风格”建议，是 PSR-4¹¹“自动加载器”建议的主要作者。他还是 Zend PHP 5.3 认证教育委员会¹的成员。

在之前的职业中，Paul 曾是美国空军的任务情报专家。在空闲时间，他喜欢在 400 英尺外射击 .308。

- ¹http://paul-m-jones.com
- ²http://aurphp.com
- ³http://solarphp.com
- ⁴http://phpsavant.com
- ⁵http://framework.com/
- ⁶https://github.com/jonpson/php-framework-benchmarks
- ⁷http://paul-m-jones.com/?p=421
- ⁸http://pear.php.net
- ⁹http://php-fig.org/
- ¹⁰http://php-fig.org/psr/psr-1
- ¹¹http://php-fig.org/psr/psr-2
- ¹²http://php-fig.org/psr/psr-4
- ¹³https://www.zend.com/services/certification/php-5-certification/education-advisory-board
