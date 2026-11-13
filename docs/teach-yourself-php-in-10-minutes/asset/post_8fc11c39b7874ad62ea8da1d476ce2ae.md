
The `realpath` function takes a pathname argument and returns its absolute pathname. Any symbolic links in the path are resolved to their actual location on disk, and any references to the current or parent directory using `.` or `..` are removed.

If you want to write to a temporary file, you can use the `tempnam` function to generate a unique temporary filename. It takes two arguments: a directory name and a filename prefix. The prefix argument is required but can be an empty string. The following statement generates a temporary filename in `/tmp` with no prefix:

```php
$filename = tempnam("/tmp", "");
```

## Reading and Writing Files

Now let's see how to read and write files from PHP.

### Simple Methods for Reading and Writing Files

PHP provides some simple, high-level functions that can open a file and grab its contents or write data to a file in a single operation.

To read the contents of a file into a string variable, you use `file_get_contents`. The argument is a filename, which can contain a relative or absolute path. The following statement reads a file called `file.txt` into the variable `$data`:

```php
$data = file_get_contents("file.txt");
```

An optional second Boolean argument can be set to `TRUE` to search the include path for the given filename. You will see how to configure the include path in Lesson 23, "PHP Configuration."

The function `file_put_contents` simply dumps the contents of a variable to a local file. Its arguments are the filename to write to and the data to write. The following statement writes the value of `$data` to `file.txt`:

```php
file_put_contents("file.txt", $data);
```

### Lower-Level File Access

The functions `file_get_contents` and `file_put_contents` are high-level functions that perform a number of steps that can be done individually with lower-level PHP functions. Although in many cases reading the entire contents of a file or writing data to a file is the task you will want to perform, PHP provides a flexible way to interface with the filesystem.

All file access begins with a file handler, which is established with the `fopen` function. The arguments to `fopen` are a filename and the mode in which to open the file. The available modes are shown in Table 17.3.

### Table 17.3. File Mode Arguments to `fopen`

| Mode | Description |
| :--- | :--- |
| r | Opens for reading only from the beginning of the file. |
| r+ | Opens for reading and writing from the beginning of the file. |
| w | Opens for writing only; overwrites the old file if one already exists. |
| w+ | Opens for writing and reading; overwrites the old file if one already exists. |
| a | Opens for writing only and appends new data to the end of the file. |
| a+ | Opens for reading and writing at the end of the file. |

Each file handler points to a position in the file. You can see from Table 17.3 that when a file is opened by using `fopen`, the handler always points to either the beginning or the end of the file. As you read or write using that handler, its pointer location moves, and subsequent actions take place from that point in the file.

Let's look at an example where you read the contents of a file a few bytes at a time. By calling `fopen` with the `r` mode argument, you create a read-only file handler that initially points to the start of that file.

The `fread` function reads a fixed number of bytes from a file handler. Its arguments are the file handler and the number of bytes to read. By performing this action in a loop, you can eventually read the entire contents of a file:

```php
$fp = fopen("file.txt", "r");
while ($chunk = fread($fp, 100)) {
    echo $chunk;
}
```

This is a very compact statement that checks that `fread` has succeeded on each pass of the loop. When there is no more data to read, `fread` returns `FALSE`. In fact, by using this loop to output the file to screen, you cannot tell from the result that it was actually done in smaller chunks.

An alternative to `fread` is `fgets`, which reads a line of the file at a time. The size argument to `fgets` has been optional since PHP 4.3 but is shown in these examples for completeness. No more data is read after a carriage return is reached in the file or the specified number of bytes has been read, whichever is sooner.

The following example uses `fgets` in a loop, assuming that no line in the file is more than 100 characters wide:

```php
$fp = fopen("file.txt", "r");
while ($line = fgets($fp, 100)) {
    echo $line;
}
```

**Chopping Strings** Each line read by `fgets` ends with a newline character. If you want to exclude the newline, you can use the `rtrim` function on the string to remove it along with any trailing whitespace characters.

When you are finished with a file pointer, you should free up its resources by calling the `fclose` function:

```php
fclose($fp);
```

### Random Access to Files

The file pointer does not have to be moved sequentially through a file; it can be reassigned to any position while the file handle is still open.

To find the current location of the file pointer, you use `ftell`. An integer is returned—the number of bytes from the start of the file:

```php
$filepos = ftell($fp);
```

To send the file pointer to a specific location, you use the `fseek` function. The following statement places the file pointer 100 bytes from the start, using the file handler `$fp`:

```php
fseek($fp, 100);
```

Most often you just want to return the file pointer to the beginning of the file. You could set `fseek` to position zero, or you could just use the built-in function `rewind`:

```php
rewind($fp);
```

### Writing to a File Pointer

The complementary functions to `fgets` and `fread` to perform write operations on a file pointer are `fputs` and `fwrite`. These functions are actually identical to one another, with the newline character treated just like any other character as they are written to the file.

The following example opens a file and writes to it the current time:

```php
$fp = fopen("time.txt", "w");
fwrite($fp, "Data written at ".date("H:i:s"));
fclose($fp);
```

Remember that the apache user needs to have write permissions on the directory in order to create a new file.

If you examine the new `time.txt` file, you will see that it does indeed contain the current time.

### Working with Data Files

One of the reasons you might need to access the filesystem from PHP is to load data from a structured file format into your script. One of the easiest file formats to use is comma-separated values (CSV).

Although it would appear to be fairly easy to read a line of the file at a time and call `explode` to break up the line where each comma appears, this would not work where data elements in the CSV file contain commas. If you export data from a spreadsheet, columns containing commas are usually enclosed in quotes, so you need quite a complex rule to manipulate the data successfully.

Fortunately, PHP includes the function `fgetcsv`. It works in a similar way to `fgets`, except that an array is returned, containing one element for each comma-separated value in the list. The size argument to `fgetcsv` is optional as of PHP 5.

Often the first line of a CSV file contains the column headings. If you know that this is the case, you should discard the file line before processing the data file. The following example reads a comma-separated data file and dumps each record to screen by using `print_r`:

```php
$fp = fopen("data.csv", "r");
while ($record = fgetcsv($fp, 1000)) {
    echo $record;
}
```

![](img/2edc6e6954e3485ad7d94117645931d8_188_0.png)

> **Reading CSV Files** The `fgetcsv` function requires a line length argument, just like `fgets`. In the previous example, this has an arbitrary value of `1000`, but you should ensure that whatever value you use is larger than the longest line in your data file.

You can also write data to a CSV file without having to manually encode the format. The `fputcsv` function takes a file handle and an array argument and writes a comma-separated list of the elements in the array.

The optional third and fourth arguments to `fputcsv` allow you to specify an alternate delimiter and enclosure characters, respectively; the defaults are the comma and double quote characters.

### Working with URLs

A powerful feature of PHP is its ability to deal with remote documents in the same way it deals with local files. It is possible to open a file handle or use the high-level filesystem access functions with a URL argument to read a web page from a PHP script.

The following statements are both valid:

```php
$page = file_get_contents("http://www.samspublishing.com/");
$fp = fopen("http://www.samspublishing.com/", "r");
```

You cannot write to an HTTP URL by using `file_put_contents` or `fputs`, however.

### Working with Directories

Similarly to the way that `fopen` generates a file handle for accessing the contents of a file, you can create a directory handle to view the contents of a directory by using the `opendir` function.

There are just three calls that can be performed on a directory handle—`readdir`, `rewinddir`, and `closedir`—each of which takes a single resource argument.

Each call to `readdir` returns the next file from the directory. The order in which files are returned is the order in which they are stored by the filesystem and cannot be changed. The special items `.` and `..` (the current working directory and its parent) are always returned.

You use `rewinddir` to reset the directory handle to the beginning of the file list at any time, and you close the handle with `closedir` when you are finished with it.

To find the name of the current working directory, you use `getcwd`. No arguments are required, and the full path to the current directory is returned. To change directory, you use `chdir` with a relative or absolute path.
