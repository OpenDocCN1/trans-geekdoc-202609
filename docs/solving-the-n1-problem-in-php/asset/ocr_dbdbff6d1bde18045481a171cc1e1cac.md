```
/** database columns */
public $post_id;
public $author_id;
public $datetime;
public $title;
public $body;

/** associations */
public $author;
public $comments;
public $summary;
public $tags;
}
class Summary {
  /** database columns */
public $post_id;
public $view_count;
public $comment_count;
}
class Tag {
  /** database columns */
public $tag_id;
public $name;
}
```