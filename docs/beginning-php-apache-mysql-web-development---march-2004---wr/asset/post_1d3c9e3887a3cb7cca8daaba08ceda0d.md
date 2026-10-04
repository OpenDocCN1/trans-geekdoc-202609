
## E-mailing with PHP

Now you've created the database, select that database.

```php
mysql_select_db("postcard", $conn);
```

Create the images table in the database, containing three columns. If it is successful, print "images table created" to the screen and on.

```php
$sql = 'CREATE TABLE images (id int NOT NULL primary key
auto_increment, img_url VARCHAR (255) NOT NULL,
img_desc text);
$success = mysql_query($sql, $conn) or die (mysql_error());
echo "images table created.';
```

Now create two arrays of values to place in the images table. We need to know the location of the postcards entered previously in Step 1, and their descriptions. Each URL corresponds to a description in the other array.

Loop through the arrays, pulling the location and description text and inserting them into the images table. If there are no errors, print "Data created" to the screen and you're done.

```php
Echo "Data created.";
```

When running this PHP script, if anything goes wrong, make sure you delete the postcard database before running again. Otherwise, you will get an error (database exists) and it will stop executing.

If you need further information on MySQL commands, check out Appendix F, or visit www.mysql.com/documentation/index.html.

We include the code to use the images in the next section, "Getting Confirmation."

## Getting Confirmation

So far, you have a pretty cool postcard application. Any user can send a postcard to whoever he or she wants, and PHP takes care of mailing it. Unfortunately, there is a small problem with the application.

As the application stands right now, it is easy for the user to use any e-mail address in the "From" field. This is a bad thing because nasty e-mails can be sent on someone else's behalf, and you don't want to do that. In order to prevent such maliciousness, you must first send a confirmation e-mail to the "From" Once you get the confirmation, you know the user entered a good e-mail address, and you can go ahead and send the e-mail.

This act of achieving confirmation is the first step toward creating a workflow application. We look at workflow applications in more detail in Chapter 12, but for now understand that a workflow application is one that requires input from various parts before it reaches its destination.

## Try It Out

## Getting Confirmation

In order to accommodate this workflow, much of the code we have used so far in pc_sendmail.php will be recycled. If you are an experienced developer, we are sure you know well how to cannibalize your old code! If you are not familiar with cannibalization, now is the time to write a function that you have written before another application. With a couple of modifications, it will work in your app. So, copy and paste it into your application and make the necessary changes. Voila, for your first cannibalization!

In order to confirm an e-mail address, the postcard information needs to be stored in a table, to be retrieved later on, confirmation has been established:

- 1. Open your PHP editor and create a new PHP file db_makeconfirm.php: Make sure use the correct server, username, and password.

```php
<?php
$conn = mysql_connect("server", "joeuser", "yourpass");
mysql_select_db("postcard", $conn);
$sql = <<EOD
CREATE TABLE confirm (
id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
validator VARCHAR (52) NOT NULL,
to_email VARCHAR (100) NOT NULL,
tname VARCHAR (50) NOT NULL,
from_email VARCHAR (100) NOT NULL,
fromname VARCHAR (50) NOT NULL,
bcc_e_mail VARCHAR (100),
cc_e_mail VARCHAR (100),
subject VARCHAR (255),
postcard VARCHAR (255) NOT NULL,
message text
);
EOD;
$query = mysql_query($sql, $conn) or die(mysql_error());
echo "<table>$confirm</table> created.";
?>
```

- 2. Run db_makeconfirm.php, and then check your MySQL server to make sure the confirm table was indeed created in the database.

- 3. Enter the new and improved postcard.php in your favorite PHP editor and save it:

```html
<html>
<head>
<title>Enter E-mail Data</title>
</head>
<body>
<form name="theform" method="post" action="sendconf.php">
<center>
<table width="640" padding="0" cellpadding="4" cellspacing="0">
<tr>
<td colspan="2"><h2>Postcard Sender/</h2></td>
</tr>
<tr bgcolor="#CCCCCC">
<td>To:</td>
<td><input type="text" name="toname" size="30"></td>
</tr>
<tr>
<td>e-mail:</td>
<td><input type="text" name="to" size="40"></td>
</tr>
<tr>
<td>From:</td>
<td><input type="text" name="fromname" size="30"></td>
</tr>
<tr>
<td>e-mail:</td>
<td><input type="text" name="from" size="40"></td>
</tr>
<tr bgcolor="#CCCCCC">
<td>Cc:</td>
<td><input type="text" name="cc" size="40"></td>
</tr>
<tr>
<td>Bcc:</td>
<td><input type="text" name="bcc" size="40"></td>
</tr>
<tr>
<td colspan="2">Choose a Postcard:
<select name="postcard" onchange="changepostcard(this.value)">
<?php
include("includes/conn_mimic.inc");
$sql = "SELECT * FROM images ORDER BY img_desc";
$images = mysqli_query($sql, $conn) or die(mysql_error());
$loop = 0;
while ($imagearray = mysqli_fetch_array($images)) {
//$id = $imagearray['id'];
$url = $imagearray['img_url'];
$desc = $imagearray['img_desc'];
if ($loop == 0) {
echo "<option value='$url'>$desc</option>\n";
$img_url = $imagearray['img_url'];
} else {
echo "<option value='$url'>$desc</option>\n";
}
$loop++;
?>
</select><br>
</body>
</html>
```
