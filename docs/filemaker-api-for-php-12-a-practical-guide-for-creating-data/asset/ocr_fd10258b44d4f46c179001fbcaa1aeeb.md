Use the foreach looping method to create the HTML for all the records in the table. To display the image from the container field you will pass two pieces of information to the ContainerBridge.php file. The source attribute for the image will be the name of the file: ContainerBridge.php followed by the name=value pair of path=?and the value for the contents of the container field in encoded format. Earlier in the book we described how the workings of the ContainerBridge.php file work to do all the heavy lifting. To display the contents of the field you only need to pass this information to the header. should serve as a good example why it is important to separate your code into logical pieces so they can be reused by more than one web page.

```
foreach ($records as $record) {
echo '<tr>';
echo '<td>' . $record->getField('FirstName') . '</td>';
echo '<td>' . $record->getField('LastName') . '</td>';
echo '<td>' . <img src="ContainerBridge.php?path=' . urlencode($record->getField('Image')) . ' /></td>';
echo '</tr>';
}
```

FileMaker API Syntax: <img src="ContainerBridge.php?Path="/>

src = Name of the php file that will convert the image — ContainerBridge.php path = urlencode the contents of the container field using the getField method.

<img src="ContainerBridge.php?path=' . urlencode($record->getField('Image')) . ' />

urlencode: URL encodes the supplied string or variable.

http://us.php.net/manual/en/function.urlencode.php

Close the PHP code to create the table.

```
echo '</tr>';
?
```

| First Name | Last Name | Container |
|---|---|---|
| Todd | Duel | [image] |
| Tim | Wamer | [image] |

Figure 7-29: DisplayContainerField.php page.