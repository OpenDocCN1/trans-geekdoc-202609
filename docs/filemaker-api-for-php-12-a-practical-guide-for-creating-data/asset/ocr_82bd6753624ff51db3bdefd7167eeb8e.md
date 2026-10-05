```
<?php
for($counter=1; $counter<=5; $counter++)
{
    echo "Number " . $counter . "<br>";
}
?>
```

When you want to display records from the database you will use the foreach loop — foreach($array as $value). To make the foreach loop easy you should define the $array as plural ($records). Then define the $value as a singular ($Record). Notice the example below displays the data from the FirstName and LastName fields for each record. You also have to include all the correct html structure for the table row and data tags in a foreach loop.

# foreach($records as $record)

```
echo '<tr>';
echo '<td>' . $record->getField('FirstName') . '</td>';
echo '<td>' . $record->getField('LastName') . '</td>';
echo '</tr>';
```

# Arrays

A variable stores a single piece of data such as a number or text, whereas an array is a special variable that can store multiple values or records from a database in a single variable. The hardest part about arrays and databases is visualizing the actual data in the array and where each record is located in the array. With FileMaker Pro you can see the (array) while you loop through the Script Debugger. You're not going to be fortunate when you use PHP as there is no debugger and there is no direct connection to the database that shows the records as you loop through the code. Therefore, it will take a bit of imagination to work with arrays, especially when you only need to work with a specific range of records such as 11 through 20 of 100.

There are three types of arrays. Numeric is the most common. It assigns an index number to each of the records in the array, starting with 0. An associative array uses an ID key with each value. Multidimensional array is an array of arrays.

In the numeric example below the $names array contains 3 records. The output displays the value of each record in the array. If you want to extract a specific record from the array you can use the index number. This is a common approach if you just want the first record. Otherwise, in most cases you'll be using a foreach loop, which does not require you to specify the index number for each record.

```
<?php
$names=array("Todd", "Fred", "Tim");
echo $names[0] . ", " . $names[1] . ", " . $names[2];
?>
```

# $_GET, $_POST, $_REQUEST

Forms are a requirement to build web sites, create, update, and delete records in your database. The main thing about PHP is that all the form elements are automatically available to the PHP scripts using the $_GET, $_POST, $_REQUEST. How you retrieve the content of the elements depends on your use of the get and Post methods in the form. The form will send all the information to the web page via the URL. With that method users may be able to see the information in the URL and you don't want them to see and they may also be able to bookmark pages that change over time. The other downfall is that the Get method is limited to 2048 characters, which in general, you should only use the Get method when you are searching for records or navigating between pages. For all other circumstances you should use the Post method. The Post method sends all the information in the header of the request. That means that the data, although not encrypted, is hidden from the users. You can also theoretically send an unlimited amount of data using the Post method. However, the PHP.ini configuration file is pre-set to limit the max_post_size to 8 MB. You can change this if