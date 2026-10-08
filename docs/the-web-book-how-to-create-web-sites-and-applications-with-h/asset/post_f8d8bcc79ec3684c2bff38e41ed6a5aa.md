
![](img/50e1558b8202f19b96c1cc386ea5ec66_287_0.png)

This should be enough to help you track down the problem. However, some server operators regard it as a security risk to display syntax errors, because they could provide hackers with clues as to the inner workings of a program (such as the names of variables or the locations of files). So they configure their server not to display syntax errors at all. Which means that, if there's one in your PHP file, all you'll see is a blank screen. The program won't run, but you won't be told why. In such cases, your only realistic option is to find a different server.

It's important to note that, although server-generated syntax errors tell you the line number in your code that contains the error, this number isn't always correct. It's a great starting point when you're trying to track down the problem, but it's not infallible. This is because PHP tends to assume that the error occurred on the line following the last valid line. Which isn't always the case. This often means that the indicated line number will be "out" by 1 or 2, although in rare cases (especially if you have long blocks of bracketed code and you've omitted a bracket or added an extra one) it can be even more inaccurate.

One useful technique, if you're stuck with a particularly elusive syntax error, is "the chop". Split the PHP file into two separate files, of roughly even lengths. So long as you don't break up any blocks of bracketed code, ie so long as the opening or closing bracket doesn't end up in the other file, you should be safe. The programs won't work the way you expect, but that doesn't matter. What matters is that one of them will generate a syntax error when you surf to it, and one won't. You now know for sure which half of the file contains the error. So split that file into 2 and repeat the process. Eventually, the "half" which contains the syntax error will be small enough that you should be able to recognise where the problem lies.

### Coding Errors

When it comes to tracking down coding errors, your best friend is a simple **echo** statement, possibly followed by **exit()**. For example, in the case mentioned above, precede the line with:

```php
echo $room[1];
exit();
```

When your program reaches this point, it will display the value of the variable and then stop. Of course, the fact that the variable is blank means that you won't see anything, so you might prefer:

```php
echo "XYZ" . $room[1] ;
exit();
```

You can now look on the generated web page for XYZ, and you'll know where to expect to see the room number displayed alongside.

And one final addition, which will also help. Change the code to:

```php
echo "XYZ" . $room[1]; #debug
exit();                #debug
```

This way, once the program is working properly, you can easily search for the lines with the comment in order to remove them.

If all this effort doesn't bring the bug out of the woodwork, then move your debug code further up the file, to just after the place where $room[1] is initially defined. Hopefully, its value at that point should be correct. So somewhere between those two points it's being changed. All that remains is to position your debug code, in turn, just after every line that changes (or which you suspect might change) the value of $room[1]. Chances are, the problem will be down to a simple mis-spelling, eg rooms rather than room, or "1" rather than 1.

If you want to output the values of an entire array rather than a single variable, you don't have to write a for... loop to do it. PHP has such a feature built in. Assuming there's a problem with one or more elements of the $rooms array, and you want to see the whole array rather than just element 1, use var_dump. The following code:

```php
<?php
$rooms[1] = "ABC";
$rooms[2] = "DEF";
$rooms[3] = "GHI";

echo "<pre>";
var_dump($rooms);
echo "</pre>";
?>
```

Produces the following output:

```
array(3) {
  [1]=>
  string(3) "ABC"
  [2]=>
  string(3) "DEF"
  [3]=>
  string(3) "GHI"
}
```

This tells you that the array has 3 elements. Element [1] is a 3-letter string comprising ABC. Element 2 is a 3-letter string of DEF, and so on.

If this still doesn't help, you can go one step further and output the contents of every variable that the program knows about. Just do this:

```php
echo "<pre>";
var_dump(get_defined_vars());
echo "</pre>";
```

This works because there's a PHP function which creates an array containing all of the variables. So we call this function, then use var_dump to display the array. As for the other two lines, the <pre> tag tells the web browser that it's being asked to display preformatted text, and is often used when displaying program listings and the like. Just trust me that the output of var_dump looks much more readable if surrounded by such tags.

While this also produces the list of the contents of the rooms array, it comes at the end of a very long (many hundreds of lines) listing of lots of other variables as well. These are not variables that your program has created, but ones which the web server and PHP use for their own internal purposes. Some of these are very useful. For example, take a look at this extract from the list that is returned on the the-web-book.com server:

```
["_SERVER"]=>
array(31) {
  ["DOCUMENT_ROOT"]=>
  string(27) "/home//thewebbbo/public_html"
  ["GATEWAY_INTERFACE"]=>
  string(7) "CGI/1.1"
  ["HTTP_ACCEPT"]=>
  string(22) "image/jpeg, application/x-ms-application, image/gif, application/xaml+"
  ["HTTP_ACCEPT_ENCODING"]=>
  string(13) "gzip, deflate"
  ["HTTP_ACCEPT_LANGUAGE"]=>
  string(5) "en-GB"
  ["HTTP_CACHE_CONTROL"]=>
  string(14) "max-age=259200"
  ["HTTP_CONNECTION"]=>
  string(10) "keep-alive"
  ["HTTP_HOST"]=>
  string(20) "www.the-web-book.com"
  ["HTTP_USER_AGENT"]=>
  string(151) "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; Trident/4.0; SLCC2;
  ["HTTP_VIA"]=>
  string(61) "1.1 sulafat.brighton.ac.uk:8080 (squid/2.5.STABLE12-20051129)"
  ["HTTP_X_FORWARDED_FOR"]=>
  string(13) "194.83.112.39"
  ["PATH"]=>
  string(13) "/bin:/usr/bin"
  ["QUERY_STRING"]=>
  string(0) ""
  ["REDIRECT_STATUS"]=>
  string(3) "200"
  ["REMOTE_ADDR"]=>
  string(13) "194.81.199.59"
  ["REMOTE_PORT"]=>
  string(5) "64425"
  ["REQUEST_METHOD"]=>
  string(3) "GET"
  ["REQUEST_URI"]=>
  string(14) "/breakfast.php"
```

This section, as you can see from the top line, is concerned with the contents of the $_SERVER[] array, which contains 31 elements. The element called “REQUEST_URI” (remember that element names don’t have to be numeric), right down at the bottom of the list here, seems to contain the name of our program file. Let’s just check this, by writing a program thus:

```php
<?php
echo $_SERVER["REQUEST_URI"];
?>
```

And here’s the result:

![](img/50e1558b8202f19b96c1cc386ea5ec66_291_0.png)

This is hugely useful, for reasons we'll come onto in the next chapter.

## The $_SERVER Variables

There are lots of other useful items in the $_SERVER[] array. Let's have a look at it with a var_dump($_SERVER) call. This gives us:

```
array(31) [
  ["DOCUMENT_ROOT"] => string(27) "home7//theWebbo/public_html" ["GATEWAY_INTERFACE"] => string(7) "CGI/1.1" ["HTTP_ACCEPT"] => string(22) "text/ms-apple, image/g, ap lication/vnd.wap.ms-app, image/page, application/vnd.ms-excel, application/vnd.ms-powerpoint, app lica25920" ["HTTP_ENCODING"] => string(13) "gzip, deflate" ["HTTP_ACCEPT_LANGUAGE"] => string(5) "en-GB" ["HTTP_CACHE_CONTROL"] => string(14) "max-age=25920" ["HTTP_CONNECTION"] => string(10) "Keep-Alive" ["HTTP_HOST"] => string(20) "www.the-web-book.com" ["HTTP_USER_AGENT"] => string(151) "Media 8, 0, Windows NT 6.1, Trident/4, 0, SLCC2, NET CLR 2.0, 50727, NET CLR 3.5.30729, NET CLR 3.0, 30729, Media Center PC 6.0" ["HTTP_VIA"] => string(60) "1.1 masi cqued25 STABLE2.2.0051129)" ["HTTP_X_FORWARDED_FOR"] => string(13) "194.83.112.39" ["PATH"] => string(13) "bin; etc;" ["QUERY_STRING"] => string(0) "" ["REDIRECT_STATUS"] => string(3) "200" ["REMOTE_ADDR"] => string(13) "194.81.199,56" ["REMOTE_PORT"] => string(5) "31986" ["REQUEST_METHOD"] => strin G(5) "GET" ["REQUEST_URI"] => string(11) "test99.php" ["SCRIPT_FILENAME"] => string(38) "home7//theWebbo/public_html/test99.php" ["SCRIPT_NAME"] => string(11) "/test99.php" ["SERVER_ADDR"] => string(14) "167.417.140,168" ["SERVER_ADMIN"] => string(26) "webmaster@theWeb-book.com" ["SERVER_NAME"] => string(20) "www book.com" ["SERVER_PORT"] => string(2) "80" ["SERVER_PROTOCOL"] => string(8) "HTTP/1.1" ["SERVER_SIGNATURE"] => string(79) "Apache/2.2.21 (Unix) mod_ssl/2.2.11 OpenSSL/0.9,8k_DAT/2 mod_auth_passthrough/2,1, mod, bwiimited/1.4 FrontPage/5.0.2.2635 Server at www-the-web-book.com Port 2635" ["SERVER_SOFTWARE"] => string(120) "Apache/2.2.11 (Unix) mod_ssl/2.2.11 OpenSSL/0.9,8k_DAT/2 mod, auth_passthrough/2.1 mod, bwiimited/1.4 FrontPage/5.0.2.2635" ["SERVER_SOFTWARE"] => string(120) "Apache/2.2.11 (Unix) mod_ssl/2.2.11 OpenSSL/0.9,8k_DAT/2 mod, auth_passthrough/2.1 mod, bwiimited/1.4 FrontPage/5.0.2.2635" ["REQUEST_TIME"] => sat(129398676)
```

Oops, that's what happens if you forget the <pre> tags! Let's try that again:

```
array(32) {
["DOCUMENT_ROOT"] =>
string(27) "/home7//theWebbo/public_html"
["GATEWAY_INTERFACE"] =>
string(7) "CGI/1.1"
["HTTP_ACCEPT"] =>
string(3) "*/ *"
["HTTP_ACCEPT_ENCODING"] =>
string(13) "gzip, deflate"
["HTTP_ACCEPT_LANGUAGE"] =>
string(5) "en-GB"
["HTTP_CACHE_CONTROL"] =>
string(14) "max-age=25920"
["HTTP_CONNECTION"] =>
string(10) "keep-alive"
["HTTP_HOST"] =>
string(20) "www.the-web-book.com"
["HTTP_PRAGMA"] =>
string(8) "no-cache"
["HTTP_USER_AGENT"] =>
```
