The header of the e-mail needs to follow the specification that defines how e-mail is to be constructed and the $from value needs to be valid, even though the actual e-mail address used doesn't.

```
// Mail headers, do not alter
$mailHeaders = "From: " . $from . " <> \n\n";
```

When all of the variables and e-mail information have been created, the actual e-mail can be sent. This is done by making a call to the mail() function, passing along the information that was built in the previous steps.

```
if(mail(
$to,
"Automated response from Site Monitor",
$emailInfo,
$mailHeaders))
{
print "result=success";
}
```

![](bbox=[0.1, 0.42, 0.25, 0.45])

The mail() function returns a success message if the function is properly called. The function does not know the status of the actual sending of the e-mail.

Here is the completed PHP code for monitor.php:

```
<?php

require('dbconn.php');

$action = (isset($_GET['action'])) ? $_GET['action'] : "";

if($action == "getsites")
{
$result = mysql_query("SELECT * FROM siteMonitor WHERE active=1");

$xml = "<?xml version=\"1.0\" ?>\n";
$xml .= "<sites>\n";
while($row = mysql_fetch_array($result))
{
$xml .= sprintf("<t<site name=\"%s\" uri=\"%s\" />\n",
$row['name'],
$row['uri']);
}

$xml .= "</sites>";

header("Content-type: text/xml");
```