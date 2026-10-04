# Mailing Lists

The ml_subscriptions table where most of the "work" is done when it comes to mailing lists. It contains three columns: ml_id, user_id, and pending. The combination of ml_id and user_id must be unique. (You don't want to have the same user as the same mailing list more than once, right?). The pending column is used to determine whether or not a user has finished or her subscription. We describe the use of the pending column in this chapter.

The following lines simply run the SQL queries to create the tables. As long as all three tables are created (or already exist), you will see "Done" to the screen. Otherwise, you will see an error message.

```
$res = mysql_query($sql1) or die(mysql_error());
$res = mysql_query($sql2) or die(mysql_error());
$res = mysql_query($sql3) or die(mysql_error());
echo "Done.";
```

Next, let's take a look at admin.php:

```
require('config.php');
```

Now you see how we put the connection in a separate file. By doing this, all you need is a single line to include the constants, and you can use them in this page.

Let's pause for a moment and talk about form submit. A common practice is to post a form back to itself, and you certainly could have done that. When your page contains data that needs to be inserted into a database, you need to think twice about a self-posting form. If the user were to refresh or reload the page, all of your database functions would run disastrous. You would end up with duplicate data, or delete records you didn't mean to delete.

Obviously, you don't want that to happen, so in order to minimize the probability, to post a separate form called admin_transact.php. This page handles all of the necessary database transactions, and then redirects back to the page from which you came. If the user reloads the page at that, no harm will come to your database.

```
<form method="post" actions="admin_transact.php">
```

You might notice that all of your buttons have the same name, "action", each with a different value. When posting the form, you are accessing the $_POST['action'] variable to set which button was pressed, and perform the action. This allows you to use one script for multiple transactions, rather than having to create a multiple page with each form, allowing posting to a different transaction page.

```
<input type="submit" name="action" value="Add New Mailing List />
```

Now you get all of the mailing lists available and wrap them in option tags so that they will appear on your page in a drop-down select box.

```
<select name="ml_id">
<?php
$conn = mysql_connect(SQL_HOST, SQL_USER, SQL_PASS))
```

433