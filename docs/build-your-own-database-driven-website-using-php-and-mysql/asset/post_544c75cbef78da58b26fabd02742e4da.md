
automatic login details is deleted before their next visit, they can simply reenter their username and password by hand.

## PHP Sessions

Because of the limitations I've just described, cookies are not appropriate for storing large amounts of information. Also, because of the negative impression that many have of cookies, it's not uncommon for users to disable cookies in their browsers. So if you run an ecommerce Website that uses cookies to store the items in a user's shopping cart as they make their way through your site, this can be a big problem.

Sessions were developed in PHP as the solution to all these issues. Instead of storing all your (possibly large) data as cookies in the Web browser, sessions let you store the data on your Web server. The only thing that's stored on the browser is a single cookie that contains the user's session ID - a variable that PHP watches for on subsequent page requests, and uses to load the stored data that's associated with that session.

Unless configured otherwise, a PHP session works by automatically setting in the user's browser a cookie that contains the session ID - a long string of letters and numbers that serves to uniquely identify that user for the duration of his or her visit to your site. The browser then sends that cookie along with every request for a page from your site, so that PHP can use it to identify which of potentially numerous sessions-in-progress the request belongs to. Using a set of temporary files that are stored on the Web server, PHP keeps track of the variables that have been registered in each session, and their values.

One of the big selling points of PHP sessions is that they also work when cookies are disabled! If PHP detects that cookies are disabled in the user's browser, it will automatically add the session ID as a query string variable on all the relative links on your page, thus passing the session ID onto the next page. Be aware that all of the pages on your site need to be PHP files for this to work, because PHP won't be able to add the session ID to links on non-PHP pages. Also, for this feature to work, session.use_trans_sid must be enabled in your php.ini file (see below), and PHP must be compiled with the --enable-trans-sid option if you're doing it yourself under Linux (or other Unix variants).

Before you can go ahead and use the spiffy session-management features in PHP, you need to ensure that the relevant section of your php.ini file has been set up properly. If you're using a server that belongs to your Web host, it's probably safe to assume this has been done for you. Otherwise, open your php.ini file in a text editor and look for the section marked [session]. Beneath it, you'll find twenty-some options that begin with the word session. Most of them are just fine if left as-is, but here are a few crucial ones you'll want to check:

```
session.save_handler   = files
session.save_path      = C:\\WINDOWS\\TEMP
session.use_cookies    = 1
session.use_trans_sid  = 1
```

session.save_path tells PHP where to create the temporary files used to track sessions. It must be set to a directory that exists on the system, or you'll get ugly error messages when you try to create a session on one of your pages. Under Unix, /tmp is a popular choice. In Windows, you could use C:\\WINDOWS\\TEMP, or some other directory if you prefer (I use D:\\PHP\\SESSIONS). With these adjustments made, restart your Web server software to allow the changes to take effect.

You're now ready to start working with PHP sessions. But before we jump into an example, let's quickly look at the most common session management functions in PHP. To tell PHP to look for a session ID, or to start a new session if none is found, you simply call session_start. If an existing session ID is found when this function is called, PHP restores the variables that belong to that session. Since this function attempts to create a cookie, it must come before any page content is sent to the browser, just as we saw for setcookie above.

```
session_start();
```

To tell PHP that you want a particular variable to be stored in the current session so that it is available to other scripts run in the same session, you must call session_register. For example, the following will store the variable called $pwd in the current session:

```
session_register('pwd');
```

To remove a variable from the current session, you just use session_unregister:

```
session_unregister('pwd');
```

Finally, should you want to end the current session, deleting all registered variables in the process, you can use session_destroy:

```
session_destroy();
```

For more detailed information on these and the other session-management functions in PHP, see the relevant section of the PHP Manual (http://www.php.net/session).

Now that we have these basic functions under our belt, let's put them to work in a simple example.

## A Simple Shopping Cart

This example will consist of two PHP scripts:

- A product catalog, where you can add items to your shopping cart.
- A checkout page, which displays the contents of the user's shopping cart for confirmation.

From the checkout page, the order could then be submitted to a processing system that would handle the details of accepting payment and shipping arrangements. That system is beyond the scope of this book, and will not be discussed here.

Let's start with the list of items we'll have for sale in our online store:

| Item Description | Price |
|------------------|-------|
| Canadian-Australian Dictionary | $24.95 |
| Used Parachute (never opened) | $1,000.00 |
| Songs of the Goldfish (2CD Set) | $19.99 |
| Ending PHP4 (O'Reilly Press) | $34.95 |

All prices are in imaginary dollars.

Now, instead of hard-coding the items, we'll place them in a PHP array and generate the page dynamically. Arrays are created with the built-in PHP function array, by listing the elements to be included in the array as the parameters of the function. Items and their prices would normally be stored in a database, but I'm using this method so we can focus on sessions. You should already know all you need in order to put together a database-driven product catalog, so I'll leave that to you as an exercise.

Here's the code for our dynamically generated product catalog:

```php
<?php
$items = array( "Canadian-Australian Dictionary",
       "Used Parachute (never opened)",
       "Songs of the Goldfish (2CD Set)",
       "Ending PHP4 (O'Reilly Press)");
$prices = array( 24.95, 1000, 19.99, 34.95 );
?>
<table border="1">
<tr>
<th>Item Description</th>
<th>Price</th>
</tr>
<?php
for($i = 0; $i < count($items); $i++) {
    echo("<tr>");
    echo("<td>".$items[$i]."</td>");
    echo("<td>$".number_format($prices[$i],2)."</td>");
    echo("</tr>");
}
?>
</table>
<p>All prices are in imaginary dollars.</p>
```

This code produces the exact same HTML we saw above. The table row for each item is created using a for loop that counts through the $items array (the function count returns the number of items in the array). for loops were introduced on page 47. We also use PHP's built-in number_format function to display the prices with two digits after the decimal point (see http://www.php.net/number_format for more information about this function).

Now, we're going to store the list of items the user placed in their shopping cart in yet another array called $shoppingcart. Because we'll need this variable to persist throughout a user's visit to your site, we'll store it using PHP sessions. Here's the code responsible for all this:

```
$shoppingcart = array();
session_start();
session_register('shoppingcart');
```

This code begins by creating the $shoppingcart variable as an empty array. This will be the initial state of the variable when the user first enters the site. session_start() then either starts a new session (and sets the session ID cookie), or restores the variables registered in the existing session if one exists. In the latter case, our empty $shoppingcart will be overwritten by the version that was stored in the session. Finally, we use session_register to register the $shoppingcart variable to be stored in the current session, if it hasn't been already.

We can now print out the number of items in the user's shopping cart:
`<p>Your shopping cart contains <?=count($shoppingcart)?> items.</p>`
