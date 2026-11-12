
```
Category Number:
<select name="categorynum">
<?php
foreach ($catByNum as $num=>$name) {
print "<option value=\"$num\">$name</option>\n";
}
?>
</select>
<br>
<input type="submit" name="Submit"
value="Show All">
</form>
</body></html>
```

If you open Listing 5-3, categoryname.php, in a browser on a client computer, you see something like Figure 5-1.

![](img/3f967ab8a8fddc723173059f56621648_585_0.png)

Figure 5-1: The client browser shows a list of categories.

In Listing 5-3, the PHP code simply does a query on the entire category table. Here’s the select statement:

```
select * from phpbase.category
```

The PHP code then loops through every row, saving the category names in an associative array keyed by categoryID, which is a number. By the time the code reaches the mysql_close function, the catByNum array contains all the categories as values, with the category numbers as keys.

Later, inside the HTML form, the PHP processor kicks back in for a second round of PHP fun. This time, the PHP code constructs a set of HTML option value statements for the combo box control (which is called a “select” object in the HTML world). The cool thing about the option value statements is that you can set up a list of words to display in the combo box and, for each word, provide a value that gets sent out in the URL to the server. Bingo! That's where you can put the category numbers. Thus, one option value that results from this code is as follows:

```
<option value="1">appliances</option>
```

This means that the combo box will show the word appliances, but if I choose appliances, the browser will send the value 1, not the word appliances. The value 1, in turn, is the categoryID associated with appliances. It works!

At this point, you may realize that you could just as easily hardcode the category values in your HTML file rather than look them up in the table. However, the idea is that if you modify your table by changing the category names, removing categories, or adding new categories, using the option value method means you don’t have to change the categoryname.php file. If you hardcode the values, after changing the table in the database you would also have to change the HTML, which is extra work.

Having said that, I can think of at least two instances when you may want to skip the PHP and hardcode the categories in the HTML. First, if you don’t expect to change the categories very often; and second, if you’re running a very large server and need to keep your database lookups to a minimum. Both cases would justify hardcoding the categories in the HTML.

## Modifying Data with a Web Page

Although allowing users to look up data is great, letting them change the data (in certain situations) is even better. For example, you may want to give users the ability to modify an ad by fixing spelling errors or changing the ad’s status, for example.

Typically, you allow users to modify a row in a table by first looking up the row and determining all the information about the row. Then you display the row in an HTML form, allowing the user to change the data. The HTML form sends the data back to the server, where a .php file updates the row with any new values. That doesn’t sound too hard — and it’s not.

In this section, I show you how to allow users to modify an ad. The catch is that anybody can modify any ad. If this were a real classified ad system, you would want to add some security measures, such as a login section. By using the techniques I show you in Book VI, Chapter 7, you can add a login section. To make this work, you must modify the customer table to include an encrypted password. When the user logs in, you encrypt the user’s password and compare it to the one in the customer table. Then that customer can modify only the ads “owned” by that customer, which means the ads containing a customerID value matching the customerID for the logged in customer.

## Contending with add, search, and update

The designers of online database systems tend to want to use the same form for the add, search, and update interfaces. This is a bad idea because it can confuse people. For example, I once helped work on a database system for an oil change center back in the mid-1980s. The single form contained all the fields, you could type in any field, and you could use this form to add, search, and update. After typing the data, you could click a search button to get the rest of the columns for the row, and from there, you could change them and make a really big mess. Confusing? Absolutely! Instead, have one form for adding new data. Then have another form for searching for data. Finally, if the user searches for data and obtains a row, you may want to include a link on the page that lets the user go to a different page to modify the data. Use different forms, and life will be much easier for all involved. Users will thank you in the end.

In the spirit of the “Contending with add, search, and update” sidebar, I use three forms for this example. This example includes a form for adding an ad, a form for looking up an ad (based on the examples earlier in this chapter), and a form for updating the data.

### Creating a new ad

The techniques I show you here are not new. Everything I show you here I describe in Book VI, Chapter 4. Further, this form includes a category search using the techniques I explained in the earlier section, “Looking up by category name.” The createAd1.html file in Listing 5-4 is the form that serves as the starting point for creating an ad. This is an .html file with no PHP code in it, and it simply contains a form asking for the user’s e-mail address. When the user clicks Submit, the Web server moves on to the file createAd2.php in Listing 5-5.

### Listing 5-4: The Form That Asks for the User's E-mail Address

```
<html><head><title>Locate Customer</title></head>
<body bgcolor="#FFFFFF" text="#000000">
<h2>Please enter your email address
so I can find you in the system.</h2>
<form name="form1" method="get"
action="createAd2.php">
<input type="text" name="email">
<input type="submit" value="Submit">
</form></body></html>
```

After obtaining the user's e-mail address, the ad system is ready for the user to enter an ad. The createAd2.php file in Listing 5-5 enables you to do this. The first thing that this PHP program does is make sure that the e-mail address is for a legitimate user of the system. If not, the code prints out the message Sorry, you are not a known user.

To demonstrate the techniques of entering data into a MySQL server via the Web, I purposely left out a part that would probably be important to any online classified ad system: a password system. As it is, anybody can access this system and place ads for anybody else. The point here, however, is to show you how to enter data through HTML forms. In Book VI, Chapter 7, I take you through the creation of an example Web site that allows users to register with the site and log in. To make a successful classified ad system, combine the information in that chapter with the information in the present chapter.

### Listing 5-5: The Form That Allows the User to Enter an Ad

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
