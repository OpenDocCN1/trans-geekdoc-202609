After obtaining the user's e-mail address, the ad system is ready for the user to enter an ad. The createAd2.php file in Listing 5-5 enables you to do this. The first thing that this PHP program does is make sure that the e-mail address is for a legitimate user of the system. If not, the code prints out the message Sorry, you are not a known user.

To demonstrate the techniques of entering data into a MySQL server via the Web, I purposely left out a part that would probably be important to any online classified ad system: a password system. As it is, anybody can access this system and place ads for anybody else. The point here, however, is to show you how to enter data through HTML forms. In Book VI, Chapter 7, I take you through the creation of an example Web site that allows users to register with the site and log in. To make a successful classified ad system, combine the information in that chapter with the information in the present chapter.

# Listing 5-5: The Form That Allows the User to Enter an Ad

```
<html><head><title>Create New Ad</title></head>
<body bgcolor="#FFFFFF" text="#000000">
<?php
$CustomerOkay = false;
mysql_connect("localhost", "phpuser", "phppass");
$email = $_GET['email'];
$result = mysql_query(
 "select ID, name from phpbase.customer ". // space!
 "where email = '$email'");
if ($result) {
 if (mysql_num_rows($result) > 0) {
 $row = mysql_fetch_assoc($result);
 $CustomerOkay = true;
 $CustName = $row['name'];
 $CustID = $row['ID'];
 }
}
if ($CustomerOkay == false) {
 print "<h1>Sorry, you are not ".
 "a known customer.</h1>";
}
else {
 print "<h1>Welcome, $CustName!</h2>";
 // Categories
 $result = mysql_query(
 "select * from phpbase.category");
 if ($result) {
 if (mysql_num_rows($result) > 0) {
 while ($row =
 mysql_fetch_assoc($result)){
 $name = $row["category_name"];
 $num = $row["categoryID"];
```