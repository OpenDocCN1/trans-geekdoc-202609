# Solving N+1 With A Single Query

```
$post->body = $row['post_body'];

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
```

With that, we have avoided the N+1 problem entirely for our "many-to-one" and "one-to-one" relationships. Adding more "to-to-one" relationships is as easy as adding another JOIN and creating the associated entity in the PHP loop.