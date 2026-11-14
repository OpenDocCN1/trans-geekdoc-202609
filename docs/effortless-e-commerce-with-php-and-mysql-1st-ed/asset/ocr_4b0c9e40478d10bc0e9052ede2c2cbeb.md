+   5. Require the database connection:
+   
+   `require (MYSQL);`

+   6. Clear the shopping cart:
+   
+   `$r = mysqli_query($dbc, "CALL clear_cart('$uid')");`
+   
+   Now that the order has been completed, the contents of the user's shopping cart should be cleared. This is accomplished by calling the clear_cart() stored procedure.

+   7. Include the script that will send the email:
+   
+   `include('./includes/email_receipt.php');`
+   
+   The email_receipt.php script isn't that complicated, but is verbose enough that it merits standing on its own. It will be created in just a few pages.

+   8. Include the header file:
+   
+   `$page_title = 'Coffee - Checkout - Your Order is Complete';
+   include('./includes/checkout_header.html');`

+   9. Include the view:
+   
+   `include('./views/final.html');`

+   10. Clear the session:
+   
+   `$_SESSION = array();
+   session_destroy();`
+   
+   Clearing the session prevents a second immediate order by the same customer from conflicting with the order just submitted. That may not be a common occurrence, but without this code, if the customer does go back and purchase something else, the existing order ID will be erroneously used.

+   11. Complete the page:
+   
+   `include('./includes/footer.html');
+   ?>`

+   12. Save the file.

# Creating the View File

The view file can be as simple or as complex as you want it to be, just ensure that it's appreciative and communicative. For final.html, stored in the views directory, a couple of messages are printed, providing the customer with the order ID and total, along with an indication of what will happen next (Figure 10.17).

> tip
> 
> You may want to add to the final checkout page an obvious link back to the shopping area.