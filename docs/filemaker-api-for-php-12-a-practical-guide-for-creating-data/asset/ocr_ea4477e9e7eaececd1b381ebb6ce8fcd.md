If the file type matches what we're allowing for an uploaded file there's nothing to do. Otherwise you should stopnthe script and alert the user that they are trying to upload an unapproved file.

```
{
  # true - do nothing
} else {
  $type = $_FILES['new_image']['type'];
  die ('Only gif, jpg, jpeg, and png files are allowed to be uploaded: ' . $type);
}
```

Next, we will validate the file size by checking to see if it is more than 20 KB. I normally recommend limiting the file size so we can prevent numerous errors. The $_FILES superglobal measures file size in Bytes, which is approximately 1 MB = 1,000 KB. If you want to be 1 KB = 1024 Bytes.

```
if($_FILES['new_image']['size'] > 20000) {
  $size = round($_FILES['new_image']['size']/20480,1);
  die ('The file cannot be larger than 20 KB: ' . $size . ' KB');
}
```

Before the file is uploaded we can do one last check to see if there were any errors during the upload. If there was an error we'll stop the script and alert the user.

```
if($_FILES['new_image']['error'] > 0 {
  $error = $_FILES['file']['error'];
  die ('There is an error with your file: ' . $error);
}
```

Now we can set the variables for the image directory and get the name of the temporary file on the server. The image directory is where we want the upload folder, which is relative to the web page. The $_FILES superglobal will retrieve the file from the temporary folder on the server. This is the only way to get the name of the file because PHP will rename the temporary file to a unique, random string such as php4H6d3M. Once the script ends the temporary file will be deleted from the server.

```
$image_directory = 'Images';
$temporary_file = $_FILES['new_image']['tmp_name'];
```

Next

```
function findext($filename) {
  $filename = strtolower($filename);
  $ext = explode(".", $filename);
  $ext = end($ext);
  return $ext;
}
```