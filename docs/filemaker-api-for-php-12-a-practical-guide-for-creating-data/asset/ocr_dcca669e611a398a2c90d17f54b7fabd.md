Close out the table and the PHP code.

```
echo '</table>';
?
```

![](bbox=[0.095, 0.153, 0.705, 0.343])

Figure 7-23: SearchResultsPortal.php page.

SearchResultsDetailPortal.php

Always start by including the connection to the database.

```
<php
include("../Conndbase.php");
?
```

Start by retrieving the records based on the id used in the URL. Store the records in the $record variable
$record = $fm->getRecordById("Demo php", $_GET["id"]);

Check to make sure the id value is valid. Otherwise, stop the script and alert the user.

```
if (empty($_GET["id"))
{
    die('The RecordID is missing.\');
}
```

The next section of code checks to see if the newRelatedData was set from the below. If it was you can tell the to create a new record using the related data table and store the results in the $new_record variable. Next, you can update the Text field with the value passed in the URL from the form. Usually, you'll need to commit the request. Finally, you can call the $fm object to get the id value used in the URL from the $record variable.

```
if (isset($_POST["newRelatedData\]))
{
    $new_record = $record->newRelatedRecord("related_data");
    $new_record->setField("related_data::Text", $_POST["Text"]);
    $result = $new_record->commit();
    $record = $fm->getRecordById("Demo php", $_GET["id"]);
```

Next, store all the records in the $related_records variable and create the $table_data variable to store the HTML for the form. This will allow the PHP code to display the results with a new form after the user clicks the