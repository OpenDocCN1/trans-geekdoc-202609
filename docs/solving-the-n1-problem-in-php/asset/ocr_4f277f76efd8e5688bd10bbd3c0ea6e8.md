# Unify Query-And-Stitch Logic

The inline approach is fine for legacy codebases, but it is messy. If we have a more modern codebase with well-separated layers, we would do better to extract the separated association-building logic to an appropriate layer. This is by far the preferred approach.

For example, let's say we have a PostsMapper and a CommentsMapper:

Mapper classes

```
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
?>
```