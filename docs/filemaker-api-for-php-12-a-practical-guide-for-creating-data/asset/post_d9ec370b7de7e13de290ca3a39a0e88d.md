
<table>
  <tr>
    <th>Last Name</th>
    <td><input type="text" name="LastName" value="<?php echo $LastName; ?>" /></td>
  </tr>
  <tr>
    <th>Number</th>
    <td><input type="text" name="Number" value="<?php echo $Number; ?>" /></td>
  </tr>
  <tr>
    <th>Date</th>
    <td><?php echo $Date; ?></td>
  </tr>
  <tr>
    <th>Time Stamp</th>
    <td><?php echo $TimeStamp; ?></td>
  </tr>
  <tr>
    <th>Modification ID</th>
    <td><?php echo $modID; ?></td>
  </tr>
</table>
<p>
  <input name="save" type="submit" value="Save" />
</p>
<p>
  <?php echo $message; ?> '<a href="MultiUserEditRecord.php">Click here to return to the list page</a>' '
</p>
</body>
</html>

![](img/5a2c5fda68d42e5d65f51850276e49ec_207_0.png)

| First Name | Todd |
| :--- | : |
| Last Name | Dwell |
| Number | 57 |
| Date | 09/07/2010 |
| Time Stamp | 08/03/2010 15:46:50 |
| Modification ID | 147 |

Click here to return to the list page

Figure 7-53: MultiUserEditRecordDetail.php page.

## Lesson 21: Run a Script — Import XLS File

**Objective:** In this lesson you will learn how to upload an Excel file to the server. Then use a script to import the records from the Excel file. We are well accustomed to importing data using FileMaker Pro. Unfortunate, that's not possible from a web page. The only way to import data is from a file stored on the server. FileMaker Server will only import records from the Documents folder. That location is not inside the web root directory. PHP cannot move files outside the root directory for security issues — you wouldn't want an unknown web user moving over your server or network. Therefore, we'll need to utilize the Trio File plugin to move the file from the web root to the FileMaker Documents folder.

This is an Apache/OS X technique. IIS throws too many generic 500 errors with this PHP code. The code runs on IIS, but it still displays an error after the upload is completed. You will need the Trio File plugin server license to use this technique. Please follow the instructions from Trio to install the plugin on FileMaker Server for use with the web publishing engine. You can obtain the Trio File Plugin demo from our web site at www.trio.com or from the provided sample files. As of the writing this I have validated the use of version 6 of the plugin.

Difficult

**Sample Files:**
- PHPFiles/Advanced/Lesson21/Import.php
- PHPFiles/Advanced/Lesson21/Trio File Plugin v6.1
- PHPFiles/Advanced/Lesson21/Import/sample_import.xls

Page Navigation:

![](img/5a2c5fda68d42e5d65f51850276e49ec_208_0.png)

**FileMaker API Methods:**
- newSqlCommand()\execute()
- getMessage()
- newFindAllCommand()
- getLastRecord()
- EditRecord()
- newEditCommand()
- setField()
- PerformScriptCommand()

**Code:**
I've already used the import process in an earlier example. Therefore, there's nothing really new from the PHP code perspective. The important changes in this process come from the use of the Trio File Plugin and the FileMaker script to move the xls file from the root directory to the FileMaker Server Documents folder.

Always start by including the connection to the database.

```php
<?php
include("../../Conn/dbaccess.php");
?>
```

Create the variables for the messages to display to the users during the import process.

```php
<?php
echo $message;
```

```php
echo $importMessage;
?>
```

Create the form to import the file to the server. Click Import to run the script to import the records.

```html
<p>
  <form action="ImportXLS.php" method="post" enctype="multipart/form-data">
  upload xls file for import: <input name="xls_file" type="file" />
  <input type="submit" name="import" value="Import" />
  </form>
</p>
```

Check if the user clicked the Import button. Validate the file they are trying to upload is an Excel file using application/vnd.ms-excel.

> You NEVER allow unknown users to import records to your database. This process generally be reserved for internal employees or trusted business partners.

```php
if (isset($_POST['import']) == 'Import') {
  if ($_FILES['xls_file']['type'] == 'application/vnd.ms-excel') {
```

Add a new record to the Import php table. For this example, I'm using a separate table to track all the files that are used to import records in the database. You can think of it as a log file. That way you can troubleshoot any files that failed to import the file.

```php
$request = $fm->newAddCommand('Import php');
$request->execute();
```

Trap for errors, if the import was successful you can get the Record ID from the very last record, which will be by the FileMaker script. Of course, if the validation failed to the file not being Excel, you should supply the user with an error message and stop the script.

```php
if (FileMaker::isError($result)) {
  $message = "<p>" . $result->getMessage() . "</p>";
  exit;
} else {
  $request = $fm->newfindAllCommand('Import php');
  $result = $request->execute();
  $record = $result->getLastRecord();
  $id = $record->getObjectID();
} else {
  $type = $_FILES['xls_file']['type'];
  die ('Only xls files are allowed to be uploaded: ' . $type);
}
```

```php
// FileMaker Syntax: getLastRecord()
$record = $result->getLastRecord();
```

Next, check for any generic errors returned from the $_FILES superglobal.

```php
if ($_FILES['xls_file']['error'] > 0) {
    $error = $_FILES['xls_file']['error'];
    die ('There was an error moving file: ' . $error);
}
```

Define the directory on the server.

```php
$import_directory = 'Import/';
```

Get the temporary name of the file.

```php
$temporary_file = $_FILES['xls_file']['name'];
```

Obtain the extension from the file.

```php
function extension($filename) {
    $parts = explode(".", $filename);
    $ext = end($parts);
    return $ext;
}
```

Move the file to the server.

```php
$move = rename($temporary_file, $import_directory . $filename);
if ($move) {
    $url = $import_directory . $filename;
    $insert = $fm->newEditCommand('Import php');
    $insert->setField('URL', $url);
    $insert->execute();
}
```

Finally, provide the user with a message telling them the uploaded.

```php
$importMessage = '<p>The file was uploaded successfully.</p>';
```

```php
echo '<meta http-equiv="refresh" content="3;URL=' . $_SERVER['PHP_SELF'] . '">';
?>

![](img/5a2c5fda68d42e5d65f51850276e49ec_211_0.png)

Figure 7-54: ImportXLS.php page.

## PHP Import Records

The FileMaker Script imports records from an xls file I decided to create a fully example that logs the import process. In a production system it's important to know when an import failure occurs and on which file. That way you can rewrite your script before it is successful. It will also allow you to schedule the import for the night to reduce the peak hours usage of the server.

There are a couple of ways to move the file from the root folder to the FileMaker Documents folder. I believe that the Trio Plugin is the best method as it works in conjunction with the FileMaker script and it's relatively easy to work with. Plus the plugin is very versatile for many tasks. The only downfall is that it is not free. You do need the web license for this process.

There are couple of free methods to move the file. The first method is using the Folder Action and Automator on OS X. With this method it may cause your script to fail the file was not moved in time before the script reaches the Import Records steps. The Pause script is not available to FileMaker Server. Therefore, your only option to use Folder Actions and Automator is to use a scheduled script FileMaker Server to batch import all the files uploaded to the server. Therefore, you will have to wait until the night when the server isn't quite busy. The downfall is future support of Folder Actions and Automator. In my experience the OS X scripts seem to change dramatically with OS update/upgrade.

The other free process that will work is to create a shell script (OS X) or batch script (Windows) to move the file. Use then the FileMaker Server Schedule to run the shell or batch script prior to running the import script. Again, you still have to run a scheduled script, which will delay the import process based on the time the schedule.
