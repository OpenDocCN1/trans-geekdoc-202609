# II.4.13. Downloading Data from a Database Dump

As with MP3 files, if the echo $file['content'] statement is followed by any output to the browser window, including spaces or line feeds after the ?>?> tag, the image file will be corrupted.

To execute multiple SQL queries from the database dump, the contents of the catalog.sql file are read and broken into individual queries using the #;\s]*\r\n#is regular expression (Listing II.4.39). In a properly performed MySQL database dump, each query is terminated with a semicolon.

+   Listing II.4.39. Downloading data from a database dump

```
<php
// Connecting to the database
include "config.php";
// The name of the file with the SQL instructions
$filename = "catalog.sql";
// Opening the instruction file
// and reading it into a buffer
$fp = fopen($filename, "r");
$contents = fread($fp, filesize($filename));
fclose($fp);
// Breaking the file's contents
// at the semicolon boundaries
$quer = preg_split("#;\\s]*\r\n#is", $contents);
// Executing the SQL queries
foreach($quer as $query) {
    if(!$mysql_query($query)) exit(mysql_error());
}
?>
```