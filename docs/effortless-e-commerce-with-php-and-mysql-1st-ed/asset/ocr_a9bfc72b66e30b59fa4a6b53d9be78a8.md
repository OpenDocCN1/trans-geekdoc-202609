# # CREATING CHECKOUT.HTML

The checkout.html view file is included by checkout.php. It must include checkout_cart.html and then display the form for obtaining the customer's shipping information (Figure 10.12).

![](bbox=[0.067, 0.216, 0.356, 0.513])

Figure 10.12

+   1. Create a new HTML page in your text editor or IDE to be named checkout.html and stored in the views directory.

+   2. Add the progress indicator:

```
<div align="center"><img src="/images/checkout_indicator1.png" />
</div>
<br clear="all" />
```

To make the checkout process clear to the customer, and where they are in that process, a progress indicator or progress tracker will be used (see Figure 10.3).

+   3. Include the checkout_cart.html view:

```
<?php include ('./views/checkout_cart.html'); ?>
```

This includes the script just created. The file reference is relative to checkout.php, which is including this checkout.html view file (which is why the code is ./views/checkout_cart.html instead of just checkout_cart.html).