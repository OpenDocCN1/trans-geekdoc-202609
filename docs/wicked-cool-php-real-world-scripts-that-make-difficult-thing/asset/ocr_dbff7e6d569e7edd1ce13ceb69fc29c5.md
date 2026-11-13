# #51: Creating and Writing to a File

Here's how to write a string to a file:

```
<?
$file_data = "Hello, file.\nSecond line.";
$fd = fopen('file.txt', 'w');
if (!$fd) {
    echo "Error! Couldn't open/create the file.";
    die;
}
fwrite($fd, $file_data);
fclose($fd);
?>
```

Notice that this script explicitly includes newlines. When viewed on a Unix machine, the file looks like this:

```
Hello, file.
Second line.
```

The separator between the two lines is called a newline. On Unix and Macs, it's a single character represented in PHP as \n inside double quotes. However, in Windows and Macs, the newline is the \r\n sequence ("carriage return, then newline").

Therefore, if you actually care about cross-platform text file readability, you need to be a little careful. A Unix text file appears as one big line in Windows, and a Windows text file has a carriage return before the end of each line.

You can explicitly state the newline as \r\n if you like, but if you're really worried about portability, add a t to the end of the mode in fopen(), so the mode is wt. This automatically translates \n to \r\n on Windows.

# #52: Checking to See If a File Exists

fopen() generates error messages if you're trying to open a file that doesn't exist, as do other functions such as unlink(), when you attempt to delete a nonexistent file. To see if a file exists before you perform a file operation, use the file_exists() function in a test condition:

```
<?
if (file_exists('file.txt')) {
    print 'OK, file.txt exists.';
}
```

As you can see, this function returns true if the file exists and false if it does not.