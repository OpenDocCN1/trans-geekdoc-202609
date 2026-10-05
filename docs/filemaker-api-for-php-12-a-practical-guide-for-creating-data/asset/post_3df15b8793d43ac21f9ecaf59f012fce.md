
```php
<?php
for($counter=1; $counter<=5; $counter++)
{
    echo "Number " . $counter . "<br>";
}
?>
```

When you want to display records from the database you will use the foreach loop — foreach($array as $value). To make the foreach loop easy you should define the $array as plural ($records). Then define the $value as a singular ($Record). Notice the example below displays the data from the FirstName and LastName fields for each record. You also have to include all the correct html structure for the table row and data tags in a foreach loop.

## foreach($records as $record)

```php
echo '<tr>';
echo '<td>' . $record->getField('FirstName') . '</td>';
echo '<td>' . $record->getField('LastName') . '</td>';
echo '</tr>';
```

## Arrays

A variable stores a single piece of data such as a number or text, whereas an array is a special variable that can store multiple values or records from a database in a single variable. The hardest part about arrays and databases is visualizing the actual data in the array and where each record is located in the array. With FileMaker Pro you can see the (array) while you loop through the Script Debugger. You're not going to be fortunate when you use PHP as there is no debugger and there is no direct connection to the database that shows the records as you loop through the code. Therefore, it will take a bit of imagination to work with arrays, especially when you only need to work with a specific range of records such as 11 through 20 of 100.

There are three types of arrays. Numeric is the most common. It assigns an index number to each of the records in the array, starting with 0. An associative array uses an ID key with each value. Multidimensional array is an array of arrays.

In the numeric example below the $names array contains 3 records. The output displays the value of each record in the array. If you want to extract a specific record from the array you can use the index number. This is a common approach if you just want the first record. Otherwise, in most cases you'll be using a foreach loop, which does not require you to specify the index number for each record.

```php
<?php
$names=array("Todd", "Fred", "Tim");
echo $names[0] . ", " . $names[1] . ", " . $names[2];
?>
```

## $_GET, $_POST, $_REQUEST

Forms are a requirement to build web sites, create, update, and delete records in your database. The main thing about PHP is that all the form elements are automatically available to the PHP scripts using the $_GET, $_POST, $_REQUEST. How you retrieve the content of the elements depends on your use of the get and Post methods in the form. The form will send all the information to the web page via the URL. With that method users may be able to see the information in the URL and you don't want them to see and they may also be able to bookmark pages that change over time. The other downfall is that the Get method is limited to 2048 characters, which in general, you should only use the Get method when you are searching for records or navigating between pages. For all other circumstances you should use the Post method. The Post method sends all the information in the header of the request. That means that the data, although not encrypted, is hidden from the users. You can also theoretically send an unlimited amount of data using the Post method. However, the PHP.ini configuration file is pre-set to limit the max_post_size to 8 MB. You can change this if you need some more data. Therefore, the Post method should be used to create, update, and delete records and hide information you do not want the user to see.

The form itself has many elements. The first required element is the form tag. The action specifies what web page is going to be sent to. Depending on how you build your web page(s) you can send the information back to the same page or send it to a totally different page. My personal preference is to use two pages because it makes the intended use of pages more obvious in the code and each page has level troubleshoot. Next, in the forms you can do things as send hidden values that you don't want displayed on the Search: for example you can pass the ID from the URL using PHP code. For a standard search field you'll include a text box that the users can fill in. In the example search below I included a text field the name Search, which will be the name of the value in the URL. Lastly, in the example I included a button named Search that allows the user to submit their request. This way allows you to differentiate between multiple buttons in the form such as delete, cancel, edit, etc. to ensure the correct code based on the user's choice.

```html
<form action="Forms.php" method="get">
    <input name="ID" type="hidden" value="<?php echo $_REQUEST['ID']; ?>">
    Search: <input name="Search" type="text">
    <input name="submit" type="submit" value="Search" />
</form>
```

When you send information from a form it sends the data as name=value pairs. In the example above, the forms send three name=value pairs. For example, ID=3 and Search=Todd. The one most people forget about is the name=value pair for the buttons, which is submit=Search. All name=value pairs are separated by ampersand (&); The URL when you click the Search button for the form will look like:

`http://localhost/Forms.php?ID=3&Search=Todd`

Remember I said earlier that all elements are available to PHP scripts. That means that you retrieve any information from a Get or Post method using the superglobal $_GET, $_POST, and $_REQUEST. If you use the Get method in your form you can retrieve any value by specifying the name. In the example you could use $_GET['Search'] to retrieve the value from the field. If you use the Post method you'd use $_POST['Search'] to retrieve the contents. If you want to retrieve the contents regardless of which method was used use $_REQUEST['Search']. I have noticed that using the $_REQUEST method throws errors. Therefore, you will have to use $_GET or $_POST depending on the method chosen.

## Sample Database

Included with the samples for this book is a fully database file php_demo.fmp which you should have already uploaded to the server. You will use this file for all the example PHP web pages. It includes every possible type of field, value list, portal, layout, scripts, etc. to provide you with a complete example file. The file is set to automatically open with the following account:

Account: Admin
Password: 1234

Normally you would never use the Admin account or a simple password as it is easily broken. However, for demonstration purposes it will work fine.

![](img/5a2c5fda68d42e5d65f51850276e49ec_69_0)

## Table Structure

The table structure is very simple to work with. First is interacting with a single table. Second is interacting with a related table: For much of the demo pages you only work with php_demo. Then you'll work with related records which use the related data table. There's nothing spectacular about the relationship between the two tables. The php_demo file uses the RecordID to make the relationship to the FK field in related_data table. FK stands for "foreign key". The table is used as part of the demo files that run a script to upload files to the user's computer. Think of it as a table log to document what files were uploaded and if the upload was successful.

> You will NOT interact with the actual tables using the FileMaker API for PHP. You will need to create specific layouts with all the elements (i.e. fields, portals, value lists, etc.) you want to access.

![](img/5a2c5fda68d42e5d65f51850276e49ec_69_1)

![](img/5a2c5fda68d42e5d65f51850276e49ec_70_0)

## Fields

The php_demo has options for Auto-Enter and Validation. This is the main table that you will work with so you can learn how to work with every possible field. One field that you should take note of is the RecordID. This is used to uniquely identify the records based on an internally generated, unmodifiable FileMaker ID number used as the primary key to make the relationship to the related_data table. If you are building web pages it will be much easier to create relationships using the RecordID rather than auto-enter server field number since the FileMaker API for PHP can easily acquire the RecordID number with the built-in dynamic method — getRecordID().

The FileMaker API for PHP uses the RecordID to find records, not the auto-enter server number.

| Field Name | Type | Options / Comments (Click to toggle) | View by |
| :--- | :--- | :--- | :--- |
| * FirstName | Text | Indexed, Maximum, Allow Override | |
| * Lastname | Text | Indexed, Maximum | |
| * Number | Number | Indexed, Required, Numeric Range, Maximum | |
| * Date | Date | Required Value | |
| * Timestamp | Timestamp | Required Value | |
| * Calculation | Calculation | Unstarred | |
| * RecordID | Calculation | Indexed — Number + Get(RecordNumber) | |
| * Email | Text | Indexed, Maximum, Message | |
| * URL | Text | Indexed, By Calculation | |
| * Password | Text | Indexed, By Calculation | |
| * Username | Text | Unstarred — Get(RecordModificationCount) | |
| BooleanCheckbox | Number | Indexed | |
| * Checkbox | Text | Indexed, By Value List | |
| * MultValueList | Text | Indexed | |
```
