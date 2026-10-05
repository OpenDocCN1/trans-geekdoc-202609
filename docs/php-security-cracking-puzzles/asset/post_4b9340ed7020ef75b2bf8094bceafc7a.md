
```php
$header = "";
foreach($listemail as $email)
{
    $header .= "Bcc:".trim($email)."\r\n";
}
$header .= "\r\n";
mail(trim($listemail[0]), $theme, $body, $header);
```

As can be seen in Listing II.11.6, a loop is only used to form recipient mail addresses. The mail() function sending messages to these addresses is called only once.

## II.11.4. Preventing Mass Mailing

The most acceptable way to implement a 5-minute delay is to register the IP addresses of all users who access the mail service. Because the delay is only 5 minutes long, users accessing the Internet from one IP address are unlikely to experience any inconveniences.

The easiest way to implement this solution is to use MySQL. Create a table named mailerlist, composed of the following two columns:

- A BIGINT field for storing IP addresses
- putdate — A DATETIME field for the last access time to the mail server from the IP address stored in the corresponding ip field

The CREATE TABLE query for creating such a table is shown in Listing II.11.7.

## Listing II.11.7. A query to create the mailerlist

```php
CREATE TABLE mailerlist (
ip bigint(20) NOT NULL default '0',
putdate datetime NOT NULL default '0000-00-00 00:00:00'
) TYPE = MyISAM;
```

After the table is created, all that remains is to store the IP addresses of users accessing the mail service and the time, at which they do. When a user attempts to use the mail service again, the table is checked for the given IP address.

IP addresses are stored as 8-byte integers. IP addresses are converted from the xxx.xxx.xxx.xxx format into the integer format using the MySQL INET_ATON() function; the reverse conversion is done using the INET_NTOA() function.

## Listing II.11.8. Checking user IP addresses

```php
<?php
// Connecting to the database
include "config.php";
// Deleting expired records
$query = "DELETE FROM mailerlist\nWHERE PUTDATE > NOW() - INTERVAL 5 MINUTE";
if(!mysql_query($query)) exit(mysql_error());
// Checking whether the user mailed an
// messages within the last 5 minutes
$query = "SELECT COUNT(*) FROM mailerlist\nWHERE ip = INET_ATON($SERVER[REMOTE_ADDR])";
$cnt = mysql_query($query);
if(!$cnt) exit(mysql_error());
$total = mysql_result($cnt,0);
if($total > 0)
exit("Only one message every five minutes is allowed.\nTry to use the service later.");
// If the message is posted, store the IP address
// of the user and the posting time.
if(mail($mail, $theme, $body)) {
    $query = "INSERT INTO mailerlist\nVALUES(INET_ATON($SERVER[REMOTE_ADDR]), NOW())";
    if(!mysql_query($query)) exit(mysql_error());
}
else {
    exit("Sorry, the message was not posted.");
}
?>
```

When the script shown in Listing II.11.8 is executed, the first SQL query deletes all records in the mailerlist table that are older than 5 minutes. Next, the script checks whether the IP address of the user attempting to access the mail service (stored in the $_SERVER['REMOTE_ADDR'] array element) is still in the table. If the check is positive, the script's execution is terminated. Otherwise, the script calls the mail() function, which in case of successful posting enters the IP address of the user and the posting into the mailerlist table.

## II.11.5. Sending Email Using SMTP Relay

PHP has no built-in functions for working with simple mail transfer protocol (SMTP) servers. A custom function for posting email messages using a remote relay is shown in Listing II.11.9.

Messages are sent in this way only through a public mail relay or mail relays that allow the sender's IP address to be used for mailing. Of late, however, as a part of an antispam campaign, public relayers have been closed and administrators of corporate networks and system administrators do not allow messages to be mailed from addresses that do not originate within their networks.

## Listing II.11.9. Posting a message using a remote SMTP server

```php
<?php
// A message posting function:
// opens a socket, connects a dialog with the server,
// writes data, closes the socket
function send($server, $to, $from, $subject="", $msg, $headers="")
{
    // Forming the header fields
    $headers =
    "To: $to\nFrom: $from\nSubject: $subject\nX-Mailer: My Mailer\n$headers";
    // Connecting to the server to port 25;
    // $fp variable contains
    // the link identifier.
    $fp = fsockopen($server, 25, &$errno, &$errstr, 30);
    if (!$fp) die("Server $server. Connection failed: $errno, $errstr");
    // If the connection attempt is successful,
    // write data to the socket;
// i.e.
```

First, the script uses the $fsockopen() function to open a connection with the email relay of a remote SMTP server on port 25. Then the SMTP commands described earlier in the chapter are sent to server. Message text must end with a blank line on a separate page; therefore, the message posting string must have a period in it:

```php
fputs($fp, "$msg\n.\r\n");
```

## II.11.6. Determining the Mail Relay's Address

The names of the mail relays of a specific SMTP server can be determined by the script in Listing II.11.10. The script displays a list of the mail relays and their priorities.

## Listing II.11.10. Obtaining a list of mail relays

```php
<?php
// An email address
$email = "mail@yandex.ru";
// Breaking the address into a two-element array:
// the mailbox name and the server name
$arr = explode("@", $email);
// Placing the mail server name into the $host variable
$host = $arr[1];
// Determining the mail relays of the $host server and
// displaying them, indicating the priorities
$relays = getmxrecords($host);
foreach($relays as $relay) {
    echo $relay . "\n";
}
?>
```
