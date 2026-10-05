# Lesson 16: Alternate Background

**Objective:** In this lesson you will learn how to display a list of records with an alternating background color. FileMaker has a built in alternating row color for portals for a long time. Records in list view are a different story. There has been many work-arounds for a long time. Fortunately, a web browser doesn't tax the database to alternate the row tag.

**Difficulty:** Easy

**Sample Files:** AlternateBackground.php

**Page Navigation:**

![](bbox=[0.105, 0.246, 0.285, 0.315])

FileMaker newFindAllCommand()\nexecute()\getMessage()\ngetRecords()
getField()

**Code:**

Alternating the background color is best achieved if you use CSS. Normally you would include a separate CSS file. However, to make the demo easier we embedded the CSS for alt_row_color in the page. You can embed the CSS style in the head tag.

```
<html>
<head>
<title>Alternate Background</title>
<style type="text/css">
--
alt_row_color {background-color: #CCCCCC}
--
</style>
</head>
<body>
```

Always start by including the connection to the database.

```
<?php
include("../Conn/dbaccess.php");
?
```

Find all the records. Then execute the request.

```
$request = $fm->newFindAllCommand('Demo php');
$result = $request->execute();
```

Trap for errors.

```
if (FileMaker::isError($result))
{
echo "<p>Error: " . $result->getMessage() . "</p>";
exit;
```