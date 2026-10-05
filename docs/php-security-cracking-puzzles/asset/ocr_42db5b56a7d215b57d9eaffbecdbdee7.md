# Chapter II.9: File Transfer Protocol

Listing II.9.6 shows a script for downloading files from an FTP server. As in the file upload script in Listing II.9.5, the file download process is controlled in a while loop using the ftp_nb_continue() function considered previously.

# Listing II.9.6. Downloading a file from an FTP server

```
<?php
// Opening a connection to the FTP server
require_once("config.php");
// Initializing file download
$ret = ftp_nb_get($link, "C:\file.zip", "/path/file.zip", FTP_BINARY);
// The download loop
while ($ret == FTP_MOREDATA) {
// Displaying dots to inform the user
// that the download is in progress
echo ";";
// Continuing the download
$ret = ftp_nb_continue($link);
}
// If an error occurs during the download,
// the user is informed about it
if ($ret != FTP_FINISHED) {
    exit("<br>Error downloading the file...");
    exit();
}
?>
```

# II.9.4. Changing Access Permissions

In addition to specifying access permissions in text form as described previously, in UNIX access permissions can be specified using octal numbers. In this format, read permissions are denoted by the digit 4, write permissions by 2, and execution permissions by 1. Overall permissions for a group are specified by a sum of these digits. For example, 6 (i.e., 4+2) denotes read and write permissions, and 7 (i.e., 4 + 2 + 1) gives full access rights to a file or directory. Using this format, the octal number