Now, the user's shopping cart is going to stay very empty if we don't provide a way for them to add items to it, so let's modify the for loop that displays our table of items, and enable it to provide a 'Buy' link on the end of each row:

```
```php
<?php
for($i = 0; $i < count($items); $i++) {
    echo("<tr>");
    echo("<td>" . $items[$i] . "</td>");
    echo("<td>$" . number_format($prices[$i], 2) . "</td>");
    echo("<td><a href='$PHP_SELF?buy=$i'>Buy</a></td>");
    echo("</tr>");
}
?>
```
```

Now each product in our catalog has a link back to the catalog with buy=n in the query string, where n is the index of the item that's to be added to the shopping cart in the $items array. We can then watch for the $buy variable to appear at the top of the page, and when it does, we'll add the item to the $shoppingcart array before redirecting the browser back to the same page, but with no query string (to ensure that refreshing the page doesn't repeatedly add the item to the cart).

```
```php
if ($buy != "") {
    // Add item to the end of the $shoppingcart array
    $shoppingcart[] = $buy;
    header("Location: $PHP_SELF");
    exit();
}
```
```

Now, this works just fine if the user has cookies enabled, but when cookies are disabled, PHP's automatic link adjustment doesn't affect the header function, so the session ID gets lost at this point. Fortunately, if PHP identifies that cookies are disabled, it creates a constant, named SID, that contains a query string to pass on the session ID. We can make our code compatible with disabled cookie support as follows:

```
```php
if ($buy != "") {
    // Add item to the end of the $shoppingcart array
    $shoppingcart[] = $buy;
    header("Location: $PHP_SELF" . SID);
    exit();
}
```
```

All that's left is to add a 'view your cart' link to the appropriate page, and we'll have completed the catalog script. Here is the complete code for this page (it's also available in the code archive located at http://www.sitepoint.com/books/).