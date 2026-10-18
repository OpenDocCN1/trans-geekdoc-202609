uploaded file is written before the file is closed:

```
$fileTextFile = fopen ("uploadedfiles.txt",'a');
fwrite($fileTextFile, "$strRealname\r\n");
if (!fclose($fileTextFile) )
    echo "<p>Error closing file!</p>";
```

The script now provides us with a list of files which have been uploaded. We can now write a simple script which allows us to see and view the files:

```
<?php
// File: example12-22.php

$fileTextFile = fopen ("uploadedfiles.txt",'r');

echo "<h1>The following files have been uploaded</h1>";
while (!feof($fileTextFile) ) {
    $strLine = fgets($fileTextFile);
    echo "<p><a href='uploaded/$strLine'>$strLine</a></p>";
}

if (!fclose($fileTextFile) )
    echo "<p>Error closing file!</p>";
?>
```

The script is very simple. It opens the ‘uploadedfiles.txt’ file:

```
$fileTextFile = fopen ("uploadedfiles.txt",'r');
```

Using a ‘while’ construct, it displays all the files uploaded:

```
while (!feof($fileTextFile) ) {
    $strLine = fgets($fileTextFile);
    echo "<p><a href='uploaded/$strLine'>$strLine</a></p>";
}
```

The output from the above script looks something like that shown in Figure 12.15. Try clicking on the uploaded file links to see what happens.

# FIGURE 12.15 File upload viewer

![](bbox=[0.1, 0.73, 0.77, 0.95])