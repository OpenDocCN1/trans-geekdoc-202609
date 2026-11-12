
"a": Opens the file in write-only mode. The file pointer is placed at the end of the file. If the file does not exist, try to create it.

"r+": Opens the file for reading and writing. The file pointer is placed at the beginning of the file.
The fopen() function returns a file pointer which is used by other file manipulation functions such as fread(), fwrite(), etc. If the fopen() function fails, it returns FALSE.

Here's an example:

```php
<?php
$handle = fopen("filetext/poem1.txt", "r");
?>
```

After opening the file with the fopen() function, the next step is to read its contents. PHP offers several functions for this task, including the fread() function, the fgets() function and the fgetc() function. Each of these functions offers a different method for reading data from the open file.

**The fread() function:** reads a specific number of bytes from the file opened with fopen(). It takes two arguments: the file pointer returned by fopen() and the number of bytes to be read. However, if you wish to read the entire file, you can use the filesize() function, which returns the total size of the file. Simply provide the name of the file you wish to read.

```php
<?php
$handle = fopen("filetext/poem1.txt", "r");
$content = fread($handle, filesize("filetext/poem1.txt"));
echo $content;
?>
```

Execution of this code will open the poem1.txt file and allow read-only access to its entire contents.

![](img/caba2aa22f5409ba73dea47176330677_302_0.png)

If you wish to read a specific number of bytes from the file contents, simply specify this number of bytes as the second argument to the fread() function. For example, the following code allows you to read only 50 bytes of this content.

```php
<?php
$handle = fopen("filetext/poem1.txt", "r");
$content = fread($handle, 50);
echo $content;
?>
```

### Result:

### The fgets() function:
reads an entire line from the file opened by fopen(). It takes as argument the file pointer returned by fopen(). This function reads the line up to the end-of-line character, usually a line feed or carriage return. It returns the line read as a string, including the end-of-line character. If it reaches the end of the file, it returns false.

### Example:

```php
<?php
$handle = fopen("filetext/poem1.txt", "r");
$content = fgets($handle);
echo $content;
?>
```

### Result:

Shall I compare thee to a summer's day?

### The fgetc() function:
reads one character at a time from the file opened by fopen(). It takes as argument the file pointer returned by fopen(). Each time fgetc() is called, it advances one character in the file and returns the character read as a string. If it reaches the end of the file, it returns false.

In the following example, the fgetc() function will be executed six times, displaying the first six characters of the file in question:

```php
<?php
$handle = fopen("filetext/poem1.txt", "r");
echo fgetc($handle);
echo fgetc($handle);
echo fgetc($handle);
echo fgetc($handle);
echo fgetc($handle);
echo fgetc($handle);
?>
```

### Result:

![](img/caba2aa22f5409ba73dea47176330677_305_0.png)

To read the entire contents of a file using the fgetc() function, you can call it in a while loop until it returns false, indicating the end of the file.

Here is an example of the code:

```php
<?php
$file = fopen("filetext/poem1.txt", "r");
if ($file) {
// Loop for reading character by character
while ((!$char = fgetc($file)) != false) {
echo $char;
}
}
?>
```

This PHP code opens the "poem1.txt" file in read mode using the fopen() function. If the file is opened successfully (i.e. if $file is not equal to false), then a while loop is initiated. At each iteration of the loop, the fgetc() function is used to read a character from the file. The loop condition checks whether the value returned by fgetc() is not false, meaning that there are still characters to read from the file. If so, the character is displayed using echo. This loop is repeated until the end of the file is reached, at which point the value returned by fgetc() becomes false, thus terminating the loop.

### The fclose() function:
is used to close a file that has been previously opened with the fopen() function. It takes as argument the file pointer returned by fopen().

Example of using fclose() :

```php
<?php
$handle = fopen("filetext/poem1.txt", "r");

if ($handle) {
$content = fread($handle, filesize("filetext/poem1.txt"));
echo $content;
fclose($handle); // Close file
} else {
echo "Unable to open file";
}
?>
```

This PHP code opens the file "poem1.txt" in read mode using the fopen() function. If the file is opened successfully, the file size is obtained using the filesize() function and the file contents are read into a variable using the fread() function. The contents are then displayed with echo.

After reading the file contents, the fclose() function is used to close the file and release the associated resources. If the file cannot be opened, an error message is displayed indicating that file opening has failed.

## File creation

Creating files in PHP is a common operation that can be easily performed using a few built-in functions. Here's how to create a new file :

### Using the fopen() function

The first step in creating a file is to use the fopen() function. This function opens a file or creates one if it doesn't already exist. Here's an example:

```php
<?php
// Open a file in write mode (create a new file if it doesn't exist)
$handle = fopen("filetext/new_file.txt", "w");

// Check if the file has been opened successfully
if ($handle != false) {
    echo "The file has been created successfully!";
    fclose($handle); // Close file after use
} else {
    echo "Impossible to create the file";
}
?>
```

In this example, we use fopen() to open a file named "new_file.txt" in write mode ("w"). If the file does not exist, fopen() will create it. If the file is opened successfully, a success message is displayed, otherwise an error message is displayed.

The fopen() function can also be used to open files in other modes, such as read-only ("r"), read/write ("r+"), append ("a") and so on.

This step is essential for creating a file before writing data to it.

If this code is executed without error, the message "The file has been created successfully" is displayed, and a new empty file named "new_file.txt" is created in the "filetext" directory.

![](img/caba2aa22f5409ba73dea47176330677_309_0.png)

## Writing files

Writing to files in PHP is a common operation when it comes to generating data files, activity logs or reports. PHP offers several methods for writing to files, providing great flexibility to meet different development needs. In this section, we'll explore different ways of writing to files in PHP.

### Using the fwrite() function

Once the file has been successfully opened, we can write data to it using the fwrite() function.

The fwrite() function in PHP is used to write data to a file. It generally takes three arguments: the file pointer (usually returned by the fopen() function), the string to be written to the file, and optionally the length of the string to be written. If the length is not specified, fwrite() will write the entire string supplied.

The fwrite() function returns the number of bytes written to the file, or FALSE on error. It is often used in conjunction with the fopen() function to open a file in write mode. Once the data has been written, we recommend closing the file using the fclose() function to free up system resources.

Here's an example of how to use fwrite() to write to a file:

```php
<?php
// Open a file in write mode
$file = fopen("filetext/new_file.txt", "w");

// Write a string to the file
$data = "This is an example of content to be written to the file.";
fwrite($file, $data);

// Close the file
fclose($file);
?>
```

In this example, the fopen() function opens the file named "new_file.txt" in write mode ("w"). Next, the fwrite() function writes the string stored in the $data variable to this file. Finally, the fclose() function closes the newly created file.

### Using the file_put_contents() function

The file_put_contents() function in PHP is used to write data to a file. It takes as parameters the path of the file to write to, the data to be written, and possibly additional options.

Example of using file_put_contents() to write to a file :

```php
<?php

// Data to be written to the file
$data = "Content to be written to the file.";

// Target file path
$filename = "filetext/new_file.txt";

// Write data to file
file_put_contents($filename, $data);
```
