```
<?php
    }
?>
```

*Sending Form Data Via Email (form-mail.php; excerpt)*

# Getting Information
About File Uploads

```
printf('<p>Error: %s<br />
    Original name: %s<br />
    File size: %s<br />
    Temporary name: %s<br />
    MIME type: %s</p>',
$_FILES['File']['error'],
$_FILES['File']['name'],
$_FILES['File']['size'],
$_FILES['File']['tmp_name'],
$_FILES['File']['type'])
```

When uploading files to the web server using <input type="file" />, the HTML form has to fulfill two requirements:

+   - The enctype attribute has to be set to "multipart/form-data"
+   - The method attribute has to be set to "post"

Without these settings, the file upload does not work. It also does not work if the following information is missing from php.ini:

```
file_uploads = On
```

But if it does, retrieving information about the file is quite easy: In the (superglobal) array $_FILES, you can find the file upload form field under its name. Then, the following subkeys provide further information about the uploaded file: