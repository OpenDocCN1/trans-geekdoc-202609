# Core PHP Programming

```
<?php
// open file for writing
$myFile = fopen("data.txt","w");

// make sure the open was successful
if(!($myFile) {
    print("file could not be opened");
    exit;
}

// use 1K buffer
print(set_file_buffer($myFile, 1024));

for($index=0; $index<10; $index++) {
    // write a line to the file
    fwrite($myFile, "line $index\n");
}

// close the file
close($myFile);
?>
```

# array stat(string filename)

The **stat** function executes C's stat function and returns an array. The array contains 13 elements, numbered starting at zero. If the filename argument points to a symbolic link, the array will reflect the file to which the link points. To get information about the link itself, use the istat function. Table 8.7 lists the contents of the array.

```
<?php
/*
 print stat information based on OS
 */

// get stat information
$statInfo = stat("data.txt");

if(ereg("windows", $os)) {
    // print until information for Windows
    printf("Drive: %c <BR>\n", $statInfo[0]+65);
    printf("Mode: %o <BR>\n", $statInfo[2]);
    printf("Size: %s bytes <BR>\n", $statInfo[7]);
    printf("Last Accessed: %s <BR>\n",
    date("H:i S D, Y", $statInfo[8]));
    printf("Last Modified: %s <BR>\n",
    date("H:i S D, Y", $statInfo[9]));
    printf("Created: %s <BR>\n", $statInfo[10]);
}
```