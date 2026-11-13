# Using the Script

```
<?php
$start_number = intval($_GET("start"));
$items_per_page = 100;
$category_sales = null;
if ($start_number >= 0) {
    // Count the items in the category.
    $sql = "SELECT count(*) AS count FROM product_info
            WHERE category = 'shoes'";
    $result = @mysql_query($sql, $connect_string) or die("Error is " .
    mysql_error());
    while($row = mysql_fetch_array($result)) {
        $count = $row['count'];
    }
    // Now get the results to show to the customer.
    $sql = "SELECT product_id, product_name FROM product_info
            WHERE category = 'shoes'
            LIMIT $start_number, $items_per_page";
    $result = @mysql_query($sql, $connect_string) or die("Error is " .
    mysql_error());
    if (mysql_num_rows($result) > 0) {
        while($row = mysql_fetch_array($result)) {
            // Loop through and add your HTML display info
            // into $category_sales.
            $category_sales .= "Data from SQL query";
        }
    } else {
        $category_sales = "There were no items in this category.";
    }
    $navbar = create_navbar($start_number, $items_per_page, $count);
}
if (is_null($category_sales)) {
    echo "Invalid input.";
} else {
    echo "$navbar<br />$category_sales";
}
?>
```

This example shows how to use the create_navbar() function in conjunction with a set of data from a database table (see the appendix for the data details). The script works as follows:

+   1. The starting row number is extracted from a GET parameter into the
+      $start_number variable.
+   2. An initial SQL query extracts the total number of displayable rows in
+      the table.