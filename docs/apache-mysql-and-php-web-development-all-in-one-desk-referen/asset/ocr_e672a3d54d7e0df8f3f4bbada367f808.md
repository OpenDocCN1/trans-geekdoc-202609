# # Dealing with Errors in Your PHP Code

Because PHP is a script processor that lets you generate HTML pages, you may wonder about errors. If you make a mistake in your PHP code, what happens?

The answer is a frightening one: The error messages appear in the generated HTML page. This means that the users who connect to your site see the error messages in all their glory right on their Web browser screens.

Suppose this is your PHP file:

```
<html>
<head>
<title>Error Demo!</title>
</head>
<body>
<?php
(as=*#fa!@#
?>
there<br>everybody
</body>
</html>
```

The PHP code in this file consists of several random characters, which, as luck would have it, do not happen to create a valid PHP program. If you try to open this file in your browser, you (and any visitors to your site) see the following:

Parse error: parse error in /home/jeffcogs/public_html/errordemo.php on line 7

This error message appears right in the browser.

Therefore, as with any other program, always test out your PHP code by putting it on your Web server and requesting it through a browser. You can then see your errors and go back and fix them in the code.

# # Exploring Some PHP Ground Rules

To conclude this chapter, here are a few quick ground rules for the PHP language:

+   - End your statements with semicolons. You can see how I did this in the examples throughout this chapter.