password file. To prevent that from happening, the third part of the conditional checks that the first character isn't a period.

If all three conditions are true, then an absolute path to the file is defined. Next, the file is tested to confirm that it exists and is a file (as opposed to a directory).

+   5. Get the PDF information from the database:

```
```php
$q = 'SELECT title, description, file_name FROM pdfs WHERE
  tmp_name="". mysqli_real_escape_string($dbc, $_GET['id']) . '';
$r = mysqli_query($dbc, $q);
if (mysqli_num_rows($r) == 1) { // Ok!
    $row = mysqli_fetch_array($r, MYSQLI_ASSOC);
    $valid = true;
}
```
```

The query fetches the PDF's title, description, and original file name. The first two pieces of information will be used if the current viewer doesn't have permission to see the PDF itself. If one row was returned, the data is retrieved and the $valid variable is changed to true.

+   6. Only display the PDF to a user whose account is active:

```
```php
if (isset($_SESSION['user_not_expired'])) {
    header("Content-type:application/pdf");
    header("Content-Disposition:inline;filename="" . $row['file_name'] . "");
   $fs = filesize($file);
    header ("Content-Length:$fs\n");
    readfile($file);
    exit();
}
```
```

If the user's account is active, the PDF should be loaded in the browser. To do that in PHP, start by sending a header indicating the content type. Then indicate the content's disposition—inline, meaning show the file in the browser—and what its filename is. For the file's name, the original file name is provided. Next, the size of the file is indicated, using the actual file's size, not the database-stored approximation. Finally, the readfile() function reads in all the binary data and sends it to the browser. The script is then terminated.

note Different browsers will use the filename disposition differently.

+   7. For inactive users, show the content's description:

```
```php
} else { // Inactive account!
    $page_title = $row['title'];
    include('./includes/header.html');
    echo "<h3>$page_title</h3>";
```
```