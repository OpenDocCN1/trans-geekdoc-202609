# Chapter 12

```
sql = 'SELECT name,e-mail * 
FROM cms_users * 
WHERE user_id=' . $_SESSION['user_id'];
$result = mysql_query($sql, $conn)
or die('Could not look up user data: ' . mysql_error($conn));
$user = mysql_fetch_array($result);
?>
<form method="post" action="transact-user.php?>

<p>Name:<br>
<input type="text" id="name" name="name"
value="<?php echo htmlspecialchars($user['name']); ?>\></p>
<p>E-Mail:<br>
<input type="text" id="e-mail" name="e-mail"
value="<?php echo htmlspecialchars($user['e-mail']); ?>\></p>

<p><input type="submit" class="submit" name="action"
value="Change my info" /></p>
</form>
```

<h2>Pending Articles</h2>
<div class="scroller">
<table>
<?php

```
$sql = "SELECT article_id
```

</table>
</div>
<br />
<h2>Published Articles</h2>

372