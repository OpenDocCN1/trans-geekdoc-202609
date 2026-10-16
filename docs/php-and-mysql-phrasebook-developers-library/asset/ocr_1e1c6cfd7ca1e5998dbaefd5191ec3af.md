method read() iterates through the list of entries. The preceding code does exactly this and prints out the contents of the current directory.

Note that the two directory entries . (current directory) and .. (parent directory, if you are not in the root directory) are printed out.

# Using PHP Streams

```
<?php
$filename = __FILE__;
$zipfile = "$filename.zip";

$data = file_get_contents(__FILE__);
echo 'Loaded file (size: ' . strlen($data) . ')'.br />';

file_put_contents("compress.zlib://$zipfile",
$data);
echo 'Zipped file (new size: ' .
filesize($zipfile) . ')'.br />';

$data = file_get_contents("compress.zlib://$zipfile");
echo 'Original file size: ' . strlen($data) . '.';
?>
```

*Zipping and Unzipping a File (zip.php; excerpt)*

In PHP the concept of PHP streams was introduced. Since then, there is a common denominator for all kinds of resources: files, HTTP and FTP data, and even archive file formats. You can find greater detail about the networking aspect of this in Chapter 11, “Communicating with Others”. this chapter just picks out some file-specific features: compression streams.