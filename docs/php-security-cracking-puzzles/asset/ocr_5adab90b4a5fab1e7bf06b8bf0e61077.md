```
// in the archive.tar file
$fd = fopen("archeve.tar", "w");
fwrite($fd, implode("", $arr));
close($fd);
```

Listing II15.6 uses the gzfile() function, which is analogous to the file() function. The gzfile() function returns an array, each element of which contains a line of the decompressed GZ file. The array elements are joined into a string using the implode() function producing the original archive.tar file.

# ## II15.4. Buffering Data

An easy way to solve this problem is to use buffering. The output is buffered with the help of the ob_start() function, which tells the PHP interpreter not to display the output in the browser window to store it in an internal buffer instead. The contents of the buffer can be retrieved using the ob_get_contents() function. The buffer is cleared using the ob_end_clean() function The function returns true when the buffer is successfully cleared, false otherwise. The task of setting off in bold all 1 digits in a random sequence of digits can be solved as shown in Listing II15.7.

Listing II15.7. Highlighting all 1 digits

```
<?php
// Redirecting all output to a buffer
ob_start();
// Forming the page
for($i = 0; $i < 1000; $i++) echo rand().
```