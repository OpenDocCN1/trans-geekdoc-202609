# Core PHP Programming

```
<?php
/*
 ** Check that a file is a GIF89
 */

$filename = "php.gif";

$fp = fopen($filename, "r");

//get first 128 bytes
$data = fread($fp, 128);

//close file
close($fp);

//check for GIF89
if(substr($data, 0, 5) == "GIF89")
{
    print("$filename is a GIF89 file.\n");
} else {
    print("$filename isn't a GIF89 file.\n");
}\?>
```

# integer fseek(integer file_handle, integer offset)

To change PHP's internal file pointer, use fseek. It expects a valid file handle as created by fopen. It also expects an offset, the number of bytes past the beginning of the file. If an error occurs, fseek returns negative one (-1); otherwise it returns zero (0). Take note that this is different from other PHP functions.

Seeking past the end of the file is not an error; however, fseek on a file opened by fopen if it was used using http:// or ftp:// is forbidden.

If you need to know where the file pointer points, use the ftell function.

```
<?php
// open a file
if($myFile = fopen("data.txt", "r"))
{
    // jump 32 bytes into the file
    fseek($myFile, 32);

    // dump the rest of the file
    fpassthru($myFile);
} else
```

IT-SC book

145