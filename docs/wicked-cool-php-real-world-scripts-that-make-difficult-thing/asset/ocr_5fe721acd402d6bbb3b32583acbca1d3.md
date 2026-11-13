Accessing and storing cookies in PHP involve two separate mechanisms.
You can read cookies that the client sends to you through the $_COOKIE array.
This works like the $_POST and $_GET arrays.

To set cookies, use the setcookie() function, which has three required parameters:

+   - The cookie name. This script uses stored_user_name.
+   - The cookie value.
+   - When the cookie should expire on the user’s computer, as a Unix timestamp. This script uses time()+604800—seven days from the current time (see Chapter 6 for more detail on timestamps).

There are also three optional parameters:

# A path to limit the places on your site where this cookie is valid.

This works like a directory; for example, if you want the cookie to be valid only for everything under /content/ on your site, use /content/ as this parameter. If you want the cookie to be valid everywhere on your site, use /.

# A domain where the cookie is valid.

Let’s say that you have www.example.com and sales.example.com hosts, and you want the cookie to be valid for both. To achieve this, use .example.com as the domain parameter. Don’t bother with this if you have only one webserver host in your domain.

# A setting for secure connections.

Using 1 as this parameter specifies that the browser should send the cookie only if the connection is secure.

# What Can Go Wrong?

There are a number of problems that frequently occur when setting and retrieving cookies:

# You sent data to the user’s browser before calling setcookie().

Cookie request information is in the HTTP header of a response from a webserver. Therefore, you can’t send any real document data to the client before you call setcookie(), that is, no printing or other operations that cause output. With warnings turned on, PHP tells you when you’ve made this mistake.

A common cause of this problem is being sloppy about whitespace in your PHP files. If you have any blank lines or spaces before the <? that starts the PHP code section, this problem will happen. This situation also applies to any files that you include before calling setcookie(); furthermore, included files can’t have any whitespace after the closing ?> marker.

# The user’s browser rejects the cookie.

If the browser doesn’t accept the cookie, you won’t get any feedback. To check for a cookie, use isset() to see if there is anything in the $_COOKIE[] array slot. The most common cause of a browser rejecting a cookie is an