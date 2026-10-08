The gzgetc function returns a single character from a compressed file. It expects a file handled by gzopen.

```
<?php
// open compressed file and print each character
if($myFile = gzopen("data.gz", "r")) {
    while(!gzeof($myFile)) {
        $myCharacter = gzgetc($myFile);
        print($myCharacter);
    }

    gzclose($myFile);
}
?>
```

# stringgets(integer file_handle, integer length)

The gzgets returns a string from a compressed file specified by the file handle, which must have been created with gzopen. It will attempt to read as many characters specified by the length argument (one presumably this PHP showing its C heritage). A linebreak is treated as a stopping point, as is the end of the file. Linebreaks are included in the return string.

```
<?php
// open file and print each line
if($myFile = gzopen("data.gz", "r")) {
    while(!gzeof($myFile)) {
        $myLine = gzgets($myFile, 255);
        print($myLine);
    }

    gzclose($myFile);
}
?>
```

# string gets(integer file_handle, integer length, string ignore)

The gzss function is in all respects identical to gzgets except that it attempts to strip any HTML or PHP code before returning a string. The optional ignore argument may contain tags to be ignored.