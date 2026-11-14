# # TESTING THE SITE

With all the code written, you can fully test the site. You could use your own information—including credit card data—to test the payment gateway, but that's not the best of ideas. Here are syntactically valid, test credit card numbers:

+   - 370000000000002, American Express
+   - 6011000000000012, Discover
+   - 555555555554444, MasterCard
+   - 4007000000027, Visa

**tip**

In January, the site won't accept an expiration date in the past because the year would have to be the previous year, which isn't an option.

Those numbers will work, regardless of the address and CVV values used with them. If you want to make them fail, one option is to use an expiration date in the past.

Authorize.net has its own method for triggering specific responses. If you use the faux-Visa number 4222222222222222, the `amount` value can trigger a specific error response. For example, the response reason code of 6 means the credit card number is invalid. If you process a test transaction using that Visa number and an amount of 6.00, the returned response will be that the transaction was declined because of an invalid credit card number.

Because the amount used in the payment process is not an editable, dynamic value (which, for security purposes, is for the best), you'll have to manually alter the `gateway_process.php` script accordingly:

```
$data['x_amount'] = 6.00;
```

You also need to add this parameter:

```
$data['x_test_request'] = 'TRUE';
```

You should know that when you use the `x_test_request` setting, the returned transaction ID will always be zero. This is not a mistake.