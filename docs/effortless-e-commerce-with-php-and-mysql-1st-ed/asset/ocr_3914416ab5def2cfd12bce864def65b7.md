# # Creating the PHP Script

The PHP script should be accessed at least twice: originally as a GET request, at which point the form should be loaded, and as a POST request, when the form is submitted. The latter action demands about 100 lines of validation, which is the bulk of the script.

Unlike the shopping area of the Web site, the checkout process will use PHP sessions. This is necessary because multiple scripts will all need access to some of the same information. By default, PHP will store the session identifier in a cookie. You might not be aware of this, but with respect to cookies, http://www.example.com and https://www.example.com are separate realms, meaning that a cookie sent over HTTP is available only to pages accessed via HTTP (and the same goes for HTTPS). I mention this now, because the sessions used by the checkout process will not be available on the shopping side of the site, and the cookie used on the shopping side of the site is not available in the checkout process.

> > **tip**
> 
> The .htaccess modifications in Chapter 7, “Second Site: Structure and Design,” ensure that checkout.php is accessible only over HTTPS.

+   1. Create a new PHP script in your text editor or IDE to be named checkout.php and stored in the Web root directory.

> > **tip**
> 
> When the user returns to the shopping side of the site, the wish list and cart cookie will still be usable, even after checking out.

+   2. Include the configuration file:

```
```php
<?php
require('./includes/config.inc.php');
```
```

+   3. Check for the user's cart ID, available in the URL:

```
```php
if ($_SERVER['REQUEST_METHOD'] == 'GET') {
    if (isset($_GET['session])) {
        $uid = $_GET['session'];
    }
```
```

In order to access the customer's shopping cart, this script needs the user's shopping cart session ID, stored in a cookie in the user's browser. However, that cookie was sent over HTTP, meaning that it's not available to checkout.php, because this script is being accessed via HTTPS. The remedy is to pass the cookie value to this script when the user clicks the checkout button on cart.php. This script first confirms that a session value was passed along in the URL. If so, it's assigned to the $uid variable for later use.

+   4. Use the cart ID as the session ID, and begin the session:

```
```php
session_id($uid);
session_start();
```
```

The shopping part of the site purposefully does not use sessions (in order to give longevity to the customer's cart and wish list), but the checkout process will. For continuity, and because the shopping cart ID will be