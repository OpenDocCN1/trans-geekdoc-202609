# # Safely handling file uploads

For example, assume there is a basic PHP file that accepts file uploads and stores the uploaded file information in a database.

The first question to ask is what parts of this simple application are potential security concerns?

+   - The form itself?
+   - The database component?
+   - The file being uploaded?

# ## Checking for valid file extensions

The uploaded file would be the least obvious point of a security breach, but look at some sample code that explains how it can very easily become an issue. A very common, but misleading attempt to secure the file uploading process is to check for a valid extension, such as:

```
<?php
$file = $_FILES[0];

if(strpos($file['name'], '.jpg') !== false)
{
    if(!move_uploaded_file($file['tmp_name'], 'storage/'))
    {
        print "File uploaded";
    }
}

?>
```

As you can see, the code is set up to look for the .jpg file extension. The strpos function is used to return the index or placement of the checked value, which in this example is .jpg. At first glance this seems pretty secure and should stop malicious uploading, but it doesn't. This code doesn't care where the file extension is, so you could have imagename.jpg.php as the filename and it will pass. Even worse, if this is for a publicly accessible photo gallery, that file can execute PHP freely because it is already on the server. The ability to execute arbitrary code becomes a great concern when the malicious user is able to place code directly on an unsuspecting server.

Imagine an image being uploaded that is actually a PHP file with code such as the following:

```
<?php
error_reporting(E_ALL);

phpinfo();

mysql_connect('localhost', 'anyuser', 'anypass');
?>
```