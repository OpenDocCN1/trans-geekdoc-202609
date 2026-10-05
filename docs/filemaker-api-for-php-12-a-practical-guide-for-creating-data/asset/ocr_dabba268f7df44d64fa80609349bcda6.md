# Upload.php

All the hard work of uploading, renaming, and validating the file is done in this file. It includes a lot of built in PHP features to make your life very easy. Uploading files is also available with ASP. However, I've yet to find a JSP version that works with FileMaker Server.

Always start by including the connection to the database.

```
<?php
include("../Conn/dbaccess.php");
?>
```

Start making sure the Record ID was passed in the URL as the id value. It is critical that we have this value to rename the file and match it to the database record.

```
if (empty($_REQUEST['id']))
{\ die('The record id is missing.');
}
```

The upload process is done with a form at the end of the code. We need to check to see that the Post method is used and that the user clicked the Upload button.

```
if (isset($_POST['upload']) && $_POST['upload'] == 'Upload')
```

Next, we can validate the file type that the user is trying to upload using the $_FILES superglobal. In this example we are limiting the upload to MIME types for gif, jpeg, jpg and png images. It's usually a good idea to prevent any other known file types to prevent viruses from being uploaded.

![](bbox=[0.068, 0.513, 0.175, 0.606])

ppjg is a "progressive" jpg file. Processing jpeg divides the file into a series of scans. The first scan shows the image at the equivalent of a very low quality setting, which takes very little space. Following scans gradually improve the quality. Each scan adds to the data already provided, so that the total storage requirement is roughly the same as for a baseline JPEG image of the same quality as scan.

$FILES: Superglobal allows you to upload files from a client computer to the server, capturing important information about the file.

$FILES["file']['name"] - the name of the uploaded file

$FILES["file']['type'] - the type of the uploaded file

$FILES["file']['size'] - the size in bytes of the uploaded file

$FILES["file']['tmp_name'] - the name of the temporary copy of the file stored on the server

$FILES["file']['error"] - the error code resulting from the file upload

```
if(
($_FILES["new_image"][	ype"] == "image/gif"
  ($_FILES["new_image"][	ype"] == "image/jpg"
  ($_FILES["new_image"][	ype"] == "image/jpeg"
  ($_FILES["new_image"][	ype"] == "image/pjpg"
  ($_FILES["new_image"][	ype"] == "image/png"))
```

144