0755 means that the directory owner has full rights (rwx) and all other users view files in the directory and view the contents of the directory (r-x).

In PHP, octal numbers are prefixed with a zero.

Access permissions for files and directories are set using the ftp_chmod() function, which has the following general syntax:

```
string ftp_chmod(resource link, int mode, string directory)
```

Most like other FTP functions, the function accepts the link returned by the ftp_connect() function as the first parameter. The second parameter, mode, is an octal number specifying permissions for the directory. The last parameter, directory, names the directory whose access permissions are being changed. The function returns the newly-assigned permissions if there is success and otherwise returns false. Listing II.9.7 shows a script for setting file or directory access permissions.

# Listing II.9.7. Setting access permissions for files and directories

```
<?php
// Opening a connection to the FTP server
require_once("config.php");
// Setting the directory's access permissions
ftp_chmod($link, 0755, "logs");
// Changing the file's access permissions
ftp_chmod($link, 0644, "/path/file.zip");
?>
```