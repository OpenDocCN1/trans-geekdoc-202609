The content/header.php file, which is included in every page in the content-management system, contains the following code:

```
require('authenticate.php');
```

Because we have placed the administrative code in a subdirectory of the main content directory, this one statement will include either the basic authenticate.php file (for normal users) or the content/admin/authenticate.php file (for administrators). Here are the contents of the basic authenticate.php file.

```
<?php

check_session();
if (!isset($_SESSION))
{
	global $_SESSION;
}

$realm = 'Netsloth Content Management';
$message = 'You must enter a valid name & password to access this function';

$submit = array_key_value($_REQUEST, 'submit', NULL);
if ($submit == 'logout')
{

	logout();
}

$username = session_auth(array(
	'realm' => $realm
	, 'message' => $message
	, 'validate_function' => 'connect_validate_login'
));

$result = db_connect()->getRow(
	'select u.*, if(a.username is null, 0, 1) as is_admin
	from users u left join admin a on u.username = a.username
	where u.username = ? '
	, array($username)
	, DB_FETCHMODE_ASSOC
);
foreach ($result as $k => $v)
{
```