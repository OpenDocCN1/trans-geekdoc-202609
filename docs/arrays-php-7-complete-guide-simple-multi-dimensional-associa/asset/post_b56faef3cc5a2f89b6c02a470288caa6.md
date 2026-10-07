
```php
$customer = filter_input_array(INPUT_POST);

$customer_info = validate_array($customer["customer_record"]);
array_push($customer_record, $customer_info);
print_r($customer_record);
$query = "INSERT INTO customers(first_name, last_name, address, city, state, zip_code) VALUES (";
$query .= $customer_info[0] . "," . $customer_info[1] . "," . $customer_info[2] . "," .
$query .= $customer_info[3] . "," . $customer_info[4] . "," . $customer_info[5] . ")";
$result = $mysqli->query($query);
$mysqli->close();
}
catch(Exception $e) {
{
    print "An Exception occurred. Message: " . $e->getMessage();
}
catch(Error $e) {
{
    print "An Error occurred. Message: " . $e->getMessage();
}
?>


Example 2-6 provides a very simplified example using a MySQL database.
$mysqli = new mysqli("localhost", "website"

The fetch_all method converts the database rows into a two dimensional array (with numeric subscripts). The array is placed into $customer_record.

The next lines are the same as the previous example.

```php
$query = "INSERT INTO customers(first_name, last_name, address, city, state, zip_code) VALUES (";
$query .= $customer_info[0] . "," . $customer_info[1] . "," . $customer_info[2] . "," .
$query .= $customer_info[3] . "," . $customer_info[4] . "," . $customer_info[5] . ")";
```

After the information from the html form is attached to $customer_record array (and displayed) a SQL string is created from the information gathered in the html form.

```php
$result = $mysqli->query($query);
```

The query command then adds the record to the database.

```php
$mysqli->close();
```

The close statement then closes the database connection. Any Exceptions or Errors are caught by catch blocks. There is no reason to reload all the records back into the database. In this example only one record needs to be added to the current records. Let’s revisit foreach loop to display information contained in two-dimensional arrays.

```php
$customer_record = array(
    array('Pete', 'Smith', '123 Main Street', 'Atlanta', 'GA', '30001'),
    array('Sally', 'Parisi', '101 South Street', 'Atlanta', 'GA', '30001')
);
```

```php
foreach($customer_record as $row) {
    foreach($row as $column_value) {
        print $column_value . " ";
    }
}
foreach($customer_record as $row) {
The first foreach statement contains the array ($customer_record) and the row currently accessed by the loop ($row).
```

```php
This is similar to using one subscript when retrieving information from a two-dimensional array. The statement above will pull the current row (array) and display it. The outer foreach loop also pulls the current row (array) and places it in $row.

The first time the loop executes, it will be on row 0 (Pete). Each time the program hits the bottom of the outer loop and returns to the top, the foreach loop will move to the next row until there are no more rows.

```php
foreach($row as $column_value) {
The internal loop moves through the value within each column for the row that has been selected by the foreach loop. $row contains all columns (values) in the current row. $column_value contains the contents of the current column. Each time the program hits the bottom of the inner loop and returns to the top, the inner loop the next column is selected. When no more columns exist in the row, the loop ends.
```

When this occurs, the flow of the program will also drop to the bottom. This sends the flow back to the top of the outer loop, which retrieves the next row (if there is one). The print statement contained inside the loop displays the values within each row. The format used above does not allow us to retrieve subscript number (0, 1) or the column subscript (0, 1, 2, 3, 4, 5). To access this information we must break the $row property into two parts. Currently $row is the actual array (row) that will be accessed. To access the subscript we must request both the row subscript and the values in the row using the following format:

```php
foreach($customer_record as $row => $row_array) {
    foreach($row_array as $column => $column_value) {
        print "Row: $row Column: $column Value: $column_value";
    }
}
```

```php
print "<br>";
}
```

Row 0: Column 0 Value: Pete
Row 0: Column 1 Value: Smith
Row 0: Column 2 Value: 123 Main Street
Row 0: Column 3 Value: Atlanta
Row 0: Column 4 Value: GA
Row 0: Column 5 Value: 30001
Row 1: Column 0 Value: Sally
Row 1: Column 1 Value: Parisi
Row 1: Column 2 Value: 101 South Street
Row 1: Column 3 Value: Atlanta
Row 1: Column 4 Value: GA
Row 1: Column 5 Value: 30001
Row 1: Column 0 Value: Fred
Row 1: Column 1 Value: Smith
Row 1: Column 2 Value: 123 Main Street
Row 1: Column 3 Value: Atlanta
Row 1: Column 4 Value: GA
Row 1: Column 5 Value: 30001

This style is commonly referred to as the $key => $value format. The loop above uses $row instead of $key and $row_array instead of $value. It also uses $column instead of $key and $column_value instead of $value. The programmer can use any name for the key and value properties. The format becomes clear when looking at the print statement and the output from the print statement. It is clear that $row contains the actual row subscript, $column contains the column subscript, and $column_value contains the value in the row and column specified.

foreach loops can also be used to populate an array with values. It is common practice to provide initial values in an array, especially if the array will be used in calculations. In chapter 1, we talked about the possibility that an array, in some program languages, could contain a NULL value. If an attempt is made to do a calculation on a position in an array that contains a NULL value, an Error will be thrown. This can be avoided by providing initial values.

```php
foreach($customer_record as $row => $row_array) {
    foreach($row_array as $column => $column_value) {
        $customer_record[$row][$column] = "default";
    }
}
```

The code above will place "default" in every position in the array. Remember, in many situations, the loading of initial values in a PHP array is not necessary because the array positions can be created and populated with actual values at the same time. Some programmers chose to still initialize values to be consistent with the logic used in other programming languages.

PHP also provides the method `array_fill` which will accomplish the same task as the previous example.

```php
$customer_record = array_fill(0, 3, array_fill(0, 5, "default"));
```

The statement will create and fill each position in a $customer_record two-dimensional array with the value "default".

The array_fill syntax is:

Array name = array_fill(first subscript in array, last subscript in array, value used to fill array);

In the example, four rows are created (0, 1, 2, 3) as indicated by 0, 3. Each row contains an array (shown by the third position creating another array) with six columns (0, 1, 2, 3, 4, 5) as indicated by 0, 5. The limitation of using this method is that we need to know the initial size of the array. Of course, we can always add more rows and columns as needed.

```php
$customer_record = array_fill(0, 5, "default");
```

For one dimensional array, we include the starting subscript (0), the ending subscript (5), and the value we want to place in each position ("default").
