```
$FirstName = $_GET['FirstName'];
$request = $fm->newFindCommand('Demo php');
$request->findCriterion('FirstName', $FirstName);
}
```

Execute the search request.

```
$result = $request->execute();
```

Trap for errors.

```
if (FileMaker::isError($result)) {
  echo "<p>Error: " . $result->getMessage() . "</p>";
  exit;
}
```

Display the header for the results table.

```
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
</tr></tr>
```

Display the content from the fields using the foreach loop to display each of the records from the array.

```
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

```
echo '<td><a href="SearchResultsDetailPortal.php?id=' . $record->getRecordID() . '">delete</a></td>';
}</tr>
```

Close the table and the PHP code.

```
echo '</table>';
?>
```