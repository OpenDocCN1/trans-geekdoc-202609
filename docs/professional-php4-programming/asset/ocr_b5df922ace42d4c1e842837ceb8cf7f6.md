# # userprivilege.php

```
<?php
require("DB.php");
require("priv.classes.inc");

$sql = new DB("localhost", "", "", "userprivilege");
$sql->open();
```

displayUserSelection() sets up a list box of all the available users:

```
function displayUserSelection($aUsers)
{
    // Generate page for selecting a user

    echo "<?xml version=\"1.0\"?>\n";
    ?>
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
        "DTD/xhtml1-transitional.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
    <head>
    <title>User Privilege</title>
    </head>
    <body>
    <form method="post" action="userprivilege.php">
    <select name="username">
    <?php
    foreach ($aUsers as $sUsername => $sFullname) {
    echo(
        "<option value=\"" . $sUsername . "\">" .
        stripslashes(htmlspecialchars($sFullname)) .
        "</option>\n"
    );
    }
    ?>
    </select>
    <br />
    <br />
    <input type="submit" name="action" value="View Privileges" />
    <input type="submit" name="action" value="Exit" />
    </form>
    </body>
    </html>
    <?php
}
```

displayPrivileges() displays all the possible privileges that can be assigned to a user. The ones that are already set have checked checkboxes:

```
function displayPrivileges($oUser, $aPrivileges)
{
    // Generate page for privilege assignment
```