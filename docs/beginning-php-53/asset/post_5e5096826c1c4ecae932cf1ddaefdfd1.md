
PHP allows you to limit the size of uploaded files in a few ways. First, if you have access to your php.ini file, you can add or edit a directive called upload_max_filesize in the file:

```
; Maximum allowed size for uploaded files.
upload_max_filesize = 32M
```

Then, if a user tries to upload a file larger than this value (32 megabytes in this example), the file upload is cancelled and the corresponding error array element is set to UPLOAD_ERR_INI_SIZE.

You can find out more on editing your php.ini file in Appendix B.

If you don't have access to your server's php.ini file, you can add a hidden form field called MAX_FILE_SIZE that specifies the maximum allowed size (in bytes) of an uploaded file. This should be placed before the file upload field:

```
<input type="hidden" name="MAX_FILE_SIZE" value="10000" />
<input type="file" name="fileSelectField" id="fileSelectField" value="" />
```

If the uploaded file is larger than this figure, the upload is cancelled and the corresponding error array element is set to UPLOAD_ERR_FORM_SIZE. In theory, a browser can also look at the MAX_FILE_SIZE field in the form and prevent the user from uploading a file bigger than that value in the first place. In practice, though, hardly any browsers support this technique.

It's also relatively easy for an attacker to modify your Web form and alter the value of the MAX_FILE_SIZE hidden field (or even remove the field altogether). For this reason, it's best to use upload_max_filesize to limit your file uploads, if possible.

Of course, you can also check the size of an uploaded file manually and reject it if it's too large:

```
if ( $_FILES["photo"]["size"] > 10000 ) die( "File too big!" );
```

## Storing and Using an Uploaded File

Once a file has been successfully uploaded, it is automatically stored in a temporary folder on the server. To use the file, or store it on a more permanent basis, you need to move it out of the temporary folder. You do this using PHP's move_uploaded_file() function, which takes two arguments: the path of the file to move, and the path to move it to. You can determine the existing path of the file using the tmp_name array element of the nested array inside the $_FILES array. move_uploaded_file() returns true if the file was moved successfully, or false if there was an error (such as the path to the file being incorrect). Here's an example:

```
if ( move_uploaded_file( $_FILES["photo"]["tmp_name"], "/home/matt/photos/photo.jpg" ) ) {
 echo "Your file was successfully uploaded.";
} else {
 echo "There was a problem uploading your file - please try again.";
}
```

## Try It Out Create a File Upload Script

You now have all the knowledge required to create file upload forms and PHP scripts that can handle them. In this example, you create a script that displays a form allowing the user to upload a JPEG photo, which is then displayed to them in the page.

First, save the following script as photo_upload.php in your document root folder:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Uploading a Photo</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>

<?php
if ( isset( $_POST["sendPhoto"] ) ) {
processForm();
} else {
displayForm();
}

function processForm() {
if ( isset( $_FILES["photo"] ) and $_FILES["photo"]["error"] == UPLOAD_ERR_OK ) {
if ( $_FILES["photo"]["type"] != "image/jpeg" ) {
echo "<p>JPEG photos only, thanks!</p>";
} elseif ( !move_uploaded_file( $_FILES["photo"]["tmp_name"], "photos/" . basename( $_FILES["photo"]["name"] ) ) {
echo "<p>Sorry, there was a problem uploading that photo.</p>" .
$_FILES["photo"]["error"] ;
} else {
displayThanks();
}
} else {
switch( $_FILES["photo"]["error"] ) {
case UPLOAD_ERR_INI_SIZE:
$message = "The photo is larger than the server allows.";
break;
case UPLOAD_ERR_FORM_SIZE:
$message = "The photo is larger than the script allows.";
break;
case UPLOAD_ERR_NO_FILE:
$message = "No file was uploaded. Make sure you choose a file to upload.";
break;
default:
$message = "Please contact your server administrator for help.";
}
echo "<p>Sorry, there was a problem uploading that photo. $message</p>";
}
}
function displayForm() {
?>
	<h1>Uploading a Photo</h1>

	<p>Please enter your name and choose a photo to upload, then click Send Photo.</p>

	<form action="photo_upload.php" method="post" enctype="multipart/form-data">
		<div style="width: 30em;">
			<input type="hidden" name="MAX_FILE_SIZE" value="50000" />

			<label for="visitorName">Your name</label>
			<input type="text" name="visitorName" id="visitorName" value="" />

			<label for="photo">Your photo</label>
			<input type="file" name="photo" id="photo" value="" />

			<div style="clear: both;">
				<input type="submit" name="sendPhoto" value="Send Photo" />
			</div>
		</div>
	</form>
<?php
}

function displayThanks() {
?>
	<h1>Thank You</h1>
	<p>Thanks for uploading your photo<?php if ( $_POST["visitorName"] ) echo ", " . $_POST["visitorName"] ?>!</p>
	<p>Here's your photo:</p>
	<p><img src="photos/<?php echo $_FILES["photo"]["name"] ?"/>" alt="Photo" /></p>
<?php
}
?>
</body>
</html>
```

Next, create a photos folder in the same folder on your Web server (the document root). This folder is to store the uploaded photos. You’ll need to give your Web server user the ability to create files in this folder. On Linux or Mac OS X you can do this in a Terminal window as follows:

```
cd /path/to/document/root
chmod 777 photos
```

## Part III: Using PHP in Practice

On Windows you can use Windows Explorer to set permissions on the `photos` folder.

Now try running the script in your browser. You should see the form shown in Figure 9-10. Enter your name and choose a JPEG photo to upload, then click Send Photo. You should see a thank-you message appear along with your uploaded photo, as in Figure 9-11.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_299_0.png)

### Figure 9-10

![](img/1ddec54918a4802eb9b4febec3d4e7f6_299_1.png)

### Figure 9-11

## How It Works

The script first checks to see if the form has been submitted by looking for the existence of the sendPhoto submit button field. If the form was submitted, processForm() is called to handle the form; otherwise the form is displayed with displayForm():

```
if ( isset( $_POST["sendPhoto"] ) ) {
	processForm();
} else {
	displayForm();
}
```

processForm() handles the uploaded file (if any). First it checks to make sure a file was uploaded, and that it uploaded without error:

```
if ( isset( $_FILES["photo"] ) and $_FILES["photo"]["error"] == UPLOAD_ERR_OK ) {
```

If the uploaded file is not a JPEG photo, the function refuses it:

```
if ( $_FILES["photo"]["type"] != "image/jpeg" ) {
	echo "<p>JPEG photos only, thanks!</p>";
}
```

The function then attempts to move the uploaded file from the temporary folder to the photos folder, displaying an error message if there was a problem. If all goes well, the thank-you page is displayed:

```
} elseif ( !move_uploaded_file( $_FILES["photo"]["tmp_name"], "photos/" . basename( $_FILES["photo"]["name"] ) ) ) {
	echo "<p>Sorry, there was a problem uploading that photo.</p>";
} else {
	displayThanks();
}
```

Note the use of the PHP basename() function. This takes a file path and extracts just the filename portion of the path. Some browsers send the full path of the file when it's uploaded — not just the filename — so the script uses basename() to make sure that only the filename portion is used for the file in the photos folder. Furthermore, this prevents attackers from inserting malicious characters (for example, "../") into the filename.

The function also displays an error message if no photo was uploaded, or if PHP reported an error in the $_FILES array:

```
} else {
	switch( $_FILES["photo"]["error"] ) {
	case UPLOAD_ERR_INI_SIZE:
		$message = "The photo is larger than the server allows.";
		break;
	case UPLOAD_ERR_FORM_SIZE:
		$message = "The photo is larger than the script allows.";
		break;
```
