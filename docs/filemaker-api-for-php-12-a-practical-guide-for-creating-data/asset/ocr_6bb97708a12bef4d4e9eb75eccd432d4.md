# Lesson 24: Multi Value List

**Objective:** In this lesson you will learn how to update a record using a multi value list (i.e. drop down) with more than one value. This example is exactly the same as the check box example. The only difference is the HTML for the multi value list.

**Difficulty:** Medium

**Sample Files:**
PHPFiles/Advanced/Lesson24/MultiValueList.php
PHPFiles/Advanced/Lesson24/UpdateMultiValueList.php

**Page Navigation:**

![](bbox=[0.105, 0.263, 0.305, 0.328])

**FileMaker API Methods:**
newFindAllCommand()
execute()
getMessage()
getFirstRecord()
getRecordID()
Layout()
GetValueList()
getField()
getRecordByID()
newEditCommand()
setField()

**Code:**

MultiValueList.php

Multi value lists use repetitive code to display the content as HTML. That makes it easy for a database and PHP code to assemble the multi value list. If the value is selected, you only need to add "selected". This example will create the multi value list code looks like this:

```
<select name="MultiValueList" size="3">
  <option value="Dog" selected>Dog</option>
  <option value="Cat" selected>Cat</option>
  <option value="Fish">Fish</option>
  <option value="Bird">Bird</option>
</select>
```

Always start by including the connection to the database.

```
<?php
include("../Conn/dbaccess.php");
?
```

Find all the records and execute the search.

```
<?php
$request = $fm->newFindAllCommand('Demo php');
$result = $request->execute();
```