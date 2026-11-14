```
} else {
    Billing_errors['cc_city'] = 'Please enter your city!';
}
if (preg_match ('/^[A-Z]{2}$/', $_POST['cc_state'])) {
    $cc_state = $_POST['cc_state'];
} else {
    Billing_errors['cc_state'] = 'Please enter your state!';
}
if (preg_match ('/^\d{(5)})(\^\d{(5)}\-\d{(4)})$/', $_POST['cc_zip'])) {
    $cc_zip = $_POST['cc_zip'];
} else {
    Billing_errors['cc_zip'] = 'Please enter your zip code!';
}
```

+   10. If no errors occurred, convert the expiration date to the correct format:

```
if (empty($Billing_errors)) {
    $cc_exp = sprintf("%02d%d", $_POST['cc_exp_month'],
    $_POST['cc_exp_year']);
```

Authorize.net can accept the expiration date in many different formats: MMYY, MM-YY, MMYYYY, MM/YYYY, and so on; this site will submit it as MMYYYY. The year will already be four digits long, but the month could be either one or two digits. To turn the month into a two-digit value, the sprintf() function can be used. Its first argument is the formatting pattern: %02d%d. The %02d will format an integer as two digits, adding extra zeros as necessary. The subsequent %d just represents an integer without any additional formatting. The second and third arguments in this sprintf() call are the values to be used for the two placeholders. The end result will be values like 012011 or 102011.

+   11. Check for an existing order ID in the session:

```
if (isset($_SESSION['order_id'])) {
    $order_id = $_SESSION['order_id'];
    $order_total = $_SESSION['order_total'];
```

The next bit of code needs to create a new order ID, which is to say a new set of records in the orders and order_contents tables. However, the billing form could be submitted more than once, so the script shouldn't automatically call the associated stored procedure to do that.

For example, if the payment gateway said there was a problem with the provided credit card, the customer would correct that information (in the form) and resubmit the form. In such a case, the site should not create a second, duplicate order. To prevent that from happening, the script will