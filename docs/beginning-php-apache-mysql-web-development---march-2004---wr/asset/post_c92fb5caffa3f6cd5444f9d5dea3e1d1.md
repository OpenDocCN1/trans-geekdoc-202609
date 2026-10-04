
# Chapter 13

```php
$row = mysql_fetch_array($result);
$user_id = $row['user_id'];
$url = "http://" . $_SERVER['HTTP_HOST'] . 
dirname($_SERVER['PHP_SELF']) . 
"/remove.php?u=" . $user_id;
$ml_id = $_POST['ml_id'];
header("Location: $url");
exit();
```

Note the exit() function intently immediately following header(). This is important, so the rest of the page is not loaded. Each of our case statement creates a break so that the rest of the statements are not executed.

If the user clicks the Subscribe button, many things have to happen. First, you must look up the e-mail address to see if the user already exists:

```php
case 'Subscribe':
$sql = "SELECT user_id FROM ml_users " 
"WHERE e-mail="" . $_POST['e-mail'] . ";";
$result = mysql_query($sql, $conn);
```

If the user does not exist (no rows were returned from your query), you will insert a new record in the ml_users table. MySQL automatically assigns a user id.

To retrieve the user id, use the PHP function mysql_insert_id. The variable $conn is optional, but its a good idea to include. If you omit it, it will automatically use the last open connection. mysql_insert_id will return a valid value only if the SQL statement resulted in a column being automatically incremented. In this case that happen--the column is the user_id, which is the value you need for the next part of your code.

```php
$user_id = mysql_insert_id($conn);
}
```

If the e-mail address was found in the database, simply grab the user id from the record that was returned. Either way, you now have a $user_id. You also have a mailing list id, retrieved from $_POST['ml_id']. That's all you need to create a subscription request.

# Mailing Lists

```php
else
{
  $row = mysql_fetch_array($result);
  $user_id = $row['user_id'];
}
```

You may recall that the ml_subscriptions table contains three columns: user_id, ml_id, and pending. The first two values you have are. The last one, pending, should be set to 1 until the user confirms the subscription. You have initially set up the table setting to 1 as a default, so that the column is automatically taken care of. Now you have all the data you need to create a subscription, and like that, you insert the appropriate data into the subscriptions table.

```php
$sql = "INSERT INTO ml_subscriptions (user_id, ml_id) 
VALUES ('" . $_POST['user_id'] . "','" . $_POST['ml_id'] . "');
mysql_query($sql, $conn);
```

Now all that is left is to notify the user. You do this in two ways: with a Thank You Web page that confirms the subscription was processed, and with an e-mail to request confirmation you don't want people to sign up other people for mail. It's not a foolproof security measure, but it will stop most abuse.

You'll send an email, and then redirect the user to the Thank You page. The first thing you do is to get the name of the mailing list, using the list id. That's how you tell the user in the e-mail which list he or she subscribed to, and with it wouldn't be helpful to show you mailing list #42!

Next, you build up a URL that will be at the bottom of the e-mail message. This directs the user back to this same page, with an 'action=confirm' (the third 'action' which we'll look at).

```php
$url = "http://" . $_SERVER['HTTP_HOST'] .
dirname($_SERVER['PHP_SELF']) .
"/user_trans.php?user=" . $user_id . ".&ml=" . $_POST['ml_id'] . ".&action=confirm";
```

Then you build the subject and body of the message, concatenating the URL to the bottom and send it off with the mail():

```php
$subject = "Mailing list confirmation";
$body = "Hello " . $_POST['firstname'] . " \n\nOur records indicate that you have subscribed to the \n" . $listname . " mailing list. \n\n\nIf you did not subscribe, \n \nplease accept our apologies. \n\nYou will not be subscribed if you do not visit the \nconfirmation URL. \n\n\n";
```

# Chapter 13

"If you subscribed, please confirm this by visiting the " 
"following URL:\n" . $url;

```php
mail($_POST['e-mail'], $subject, $body, $headers);
```

Once the mail has been sent, all that is left to do is to send the user to the Thank You page. We will look at the Thank You page shortly.

```php
$redirect = "thanks.php?u=" . $user_id . "&ml=" . $_POST['ml_id'] . "&s=";
break;
```

When the user receives the confirmation email, he or she clicks the link at the bottom, which loads user_transact.php again, with action=confirm. When confirming, you simply need to do one thing—change the flag for the subscription to 0. Once that is done, redirect the user to the Thank You page for confirmation, and send another e-mail informing the user of his her new subscription. You will also provide an easy means of removal.

The first thing to do is make sure the user_id and mailing list id were passed to the function. If not, simply redirect the user to user.php.

```php
case 'confirm':
if (isset($_GET['u']) && isset($_GET['ml'])) {
  ...
} else {
  $redirect = 'user.php';
}
```

Next, find the subscription that matches the user id and mailing list id and updating the pending column to 0. Remember that user_id and ml_id columns make a primary key, so there can be one record for each possible values.

```php
$sql = "UPDATE ml_subscriptions SET pending=0 
WHERE user_id=" . $_GET['u'] . " AND ml_id=" . $_GET['ml'];
mysql_query($sql, $conn);
```

Look familiar? We are grabbing the mailing list name from the mailing list id, just as we did for Subscribe case. This looks like a prime candidate for function:

```php
$sql = "SELECT lastname FROM ml_lists "
"WHERE ml_id=" . $_GET['ml'];
$result = mysql_query($sql, $conn);
$row = mysql_fetch_array($result);
$lastname = $row['lastname'];
```

# Mailing Lists

Now you need to retrieve the user's e-mail address based on his her user id, you can send him or her e-mail. This should also look familiar:

```php
$sql = "SELECT * FROM ml_users 
"WHERE user_id='" . $_GET['u'] . "";
$result = mysql_query($sql, $conn);
$row = mysql_fetch_array($result);
$firstname = $row['firstname'];
$e_mail = $row['e-mail'];
```

The body of this message is a little different. You are building the subject and body parameters for the mail() function and sending it to the user. You just need to send it on its way.

```php
$url = "http://" . $_SERVER['HTTP_HOST'] .
dirname($_SERVER['PHP_SELF']) .
"/remove.php?u=" . $_GET['u'] . "&ml=" . $_GET['ml'];
```

```php
$subject = "Mailing List Subscription Confirmed";
$body = "Hello " . $firstname . "\n"
"Thank you for subscribing to the "
"mailing list. Welcome!\n\n"
"If you did not subscribe, please accept our apologies.\n"
"You can remove this subscription immediately by "
"visiting the following URL:\n" . $url;
```

```php
mail($e_mail, $subject, $body, $headers);
```

Off your user goes, to the Thank You page:

```php
$redirect = "thanks.php?u=" . $_GET['u'] . "&ml=" . $_GET['ml'] . "&ts=" . time();
```

Finally, if 'action' is something other than Remove, Subscribe, or confirm, you will need to redirect the user somewhere else, in this case, user.php. The final lines handle the redirection:

```php
default:
  $redirect = 'user.php';
}
```

```php
header('Location: ' . $redirect);
```

The user_transact.php page is not terribly complicated. However, when you have a single page performing multiple tasks, you need to be careful that all situations are handled correctly.

# thanks.php

Next let's look at the code in thanks.php. Most of it is familiar code that you have used elsewhere. You should have no problem breathing through one:

# Chapter 13

Connect to the database:

```php
$conn = mysql_connect(SQL_HOST, SQL_USER, SQL_PASS)
or die(`Could not connect to MySQL database. ` . mysql_error());

mysql_select_db(SQL_DB, $conn);
```

Get user info based on the user id. If you find it, display the “Thank You,” followed by the user’s first name. Also grab the user’s email address. You’ll use it.

```php
if (isset($_GET['user']))
{
  $uid = $_GET['user'];
  $sql = "SELECT * FROM ml_users WHERE user_id = '" . $uid . "'";
  $result = mysql_query($sql)
  or die(`Invalid query: ` . mysql_error());
  if (mysql_num_rows($result)) {
    $row = mysql_fetch_array($result);
    $msg = "<h2>Thank You, " . $row['firstname'] . "</h2><br /> <br />";
    $email = $row['email'];
  } else {
    die(`No match for user id: ` . $uid);
  }
}
```

Next, you get the listname based on the mailing list id. If you find it, you build the message to include “Thanks for subscribing. Once you get this pass, you know the user id and mailing list id.

```php
if (isset($_GET['ml']))
{
  $ml_id = $_GET['ml'];
  $sql = "SELECT * FROM ml_lists WHERE ml_id = '" . $ml_id . "'";
  $result = mysql_query($sql)
  or die(`Invalid query: ` . mysql_error());
  if (mysql_num_rows($result)) {
    $row = mysql_fetch_array($result);
    $msg = "<h2>Thank you for subscribing to the <li>" . $row['listname'] . "</li><br /> <br />";
  } else {
    die(`Could not find Mailing List ` . $ml_id);
  }
} else {
  die(`Mailing List is missing.`);
}
```

Now all you have to determine the type of message you’re displaying.

```php
if (!isset($_GET['t'])) die(`Missing Type`);
```

It is crucial that the type be set. If not, stop processing this page. You don’t know what to thank the user for.
