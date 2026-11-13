```
<!-- jokes.php -->
<html>
<head>
<title> Manage Jokes </title>
</head>
<body>
<h1>Manage Jokes</h1>
<p><a href="newjoke.php">Create New Joke</a></p>
<?php
$dbcnx = mysql_connect("localhost", "root", "mypasswd");
mysql_select_db("jokes");
$authors = mysql_query("SELECT ID, Name FROM Authors");
$cats   = mysql_query("SELECT ID, Name FROM
Categories");
?>
<form action="jokelist.php" method="post">
<p>View jokes satisfying the following criteria:<br />
By Author:
<select name="aid" size="1">
<option selected value=" ">Any Author</option>
<?php
while ($author = mysql_fetch_array($authors)) {
  $aid = $author['ID'];
  $aname = htmlspecialchars($author['Name']);
  echo("<option value='$aid'>$aname</option>\n");
}
?>
</select><br />
By Category:
<select name="cid" size="1">
<option selected value=" ">Any Category</option>
<?php
while ($cat = mysql_fetch_array($cats)) {
  $cid = $cat['ID'];
  $cname = htmlspecialchars($cat['Name']);
  echo("<option value='$cid'>$cname</option>\n");
}
?>
</select><br />
Containing Text: <input type="text" name="searchtext" />
<br />
<input type="submit" name="submit" value="Search" />
</form>
<p align="center"><a href="admin.html">Return to Front
Page</a></p>
</body>
</html>
```

Note that the \n at the end of the strings that are output by the echo function
is the special code for a new line, which serves to make the HTML code