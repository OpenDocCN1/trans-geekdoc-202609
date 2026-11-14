Outside the Web site itself, one recommendation I would make, which Authorize.net also suggests, is that you change your Authorize.net identifying information regularly. This includes the user account password (used to access the Merchant Interface), the login ID, and the transaction key. These values can all easily be changed (in the Merchant Interface). After you change the login ID and transaction ID, only two lines in `gateway_process.php` need to be updated to account for the changes.

Regardless of what payment gateway you use, change the password frequently!

# # Preventing Duplicate Orders

The `billing.php` script can take a few moments to execute, once the form is submitted, because it has to send a request to the gateway and await a response. This extra delay can fool customers into thinking their form was not submitted, causing them to perhaps click the submit button again to "correct" the problem. With the site as written, this won't actually create two orders because the gateway will reject duplicate submissions within a default time period of two minutes. Still, it'd be better to avoid this potential problem entirely. And it'd be better to give an indication to the customer that their order is being processed and that a delay is to be expected. Although this is a valuable approach, I omitted it from the `billing.php` script because it requires JavaScript, and I didn't want to further confuse an already complex system.

You can adjust the Authorize.net duplicate-order time window by setting `x_duplicate_window` to some value in seconds.

When it comes to JavaScript, you can either create your own code or use a framework. I'm comfortable with either approach, but frameworks are so easy to use that I recommend that route for beginners. My current favorite framework of choice (and the favorite of many) is jQuery (www.jquery.com). I like it because it has excellent browser support, is easy to use, and degrades nicely. To update the billing form to use jQuery...

+   1. At the end of billing.html, add:

```
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.4.2/jquery.min.js" type="text/javascript" charset="utf-8"></script>
```

This line will load the jQuery library from Google's API system. There's a potential performance benefit in using the Google-provided version of the jQuery library instead of adding a copy to the site: If the customer has visited another site that also used this same jQuery library from Google, the user's browser won't have to download the library again, thereby improving how quickly your page loads.

Loading JavaScript near the end of the page can help the page to load faster in the Web browser.

+   2. Add a <SCRIPT> block:

```
<script type="text/javascript" charset="utf-8">
</script>
```