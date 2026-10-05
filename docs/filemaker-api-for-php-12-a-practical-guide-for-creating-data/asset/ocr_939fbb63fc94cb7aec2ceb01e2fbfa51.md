# Lesson 19: Display Record Navigation

**Objective:** In this lesson you will learn how to create links for record navigation. This will enable your users to navigate one record at a time, which is similar to Page View in FileMaker using the bookmark icons. You will create links for the first record, go to the previous record, go to the next record, and go to the last record.

**Difficulty:** Difficult

Sample Files:
PHPFiles/Advanced/Lesson19/Naviation.php
PHPFiles/Advanced/Lesson19/images/first_record.php
PHPFiles/Advanced/Lesson19/images/last_record.php
PHPFiles/Advanced/Lesson19/images/next_record.php
PHPFiles/Advanced/Lesson19/images/previous_record.php

**Page Navigation:**

![](bbox=[0.118, 0.313, 0.255, 0.375])

**FileMaker API Methods:**
newfindAllCommand()
addFindCriterion()
setRange()
getMessage()
getRecords()
getFoundCount()
TableRecordCount()
getField()

**Code:**



```
<?php
include("../Conn/dbaccess.php");
?>
```

Create the search form to the same page using the Get method. Include the default skip value of 0 and the max value of 1. This will place the user on the first record and display one record at a time.

```
<form action="<?php echo($_GET['search']); ?>" method="get" id="search">
<input name="skip" type="hidden" value="0" />
<input name="max" type="hidden" value="1" />
First Name: <input name="FirstName" type="text" />
<input name="submit" type="submit" id="submit" value="Submit" />
</form>
```

Start by finding the records. If the FirstName has not been entered find all records in the table. Otherwise search the records by the FirstName name.

```
if(empty($_GET['FirstName'])) {
$FirstName = "";
$request = $fm->newfindAllCommand('Demo php');
}
```