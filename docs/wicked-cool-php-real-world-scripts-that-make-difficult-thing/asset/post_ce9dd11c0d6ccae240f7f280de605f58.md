
Let’s say that you have a form parameter that you eventually place into
a variable named $product, and you create some SQL like this:

```
$sql = "select * from pinfo where product = '$product'";
```

If that parameter came straight from the form, use database-specific
escapes with PHP’s native functions, like this:

```
$sql = "Select * from pinfo where product = '" .
mysql_real_escape_string($product) . "'";
```

If you don’t, someone might just decide to throw this fragment into the
form parameter:

```
39'; DROP pinfo; SELECT 'FOO
```

Then the result of $sql is:

```
select * from pinfo where product = '39'; DROP pinfo; SELECT 'FOO'
```

Because the semicolon is MySQL’s statement delimiter, the database
processes these three statements:

```
select * from pinfo where product = '39'
DROP pinfo
SELECT 'FOO'
```

Well, there goes your table.

Note that this particular syntax won’t actually work with PHP and MySQL,
because the mysql_query() function allows just one statement to be processed
per request. However, a subquery will still work.

To prevent SQL injection attacks, do two things:

- Always validate all parameters. For example, if something needs to be a
number, make sure that it’s a number.

- Always use the mysql_real_escape_string() function on data to escape any
quotes or double quotes in your data.

> NOTE To automatically escape any form data, you can turn on Magic Quotes. See "#15: Enabling Magic Quotes" on page 26.

Some MySQL damage can be avoided by restricting your MySQL user
privileges. Any MySQL account can be restricted to only do certain kinds
of queries on selected tables. For example, you could create a MySQL user
who can select rows but nothing else. However, this is not terribly useful for
dynamic data, and, furthermore, if you have sensitive customer information,
it might be possible for someone to have access to some data that you didn’t
intend to make available. For example, a user accessing account data could
try to inject some code that accesses another account number instead of the
one assigned to the current session.

## #20: Preventing Basic XSS Attacks

XSS stands for _cross-site scripting_. Unlike most attacks, this exploit works on the client side. The most basic form of XSS is to put some JavaScript in user-submitted content to steal the data in a user's cookie. Since most sites use cookies and sessions to identify visitors, the stolen data can then be used to impersonate that user—which is deeply troublesome when it's a typical user account, and downright disastrous if it's the administrative account. If you don't use cookies or session IDs on your site, your users aren't vulnerable, but you should still be aware of how this attack works.

Unlike MySQL injection attacks, XSS attacks are difficult to prevent. Yahoo!, eBay, Apple, and Microsoft have all been affected by XSS. Although the attack doesn't involve PHP, you _can_ use PHP to strip user data in order to prevent attacks. To stop an XSS attack, you have to restrict and filter the data a user submits to your site. It is for this precise reason that most online bulletin boards don't allow the use of HTML tags in posts and instead replace them with custom tag formats such as [b] and [linkto].

Let's look at a simple script that illustrates how to prevent some of these attacks. For a more complete solution, use SafeHTML, discussed later in this chapter.

```
function transform_HTML($string, $length = null) {
 // Helps prevent XSS attacks

 // Remove dead space.
 $string = trim($string);

 // Prevent potential Unicode codec problems.
 $string = utf8_decode($string);

 // HTMLize HTML-specific characters.
 $string = htmlentities($string, ENT_NOQUOTES);
 $string = str_replace("#", "&#35;", $string);
 $string = str_replace("%", "&#37;", $string);

 $length = intval($length);
 if ($length > 0) {
   $string = substr($string, 0, $length);
 }
 return $string;
}
```

This function transforms HTML-specific characters into HTML literals. A browser renders any HTML run through this script as text with no markup. For example, consider this HTML string:

```
<STRONG>Bold Text</STRONG>
```

Normally, this HTML would render as follows:

```
Bold Text
```

However, when run through transform_HTML(), it renders as the original input. The reason is that the tag characters are HTML entities in the processed string. The resulting string from transform_HTML() in plaintext looks like this:

```
&lt;STRONG&gt;Bold Text&lt;/STRONG&gt;
```

The essential piece of this function is the htmlentities() function call that transforms <, >, and & into their entity equivalents of &lt;, &gt;, and &amp;. Although this takes care of the most common attacks, experienced XSS hackers have another sneaky trick up their sleeve: Encoding their malicious scripts in hexadecimal or UTF-8 instead of normal ASCII text, hoping to circumvent your filters. They can send the code along as a GET variable in the URL, saying, “Hey, this is hexadecimal code, but could you run it for me anyway?” A hexadecimal example looks something like this:

```
<a href="http://host/a.php?variable=%22%3e
%3c%53%43%52%49%50%54%54%45%44
%6f%73%66%dd%65%74%68%89%69%e6%7f%d6%1c%c6%93%39%69%6f%75%73%c3%c2%f5%43%43%52
%49%50%54%3e">
```

But when the browser renders that information, it turns out to be:

```
<a href="http://host/a.php?variable="> <SCRIPT>DoSomethingmalicious</SCRIPT>
```

To prevent this, transform_HTML() takes the additional steps of converting # and % signs into their entity, shutting down hex attacks, and converting UTF-8–encoded data.

Finally, just in case someone tries to overload a string with a very long input, hoping to crash something, you can add an optional $length parameter to trim the string to the maximum length you specify.

## #21: Using SafeHTML

The problem with the previous script is that it is simple, and it does not allow for any kind of user markup. Unfortunately, there are hundreds of ways to try to sneak JavaScript past someone's filters, and short of stripping all HTML from someone's input, there's no way of stopping it.

Currently, there's no single script that's guaranteed to be unbreakable, though there are some that are better than most. As you'll learn in more detail in “Verification Strategies” on page 46, there are two approaches to security, whitelisting and blacklisting, and whitelisting tends to be less complicated and more effective.

One whitelisting solution is the SafeHTML anti-XSS parser from PixelApes. SafeHTML is smart enough to recognize valid HTML, so it can hunt and strip any dangerous tags. It does its parsing with another package called HTMLSax.

To install and use SafeHTML, do the following:

- 1. Go to http://pixel-apes.com/safehtml/?page=safehtml and download the latest version of SafeHTML.
- 2. Put the files in the classes directory on your server. This directory contains everything that SafeHTML and HTMLSax need to function.
- 3. Include the SafeHTML class file (safehtml.php) in your script.
- 4. Create a new SafeHTML object called $safehtml.
- 5. Sanitize your data with the $safehtml->parse() method.

Here's a complete example:

```
<?php
/* If you're storing the HTMLSax3.php in the /classes directory, along
with the safehtml.php script, define XML_HTMLSAX3 as a null string. */
define('XML_HTMLSAX3', '');
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

## What Can Go Wrong?

The biggest mistake you can make is assuming that this class completely shuts down XSS attacks. SafeHTML is a fairly complex script that checks for almost everything, but nothing is guaranteed. You still want to do the parameter validation that applies to your site. For example, this class doesn't check the length of a given variable to ensure that it fits into a database field. It doesn't check for buffer overflow problems.

XSS hackers are creative and use a variety of approaches to try to accomplish their objectives. Just look at RSnake's XSS tutorial at http://ha.ckers.org/xss.html to see how many ways there are to try to sneak code past someone's filters. The SafeHTML project has good programmers working overtime to try to stop XSS attacks, and it has a solid approach, but there's no guarantee that someone won't come up with some weird and fresh approach that could short-circuit its filters.

> **NOTE** For an example of the powerful effects of XSS attacks, check out http://namb.la/popular/tech.html, which shows a step-by-step approach to creating the JavaScript XSS worm that overloaded the MySpace servers.
