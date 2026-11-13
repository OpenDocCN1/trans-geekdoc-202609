Two optional arguments to headers_send allow you to find out the script name and line number where the headers were sent. This is useful if your script is giving an error but you think that the headers have not been sent at that point.

Listing 16.1 attempts to perform a redirect by using a Location header, but if it fails, it displays the reason and an alternative way to get to the destination page. If you run this on your web server, you should add some whitespace or HTML at the top of the script, outside the `<?php` tags, to make sure the headers are sent prematurely.

# Listing 16.1. Checking Whether Headers Have Been Sent

```
<?php
$destination = "http://www.lightwood.net/";
if (!headers_sent($filename, $line)) {
    header("Location: $location");
} else {
    echo "Headers were sent in line $line of $filename <br>";
    echo "<A HREF="$destination">Click here to continue</A>";
}
?>
```

# Displaying HTTP Headers

If you want to see which HTTP headers have been or will be sent, you use the `headers_list` function, which is available in PHP version 5 and above. This function returns an array that contains one header per element.

You can perform a loop on the array returned to grab each value in turn. However, in many cases, all you want to do is see the headers that are being output to check them over, and in this case, passing the array to `print_r` does the trick:

```
print_r(headers_list());
```

You need to make sure to put `<PRE>` tags around this for readability. The following is typical output:

```
Array
(
    [0] => X-Powered-By: PHP/5.0.2
    [1] => Set-Cookie: mycookie=somevalue
    [2] => Content-type: text/html
)
```

# Changing Cache Settings