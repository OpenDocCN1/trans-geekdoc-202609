```
WHERE ID = $ID";
```

```
$result = @mysql_query($query, $connection) or die(mysql_error());
if (mysql_num_rows($result) == 0) {
    die('Invalid ID.');
}
```

If we get this far, the entry is valid, so let's assign its data to the Smarty object:

```
$row = mysql_fetch_array($result);
$smarty->assign("title", $row["title"]);
$smarty->assign("content", $row["content"]);
$smarty->assign("category", $row["category"]);
$smarty->assign("date", date("F dS Y, h:ia", $row["entry_time"]));
$smarty->assign("id", $ID);
```

Now we look up the comments with a very simple MySQL query (there is no need to join tables):

```
/* Look up comments. */
$query = "SELECT comment, name,
    UNIX_TIMESTAMP(comment_time) AS comment_time
    FROM blog_comments
    WHERE ID = $ID
    ORDER BY comment_time ASC";
$result = @mysql_query($query, $connection) or die (mysql_error());
```

It's time to do the dirty work of placing the comments into an array of arrays called $comments and assigning that to the Smarty $comments variable. Typically, this kind of code is a mess of print statements for tag closings and openings, but as previously mentioned, with Smarty's {section} feature, it's a piece of cake:

```
$comments = array();
while ($row = mysql_fetch_array($result)) {
    $comments[] = array(
        "name"    => $row["name"],
        "comment" => $row["comment"],
        "time"    => date("F dS Y, h:ia", $row["comment_time"]),
    );
}
$smarty->assign("comments", $comments);
```

There's nothing left to do now but process the template.

```
/* Display page. */
$smarty->display("blog_display.tpl");
?>
```