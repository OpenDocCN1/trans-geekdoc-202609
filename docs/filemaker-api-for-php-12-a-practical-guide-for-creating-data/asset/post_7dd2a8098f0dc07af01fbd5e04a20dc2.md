
```php
if(empty($_GET['FirstName']))
{
  $firstName='';
}else{
  $firstName=$_GET['FirstName'];
}
```

Now it starts to get a bit tricky with the logic. You have to determine how many page links you need to display based on the number of records in the found set and the max number of records to display per page. Start by using the module function to figure out if there is a remainder when you divide the count by the max number of records to display. If there is a remainder you'll need to display one extra link for the remaining records on the last page. Otherwise you have an even number of records to pages. The variable $totalLinks will be important in the following code when building the actual pagination links.

```php
if($found % $max > 0)
  $totalLinks = intval($found / $max) + 1;
else
  $totalLinks=intval($found / $max);
```

The final part of the PHP code is to build the actual links so it looks like 1 2 3 4, where the link that is not underlined is the page you are on and the underlined represent other pages of records. During this process the skip value is the only thing that changes as each page has to start at the record number chosen by the while loop and then step down. The skip value of the links will be used as a counter while the while loop runs. TotalLinks calculated above will be used to stop the loop when the n is less than or equal to TotalLinks. $totalLinks also has to be more than 1 page or there's no reason to create the pagination links. The trick to the display is to not create a link for the page the user is on — only display the page number when the page is equal to $. you will need to assemble the URL for the link. The URL will include the values for page, skip, max, and the search criteria for the FirstName. Each time you loop through the code you increment $n by +1 until the criteria is no longer met. The URL will look like the example below.

```http
http://localhost/ToddBuPHP/Pagination.php?page=1&skip=0&max=10&FirstName=Todd&submit=Submit
```

```php
$n=1;
while($n<=$totalLinks && $totalLinks>1)
  if($page == $n)
    echo $n . '&nbsp;'
    $n++;
  else{
    $skip = ($n - 1) * $max;
    echo '<a href="'.$_SERVER['PHP_SELF'] . '?page=' . $n . '&skip=' . $skip . '&max=' . $max . '&FirstName=' . $firstName . '">';
  }
```

Now that the record pagination links are displayed you can use the HTML for the table to display the records.

```php
echo '<table border="1">
<tr>
<th>First Name</th>
<th>Last Name</th>
<th>Number</th>
<th>Date</th>
<th>Time Stamp</th>
<th>Calculation</th>
<th>Record ID</th>
</tr>
';
```

```php
$row = 0;
foreach ($records as $record) { 
    if($row % 2 == 0) {
        echo '<tr class="alt_row_color">';
    } else {
        echo '<tr>';
    }
    echo '<td>' . $record->getField('FirstName') . '</td>';
    echo '<td>' . $record->getField('LastName') . '</td>';
    echo '<td>' . $record->getField('Number') . '</td>';
    echo '<td>' . $record->getField('Date') . '</td>';
    echo '<td>' . $record->getField('Timestamp') . '</td>';
    echo '<td>' . $record->getField('Calculation') . '</td>';
    echo '<td>' . $record->getField('RecordID') . '</td>';
    echo '</tr>';
    $row++;
}
echo '</table>';
?>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_197_0.png)

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

![](img/5a2c5fda68d42e5d65f51850276e49ec_198_0.png)

**FileMaker API Methods:**
- newfindAllCommand()
- addFindCriterion()
- setRange()
- getMessage()
- getRecords()
- getFoundCount()
- TableRecordCount()
- getField()

**Code:**

```php
<?php
include("../Conn/dbaccess.php");
?>
```

Create the search form to the same page using the Get method. Include the default skip value of 0 and the max value of 1. This will place the user on the first record and display one record at a time.

```html
<form action="<?php echo($_GET['search']); ?>" method="get" id="search">
<input name="skip" type="hidden" value="0" />
<input name="max" type="hidden" value="1" />
First Name: <input name="FirstName" type="text" />
<input name="submit" type="submit" id="submit" value="Submit" />
</form>
```

Start by finding the records. If the FirstName has not been entered find all records in the table. Otherwise search the records by the FirstName name.

```php
if(empty($_GET['FirstName'])) {
  $FirstName = "";
  $request = $fm->newfindAllCommand('Demo php');
}
```

```php
else
{
  $FirstName = $_GET['FirstName'];
  $request = $fm->newFindCommand('Demo php');
  $request->addFindCriterion('FirstName', $FirstName);
}
```

Next, tell FileMaker which record to return. If the URL value for skip is empty, display the first record. Otherwise display the record from the URL value. Since this is record pagination (i.e. one page at a time), the max will always be one. Now that you have the variables you can tell FileMaker which record to return and execute the search.

```php
if (empty($_GET['skip']))
{
  $skip=0;
}
else
{
  $skip=$_GET['skip'];
}
if (empty($_GET['max']))
{
  $max=1;
}
else
{
  $max=$_GET['max'];
}
$request->setRange($skip, $max);
$result = $request->execute();
```

Trap for errors.

```php
if (FileMaker::isError($result))
{
  echo "<p>" . $result->getMessage() . "</p>";
  exit;
}
```

Get the record in the $records variables.

```php
$records = $result->getRecords();
```

Finally, display the found text (i.e. 1 of Total).

```php
if (empty($_GET['skip']) || empty($_GET['max'])) {
  $currentRecord = 1;
}
else {
  $currentRecord = $_GET['skip'];
}

$found = $result->getFoundCount();
$total = $result->getTableCount();
echo "<p>Record " . $currentRecord . " of " . $found . " of $total";
?>
```

Now we can move to the next part of this example. How to display the record links. Instead of using text for the links, this demo is going to spice things up and use actual images. The images are included in the folder.
