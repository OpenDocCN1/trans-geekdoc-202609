# Core PHP Programming

```
print("<H1>Local</H1\n");
print("<HR>\n");

// open a local file
if(!$myFile = fopen("data.txt", "r\))
{
    print("file could not be opened");
    exit;\n}
while(!feof($myFile))
{
    // read a line from the file
    $myLine = fgets($myFile, 255);
    print("$myLine<BR>\n");
}

// close the file
close($myFile);
```

# boolean fpassthru(integer file_handle)

The fpassthru function prints contents of the file to the browser. Data from the current file position to the end are sent, so you can read a few lines and output the rest. The file is closed after being sent. If an error occurs, fpassthru returns false. The gzipsthru function offers the same functionality for compressed files.

```
?
/*
 ** Get a Web page, change the title tag
 */

// open a file using http protocol
if(!$myFile = fopen("http://www.clearink.com", "r"))
{
    print("file could not be opened");
    exit;
}

$KeepSearching = TRUE;

while(!feof($myFile) AND $KeepSearching)
{
    // read a line from the file
    $myLine = gets($myFile, 1024);

    //watch for body tag
    if(eregi("<body", $myLine))
    {
        //no chance to find a title tag
        //after a body tag
    }
```

IT-SC book

143