PHP script explained:

+   - $target_dir = "uploads/" - specifies the directory where the file is going to be placed
- $targetFile specifies the path of the file to be uploaded
- $uploadOk=1 is not used yet (will be used later)
- $imageFileType holds the file extension of the file (in lower case)
- Next, check if the image file is an actual image or a fake image

Note: You will need to create a new directory called “uploads” in the directory where “upload.php” resides. The uploaded files will be saved there.

# Check if File Already Exists

We can now add some restrictions.
First, we will check if the file already exists in the “uploads” folder. If it does, an error message is displayed, and $uploadOk is set to 0:

```
// Check if file already exists
if (file_exists($target_file)) {
    echo "Sorry, file already exists.";
    $uploadOk = 0;
}
```

# Limit File Size

The file input in your HTML form above is named “fileToUpload”.
Now, we want to check the size of the file. If the file is larger than 500KB, an error message is displayed, and $uploadOk is set to 0:
// Check file size

```
if ($_FILES["fileToUpload"]["size"] > 500000) {
    echo "Sorry, your file is too large.";
    $uploadOk = 0;
}
```