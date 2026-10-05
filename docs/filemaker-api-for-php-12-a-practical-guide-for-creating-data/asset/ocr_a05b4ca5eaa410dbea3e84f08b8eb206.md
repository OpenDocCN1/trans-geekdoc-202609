```
}
```

Execute the search request.

```
$result = $request->execute();
```

Trap for errors.

```
if (FileMaker::isError($result))
{
    echo "<Error: " . $result->getMessage() . "</p>";
    exit;
}
```

Get the records as an array in the $records variable.

```
$records = $result->getRecords();
```

Create the header to display the records.

```
echo '<table border="">
<tr>
<th>First Name</th>
<th>Last Name</th>
<th>Number Number</th>
<th>Date</th>
<th>Time Stamp</th>
<th>Calculation</th>
<th>Record ID</th>
<th>View Detail</th>
</tr>';"
```

Loop through all the records using the fetch method. Display the contents from the fields using the getField method. The last column contains the view link to the detail page. When the user clicks the link it will open the detail page and pass the name as "id" and the value as the RecordID from the record using the method getRecordID.

```
foreach ($records as $record) {
    echo '<td>' . $record->getField('FirstName') . '</td>';
    echo '<td>' . $record->getField('LastName') . '</td>';
    echo '<td>' . $record->getField('Number') . '</td>';
    echo '<td>' . $record->getField('Date') . '</td>';
    echo '<td>' . $record->getField('Timestamp') . '</td>';
    echo '<td>' . $record->getField('Calculation') . '</td>';
    echo '<td>' . $record->getField('RecordID') . '</td>';
    echo '<td><a href="SearchResultsDetail.php?id=" . $record->getRecordID() . '">view</a></td>';
</tr>
```

![](bbox=[0.108, 0.813, 0.178, 0.866])

FileMaker API Syntax: getRecordID()
$record->getRecordID();