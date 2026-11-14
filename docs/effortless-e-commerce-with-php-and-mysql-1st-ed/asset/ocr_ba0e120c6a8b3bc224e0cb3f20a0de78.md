The comma between the table names in the queries is equivalent to the word JOIN.

# 10. Update the site's inventory:

```
```php
$q = 'UPDATE specific_coffees AS sc, order_contents AS oc SET
\\sc.stock=sc.stock-oc.quantity WHERE sc.id=oc.product_id AND
\\oc.product_type="coffee" AND oc.order_id=' . $order_id;
$r = mysqli_query($dbc, $q);
$q = 'UPDATE non_coffee_products AS ncp, order_contents AS oc SET
\\ncp.stock=ncp.stock-oc.quantity WHERE ncp.id=oc.product_id AND
\\oc.product_type="other" AND oc.order_id=' . $order_id;
$r = mysqli_query($dbc, $q);
```
```

Now that the items in the order have officially been purchased and can head out the door, the site's inventory needs to reflect the sold items.

This means that for every item in the order_contents table (for the current order), the corresponding records in the specific_coffees and non_coffee_products tables have to be updated.

MySQL actually allows you to perform a JOIN on an UPDATE query; two such queries can update the entire inventory, no matter how many records are present in the order_contents table. Each query may make more sense if viewed as a standard SELECT JOIN:

```
```sql
SELECT sc.stock, oc.quantity FROM specific_coffees AS sc,
order_contents AS oc WHERE sc.id=oc.product_id AND
oc.product_type="coffee" and oc.order_id=X
```
```

Instead of selecting the two values—stock and quantity—in matching rows, the one value is used to update the value in the other.

# 11. If the payment request didn't succeed, create an error:

```
```php
} else {
$error = "The payment could not be processed because: $response_array[3]";
} // End of payment response IF-ELSE.
```
```

As in Chapter 10, $response_array[3] contains a textual description of the problem. This will be safe to reveal to the administrator.

# 12. Complete the order total IF-ELSE:

```
```php
} else { // Invalid order total!
$error = "The order total ($$order_total) is invalid.";
} // End of $order_total IF-ELSE.
```
```

If the order total was not a positive number, that message is assigned to an error variable, along with the actual total.