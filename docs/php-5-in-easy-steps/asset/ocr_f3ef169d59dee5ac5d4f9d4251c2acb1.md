# Listing table names

Similar to the mysql_list_dbs() function, the PHP mysql_list_tables() function returns a result set of information about all tables in a database.

Each table name can be extracted by specifying the result set, and its row number in the result set, as the arguments to the mysql_listtablename() function. The example below reveals the names of three tables that have been added to the test database.

![](bbox=[0.145, 0.273, 0.266, 0.368])

```
<?php $conn = @mysql_connect("localhost", "mike", "bingo")
or or die("Sorry - could not connect to MySQL: ");");

$rs1 = mysql_list_dbs($conn);
for($row = 0; $row < mysql_list_num_rows($rs1); $row++) {
    $thisdb = mysql_listtablename($rs1, $row);
    $list = "<b>" . $thisdb . ".<br>";
    if ($thisdb != "mysql") {
        $rs2 = mysql_list_tables($thisdb);
        for($num = 0; $num < mysql_list_num_rows($rs2); $num++) {
            $list = "<li>" . ".mysql_listtablename($rs2,$num)".<br>>";
        }
    }
}
?>
```

MySQL's own database (called "mysql") must be excluded, as tables cannot be read in this way for security reasons.

```
<html><head><title>Listing Tables</title></head><body><?php echo ($list); ?></body></html>
```

| Listing Tables |
| --- |
| File Edit View Favorites Tools Help |
| Address http://localhost/list-tables.php | Go |
| mysql |
| test |
| - first_table |
| - second_table |
| - third_table |
| Done | Local intranet

11. PHP & MySQL together | 143