# Chapter II.10: Hypertext Transfer Protocol 323

When working with sockets, the program has to do all of the dirty work, sending HTTP requests to the server and receiving and processing responses to them. In the script, the call to the fsockopen() function is wrapped in a user-defined get_content() function. This function accepts two parameters: $hostname is the name of the server, with which the connection is being established, and $path is the path to the target page relative to the server name.

When working with the fsockopen() function, you should remember that the server name, specified in the first parameter, must not contain the http:// prefix or the port number. Implementing the protocol is the programmer's responsibility, and the port is specified in the second parameter of the function.

After a connection with the server is opened, an HTTP GET request is formed in the $headers variable. When all variables are set, the headers in Listing II.10.2 are sent to the server.

# Listing II.10.2. The headers sent to the www.php.net server

```
GET /HTTP/1.1\r\n
Host: www.php.net\r\n
Connection: Close\r\n\r\n
```

After the headers are sent, the reply is read by the fgets() function in blocks of 1024 bytes until the end of the file character is detected by the eof() function. After the entire file is read, the function returns the result, which is displayed in the browser window.

In the first line of code in Listing II.10.2, the index file of the server's root directory (/) is requested from the server using the GET method over HTTP 1.1. The second line of code provides the server's address, and the third one tells the server to close the connection after the data is transferred.

Instead of the root directory (/), the address of a page on the server can be sent. For example, sending /downloads.php will load this page. Browsers work on this principle. When a user requests a page by clicking a link, the browser extracts the part of the address following the domain name and sends an HTTP request plugging in this part of the address after the GET keyword.

These three lines are equivalent to sending http://www.php.net/ to the browser. The results of executing the script in Listing II.10.1 are shown in Fig. II.10.1.