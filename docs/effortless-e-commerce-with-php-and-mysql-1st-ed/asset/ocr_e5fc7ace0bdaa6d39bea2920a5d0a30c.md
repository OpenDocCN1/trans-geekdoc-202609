The parse_sku() function will turn a value such as _C23_ into a type of _coffee_ and an ID of 23, necessary for the queries. This $id variable has already been bound to the prepared statements.

+   **10. Execute the correct prepared statement based upon the type:**

```
if ($type == 'coffee') {
  mysqli_stmt_execute($stmt1);
  $affected += mysqli_stmt_affected_rows($stmt1);
} elseif ($type == 'other') {
  mysqli_stmt_execute($stmt2);
  $affected += mysqli_stmt_affected_rows($stmt1);
}
```

If the current item's type equals _coffee_, the first prepared statement will be executed, updating a record in the **specific_coffees** tables. If the type equals _other_, the second prepared statement will be executed, updating a record in the **non_coffee_products** table. The number of affected rows is added to the existing count in both cases.

+   **11. Complete the quantity validation IF and the foreach loop. Print the results:**

```
} // End of IF.
} // End of FOREACH.
echo "<h4>$affected Item(s) Were Updated!</h4>";
```

+   **12. Complete the form submission conditionals:**

```
} // End of $_POST['add'] IF.
// End of the submission IF.
```

+   **13. Begin the form:**

```
?><h3>Add Inventory</h3>
<form action="add_inventory.php" method="post"
accept-charset="utf-8">
<fieldSet><legend>Indicate how many additional quantity of each
product should be added to the inventory.</legend>
```

+   **14. Create a table:**

```
<table border="0" width="100%" cellspacing="4" cellpadding="4">
<thead>
<tr>
<th align="right">Item</th>
<th align="right">Normal Price</th>
<th align="right">Quantity in Stock</th>
<th align="center">Add</th>
```