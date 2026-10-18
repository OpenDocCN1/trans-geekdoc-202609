
</p>
<p><input type='submit' name='submit'/></p>
</form>

<?php
// File: example20-16.php
if (isset($_POST["submit"])) {
    $strMessage = $_POST["strMessage"];
    echo "<p>" . htmlentities("Your message is " . $strMessage) . ".</p>";
}
echo "<p>This is some text further down the web page.</p>";
?>

The output from the above script is illustrated in Figure 20.8.

> **NOTE** If you don't write your code to prevent HTML injection and your application allows such user input it will only be a matter of time until this occurs either deliberately or accidentally.

## Escaping characters and SQL injection

Another form of character injection can be a little more sinister and this is known as SQL injection. To explain SQL injection we need to create a database and populate it with some data. We will create a database called 'users' with a single table called 'users'. The table fields and field types are shown in Table 20.2.

## FIGURE 20.8 HTML injection prevented

![](img/b2471264f405d17994ef173e4b9cec92_624_0.png)

## **TABLE 20.2** Table users: fields and types

| Field | Type | Other |
|---|---|---|
| Id | Int | Auto_increment, primary key |
| Username | Varchar (30) | |
| Password | Varchar (30) | |

## **TABLE 20.3** Table users: data

| Id | Username | Password |
|---|---|---|
| 1 | Alan | Smith |
| 2 | David | Regan |

And suppose that we populate this with the data shown in Table 20.3.

Now we can create a simple script to allow us to access the database:

```php
<?php
// File: example20-17.php

$strUsername = 'David';
$strPassword = 'Regan';

$dbLocalhost = mysql_connect("localhost", "root", "")
    or die("Could not connect: " . mysql_error() );

mysql_select_db("users", $dbLocalhost)
    or die("Could not find database: " . mysql_error() );
$dbRecords = mysql_query("SELECT * FROM users WHERE username = '$strUsername'");

$arrRecords = mysql_fetch_array($dbRecords);
if ($strPassword != $arrRecords["password"])
    echo "<p>Invalid Password/Username</p>";
else
    echo "<p>Password and Username match!</p>";
?>
```

The script is a basic username and password verification script. We start with a username and password which we can assume the user has entered (but for the sake of simplicity we have hard-coded into the script). We then check the database for the username, reporting an error if it is not present and finally check if the database stored password matches that supplied along with the username. You should find that the script works fine.

However, what if the username value of ‘David’ was replaced with:

```text
"' OR '1 = 1";
```

To be clear the above value of $strUsername consists of the following characters:

- Double-quote
- Single-quote
- Space character
- OR
- Space character
- Single-quote
- 1
- =
- 1
- Double-quote
- Semi-colon

$strPassword is set to blank:

```
$strPassword = '';
```

The script now looks like this:

```php
<?php
// File: example20-18.php

$strUsername = "'" OR '1=1";
$strPassword = '';
$dbLocalhost = mysql_connect("localhost", "root", "")
    or die("Could not connect: " . mysql_error() );

mysql_select_db("users", $dbLocalhost)
    or die("Could not find database: " . mysql_error() );

$dbRecords = mysql_query("SELECT * FROM users WHERE username = '$strUsername' ");

$arrRecords = mysql_fetch_array($dbRecords);
echo $arrRecords["Password"];
if ($strPassword != $arrRecords["Password"])
    echo "<p>Invalid Password/Username</p>";
else
    echo "<p>Password and Username match!</p>";
?>
```

The problem is that when it now runs, the script returns the string 'Passwords and Usernames match!' and our security has been breached through changing the SQL statement. The above works because the SQL statement with the contents of $strUsername expanded now reads:

```
SELECT * FROM users WHERE username='' OR '1=1'
```

This actually returns no records and as the password is set to null, the 'if' statements comparing the passwords evaluates to true. Therefore the script thinks that the username and password matches.

SQL injection can be prevented through the use of the mysql_escape_string() function:

```
mysql_escape_string ( string unescaped_string )
```

This function escapes quotation characters in the SQL string so that, in our example, the query looks like this:

```
SELECT * FROM users WHERE username='\' OR \'1=1'
```

The escaped characters remove the danger of the quotes being interpreted incorrectly by the SQL parser. In addition, it is important to ensure that you include code which checks to see if any records have been returned from the database by your query. If you are expecting one and none are returned there is a potential problem. We can use the mysql_num_rows() function to do this, for example:

```
if (mysql_num_rows($dbRecords) != 1)
    echo "<p>Username not found!</p>";
```

Our amended script now looks like this and removes the possibility that SQL injection will be able to circumvent our login security:

```php
<?php
// File: example20-19.php

$strUsername = '' OR '1='1';
$strPassword = '';

$dbLocalhost = mysql_connect("localhost", "root", "")
    or die("Could not connect: " . mysql_error() );

mysql_select_db("users", $dbLocalhost)
    or die("Could not find database: " . mysql_error() );

$strUsername = mysql_real_escape_string($strUsername);

$dbRecords = mysql_query("SELECT * FROM users WHERE username = '$strUsername' ");

$arrRecords = mysql_fetch_array($dbRecords);

if (mysql_num_rows($dbRecords) != 1)
    echo "<p>Username not found!</p>";
else {
    if ($strPassword != $arrRecords["Password"])
        echo "<p>Invalid Password/Username</p>";
    else
        echo "<p>Password and Username match!</p>";
}
?>
```

## 20.4 User authentication and passwords

### Checking the referrer

We briefly introduced the concept of checking the referrer page in an earlier chapter, but here is a recap. Consider the following script:

```php
<?php
// File: example20-20.php
```

```
if(isset($_POST["submit"])) {
    $strUserPass = array ( "john" => "red",
                           "simon" => "green",
                           "liz" => "blue",
                           "david" => "yellow");

    if ($strUserPass[$_POST["strUsername"]] == $_POST["strPassword"])
        header("location: example20-21.php");

    echo "<h1>Incorrect Username and/or password!</h1>";
}
?>

<form method="post" action="">
<p>
<label for="strUsername">Username: </label>
<input type="text" name="strUsername" id="strUsername"/></p>
<p>
<label for="strPassword">Password: </label>
<input type="password" name="strPassword" id="strPassword"/></p>
<p><input type="submit" name="submit" /></p>
</form>
```

The above script outputs a form consisting of three elements: a text field, a password field and a submit button. The user enters a username and password and these are then checked against a simple array of usernames and passwords. If a match is found then the user is redirected to a new page like this:

```php
<?php
// File: example20-21.php

if ($_SERVER["HTTP_REFERER"])
    if ($_SERVER["HTTP_REFERER"] != "http://localhost/Book/example20-20.php")
        header("location: example20-20.php");
?>

<h1>Well, done you are correctly logged in!</h1>
```

Obviously we don't want the user or some malicious person to be able to jump directly to the second page by typing into the browser the address of the second page and completely bypassing the security we have put in place, for example:

http://localhost/example20-21.php

To stop this we have included the following lines at the top of the second script:

```
if ($_SERVER["HTTP_REFERER"])
    if ($_SERVER["HTTP_REFERER"] != "http://localhost/Book/example20-20.php")
        header("location: example20-20.php");
```

These check the value ‘HTTP_REFERER’ which is held in the associative array $_SERVER. In this instance we need to check whether the value stored is equal to:

http://localhost/Book/example20-20.php

This value indicates the address of the page from which the current page was launched. If the user correctly completed the username and password login form then this will be set
