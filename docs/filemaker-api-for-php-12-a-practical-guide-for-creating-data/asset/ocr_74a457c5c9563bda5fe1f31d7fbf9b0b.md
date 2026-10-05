# Lesson 14: Display Search Results

**Objective:** In this lesson you will learn how to display the record count from the database after a search request.
For example: Displaying 3 Record(s) of 10 total.

**Difficulty:** Easy

**Sample Files:** SearchResultsLabel.php

**Page Navigation:**

![](bbox=[0.106, 0.213, 0.233, 0.283])

**FileMaker API Methods:**

+   - newFindAllCommand()
- execute()
- getMessage()
- getTableRecordCount()
- getFoundSetCount()
- getRecords()
- getField()

**Code:**

```
<?php
include(\../Conn/dbaccess.php\n?>
```

Always start by including the connection to the database.
Find all the records. Then execute the search request.

```
$request = $fm->newFindAllCommand('Demo php');
$result = $request->execute();

if (FileMaker::isError($result)) {
echo "Error: " . $result->getMessage() . "</p>";
exit;
}
```

Trap for errors.

Build the search results message to display the search results at the top of the table. For example: Displaying 3 Record(s) of 10 Total. If no records are found you can display the 'No records found.'. The $total variable stores the number of records in the table using the getTableRecordCount method. The $found variable stores the found count using the getFoundSetCount method.

```
$total = $result->getTableRecordCount();
$found = $result->getFoundSetCount();
if($found == 0) {
$record_count = 'No records found.';
} else {
$record_count = 'Displaying ' . $total . ' record(s) of ' . $found . ' total';
}
```