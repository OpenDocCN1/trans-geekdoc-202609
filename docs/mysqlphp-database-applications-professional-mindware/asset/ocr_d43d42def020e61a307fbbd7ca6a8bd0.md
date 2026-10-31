# Testing Variables

At the start of this chapter, we showed that assigning data to a variable determines the variable type. The appearance of the variable gives no indication as to what the variable contains. If you see $var sitting in a script you’ll have no idea if this contains a string, an integer, a floating-point number, or an array. In fact, many times in your scripts you won’t be sure if the variable contains a value, or even if it exists at all. For all these reasons, you need to perform tests. The following sections describe the types of tests you can perform.

# isset()

This function tests whether a variable has any value, including an empty string. It returns a value of either true or false. If the variable has not been initialized or has not been set, isset() will test false.

Consider the following script, which processes a MySQL query. You already know that database fields can contain both empty strings and null values. It’s quite possible that in your script you would want to treat the two differently. To print out a special message when the query comes across null values, you would need to use isset(). In this code, $query is a select statement typed into a form element.

```
$result = mysql_query($query) or
    die (mysql_error());

$number_cols = mysql_num_fields($result);

echo "<b>query: $query</b><br>\n";
//layout table header
echo "<table border = 1>\n";
echo "<tr align=center>\n";
for ($i=0; $i<$number_cols; $i++)
{
    echo "<th>", mysql_field_name($result, $i), "</th>\n";
}
echo "</tr>\n";//end table header

//layout table body
while ($row = mysql_fetch_row($result))
{
    echo "<tr align=left>\n";
    for ($i=0; $i<$number_cols; $i++)
    {
        echo "<td>";
        if (!isset($row[$i])) //test for null value
            (echo "NULL";)
```