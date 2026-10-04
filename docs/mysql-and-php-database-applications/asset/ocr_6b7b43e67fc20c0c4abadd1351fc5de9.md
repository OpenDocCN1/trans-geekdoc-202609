# Part II: Working with PHP

If you don't wish to commit these functions to memory, you could use the following code to achieve the same thing.

```
$result = mysql_query("show tables from test") or
die(mysql_error());
while ($row = mysql_fetch_row($result)) {
    echo $row[0], "<br>\n";
}
```

MYSQL_LIST_FIELDS() This function returns a result identifier, which you can then use to get information about the MySQL columns.

```
int mysql_list_fields(string database_name, string table_name,
 int link_identifier)
```

You must use a identifier from this function to get information from the mysql_field_flags(), mysql_field_len(), mysql_field_name(), and mysql_field_type() functions. All of these functions take the same arguments: the first is the result identifier, the second is the numeric offset of the column, starting at 0. These columns return about what you'd expect, respectively name flags (such as NOT NULL, PRIMARY KEY), the length, of the field, and the type (such as int, text, and so on).

As an example, create the table with the following create statement:

```
create table show_stuff (
    stuff_id int not null primary key auto_increment,
    stuff_desc varchar(255) null,
    stuff_stuff text
);
```

The following script will return everything you'd need to know about the columns. (The results of the script can be show in Figure 6-1.)

```
$result = mysql_list_fields("test", "show_stuff");
$i = 0;
while($i<mysql_num_fields($result)) {
    echo "<b>", mysql_field_name($result, $i) . "<b><br>";
    echo mysql_field_flags($result,$i) . "<b><br>";
    echo mysql_field_len($result, $i) . "<b><br>";
    echo mysql_field_type($result, $i) . "<b><br>";
    $i++;
}
```