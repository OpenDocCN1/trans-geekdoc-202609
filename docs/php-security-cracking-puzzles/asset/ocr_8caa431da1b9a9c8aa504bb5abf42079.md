# II.3.4. Download Counter

All download counters are based on the principle that users are given a link not to the file itself but only a link to the script that registers the download and sends the file to the user.

The script for solving the posed problem, counting the number of times a file is downloaded, constructed so that the link to the file to download is implemented as a link to the current page with the file name passed as a parameter: for example, index.php?down = archive.zip. The script checks whether the down parameter was passed and, if it was, registers the download in the filecount.txt file. Every time the page is loaded, the counter value for each archive is extracted from this file and displayed in the browser window. The requested file is made available for downloading by sending the user an HTTP header named that contains a link to the archive to download. The actual file download script may look like the one shown in Listing II.3.6.

> NOTE It is more convenient to store statistical information for industrial and large systems in a file.

# Listing II.3.6. A file download counter

```
<?php
// Registering the file names in an array
$file_name = array('archive1.zip', 'archive2.zip', 'archive3.zip');

// The name of the file that stores statistics
$countname = "filecount.txt";
// If the file exists, reading the
// current statistics into the array.
if (file_exists($countname)) {
    $fd = fopen($countname, "r");
    $content = fread($fd, filesize($countname));
    fclose($fd);
    // Unpacking the array
    $count = unserialize($content);
}
```