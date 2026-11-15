# Timing

Finally, an important note: As cookies are sent as part of the HTTP header, all calls to setcookie() must be made before the first HTML output.3 This is because as soon as HTML is delivered, the HTTP headers have already been sent. If you still set HTTP headers afterward, the error message shown in Figure 14.4 appears in some PHP versions and configurations.

![](bbox=[0.14, 0.222, 0.735, 0.359])

Figure 14.4 Cookies Must Be Set at the Beginning of the Script

In the following script, it is done correctly; that is, a few cookies are set before the HTML code is output.

```
<?php
setcookie("ProgrammingLanguage", "PHP",
    time() + 60*60*12, "/");
setcookie("LanguageVersion", "8",
    mktime(0, 0, 0, 12, 24, 2025), "/");
setcookie("Session", "abc123", 0, "/");
?>
<html>
<head>
<title>Cookies</title>
</head>
<body>
<p>Cookies have been set!</p>
</body>
</html>
```

# Listing 14.1 Three Cookies Are Set ("set.php")

The output of this script is relatively meagre because—as already mentioned—cookies are only sent to the server the next time a page is accessed. However, if you look at the browser developer tools, you will at least see the Cookie HTTP headers. Figure 14.5 shows that in the Chrome browser.

3 At least so long as output buffering is deactivated. If you have set the output_buffering option to an appropriate value in php.ini, then PHP will still set the cookies in good time and no error message will appear.