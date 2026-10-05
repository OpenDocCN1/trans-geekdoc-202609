# Lesson 12: Display Container Field

**Objective:** In this lesson you will learn how to display the contents of a container field using the ContainerBridge.php file. Although this technique works, it's not recommended if you have large record sets or large images as the server and web publishing engine will take a serious performance hit to display the images. You are much better off in all cases using a test field that contains the path to the image stored on the server. However, since the method is available, it's important to show how to use it. If you are using the container field feature to store your image externally to the database you will want to use the containerDataURL method instead.

**Difficulty:** Easy

**Sample Files:** PHPFiles/Advanced/Lesson12/DisplayContainerField.php

**Page Navigation:**

![](bbox=[0.085, 0.31375, 0.165, 0.37375])

**FileMaker API Methods:**
newFindAddCommand(
execute()
getRecords()
getField()

**Code:**
Always start by including the connection to the database.

```
<?php
include("../Conn/dbaccess.php");
?>
```

This is a simple example that displays all records from the Demo page layout.

```
$request = \$fm->newFindAllCommand('Demo php');
$result = \$request->execute();
```

Check for errors.

```
if (FileMaker::isError($result))
(
echo "<p>Error: " . \$result->getMessage() . "</p>";nexit;
)
```

Get the records and store the results in the $records array.

Create the header for the table to display the records.

```
echo "<table border="1">
<tr>
<th>First Name</th>
<th>Last Name</th>
<th>Container</th>
</tr>";
```