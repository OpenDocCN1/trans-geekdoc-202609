```
// the charge went through - write the order to the
// database using the SaveOrder() method of the Order class.
$order->write_to_db();

// redirect the user to the receipt page for a receipt
// they can print or save to a file, and exit the script.
// pass on the ID value of the new order record and
// the session ID that was passed in to this script.

$url = 'receipt.php?order_id='
    . $order->order_id
    . '&sessid='
    . session_id()
    ;

// header('Location: $url');
print paragraph(anchor_tag($url, $url));
// exit;
}
}
```

```
print start_page(
    anchor_tag('index.php', "Bag O'Stuff")
    . '<br>&nbsp;<br>Check Out'
);
```

```
print paragraph(
    start_form()
    , submit_field(array('name'=>'reset_order','value'=>'Reset Order Object'))
    , end_form()
);
```

```
// include the shopping cart form
print print_cart($order);
```

```
// begin the order form.
print start_form();
```

```
print hidden_field('sessid', session_id());
```

```
print subtitle('User Info');
// store the IDs of the user and address (if any)
print hidden_field('user_id', $order->user_id);
```