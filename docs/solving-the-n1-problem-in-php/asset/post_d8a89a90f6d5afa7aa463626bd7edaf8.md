
# Solving N+1 With Query-Stitch

```php
<?php
// create a comma-separated list of quoted post_id values
$quoted_post_ids = [];
foreach (array_keys($posts) as $post_id) {
    $quoted_post_ids[] = $pdo->quote($post_id);
}
$quoted_post_ids = implode(',', $quoted_post_ids);

// fetch all the comments for the posts
$stmt = "SELECT 
FROM comments
WHERE post_id IN ($quoted_post_ids)";
$stmt = $pdo->prepare($stmt);
$stmt->execute();
$comment_entities = $stmt->fetchAll(PDO::FETCH_CLASS, 'Comment');
?>
```

> The comment-coding feature creates a comma-separated list of post_id values for the use in the IN clause. Normally we would prefer to use placeholder binding, but unfortunately PDO does not bind arrays. Further, quote() does not convert arrays to quoted-separated values. As much, we must create the quoted set of comma-separated values. (Some database access libraries do bind arrays as comma-separated values, such as AuraSql. If you are using one of them, so much the better.

Finally, we commit the Comment entries into the root collection of Post entities. Because the $posts collection is keyed on post_id values, it is easy to match each Comment to each Post.

```php
<?php
foreach ($comment_entities as $comment) {
    $post_id = $comment->post_id;
    $comment_id = $comment->comment_id;
    $posts[$post_id]->comments[$comment_id] = $comment;
}
?>
```

Voila: we have used a total of two queries and two loops to create the root collection of Post entities with their associated Comment collections.

Although we are still loops, the important distinction is that we are not using queries inside the loops. The loops that stitch the associated entities into the root collection are very fast compared to running queries inside those loops.

https://github.com/aurasphp/AuraSql

# Solving N+1 With Query-And-Stitch

## Handling “Many-To-Many” Relationships

We can also associate entities from a many-to-many relationship. For example, if we need to associate a Tag collection in a many-to-many relationship for each Post, we could do something like:

```php
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

## Handling “Many-To-One” Relationships

If we want to add a “many-to-one” relationship, sometimes called a “belongs-to” association, the query-and-stitch logic is somewhat more complex. We need to build a collection of unique associated entities, then stitch the associated entities into the root collection. We do not want to create multiple copies of each associated entity in this case, each is represented by the same backing database row.

For example, if each Post belongs to an Author, we need to collect the unique Author entities first, then stitch them into the Post collection. If one Author is associated with multiple Post entities, changing the Author data through one Post will be reflected in all other Post entities with that same Author.

```php
<?php
// get the unique author_id values from the posts collection
$quoted_author_ids = array();
foreach ($posts as $post) {
    $quoted_author_ids[] = $pdo->quote($post->author_id);
}
$quoted_author_ids = implode(',', array_unique($quoted_author_ids));

// fetch all authors into the posts collection
$stmt = "SELECT *
FROM authors
WHERE author_id IN ($quoted_author_ids)";

$stmt = $pdo->prepare();
$stmt->execute();
$author_entities = $stmt->fetchAll(PDO::FETCH_CLASS, 'Author');

// key all authors collection on its identity values
$authors = array();
foreach ($author_entities as $author) {
    $author_id = $author->author_id;
    $authors[$author_id] = $author;
}

// stitch the author entities into the posts
foreach ($posts as $post) {
    $author_id = $post->author_id;
    $post->author = $authors[$author_id];
}
?>
```

The Author is the third association we have added to each Post (the others were Comment and Tag associations). In doing so we have added only 1 query, for a total of 4. In this case, there were two additional loops, one to create the Author collection and to stitch each Author into its associated Post.

## Handling “One-To-One” Relationships

Adding a "one-to-one" relationship is the simplest case to deal with. We add one more query, and one more loop, to fetch the associations for the root collection all, and stitch them into the root collection. There's no need for uniqueness tracking as "many-to-one", but we need to key the associated entities on their foreign key values.

Let's say we want to bring in the Summary entry for each Post for the view and comment counts:

```php
<?php
 // fetch all summaries for the post collection
 $stmt = "SELECT *
 FROM summaries
 WHERE post_id IN ({$quoted_post_ids})";

 $sth = $pdo->prepare();
 $sth->execute();
 $summary_entities = $sth->fetchAll(PDO::FETCH_CLASS, 'Summary');

 // key a summaries collection on its foreign key values
 $summaries = array();
 foreach ($summary_entities as $summary) {
 $post_id = $summary->post_id;
 $summaries[$post_id] = $summary;
}

 // stitch the summaries into the posts
 foreach ($posts as $post) {
 $post_id = $post->post_id;
 $post->summary = $summaries[$post_id];
}
 ?>
```

The Summary marks the fourth association for the root collection of Post entities.

## Performance Implications

Let's tally up our query and loop counts:

- A total of 5 queries: 1 for the root collection, and 1 for each of the Comment, Tag, Author, and Summary associations
- A total of 9 loops:
  - 1 to key the Post collection on its key values,
  - 1 each to rekey the Author and Summary collections on their key values
  - 1 each to create the quoted-separated values for post_id and author_id lists
  - 1 each to stitch the Comment, Tag, Author, and Summary associations into the root collection

By contrast, an N+1 situation with 10 Post entities in the root collection would have had one loop, but would have issued 41 queries. The query-and-stitch solution is certainly more lines of code, but its performance is much better because of the reduced number of queries.

# 7. Refactoring The Codebase To Remove N+1 Problems

Now that we have discussed solutions for N+1 problems, we can begin to remove them from our codebase. We need not rewrite the entire application; instead, we can incrementally improve the codebase through refactoring.

## Prerequisites

Before we get started, we should have some prerequisites in place.

Most importantly, we should have tests of some sort for our application, or at least for the parts we are going to modify. These tests will help us assure that any changes we make while removing N1 problems do not break the application. These need not be unit tests, Characterization tests will just do fine. If nothing else, make friends with your QA team and apply their acceptance tests to your changes.

If we are not using a revision version control system, such as Git, now would be an excellent time to start. We should do our work in a separate branch, not in the same branch as the main thrust of development work. We can merge our changes after we know they work properly.

We need to be able to work in short iteration loops while diagnosing and resolving our database-interaction loops. This means we need access to the database itself, even if only a local copy, with a representative set of data for the querying testing. This is in addition to a working installation of the application code, of course.

Finally, if you have not Modernizing Legacy Applications in PHP and applied its formula to your codebase, you should consider doing so. While not strictly required, it will be very helpful. This is because we want to work on a codebase that has a good separation of concerns in place. If the database code is mixed in business logic and presentation, it is going to be that much more difficult to pick apart (and test!) the SQL queries contributing to our N+1 problems.
