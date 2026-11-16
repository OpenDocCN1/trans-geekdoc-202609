```
<?php
// Assume that we have already connected and authenticated to an FTP server

$directory = 'foo';

$created_dir = ftp_mkdir($ftp_handle, $directory)
    or die("Could not create directory '$directory'.");

echo("Directory '$created_dir' was created. We asked the FTP server
    to create a directory named '$directory'.");
?>
```

Creates a directory on the remote system.

# ftp_nlist()

```
array ftp_nlist(int ftp_link, string directory)
```

Returns a numerically indexed array of file names on success, and false on failure:

```
<?php
// Assume that we have already connected and authenticated to an FTP server

// Get a list of the files in the remote current working directory
$directory = '.';

$file_list = ftp_nlist($ftp_handle, $directory)
    or die("Could not list the files in directory '$directory'.");

echo("Directory '$directory' contains the following files:");
print_r($file_list);
?>
```

Returns a listing of the files in a remote directory.

# ftp_pasv()

```
boolean ftp_pasv(int ftp_link, int enabled)
```

Returns true on success, and false on failure: ,

```
<?php
// Assume that we have already connected and authenticated to an FTP server

$pasv_setting       = TRUE;
$pasv_setting_name = $pasv_setting ? 'enabled' : 'disabled';

if (ftp_pasv($ftp_handle, $pasv_setting)) {
    echo("PASV was successfully $pasv_setting_name.");
} else {
    echo("PASV could not be $pasv_setting_name.");
}
?>
```