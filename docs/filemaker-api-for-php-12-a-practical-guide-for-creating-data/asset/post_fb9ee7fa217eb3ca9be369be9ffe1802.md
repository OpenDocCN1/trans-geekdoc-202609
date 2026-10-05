
```php
$number=$_POST['Number'];
$int_options = array(
  "options"=>array(
    "min_range"=>0,
    "max_range"=>100
  )
);
```

```php
if(filter_var($number, FILTER_VALIDATE_INT, $int_options))
  die("Number is not between 0-100");
} else
{
  $request->addField('Number', $_POST['Number']);
}
```

Validating dates is a little trickier because you have to make sure the format is correct and the actual date is valid. In the case of FileMaker the format is MM/DD/YYYY. The problem is that users can enter dates as DD/MM/YYYY or even incorrect dates such as 02/31/2010. Therefore, the easiest way to validate the date is to use the PHP explode function to pull the formatting of the entered date. Then reassemble it into the desired format. Start by creating the variable with the contents from the $_POST superglobal.

```php
$Date=$_POST['Date'];
```

Next, use the PHP explode method to separate the three sets of numbers (MM, DD, YYYY ), based on the slash "/" as the separator, into an array where $mm will be assigned to the first array. $dd will be assigned to the second array. $yyyy will be assigned to the third array.

```php
$array=explode("/", $Date);
$mm=$array[0];
$dd=$array[1];
$yyyy=$array[2];
```

Now you can reassemble the date using the PHP checkdate method. If it is not a valid date you can stop the script. If it is a valid date you can insert it into the database. You might be wondering where the validation is for the slashes "/". When we used the explode function we specified the separator as "/". If the user entered 12.12.2010 or 12-12-2010 the explode function would have placed the entire date into the first array because it would not have found the required separator. Therefore, the date format would be reassembled as 12.12.2010??, which is of course invalid.

```php
if(!checkdate($mm, $dd, $yyyy))
{
  die("Invalid date " . $Date);
} else
{
  $request->addField('Date', $_POST['Date']);
}
```

Validating email addresses also represents a significant challenge. Without sophisticated web methods the only thing you can do is verify that the address represents a valid format. A built method in PHP with the FILTER_VALIDATE_EMAIL option lets you just do that. If the email address is valid you can insert the entry. Otherwise you can stop the script and display a message to the user.

```php
if(filter_var($_POST['Email'],FILTER_VALIDATE_EMAIL))
{
  $request->addField('Email', $_POST['Email']);
} else
```

```php
{
  die("Your email address is not valid.");
}
```

Once everything on the form has been validated you can execute the request. Trap for errors. Finally, display the insert form with any appropriate message to let the user know that the record was inserted successfully.

```php
$result=$request->execute();

if (FileMaker::isError($result)) {
  $message = "<p>Error: " . $result->getMessage() . "</p>";
  exit;
} else {
  $message = '<p>Record was created successfully.</p>';
}
?>
<?php
echo $message;InsertValidation; 
?>
<form action="InsertRecordValidation.php" method="post" name="Insert"> 
  <table border="1">
    <tr>
      <td>First Name</td>
      <td><input name="FirstName" type="text" id="FirstName" /></td>
    </tr>
    <tr>
      <td>Last Name</td>
      <td><input name="LastName" type="text" id="LastName" /></td>
    </tr>
    <tr>
      <td>Number</td>
      <td><input name="Number" type="text" id="Number" /></td>
    </tr>
    <tr>
      <td>Date</td>
      <td><input name="Date" type="text" id="Date" /></td>
    </tr>
    <tr>
      <td>Time Stamp</td>
      <td><input name="Timestamp" type="text" id="Timestamp" /></td>
    </tr>
    <tr>
      <td>Email</td>
      <td><input name="Email" type="text" id="Email" /></td>
    </tr>
  </table>
  <p>
    <input name="insert" type="submit" id="save" value="Save" />
    <input name="insert" type="submit" id="cancel" value="Cancel" />
  </p>
</form>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_111_0.png)

Figure 7-12: InsertRecordValidation.php File.

# Lesson 6: Delete->Detail

**Objective:** In this lesson you will learn how to delete records in the database using a form. This is the same as deleting a record in FileMaker Pro. The process to delete a record is to pass the RecordID from the list page to a detail page. That allows you to isolate a single record. When the user is done they can click a link back to the list page where the list of records will be refreshed and the deleted record will be removed.

**Difficulty:** Medium

**Sample Files:**
- PHPFiles/Core/Lesson6/DeleteRecord.php
- PHPFiles/Core/Lesson6/DeleteRecord.php

**Page Navigation:**

![](img/5a2c5fda68d42e5d65f51850276e49ec_112_0.png)

FileMaker API Methods:
- newFindAllCommand()
- newFindCommand()
- findCriterion()
- execute()
- setField()
- getMessage()
- Records()
- getField()
- RecordID()
- getRecordByID()
- delete()

**Code:**

DeleteRecord.php

Always start by including the connection to the database.

Create a form to search the records. In this case the form is pointed back to the same page using the method.

```html
<form action="DeleteRecord.php" method="GET">
  First Name:<input name="FirstName" type="text">
  <br />
  <input name="submit" type="submit" />
</form>
```

Create the PHP code to search the database and display the results. This is the same as the previous examples.

```php
<?php
if(empty('FirstName'))
{
  $FirstName = "";
  $request = $fm->newFindAllCommand('Demo php');
}
else
{
  $FirstName = $_GET['FirstName'];
  $request = $fm->newFindCommand('Demo php');
  $request->findCriterion('FirstName', $FirstName);
}
```

Execute the search request.

```php
$result = $request->execute();
```

Trap for errors.

```php
if (FileMaker::isError($result))
{
  echo "<p>Error: " . $result->getMessage() . "</p>";
  exit;
}
```

Display the header for the results table.

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
    <th>Delete</th>
  </tr>';
```

Display the content from the fields using the foreach loop to display each of the array.

```php
foreach ($records as $record) {
  echo '<tr>';
  echo '<td>' . $record->getField('FirstName') . '</td>';
  echo '<td>' . $record->getField('LastName') . '</td>';
  echo '<td>' . $record->getField('Number') . '</td>';
  echo '<td>' . $record->getField('Date') . '</td>';
  echo '<td>' . $record->getField('TimeStamp') . '</td>';
  echo '<td>' . $record->getField('Calculation') . '</td>';
  echo '<td>' . $record->getField('RecordID') . '</td>';
  echo '<td><a href="DeleteDetail.php?id=' . $record->getID() . '">delete</a></td>';
  echo '</tr>';
}
```

Close the table and the PHP code.

```php
echo '</table>';
?>
```

# Delete - Detail

![](img/5a2c5fda68d42e5d65f51850276e49ec_114_0.png)

| First Name | Last Name | Number | Date | Time Stamp | Calculation | Record ID | Delete |
|---|---|---|---|---|---|---|---|
| Tim | | | | | | | |
| Fred | | | | | | | |
| Mike | | | | | | | |
| Heath | | | | | | | | |
| Mike | | | | | | | | |
| Bell | | | | | | | | |
| Kevin | | | | | | | | |
| Emes | | | | | | | | |
| Frost | | | | | | | | |
| Garland | | | | | | | | |
| John | | | | | | | | |
| Luke | | | | | | | | |
