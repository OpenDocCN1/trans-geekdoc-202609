```
printf("<p><b><a href=\"gb-admin.php?id=%s\">Delete this entry </a>\n - <a href=\"gb-edit.php?id=%s\">Edit this entry</a></b></p>\n<p><a href=\"mailto:%s\">%s</a> wrote on/at %s:</p>\n<h3>%s</h3><p></p><hr noshade=\"noshade\" />",\nurldecode($row->id),\nurldecode($row->id),\nhtmlspecialchars($row->email),\nhtmlspecialchars($row->author),\nhtmlspecialchars($row->date->format("Y-m-d H:i:s")),\nhtmlspecialchars($row->heading),\nnl2br(htmlspecialchars($row->entry)))\n);\n}\nsqlsrv_close($db);\n} else {\necho \"Error!\";\n}\n}\n?>
</body>
</html>
```

# Listing 21.12 Display of All Data Including Deletion Option ("gb-admin.php")

# 21.3.5 Edit Data

Finally, the following listing both reads the data and sends it back to the database (via UPDATE). What we said earlier about inserting also applies to the update process: it would be more efficient and even safer to use a stored procedure, as demonstrated previously.

```
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
$Name = "";
$Email = "";
$Heading = "";
$Comment = "";
if (isset($_GET["id"])) &&
is_numeric($_GET["id"])) {
if ($db = sqlsrv_connect(
```