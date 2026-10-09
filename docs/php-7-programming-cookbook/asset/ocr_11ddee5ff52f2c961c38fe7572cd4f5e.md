# See also

+   In Chapter 6, Building Scalable Websites, the recipe entitled Chaining $_POST validators discusses how to incorporate the basic validation concepts covered here into a comprehensive filter chaining mechanism.

# Safeguarding the PHP session

The PHP session mechanism is quite simple. Once the session is started using session_start() or the php.ini session.autostart setting, the PHP engine generates a unique token that is, by default, conveyed to the user by way of a cookie. On subsequent requests, while the session is still considered active, the user’s browser (or equivalent) presents the session identifier, again usually by way of a cookie, for inspection. The PHP engine then uses this identifier to locate the appropriate file on the server, populating $_SESSION with the stored information. There are tremendous security concerns when the session identifier is the sole means of identifying a returning website visitor. In this recipe, we will present several techniques that will help you to safeguard your sessions, which, in turn, will vastly improve the overall security of the website.

# How to do it...

+   1. First of all, it’s important to recognize how using the session as the sole means of authentication can be dangerous. Imagine for a moment that when a valid user logs in to your website, that you set a loggedIn flag in $_SESSION:

```
session_start();
$loggedIn = $_SESSION['isLoggedIn'] ?? FALSE;
if (isset($_POST['login'])) {
    if ($_POST['username'] == // username lookup
    && $_POST['password'] == // password lookup) {
        $loggedIn = TRUE;
        $_SESSION['isLoggedIn'] = TRUE;
    }
}
```

+   2. In your program logic, you allow the user to see sensitive information if $_SESSION['isLoggedIn'] is set to TRUE:
<br>Secret Info
<br><?php if ($loggedIn) echo // secret information; ?>