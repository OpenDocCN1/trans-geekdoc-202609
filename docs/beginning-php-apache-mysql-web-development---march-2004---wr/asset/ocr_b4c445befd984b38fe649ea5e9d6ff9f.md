# Chapter 12

Yada, yada, yada. Don't you know HTML?

```
Ah... more PHP!?>
</table>
</div>
<br />
<h2>Published Articles</h2>
<div class="scroller">
<table>
```

Okay, this code is almost identical to the code used to display pending articles. This time, using the date_published column.

```
<?php
$sql = "SELECT article_id, title, date_published " . \
"FROM cms_articles * \
"WHERE is_published=1 * \
"AND author_id=" . \$_SESSION['user_id'] . " * \
"ORDER BY date_published DESC";
$result = mysql_query($conn,$sql)
or die("Could not get list of pending articles: " . mysql_error($conn));

if (mysql_num_rows($result) == 0) {
    echo "<li>No published articles available</li>";
} else {
    while ($row = mysql_fetch_array($result)) {
        echo "<tr>\n";
        echo "<td><a href="viewarticle.php?id=" . htmlspecialchars($row['id']) . ">" . $row['title'] . "</a></td>\n";
        echo "<td>" . date("F j, Y", strtotime($row['date_published'])) . "</td>\n";
        echo "</tr>\n";
    }
}
?>
```

# footer.php

Then load it. It is only a few lines of HTML for now, but today you will want to add a menu, or perhaps a copyright. The great thing is, even if your site uses 300 pages, you will have to add that information in one place: footer.php.

```
?>
</table>
</div>
<br />
<?php require_once 'footer.php'; ?>
```

Now let's take a look at the next Web display page, useraccount.php. First thing you'll notice is your old friend conn.php. But where is header.php? No worries—it will show up soon. As long as you don't attach anything to the page, you're okay.

408