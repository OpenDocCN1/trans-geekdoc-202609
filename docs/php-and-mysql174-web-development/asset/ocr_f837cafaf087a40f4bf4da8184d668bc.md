The length parameter should be greater than the length in characters of the longest line in the file you are trying to read, or 0 if you do not want to limit the line length.

The enclosure parameter specifies what each field in a line is surrounded by. If not specified, it defaults to " (a double quotation).

# Reading the Whole File: readfile(), fpassthru(), file(), and file_get_contents()

Instead of reading from a file at a time, you can read the whole file in one. Here are four different ways you can do this.

The first uses readfile(). You can replace almost the script you wrote previously with one line:

```
readfile("$document_root/../orders/orders.txt");
```

A call to the readfile() function opens the file, echoes it to standard output (browser), and closes the file. The prototype for readfile() is

```
int readfile(string filename, [bool use_include_path[, resource $context]]);
```

The second option specifies whether PHP should look for the file in the include_path and operates the same way as fopen(). The context parameter is used only when files are opened remotely, for example, HTTP: we cover such usage in detail in Chapter 18. The function returns the number of bytes read from the first.

Second, you can use fpassthru(). To do so, you need to open the file using fopen() first. You can then pass the file pointer as an argument to fpassthru(), which dumps the contents of the file from the pointer's position to output. It closes the file when it is finished.

You can use fpassthru() as follows:

```
$fp = fopen("$document_root/../orders/orders.txt", 'rb');
fpassthru($fp);
```

The function fpassthru() returns true if the read is successful and false otherwise.

The third option for reading the whole file is using the file() function. This function is identical to readfile() except that instead of echoing the file to standard output, it turns into an array. We cover this function in more detail when we look at arrays in Chapter 3. For reference, you would call it

```
$filearray = file("$document_root/../orders/orders.txt"
```

This line reads the entire file into the array $filearray. Each line of the file is stored in a separate element of the array. Note that this function was not binary safe in older versions of PHP.