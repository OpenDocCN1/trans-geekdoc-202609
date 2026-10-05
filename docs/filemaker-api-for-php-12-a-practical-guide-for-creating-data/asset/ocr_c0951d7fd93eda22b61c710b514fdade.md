```
<form action="<?php \$_SERVER['PHP_SELF']; ?>">
method="get" name="search" id="search">
<input name="page" type="hidden" value="1" />
<input name="skip" type="hidden" value="0" />
First Name: <input name="FirstName" type="text">
<p>
```

```
$_SERVER['PHP_SELF'] Returns the full path to the current file.
http://us2.php.net/manual/en/reserved.variables.server.php
```

To make the display of records user friendly we will allow the user to define how many records they want to display for each page. That's as easy as creating a drop down list. I highly recommend you define how many records you want to be able to display rather than having them in a random number. For this example defining sets of 10, 25, 50, and 100 records and assigning that number to the value 'max'. The max value will be used to tell FileMaker how many records to return to the browser. Finally, close out the form with the Submit button.

```
Records Per Page:
<select name="max">
<option>10</option>
<option>25</option>
<option>50</option>
<option>100</option>
</select>
<p>
```

Now we can create the PHP code to find and display the records and the pagination links. Start by defining the skip variable. By default the value is 0 when the user first comes to the page so the database starts at the record in the table. Otherwise you can get the skip value from the URL after a search is performed.

```
if(empty($_GET['skip']))
{
$skip=0;
} else
{
$skip=$_GET['skip'];
}
```

Next, define the max variable for the number of records that will be displayed on each page. By default, we'll define 10 records per page until the user selects another value from the pop up menu. This will minimize the load on the server. Otherwise you can get the max value from the URL after a search is performed.

```
if(empty($_GET['max']))
{
$max=10;
} else
{
$max=$_GET['max'];
}
```

Now we can search the records. If nothing is entered into the text field then we will show all the records. Otherwise we search the FirstName field.

```
if(empty($_GET['FirstName']))
```