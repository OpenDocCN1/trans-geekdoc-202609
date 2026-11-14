+   8. Include the view files:

```
if (mysqli_num_rows($r) > 0) {
if (isset($_SESSION['shipping_for_billing']) &&
($_SERVER['REQUEST_METHOD'] != 'POST')) {
$Values = 'SESSION';
} else {
$Values = 'POST';
}
}
include ('./views/billing.html');
} else { // Empty cart!
include ('./views/emptycart.html');
}
```

You've seen most of this code several times over by now, the one difference being the conditional that checks for the `$_SESSION['shipping_for_billing']` element. This conditional is necessary because the HTML form in the view file could be prepopulated with values in two situations.

In the first case, the customer selected the check box (on `checkout.php`) to use their shipping information as their billing information. If so, the values already stored in `$_SESSION` should be used for the form elements.

The second situation in which there will be values to display in the form is when the customer submitted the form but errors occurred. If so, the values should come from `$_POST`. Note that even if the user opted to use the same information for shipping and billing, once they've submitted the form, only the posted values will count. This way, if the customer altered any of the prepopulated values, the changes will be reflected when the form is redisplayed. Still, if the customer did not alter the original session-based values, those same values will be used again after any errors.

+   9. Complete the page:
+   
+   include ('./includes/footer.html');
+   
+   ?>

+   10. Save the file.

# Creating the View File

The next step is to create the `billing.html` view file. Like `checkout.html`, this script should include `checkout_cart.html` (to display the cart), and then create an HTML form, primarily using the `create_form_input()` function (Figure 10.15).