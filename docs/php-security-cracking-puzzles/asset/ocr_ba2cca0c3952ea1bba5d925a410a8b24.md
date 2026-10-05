# Chapter II.10: Hypertext Transfer Protocol 325

![](bbox=[0.109, 0.113, 0.891, 0.453])

The results of the script in Listing II.10.3 are shown in Fig. II.10.2. Even though the script loads the page from the http://www.php.net portal, the address in the address field points to the script located on the local host. Thus, the script plays the role of the browser here.

# II.10.2. Obtaining HTTP Headers from a Server

To receive only the headers of an HTTP reply, the function in Listing II.10.1 is modified as shown in Listing II.10.4.

# II.10.4. A script for extracting the headers from an HTTP reply

```
<?php\// A function to extract the HTTP headers\function get_content($hostname, $path)
{
    $line = ""
    // Establishing a connection with the host
    // whose name was passed in the $hostname variable
    $fp = fsockopen($hostname, 80, $errno, $errstr, 30);
```