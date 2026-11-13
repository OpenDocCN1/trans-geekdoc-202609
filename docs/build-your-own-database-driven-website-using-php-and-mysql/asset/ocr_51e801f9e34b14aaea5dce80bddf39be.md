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
<title> Generating <?=$targetfilename?> </tutke>
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
```