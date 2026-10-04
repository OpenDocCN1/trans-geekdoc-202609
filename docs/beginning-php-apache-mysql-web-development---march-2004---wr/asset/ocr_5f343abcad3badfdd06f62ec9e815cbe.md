# Chapter 13

or die('Could not connect to MySQL database.' . mysql_error());

mql_select_db($SQL_DB, $conn);

?
<select>

This is the link to the admin portion of the functions, which is pretty self-explanatory:

<a href="quickmsg.php">Send a message to users</a>

You should be able to figure out quickmsg.php fairly easily. Most of it is HTML, and the PHP code is practically identical to the code used to build the list in admin.php. Feel free to canonicalize your own code as you need to.

Finally, we come to the real workhorse of the Mailing List Administrator application, admin_transact.php is the page to which you post your forms, and it will process that information, update the database tables, and send out e-mails as requested. Let's take a look under the hood:

```
require('config.php');
```

Remember seeing the precedeing line in admin.php? Having the connection data in one file and including in each page makes your code more efficient. Of course, you already know that. Let's move to create the connection to the database, and select it that you can work with:

```
$conn = mysql_connect(SQL_HOST, SQL_USER, SQL_PASS)
or die('Could not connect to MySQL database.' . mysql_error());

mql_select_db($SQL_DB, $conn);
```

Did the user click an "action" button?

```
if (isset($_POST['action']))
```

Depending on which button was clicked, you're going to perform one of three actions: create a new mailing list, delete an old mailing list, or send a message to the users subscribing to a mailing list:

```
switch ($_POST['action'])
(
```

Not only must you delete the mailing list, like this: