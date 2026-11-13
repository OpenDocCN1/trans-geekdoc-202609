+   2. Put the files in the classes directory on your server. This directory contains everything that SafeHTML and HTMLSax need to function.
+   3. Include the SafeHTML class file (safehtml.php) in your script.
+   4. Create a new SafeHTML object called $safehtml.
+   5. Sanitize your data with the $safehtml->parse() method.

Here's a complete example:

```
<?php
/* If you're storing the HTMLSax3.php in the /classes directory, along
with the safehtml.php script, define XML_HTMLSAX3 as a null string. */
define(XML_HTMLSAX3, '');
// Include the class file.
require_once('classes/safehtml.php');
// Define some sample bad code.
$data = "This data would raise an alert <script>alert('XSS Attack')</script>";
// Create a safehtml object.
$safehtml = new safehtml();
// Parse and sanitize the data.
$safe_data = $safehtml->parse($data);
// Display result.
echo 'The sanitized data is <br />' . $safe_data;
?>
```

If you want to sanitize any other data in your script, you don't have to create a new object; just use the $safehtml->parse() method throughout your script.

# What Can Go Wrong?

The biggest mistake you can make is assuming that this class completely shuts down XSS attacks. SafeHTML is a fairly complex script that checks for almost everything, but nothing is guaranteed. You still want to do the parameter validation that applies to your site. For example, this class doesn't check the length of a given variable to ensure that it fits into a database field. It doesn't check for buffer overflow problems.

XSS hackers are creative and use a variety of approaches to try to accomplish their objectives. Just look at RSnake's XSS tutorial at http://ha.ckers.org/xss.html to see how many ways there are to try to sneak code past someone's filters. The SafeHTML project has good programmers working overtime to try to stop XSS attacks, and it has a solid approach, but there's no guarantee that someone won't come up with some weird and fresh approach that could short-circuit its filters.

> **NOTE** For an example of the powerful effects of XSS attacks, check out http://namb.la/popular/tech.html, which shows a step-by-step approach to creating the JavaScript XSS worm that overloaded the MySpace servers.