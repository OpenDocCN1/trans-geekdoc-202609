```
if ($command = sqlsrv_prepare($db, $sql, $parameter)) {
if (sqlsrv_execute($command)) {
$result = sqlsrv_query($db, "SELECT @@IDENTITY");
sqlsrv_fetch($result);
$id = sqlsrv_get_field($result, 0);
echo "Entry added.
<a href=\"\\gb-edit.php?id=$id\">Edit</a>";
} else {
echo "Error!";
}
} else {
echo "Error!";
}
sqlsrv_close($db);
} else {
echo "Error!";
}
}
?>
<form method="post" action="">
Name <input type="text" name="Name" /> <br />
Email address <input type="text" name="Email" /> <br />
Heading <input type="text" name="Heading" /> <br />
Comment
<textarea cols="70" rows="10" name="Comment"></textarea><br />
<input type="submit" name="Submit" value="Submit" />
</form>
</body>
</html>
```

# Listing 21.10 Data Can Be Entered ("gb-enter.php")

# 21.3.3 Output Data

To output the data, you can use one of the sqlsrv_fetch_* functions. We use the object variant here, but how you proceed is purely a matter of taste.

```
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
```