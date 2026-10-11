
# PHP Superglobals

## HTTP_USER_AGENT
Contents of the user agent. This is a string which contains all the information about the client's browser, including operating system.

## HTTP_COOKIE
All cookies in a concatenated string, with a semi-colon delimiter.

## SERVER_ADDR
The IP address of the server, of which the current script is running.

## PHP_SELF
The file name of the currently executed script, relative to document root.

This would return `/`

## REQUEST_TIME_FLOAT
The timestamp of the start of the request, with microsecond precision. Available since PHP 5.4.0.

## REQUEST_TIME
The timestamp of the start of the request. Available since PHP 5.1.0.

## $_GET
![](Image00097.jpg)

An associative array of variables passed to the current script via the URL parameters.

`$_GET` is an array that contains all the URL parameters; these are the whatever is after the `?` in the URL.

| `$_GET` | `[]` | `"myVar"` |
| --- | --- | --- |

Using [http://www.example.com/index.php?myVar=myVal](http://www.example.com/index.php?myVar=myVal) as an example. This information from this URL can be obtained by accessing in this format `]` and the result of this will be `myVal`.

Using some code for those that don't like reading.

```php
// URL = http://www.example.com/index.php?myVar=myVal
echo $_GET["myVar"] == "myVal" ? "true" : "false"; // returns "true"
```

The above example makes use of the ternary operator.

This shows how you can access the value from the URL using the `$_GET` superglobal.

Now another example!

![](Image00099.jpg)

It is possible to send multiple variables through the URL by separating them with an ampersand (`&`) character.

### Security risk
It is very important not to send any sensitive information via the URL as it will stay in history of the computer and will be visible to anyone that can access that browser.

## $_POST
![](Image00100.jpg)

An associative array of variables passed to the current script via the HTTP POST method when using `application/x-www-form-urlencoded` or `multipart/form-data` as the HTTP Content-Type in the request.

Very similar to `$_GET` in that data is sent from one place to another.

I'll start by going straight into an example. (I have omitted the `action` attribute as this will send the information to the page that the form is in).

![](Image00101.jpg)

Above is a basic form for which data can be sent. In a real environment the `value` attribute would not be set meaning the form would be blank. This would then send whatever information is entered by the user.

![](Image00102.jpg)

### Security risk
Sending data via POST is also not secure. Using HTTPS will ensure that data is kept more secure.

## $_FILES
![](Image00103.jpg)

An associative array of items uploaded to the current script via the HTTP POST method. The structure of this array is outlined in the [POST method uploads](http://php.net/manual/en/features.file-upload.post-method.php) section.

Let's start with a basic form.

![](Image00104.jpg)

| `enctype` | `=` | `"multipart/form-data"` |
| --- | --- | --- |

Note that I omitted the `action` attribute (again!). Also, I added `enctype`, this is important to any form that will be dealing with file uploads.

![](Image00105.jpg)

This is used to upload one file. Sometimes you may wish to upload more than one file. An attribute exists for that, it's called `multiple`.

There's an attribute for just about anything. [I'm sorry](https://www.youtube.com/watch?v=szrsfeyLzyg) Below is an example of a form submitting multiple files.

![](Image00106.jpg)

Note the changes made here; there are only a few.

![](Image00107.jpg)

The input name has square brackets. This is because it is now an array of files and so we are telling the form:

| `$_FILES` | `[]` | `"myVar"` |
| --- | --- | --- |

to make an array of the files selected. Omitting the square brackets will result in the latter most file being set to `]`.

![](Image00108.jpg)

This is a very simple example and doesn't handle problems such as file extensions that aren't allowed or files named with PHP code (like a PHP equivalent of an SQL injection). See the documentation.

The first process is checking if there are any files, and if so, set the total number of them to `$total`.

Using the `for` loop allows an iteration of the `$_FILES` array and accessing each item one at a time. If that file doesn't encounter a problem then the `if` statement is true and the code from the single file upload is run.

If a problem is encountered the `switch` block is executed and an error is presented in accordance with the error for that particular upload.

## $_COOKIE
![](Image00109.jpg)

An associative array of variables passed to the current script via HTTP Cookies.

Cookies are variables that contain data and are stored on the client's computer.

Unlike the aforementioned superglobals, cookies must be created with a function (and not by assigning a value). The convention is below.

![](Image00110.jpg)

In this example a name is specified for the cookie (in this example it is `"myVar"`), a value is given (in this example it is `"myVal"`, but a variable can be passed to assign its value to the cookie), and then an expiration time is given (in this example it is one hour since 3600 seconds is a minute).

Despite the convention for creating a cookie being different, it is accessed in the same way as the others.

![](Image00111.jpg)

To destroy a cookie, `setcookie` must be called again, but the expiration time is set to any time in the past. See below.

![](Image00112.jpg)

This will unset the cookies and remove it from the clients computer.

## $_SESSION
![](Image00113.jpg)

An associative array containing session variables available to the current script. See the [Session functions](http://php.net/manual/en/ref.session.php) documentation for more information on how this is used.

Sessions are much like cookies except they are server side.

| `session_start()` |
| --- |

To use sessions you must include `session_start()` at the top of your scripts to allow sessions to be utilised.

Setting a session variable is the same as setting any other variable. See example below.

![](Image00114.jpg)

| `session_id()` |
| --- |

When starting a session a random ID is set as a cookie and called `"PHPSESSID"` and will contain the session ID for that current session. This can be accessed by calling the `session_id()` function.

| `unset()` | `$_SESSION` | `[]` | `"myVar"` |
| --- | --- | --- | --- |

It is possible to destroy session variables using the `unset()` function (such that `unset($_SESSION["myVar"])` would destroy that variable).

| `session_destroy()` |
| --- |

The alternative is to call `session_destroy()`. This will destroy the entire session meaning that all session variables will no longer exist.

## $_REQUEST
![](Image00115.jpg)

An associative array that by default contains the contents of [`$_GET`](http://php.net/manual/en/reserved.variables.get.php), [`$_POST`](http://php.net/manual/en/reserved.variables.post.php) and [`$_COOKIE`](http://php.net/manual/en/reserved.variables.cookies.php).

As the PHP documentation states, this is just a collation of `$_GET`, `$_POST`, and `$_COOKIE` all in one variable.

| `php.ini` |
| --- |

Since it is possible for all three of those arrays to have an index with the same name, there is a setting in the `php.ini` file called `request_order` which can specify which of the three has precedence.

For instance, if it was set to `"GPC"`, then the value of `$_COOKIE` will be used, as it is read from left to right meaning the `$_REQUEST` will set its value to `$_GET`, then `$_POST`, and then `$_COOKIE` and since `$_COOKIE` is last that is the value that is in `$_REQUEST`. See [this question](http://stackoverflow.com/questions/43157933/what-is-the-request-precedence).

## $_ENV
![](Image00116.jpg)

An associative array of variables passed to the current script via the environment method.
