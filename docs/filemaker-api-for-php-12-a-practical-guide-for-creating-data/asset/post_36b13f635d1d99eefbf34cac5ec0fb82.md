
Turn Allow User Abort and Set Error Capture so you don't have any problems with the script.

Allow User Abort [ On ]
Set Error Capture [ On ]

Enter find and find the record on the email address parameter by the web page. To get the parameter you can use Get(ScriptParameter) just as you would with a button on FileMaker Pro. Don't forget that you have to search for addresses using the match field (also known as exact match) "=" operator because of the "@" wildcard in the email address.

Enter Find Mode [ ] Set field [ php_demo::Email; "=" & Get(ScriptParameter) ]
Perform Find [ ]

Trap for errors. If there are no errors finding the record you can send the password using the built-in Send Mail function.

> You need to enable the SMTP settings for it to work on your network.

If [ Get(LastError) = 0 ]
Send Mail [ via SMTP Server; To: Get(ScriptParameter); Subject: "Lost Password";
Message: "Your password is: " & php_demo::Password;"
Authentication Type: None ] [ No dialog. ]

If there are no records found exit the script and FileMaker Server returns an error. That will allow you to trap the error in your PHP code so you can alert the user that their email address does not exist.

Else
Exit Script [
End If

| View: all by category |
| --- |
| Control | |
| Perform Scripts | |
| Perform Script | |
| Exit Script | |
| Halt Script | |
| If | |
| Else | |
| End If | |
| Loop | |
| Exit Loop | |
| Allow User Abort | |
| Set Error Capture | |
| Set Window | |
| Navigation | |
| Go to Record/Request | |
| Go to Recorded Page | |
| Go to Portal Row | |
| Go to Objects | |
| Go to New Field | |
| Go to Previous Field | |
| Enter Browser Mode | |
| Enter Find Mode | |

- Send an email to the user if they lost their password. Start by finding their record.
- If we set your system up to store passwords as an md5 hash you'll need to
- Set Error Capture - If FileMaker returns an error make sure the dialog box is not
- Set Error Capture
- Get Record with the parameter passed by the newPerformScriptCommand(0).
- Find Mode []
- Set Field Email="=" & Get(ScriptParameter)
- Perform Find []
- If record is found, call the user their password. If they have to
- IMPORTANT: You must modify the SMTP server settings to send the email
- Else
- SMTP Server returns no dialog. To: Get(ScriptParameter); Subject "Lost Password"
- Otherwise else FileMaker throws an error if there are no records found PHP can send
- Exit Script [] Run script with full access privileges

Figure 7-49: Lost Password script.

# Lesson 18: Display Pagination

**Objective:** In this lesson you will learn how to enable the user to specify how many records to display per page and how to create pagination links. It's one thing to display a short list of sample records. It's another thing to display thousands of records on a production server for concurrent users. The more records you display the more the database and the web server. Therefore you want to limit the number of records that have to be returned from the server to display on each page.

**Difficulty:** Difficult

**Sample Files:** Pagination.php

![](img/5a2c5fda68d4e5d65f1850276e493.png)

**FileMaker API Methods:**
- FindAll()
- addCriterion()
- setRange()
- execute()
- getMessage()
- getRecords()
- getFoundCount()
- getField()

**Code:** This example is to combine several techniques from previous examples. Overall purpose is to provide a functional example. Embed the CSS style in the head tag to alternate the background color.

```html
<head>
<style type="text/css">
.alt_row { background-color: #CCCCCC; }
</style>
<title>Pagination</title>
</head>
<body>
```

Always start by including the connection to the database.

```php
<?php
include("../Conn/dbaccess.php");
?>
```

Create the form. The PHP $_SERVER['SELF'] is a dynamic method that returns the URL for the current file rather than hardcoding it. If you change the name of the page the code would break. Next we're going to include hidden values. The first page is with a value of 1 and skip with a value of 0. The page value is used to display pagination links (1, 2, 3, 4, etc.). After a new search you are always to be on the first page. The skip value tells FileMaker not to skip records to start at the first record in the found set. Again, after a new search you are always to be on the first record. Next you can include the search field for FirstName.

```html
<form action="<?php $_SERVER['SELF']; ?>" method="get" name="search" id="search">
<input name="page" type="hidden" value="1" />
<input name="skip" type="hidden" value="0" />
First Name: <input name="FirstName" type="text">
<p>
```

```php
$_SERVER['SELF'] Returns the full path to the current file.
// manual/reserved_variables.php
```

To make the display of records user friendly we will allow the user to define how many records they want to display for each page. That's as easy as creating a drop-down list. I highly recommend you define how many records you want to be able to display rather than having them in a random number. For this example defining sets of 10, 25, 50 and 100 records and assigning that number to the value 'max'. The max value will be used to tell FileMaker how many records to return to the browser. Finally close out the form with the Submit button.

```html
Records Per Page:
<select name="max">
<option value="10"></option>
<option value="25"></option>
<option value="50"></option>
<option value="100"></option>
</select>
<p>
```

Now we can create the PHP code to find and display the records and the pagination links. Start by defining the skip variable. By default the value is 0 when the user comes to the page so the database starts at the record in the table. Otherwise you can get the skip value from the URL after a search is performed.

```php
if(empty($_GET['skip']))
{
    $skip=0;
} else
{
    $skip=$_GET['skip'];
}
```

Next, define the max variable for the number of records that will be displayed on each page. By default we'll define 10 records per page until the user selects another value from the pop up menu. This will minimize the load on the server. Otherwise you can get the max value from the URL after a search is performed.

```php
if(empty($_GET['max']))
{
    $max=10;
} else
{
    $max=$_GET['max'];
}
```

Now we can search the records. If nothing is entered into the text field then we will show all the records. Otherwise we search the FirstName field.

```php
if(empty($_GET['FirstName']))
{
    $FirstName = "";
    $request = $fm->newFindCommand('Demo php');
} else
{
    $FirstName = $_GET['FirstName'];
    $request = $fm->newFindCommand('Demo php');
    $request->addCriterion('FirstName', $FirstName);
}
```

Before you execute the search we'll tell FileMaker how many records to skip and how many to return (max). Then we can execute the search.

```php
$request->setRange($skip, $max);
$result = $request->execute();
```

![](img/5a2c5fda68d4e5d65f1850276e493.png)

FileMaker Syntax: setRange('Skip', 'Max')

```php
$request->setRange($skip, $max);
```

Trap for errors.

```php
if (FileMaker::isError($result))
    echo "<p>" . $result->getMessage() . "</p>";
    exit;
```

Get the records as an array in the $records variable.

```php
$records = $result->getRecords();
```

Display the found count for the user.

```php
$found = $result->getFoundCount();
$total = $result->getTableRecordCount();
echo "<p>" . $found . " of " . $total . " Total Records</p>";
```
