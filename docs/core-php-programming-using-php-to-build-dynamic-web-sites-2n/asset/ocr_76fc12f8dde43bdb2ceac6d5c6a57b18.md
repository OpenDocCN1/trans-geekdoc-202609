Core PHP Programming

```
/*
** print a file, then print the first line again
 */

// open a local file
if(!$myFile = gzopen("data.gz", "r\))
{
    print("file could not be opened");
    exit;
}

while(!gzeof($myFile))
{
    // read a line from the file
    $myLine = gzgets($myFile, 255);
    print("$myLine <BR>\n");
}

gzrewind($myFile);
$myLine = gzgets($myFile, 255);
print("$myLine <BR>\n");

// close the file
gzclose($myFile);
```

# integer gzseek(integer file_handle, integer offset)

This function works exactly like fseek, except that it operates on compressed files.

```
<?
// open a file
if(!$myFile = gzopen("data.gz", "r\))
{
    print("file could not be opened");
    exit;
}

// jump 32 bytes into the file
gzseek($myFile, 32);

$myLine = gzgets($myFile, 255);
print("$myLine");

// dump the rest of the file
gzpassthru($myFile);
?>
```

# integer gztell(integer file_handle)

IT-SC book 167