The first foreach statement contains the array name ($customer_record) and the row currently accessed by the loop ($row).
print_r($customer_record);

This is similar to using one subscript when retrieving information from a two-dimensional array. The statement above will pull the current row (array) and display it. The outer foreach loop also pulls the current row (array) and places it in $row.

The first time the loop executes, it will be on row 0 (Pete). Each time flow of the program hits the bottom of the outer loop and returns to the top, the foreach loop will move to the next row, until there are no more rows.

foreach($row as $column_value)

The internal loop moves through the value within each column for the row that has been selected by the foreach loop. $row contains all columns (values) in the current row. $column_value contains the contents of the current column. Each time flow of the program hits the bottom of the inner loop and returns to the top of the inner foreach loop the next column is selected. When no more columns exist in the row, the loop ends.

When this occurs, the flow of the program will also drop to the bottom of the outside loop. This sends the flow back to the top of the outer loop, which retrieves the next row (if there is one).

print $column_value . " "

The print statement contained inside the inter loop displays the values in column within each row.

The format used above does not allow us to retrieve subscript number (0, 1) or the column subscript number (0, 1, 2, 3, 4, 5). To access to this information we must break the $row property into two parts. Currently $row is the actual array (row) that will be accessed. It does allow us to the subscript. To access the subscript we must request both the row subscript and the values in the row using the following format.

```
foreach($customer_record as $row => $row_array)
{
    foreach($row_array as $column => $column_value)
    {
        print "Row: $row Column: $column Value: $column_value";
    }
}
```