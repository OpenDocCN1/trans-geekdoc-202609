Solving N+1 With Query-And-Stitch

# Handling “Many-To-Many” Relationships

We can also associate entities from a many-to-many relationship. For example, if we need to associate a Tag collection in a many-to-many relationship for each Post, we could do something like:

```
<?php
// fetch all tags through a `posts_tags` association table
$stmt = "SELECT
    posts_tags.post_id AS post_id,
    tags.*
FROM tags
JOIN posts_tags ON posts_tags.tag_id = tags.tag_id
WHERE posts_tags.post_id IN ({$quoted_post_ids})";

$stmt = $pdo->prepare();
$stmt->execute();
$tag_entities = $stmt->fetchAll(PDO::FETCH_CLASS, 'Tag');

// stitch the tag into the posts
foreach ($tag_entities as $tag) {
    $post_id = $tag->post_id;
    $tag_id = $tag->tag_id;
    $posts[$post_id]->tags[$tag_id] = $tag;
}
?>
```

> Note that we do not capture the association table mapping data itself. For that, we would need another query, and another entity to retain the data.

Using the query-and-stitch technique, we have issued a total of 3 queries, and used a total of 4 loops, to get the root entity IDs and stitch together two associations (comments and tags). In an N+1 situation, would have used a single loop in the PHP code, but we would have issued a total of 21 queries. The performance of the multiple PHP loops is practically guaranteed to be better than the performance of 21 queries.

# Handling “Many-To-One” Relationships

If we want to add a “many-to-one” relationship, sometimes called a “belongs-to” association, the query-and-stitch logic is somewhat more complex. We need to build a collection of unique associated entities, then stitch the associated entities into the root collection. We do not want to create multiple