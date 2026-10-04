

## 处理“一对多”关系

遗憾的是，单查询解决方案对于大多数“一对多”和“多对多”情况几乎完全是不适用的。让我们来看看之前的“帖子与评论”示例，找出为什么如此。我们将首先获取所有的 Post 实体（而不仅仅是 10 个）以及它们的所有评论：

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

- 1. 对于“一对一”，我们不再使用 SELECT *；仍然需要对相似的列名进行解构。
- 2. 对于“一对多”关系，我们添加了 LEFT JOIN 子句，在本例中是连接 comments 表。（我们使用 LEFT JOIN 是以防某些帖子没有评论）。
- 3. 同样对于“一对一”，我们使用 PDO::FETCH_ASSOC 模式而不是 PDO::FETCH_CLASS，并且我们必须自己创建对象实例。

结果集将会非常大，并且包含大量重复内容。如果系统中有 50 个 Post 实体，每个 Post 关联了 5 个 Comment 实体，这意味着结果集中将有 250 行。它看起来像这样：

## 使用单查询解决 N+1 问题

### 带有评论和重复帖子的结果行

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

由于结果集中的这些重复，我们需要遍历结果集并提取出不同的 Posts。同时，我们需要保留与每个 Post 关联的多个 Comment 实体。实现此操作的代码如下：

```php
<?php
$posts = array();
foreach ($rows as $row) {
    // 此行的 post 实体 ID
    $post_id = $row['posts__post_id'];
    
    // post 实体是否已于 $posts 集合中？
    if (!isset($posts[$post_id])) {
        // 创建一个新的 post 实体
        $post = new Post();
        $post->post_id = $row['posts__post_id'];
        $post->author_id = $row['posts__author_id'];
        $post->datetime = $row['posts__datetime'];
        $post->title = $row['posts__title'];
        $post->body = $row['posts__body'];
        $post->comments = array();
    }

    // 从行数据创建一个 comment 实体
```php
$comment = new Comment();
$comment->comment_id = $row['comment__comment_id'];
$comment->name = $row['comment__name'];
$comment->email = $row['comment__email'];
$comment->website = $row['comment__website'];
$comment->body = $row['comment__body'];

// 将 comment 关联到 post
$posts[$post_id]->comments[$comment->comment_id] = $comment;
}
?>
```

在循环结束时，我们将拥有一个包含所有 Post 实体及其所有关联 Comment 实体的 $posts 集合。

## 单查询在处理“一对多”关系时失效

虽然单查询解决方案看起来可能是解决应用于“一对多”关系的 N+1 问题的办法，但它存在一些主要的缺点。

首先，没有合理的方法可以添加按我们所需方式工作的 LIMIT 子句。这是因为 LIMIT 应用于返回的行数，而不是所代表的实体数量。这种区别虽然微妙但非常重要。

如果我们在上面的查询中添加 LIMIT 10，我们实际上会得到 10 行。但这些行并不一定代表 10 个 Post 实体（至少除非每个 Post 只有一个评论）。即使是对 FROM 和 JOIN 子句进行子查询变体，并在子查询中使用 LIMIT 子句，在“一对多”关系中也无法按照我们想要的方式工作。

事实证明，在单查询解决方案中强制执行“一对多”关系的 LIMIT 的唯一方法是在 PHP 循环代码中计数实体。可以说，这是一种次优方法。

其次，如果有两个或多个“一对多”关系，构建查询并解析结果集以创建实体将变得困难得多。重复问题会呈指数级变得棘手，我们需要跟踪每个关联实体的存在。此外，结果集的大小也会成为问题，无论是列数（因为每行都包含每个实体的所有列）还是行数（因为每行都会重复每个实体的每个数据元素，乘以关系的数量）。

总体而言，单查询解决方案可能适用于“一对一”关系，但完全不适用于任何数量的“一对多”关系。

## 6. 使用 Query-And-Stitch 解决 N+1

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

以下是使用查询与缝合技术重写的之前的帖子-评论示例。获取主 Post 实体的查询是相同的，但请注意我们随后创建了一个基于 post_id 的根集合（即而不是顺序键）。

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

现在我们有了根据标识值键索引的 Post 实体集合，我们通过一次查询获取整个 $posts 集合的所有 Comment 实体。

