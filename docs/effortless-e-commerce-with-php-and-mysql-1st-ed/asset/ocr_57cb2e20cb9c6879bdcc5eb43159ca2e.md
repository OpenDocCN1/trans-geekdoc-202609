# GOING LIVE

Once you're happy with the site and it's time to go live, here's all you need to do...

+   1. Make sure you have an actual Authorize.net account, associated with your merchant bank.

+   2. Use your actual Authorize.net login ID and transaction key in the gateway_process.php script.

+   3. Set the site to live in the configuration file:

```
$live = true;
```

By changing the value of the $live variable, the site will hide all errors and use the live Authorize.net URL. If you still want to see the errors (for the last round of testing, Step 4), keep $live set to false in the configuration file but set $live equal to true at the top of gateway_process.php.

+   4. Test the site a couple more times, just to be safe.

Unless you go into the Merchant Interface to change your account mode, even a real Authorize.net account begins in test mode. So this round of tests just confirms that your account information is working with the live Authorize.net URL.

+   5. Use the Merchant Interface to take your account live.

+   A. Log in to the Merchant Interface at https://account.authorize.net.
+   B. Click Account in the main toolbar.
+   C. Click General Security Settings > Test Mode.
+   D. Click Turn Test Off.

+   6. Run one or two real transactions, as an extra precaution.

You can test the site by purchasing something inexpensive, just to be safe. Then you can go into the Merchant Interface and quickly void the transaction. (You can easily find the transaction under Search > Unsettled Transactions.)

> **tip**
> 
> Authorize.net, like all payment gateways, completes the processing of all transactions at a particular time each day.