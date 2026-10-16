When you are uploading files to the Web server using `<input type="file" />`, the HTML form has to fulfill two requirements:

+   - The enctype attribute has to be set to "multipart/form-data".
+   - The method attribute has to be set to "post".

Without these settings, the file upload does not work. It also does not work if the following information is missing from php.ini:

```
file_uploads = On
```

But if it does, retrieving information about the file is quite easy: In the (superglobal) array `$_FILES`, you can find the file upload form field under its name. Then, the following subkeys provide further information about the uploaded file:

+   - `$_FILES["File"]["error"]`—Error code (0 in case of success)
+   - `$_FILES["File"]["name"]`—Original filename
+   - `$_FILES["File"]["size"]`—Size of the file
+   - `$_FILES["File"]["tmp_name"]`—Temporary filename where PHP saved the file
+   - `$_FILES["File"]["type"]`—The file's MIME type as sent by the client, not reliable

The preceding code outputs the available file information (see Figure 5.4). The call to `is_uploaded_file()` adds an additional layer of security by first checking whether the file has really been uploaded by the client.