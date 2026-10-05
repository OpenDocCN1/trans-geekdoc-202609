# Chapter II.4: MySQL and SQL Injections 225

```
// Deleting the file in the temporary directory
link($FILES['image']['tmp_name']);
```

```
// Escaping special characters in the file's binary contents
$content = mysql_escape_string($content);
```

```
if(mysql_query($query)) {
    // Automatically reloading the page
    echo "HTML<HEAD>
    <META HTTP-EQUIV='Refresh' CONTENT='0; URL=$_SERVER[PHP_SELF]>
    </HEAD></HTML>";
} else exit(mysql_error());
}
```

```
// Checking the current page number was passed
if(isset($_GET['page'])) $page = $_GET['page'];
else $page = 1;
```

```
// The initial position
$start = (($page - 1) *$pnumber + 1);
```

```
// Listing the files
$query = "SELECT * FROM image LIMIT $start, $pnumber";
$img = mysql_query($query);
if(!$img) exit(mysql_error());
// If there is at least one record,
// displaying it
if(mysql_num_rows($img) > 0) {
    while($image = mysql_fetch_array($img)) {
        echo "<img src=get.php?id_image=$image[id_image]>&nbsp;";
    }
}
```