# URLs

A URL (Uniform Resource Locator) is an address on the World Wide Web. Every Web page has its own URL or address. The URL is used by the Web server to find the Web page and send it to a browser.

The format of a URL is

```
HTTP://servername:portnumber/path#target?string=string
```

Here's a breakdown of the parts that make up the URL:

HTTP://servername: This tells the server that the address is a Web site and gives the name of the computer where the Web site is located. Other types of transfer can be specified, such as FTP (File Transfer Protocol), but these aren't related to the subject of this book. If this part of the URL is left out, the Web server assumes that the computer is the same computer that the URL is typed on. Valid choices for this part are HTTP://amazon.com or HTTP://localhost. Note: HTTP doesn't have to be in uppercase letters.

:portnumber: The Web server exchanges information with the Internet at a particular port on the computer. Most of the time, the Web server is set up to communicate via port 80. If the port number isn't specified, port 80 is assumed. In some unusual circumstances, a Web server may use a different port number, in which case the port number must be specified. The most common reason for using a different port number is to set up a test Web site on another port that's available only to developers and testers, not customers. When the site is ready for customers, it is made available on port 80.

path: This is the path to the file, which follows the rules of any path. The root of the path is the main Web site directory. If the path points to a directory, rather than a file, the Web server searches for a default file name, such as default.html or index.html. The person who administers the Web site sets the default file name. The path /catalog/show.php indicates a directory called catalog that is in the main Web site directory and a file named show.php. The path catalog/show.php indicates a directory called catalog that is in the current directory.

#target: An HTML tag defines a target. This part of the URL displays a Web page at the location where the target tag is located. For instance, if the tag <a name="target"></a> is in the middle of the file somewhere, the Web page will be displayed at the tag rather than at the top of the file.

?string=string: The question mark allows information to be attached to the end of the URL. The information in forms that use the get method is passed at the end of the URL in the format fieldname=value. You can add information to the end of a URL to pass it to another page. PHP automatically gets information from the URL and puts it into built-in arrays. You can pass more than one string=string pair by separating each pair with an ampersand (&); for example, ?state=CA&city=home.