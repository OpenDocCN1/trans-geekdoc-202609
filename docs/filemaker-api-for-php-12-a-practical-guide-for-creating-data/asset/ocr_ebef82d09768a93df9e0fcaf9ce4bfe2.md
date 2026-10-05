# Lesson 3: Search Records, Simple

**Objective:** In this lesson you will learn how to search for records based on a single field using a form.

**Difficulty:** Easy

**Sample Files:** PHPFiles/Core/Lessons/SearchRecordsSimple.php

**Page Navigation:**

Search

**FileMaker API Methods:**

```
newFindAllCommand()
newFindAllCommand()
addCriterion()
execute()
getMessage()
getRecords()
getField()
```

**Code:**

Always start by including the connection to the database.

```
<?php
include("../dbaccess.php");
```

Create the search form to find the file SearchRecordsSimple.php to search by the field FirstName. This file will act as both the search form and the display for the set of records. The form uses the Get method, which means the search string will be viewable in the URL for the user. The input name FirstName will be passed as the name in the URL. I prefer to use the actual name of the field to make it easier to read the URL. The value will be what the user types in the search box.

```
<form action="SearchRecordsSimple.php" method="get">
First Name:<input name="FirstName" type="text" />
<br>
<input name="submit" type="submit" />
</form>
```

Start the code by checking the URL $_GET superglobal for the FirstName. If it's empty tell the $request variable to add all the records on the demo php layout. Otherwise, use the $_GET superglobal to retrieve the FirstName value from the URL. Then fill the fm object to add a new find command to the $request variable. Finally, tell the $request variable to add the find criteria to the FirstName field using the contents from the FirstName variable.

```
<?php
if(empty($_GET['FirstName']))
$FirstName = ""
$request = $fm->newFindAllCommand('Demo php');
elelse
{
FirstName = $_GET['FirstName'];
$request = $fm->newFindCommand('Demo php');
$request->addCriterion('FirstName', $FirstName);
}
```