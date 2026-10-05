
```html
<table>
  <tr>
    <th>Time Stamp</th>
  </tr>
  <tr>
    <td><?php echo $TimeStamp; ?></td>
  </tr>
</table>
<p>
  <input name="save" type="submit" value="Save" />
</p>
<?php echo $message . "<a href=EditRecord.php>Click here to return to the list page</a>"; ?>
</p>
</body>
</html>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_121_0.png)

Click here to return to the list page

Go to "http://127.0.0.1/PHPFiles/Core/Lesson7/EditRecordDetail.php?id=5"

# Figure 7-17: EditRecordDetail.php File.

![](img/5a2c5fda68d42e5d65f51850276e49ec_121_1.png)

Your changes have been saved

Click here to return to the list page

# Figure 7-18: Save the changes and return to the list page.

# Lesson 8: Search Portal->Detail Portal

**Objective:** In this lesson you will learn how to display related records from the database on a detail page. The process to display related records is to pass the RecordID from the list page to a detail page. That allows you to isolate a single record to display the related records.

**Difficulty:** Medium

**Sample Files:**
- PHPFiles/Core/Lessons8/SearchResultsPortal.php
- PHPFiles/Core/Lesson8/SearchResultsDetailPortal.php

**Page Navigation:**

![](img/5a2c5fda68d42e5d65f51850276e49ec_122_0.png)

**FileMaker API Methods:**
- FindAllCommand()
- newCommand()
- addCriterion()
- execute()
- getMessage()
- Records()
- getField()
- RecordID()
- getRecordByID()
- getRelatedSet()

**Code:**

### SearchResultsPortal.php

Always start by including the connection to the database.

```php
<?php
include("./../conn/dbaccess.php");
?>
```

Create a form to search the records. In this case the form is pointed back to the same page using the method.

```html
<form action="SearchResultsPortal.php" method="GET">
First Name: <input name="FirstName" type="text" />
<br />
<input name="submit" type="submit" />
</form>
```

Create the PHP code to search the database and display the results. This is the same as the previous examples.

```php
<?php
if(empty($_GET['FirstName']))
{
$FirstName = "";
$request = $fm->findAllCommand('Demo php');
}
else
{
```

```php
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
if (FileMaker::isError($result)) {
  echo "<p>Error: " . $result->getMessage() . "</p>";
  exit;
}
```

Display the header for the results table.

```php
echo '<table border="1">
<tr>
<th>FirstName</th>
<th>LastName</th>
<th>Number Number</th>
<th>Date</th>
<th>Timestamp</th>
<th>Calculation</th>
<th>RecordID</th>
<th>View Detail</th>
</tr>';
```

Display the content from the fields using the foreach loop to display each of the records from the array.

```php
foreach ($records as $record) {
  echo '<tr>';
  echo '<td>' . $record->getField('FirstName') . '</td>';
  echo '<td>' . $record->getField('LastName') . '</td>';
  echo '<td>' . $record->getField('Number') . '</td>';
  echo '<td>' . $record->getField('Date') . '</td>';
  echo '<td>' . $record->getField('Timestamp') . '</td>';
  echo '<td>' . $record->getField('Calculation') . '</td>';
  echo '<td>' . $record->getField('RecordID') . '</td>';
```

Create the link to view the detail page. Pass the RecordID to the SearchResultsDetailPortal.php page so the individual record is isolated.

```php
echo '<td><a href="SearchResultsDetailPortal.php?id=' . $record->getRecordID() . '">delete</a></td>';
} '</tr>';
```

Close the table and the PHP code.

```php
echo '</table>';
?>
```

# Search Results -> Detail

First Name: Todd

Submit

| First Name | Last Name | Number | Date | Time Stamp | Calculation | Record ID | View Detail |
|---|---|---|---|---|---|---|---|
| Todd | Duell | 47 | 09/07/2010 | 15:46:58 | | 52 | View |
| Tim | Warner | 13 | 08/01/2010 | 15:46:50 | | 54 | View |
| Fred | Hutchinson | 14 | 08/09/2010 | 11:54:22 | | 59 | View |
| Mike | Adams | 37 | 08/25/2010 | 13:20:21 | | 81 | View |
| Heath | Bell | 21 | 08/25/2010 | 13:31:26 | | 82 | View |
| Kevin | Correa | 29 | 08/25/2010 | 15:23:45 | | 83 | View |
| Ernesto | Frier | 39 | 08/25/2010 | 20:55:46 | | 84 | View |
| John | Garland | 27 | 08/25/2010 | 21:06:35 | | 85 | View |
| Luke | Gregson | 57 | 08/25/2010 | 25:21 | | 86 | View |
