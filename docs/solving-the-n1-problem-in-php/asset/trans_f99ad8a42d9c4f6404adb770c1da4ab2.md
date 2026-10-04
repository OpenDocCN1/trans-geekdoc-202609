

# 流程

解决 N+1 问题的通用流程如下：

- 1. 诊断是否存在 N+1 问题，并发现其在代码库中的位置。
- 2. 确定 N+1 代码的性质：
    - 如果根集合和关联关系都是一起构建的，我们应该能够对代码进行原地重构。
    - 反之，如果根集合是在一个位置构建的，而关联是在另一个位置构建的，我们必须修改不同位置的代码，或者将其收集到一个单一位置。
- 3. 一旦解决了 N+1 问题，对应用程序进行测试或抽检，以确保其运行正常。
- 4. 提交更改，将其推送到中央仓库，并通知 QA（质量保证）。
- 5. 诊断是否仍存在其他 N+1 问题，并重新开始该流程。

由于我们已经涵盖了 N+1 问题的诊断和发现技术，现在可以继续确定所发现的 N+1 代码的性质。

# 单一位置中的 N+1

这是最容易解决的 N+1 变。在这种情况下，实体的根集合和所有关联都在单个函数、方法或类中构建。它看起来类似于我们之前的帖子和评论示例，我们可以直接对现有代码应用单查询解决方案和/或“查询并缝合”（query-and-stitch）方案。

# 跨分离位置的 N+1

这是更困难的 N+1 变体，在现代化的代码库中很常见。在这里，实体的根集合在代码库中的一个位置构建，但关联在另一个独立的位置构建。

例如，如果我们的业务逻辑构建了一个 Post 实体集合……

# 重构代码库以消除 N+1 问题

/path/to/posts_controller.php

```php
<?php
$stmt = 'SELECT * FROM posts ORDER BY datetime DESC LIMIT 10';
$sth = $pdo->prepare($stmt);
$sth->execute();
$posts = $sth->fetchAll(PDO::FETCH_CLASS, 'Post');
?>
```

并且我们的表现层遍历 Post 实体以显示 Comment 集合……

/path/to/templates/show_posts.php

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

# 内联嵌入“查询并缝合”逻辑

由于“1”和“N”位于不同的位置，即使在关联是单个实体的情况下，我们也无法应用单查询解决方案。我们需要在分离的位置中内联嵌入“查询并缝合”逻辑。

首先，我们更改构建根集合的代码，使其根据 Post 的标识值对集合进行键化处理。（这看起来应该熟悉；它取自关于查询并缝合的章节.）

/path/to/posts_controller.php

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

/path/to/templates/show_posts.php

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

# 统一“查询并缝合”逻辑

内联方法对于遗留代码库是可行的，但它很混乱。如果我们有一个分层良好的现代代码库，那么最好将分离的关联构建逻辑提取到适当层中。这到目前为止是首选的方法。

例如，假设我们有一个 PostsMapper 和 CommentsMapper：

Mapper 类

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

# 重构代码库以消除 N+1 问题

我们的 N+1 表现逻辑可能看起来如下：

/path/to/templates/show_posts.php

```php
foreach ($posts as $post) {
    // 显示帖子，然后...
    foreach ($post->comments as $comment) {
        // 显示每个评论
    }
}
```

使用“查询并缝合”的一种方法是将将其放在 CommentsMapper 中。

CommentsMapper.php

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

（不需要返回 $posts，因为 $posts 是按引用传递的。）

然后表现逻辑可以变成这样：

/path/to/templates/show_posts.php

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

通过这种方式，我们解决了 N+1 问题。然而，我们仍然存在层分离问题。作为进一步的重构，我们可能希望在领域层中统一“查询并缝合”逻辑，并以更好的方式构建 Post 实体集合。

