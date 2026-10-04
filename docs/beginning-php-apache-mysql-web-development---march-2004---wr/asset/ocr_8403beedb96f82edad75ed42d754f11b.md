# Chapter 13

Connect to the database:

```
$conn = mysql_connect(SQL_HOST, SQL_USER, SQL_PASS)
or die(`Could not connect to MySQL database. ` . mysql_error());

mysql_select_db(SQL_DB, $conn);
```

Get user info based on the user id. If you find it, display the “Thank You,” followed by the user’s first name. Also grab the user’s email address. You’ll use it.

```
if (isset($_GET['user']))
{
  $uid = $_GET['user'];
  $sql = "SELECT * FROM ml_users WHERE user_id = ' . $uid . '\'";
  $result = mysql_query($sql)
  or die(`Invalid query: ` . mysql_error());
  if (mysql_num_rows($result)) {
    $row = mysql_fetch_array($result);
    $msg = "<h2>Thank You, " . $row['firstname'] . "</h2><br /> </br />";
    $email = $row['email'];
  } else {
    die(`No match for user id: ` . $uid);
  }
}
```

Next, you get the listname, based on the mailing list id. If you find it, you build the message to include “Thanks for subscribing. Once you get this pass, you know the user id and mailing list id.

```
if (isset($_GET['ml']))
{
  $ml_id = $_GET['ml'];
  $sql = "SELECT * FROM ml_lists WHERE ml_id = ' . $ml_id . ''"";
  $result = mysql_query($sql)
  or die(`Invalid query: ` . mysql_error());
  if (mysql_num_rows($result)) {
    $row = mysql_fetch_array($result);
    $msg = "<h2>Thank you for subscribing to the <li>" . $row['listname'] . "</li><br />";
  } else {
    die(`Could not find Mailing List ` . $ml_id);
  }
} else {
  die(`Mailing List is missing.`);
n
```

Now all you have to determine the type of message you’re displaying.

```
if (!isset($_GET['t'])) die(`Missing Type`);
```

It is crucial that the type be set. If not, stop processing this page. You don’t know what to thank the user for.

452