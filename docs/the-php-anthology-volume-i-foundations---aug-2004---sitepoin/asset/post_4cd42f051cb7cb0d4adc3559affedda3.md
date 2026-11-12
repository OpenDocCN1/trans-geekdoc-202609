
- `$_FILES['fieldname']['type']`: the MIME type[8] of the file
- `$_FILES['fieldname']['tmp_name']`: the temporary name and location of the file, which PHP created when the file was uploaded
- `$_FILES['fieldname']['error']`: 0 if all went well (see the PHP Manual[9] for error codes)
- `$_FILES['fieldname']['size']`: the size of the file in bytes

Here’s an example of the array of information for a file upload, as produced by PHP’s print_r function:

```
Array
(
    [name] => php_logo.gif
    [type] => image/gif
    [tmp_name] => /tmp/php1B1B.tmp
    [error] => 0
    [size] => 3872
)
```

Armed with this knowledge, let’s look at a simple script that accepts a GIF file upload and copies it to the files subdirectory of the current directory:

```
<?php
// Include Magic Quotes filter
require_once 'MagicQuotes/strip_quotes.php';

// If the form has been submitted...
if (isset($_POST['submit'])) {

    // If the file is a GIF image...
    if ($_FILES['image']['type'] == 'image/gif') {

        // Copy the file from temporary storage to final destination
        copy($_FILES['image']['tmp_name'], "./files/" . $_FILES['image']['name'])
or die("Could not copy");

// Display some information about the file
echo "File Upload Complete<br />\n";
echo "Name: " . $_FILES['image']['name'] . "<br />\n";
echo "Size: " . $_FILES['image']['size'] . "<br />\n";
echo "Type: " . $_FILES['image']['type'] . "<br />\n";
echo "<img src=\"\\files/" . $_FILES['image']['name'] . "\\" />";
}

// ... otherwise display the form
} else {
?>
<form method="POST"
    action="?<?php echo $_SERVER['PHP_SELF']; ?>"
    enctype="multipart/form-data">
Upload a GIF image: <input type="file" name="image" />
<input type="submit" name="submit" value="Submit" />
</form>
<?php
}
?>
```

Hey presto, instant file upload! See the result for yourself in Figure 9.5.

### Figure 9.5. PHP Logo Uploaded Successfully

![](img/5b6cdf7cf4cf53e30b19e047895dc464_303_0.png)

### Be Sure it's an Upload

Perhaps you have a more complicated script in which you passed the temporary file name to another PHP variable, performed various tricks, and then forgot you’d left a hole in your code—a hole that allowed a user to modify the contents of the PHP variable with a different file name! It’s worth using the PHP function `is_uploaded_file` to double-check that the uploaded file really is the right one before you do anything with it, such as copying it to a public directory where others can see it. In the past, people have tricked PHP scripts into copying a file containing a password, rather than the image that was actually uploaded, to a public directory. Be safe, rather than sorry.

### Using QuickForm for File Uploads

Let’s put our friend QuickForm back into action, and learn to store the files in MySQL.

The construction of the form is very similar to the example in “How do I handle HTML forms in PHP?”:

```
<?php
// Include the MySQL class
require_once 'Database/MySQL.php';

// Include the QuickForm class
require_once 'HTML/QuickForm.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

// A function to apply mysql_real_escape_string
function escapeValue($value)
{
    return mysql_real_escape_string($value);
}

// Instantiate QuickForm
$form = new HTML_QuickForm('imageUpload', 'POST');

// The file upload field
$form->addElement('file', 'image', 'Select Image:');
$form->addRule('image', 'The maximum file size is 56KB',
    'maxfilesize', 57344);
$form->addRule('image', 'The file must be an image', 'mimetype',
    array('image/gif', 'image/jpeg', 'image/pjpeg',
    'image/png'));
$form->addRule('image', 'No file selected.', 'uploadedfile', NULL,
    'client');

// The submit button
$form->addElement('submit', 'submit', 'Upload');
```

Note that we've applied the mimetype rule, which allows us to pass an array of allowed MIME types that users can upload³.

³Note that JPEG files can be reported as image/jpeg or image/pjpeg, depending on the browser; thus, both are included in the list of acceptable types.

Although calling the applyFilter method escapes all the text values submitted to the form, it does not escape the values associated with the file upload. We must, therefore, apply the escapeValue function to each of these values (including the binary file data) as we retrieve them from the $form object:

```
if ($form->validate())
{
    // Apply the escape filter to all fields
    $form->applyFilter('__ALL__', 'escapeValue');

    // Instantiate the MySQL class
    $db = &new MySQL($host, $dbUser, $dbPass, $dbName);

    // Fetch the details of the file
    $name = escapeValue($form->_submitFiles['image']['name']);
    $size = escapeValue($form->_submitFiles['image']['size']);
    $type = escapeValue($form->_submitFiles['image']['type']);

    // Fetch file data
    $contents = file_get_contents(
        $form->_submitFiles['image']['tmp_name']);

    // Escape binary data
    $contents = escapeValue($contents);

    $sql = "INSERT INTO image SET
        name='$name',
        size='$size',
        type='$type',
        contents='$contents'";

    // Perform the query
    $result = $db->query($sql);

    // If all went well, say thanks
    if (!$result->isError()) {
        echo 'File Uploaded Successfully';
    } else {
        $form->display();
    }
} ?>
```

Note that when fetching the details of the file, we accessed one of QuickForm's properties (_submitFiles) directly, which is technically bad practice when using objects (if the variable name changes in a future version of QuickForm, this will break my script). Unfortunately, QuickForm doesn't currently offer a mechanism to access this information, so we're forced to resort to this work around.

Now that we've uploaded some files and stored them in the database, what about displaying them?

```
File: 10.php
<?php
// Include the MySQL class
require_once 'Database/MySQL.php';

$Host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

$db =& new MySQL($Host, $dbUser, $dbPass, $dbName);

// Define SQL statement to fetch image information
// but NOT CONTENTS!!!
$sql = "SELECT image_id, name, size, type FROM image
    ORDER BY name";

// Fetch the result object
$result = $db->query($sql);

// A loop for each row of the result set
while ($row = $result->fetch()) {
    echo '<img src="11.php?id=' . $row['image_id'] . '" /> <br />';
    echo $row['name'] . ': ' . $row['size'] . ' : ' .
        $row['type'] . '<br />';
}
?>
```

The above code lists the images in the database. It then generates some HTML that uses the img tag to specify another PHP script, and it's this that actually displays the image. Note that we've been careful not to select the contents of the image—just the information we need for each one. Otherwise, this would eat up PHP's memory very quickly.

Here's the HTML it generates:

```
<img src="11.php?id=2" /><br />
mysql.png : 1107 : image/png<br />
<img src="11.php?id=1" /><br />
php_logo.gif : 3872 : image/gif<br />
<img src="11.php?id=3" /><br />
sitepoint_arrow.gif : 508 : image/gif<br />
```

Now, look at 11.php, which shows the code that's used to generate the image:

```
<?php
// Include the MySQL class
require_once 'Database/MySQL.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

// Instantiate the MySQL class
$db =& new MySQL($host, $dbUser, $dbPass, $dbName);

// If there's not image, die
if (!isset($_GET['id'])) {
	die('No image selected');
}

// Escape the string, for good practice
$_GET['id'] = mysql_real_escape_string($_GET['id']);

// An SQL statement to get the contents and MIME type of the image
$sql = "SELECT * FROM image WHERE image_id='" . $_GET['id'] . "'";

// Fetch the data
$result = $db->query($sql);
$row = $result->fetch();

// Use a header to tell the browser what MIME type the image is
header('content-disposition: inline; filename=' . $row['name']);
header('content-type: ' . $row['type']);
header('content-length: ' . $row['size']);

// Display the contents
echo $row['contents'];
?>
```
