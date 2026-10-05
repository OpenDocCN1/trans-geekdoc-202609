
```php
$result = $request->execute();

Trap for errors. In this case, we want to return all the records so the rest of the login page doesn't have problems.
if ($FileMaker::isError($result)) {
  $request = $fm->newFindAllCommand('Demo php');
  $result = $request->execute();
}
```

Next, we can get the count from the search request using the getFoundSetMethod. If there is only 1 record in the count found we can change the login $_SESSION superglobal for login to "1" and redirect the user to the protected success page using the php header method. Note that we are assuming the user only has a unique record based on their email address and password. That means when the user signs up for your site we will have to check the database for existing records to prevent them from creating more than one record.

```php
$found = $result->getFoundSetCount();
if($found == 1) {
  $_SESSION['login']=1;
  header("location:TimeoutSuccess.php");
  exit;
} else
```

```php
header: Redirect to another page by location.
// php
http://us3.php.net/manual/en/function.header.php
```

If there are no more or than one record in the database you should immediately log out the user by changing the $_SESSION superglobal for login to "0" and provide the user with a message. I recommend that the message be very generic so they can't try to figure out if they have the email address or password correct. This will limit the effort of people trying to break into your system.

```php
{
$_SESSION['login']=0;
$message = 'Incorrect user name or password.';
}
else
```

The last part of the PHP code is the default message if the user didn't enter either an email address or a password.

```php
{
$message = 'Please enter a user name and password.';
?>
```

The form is simple. It points back to the same page as the PHP code will run and uses the Post method. It is like to place the $message variable at the top of the form. It only passes the username (i.e. email address field in the database) and the password.

```html
<form action="Timeout.php" method="post">
<table border="0" cellspacing="3" cellpadding="3">
<tr>
<td>&nbsp;</td>
<td><?php echo $message; ?></td>
</tr>
<tr>
<td>User Name</td>
<td><input name="username" type="text" />
</tr>
<tr>
<td>Password</td>
<td><input name="password" type="password" />
</tr>
<tr>
<td>&nbsp;</td>
<td><input name="Login" type="submit" value="login" />
</tr>
</table>
</form>
<body>
<html>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_176_0.png)

Figure 40: LoginTimeout.php page.

### LoginSuccess.php

The login page does the majority of the hard work. The rest of your protected pages only need a few lines of code at the very beginning to maintain the login security. Again, the session_start() method is required to be placed BEFORE the HTML tag. This carries the existing session information forward to this page. Since the LoginTimeoutSuccess page is the entry point into your protected pages you should check to see if $_SESSION superglobal is set and the login value is 1. If the user has not logged in properly they will be redirected to the login page.

```php
<?php
session_start();
if(!isset($_SESSION['login']) || $_SESSION['login']!=1) {
  header("location:LoginTimeout.php");
  exit;
}
```

The next part is used to automatically log the user out after a predefined period of inactivity. Time is measured in seconds. Therefore, we will start by defining the $inactive variable for 10 minutes to 10 x 60 seconds.

```php
$inactive = 10*60;
```

Next, every time the user accesses the page or refreshes the content we will check to see if $_SESSION['timeout'] superglobal has been set. The timeout value is actually set at the end of this code. If the timeout is set, calculate the amount of time the user has inactive and store it as the $session_life variable.

This is achieved by taking the current time() value and subtracting the $_SESSION['timeout'] value. This will return the number of minutes the user has been inactive. If the user has been inactive longer than the inactive limit we will destroy all the session information and redirect the user to the login page.

```php
if(isset($_SESSION['timeout']))
{
  $session_life = time() - $_SESSION['timeout'];
  if($session_life > $inactive) {
    session_destroy();
    header("Location:login.php");
  }
}
```

# time(0): Returns the current time in seconds from Jan 1. 1970.

```php
http://www3.php.net/manual/en/function.php
```

The last line of code is set to use the $_SESSION['timeout'] value with the current time. Why does it come last? Because every time the user accesses or refreshes the page within the time limit you want to reset the timeout so they will have 10 minutes on their clock. If you are really picky you want to boot entirely from the page you are on. Just within their time limit. Also include meta refresh code to force the page at a certain interval and redirect the user to the login page. Just make sure that the refresh is set to run longer than the inactive time. Otherwise, they will never get out for inactivity because the time will be constantly reset before the 10-minute limit. Lastly, if you want to use the same inactive value for the refresh you will have to uncomment the code in the sample file.

```php
$_SESSION['timeout'] = time();
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_177_0.png)

This page works with LoginSuccess.php to log out after a predefined period of inactivity.
Login at: 08/03/2012 10:55:53
Your session will end at: 08/03/2012 11:05:53

Figure 41: LoginTimeout.php

# Lesson 16: Alternate Background

**Objective:** In this lesson you will learn how to display a list of records with an alternating background. FileMaker has built-in alternating row color for portals for a long time. Records in list view are a different story. There has been many workarounds for a long time. Frankly, web browser doesn't tax the database to alternate the row tag.

**Difficulty:** Easy

**Sample Files:** AlternateBackground.php

**Page Navigation:** ![](img/5a2c5fda68d42e5d65f51850276e49ec_178_0.png)

findAllCommand(), execute(), getRecords(), getField()

**Code:** Alternating the background color is best achieved if use CSS. Normally you would include a separate CSS file. However, to make the demo easier we embedded the CSS for alt_row_color in the page. You can embed the CSS style in the head tag.

```html
<html>
<head>
<title>Alternate Background</title>
<style type="text/css">
alt_row_color {background-color: #CCCCCC}
</style>
</head>
<body>
```

Always start by including the connection to the database.

```php
<?php
include("../Conn/dbaccess.php");
```

Find all the records. Then execute the request.

```php
$request = $fm->newFindAllCommand('Demo php');
$result = $request->execute();
```

Trap for errors.

```php
if (FileMaker::isError($result)) {
  echo "<p>Error: " . $result->getMessage() . "</p>";
  exit;
}
```

Store the records in the $records variable.

```php
$records = $result->getRecords();
```

Create the header for the table.

```php
echo '<table border="1">
<tr>
<th>First Name</th>
<th>Last Name</th>
<th>Number</th>
<th>Date</th>
<th>Time Stamp</th>
<th>Calculation</th>
<th>Record ID</th>
</tr>';
```

Now for the example of the fields. This is very similar to some of the FileMaker tricks to activate the background color for a list of records. The difference is that it doesn't take any special fields and doesn't tax the database. We are going to use the CSS style alt_row_color and the clever modulo function with a row variable to figure out if the row is odd or even number. Start by setting the $row variable to zero. Then start the foreach looping to display the results.

```php
$row = 0;
foreach ($records as $record)
```

The very first row tag is where you apply the CSS style. Using the modulo function we define the row by 2. If there is a remainder we know its an odd row. If there is no remainder the row is even. Odd rows will use the CSS style. Even rows will only use the row tag.

```php
if($row % 2 == 0) {
  echo '<tr class="alt_row_color">';
} else {
  echo '<tr>';
}
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_179_0.png)

Modulo function: Returns the remainder of a value divided by b (a/b)
http://www.php.net/manual/en/language.operators.arithmetic.php

Next, the contents of the fields. Then increment the $row +1 for the next loop using $row++.

```php
echo '<td>' . $record->getField('FirstName') . '</td>';
echo '<td>' . $record->getField('LastName') . '</td>';
echo '<td>' . $record->getField('Number') . '</td>';
echo '<td>' . $record->getField('Date') . '</td>';
echo '<td>' . $record->getField('Timestamp') . '</td>';
echo '<td>' . $record->getField('Calculation') . '</td>';
echo '<td>' . $record->getField('RecordID') . '</td>';
echo '</tr>';
$row++;
```
