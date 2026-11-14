
```php
$qty = (filter_var($_GET['qty'], FILTER_VALIDATE_INT, array('min_range'
    >= 1))) ? $_GET['qty'] : 1;
$r = mysqli_query($dbc, "CALL add_to_wish_list('$uid', '$sp_type',
    $spid, $qty)");
$r = mysqli_query($dbc, "CALL remove_from_cart('$uid', '$sp_type',
    $spid)");
} elseif (isset($_POST['quantity'])) {
    foreach ($_POST['quantity'] as $sku => $qty) {
        list($sp_type, $spid) = parse_sku($sku);
        if (isset($sp_type, $spid)) {
            $qty = (filter_var($qty, FILTER_VALIDATE_INT, array('min_range'
                >= 0))) ? $qty : 1;
            $r = mysqli_query($dbc, "CALL update_wish_list('$uid',
                '$sp_type', $spid, $qty)");
        }
    }
}
$r = mysqli_query($dbc, "CALL get_wish_list_contents('$uid')");
if (mysqli_num_rows($r) > 0) {
    include('./views/wishlist.html');
} else {
    include('./views/emptylist.html');
}
include('./includes/footer.html');
?>
```

## Creating the Views

The emptyList.html view is used when the customer's wish list is empty (Figure 9-7).

![](img/4f47e47c67bd619ac73250f11c9fc7ce_261_0.png)

Figure 9-7

<!-- box begin -->
<div class="box alt"><div class="left-top-corner"><div class="right-top-corner"><div class="border-top"></div></div></div>
<div class="border-left"><div class="border-right"><div class="inner">
<h2>Your Wish List</h2>
<p>Your wish list is currently empty.</p>
(continues on next page)
</div></div></div><div class="left-bot-corner"><div class="right-bot-corner"><div class="left-border-bot"></div><div class="border-bot"></div></div></div></div></div></div><!-- box end -->

**note**
Of course, the two view files go in the views directory.

The wishlist.html view file displays the wish list in an HTML table. As with the shopping cart, the wish list contents can be altered in a couple of ways:

- Their quantities can be changed.
- Items can be moved to the shopping cart.
- Items can be removed from the wish list.

Unlike the shopping cart page, the wish list does not display an order total or a link to checkout (Figure 9.8). Also, instead of indicating that insufficient quantity of a product is in stock, the wish list will indicate those items that are running low, in the hopes of inducing the customer to purchase the items now (Figure 9.9).

![](img/4f47e47c67bd619ac73250f11c9fc7ce_262_0.png)

Figure 9.8

![](img/4f47e47c67bd619ac73250f11c9fc7ce_262_1.png)

Figure 9.9

<div class="box alt"><div class="left-top-corner"><div class="right-top-corner"><div class="border-top"></div></div></div></div><div class="border-left"><div class="border-right"><div class="inner"><h2>Your Wish List</h2><p>Please use this form to update your wish list. You may change the quantities, move items to your cart for purchasing, or remove items entirely.</p><form action="/wishlist.php" method="POST"><table border="0" cellspacing="8" cellpadding="6"><tr><th align="center">Item</th><th align="center">Quantity</th><th align="right">Price</th><th align="right">Subtotal</th><th align="center">Options</th></tr>

```php
<?php
while ($row = mysqli_fetch_array($r, MYSQLI_ASSOC)) {
	$price = get_just_price($row['price'], $row['sale_price']);
	$subtotal = $price * $row['quantity'];
	echo '<tr>
	<td>'. $row['category'] . ' :: '. $row['name'] . '</td>
	<td align="center"><input type="text" name="quantity[' . $row['sku'] . ']" value="' . $row['quantity'] . '" size="2" /></td>
	<td align="right">$". number_format($price, 2) . '</td>
	<td align="right">$". number_format($subtotal, 2) . '</td>
	<td align="right"><a href="/cart.php?sku='. $row['sku'] .
		'&action=move&qty=' . $row['quantity'] . '">Move to Cart</a><br />
	<a href="/wishlist.php?sku=' . $row['sku'] . '&action=remove">
	Remove from Wish List</a></td>
</tr>';
};
// Check the stock status:
if (($row['stock'] > 0) && ($row['stock'] < 10)) {
	echo '<tr class="error"><td colspan="5" align="center">There are
	only '. $row['stock'] . ' left in stock of the '. $row['name'] . '.</td>
	</tr>';
}
} // End of WHILE loop.
?> </table><p align="center"><input type="submit" value="Update Quantities" class="button" /></form></p></div>
<div><div class="left-bot-corner"><div class="right-bot-corner"><div class="border-bot"></div></div></div>
</div></div>
<!-- box end -->
```

## CALCULATING SHIPPING

A nice feature worth adding to the shopping cart is an indication of how much
the shipping will be. For many customers, the shipping and handling charges
are a significant factor when deciding whether or not to make an online pur-
chase. The shipping cost may be a fixed price or be based upon:

- The total weight of the order
- The distance between the origination and destination
- The physical size of the order (for example, large furniture costs extra)
- The total amount of the sale

This site will use this last criterion.

The first step is to define a function that will calculate the shipping using a formula. As an example, let's say that shipping starts with a base rate, which covers the simple fact that some employee has to be paid to assemble and box the order. Added to that should be an amount that's partly based on the amount of the order: Presumably, as the order total increases, more items are being shipped, but at the same time the site is making more money. Therefore, the bulk of the shipping cost will be proportional to the order total, and that proportion will decrease for larger orders. Here, then, is the function:

```php
function get_shipping($total = 0) {
 // Set the base handling charges:
 $Shipping = 3;
 // Rate is based upon the total:
 if ($total < .10) {
 $rate = .25;
 } elseif ($total < 20) {
 $rate = .20;
 } elseif ($total < 50) {
 $rate = .18;
 } elseif ($total < 100) {
 $rate = .16;
 } else {
 $rate = .15;
 }
 // Calculate the shipping total:
 $Shipping = $Shipping + ($total * $rate);
 // Return the shipping total:
 return number_format($Shipping, 2);
} // End of get_shipping() function.
```

Logically, this function should be defined in the product_functions.inc.php script so that it's available to multiple scripts (such as cart.php and checkout.php, which will be written in the next chapter).

To use this function in cart.php (the wish list does not display a total), add this code before displaying the total (Figure 9.10):

```php
$shipping = get_shipping($total);
$Total += $shipping;
echo '<tr>'
<td colspan="3" align="right"><strong>Shipping &amp; Handling</strong></td>
<td align="right">' . $shipping . '</td>
<td>&nbsp;</td>
</tr>
';
```

| Item | Quantity | Price | Subtotal | Options |
|---|---|---|---|---|
| Mugs:Pretty Flower Coffee Mug | 2 | $5.00 | $10.00 | Move to Wish List Remove from Cart |
| Kona-2 lbs - caf - whole | 3 | $13.00 | $39.00 | Move to Wish List Remove from Cart |
| | | | Shipping & Handling | $11.82 |
| | | | Total | $60.82 |

Figure 9.10

## 10 CHECKING OUT

The next step in the evolution of the *Coffee* site is to incorporate the payment processing system that will allow customers to complete their order. For this project, I’ve chosen Authorize.net as the payment processor. The first several pages of the chapter talk about Authorize.net and walk you through setting up a test account there. Once you have a test account, you can write the entire checkout process.

There are four parts to the checkout process:

- 1. Take and validate the shipping information.
- 2. Take and validate the billing information.
- 3. Process the payment.
- 4. Wrap it up (send an email, create a receipt, and so on).

This chapter probably has the most complicated code of any in the book. But this chapter also conveys the information that many readers need the most, so ample space is dedicated to explaining the code as thoroughly as possible.

## ABOUT AUTHORIZE.NET

Authorize.net is perhaps the largest payment gateway out there and was most certainly one of the first available for e-commerce. How Authorize.net functions is different than PayPal, used in Chapter 6, “Using PayPal.” PayPal fetches monies from customers’ credit cards (or PayPal accounts) and deposits those amounts into _your PayPal account_ (which you can later move to a bank account). By comparison, Authorize.net coordinates with several networked systems to transfer funds from credit cards to _your merchant bank account_. Authorize.net is an agent in the process, a true payment gateway, and when the transaction is completed, the money will automatically be transferred to your bank account. For this reason, you must have a merchant bank account (with an actual bank) that supports the Authorize.net system.

Authorize.net accepts all major credit cards and offers:

- Advanced fraud detection
- PCI DSS compliance
- Support for recurring payments
- International transactions
- An online virtual terminal
- Customer information management
- eCheck acceptance
- Multiple administrators with different permissions
- Good documentation and support

Authorize.net provides what they call the _Merchant Interface_, where you can configure your account, manage transactions, view statements, generate reports, and so forth. This chapter will mention the Merchant Interface a few times, but keep in mind that the Merchant Interface is how a site administrator manages an Authorize.net account, it’s not how the site itself communicates with the payment system.

As with PayPal and many other payment systems, there are multiple ways you can use Authorize.net: _Simple Checkout_, _Server Integration Method_ (SIM), and _Advanced Integration Method_ (AIM). When using the first two, the customer will be taken to the Authorize.net Web site, similar to the PayPal example in Chapter 6. In this chapter, the Advanced Integration Method will be demonstrated instead.

> **tip**
>
> To test Authorize.net, you don’t need an actual merchant account.

> **tip**
>
> Authorize.net has a Verified Merchant Seal image that you can display on your Web site to imply your site’s credibility.

> **tip**
>
> AIM is the Authorize.net recommended system, but requires programming and Web security skills.
