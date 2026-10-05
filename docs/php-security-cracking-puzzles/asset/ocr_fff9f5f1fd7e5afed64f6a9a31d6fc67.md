# Chapter II.5: Sessions and Cookies 239

if the static form with the static value in the `session_id` is used, or if this is the cli-
entent's first attempt to access the server, access is denied by the automatic robot (List-
ing II.5.10).

# Listing II.5.10. The HTML form handler

```
<?php
// Initiating the session
session_start();
// The current SID doesn't match the one passed from the HTML form,
// so stop the script's operation.
if ($_POST['session_id'] != session_id()) exit();
if ($_POST['name'] == 'admin' && $_POST['pass'] == 'admin')
{
    echo "<br><br>Message has been sent<br><br>";
    mail("admin@somewhere.ru", "Statistics", "Message body");
}
?>
```

# II.5.4. Determining Cookie Status on a Client Machine

Any check for support of a specific technology attempts to use that technology.
If the attempt was successful, this means it is supported by the client; other-
wise, the specific technology is not supported. The example of such a check is pro-
ed in Listing II.5.11.

> For convenience, it is possible to install cookies using JavaScript. However, if the
user has disabled JavaScript support, the result will be incorrect.

![](bbox=[0.0465, 0.7035, 0.1368, 0.7835])

# Listing II.5.11. Checking whether cookie support is enabled

```
<?php
if(!isset($_GET['probe']))
{
    // Setting the cookie with the "tešt" name
```