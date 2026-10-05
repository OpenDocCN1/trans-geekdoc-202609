
23
You can clearly see the display between the [brackets] and the value after the arrow =>. The question is how you extract the content from the array and place it into the correct code location for the value list? You do that by assigning the associative array variable for the $displayValue and the $value. That way you can extract each value correctly when you loop through the array with the foreach loop. Finally, echo the value list using the $showSecondVariable.

```php
$layout = $this->getLayout('Demo');
$values = $layout->getValueListTwoFields('ShowSecond');
$showSecond = '<select name="showSecond">';
foreach($values as $displayValue => $value) {
    $showBoth .= '<option value="' . $displayValue . '">' . $displayValue . '</option>';
}
$showSecond .= '</select>';
echo $showSecond;
```

![](img/5a2c5fda68d42e5d65f518502765e49ec163_0.png)
Figure 7-35: ListTwoFields.php page.

## Lesson 14: Display Search Results

**Objective:** In this lesson you will learn how to display the record count from the database after a search. For example: Displaying 3 Record(s) of 10 total.

**Difficulty:** Easy

**Sample Files:** SearchResultsLabel.php

**Navigation:** ![](img/5a2c5fda68d42e5d65f518502765e49ec164_0.png)

**FileMaker Methods:**
- newFindCommand()
- execute()
- getMessage()
- getTableRecordCount()
- getFoundSetCount()
- getRecords()
- getField()

**Code:**
```php
<?php
include('../Conn/dbaccess.php');
Always start by including the connection to the database. Find all the records. Then execute the search.
$request = $fm->newFindCommand('Demo');
$result = $request->execute();

if ($result->isError()) {
    echo "Error: " . $result->getMessage();
    exit;
}
// Trap for errors. Build the search results message to display the search results at the top of the table. For example: Displaying 3 Record(s) of 10 total. If no records are found you can display 'No records.'. The $total variable stores the number of records in the table using the getTableRecordCount method. The $found variable stores the found count using the getFoundSetCount method.
```php
$total = $result->getTableRecordCount();
$found = $result->getFoundSetCount();
if($found == 0) {
    $record_count = 'No records.';
} else {
    $record_count = 'Displaying ' . $total . ' record(s) of ' . $found . ' total';
}
```
```php
$total = $result->getTableRecordCount();
```
```php
$found = $result->getFoundSetCount();
```
// Now that we have the display for the $record_count we can get the records and build the HTML table with the fields. Start by getting all the records from the $result. Create the header for the table. Display the $record_count message at the top of the table.
```php
echo '<td>' . $record_count . '</td>';
<table border="1">
    <tr>
        <th>First Name</th>
        <th>Last Name</th>
        <th>Number Number</th>
        <th>Date</th>
        <th>Time Stamp</th>
        <th>Calculation</th>
        <th>Record ID</th>
    </tr>
```
// Use the foreach method to loop through the records and display the fields.
```php
foreach ($records as $record) {
    echo '<td>' . $record->getField('FirstName') . '</td>';
    echo '<td>' . $record->getField('LastName') . '</td>';
    echo '<td>' . $record->getField('Number') . '</td>';
    echo '<td>' . $record->getField('Date') . '</td>';
    echo '<td>' . $record->getField('TimeStamp') . '</td>';
    echo '<td>' . $record->getField('Calculation') . '</td>';
    echo '<td>' . $record->getField('RecordID') . '</td>';
}
echo '</table>';
?>
```

## Search Label

Displaying 28 record(s) of 28 total

| First Name | Last Name | Number Number | Date | Time Stamp | Calculation | Record ID |
|---|---|---|---|---|---|---|
| Todd | Doell | 47 | 09/07/2010 | 08/03/2010 | 15:46:50 | 48 |
| Tim | Warner | 13 | 08/01/2010 | 08/01/2010 | 14:56:50 | 55 |
| Fred | Hutchinson | 14 | 08/09/2010 | 08/09/2010 | 11:54:22 | 17 |
| Mike | Adams | 37 | 08/25/2010 | 09/09/2010 | 15:20:31 | 81 |
| Heath | Bell | 21 | 08/25/2010 | 09/09/2010 | 15:20:26 | 82 |
| Kevin | Correia | 29 | 08/25/2010 | 09/09/2010 | 15:20:47 | 83 |
| Eresso | 29 | 08/25/2010 | 09/09/2010 | 15:20:35 | 84 |
| John | Garland | 27 | 08/25/2010 | 09/09/2010 | 15:21:06 | 85 |
| Luke | Gregerson | 57 | 08/25/2010 | 09/09/2010 | 15:21:66 | 86 |
| Mar | Lains | 38 | 08/25/2010 | 09/09/2010 | 15:22:07 | 87 |

Figure 7-36: SearchResultsLabel.php page.

## Lesson 15: Create a Login in Procedure

**Objective:** In this lesson you will learn how to perform a login procedure to protect your web pages from unauthorized access. The basic premise is to start at the Login.php page. If the login is successful and you are able to find a matching record in the database the user is redirected to the protected LoginSuccess.php page. If the user tries to open a protected web page without logging in first they will be redirected back to the Login.php page. Finally, although not required, we will use sessions.

**Difficulty:** Difficult

**Sample Files:** Login.php, LoginSuccess.php, Logout.php

**Navigation:** ![](img/5a2c5fda68d42e5d65f518502765e49ec167_0.png)

**FileMaker Methods:**
- newFindCommand()
- execute()
- getMessage()
- getTableRecordCount()
- getFoundSetCount()
- getField()

**Code:**
```php
<?php
include('../Conn/dbaccess.php');
Always start by including the connection to the database. Find all the records. Then execute the search.
$request = $fm->newFindCommand('Demo');
$result = $request->execute();

if ($result->isError()) {
    echo "Error: " . $result->getMessage();
    exit;
}
// Trap for errors. Build the search results message to display the search results at the top of the table. For example: Displaying 3 Record(s) of 10 total. If no records are found you can display 'No records.'. The $total variable stores the number of records in the table using the getTableRecordCount method. The $found variable stores the found count using the getFoundSetCount method.
```
```php
session_start();
// Initialize session or resumes the current session
$_SESSION['login'] = 0; // To protect your login page
?>

<html>
<head>
<title>Login</title>
</head>
<body>
```
