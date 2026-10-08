# Implementing User Authentication

```
// if ok, put in db
$result = $conn->query('insert into user values
    ('.$username.', shal('.$password.'), '.$email.')');
```

```
if (!$result) {
    throw new Exception('Could not register you in database - please try again
later.');
}
```

```
return true;
```

There is nothing particularly new in this function; it connects to the database you set up earlier. If the session is taken or the database cannot be updated, it will throw an exception. Otherwise, it will update the database and return true.

Note that you are performing the actual database connection with a function called db_connect(), which we wrote. This function provides a single location that contains the username and password to connect to the database. That way, if you change the database password, you need to change only one file in the application. The db_connect() ) function is shown in Listing 27.10.

Listing 27.10 db_connect() Function from db_fns.php—This Function
Connects to the MySQL Database

```
<?php
function db_connect() {
    $result = new mysqli('localhost', 'bm_user', 'password', 'bookmarks');
    if (!$result) {
        throw new Exception('Could not connect to database server');
    } else {
        return $result;
    }
}
?>
```

When users are registered, they can log in and out using the regular login and logout pages.
You build them next.

# Logging In

If users type their details into the form at login.php (see Figure 27.3) and submit it, they will be taken to the script called member.php. This script logs them in if they have this