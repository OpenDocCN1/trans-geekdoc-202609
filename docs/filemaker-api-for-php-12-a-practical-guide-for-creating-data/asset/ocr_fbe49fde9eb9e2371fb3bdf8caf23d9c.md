# Lesson 13: Display a List Menu

**Objective:** In this lesson you will learn how to create a list menu (i.e. drop menu) for use in a form. The list menu will use the SampleValueList in the database.

> Although this method is technically deprecated, it still works. You should use the two field value list method described in the next method.

**Difficulty:** Medium

**Sample Files:** PHPFiles/Advanced/Lesson13/ListMenu.php

**Page Navigation:**

![](bbox=[0.106, 0.298, 0.292, 0.365])

**FileMaker API Methods:**

+   getLayout()
getValueList()
AddNewCommand()
setField()
execute()
getMessage()

**Code:**

Always by including the connection to the database.

```
<?php
include("../Conn/dbaccess.php");
?>
```

Start by creating the HTML for the list menu. List menus are repetitive, which makes it quick for a database and PHP. A typical list menu will look like this:

```
<select name="Number">
<option value="123">123</option>
<option value="456">456</option>
<option value="789">789</option>
</select>
```

Get the objects from the layout where the drop down menu is being used. You have to include drop down menus on the fields in the Demo php layout you want to access them on your web page.

```
$layout = &$php->getLayout('Demo php');
```

> FileMaker API Syntax: getLayout('LayoutName')
$layout = &$php->getLayout('Demo php');

Once you have the layout objects you can use the getValueList method to retrieve the contents of the SampleValueList stored in the database.