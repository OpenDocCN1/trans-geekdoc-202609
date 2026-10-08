
# Core PHP Programming

```php
print("</TR>\n");

// Go back to beginning
rewdir($myDirectory);

print("<TR>");
print("<TH>Size</TH>");

// get each entry
while($entryName = readdir($myDirectory)) {
    print("<TD ALIGN=\"right\">");
    print(filesize($entryName));
    print("</TD>");
}
print("</TR>");

// close directory
closedir($myDirectory);
print("</TABLE>");
?>
```

# boolean rmdir(string directory)

Use the rmdir function to remove a directory. The directory must be empty. To remove a file, use unlink.

# set_file_buffer(integer file_handle, integer size)

Use set_file_buffer to set the size of the write buffer on a file stream. It requires a valid file handle as created by fopen, fsockopen, or popen. The size argument is a number of bytes, and if you set a buffer of zero, no buffering will be used. You must call set_file_buffer before making any reads or writes to the file stream. By default, file streams start with 8K buffers.

# Core PHP Programming

```php
<?php
// open file for writing
$myFile = fopen("data.txt","w");

// make sure the open was successful
if(!($myFile)) {
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

```php
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
date("H:i F d, Y", $statInfo[10]);
}
else {
    // print UNIX version
    print("Device: $statInfo[0] <BR>\n");
    print("INode: $statInfo[1] <BR>\n");
    printf("Mode: %s <BR>\n", $statInfo[2]);
    print("links: $statInfo[3] <BR>\n");
    print("UID: $statInfo[4] <BR>\n");
    print("GID: $statInfo[5] <BR>\n");
    print("Device: $statInfo[6] <BR>\n");
    print("Size: $statInfo[7] bytes <BR>\n");
    date("H:i F d, Y", $statInfo[8]);
    print("Last Modified: %s <BR>\n");
    date("H:i F d, Y", $statInfo[9]);
    print("Last Changed: %s <BR>\n");
    date("H:i F d, Y", $statInfo[10]);
    print("Block Size: $statInfo[11] <BR>\n");
    print("blocks: $statInfo[12] <BR>\n");
}
```

# Table 7.8. Array Returned by the stat Function

| Element | Name | Description |
|---|---|---|
| 0 | Device Drive Letter | This is a number identifying the device of the filesystem. On Windows this number denotes the drive letter it is on, with the A being zero. |
| 1 | Inode | A unique identifier for the file, always zero on Windows. This is the same value you get from the inode function. |
| 2 | Mode | This is the same value you get from fileperms, the read/write/execute permissions. |
| 3 | Number of Links | Number of links to file. On Windows, this will always be 1 if the file is not on an NTFS partition. |
| 4 | User | User ID of the owner, always zero on Windows. This is the same value you get from the fileowner function. |
| 5 | Group | Group ID, always zero on Windows. This is the same value you get from the group function. |
| 6 | Device Type | This is the type of device. On Windows it repeats the device number. |
| 7 | Size | Size of the file in bytes, which is the same reported by filesize. |
| 8 | Last Accessed | Last time the file was accessed, as defined in the description of fileatime. |
| 9 | Last Modified | Last time the file was modified, as defined in the description of mtime. |
| 10 | Last Changed | Last time the file was changed, as defined in the description of ctime. On Windows this is the time the file was created. |
| 11 | Block Size | Suggested block size for I/O to file, -1 under Windows. |
| 12 | Number of Blocks | Number of blocks used by file, -1 under Windows. |

# boolean symlink(string source, string destination)

The symlink function creates a symbolic link to the source argument with the name in the destination argument. To create a hard link, use the link function.

```php
<?php
//link moredata.txt to existing file data.txt
if(symlink("data.txt", "data.txt")) {
    print("Symbolic link created");
} else {
    print("Symbolic link not created");
}
?>
```

# integer tmpfile()

The tmpfile function opens a temporary file and returns its handle. This handle may be used the same way as fopen. If the temporary file cannot be created, FALSE is returned.

```php
<?php
//open temporary file
$fp = tmpfile();

//write some data
for($i = 0; $i < 1024; $i++) {
    //write random character
    fputs($fp, chr($i));
}

//rewind to start
rewind($fp);

//dump content
passthru($fp);

//close file,
fclose($fp);
?>
```

# Core PHP Programming

# boolean touch(string filename, integer time)

The touch function attempts to set the file time to the given time, expressed in seconds since January 1, 1970. If the time argument is omitted, the current time is used. If the file does not exist, it will be created.

```php
touch("data.txt");
```

# integer umask(integer umask)

The umask function returns the default permissions set when files are created. If the optional umask argument is given, it sets the umask. Under Windows this does nothing. To find out the permissions set on a particular file, use fileperms.

```php
<?php
printf("%o", umask(0444));
?>
```

# boolean unlink(string filename)

The unlink function removes a file permanently. To remove a directory, use rmdir.

```php
<?php
if(unlink("data2.txt")) {
    print("data2.txt deleted");
} else {
    print("data2.txt could not be deleted");
}
?>
```

# Compressed File Functions

The functions in this section use the zlib library to work with files compressed with GNU tools, such as gzip. The library was written by Jean-lou Gaul and Mark Adler. The authors of the gzip tool, in fact, http://www.cdrom.com/pub/infozip/. You can obtain more information and the library itself from the zlib home page: http://www.cdrom.com/pub/infozip/zlib/

In order to activate these functions, you must include the extension. On a UNIX operating system, you can configure PHP to use zlib as you compile it. On Windows you may activate the php_zlib.dll extension either using php.ini or using the dl function.

Most of the functions for reading and writing are duplicated and they operate similarly. One difference is the lack of support for specifying files using HTTP or FTP protocol.

# boolean gzclose(integer file_handle)

The gzclose closes a file opened with gzpen. TRUE is returned if the file closed. FALSE is returned if the file cannot be closed. See gzsets for an example of use.

# boolean gzeof(integer file_handle)

As you read from a compressed file, PHP keeps a pointer to the last place in the file you read. The gzeof function returns TRUE if you are at the end of the file. See gzsets for an example of use.

# array gzfile(string filename, boolean use_include_path)

The gzfile reads an entire file into an array. Each line of the file is a separate element of the array, starting at zero. The first line is uncompressed. The optional use_include_path argument causes gzfile to search for the file within the path specified in php.ini.

```php
<?php
// open file and print each line
$myFile = gzfile("data.gz");
for($index = 0; $index < count($myFile); $index++)
{
    print($myFile[$index]);
}
?>
```

# string gzgetc(integer file_handle)
