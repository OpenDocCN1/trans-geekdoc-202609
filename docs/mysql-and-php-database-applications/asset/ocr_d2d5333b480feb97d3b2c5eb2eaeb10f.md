```
print table_row("<b>Credit Card:</b>"
```

```
db_radio_field("cc_type_code","cc_types","cc_type_code","cc_type
    "cc_type_code",$cart->cc_type_code

    )
);
```

```
print table_row("<b>Number:</b>",text_field("cc_number","$cart-
>cc_number,20));
```

```
// set the months array to a list of possible months
for ($i = 1; $i <= 12; $i++) { $months[$i] = $i; }
```

```
// set the years array to a list of plausible years
for ($i = 2000; $i <= 2005; $i++) { $years[$i] = $i; }
```

```
// use January 2001 as a default expiration date
if (empty($cart->cc_exp_mon)) { $cart->cc_exp_mon = 1; }
if (empty($cart->cc_exp_yr)) { $cart->cc_exp_yr = 2001; }
```

```
print table_row("<b>Expires:</b>",
    select_field("cc_exp_mon",$months,$cart->cc_exp_mon)
    .select_field("cc_exp_yr",$years,$cart->cc_exp_yr)
)
print end_table();
```

```
// save the ID of the address used in this order (if any)
print hidden_field("address_id",$cart->address_id);
```

```
// display the order button
print paragraph(submit_field("ordernow",$order_button));
```

```
print end_form();

include "end_page.php";
\?>
```