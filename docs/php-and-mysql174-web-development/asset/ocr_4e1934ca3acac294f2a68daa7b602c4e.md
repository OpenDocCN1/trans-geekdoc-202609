Let's go through the main parts of the script. You begin by checking the error code returned in $$_FILES['userfile']['error']. A constant is also associated with each of the codes. The possible constants and values are as follows:

+   - UPLOAD_ERR_OK, value 0, means no error occurred.
- UPLOAD_ERR_INI_SIZE, value 1, means that the size of the uploaded file exceeds the maximum value specified in your php.ini file with the upload_max_filesize directive.
- UPLOAD_ERR_FORM_SIZE, value 2, means that the size of the uploaded file exceeds the maximum value specified in the HTML form in the MAX_FILE_SIZE element.
- UPLOAD_ERR_PARTIAL, value 3, means that the file was only partially uploaded.
- UPLOAD_ERR_NO_FILE, value 4, means that no file was uploaded.
- UPLOAD_ERR_NO_TMP_DIR, value 6, means that no temporary directory is specified in the php.ini.
- UPLOAD_ERR_CANT_WRITE, value 7, means that writing the file to disk failed.
- UPLOAD_ERR_EXTENSION, value 8, means that a PHP extension stopped the file upload process.

You also check the MIME type to ensure that only certain file types are uploaded. In this case, we want to upload image files only, and specifically PNG files. So, we check the MIME type by making sure that $_FILES['userfile']['type'] contains image/png. This is really only error checking, and not security checking. The MIME type is interpreted by the user's browser from the file extension and information within the file, and then passed to your server.

You then check if the file you are trying to open has actually been uploaded and is not a local file such as /etc/passwd. We will return to this at the end of this section.

If these checks work out, the code copies the file into the /uploads/ directory, for easy access to display these uploaded files, as we do at the end of the script by printing an HTML <img> tag containing the path to the file so that the user can see the file uploaded successfully.

The results of one (successful) run of this script are shown in Figure 17.2.