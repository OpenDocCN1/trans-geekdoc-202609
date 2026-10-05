# Chapter II.12: The Whois Service

![](bbox=[0.037, 0.196, 0.866, 0.358])

# II.12.1. Determining Ownership of American IP Addresses

The problem is solved by using the fsockopen() function to connect to port 43 of the whois.arin.net server and then receiving and displaying the server's reply. A script for this is shown in Listing II.12.1.

+   II.12.1. Determining ownership of American IP addresses

```
<form method=post>
<input type=text name=ip size=35>
<input type=submit value='Enter the IP address'>
</form>
<?php
if(!empty($_POST['ip']))
{
  // Connecting to the transmission control protocol (TCP) socket
  // listening to port 43 on the whois.arin.net server
  // A file pointer, $sock, is returned.
$sock = fsockopen("whois.arin.net", 43, $errno, $errstr);
```