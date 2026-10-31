
```
reset($cart->items);
while (list($row
```
```
print table_row(
    submit_field("recalc","Recalculate")
        .end_form()
    ,
    //keep shopping is defined in the functions.php file
    keep_shopping($category_id,$product_id)
);
print end_table();
```

## CHECKOUT.PHP

Now, finally, it’s time to check out. Note that this is really the only file that needs to be on the secure server. There’s no need for the catalog portions or even the cart page to be on a secure server, because there’s really no information that needs to be protected. However, on this page we’re going to be accepting credit card information.

Once again, there are extensive comments within the script to help you get through the page’s logic.

```
include "header.php";

// if a session ID has been passed in, use it
if (isset($sessid)) { session_id($sessid); }

// get the session variables for the shopping cart and the user's email address
session_register("cart");
session_register("email");

// if a value for 'email' was posted to the script from a form, use that
// in preference to the session variable
if (!empty($HTTP_POST_VARS["email"])) { $email = $HTTP_POST_VARS["email"]; }

// set up variables defining the values of the buttons of the form
// (defining the values once helps avoid errors caused by spelling problems.)
$order_button = "ORDER NOW!";
$info_button = "Get My Info";

if (!is_object($cart))
{
    // if $cart isn't an Order class object (defined in order_class.php),
    // we're not going to do much - the shopping cart will have no
```
// items in it. initialize it as one anyway, to keep the script from
    // breaking.
    $cart = new Order;
}

// load any posted variables into the cart using the Construct()
// method of the Base class (defined in cart_base_class.php).
$cart->Construct($HTTP_POST_VARS);

if (!empty($zapthis) && is_array($zapthis))
{
    // if multiple addresses were found for the user from past orders,
    // the user can ask to have one or more of the addresses removed
    // from the database. this is done by checking HTML checkbox fields
    // named "zapthis[]", set to the ID values of the addresses.
    // if at least one of the checkboxes was set, PHP will return
    // the values in array variable $zapthis. (if no checkboxes
    // are checked, $zapthis is not necessarily empty, but it
    // will not be an array.)
    while (list($aid) = each($zapthis))
    {
        // delete the address records using the DeleteAddress()
        // method of the Address class (defined in address_class.php)
        $cart->DeleteAddress($aid);
    }
}
if (!empty($usethis))
{
    // if multiple addresses were found for the user from past orders,
    // the user can ask to use one of them for this order by clicking
    // on a radio button field named "usethis", set to the ID value
    // of the address. if $usethis is set, get the address record
    // for the ID value, using the FetchAddress() method of the
    // Address class.
    if ($cart->FetchAddress($usethis))
    {
        // there is now one and only one address for this order
        $cart->address_count = 1;
    }
}
```
if ($ordernow == $order_button)
{
    // the user hit the big ORDER button. validate their credit
    // card and charge it, using the ValidateCard() and ChargeCard()
    // methods of the Order class.
    if ($cart->ValidateCard() && $cart->ChargeCard())
    {
        // the charge went through - write the order to the
        // database using the SaveOrder() method of the Order class.
        $cart->SaveOrder();

        // redirect the user to the receipt page for a receipt
        // they can print or save to a file, and exit the script.
        //  pass on the ID value of the new order record and
        // the session ID that was passed in to this script.
        header("Location: receipt.php?order_id=$cart->order_id"
            ."&sessid=$sessid"
        );
        exit;
    }
}
elseif ($getdata == $info_button || (empty($cart->user_id) &&
!empty($email)))
{
    // either the user has asked to look up their information in the
    // database, or we don't yet have an ID value for the user but
    // do have an email address. use the LoadUser() method of the
    // User class (defined in user_class.php) to try looking up
    // address information stored for the user from past orders.
    $cart->LoadUser($email);
}

$page_title = "Check Out";
include "start_page.php";

// include the shopping cart form
include "cart_form.php";

// begin the order form. we pass on the session ID value that was
passed
// into this script as a GET-style argument because it makes it
easier
// to see if we're in the right session or not.
print start_form("checkout.php?sessid=$sessid");
```
// store the user ID of the user (if any)
print hidden_field("user_id",$cart->user_id);

print subtitle("User Info");

print start_table();

// display the user's email address, along with the button they
// can use to ask to check the database for address information.
print table_row("<b>Email:</b>",text_field("email",$cart->email,20)
.submit_field("getdata",$info_button)
);

print table_row("<b>First Name:</b>",text_field("firstname",$cart->firstname,40,40));
print table_row("<b>Last Name:</b>",text_field("lastname",$cart->lastname,40,40));

print table_row("");

if ($cart->address_count == 1)
{
    // if we've only got one address, load its properties
    // as properties of the shopping cart. the easy case.
    $cart->Construct(get_object_vars(&$cart->addresses[0]));
}
elseif ($cart->address_count > 1)
{
    // we have more than one possible address from the database
    // for the user. the hard case.
    // begin building an HTML table to display them.
    $useme_cell = start_table(array("border"=>1));

    // begin building a list of address cells
    $useme_row = "";

    // walk through the array of addresses
    while (list($i,) = each($cart->addresses))
    {
        // use a reference to avoid copying the object
        $a = &$cart->addresses[$i];

        // build an HTML table cell containing the address
        // and fields for the user to indicate how they
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
print table_row("<b>Address:</b>",text_field("address",$cart->address,40,40));
print table_row("",text_field("address2",$cart->address2,40,40));
print table_row("<b>City:</b>",text_field("city",$cart->city,40,40));
print table_row("<b>State:</b>",select_field("state",states(),$cart->state));
print table_row("<b>Zip:</b>",text_field("zip",$cart->zip,10,10));
print table_row("<b>Phone:</b>",text_field("phone",$cart->phone,20,20));
```
if (!empty($cart->address_id))
{
    // allow the user to create a new address
    print table_row("", checkbox_field("save_as_new"
            , "yes"
            , "Save this as a new address"
        )
    );
}

print end_table();

// display the available shipping methods
print subtitle("Shipping Info");

print start_table();

print table_row(
    "<b>Shipping Method</b>"
    , table_cell("<b>Per Order</b>",array("align"=>"right"))
    , table_cell("<b>Per Item</b>",array("align"=>"right"))
    , table_cell("<b>Total for This Order</b>",array("align"=>"right"))
);

// if no shipping method has been chosen, use the first one as a default
if (empty($cart->shipping_id)) { $cart->shipping_id = 1; }

// get the list of shipping methods from the database
$result = safe_query("select shipping_id,shipping,per_item,per_order
    from shipping
");
while ($ship = mysql_fetch_object($result))
{
    // calculate the cost of using this method. we use a simplistic
    // system: a fixed cost per order, and a per item charge.
    $shiptotal = $ship->per_order + ($cart->total_quantity * $ship->per_item);

    // display the shipping method with a radio field allowing the
    // user to choose it
```
