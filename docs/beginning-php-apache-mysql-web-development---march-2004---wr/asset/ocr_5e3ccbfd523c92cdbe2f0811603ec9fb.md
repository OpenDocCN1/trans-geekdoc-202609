# Building a Content Management System

```
*article_id=* . $_POST['article'];

mysql_query($sql, $conn)
or die('Could not delete article: ' . mysql_error());
}
redirect('pending.php');
break;
```

If the article ID was passed, and the comment field is filled, in process this transaction.

```
case 'Submit Comment':
if (isset($_POST['article']))
and isset(\$_POST['comment'])
{
```

Insert the article ID, the comment date (MySQL datetime format), the user ID, and the actual comment into the database. If this has been accomplished, redirect the user to the home so he can see the newly saved comment.

```
$sql = "INSERT INTO cms_comments *\n\(article_id,comment_date,comment_user,comment) *\nVALUES (\' . $_POST['article'] . \', '" . \
date('Y-m-d H:i:s') . \', '" . \$_SESSION['user_id'] . \', '" . \
$_POST['comment'] . \', \', '" . \\');\)\
```

This is a case where the article is passed in the URL. Verify that the article ID was passed and the user is logged in.

```
case 'remove':
if (isset($_GET['article']))
and isset(\$_SESSION['user_id'])
{
```

We currently allow users to delete their own articles. You might modify this transaction to allow moderators to delete any article, but for now only users can delete the articles they have written.

```
$sql = "DELETE FROM cms_articles WHERE article_id=\
```

```
mysql_query($sql, $conn)
or die('Could not remove article; ' . mysql_error());
}
redirect('cpanel.php');
break;
```