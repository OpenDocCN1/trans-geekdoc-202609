# Chapter 14: Shopping Cart

```
// add the addresses cells and close the table.
// (note: this somewhat presumes there
// won't be more than two or addresses - the table
// will get unwieldy otherwise.
$useme_cell .= table_row($useme_row);
$useme_cell .= end_table();
```

```
// display the addresses
print_row("".table_cell($useme_cell));
print_row("");
)
```

```
// these fields contain any address information that might have been
// directly entered by the user before the database was searched, or
// the information from an address from the database that has been
// selected by the user. In any case, "these" fields are what will
// be used in the order.
print_row("<b>Address:</b>",.text_field("address",$cart-
>address,40,40);
print_row("<b>Address2:</b>",.text_field("address2",$cart->2,40,40);
print_row("<b>City:</b>",.text_field("city",$cart-
>city,40,40);
print_row("<b>State:</b>",.select_field("state",states($),$cart-
>state));
print_table("<b>Zip:</b>",.text_field("zip",$cart->zip,10,10);
print_row("<b>Phone:</b>",.text_field("phone",$cart-
>phone,20,20));
```