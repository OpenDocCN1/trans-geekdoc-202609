# login method

The first and only method in this class is login. This method accepts two arguments: the username and password to validate. The first part of this method is to create a new connection to the database:

```
/**
 * Check user auth
 * @access remote
 * @returns status of user login attempt
 */
function login($user, $pass)
{
	$link = $this->getConnection();
}
```

When the database connection is established, you can mark the user as not logged in. This prevents any possible hacking attempts that could accidentally make a user log in.

```
$loggedIn = false;
```

Next is the SQL query that attempts to validate the username and password combo. The password is passed into the md5 function because Flash sends the password in clear text, but the database stores the md5 result.

```
$query = sprintf("SELECT * FROM users WHERE username='%s' AND password=MD5('%s')", $user, ($pass));
```

The next step is to make the database call and store the response in the $result variable, as shown in the following code:

```
$result = mysql_query($query, $link);
```

Once the response is stored, a conditional statement is used to determine if any rows were returned. If a row is returned, it means the data is valid and the user has been authenticated based on the credentials he or she passed along.

When a valid response is found, the $loggedIn variable is set as true to inform Flash that the user is, in fact, valid and has now successfully logged in.

```
if(mysql_num_rows($result) > 0)
{
	$loggedIn = true;
}
```

The last step is to return the result so Flash can act accordingly.

```
return array('response' => $loggedIn);
```