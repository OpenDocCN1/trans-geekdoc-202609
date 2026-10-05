```
php function: Users can define their own functions with any valid PHP code.
http://us.php.net/manual/en/functions.user-defined.php
```

```
php strtolower: Make the supplied string lower case.
http://us.php.net/manual/en/function/strtolower.php
```

```
php explode: Split a string into an array by a delimiter.
http://us.php.net/manual/en/function/explode.php
```

```
php end: Obtain the last element of an array.
http://us.php.net/manual/en/function.end.php
```

```
php return: Ends the execution of the current function, returning the argument as the value of the function.
http://us.php.net/manual/en/function.return.php
```

Now we have a function that will obtain the extension we can define a variable to create the final destination path and name that will be inserted into the URL field in the record. Combine the previously defined $image_directory path, the id value from the URL, a dot ". for the extension, and the extension from the uploaded file using the function we created above for findext.

```
$destination_file = $image_directory . $_REQUEST['id'] . ".
findext($_FILES['new_image'] . 'name');
```

Now we have all the pieces we need to move the temporary file, rename the file, and update the database. Using the PHP move_uploaded_file method and insert the $temporary_file and $destination_file variable we defined above If the $move variable is successful we can update the database and set the URL field. Otherwise, we should alert the user that there was an error.

```
$move = move_uploaded_file($temporary_file, $destination_file);
if ($move) {
  $url = $destination_file;
  $insert = $fm->newEditCommand('Demo php', $_REQUEST['id']);
  $insert->addField('URL', $url);
  $insert->execute();
} else {
  die('There was an error moving the file');
}
```