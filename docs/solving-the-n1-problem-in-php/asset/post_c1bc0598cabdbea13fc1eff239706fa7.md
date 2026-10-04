
# Solving N+1 With A Single Query

As with any N+1 situation, this will issue 1 query for the root collection of entities, and then 1 query for each association. In this case, with 10 Post entities, that means a total of 11 queries.

> As an added problem, note that the code creates a new Author entity for each Post. If all Post entities belong to the same Author, means there are ten copies of the Author data, none of which is authoritative. Changes to the Author of one Post will not be reflected in what should the same Author on another post. We will address this issue as part of the single-query solution below.

# Converting To A Single Query

Because this is a "many-to-one" query, where each Post belongs to only one Author, we can consider using a single-query approach to eliminate the N+1 problem. First, we fetch a set of rows for all Post and Author data:

```php
<?php
// get the most recent posts with their authors
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

Some things to note about this code:

- We no longer use SELECT *. We have to deconflict between tables that have the same column names (in this case author_id), and at the same time make sure we get back all the data needed to construct the relevant entities. Here we do by aliasing each column name with a prefix indicating the intended entity name, along with two underscores as a separator.
- We add a JOIN clause for the "to-one" relationship, in this case joining to the author's table.
- 3. We use the PDO::FETCH_ASSOC fetch mode instead of PDO::FETCH_CLASS. This returns an array of arrays instead of an array of object instances. Because each row represents data for two entities, a Post and an Author, no class is suitable for the row data. As such, we will have to create the object instances ourselves from the row data.

The database returns a result set that looks something like following:

# Result rows with post and author

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

Now we have the results, we loop through to create our entity objects.

```php
<?php
$authors = array();
$posts = array();
foreach ($rows as $row) {

    // create the post entity
    $post = new Post();
    $post->post_id = $row['post_post_id'];
    $post->author_id = $row['post_author_id'];
    $post->datetime = $row['post_datetime'];
    $post->title = $row['post_title'];
    $post->body = $row['post_body'];

    // does the author already exist?
    $author_id = (isset($authors[$author_id])) {
        // use the existing author entity
        $author = $authors[$author_id];
    } else {
        // create and retain a new author entity
        $author = new Author();
```

```php
$author->author_id = $author_id;
$author->name = $row['__name__'];
$authors[$author_id] = $author;
}

// associate the author entity
$post->author = $author;

// retain the post in the collection
$posts[] = $post;
```

Some notes about the object-creation code:

- 1. The approach clearly involves more lines of code than allowing PDO to create the entity instances for us. In a less naive situation, the entity constructors might receive an array of data and populate themselves, or there might be an entity factory or builder of some sort to handle that work. Regardless, this approach is guaranteed to perform better than issuing 11 queries to create the Post entities with their associated Author entities.
- 2. This solution uses unique Author associations across Post entities, unlike the N+1 code. While not strictly an N+1 problem, it does solve the issue of multiple objects representing the same author.

With that, the solution is complete. Adding “to-one” relationships to build associated entities is similarly straightforward. We would add another JOIN clause, alias the selected column names appropriately, and then pull them out of the row in our entity-creation flow, tracking unique entities along the way.

# Handling “One-To-One” Relationships

These are pretty straightforward under the single-query approach. A plain-old JOIN, without any tracking of unique entities, is all we need.

Let’s say the blogging application needs to present a list of Post entities, along with Summary data that tracks the number of views and number of comments. The retrieval and creation code would look something like this:

```php
<?php
// get the most recent posts with their authors
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

// create the posts collection with summaries
$posts = array();
foreach ($rows as $row) {
    // create the post entity
    $post = new Post();
    $post->post_id = $row['__post_post_id'];
    $post->author_id = $row['__post_author_id'];
    $post->datetime = $row['__post_datetime'];
    $post->title = $row['__post_title'];
    $post->body = $row['__post_body'];

    // associate the summary
    $post->summary = new Summary();
    $post->summary->post_id = $row['__summary__post_id'];
    $post->summary->view_count = $row['__summary__view_count'];
    $post->summary->comment_count = $row['__summary__comment_count'];

    // retain the post in the collection
    $posts[] = $post;
}
?>
```

As we can see, this is simple. Combining "many-to-one" and "one-to-one"

The major selling point of the single-query solution is that we should be able to bring in all the data for the root entity and the associated entities in one query. The combined retrieval code would look like this:

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

When we get the results, we pick up each row by building the creation logic as well:

```php
<?php
$authors = array();
$posts = array();
foreach ($rows as $row) {

    // create the post entity
    $post = new Post();
    $post->post_id = $row['post_id'];
    $post->author_id = $row['author_id'];
    $post->datetime = $row['post__datetime'];
    $post->title = $row['post__title'];
    $post->body = $row['post__body'];

    // does the author entity already exist?
    $author_id = $row['author__author_id'];
    if (isset($authors[$author_id])) {
        // use the existing author entity
        $author = $authors[$author_id];
    } else {
        // create and retain a new author entity
        $author = new Author();
        $author->id = $author_id;
        $author->name = $row['author__name'];
        $authors[$author_id] = $author;
    }

    // associate the author entity
    $post->author = $author;

    // associate the summary
    $post->summary = new Summary();
    $post->summary->post_id = $row['summary__post_id'];
    $post->summary->view_count = $row['summary__view_count'];
    $post->summary->comment_count = $row['summary__comment_count'];

    // retain the post in the collection
    $posts[] = $post;
}
?>
```
