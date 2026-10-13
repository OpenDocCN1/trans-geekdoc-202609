
These next two examples will provide all the necessary functionality for the shopping cart. The first script, `add_cart.php`, is used to add items to the shopping cart. The second, `view_cart.php`, both displays the contents of the cart and allows the customer to update the cart.

### Adding items

The `add_cart.php` script will take one argument—the ID of the print being purchased—and will use this information to update the cart. The cart itself is stored in a session, accessed through the `$_SESSION['cart']` variable. The cart will be a multidimensional array whose keys will be product IDs. The values of the array elements will themselves be arrays: one element for the quantity and another for the price (Table 19.6).

**Table 19.6. Sample `$_SESSION['cart']` Values**

![Image](graphics/19tab06.jpg)

### To create add_cart.php

**1.** Begin a new PHP document in your text editor or IDE, to be named `add_cart.php` (Script 19.9):

```php
<?php # Script 19.9 - add_cart.php

$page_title = 'Add to Cart';

include ('includes/header.html');
```

**2.** Check that a print ID was passed to this script:

```php
if (isset ($_GET['pid']) && filter_var($_GET['pid'], FILTER_VALIDATE_INT, array('min_range' => 1))) {

    $pid = $_GET['pid'];
```

As with the `view_print.php` script, the script should not proceed if no, or a non-numeric, print ID has been received. If one has been received, then its value is assigned to `$pid`, to be used later in the script.

**3.** Determine if a copy of this print had already been added to the cart:

```php
if (isset($_SESSION['cart'][$pid])) {

    $_SESSION['cart'][$pid]['quantity']++;

    echo '<p>Another copy of the print has been added to your shopping cart.</p>';
```

Before adding the current print to the shopping cart (by setting its quantity to 1), check if a copy is already in the cart. For example, if the customer selected print #519 and then decided to add another, the cart should now contain two copies of the print. The script therefore first checks if the cart has a value for the current print ID. If so, the quantity is incremented. The code `$_SESSION['cart'][$pid]['quantity']++` is the same as

```php
$_SESSION['cart'][$pid]['quantity'] = $_SESSION['cart'][$pid]['quantity'] + 1.
```

Finally, a message is displayed ![Image](graphics/circle-a.jpg).

![Image](graphics/19_figure_29_a.jpg)

![Image](graphics/circle-a.jpg) The result after clicking an *Add to Cart* link for an item that was already present in the shopping cart.

**4.** If the product is not already in the cart, retrieve its price from the database:

```php
} else { // New product to the cart.

    require ('../mysqli_connect.php');

    $q = "SELECT price FROM prints WHERE print_id=$pid";

    $r = mysqli_query ($dbc, $q);

    if (mysqli_num_rows($r) == 1) {

        list($price) = mysqli_fetch_array ($r, MYSQLI_NUM);
```

If the product is not currently in the cart, this `else` clause comes into play. Here, the print's price is retrieved from the database using the print ID.

**5.** Add the new product to the cart:

```php
$_SESSION['cart'][$pid] = array ('quantity' => 1, 'price' => $price);

echo '<p>The print has been added to your shopping cart.</p>';
```

After retrieving the item's price, a new element is added to the `$_SESSION['cart']` multidimensional array. Since each element in `$_SESSION['cart']` is itself an array, use the `array()` function to set the quantity and price. A simple message is then displayed ![Image](graphics/circle-b.jpg).

![Image](graphics/19_figure_30_b.jpg)

![Image](graphics/circle-b.jpg) The result after adding a new item to the shopping cart.

**6.** Complete the conditionals:

```php
        } else { // Not a valid print ID.

            echo '<div align="center"> This page has been accessed in error!</div>';

        }

        mysqli_close($dbc);

    } // End of isset($_SESSION['cart'][$pid] conditional.

} else { // No print ID.

    echo '<div align="center">This page has been accessed in error!</div>';

}
```

The first `else` applies if no price could be retrieved from the database, meaning that the submitted print ID is invalid. The second `else` applies if no print ID, or a non-numeric one, is received by this page. In both cases, an error message will be displayed ![Image](graphics/circle-c.jpg).

![Image](graphics/19_figure_31_c.jpg)

![Image](graphics/circle-c.jpg) The `add_cart.php` page will only add an item to the shopping cart if the page received a valid print ID in the URL.

**7.** Include the HTML footer and complete the PHP page:

```php
include ('includes/footer.html');

?>
```

**8.** Save the file as `add_cart.php`, place it in your Web directory, and test it in your Web browser (by clicking an *Add to Cart* link).

***

> **Tip**
>
> The most important thing to store in the cart is the unique product ID and the quantity of that item. Everything else, including the price, can be retrieved from the database. Alternatively, you could retrieve the price, print name, and artist name from the database, and store all that in the session so that it's easily displayed anywhere on the site.

***

> **Tip**
>
> The shopping cart is stored in `$_SESSION['cart']`, not just `$_SESSION`. Presumably other information, like the user's ID from the database, would also be stored in `$_SESSION`.

***

### Viewing the shopping cart

The `view_cart.php` script will be more complicated than `add_cart.php` because it serves two purposes. First, it will display the contents of the cart in detail ![Image](graphics/circle-d.jpg). Second, it will give the customer the option of updating the cart by changing the quantities of the items therein (or deleting an item by making its quantity 0). To fulfill both roles, the cart's contents will be displayed in a form that gets submitted back to this same page.

![Image](graphics/19_figure_32_d.jpg)

![Image](graphics/circle-d.jpg) The shopping cart displayed as a form where the specific quantities can be changed.

Finally, this page will link to a `checkout.php` script, intended as the first step in the checkout process.

### To create view_cart.php

**1.** Begin a new PHP document in your text editor or IDE, to be named `view_cart.php` (Script 19.10):

```php
<?php # Script 19.10 - view_cart.php

$page_title = 'View Your Shopping Cart';

include ('includes/header.html');
```

**Script 19.10.** The `view_cart.php` script both displays the contents of the shopping cart and allows the user to update the cart's contents.

***

```php
1   <?php # Script 19.10 - view_cart.php
2   // This page displays the contents of
        the shopping cart.
3   // This page also lets the user update
        the contents of the cart.
4
5   // Set the page title and include the
        HTML header:
6   $page_title = 'View Your Shopping Cart';
7   include ('includes/header.html');
8
9   // Check if the form has been submitted
        (to update the cart):
10  if ($_SERVER['REQUEST_METHOD'] == 'POST')
{
11
12      // Change any quantities:
13      foreach ($_POST['qty'] as $k => $v) {
14
15          // Must be integers!
16          $pid = (int) $k;
17          $qty = (int) $v;
18
19          if ( $qty == 0 ) { // Delete.
20              unset ($_SESSION['cart'][$pid]);
21          } elseif ( $qty > 0 ) { // Change
                quantity.
22              $_SESSION['cart'][$pid]
                    ['quantity'] = $qty;
23          }
24
25      } // End of FOREACH.
26
27  } // End of SUBMITTED IF.
28
29  // Display the cart if it's not empty...
30  if (!empty($_SESSION['cart'])) {
31
32      // Retrieve all of the information for the prints in the cart:
33      require ('../mysqli_connect.php'); // Connect to the database.
```
