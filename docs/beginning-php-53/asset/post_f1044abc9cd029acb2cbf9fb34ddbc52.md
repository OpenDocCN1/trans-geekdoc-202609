
As with requests, a response typically contains up to four sections:

- The status line: This tells the Web browser the status of the request
- A list of HTTP headers: These optional headers contain extra information about the response, such as the type and length of the returned content
- An empty line: This is required after the request line and any headers
- An optional message body: Usually this contains the returned content, such as the Web page markup or encoded image data

An HTTP status line consists of a status code and a corresponding reason phrase (that is, a plain English version of the status code). Common status codes include:

| Status Code | Reason Phrase | Description |
|---|---|---|
| 200 | OK | The browser's request was successful. The requested content (if any) will follow. |
| 301 | Moved Permanently | The requested resource is now at a different URL. The new URL will follow in a Location header. The browser should use the new URL in the future. |
| 302 | Found | The requested resource is temporarily at a different URL. The new URL will follow in a Location header. The browser should continue to use the existing URL in future requests. |
| 400 | Bad Request | The request sent by the browser was invalid (for example, its syntax was incorrect). |
| 403 | Forbidden | The browser is trying to access a resource that it does not have permission to access (for example, a password-protected file). |
| 404 | Not Found | The resource requested by the browser could not be found on the server. |
| 500 | Internal Server Error | There was a problem processing the request on the server. |

Many response headers are similar, or identical, to their request header counterparts. Here are a few of the more common response headers sent by Web servers:

| Header | Description | Example |
| :--- | :--- | :--- |
| Date | The date and time of the response. | Date: Mon, 05 Jan 2009 10:07:20 GMT |
| Content-Length | The length (in bytes) of the content that follows. | Content-Length: 8704 |
| Content-Type | The MIME content type for the content that follows. | Content-Type: text/html |
| Location | An alternative URL to the one requested. Commonly used with 301 and 302 status codes to send the browser to a new URL. | Location: http://www.example.com/newpage.php |
| Server | Information about the Web server, such as its type and version. | Server: Apache/1.3.34 (Debian) PHP/5.2.0-8+etch13 mod_perl/1.29 |
| Set-Cookie | Requests that an HTTP cookie be stored in the browser. | Set-Cookie: name=Fred; expires=Mon, 05-Jan-2009 10:22:21 GMT; path=/; domain=.example.com |

Here’s an example response from a Web server after a browser has requested an HTML page:

```
HTTP/1.x 200 OK
Date: Mon, 05 Jan 2009 10:19:52 GMT
Server: Apache/2.0.59 (Unix) PHP/5.2.5 DAV/2
X-Powered-By: PHP/5.2.5
Content-Length: 395
Keep-Alive: timeout=15, max=96
Connection: Keep-Alive
Content-Type: text/html

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>About Us</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>About Us</h1>
<p>We specialize in widgets for all occasions.</p>
</body>
</html>
```

Notice that the response consists of the status line, followed by various response headers, followed by a blank line and, finally, the requested content (in this case a Web page).

Once the browser receives a Web page, it usually makes additional requests for any other resources referenced in the page, such as the common.css style sheet file in this example, or any images embedded in the page. Therefore when a visitor views a Web page, several HTTP requests and responses may be initiated.

## Modifying an HTTP Response

Because the PHP engine interacts with the Web server, your PHP scripts can influence the HTTP response headers sent by the server. This can be very useful.

To get the Web server to send a custom HTTP header as part of its response, you use PHP’s header() function. This simply takes the header line to output, then injects this line into the response headers:

```
header("Server: Never you mind");
```

By default, header() replaces any HTTP header field with the same name. In the example just shown, if the response already contains a Server header, that header is replaced with the one passed into header(). However, some HTTP header fields can be included more than once in the response. If you’d like to include the same header several times, pass in false as the second argument to header():

```
header( "Set-Cookie: name=Fred; expires=Mon, 05-Jan-2009 10:22:21 GMT; path=/; domain=.example.com" );
header( "Set-Cookie: age=33; expires=Mon, 05-Jan-2009 10:22:21 GMT; path=/; domain=.example.com", false );
```

(Although you can set cookies this way, it’s easier to use PHP’s setcookie() function, as described in Chapter 10.)

Generally speaking, when you pass a header line to header(), PHP faithfully injects the header line as-is into the response. However, there are two special cases:

- If the header string starts with HTTP/, PHP assumes you want to set the status line, rather than add or replace a header line. This allows you to set your own HTTP status lines:

```
// Nothing to see here, move along
header("HTTP/1.1 404 Not Found");
```

- If you pass in a Location header string, PHP automatically sends a 302 Found status line as well as the Location header:

```
// Redirect to the login page
header( "Location: http://www.example.com/login.php" );
```

- This makes it easy to do page redirects (as you saw in Chapter 9). If you’d rather send a different status line, simply specify the status line as well:

```
header("HTTP/1.1 301 Moved Permanently");
header( "Location: http://www.example.com/newpage.php" );
```

header() is very useful if your PHP script needs to send anything other than an HTML Web page. For example, say you have a report.pdf file on the Web server, and you want to send this to the browser. You could write the following:

```
<?php
header( "Content-Type: application/pdf" );
readfile( "report.pdf" );
?>
```

The first line tells the Web browser to expect a PDF document rather than a regular Web page. The second line reads the PDF file on the server's hard drive and outputs its contents to the Web browser, which can then save or display the PDF.

Usually it's up to the browser as to whether it displays the file in the browser itself, or offers to save it to the user's hard disk. You can use a Content-Disposition: Attachment header to suggest to the browser that the file should be saved rather than displayed and, optionally, to suggest a filename for the saved file:

```
<?php
header( "Content-Type: application/pdf" );
header( 'Content-Disposition: attachment; filename="Latest Report.pdf"' );
readfile( "report.pdf" );
?>
```

By the way, you need to make sure you don't send anything to the browser before calling header(). This includes HTML markup, or even blank lines, before your opening <?php tag. This is because, once PHP has received a request to send some content to the browser, it sends the HTTP headers first (because the headers need to be sent at the start of the response). Therefore, by the time your header() call is executed, the content is already being sent, and it's too late to send any more headers. (If you fall foul of this, then your header isn't sent and PHP generates a Cannot modify header information - headers already sent warning.)

## Getting Information from the Web Server

Each time a PHP script is run, the Web server software makes a wealth of useful information available to the PHP engine. Such information includes details about the server itself, as well as details of the script being executed, and many of the HTTP request headers discussed previously in this chapter.

You can access all of this information in your PHP script through the $_SERVER superglobal array. For example, to display the IP address of the visitor's computer (or proxy server) you might use:

```
echo "Your IP address is: " . $_SERVER["REMOTE_ADDR"];
```

Because Web servers come in all shapes and sizes, the information available depends very much on your particular server setup. Having said that, there's usually a core list of values that are always present. Here's a list of the more common and useful $_SERVER variables:
