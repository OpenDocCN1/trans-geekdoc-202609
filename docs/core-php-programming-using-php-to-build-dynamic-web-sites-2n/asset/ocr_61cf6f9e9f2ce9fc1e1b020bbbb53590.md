# Core PHP Programming

| A | IP Address |
| ANY | Any records |
| CNAME | Canonical name |
| MX | Mail Exchanger |
| NS | Name Server |
| SOA | Start of a zone authority |

If an error occurs, FALSE is returned and the optional error_number and error_description arguments are set. They must be passed by reference, which means adding an ampersand (&) prior to the dollar sign. If the error number is returned, zero error occurred before php tried to connect. This may indicate a problem initializing the socket.

The optional timeout argument will set the number of seconds PHP will wait for a connection to be established. You may specify fractions of a second as well, if you wish.

The pfsockopen adds persistence to the fsockopen functionality.

```
//tell browser not to render this
header("Content-type: text/plain");

//try to connect to Web server,
//timeout after 60 seconds
$fp = fsockopen("www.clearlink.com", 80,
&$error_number, &$error_description,
60);

if($fp) {
    //set nonblocking mode
    set_socket_blocking($fp, FALSE);

    //tell server we want root document
    fputs($fp, "GET / HTTP/1.0");
    fputs($fp, "\r\n\r\n");

    while(!feof($fp)) {
        //print next 4K
        print(fgets($fp, 4096));
    }
    //close connection
    fclose($fp);
} else {
    //$connect was false
    print("An error occurred<BR>\n");
    print("Number: $error_number<BR>\n");
```