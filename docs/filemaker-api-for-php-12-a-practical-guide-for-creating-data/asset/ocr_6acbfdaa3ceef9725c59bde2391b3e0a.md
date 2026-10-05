```
<?php echo $table_data; ?>

<?php
echo '<a href="SearchResultsPortal.php">Click here to return to the list
view.</a>';
?>
```

![](bbox=[0.098, 0.145, 0.635, 0.403])

```
 <a href="http://127.0.0.1/PHP/Core/Lesson1/SearchResultsDetailPortal.php?id=12">
```

Figure 7-27: SearchResultsDetailPortal.php page.

# EditRecordDetail.php

The last step in this 3-part process is to isolate the related record so it may be deleted. Always start by the
connection to the database.

```
<?php
include ('../Conn/dbaccess.php');

```

Start the PHP code by coding the Post to see what action to take. By using the form won't display after
t user clicks the Delete button. Otherwise it will display the data to be deleted from the Text field.
Just like the previous example, the form passes hidden values for the related record and parent Record ID so
can be properly deleted and the user can click a link back to the original parent record.

```
if (isset($_POST['delete'])) {
$display = ' Are you sure you want to delete record id: ' .$record->getField('RecordID').?';
$display .= '<form action="DeleteRecordDetailPortal.php" method="post">';
$display .= '<input type="hidden" name="id" value="'.$_REQUEST['id']." />';
$display .= '<input type="hidden" name="parent" value="'.$_REQUEST['parent']." />';
}';
$display = '<p>';
$display .= '<table>';
$display .= '<tr>';
$display .= '<td>'. . $record->getField('Text') . '</td>';
$display .= '</tr>';
$display .= '</table>';
$display .= '<p>';
$display .= '<input type="submit" name="delete" value="Delete" />';
$display .= '<input type="submit" name="delete" value="Cancel" />';
$display .= '</form>';
}
else
else
```