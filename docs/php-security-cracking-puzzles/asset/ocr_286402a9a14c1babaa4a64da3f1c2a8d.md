# II.12.4. Determining the IP Address from a Domain Name

A domain name can be converted into the corresponding IP address with the help of the gethostbyname() function (Listing II.12.4).

# Listing II.12.4. Using the gethostbyname()

```
<?php
$hostname = "localhost";
$ip_address = gethostbyname($hostname);
echo ("The IP address of $hostname is: $ip_address");
?>
```

You only need to add the conversion code to Listing II.12.5 to obtain the necessary Web application.

# Listing II.12.5. Determining the IP address from a domain name

```
<form method=post>
<input type=text name=ip size=35>
<input type=submit value='Enter the domain name'>
</form>
<?php
if(!empty($_POST['ip']))
{
    // Connecting to the TCP socket listening to
    // port 43 on the whois.arin.net server
    // A file pointer, $sock, is returned.
    $sock = fsockopen("whois.arin.net", 43, $errno, $errstr);
    if (!$sock) exit(\$errno,$errstr);
}
else
{
    // Writing the string from the $_POST["ip"] variable
    // into the file pointer
    fputs ($sock, gethostbyname($_POST["ip"])."\r\n");
```