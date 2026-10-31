```
// would like to use it (if at all), and add the
// cell to the row string.
$useme_row .= table_cell(
    $a->PrintAddress()
    ."<br>"
    .radio_field("usethis"
        , $a->address_id
        , "Use this address"
    )
    ."<br>"
    .checkbox_field("zapthis[]"
        , $a->address_id
        , "Delete this address"
    )
);
}

// add the address cells and close the table.
// (note: this somewhat presumes there
// won't be more than two or three addresses - the table
// will get unwieldy otherwise.)
$useme_cell .= table_row($useme_row);
$useme_cell .= end_table();

// display the addresses
print table_row("",table_cell($useme_cell));
print table_row("");
}

// these fields contain any address information that might have been
// directly entered by the user before the database was searched, or
// the information from an address from the database that has been
// selected by the user. in any case, *these* fields are what will
// be used in the order.
print table_row("<b>Address:</b>",text_field("address",$cart-
>address,40,40));
print table_row("",text_field("address2",$cart->address2,40,40));
print table_row("<b>City:</b>",text_field("city",$cart-
>city,40,40));
print table_row("<b>State:</b>",select_field("state",states(),$cart-
>state));
print table_row("<b>Zip:</b>",text_field("zip",$cart->zip,10,10));
print table_row("<b>Phone:</b>",text_field("phone",$cart-
>phone,20,20));
```