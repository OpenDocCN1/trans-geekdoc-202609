
changed at all. Constants do not run into the same scope problems that are encountered with variables, so you can use them within functions without having to pass them in as arguments or worry about declaring globals. After you run the define() function, the constant DEFAULT_LIMIT will be available everywhere in the application.

We'll use DEFAULT_LIMIT to decide the number of entries that will be viewable on each page. You are welcome to change the value if you would like to see a larger number.

```php
// constants
define('DEFAULT_LIMIT', 2);
```

// global variables
// we'll look for offset in the $_REQUEST superglobal because it
// could be coming in from either the URL or a form. $_REQUEST is
// a combination of GET, POST, and cookie-based values.

```php
$offset = array_key_value($_REQUEST,'offset',0);
```

If you are putting together a query using a constant, you will have to end your quoted string in order to make use of the constant value. For example,
`$query = "select * from db_name limit DEFAULT_LIMIT"`
will confuse MySQL, because PHP has not replaced the name of the constant with its value. However, this will work:
`$query = "select * from db_name limit " . DEFAULT_LIMIT`

PHP has many built-in constants you can use within your scripts, like the DIRECTORY_SEPARATOR constant seen in the header.php file. A list of constants is included in the PHP manual at http://www.php.net/manual/language.constants.php.

## FROM /GUESTBOOK2K/FUNCTIONS.PHP

On top of the standard PHP functions are those that were created for the Guestbook 2003 application. The following sections take a look at the guestbook library.

### MYSQL_DBCONNECT()
This is a slightly prettier version of the original dbconnect() function included in the first edition of this book.

```php
function mysql_dbconnect()
{
    $link = @mysql_connect('localhost','nobody','ydobon');
    if ($link == FALSE)
    {
        $private_error = 'mysql_dbconnect: could not open connection
to mysql:'
        .'<li>errno:'.mysql_errno()
        .'<li>error:'.mysql_error()
        ;
        error_log($private_error, 0);
        die('Error: could not connect to database server. Please
contact the system administrator.');
        exit;
    }
    if (!@mysql_select_db('guestbook2k'))
    {
        $private_error = 'mysql_dbconnect: could not select
guestbook database:'
        .'<li>errno:'.mysql_errno()
        .'<li>error:'.mysql_error()
        ;
        error_log($private_error, 0);
        die('Error: could not connect to guestbook database. Please
contact the system administrator.');
        exit;
    }

    return $link;
}
```

The @ in front of the calls to mysql_connect() and mysql_select_db() tells PHP not to print out any errors or warnings that happen inside those functions. That enables us to write out the detailed errors to the error log while sending a simpler error to the user.

### SAFE_MYSQL_QUERY()
This function will save you from pulling your hair out when you're trying to get your queries right.

```php
function safe_mysql_query ($query='')
{
    if (empty($query))
    {
        return FALSE;
    }

    $result = @mysql_query($query);
    if ($result == FALSE)
    {
      // if there was an error executing the query, write out the
      // details to the error log
      $private_error = 'ack! query failed: '
        .'<li>errno='.mysql_errno()
        .'<li>error='.mysql_error()
        .'<li>query='.$query
        ;
      error_log($private_error, 0);
      // send a generic error message to the user
      die('There was an error executing a query. Please contact
      the system administrator.');
      exit;
    }
    return $result;
}
```

Throughout the application, we will run our queries through this function. This
way, if the query fails for some reason, we can get a pretty good idea of what hap-
pened. This is another example of safe coding. After troubleshooting your code, we
won't run into these problems often, but if a change is made somewhere (perhaps
without our knowledge) we'll get a pretty good idea of what's going on.

### GUESTBOOK_AUTHENTICATE()
This function will require the user to enter a
name and password and will then validate those against the guestbook_admin
table in the database. If the username and password don't match any valid entries,
or if the user (by hitting Cancel, say) doesn't submit them, an error message will be
displayed.

```php
function guestbook_authenticate($realm = 'Guest Book Administration'
  , $errmsg = 'You must enter a valid name and password to access
  this function'
  )
{
// check if we can use HTTP authentication - as of now, that
// means checking if we are running as an Apache module.

    $http_auth_OK = (php_sapi_name()) == 'apache';

// $_SERVER['PHP_AUTH_USER'] and $_SERVER['PHP_AUTH_PW'] are values
// supplied by PHP, corresponding to the user name and password
// the user has entered in the pop-up window created by an HTTP
// authentication header. If no authentication header has ever been
// sent, these variables will be empty. If we are not using HTTP
// authentication, the login form will create entries in the
// $_POST superglobal with the same names.

    foreach (array('PHP_AUTH_USER','PHP_AUTH_PW') as $v)
    {
        if (!isset($_SESSION[$v]))
        {
            if ($http_auth_OK)
            {
                $_SESSION[$v] = array_key_value($_SERVER,$v,'');
            }
            else
            {
                $_SESSION[$v] = array_key_value($_POST,$v,'');
            }
        }
    }

    $found_user = 0;
    if (!empty($_SESSION['PHP_AUTH_USER']))
    {
        // ignore case, even if MySQL has been set to
        // pay attention to it
        $query = <<<EOQ
select 1 from guestbook_admin
where password = sha1(lower('{$_SESSION['PHP_AUTH_PW']}'))
and lower(username) = lower('{$_SESSION['PHP_AUTH_USER']}')
EOQ;
        $result = safe_mysql_query($query);
        if ($result)
        {
            list($found_user) = mysql_fetch_row($result);
        }
        else
        {
            // if the query didn't work at all (which should have been caught by
            // safe_mysql_query()) in theory), we're not going to be able to
            // confirm the password, so fail.
            $private_error = "problem running authentication query
($query): "
                .mysql_error()
                ;
            error_log($private_error,0);
            die('Database error: could not check password. Please
contact the system administrator.');
            exit;
        }
        // if the query ran but didn't find a match for the user name
        // and password, $found_user will not be set to anything.
        // if this is so, have the user try again.
        if ($found_user == 0)
        {
            $errmsg .= <<<EOQ
<li>Could not find entry for username {$_SESSION['PHP_AUTH_USER']}
        please try again.
EOQ;
        }
    }
    if ($found_user == 0)
    {
        if ($http_auth_OK)
        {
            // Send a WWW-Authenticate header, to perform HTTP authentication.
            Header("WWW-Authenticate: Basic realm=\"$realm\"");
            Header("HTTP/1.0 401 Unauthorized");
            // The user should only see this after hitting the 'Cancel' button
            // in the pop-up form.
            print $errmsg;
            exit;
        }
        else
        {
            // Print out an HTML form to obtain a name and password
            // for authentication.
            if (!empty($errmsg)) { $errmsg = "<p>$errmsg</p>"; }

            print <<<EOQ
<h2>$realm</h2>
$errmsg
<form method=post>
Username: <input type=text name="PHP_AUTH_USER"
value="{$_SESSION['PHP_AUTH_USER']}">
<br>
Password: <input type=password name="PHP_AUTH_PW"
value="{$_SESSION['PHP_AUTH_PW']}">
<br>
<input type=submit>
</form>
EOQ;

            exit;
        }
        // should never get here
        $private_error = 'authenticate: error: continued after
requesting password';
        error_log($private_error);
        die('System error: please contact the system
administrator.');
        exit;
    }
    else
    {
        print <<<EOQ
<p><b>Editing as {$_SESSION['PHP_AUTH_USER']}</b></p>
EOQ;
    }
}
```

If PHP is installed as an Apache module, guestbook_authenticate() will send out a 401 HTTP response code. This header forces the browser to open the username and password box shown in Figure 8-7.

The values entered into these text fields are set by PHP to the variables $_SERVER['PHP_AUTH_USER'] and $_SERVER['PHP_AUTH_PW']. If PHP isn't running as an Apache module, an ordinary HTML form is displayed, with text fields using the same names. The text fields will be returned as values in $_POST.

When the user submits either form the same page is run, and guestbook_authenticate() is called again. Now that it has a possible username and password it can query MySQL to check if the values are stored in the database. If they are not, the password form is displayed again.
