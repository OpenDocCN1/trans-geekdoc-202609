# Interacting with the Environment: getenv() and putenv() 401

```
echo '</pre>';
echo <hr />;

// backticks
echo '<h1>Using Backticks</h1>';
echo '<pre>';

// unix
$result = `ls -al`;

// windows
$result = `dir`;

echo $result;
echo '</pre>';

?>
```

You could use one of these approaches as an alternative to the directory-browsing script you saw earlier. Note that one of the side effects of using external functions is amply demonstrated by this code: Your code is much less portable, as uses Unix commands, and the Windows commands show (but commented out) may not produce the effects you want.

If you plan to include user-submitted data as part of the command you're going to execute, you should always run it through the `escaphellcmd()` function first. This way, you stop users from maliciously (or otherwise) executing commands on your system. You can call it like this: `system(escaphellcmd($command));`

You should also use the `escaphellarg()` function to escape any arguments you plan to pass to your shell command.

# Interacting with the Environment: getenv() and putenv()

Before we dive into this, let's look at how to use environment variables from PHP. Two functions serve this: `getenv()`, which enables you to retrieve environment variables, and `putenv()`, which enables you to set environment variables. Note that the environment we are talking about here is the environment in which PHP runs on the server.

You can get a list of all PHP's environment variables by running `phpinfo()`. Some are more useful than others; for example,
getenv("HTTP_REFERER");

returns the URL of the page from which the user came to the current page.