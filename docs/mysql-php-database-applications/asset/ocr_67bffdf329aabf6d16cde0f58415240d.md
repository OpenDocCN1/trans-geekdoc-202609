```
{ // calculate the cost of using this method. we use a simplistic
// system: a fixed cost per order, and a per item charge.
$shiptotal = $r['per_order'] + ($order->total_quantity *
$r['per_item']);

// display the shipping method with a radio field allowing the
// user to choose it
print table_row(
radio_field(array(
'name' => 'shipping_id'
. 'value' => $shipping_id
. 'label' => $r['shipping']
. 'match' => $order->shipping_id
))
table_cell(array('value'=>money($r['per_order']),
'align'=>'right'))
. table_cell(array('value'=>money($r['per_item']),
'align'=>'right'))
. table_cell(array('value'=>money($shiptotal),
'align'=>'right'))
);
}
print end_table();

// display payment information
print subtitle('Credit Card Info');

print start_table();

if ($order->error)
{
// if the user tried to place an order and there was an error
// when validating or charging the card, display it here.
print table_row(
table_cell(array(
'style' => 'color:red'
. 'value' => $order->error
. 'colspan'=>2
))
);
$order->error = '';
}

// display a test card number in the form for this example by
default.
```