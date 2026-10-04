# Chapter 12

If you are editing an article, instead of composing a brand new one, you must go out to the database and
retrieve the article.

```
if (isset($_GET['a'])
  and $_GET['a'] == 'edit'
  and isset($_GET['article'])) {
  $sql = "SELECT title, body, author_id * 
  "FROM cms_articles WHERE article_id=" . $_GET['article'];
}

$result = mysql_query($sql, $conn);
or die("Could not retrieve article: " . mysql_error());

$row = mysql_fetch_array($result);

$title = $row['title'];
$body = $row['body'];
$article = $_GET['article'];
$authorid = $row['author_id'];
}
```

Load the prerequisite header.php:

```
require_once 'header.php';
```

What follows is more standard HTML stuff. You know what htmlspecialchars() does, don't you? Of
course you do. If not, go back to a page or two and review.

```
?>
```

```
<form method="post" action="transact-article.php">
<h2>Compose Article/</h2>

<p>
Title:<br />
<input type="text" class="title" name="title" maxLength="255"
value="<?php echo htmlspecialchars($title); ?>" / />
</p>
<p>
Body:<br />
<textarea name="body" rows="10" cols="60">?<?php echo htmlspecialchars($body); ?>?</textarea>
</p>
<p>
```

The article ID must be carried over to the transaction page if you are modifying an existing article.
The following hidden input field will do this for you:

```
<php
echo '<input type="hidden" name="article" value="' .
$article . '" />\n";
```