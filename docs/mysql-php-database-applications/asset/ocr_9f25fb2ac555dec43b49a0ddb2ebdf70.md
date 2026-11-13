# Uploading files

This is the first application that enables users to upload files; specifically, the administrators of the catalog need to be able to upload images of their products. Uploading files is easy enough in PHP, but before you understand how the upload works you need to know how PHP handles uploaded files.

In your HTML page you have a form like the following:

```
<form action="admin_product.php" method="post"
enctype="multipart/form-data" >
<input type=file name="imagefile">
</form>
```

![](bbox=[0.093, 0.342, 0.182, 0.409])

When you allow file uploads, you open yourself up to denial-of-service (DoS) attacks. If you're not careful, someone could send many multi-megabyte files to your system simultaneously, which could bring your machine to a crashing halt. There are two things you can do about this. The first is to put a hidden form field before your `<INPUT TYPE="file">` tag. The hidden field should look like this:

```
<INPUT TYPE="hidden" name="MAX_FILE_SIZE" value="1000">
```

where value indicates the maximum size allowed, in bytes. This is a reasonable first step and can be of help in stopping someone who didn't know you have a size limit. However, this measure will not stop anyone with stronger malicious intent. All that person has to do is look at the source code of your page and make the needed changes.

The other security measure has to do with altering the php.ini file, which contains the upload_max_filesize item. If you have access to your php.ini, you can set the value of this item to a number that you think is reasonable. (By default php.ini will allow 2MB uploads.) By making the change in the php.ini file you prevent the attacker from altering it.

When a file is specified and this form is submitted, PHP automatically creates a few variables. They are as follows:

+   - $_FILES[yourfieldname][tmp_name] – The name of the file as stored in the temporary directory on the server
+   - $_FILES[yourfieldname][name] – The name of the file as it was on the user's machine