# Core PHP Programming

# array mysql_fetch_row(integer result)

The mysql_fetch_row function returns an array with one element for each resulting column. FALSE is returned when no results are left. Columns are dereferenced by integers starting at zero. Compare this function to mysql_fetch_array and mysql_fetch_object.

```
<?
$Link = mysql_connect("mysql.clearlink.com");
mysql_select_db("store", $Link);

$Query = "SELECT * FROM item";
$Result = mysql_query($Query, $Link);

while($Row = mysql_fetch_row($Result))
{
    print($Row[0] . ": " . $Row[1] . ".<BR\n");
}

mysql_close($Link);
?>
```

# boolean mysql_field_seek(integer result, integer field)

Use mysql_field_seek to move the internal field pointer to the specified field.

```
<?
$Link = mysql_connect("mysql.clearlink.com");
mysql_select_db("store", $Link);

$Query = "SELECT * FROM item i, SKU s";
$Query .= "WHERE i.SKU = s.id";
$Result = mysql_query($Query, $Link);

// get description of each field
// starting with the third
mysql_field_seek($Result, 2);

while($Field = mysql_fetch_field($Result))
{
    print("Name: " . $Field->name . ".<BR\n");
    print("Table: " . $Field->table . ".<BR\n");
    print("Not Null: " . $Field->not_null . ".<BR\n");
    print("Primary Key: " . $Field->primary_key . ".<BR\n");
    print("Unique: " . $Field->unique . ".<BR\n");
    print("Type: " . $Field->type . ".<BR\n<BR\n");
}
```