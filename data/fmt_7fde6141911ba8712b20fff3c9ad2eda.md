
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
