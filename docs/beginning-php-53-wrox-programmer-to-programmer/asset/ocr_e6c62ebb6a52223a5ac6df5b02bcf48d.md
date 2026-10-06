# Chapter 16: PHP and the Outside World

In the following sections you explore how a Web browser makes an HTTP request to the Web server, how the server sends an HTTP response back to the browser; and how you can influence the HTTP communication between server and browser.

# Understanding HTTP Requests

Whenever a browser wants to display a Web page or other resource (such as an image file) that is stored on a server, the browser first connects to the server (usually via port 80, the HTTP port), and then sends various pieces of information to the server, known as the request message. The request message consists of the following sections, in order:

+   - The request line: This tells the Web server (URL) the browser wants to retrieve
- A list of HTTP headers: These optional lines of text allow the browser to send additional information to the server, such as cookies and which characters the browser can accept
- An empty line: This is required after the request line and any headers
- An optional message body: This might contain, for example, form data sent via the POST method

Each line in the message must end with a carriage return followed by a line character.
The request line is the most important part of the request, because it tells the server which resource to send back to the browser. Here is a typical request line:

```
GET /about/index.php HTTP/1.1
```

The request line consists of three parts: The request method (GET in this case), the URL to retrieve (/about/index.php), and the version of HTTP to use (most modern browsers work with HTTP/1.1). Other request methods include POST (for sending large amounts of data) and HEAD (similar to GET but asks the server to return just the response headers, rather than the actual content).

Many HTTP headers can be sent from a server to a browser. Here are some common ones:

| Header | Description | Example |
|---|---||
| Accept | A list of MIME content types that the browser will accept for the returned content. | Accept: text/html, application/xml |
| Accept-Charset | A list of character sets that the browser will accept for the returned content. | Accept-Charset: ISO-8859-1, utf-8 |
| Accept-Encoding | A list of compression methods that the browser will accept for the returned content. | Accept-Encoding: gzip, deflate |
| Accept-Language | A list of languages that the browser will accept for the returned content. | Accept-Language: en-gb, en |

489