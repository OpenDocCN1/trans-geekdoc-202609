
## Disadvantages

- Sessions are normally specific to one browser window or one browser process. When you close that window, unless you store the session ID as a persistent cookie, the user won’t get the old data back. However, with a login system, you can associate a session ID with a username.
- Out of the box on PHP, sessions are server specific. If you have a sales server and a content server, the sales server won’t see any session data from the content server. You can customize the session storage system to solve this problem.
- Because the session ID is data that a user reads and sends, unless you take precautions, it’s possible for snoopers to get access to sessions.

In abstract terms, you can think of sessions as enhanced cookies. There’s still certain data (such as the session ID) that the user’s computer gets in some way, but the real data is always on your server. There are many different implementations of session technology, but the basic idea is always the same. Remember, though, if there’s some data that you don’t want users to read or modify, you should put it in a session, not a cookie. You need to do the same verification process for cookies that you would for any form data, because it comes from the client and therefore is easy to fabricate.

## #56: Creating a “Welcome Back, Username!” Message with Cookies

One cheap parlor trick that many websites employ is displaying “Welcome back” to returning users. If you tell the site your name, it can greet you by name.

To illustrate one way to do this, here is a script that can store user information in a cookie and display the cookie if available:

```php
<?php
if (isset($_REQUEST["user_name"])) {
    setcookie("stored_user_name", $_REQUEST["user_name"], time() + 604800, "/");
    $_COOKIE["stored_user_name"] = $_REQUEST["user_name"];
}
if (isset($_COOKIE["stored_user_name"])) {
    $user = $_COOKIE["stored_user_name"];
    print "Welcome back, <b><?=$user?></b>";
} else {
?>
<form method="post">
User name: <input type="text" name="user_name" />
</form>
<?php
}
```

Accessing and storing cookies in PHP involve two separate mechanisms. You can read cookies that the client sends to you through the $_COOKIE array. This works like the $_POST and $_GET arrays.

To set cookies, use the setcookie() function, which has three required parameters:

- The cookie name. This script uses stored_user_name.
- The cookie value.
- When the cookie should expire on the user’s computer, as a Unix timestamp. This script uses time()+604800—seven days from the current time (see Chapter 6 for more detail on timestamps).

There are also three optional parameters:

- A path to limit the places on your site where this cookie is valid. This works like a directory; for example, if you want the cookie to be valid only for everything under /content/ on your site, use /content/ as this parameter. If you want the cookie to be valid everywhere on your site, use /.
- A domain where the cookie is valid. Let’s say that you have www.example.com and sales.example.com hosts, and you want the cookie to be valid for both. To achieve this, use .example.com as the domain parameter. Don’t bother with this if you have only one webserver host in your domain.
- A setting for secure connections. Using 1 as this parameter specifies that the browser should send the cookie only if the connection is secure.

### What Can Go Wrong?

There are a number of problems that frequently occur when setting and retrieving cookies:

- You sent data to the user’s browser before calling setcookie(). Cookie request information is in the HTTP header of a response from a webserver. Therefore, you can’t send any real document data to the client before you call setcookie(), that is, no printing or other operations that cause output. With warnings turned on, PHP tells you when you’ve made this mistake.

  A common cause of this problem is being sloppy about whitespace in your PHP files. If you have any blank lines or spaces before the <? that starts the PHP code section, this problem will happen. This situation also applies to any files that you include before calling setcookie(); furthermore, included files can’t have any whitespace after the closing ?> marker.

- The user’s browser rejects the cookie. If the browser doesn’t accept the cookie, you won’t get any feedback. To check for a cookie, use isset() to see if there is anything in the $_COOKIE[] array slot. The most common cause of a browser rejecting a cookie is an incorrect domain (browsers typically do not accept cookies for domains that don’t match the requesting server host).

- **Someone throws in a bad parameter.** Cookies, like anything else that the client sends you, are easily fabricated. Don’t trust their values; verify them just as you would any form data.

- **You're trying to store an array in a cookie variable.** You can’t do that. You can, however, use a serialized array (see “#5: Turning an Array into a Nonarray Variable That Can Be Restored Later” on page 12).

## #57: Using Sessions to Temporarily Store Data

A fairly common user interface design has a user entering a fairly extensive amount of data over several forms. You also may want to store a set of data for as long as the user’s browser is open (for example, for a shopping cart). Though this is technically possible with hidden form fields, it’s not desirable in most cases because of its complexity and browser-state problems.

PHP has a built-in *session management* system that you can use to store and access data on a per-browser basis. It does most of the dirty work of setting cookies (or setting a session ID parameter) and storing the data somewhere on your server. All you need to do in your PHP scripts is start the session manager with the *session_start()* function and then access session data with the $_SESSION array.

Here’s a form that uses session management to capture, summarize, and edit data. Let’s start with a simple form script. The first part starts the session and extracts existing session data:

```php
<?
session_start();

$name = $_SESSION["name"];
$color = $_SESSION["color"];
?>
```

New users won’t have these variables set, but if they return to this form at any point, this part of the script captures their old values. When printing the form, we use those old values as defaults:

```php
print '<form action="sessionview.php" method="post">';
print 'What is your name? ';
print '<input name="name" type="text" value="" . $name . " " /><br/>';
print 'What is your favorite color? ';
print '<input name="color" type="text" value="" . $color . " " /><br/>';
print '<input type="submit" />';
print '<input type="submit" name="clear" value="Clear Details" />';
?>
```

Notice that there is an extra submit button for clearing session values (you'll see how this works soon). Here's the sessionview.php script that stores the form data and gives the user the opportunity to go back and edit the values. First, we start the session and check to see if the name and/or color have been sent as form data. If they have, we set those values as session variables:

```php
<?
session_start();

if ($_REQUEST["name"]) {
    $_SESSION["name"] = $_REQUEST["name"];
}

if ($_REQUEST["color"]) {
    $_SESSION["color"] = $_REQUEST["color"];
}
?>
```

The next part checks to see if the user pressed the Clear Details button on the form. If this is the case, then we use unset() to clear the session values:

```php
if ($_REQUEST["clear"]) {
    unset($_SESSION["name"]);
    unset($_SESSION["color"]);
}
```

Now we know that the $_SESSION array contains all of the correct values, so we can print the user's information based on those values:

```php
$name = $_SESSION["name"];
$color = $_SESSION["color"];

if ($name) {
    print "Your name is <b>$name</b>.<br />";
}
if ($color) {
    print "Your favorite color is <b>$color</b>.<br />";
}
```

Finally, we give the user a chance to go back and edit the details or clear the values. We've done all of the work in our scripts already, so we just need to provide hyperlinks to the correct places:

```php
print ' <a href="sessionform.php">Edit details</a>';
print ' | <a href="sessionview.php?clear=1">Clear values</a>';
?>
```
