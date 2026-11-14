```
include ('./includes/footer.html');
exit();
}
```

This else clause applies if no records were returned by the query.

+   17. Complete the page:

```
include ('./includes/footer.html');
?>
```

+   18. Save the file and test it in your Web browser.

At this point, clicking the submit button will have no effect, however.

# # SHIPPING ORDERS

To complete the view_order.php script, the functionality for processing completed orders has to be integrated. This entire process involves:

+   1. Requesting actual payment for the order
+   2. Recording the payment request transaction in the database.
+   3. Updating the order_contents table
+   4. Updating the catalog inventory
+   5. Reporting upon the results

Although there are many steps, the code itself isn't that complicated, largely thanks to the work that's already been done for the public side of the site. First, though, a script for setting up the payment gateway for administrative purposes must be defined.

# ## Creating gateway_setup_admin.php

In Chapter 10's billing.php, payments are processed by including two files. The first, gateway_setup.php, creates an array of values particular to the public side of the site. This includes, for example, the customer's billing information. Since a payment has already been authorized, the administrative setup script only needs to identify the transaction ID associated with the prior authorization and use a payment request type of PRIOR_AUTH_CAPTURE. Here, then, is the complete gateway_setup_admin.php, which should be stored in a secure location (such as the same place you used for gateway_setup.php):