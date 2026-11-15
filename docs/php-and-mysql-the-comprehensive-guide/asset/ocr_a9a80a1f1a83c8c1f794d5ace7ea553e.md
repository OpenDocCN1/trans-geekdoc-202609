```
$result = pg_query($db, $sql);
if ($row = pg_fetch_object($result)) {
    $Name = utf8_decode($row->author);
    $Email = utf8_decode($row->email);
    $Heading = utf8_decode($row->heading);
    $Comment = utf8_decode($row->entry);
}
pg_close($db);
} else {
    echo "Error!";
}
}
?>
<form method="post" action="">
Name <input type="text" name="Name" value="<?php
echo htmlspecialchars($Name);
?>" /><br />
Email address <input type="text" name="Email" value="<?php
echo htmlspecialchars($Email);
?>" /><br />
Heading <input type="text" name="Heading" value="<?php
echo htmlspecialchars($Heading);
?>" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"><?php
echo htmlspecialchars($Comment);
?></textarea><br />
<input type="submit" name="Submit" value="Update" />
</form>
</body>
</html>
```

# Listing 23.17 Editing a Guestbook Entry ("gb-edit.php")

# 23.4 Settings

The php.ini configuration file contains the setting options listed in Table 23.1.

| Parameters | Description | Default Value |
| :--- | :--- | :--- |
| pgsql.allow_persistent | Indicates whether persistent connections are possible | "1" |

# Table 23.1 The Configuration Parameters in "php.ini"