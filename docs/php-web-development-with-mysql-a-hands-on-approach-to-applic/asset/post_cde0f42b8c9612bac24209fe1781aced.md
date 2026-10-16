
You want to do three things:

- 1. Connect to the database
- 2. Query the database
- 3. Close the connection to the database

Before we do these three things, let's create two variables for our first and last names:

```
$first_name = $_POST['first_name'];
$last_name = $_POST['last_name'];
```

### Opening the Database Connection

Right after the else { statement (but before the closing ?>) we connect to the database using the mysqli_connect()⁶ function. This function takes four string parameters (by default): host, username, password, and database_name. Our mysqli_connect() statement should look like this:

```
$dbc = mysqli_connect('localhost', 'testuser', 'testuser', 'FullName')
    or trigger_error('Error connecting to MySQL server.', E_USER_ERROR);
```

> It is not a good idea to have our password entered in clear text in our source code (especially if we accidentally post it up on some git repository). The better way to manage this is to use a configuration or environment variable.

If the call to mysqli_connect() is successful, $dbc will contain a resource connection referring to our database. It is a good idea to use the or trigger_error() statement so that you can determine if you run into a problem connecting to your database. If there is a failure, you will see the error message displayed on the web page, and execution of your PHP script will halt.

> Why not or die()? You're likely to run into legacy code or old tutorials online that use the die() statement to stop and display a message. Since it halts the execution of the PHP interpreter, your error messages are not logged to PHP's error logs and not passed to any custom error handlers. Furthermore, the only way to be notified that a user ran into an error is to wait for someone to report an outage. trigger_error() with the E_USER_ERROR severity have the same effect without the downsides.

[6] mysqli_connect(): http://php.net/function.mysqli-connect

## 12. INSERTING DATA INTO A MYSQL DATABASE

### Inserting the Full Name Into the Database

Next we want to build a SQL SELECT query and send it to our database using the mysqli_query() function[7]. This function takes two parameters: a database connection resource, and a query string. Our query string and mysqli_query() statement should look like this:

```
$query = "INSERT INTO fullName (first_name, last_name)"
  . " VALUES ('$first_name', '$last_name')";

$result = mysqli_query($dbc, $query);
```

If the call to mysqli_query() is successful, $result contains TRUE. Otherwise, if the query fails, FALSE is returned. You can also use an or trigger_error() statement as well.

### Closing the Database Connection

Finally, close the database connection using the function mysqli_close(). This function takes one parameter: the database connection. Our mysqli_close() statement should look like this:

```
mysqli_close($dbc);
```

> Whenever we want to query a database, one approach is to connect to the database, perform the query, and close the database connection. It is not a good idea to leave a database connection open. It takes up thread resources and can be a potential problem if you have a large-scale application where multiple connections can be open simultaneously. Suppose you're writing a large-scale application that may have many open connections to the database at one time. In that case, you should consider closing connections when you finish interacting with the database rather than waiting for the script to finish.

> On the other hand, PHP will automatically close any open database connections when your script terminates. For small to medium-size applications, or if your queries are spread out across many functions, you can skip calling mysqli_close() explicitly.

Putting it all together, our script now looks like Listing 12.2.

[7] mysqli_query() function: http://php.net/mysqli_query

### Listing 12.2.

```
```php
<html>
<head>
<title>Form for Entering Full Name</title>
</head>
<body>
<?php if (!isset($_POST['submit'])) { ?>
<h2>Enter Full Name</h2>
<form action="<?=$_SERVER['PHP_SELF']?>" method="POST">
First name:<br/>
<input type="text" name="first_name"/><br/>
Last name:<br/>
<input type="text" name="last_name"/><br/>
<p>
<input type="submit" name="submit" value="Submit Name" />
</form>
<?php } else { ?>
<h2>Greetings!</h2>
<?php
// Grab full name from form
$first_name = $_POST['first_name'];
$last_name = $_POST['last_name'];

// Insert full name into database
$dbc = mysqli_connect('localhost', 'testuser', 'testuser', 'FullName')
or trigger_error('Error connecting to MySQL server.', E_USER_ERROR);

$query = "INSERT INTO fullName (first_name, last_name)"
. " VALUES ('$first_name', '$last_name')";

$result = mysqli_query($dbc, $query);
or trigger_error('Error querying database.', E_USER_WARNING);

if (!$result)
{
trigger_error("Query Error description: "
. mysqli_error($dbc), E_USER_WARNING);
}

mysqli_close($dbc);
?>
<br/><br/>Hello <?= $first_name . " " . $last_name; ?>
Thanks for submitting the form!
<?php } ?>
</body>
</html>
```
```

## 12. INSERTING DATA INTO A MYSQL DATABASE

### Test and Verify

### Expected Results

Let's run our application and verify we are inserting items in our database correctly.

If all goes well, we should get the expected output shown in Figure 12.25.

Now let's check to see if our full name actually was inserted into our fullName table. In the MySQL CLI tool, select all fields and rows in the fullName table:

```
SELECT * FROM FullName;
```

Depending on your input, you should see a new row like the one in Figure 12.26.

### SUCCESS!

### Things That Can Go Wrong

A few common bugs may crop up now, and then that will prevent your application from running successfully. The most common tend to be those related to communicating with the database. Bugs due to PHP coding errors can be found with a standard debugger and using tools like Xdebug[8] and PHP Integrated Development Environments (IDE) like JetBrains’ PhpStorm.

Regarding database communication bugs, it is helpful to use a database management tool like Adminer or (for our example) the MySQL CLI tool to verify your connection parameters work. Database communication bugs typically involve a failure to connect to the database or a malformed SQL query. Let's look at both of these.

[8] Xdebug: http://xdebug.org

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_132_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_132_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_132_2.png)

## Create a PHP Application to Insert Data

### Failed Database Connection

Failing to connect to the database usually involves one or more incorrect parameters to the mysqli_connect() function, which could be incorrect credentials or a non-existent database name.

For example, you might see output like Figure 12.27.

Error output can be pretty tricky to decipher. However, we do know that our mysqli_connect() call failed. We can also see the reason given is:

```
php_network_getaddresses: getaddrinfo failed: Name or service not known in
```

The fact that we see a problem with the network address is a clue as to what's wrong. Looking up the mysqli_connect()[9] function definition in the PHP manual, we see that the first parameter expected is the hostname or IP address of the SQL server we are trying to connect to. Looking at line 24 of our code, we see Figure 12.28.

We quickly identify that we typed localhosed instead of localhost, which we can quickly fix.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_133_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_133_1.png)

Let's say we see the output in Figure 12.29 instead.

The reason given is:

```
Access denied for user 'testusers'@'localhost'...
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_133_2.png)

Because we see that access was denied, it tells us that either the username or password parameter to mysqli_connect() is incorrect. Looking at line 24 of our code, we see Figure 12.30.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_133_3.png)

Looking at the user name parameter, we can see it is misspelled and has an extra s on the end.

[9] mysqli_connect(): https://php.net/mysqli_connect
