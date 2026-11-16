```
"DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<title>Privilege</title>
</head>
<body>
<form method="post" action="privilege.php">
```

As we don't need to see the value of the privilege's ID (and shouldn't be able to change it anyway), we will use a hidden field to pass the privilege's ID along with its description:

```
<input type="hidden" name="priv_id"
       value="<?php echo($oPriv->getPriv_id()); ?>" />
<h3>Description:</h3>
<input
       type="text"
       name="description"
       value="<?php echo(stripslashes(htmlspecialchars(
                      $oPriv->getDescription()))); ?>"
       size="50"
       maxlength="50"
       />
<br />
<br />
<input type="submit" name="action" value="Save" />
<input type="submit" name="action" value="Delete" />
<input type="submit" name="action" value="Cancel" />
</form>
</body>
</html>
```

```
<?php
}
```

getPrivileges() allows us to obtain all the current privilege IDs. We aren't interested in the descriptions just now, as they aren't primary keys:

```
function getPrivileges()
{
    // Returns an array of all privileges

    global $sql;

    $aRet = array();

    $sql->query("SELECT * FROM Privilege ORDER BY priv_id");

    while ($row = $sql->fetchObject()) {
        $aRet[(int)$row->priv_id] = $row->description;
    }
    return $aRet;
}
```