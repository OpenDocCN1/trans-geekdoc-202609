# Chapter 14: Shopping Cart

```
// where $gain is set to "please" in a hidden field. we test
// this, rather than the value of $submit as in other examples,
// so the user can hit the ENTER key after typing in a new
// quantity or checking remove boxes and get a recalculation,
// without actually pressing the 'Recalculate' button.

// for each item in the cart, set its quantity property
// to the corresponding value from the $quantity[] array
// built by PHP from the 'quantity[$row]' fields submitted
// from the form.
$quantity = (array)$quantity;
```

```
reset($cart->items);
while (list($row,) = each($cart->items))
{
    // by adding 0 explicitly, PHP will set the value
    // of the quantity property to at least 0, even if,
    // for some reason, the user has set the field to
    // a blank value.
    $cart->items[$row]->quantity = $quantity[$row] + 0;
}
```

```
$remove = (array)$remove;
while (list($row,$value) = each($remove))
{
    // tag the item for removal by CalculateTotals()
    $cart->items[$row]->killme = $value;
}
```

```
// recalculate the total price for each item in the cart
$cart->CalculateTotals();
```

```
// display the contents of the shopping cart
print start_form();
print hidden_field(array("again=","please"));
```

```
print start_table(array("border=1\));
print table_row("<b>Item</td>"
    "<b>Quantity</td>"
    "<b>Price</td>"
    "<b>Total</td>"
    "<b>Remove</td>");
```