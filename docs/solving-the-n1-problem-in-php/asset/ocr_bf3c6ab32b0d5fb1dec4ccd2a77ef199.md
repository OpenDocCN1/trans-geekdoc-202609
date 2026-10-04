# Solving N+1 With A Single Query

3. We use the PDO::FETCH_ASSOC fetch mode instead of PDO::FETCH_CLASS. This returns an array of arrays instead of an array of object instances. Because each row represents data for two entities, a Post and an Author, no class is suitable for the row data. As such, we will have to create the object instances ourselves from the row data.

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

```
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
}
```