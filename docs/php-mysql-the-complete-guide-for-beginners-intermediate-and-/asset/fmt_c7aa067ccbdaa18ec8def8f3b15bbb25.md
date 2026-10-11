
## Section 43.2: Deleting directories

On the other hand, directories should be deleted with `rmdir`. However, this function only deletes empty directories. To delete a directory with files, delete the files in the directories first. If the directory contains subdirectories, recursion may be needed.

The following example scans files in a directory, deletes member files/directories recursively, and returns the number of files (not directories) deleted.

![](Image00996.jpg)

## Section 43.3: Getting file information

### Check if a path is a directory or a file

The `is_dir` function returns whether the argument is a directory, while `is_file` returns whether the argument is a file. Use `file_exists` to check if it is either.

![](Image00997.jpg)

```
$file = "/this/is/a/file.txt";
```

![](Image00998.jpg)
```
echo is_dir($dir) ? "$dir is a directory" : "$dir is not a directory", PHP_EOL,
     is_file($dir) ? "$dir is a file" : "$dir is not a file", PHP_EOL,
     file_exists($dir) ? "$dir exists" : "$dir doesn't exist", PHP_EOL,
     is_dir($file) ? "$file is a directory" : "$file is not a directory", PHP_EOL,
     is_file($file) ? "$file is a file" : "$file is not a file", PHP_EOL,
     file_exists($file) ? "$file exists" : "$file doesn't exist", PHP_EOL;
```

This gives:

![](Image00999.jpg)

### Checking file type

Use `filetype` to check the type of a file, which may be:

![](Image01000.jpg)
`fifo` `char` `dir` `block` `link` `file` `socket` `unknown`

Passing the filename to the `filetype` directly:

![](Image01001.jpg)

Note that `filetype` returns `false` and triggers an `E_WARNING` if the file doesn't exist.

### Checking readability and writability

Passing the filename to the `is_writable` and `is_readable` functions check whether the file is writable or readable respectively.

The functions return `false` gracefully if the file does not exist.

### Checking file access/modify time

Using `filemtime` and `fileatime` returns the timestamp of the last modification or access of the file. The return value is a Unix timestamp -- see Working with Dates and Time for details.

![](Image01002.jpg)
```
echo "File was last modified on " . date("Y-m-d", filemtime("file.txt"));
echo "File was last accessed on " . date("Y-m-d", fileatime("file.txt"));
```

![](Image01003.jpg)

![](Image01004.jpg)

This example will output:

![](Image01005.jpg)

![](Image01006.jpg)

### Parsing file path information

`$path` The full path of the file to be parsed

One of four available options `$option`: `PATHINFO_DIRNAME`, `PATHINFO_BASENAME`, `PATHINFO_EXTENSION` or `PATHINFO_FILENAME`

| image | | . | | jpg | | . | | png | | would be | | . | | png |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

![](Image01007.jpg)
If an option (the second parameter) is not passed, an associative array is returned otherwise a string is returned.

Does not validate that the file exists.

Simply parses the string into parts. No validation is done on the file (no mime-type checking, etc.)

| jpg |
| --- |

The extension is simply the last extension of `$path` The path for the file even if it technically a `.` file. A file without an extension will not return an extension element in the array.

## Section 43.4: Stream-based file IO

### Opening a stream

`fopen` opens a file stream handle, which can be used with various functions for reading, writing, seeking and other functions on top of it. This value is of resource type, and cannot be passed to other threads persisting its functionality.

![](Image01008.jpg)
```
$f = fopen("errors.log", "a"); // Will try to open errors.log for writing
```

The second parameter is the mode of the file stream:

| Mode | Description |
| --- | --- |
| r | Open in read only mode, starting at the beginning of the file |
| r+ | Open for reading and writing, starting at the beginning of the file |
| w | Open for writing only, starting at the beginning of the file. If the file exists it will empty the file. If it doesn't exist it will attempt to create it. |
| w+ | Open for reading and writing, starting at the beginning of the file. If the file exists it will empty the file. If it doesn't exist it will attempt to create it. |
| a | Open a file for writing only, starting at the end of the file. If the file does not exist, it will try to create it |
| a+ | Open a file for reading and writing, starting at the end of the file. If the file does not exist, it will try to create it |
| x | Create and open a file for writing only. If the file exists the `fopen` call will fail |
| x+ | Create and open a file for reading and writing. If the file exists the `fopen` call will fail |
| c | Open the file for writing only. If the file does not exist it will try to create it. It will start writing at the beginning of the file, but will not empty the file ahead of writing |
| c+ | Open the file for reading and writing. If the file does not exist it will try to create it. It will start writing at the beginning of the file, but will not empty the file ahead of writing |

| `\n` | | " line endings to " | | `\r\n` |
| --- | --- | --- | --- | --- |

Adding a `t` behind the mode (e.g. `a+b`, `wt`, etc.) in Windows will translate `""` when working with the file. Add `b` behind the mode if this is not intended, especially if it is a binary file.

The PHP application should close streams using `fclose` when they are no longer used to prevent the Too many open files error. This is particularly important in CLI programs, since the streams are only closed when the runtime shuts down -- this means that in web servers, it may not be necessary (but still should, as a practice to prevent resource leak) to close the streams if you do not expect the process to run for a long time, and will not open many streams.

### Reading

Using `fread` will read the given number of bytes from the file pointer, or until an EOF is met.

#### Reading lines

Using `fgets` will read the file until an EOL is reached, or the given length is read.

Both `fread` and `fgets` will move the file pointer while reading.

#### Reading everything remaining

Using `stream_get_contents` will read all remaining bytes in the stream into a string and return it.

### Adjusting file pointer position

Initially after opening the stream, the file pointer is at the beginning of the file (or the end, if the mode `a` is used). Using the `fseek` function will move the file pointer to a new position, relative to one of three values:

![](Image01009.jpg)
`SEEK_SET`: This is the default value; the file position offset will be relative to the beginning of the file.

`SEEK_CUR`: The file position offset will be relative to the current position.

`SEEK_END`: The file position offset will be relative to the end of the file. Passing a negative offset is the most common use for this value; it will move the file position to the specified number of bytes before the end of file.

| SEEK_SET |
| --- |

| fseek | ( | $fh |
| --- | --- | --- |

![](Image01010.jpg)
`rewind` is a convenience shortcut of `fseek($fh, 0, SEEK_SET)`.

Using `ftell` will show the absolute position of the file pointer.

For example, the following script reads skips the first 10 bytes, reads the next 10 bytes, skips 10 bytes, reads the next 10 bytes, and then the last 10 bytes in file.txt:

![](Image01011.jpg)

![](Image01012.jpg)

### Writing

Using `fwrite` writes the provided string to the file starting at the current file pointer.

![](Image01013.jpg)

## Section 43.5: Moving and Copying files and directories
