+   • A list of authorized image types is defined in an array named $allowed_types, in this case "image/jpeg" and "image/png".

+   • The in_array() function is used to check whether the type of the downloaded file is one of the permitted types defined in the $allowed_types array.

+   • If this is the case, the file is moved from the temporary folder to a destination directory specified in the $destination variable using the move_uploaded_file() function. The temporary file is specified by $_FILES["file"]["tmp_name"], and the file name is kept unchanged in $file["name"].

+   • If the file type is not authorized, an error message is displayed, instructing the user to select an image in JPEG or PNG format.

This code ensures that only JPEG or PNG files are accepted and uploaded to the server, guaranteeing data security and integrity.

To test your code, follow these simple steps: run the index.php file, select an image from your device, then validate the form. If the image you've selected complies with the specified permitted types, it will be saved in the "uploads" directory you created earlier.