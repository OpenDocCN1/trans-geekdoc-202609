# Chapter II.10: Hypertext Transfer Protocol

# II.10.4. Sending Data Using the POST Method

When accessing a server using the POST method, in addition to the HTTP POST /path HTTP/1.1 header, the Content-Length header containing the number of data bytes must be sent.

Unlike the GET method, the POST method sends data not in the request line but in the data area following the headers. Sending several variables is analogous to doing in the GET method: Groups of var_name = var_value are joined using the ampersand character (&). Because HTML form accepts parameters in the form name = Igor, pass = password, the data string may look like follows:

```
name = Igor & pass = password
```

Keep in mind that the data are sent in the text format; thus, any national characters must be encoded using the urlencode() function.

# II.10.7. Sending data via sockets using the POST method

```
<php
$hostname = "localhost";
$path = "/test2/handler.php";
$line = "";
// Establishing a connection with the host
// whose name was passed in the $hostname variable
$fp = fsockopen($hostname
```