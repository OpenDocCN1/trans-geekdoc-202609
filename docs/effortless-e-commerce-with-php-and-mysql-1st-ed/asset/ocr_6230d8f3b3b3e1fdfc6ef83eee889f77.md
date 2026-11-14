If no image-related error exists, a new name for the image is created, starting with the application of `SHA1()` to the combination of the file's current name and a unique ID. This will generate a 40-character-long random name. Then the existing extension is appended. Finally, the file is moved to its final resting place, within the **Web root directory**`/products` folder.

The image's new name and its original file name are both stored in the session for use later.

+   11. If a file upload error occurred, determine what it was:

```
} elseif (isset($_SESSION['image'])) {
switch ($_FILES['image']['error']) {
case 1:
case 2:
$add_product_errors['image'] = 'The uploaded file was too
large.';
break;
case 3:
$add_product_errors['image'] = 'The file was only partially
uploaded.';
break;
case 6:
case 7:
case 8:
$add_product_errors['image'] = 'The file could not be
uploaded due to a system error.';
break;
case 4:
default:
$add_product_errors['image'] = 'No file was uploaded.';
break;
} // End of SWITCH.
} // End of $_FILES IF-ELSEIF-ELSE.
```

Yet again, this is all similar to that in the PDF upload script. First, the `switch` will be checked only if there's no file already represented in the session. This is necessary because it's possible that the administrator uploaded an image correctly the first time, but had another error in the form. In that case, when the administrator resubmits the form, the existing image upload should be used.