Notice that the response consists of the status line, followed by various response headers, followed by a blank line and, finally, the requested content (in this case a Web page).

Once the browser receives a Web page, it usually makes additional requests for any other resources referenced in the page, such as the common.css style sheet file in this example, or any images embedded in the page. Therefore when a visitor views a Web page, several HTTP requests and responses may be initiated.

# Modifying an HTTP Response

Because the PHP engine interacts with the Web server, your PHP scripts can influence the HTTP response headers sent by the server. This can be very useful.

To get the Web server to send a custom HTTP header as part of its response, you use PHP’s header() function. This simply takes the header line to output, then injects this line into the response headers:

```
```
header ( "Server: Never you mind" );
```
```

By default, header() replaces any HTTP header field with the same name. In the example just shown, if the response already contains a Server header, that header is replaced with the one passed into header(). However, some HTTP header fields can be included more than once in the response. If you’d like to include the same header several times, pass in false as the second argument to header():

```
```
header( "Set-Cookie: name=Fred; expires=Mon, 05-Jan-2009 10:22:21 GMT;
path=/; domain=.example.com" );
header( "Set-Cookie: age=33; expires=Mon, 05-Jan-2009 10:22:21 GMT; path=/;
domain=.example.com", false );
```
```

(Although you can set cookies this way, it’s easier to use PHP’s setcookie() function, as described in Chapter 10.)

Generally speaking, when you pass a header line to header(), PHP faithfully injects the header line as-is into the response. However, there are two special cases:

+   - If the header string starts with HTTP/, PHP assumes you want to set the status line, rather than add or replace a header line. This allows you to set your own HTTP status lines:

```
```
// Nothing to see here, move along
header ( "HTTP/1.1 404 Not Found" );
```
```

+   - If you pass in a Location header string, PHP automatically sends a 302 Found status line as well as the Location header:

```
```
// Redirect to the login page
header( "Location: http://www.example.com/login.php" );
```
```

+   - This makes it easy to do page redirects (as you saw in Chapter 9). If you’d rather send a different status line, simply specify the status line as well:

```
```
header ( "HTTP/1.1 301 Moved Permanently" );
header( "Location: http://www.example.com/newpage.php" );
```
```