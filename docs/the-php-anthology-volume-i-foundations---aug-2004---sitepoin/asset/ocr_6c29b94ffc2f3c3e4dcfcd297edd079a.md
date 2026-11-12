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

Now things get interesting. First, we fetch the details of the file and load its contents into a PHP variable using PHP's file_get_contents function.

³Note that JPEG files can be reported as image/jpeg or image/pjpeg, depending on the browser; thus, both are included in the list of acceptable types.