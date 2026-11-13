
Now, the user's shopping cart is going to stay very empty if we don't provide a way for them to add items to it, so let's modify the for loop that displays our table of items, and enable it to provide a 'Buy' link on the end of each row:

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

Now each product in our catalog has a link back to the catalog with buy=n in the query string, where n is the index of the item that's to be added to the shopping cart in the $items array. We can then watch for the $buy variable to appear at the top of the page, and when it does, we'll add the item to the $shoppingcart array before redirecting the browser back to the same page, but with no query string (to ensure that refreshing the page doesn't repeatedly add the item to the cart).

```php
if ($buy != "") {
    // Add item to the end of the $shoppingcart array
    $shoppingcart[] = $buy;
    header("Location: $PHP_SELF");
    exit();
}
```

Now, this works just fine if the user has cookies enabled, but when cookies are disabled, PHP's automatic link adjustment doesn't affect the header function, so the session ID gets lost at this point. Fortunately, if PHP identifies that cookies are disabled, it creates a constant, named SID, that contains a query string to pass on the session ID. We can make our code compatible with disabled cookie support as follows:

```php
if ($buy != "") {
    // Add item to the end of the $shoppingcart array
    $shoppingcart[] = $buy;
    header("Location: $PHP_SELF" . SID);
    exit();
}
```

All that's left is to add a 'view your cart' link to the appropriate page, and we'll have completed the catalog script. Here is the complete code for this page (it's also available in the code archive located at http://www.sitepoint.com/books/):

```php
<?php
$shoppingcart = array();
session_start();
session_register('shoppingcart');
if ($buy != "") {
	// Add item to the end of the $shoppingcart array
	$shoppingcart[] = $buy;
	header("Location: $PHP_SELF?".SID);
	exit();
}
?>
<html>
<head>
<title>Product catalog</title>
</head>
<body bgcolor="#FFFFFF" text="#000000">
<p>Your shopping cart contains <?=count($shoppingcart)?>
items.</p>
<p><a href="cart.php">View your cart</a></p>
<?php
$items = array ("Canadian-Australian Dictionary",
	"Used Parachute (never opened)",
	"Songs of the Goldfish (2CD Set)",
	"Ending PHP4 (O'Reilly Press)");
$prices = array( 24.95, 1000, 19.99, 34.95 );
?>
<table border="1">
<tr>
	<th>Item Description</th>
	<th>Price</th>
</tr>
<?php
for($i = 0; $i < count($items); $i++) {
	echo("<tr>");
	echo("<td>".$items[$i]."</td>");
	echo("<td>$".number_format($prices[$i],2)."</td>");
	echo("<td><a href='$PHP_SELF?buy=$i'>Buy</a></td>");
	echo("</tr>");
}
?>
</table>
<p>All prices are in imaginary dollars.</p>
</body>
</html>
```

Now the code for cart.php is very similar to the product catalog. All it does is take the $shoppingcart variable (after loading the session of course), and use the numbers stored there to print out the corresponding items from the $items array. We also provide a link that loads the page with query string empty=1, and causes the script to session_unregister the $shoppingcart variable, which results in a new, empty shopping cart. Here's the code (also available in the code archive located at http://www.sitepoint.com/books/):

```php
<?php
$shoppingcart = array();
session_start();
session_register('shoppingcart');
if ($empty != "") {
    session_unregister("shoppingcart");
    header("Location: $PHP_SELF?".SID);
    exit();
}
?>
<html>
<head>
<title>Shopping cart</title>
</head>
<body bgcolor="#FFFFFF" text="#000000">
<h1>Your Shopping Cart</h1>
<?php
$items = array( "Canadian-Australian Dictionary",
    "Used Parachute (never opened)",
    "Songs of the Goldfish (2CD Set)",
    "Ending PHP4 (O'Reilly Press)");
$prices = array( 24.95, 1000, 19.99, 34.95 );
?>
<table border="1">
<tr>
    <th>Item Description</th>
    <th>Price</th>
</tr>
<?php
for($i = 0; $i < count($shoppingcart); $i++) {
    echo("<tr>");
    echo("<td>".$items[$shoppingcart[$i]]."</td>");
    echo("<td align=\"right\">$");
    echo(number_format($prices[$shoppingcart[$i]],2));
    echo("</td>");
    echo("</tr>");
    $total = $total + $prices[$shoppingcart[$i]];
}
?>
<tr>
<th align="right">Total:<br>
<th align="right"><?=number_format($total,2)?></th>
</tr>
</table>
<p>
<a href="catalog.php">Continue Shopping</a> or
<a href="<?=$PHP_SELF?>?empty=1">Empty your cart</a></p>
</body>
</html>
```

## Summary

In this chapter, you learned about the two main methods of creating persistent variables - those variables that continue to exist from page to page in PHP. The first stores the variable in the visitor's browser in the form of a cookie. By default, cookies terminate at the end of the browser session, but by specifying an expiry time, they can be preserved indefinitely. Unfortunately, cookies are fairly unreliable because you have no way of knowing when the browser might delete your cookies, and because some users configure their browsers to disable cookies. Obviously cookies are not something that should be relied upon.

Sessions, on the other hand, free you from all the limitations of cookies. They don't rely on cookies to work, and they let you store an unlimited number of potentially large variables. Sessions are an essential building block in modern ecommerce applications, as we demonstrated in our simple shopping cart example.

## Wrap-Up

And so the great adventure draws to an end. In these pages, we have explored the MySQL RDBMS and the PHP scripting language, two products that together provide everything needed to launch a database-driven Website with all the capabilities and administrative (not to mention financial!) benefits that stem from it.

As I wrote this book, a lot of readers wrote -- both in the SitePoint.com Forums and in private emails -- to encourage me, provide suggestions, ask lots of questions, and thank me for taking what has always seemed like a rather daunting subject and making it into something approachable and (dare I say it?) fun. While your words are all greatly appreciated (this book would not have been what it is without the level of support I have had from its readers!), I'd like to take this opportunity to thank the people who worked to create MySQL and PHP. These two products, free for personal use, together continue the long tradition of letting just about anyone project as professional and polished presence on the Internet as any big company.

A project like this is never undertaken entirely alone. I'd like to thank Mark Harbottle, Matt Mickiewicz, and Jason Donald, Co-founders of SitePoint.com for their support in this endeavor (would you believe it was their idea?). Thanks also must go to my best friend, Amy Mathieson, who didn't mind that I came all the way to Australia to visit her and spent most of my time working on this, to her sister Lisa Mathieson, who let me use her computer during my stay, and to my good friends Tony and Helen Terbizan, who provided me with an Internet connection, as well as more than one gourmet dinner!

Finally, I must thank Georgina Laidlaw, who helped add some of the spit and polish to this second edition. Her patience and dedication were much appreciated, and will help to ensure that this remains the definitive introductory tutorial for PHP and MySQL.

If you enjoyed this book, I'd encourage you to post a message on the SitePoint Forums (www.sitepointforums.com) or drop an email message in my inbox (kevin@sitepoint.com). With this major project complete, SitePoint.com will doubtless be looking for another. Let us know what you'd like to learn next!

Thanks for reading, and see you soon!

-Kevin Yank.

Montreal, June 2001.
