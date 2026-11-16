Note that $save_path and $session_name are required by PHP in writing a handler, even though they are irrelevant since we are using a database to store the sessions.

Since we are opening a persistent connection with the database, we don't need to do anything in the function sessionClose():

```
function sessionClose()
{
    return true;
}
```

In the function sessionRead(), we read session data for the provided key. Consequently, a simple SELECT statement will do, provided that the expiration is some time in the future:

```
function sessionRead($session_key)
{
    global $session;

    $session_key = addslashes($session_key);

    $session_session_value =
        mysql_query("SELECT session_value
        FROM sessions WHERE session_key = '$session_key'")
        or die(db_error_message());

    if (mysql_numrows($session_session_value) == 1) {
        return mysql_result($session_session_value, 0);
    } else {
        return false;
    }
}
```

Writing the session to the database requires a little bit more effort. We first attempt to INSERT a new key into the database. If this action fails, we know that there is already a key with this name in the database, and UPDATE the key instead. The expiration time is set to the default session expiration time in the php.ini file:

```
function sessionWrite($session_key, $val)
{
    global $session;

    $session_key = addslashes($session_key);
    $val = addslashes($val);
    $session = mysql_result(mysql_query("SELECT COUNT(*) FROM sessions
    WHERE session_key = '$session_key'"), 0);

    if ($session == 0) {
        $return =
        mysql_query("INSERT INTO sessions
        (session_key, session_expire, session_value)
        VALUES ('$session_key',
        UNIX_TIMESTAMP(NOW()), '$val')")
```