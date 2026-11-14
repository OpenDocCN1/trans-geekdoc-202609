+   - the quantities, move items to your wish list for future purchasing, or
+   - remove items entirely. The shipping and handling cost is based upon
+   - the order total. When you are ready to complete your purchase, please
+   - click Checkout to be taken to a secure page for processing.</p>

For the instructions on the cart page, you'll need to strike a balance between being informative and not being too busy. Remember that the primary purpose of the cart page is to get the customer to check out!

# 3. Begin the form:

```
<form action="/cart.php" method="POST">
```

The form is submitted back to cart.php and uses the POST method. The action value starts with a slash to indicate that cart.php is in the Web root directory. The slash isn't absolutely required for the cart.php script, but is required with many other links and references used by the site, so it's here for consistency.

# 4. Begin the table:

```
<table border="0" cellspacing="8" cellpadding="6">
<tr>
<th align="center">Item</th>
<th align="center">Quantity</th>
<th align="right">Price</th>
<th align="right">Subtotal</th>
<th align="center">Options</th>
</tr>
```

In an old-school way, I'm using a standard HTML table to display the cart's contents. There are five columns in the table.

# 5. Begin a PHP block:

```
<?php
$total = 0;
```

Within the PHP block, the total variable is initialized to zero, so that a proper order total can be calculated.

# 6. Fetch each item:

```
while ($row = mysqli_fetch_array($r, MYSQLI_ASSOC)) {
$price = get_just_price($row['price'], $row['sale_price']);
$subtotal = $price * $row['quantity'];
```

Within the loop, the item's price is first determined by passing the regular and sale prices to the get_just_price() function. Then a subtotal is calculated by multiplying the price times the quantity in the cart.

![](bbox=[0.71, 0.77, 0.81, 0.82])

> For security purposes, the price is always coming from the database; it's not possible for the customer to manipulate it.