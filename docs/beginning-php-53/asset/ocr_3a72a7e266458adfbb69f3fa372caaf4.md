PHP helps to automate this process with the built-in SID constant. If the browser supports cookies, this constant is empty; however, if the session cookie can’t be set on the browser, SID contains a string similar to the following:

```
PHPSESSID=b8306b025a76a250f0428fc0efd20a11
```

This means that you can code the links in your pages to include the session ID, if available:

```
<?php session_start() ?>
<a href="myscript.php?<?php echo SID; ?>">Home page</a>
```

If the session ID was successfully stored in a browser cookie, the preceding code will output:

```
<a href="myscript.php">Home page</a>
```

However, if PHP can’t create the session cookie, the code will output something along the lines of:

```
<a href="myscript.php?PHPSESSID=5bf28931309ba166b3a3ea8b67ff1c57">
Home page</a>
```

When the user clicks the link to view myscript.php, the PHPSESSID query string value is automatically picked up by the PHP engine and the session data is made available to the script.

> Note that you need to have called session_start() before trying to access the SID constant.

Convenient though this feature is, passing session IDs in URLs is best avoided if possible. It’s easy for a visitor to email a link — including her session ID — to a friend, thereby inadvertently giving the friend access to her session! You can mitigate against this somewhat with short session cookie lifetimes (see the next section), but generally it’s best to use only cookies if possible.

You can also retrieve the current session ID by calling the session_id() function. This allows you, among other things, to embed the session ID in a hidden PHPSESSID field in a form, so that the session can be propagated across form submissions.

# Changing Session Behavior

You can alter PHP’s default session-handling behavior in a number of ways. The php.ini file contains several configuration directives that you can alter: