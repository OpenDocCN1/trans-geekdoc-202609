form data is merged into a string. Special care is taken of form values that are arrays—this can occur with multiple selection lists. Then the form data is mailed to the webmaster; just don't forget to change the email address.

# Getting Information about File Uploads

```
<?php
if (isset($_POST['Submit']) &&
    isset($_FILES['File']) &&
    is_uploaded_file($_FILES['File']['tmp_name'])) {
printf('<p>Error: %s<br />
    Original name: %s<br />
    File size: %s<br />
    Temporary name: %s<br />
    MIME type: %s</p>',
    $_FILES['File']['error'],
    htmlspecialchars($_FILES['File']['name']),
    $_FILES['File']['size'],
    $_FILES['File']['tmp_name'],
    htmlspecialchars($_FILES['File']['type'])
);
} else {
?>
<form action="<?php echo $_SERVER['PHP_SELF']; ?>" method="post" enctype="multipart/form-data">
<input type="file" name="File" />
<input type="submit" name="Submit" value="Submit form" />
</form>
<?php
}
?>
```