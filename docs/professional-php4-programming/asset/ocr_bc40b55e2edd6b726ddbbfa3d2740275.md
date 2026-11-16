# setcookie()

```
int setcookie(string cookiename [, string value] [, integer lifetime]
[, string path] [, string domain] [, integer secure])
```

+   **cookiename**
+   The name of the cookie to set, the value of which will be accessible in all pages under the specified scope; in PHP scripts specifically as $cookiename.

+   **value**
+   The value stored in the cookie named cookiename, referenced in PHP with the variable name $cookiename.

+   **lifetime**
+   The time in seconds since the epoch (the 1<sup>st</sup> of January 1970) at which this cookie will be no longer valid.

+   **path**
+   The root path at which the cookie is accessible. This path is recursive and any subdirectories are also able access the cookie, unless set specifically to a filename. Note that, even if the path is set to /path/to/filename.php, someone could create a script at /path/to/filename.php-directory/evil-script.php and access the cookie information.

+   **domain**
+   The domain from which the cookie is accessible.

+   **secure**
+   This directive sets whether or not the cookie is accessible outside of HTTPS requests. This value is defaulted to 0, meaning that regular HTTP requests can access the cookie data.

If we omit setting a value for the cookie, it will be deleted. The first variable we provide to the function is the name of the cookie; the second variable is the value assigned to that name, thus giving the name=value pair that we expect from the cookie.

The setcookie() function is fragile, in that the cookie must be set before any headers are sent to the browser, and in this respect it is similar to PHPs header() function, which will fail if any headers have already been sent. This failure results from the fact that cookies are set as headers.

Let's understand this further, by modifying the above code for a user access counter:

```
Putting text here will force a header of Content-type: text/html to be sent,
causing the cookie to result in error. '

<?php
$accesses++;
setcookie("accesses", $accesses);
?>

<html>
Thank you for visiting my site. You've seen this page
<?php
echo($accesses);
if ($accesses == 1) {
```