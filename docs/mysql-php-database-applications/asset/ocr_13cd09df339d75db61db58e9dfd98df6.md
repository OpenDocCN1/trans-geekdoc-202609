```
}
else
{
	$op = 'is';
}
}
else
{
	if (strstr($op, '!='))
	{
		$op = '<>';
	}
}
return $op;
)
```

# Functions from /content/functions

These functions will be used throughout the application. This section will contain many references to Chapter 9 because in that chapter we first used many of the functions we'll call upon here.

# connect_validate_login()

In this example we are using MySQL's own user and password tables to set up accounts that can be used with this application. The success or failure of the attempted connection to a MySQL server tells us if a username is valid or not. We do this by splitting the authenticate() function used in previous examples into several pieces, so that we can drop in our own validation code—in this case, connect_validate_login().

```
function connect_validate_login()
{
	// if we haven't started a session yet, the references to
	$_SESSION
	// will come up invalid, so start one if we need to.
	check_session();
	if (!isset($_SESSION))
	{
		global $_SESSION;
	}
}

static $__defaults = array(
	'application' => 'content'
	, 'username' => NULL
	, 'password' => NULL
```