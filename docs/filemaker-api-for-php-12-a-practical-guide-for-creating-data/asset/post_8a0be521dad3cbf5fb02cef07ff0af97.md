
```php
$compoundRequest->add(3, $request3);
$compoundRequest->add(4, $request4);
```

| FileMaker Syntax: add(Precedence, FindRequest) |
| :--- |
| $compoundRequest->add(1, $request1); |

Specify the sort order for the fields. Notice the use of the numbered order to specify the sort field. Remember that FILEMAKER_SORT_ASCEND is the default sort order. You only have to specify FILEMAKER_SORT_DESCEND.

```php
$compoundRequest->addSortRule('MultiValueList', 1, FILEMAKER_SORT_ASCEND);
$compoundRequest->addSortRule('LastName', 2, FILEMAKER_SORT_DESCEND);
$compoundRequest->addSortRule('Number', 3, FILEMAKER_SORT_ASCEND);
```

Finally, execute the request and display the results.

```php
$result = $compoundRequest->execute();
```

Get the records from the $result variable.

```php
$records = $result->getRecords();
```

Trap for errors.

```php
if (FileMaker::isError($result))
{
    echo "<p>Error: " . $result->getMessage() . "</p>";
    exit;
}
```

Create the header for the table.

```php
echo '<table border="1">
<tr>
<th>First Name</th>
<th>LastName</th>
<th>Number</th>
<th>Pet</th>
</tr>';
```

Use the foreach method to display the fields. For the MultiValueList field, I'm using the `str_replace` PHP method to substitute the carriage return with a comma, so the information displays in a more readable format.

```php
foreach ($records as $record)
{
    echo '<tr>';
    echo '<td>' . $record->getField('FirstName') . '</td>';
    echo '<td>' . $record->getField('LastName') . '</td>';
    echo '<td>' . $record->getField('Number') . '</td>';
    echo '<td>' . str_replace("\n", ", ", $record->getField('MultiValueList')) . '</td>';
    echo '</tr>';
}
```

Finally, close the table and the PHP code.

```php
echo '</table>';
?>
```

# Compound Search

First Name*: Todd
OR Last Name*: Hutchinson
OR Number*: 9
OR Pet (OMIT): Cat
* NOTE: All values are required for the search

| First Name | Last Name | Number | Pet |
| :--- | :--- | :--- | :--- |
| Clayton | Richard | 33 | Bird |
| Saif | Lane | 28 | Bird |
| David | Eckstein | 22 | Bird |
| Chris | Denorfia | 13 | Bird |
| Kevin | Corcia | 29 | Bird |
| Tim | Warner | 13 | Dog |

Figure 7-68: CompoundSearch.php file.

# Lesson 27: Quick Find Across All Fields

**Objective:** In this lesson you will learn how to allow a user to dynamically search all the fields on a layout using one search box in the form. By using this method you can specify a separate layout with fewer fields. Then return to a layout to display more fields. This will prevent your database from being indexed and significantly speeds up the search process. This example is similar to the FileMaker Quick Find feature.

**Difficulty:** Difficult

**Sample Files:**

- PHPFiles/Advanced/Lesson27/QuickFind.php
- PHPFiles/Advanced/Lesson27/ContainerBridge.php

Page Navigation:

![](img/5a2c5fda68d42e5d65f51850276e49ec_238_0.png)

**FileMaker API Methods:**

- getLayout()
- getFields()
- findAllCommand()
- newFindCommand()
- setLogicalOperator()
- getName()
- getResult()
- addFindCriterion()
- setResultLayout()
- execute()
- getMessage()
- Records()

**Code:**

Always start by including the connection to the database.

```php
<?php
include("../Conn/dbaccess.php");
?>
```

Get the search criteria from the $_GET super global.

```php
if (isset($_GET['Search'])) {
    $search = $_GET['Search'];
} else {
    $search = '';
}
```

Clear the table html code.

```php
$html = '';
```

Get the quick find layout objects. Use the Quick Find php layout to search on a reduced number of fields. You'll switch back to the Demo page layout below to display all the fields.

```php
$layout = $fm->getLayout('Quick Find php');
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_239_0.png)

Get the fields in an array. This array of fields will be used to dynamically search just the fields on the Quick Find php layout.

```php
$fields = $layout->getFields();
```

Check to see if the user supplied any search criteria. Show all the records if they left the search field blank.

```php
if ($search == '') {
  $request = $fm->newFindFirstCommand('Quick Find php');
}
else {
```

Otherwise, create a new search request.

```php
$request = $fm->newFindFirstCommand('Quick Find php');
```

Use FILEMAKER_FIND_OR so any records with a matching request are returned as you loop through each field.

Loop through each field. Format the search based on the data type for each field: date, time, timestamp, and text. Note: FileMaker will not perform a search on a container field, so you don't need to check for that format. The foreach method used to loop through each field on the layout as defined in the $fields array created above.

```php
foreach($fields as $field)
```

Get the name of the current field in the array.

```php
$fieldName = $field->getName();
```

Get the type of the current field in the array.

```php
$fieldType = $field->getResult();
```

Format the search based on the field type. Start with the format for Date. Use the PHP date method to convert the search criteria to the correct date format.

```php
if ($fieldType == 'date') {
  if (strtotime($search)) {
  $request->addFind($fieldName, date('n/j/Y', strtotime($search)));
  }
}
```

Format the search for Time. Use the PHP date method to convert the search criteria to the correct time format.

```php
elseif ($fieldType == 'time') {
  if (strtotime($search)) {
{
  $request->addFindCriterion($fieldName, date('H:i:s', strftime($search)));
  }
}
```

Format the search for Time Stamp. Use the PHP date method to convert the search criteria to the correct time stamp format.

```php
elseif ($fieldType == 'timestamp') {
  if (strtotime($search)) {
  $request->addFindCriterion($fieldName, date('n/j H:i:s', strftime($search)));
  }
}
```

Format the search for Number. Use the PHP intval method to convert the search criteria to a number.

```php
elseif ($fieldType == 'number') {
  if (intval($search)) {
  $request->addFindCriterion($fieldName, intval($search));
  }
}
```

Finally, if none of the formats are valid you can search the field as text.

```php
else {
$request->addFindCriterion($fieldName, $search);
}
```

Next, specify the result layout to Demo php to show all the fields.

```php
$request->setLayoutLayout('Demo php');
```

Get the fields in an array.

```php
$fields = $layout->getFields();
```

Get the result layout.

```php
$layout = $fm->getLayout('Demo php');
```

Execute the search request.

```php
$result = $request->execute();
```

Trap for errors and redirect the user back to the search page.

```php
if (FileMaker::isError($result)) {
    echo "<p>Error: " . $result->getMessage() . "</p>";
    echo "<a href=" . $_SERVER['PHP_SELF'] . ">Click here to search again</a>";
    exit;
}
```

Get the records in an array.

```php
$records = $result->getRecords();
```

Create the table header.

```php
$html = '<table border="1">';
$html = '<tr>';
```

Loop through the array of field names.

```php
foreach($fields as $field)
{
$fieldName = $field->getName();
$html = '<th>' . $fieldName . 'th';
}
```

Close the header row.

```php
$html = '</tr>';
```

Loop through each record and display the results. The only special field to consider is a container field. All other fields can be output as normal.

```php
foreach($records as $record)
{
$fieldName = $field->getName();
$fieldType = $field->getResult();
if ($fieldType == 'container') {
$contents = '<img src=ContainerBridge.php?path=' . urlencode($record->getField($fieldName)) . ' />';
} else {
$contents = $record->getField($fieldName);
}
$html = '<td>' . $contents . '</td>';
}
```

Close the table row.

```php
$html = '</tr>';
}
```

Close the table and the PHP code.

```php
$html = '</table>';
?>
```

Create the search form and display the html results at the bottom.

```html
<html>
<head>
<title>Quick Find</title>
</head>
<body>
<form action="<?php $_SERVER['PHP_SELF'] ?>" method="get">
<input type="text" name="Search" value="<?php echo $search; ?>">
<input type="submit" value="Search">
</form>
<?php echo $html; ?>
</body>
</html>
```
