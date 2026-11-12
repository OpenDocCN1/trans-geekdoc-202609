handy for extracting textual content from files such as text files, CSV files or even web pages. This function is simple to use and returns the complete contents of the file in a string, making it easy to manipulate in PHP code.

# Using fopen(), fread() and fclose()

For more controlled and efficient reading of larger files, the fopen(), fread() and fclose() functions can be used. fopen() opens the file, fread() reads a specified number of bytes from the file and fclose() closes the file after reading.

Here's how to use them to read the contents of a file:

**fopen()** : This function opens a file or URL and returns a file pointer. It takes two arguments: the name of the file to be opened and the opening mode (read, write, etc.). The syntax of this function is as follows:

```
$handle = fopen("file_name", "Opening_mode");
```

The opening mode specifies how the file is to be opened. Here are some common modes:

+   "r": Opens the file in read-only mode. The file pointer is placed at the beginning of the file.

+   "w": Opens the file in write-only mode. Deletes existing contents or creates a new file if the file does not exist. The file pointer is placed at the beginning of the file.