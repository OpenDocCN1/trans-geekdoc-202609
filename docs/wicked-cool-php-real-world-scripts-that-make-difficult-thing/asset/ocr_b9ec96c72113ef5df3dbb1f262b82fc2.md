Users interact with your scripts primarily through form parameters, and therefore they’re the biggest security risk. What’s the lesson? _Always validate the data that gets passed to any PHP script in the PHP script._ “Verification Strategies” on page 46 shows how to validate discrete data. In this chapter, we show you how to analyze and protect against cross-site scripting (XSS) attacks, which can hijack your user’s credentials (and worse). You’ll also see how to prevent the MySQL injection attacks that can taint and destroy your data.

# Don’t trust users.

Assume that every piece of data your website gathers is laden with harmful code. Sanitize every piece, even if you’re positive that nobody would ever try to attack your site. Paranoia pays off.

# Turn off global variables.

The biggest security hole you can have is having the register_globals configuration parameter enabled. Mercifully, it’s turned off by default in PHP 4.2 and later. Refer to “#14: Turning Off Registered Global Variables” on page 25 to disable this setting.

Novice programmers view registered globals as a convenience, but they don’t realize how dangerous this setting is. A server with global variables enabled automatically assigns global variables to any form parameters. For an idea of how this works and why this is dangerous, let’s look at an example.

Let’s say that you have a script named _process.php_ that enters form data into your user database. The original form looked like this:

```
<input name="username" type="text" size="15" maxlength="64">
```

When running process.php, PHP with registered globals enabled places the value of this parameter into the $username variable. This saves some typing of accessing them through $_POST['username'] or $_GET['username']. Unfortunately, this also leaves you open to security problems, because PHP sets a variable for _any_ value sent to the script via a GET or POST parameter, and that is a big problem if you didn’t explicitly initialize the variable and you don’t want someone to manipulate it.

Take the script below, for example—the $authorized variable is true, it shows confidential data to the user. Under normal circumstances, the $authorized variable is set to true _only_ if the user has been properly authenticated via the hypothetical authenticated_user() function. But if you have register_globals active, anyone could send a GET parameter such as authorized=1 to override this:

```
<?php
// Define $authorized = true only if user is authenticated
if (authenticated_user()) {
    $authorized = true;
}
?>
```