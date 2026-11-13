

Here's the code for generateindex.php, with ample comments so you can see what's going on:

```
<!-- generateindex.php -->
<?php
// Sets the files we'll be using
$srcurl      = "http://localhost/index.php";
$tempfilename = "tempindex.html";
$targetfilename = "index.html";
?>
<html>
<head>
<title> Generating <?=$targetfilename?> </title>
</head>
<body>
<p>Generating <?=$targetfilename?>...</p>
<?php
// Begin by deleting the temporary file, in case
// it was left lying around. This might spit out an
// error message if it were to fail, so we use
// @ to suppress it.
@unlink($tempfilename);
// Load the dynamic page by requesting it with a
// URL. The PHP will be processed by the Web server
// before we receive it (since we're basically
// masquerading as a web browser), so what we'll get
// is a static HTML page. The 'r' indicates that we
// only intend to read from this "file".
$dynpage = fopen($srcurl, 'r');
// Check for errors
if (!$dynpage) {
echo("<p>Unable to load $srcurl. Static page ".
"update aborted!</p>");
exit();
}
// Read the contents of the URL into a PHP variable.
// Specify that we're willing to read up to 1MB of
// data (just in case something goes wrong).
$htmldata = fread($dynpage, 1024*1024);
// Close the connection to the source "file", now
// that we're done with it.
fclose($dynpage);
// Open the temporary file (creating it in the
// process) in preparation to write to it (note
// the 'w').
$tempfile = fopen($tempfilename, 'w');
// Check for errors
if (!$tempfile) {
    echo("<p>Unable to open temporary file ".
    "($tempfilename) for writing. Static page ".
    "update aborted!</p>");
    exit();
}

// Write the data for the static page into the
// temporary file
fwrite($tempfile, $htmlData);

// Close the temporary file, now that we're done
// writing to it.
fclose($tempfile);

// If we got this far, then the temporary file
// was successfully written, and we can now copy
// it on top of the static page.
$ok = copy($tempfilename, $targetfilename);

// Finally, delete the temporary file.
unlink($tempfilename);
?>
<p>Static page successfully updated!</p>
</body>
</html>
```

The above code only looks daunting because of the large comments I've included. Remove them, and you'll see it's actually a fairly simple script.

Now, whenever generateindex.php is executed (say, when a browser requests it), a fresh copy of index.html will be generated from index.php. If we move index.php and generateindex.php into a restricted-access directory, you can make sure that only site administrators have the ability to update the front page of your site in this way. Expand this script to generate all semi-dynamic pages on your site, and add an "update semi-dynamic pages" link to your content management system!

If you'd rather have your front page updated automatically, you'll need to set up your server to run generateindex.php at regular intervals (say, every hour). Under recent versions of Windows 9x, you can use the Task Scheduler (System Agent in older versions of Windows equipped with MS Plus Pack) to automatically run php.exe (a stand-alone version of PHP included with the Windows PHP distribution) every hour. Just create a batch file called generateindex.bat that contains this line of text:

```
C:\PHP\php.exe C:\www\generateindex.php
```

Adjust the paths and filenames as necessary, and then set up Task Scheduler to run `generateindex.bat` every hour (in some versions of Windows, you'll need to set up 24 tasks to be run daily at the appropriate times). Done!

Under Linux (or other UNIX-based platforms) you can do a similar thing with `cron` -- a program installed on just about every UNIX system out there that lets you define tasks to be run at regular intervals. Ask your friendly neighborhood Linux know-it-all, check your favorite Linux Web site, or post a message on the SitePoint.com Forums (www.sitepointforums.com) if you need any help getting started with `cron`.

The task you'll set up `cron` to run will be very similar to the Windows task discussed above. The stand-alone version of PHP you'll need, however, doesn't come with the PHP Apache loadable module we compiled way back in Chapter 1. You'll need to compile it separately from the same package we used to compile the Apache module. Instructions for this are provided with the package and on the PHP Web site (www.php.net), but feel free to post in the SitePoint.com Forums (www.sitepointforums.com) if you need help!

For experienced `cron` users in a hurry, here's what the line in your crontab file should look like:

```
0 0-23 * * * php /path/to/generateindex.php > /dev/null
```

## Handling File Uploads

All of our examples of database-driven Web sites in this series so far have dealt with sites based around textual data. Jokes, articles, authors... all of these things can be fully represented with strings of text. But what if you ran, say, an online digital photo gallery where people could upload pictures taken with digital cameras? For this to work, we need to be able to let visitors to our site upload their photos and we need to be able to keep track of them.

We'll start with the basics: let's write an HTML form that allows users to upload files. HTML makes this quite easy with its `<input type="file">` tag. By default, however, only the name of the file selected by the user is sent. To have the file itself submitted with the form data, we need to add `enctype="multipart/form-data"` to the `<form>` tag:

```
<form action="fileupload.php" method="post"
 enctype="multipart/form-data">
<p>Select file to upload: <input type="file"
 name="uploadedfile" /></p>
<p><input type="submit" name="submit" value="Submit" />
</p>
</form>
```

As we can see, a PHP script (`fileupload.php`) will handle the data submitted with the form above. And, as you'd expect, a PHP variable named $uploadedfile (from the NAME attribute of the <input> tag) will be automatically created. However, instead of storing the contents of the uploaded file, $uploadedfile contains the name of the file stored on the Web server's hard disk, in the directory set by the TEMP environment variable (e.g. C:\Windows\TEMP\ on most Windows 9x systems), (unless it has been specified explicitly, using the upload_tmp_dir setting in your php.ini file). This file is only kept for as long as the PHP script responsible for handling the form submission is in operation, so if you want to use it for anything later on (e.g. storing it for display on the site) you need to make a copy of it somewhere else - to do this, use the copy function described in the previous section.

In addition to $uploadedfile, three other variables are automatically created as well. $uploadedfile_name contains the name of the file before it was submitted (submitted files are stored as phpx, where x is a number, in the TEMP directory), $uploadedfile_size contains the size (in bytes) of the file, and $uploadedfile_type contains the MIME type (e.g. text/plain, image/gif, etc.) of the file. Remember, "uploadedfile" is just the name attribute of the <input> tag that submitted the file, so the actual names of these variables will depend on that attribute.

You can use these variables to decide whether to accept or reject an uploaded file. For example, in our photo gallery we would only really be interested in JPEG and possibly GIF files. These files have MIME types of image/pjpeg and image/gif respectively, so the code that validates uploaded files might look something like this:

```
if ($uploadedfile_type == "image/pjpeg" || $uploadedfile_type == "image/gif") {
// Handle the file...
} else {
echo("<p>Please submit a JPEG or GIF image ".
"file.</p>\n");
}
```

While you can use a similar technique to disallow files that are too large (by checking the $uploadedfile_size variable), this is not usually a good idea. Before this value can be checked, the file is already uploaded and saved in the TEMP directory. If you try to reject files due to limited disk space and/or bandwidth, the fact that large files can still be uploaded (even though they get deleted almost immediately) may be a problem for you.

Instead, you can tell PHP in advance the maximum file size you wish to accept. There are two ways to do this. The first is to adjust the upload_max_filesize setting in your php.ini file. The default value is 2MB, so if you want to accept uploads larger than that you'll immediately need to change that value.

