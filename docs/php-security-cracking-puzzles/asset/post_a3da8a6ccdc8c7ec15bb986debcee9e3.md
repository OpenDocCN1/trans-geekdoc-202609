
```php
}
// Closing the connection
close($sock);
}
?>
```

## II.12.3. Following Up with the Referral Server

The main Whois service has no information about the requested IP address, it provides, in the ReferralServer field, a link to the regional Whois service responsible for the given range of IP addresses. Therefore, the process of accessing the Whois service should be implemented as a separate function named, for example,whois(). The function accepts two parameters: the address of the Whois service and the target IP address. If the returned report contains a link to a referral service, the whois() function is called recursively. A corresponding script is shown in Listing II.12.3.

-   II.12.3. Recursively calling the referral server

```php
<center>
<form method=post>
<input type=text name=ip size=35>
<input type=submit value='Enter the IP address'></form>
</center>
<?php
if(!empty($_POST['ip'])) echo whois("whois.arin.net"
```

```php
fputs($sock, $ip."r\n");
// Reading from the file pointer
$text = "";
while (!feof($sock)) {
    $text = fgets($sock, 128)."<br>";
}
// Closing the connection
close($sock);
```

```php
// Looking for the referral server
$pattern = "ReferralServer: whois://([^\n<]+)|i";
preg_match($pattern, $text, $out);
if (!empty($out[1])) return $out[1], $ip);
else return $text;
```

```php
}
?>
```

![](img/a893312ec68b8170fe567f785e95c06e_360_0.png)

Fig. II.12.2. The ownership information for IP address 213.115.162.82

# Part II: Solutions

The script always starts the search with the ARIN Whois, moving on to referral services if necessary. The List of Whois visited by the script is displayed before the final report. Thus, a report for IP address 213.115.162.82, belonging to MySQL AB, may look as shown in Fig. II.12.2.

As can be seen from Fig. II.12.2, the script visits two Whois: ARIN and RIPE.

A report for IP address 192.131.90.161, corresponding to the network name http://www.w3c.org, may look as shown in Fig. II.12.3. The report shows that the information for this IP address was found at the Asia Pacific Network Information Centre (APNIC) Whois service http://www.whois.apnic.net).

![](img/a893312ec68b8170fe567f785e95c06e_361_0.png)

## II.12.4. Determining the IP Address from a Domain Name

A domain name can be converted into the corresponding IP address with the help of the gethostbyname() function (Listing II.12.4).

# Listing II.12.4. Using the gethostbyname()

```php
<?php
$hostname = "localhost";
$ip_address = gethostbyname($hostname);
echo ("The IP address of $hostname is: $ip_address");
?>
```

You only need to add the conversion code to Listing II.12.5 to obtain the necessary Web application.

# Listing II.12.5. Determining the IP address from a domain name

```php
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
    if (!$sock) exit($errno,$errstr);
}
else
{
    // Writing the string from the $_POST["ip"] variable
    // into the file pointer
    fputs ($sock, gethostbyname($_POST["ip"])."\r\n");
```

```php
// Reading from the file pointer
while (!feof($sock)) {
    echo (str_replace(":","&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;",",gets($sock, 128))."<br>");
}
// Closing the connection
close($sock);
?>
```

## II.12.5. Determining the Domain Name from an IP Address

This problem can be solved with the help of the gethostbyaddr() function, which returns the domain name of the corresponding IP address (Listing II.12.6).

### ### Listing II.12.6. Using the gethostbyaddr() function

```php
<?php
echo gethostbyaddr("81.19.69.28");
?>
```

## II.12.6. Is That Domain Name Taken?

The Whois service can also be used to determine whether a particular domain name is taken. To this end, the domain name must be sent to port 43 of the Whois server. However, the task is complicated by each first-level domain name being serviced by its own Whois server, names in the .com, .edu, .net, and .org domains must be checked with the whois.verisign-grs.net server, whereas names in the .uk domain are checked with the whois.thnic.net server. Consequently, to cover a sizable number of domain names, numerous Whois servers will have to be consulted. First, create a script to check domain names in the .com zone (Listing II.12.7).

# Chapter II.12: The Whois Service 351

Listing II.12.7. Checking whether the mysql.com domain name is taken

```php
<?php
// Setting unlimited execution time for the script
set_time_limit(0);
// The domain name
$domain = "microsoft.com";
// Consulting the Whois server and obtaining
// information about the domain name
$fp = fsockopen("whois.verisign-grs.net", 43);
futs($fp, "$domain\r\n");
$str = "";
while (!feof($fp)) {
  $str .= fgets($fp, 128);
}
close($fp);
// Displaying the answer
echo "<pre>";
echo $str;
echo "</pre>";
?>
```

The results of the script's operation are shown in Fig. II.12.4.
The answer contains volumes of useful information about the domain name's owner and its expiration dates. In particular, the mysql.com domain name was registered February 3, 1999; was renewed January 14, 2005; and will belong to the owner until February 3, 2013. If the registration is not renewed before the expiration date, anyone can buy it.

The latter matter is unlikely to happen, because registrars repeatedly notify owners before a domain name registration expires. Nevertheless, if you own a desirable Web resource, don't procrastinate the domain name registration; cybersquatters will buy it within hours, not minutes. If a domain is not registered (e.g., mysql.com), the answer from the Whois server may look like Fig. II.12.2.

![](img/a893312ec68b8170fe567f785e95c06e_364_0.png)

# 352 Part II: Solutions

![](img/a893312ec68b8170fe567f785e95c06e_365_0.png)

```php
Whois Version 1.3

Domain names in the .com and .net can be registered with many different registrars. Go to http://www.internic.net for detailed information.

Domain Name: MYSQL.COM
Registrar: NETWORK SOLUTIONS, LLC.
Whois Server: http://www.networksolutions.com
Name Server: DNS2.COM
Name Server: DNS1.COM
Status: REGISTRAR-LOCK
Updated Date: 14-jan-2005
Creation Date: 03-feb-1999
Expiration Date: 03-feb-2013
```

Fig. II.12.4. The Whois server's answer to the domain name request

# 353 Chapter II.12: The Whois Service

By the time this book is published, the mysql3.com domain name may be registered.

Unfortunately, the reply format is not standardized, and different Whois servers give a different answer for an unregistered domain name. Consequently, answers from each Whois server must be processed individually. This task can be implemented with the help of the script shown in Listing II.12.8.

The complete source code for the script can be found on the accompanying CD-ROM.

# Listing II.12.8. A universal script for domain names

```php
<?php
// Setting unlimited execution time for the script
set_time_limit(0);
$servers = array(
array("ac", "whois.nic.ac", "No match"),
....
array("com", "whois.verisign-grs.net", "No match"),
array("au", "whois.aunic.net", "No Data Found"),
array("com.br", "whois.nic.br", "No match"),
....
array("com.cn", "whois.cnnic.net.cn", "No entries found"),
array("com.eg", "whois.ripe.net", "No entries found"),
array("com.hk", "whois.hnic.net.hk", "No Match for"),
array("com.mx", "whois.nic.mx", "Nombre del Dominio"),
array("com.ru", "whois.ripn.ru", "No entries found"),
array("com.tw", "whois.tnic.net", "NO MATCH TIP"),
....
array("zj.cn", "whois.cnnic.net.cn", "No entries found")
);

// The domain name
$domain = "mysql.com";
```
