# FIGURE 5.2
Example secure page that is only visible if the user is logged in

![](bbox=[0.102, 0.182, 0.422, 0.402])

# Server integration for login module

The PHP code for the login module is the next part in the process.

```
<?php

error_reporting(0); // disable all error reporting

$user = $_POST['user'];
$pass = $_POST['pass'];

// sample password response, normally
// would be sent from database
$storedPassword = "83e4a96aed96436c621b9809e258b309";

if(!empty($_POST))
{
	if($user == "guest" && md5($pass) == $storedPassword)
	{
		print "resultCode=LOGGED_IN";
	}
	else
	{
		print "resultCode=NOT_LOGGED_IN";
	}
}
?>
```