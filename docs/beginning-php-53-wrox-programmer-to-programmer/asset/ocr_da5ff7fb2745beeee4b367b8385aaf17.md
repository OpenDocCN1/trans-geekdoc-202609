# Understanding Files and Directories

Everything on your hard drive is stored as a file of one kind or another, although folks think in terms of files and directories. There are ordinary program files, data files, files that are directories, and special files that help the hard drive keep track of the contents of folders and files. PHP has functions that can work with any type, but typically you'll be working with files that contain data.

The "directory" and "folder" are used interchangeably in this book (and in the PHP community); they mean exactly the same thing.

A file is nothing more than an ordered sequence of bytes stored on a disk or other storage media. A directory is a special type of file that holds the names of files and directories inside the folder (sometimes denoted as subdirectories or subfolders) and pointers to their storage area the media.

Many differences exist between UNIX-based and Windows operating systems, one of being the way directory paths are specified. UNIX-based systems as Linux use slashes to delimit elements in a path, like:

```
/home/matt/data/data.txt
```

Windows uses backslashes:

```
C:\MyDocs\data\data.txt
```

Fortunately, PHP on Windows automatically converts the former to the latter in many situations, so you can safely use slashes in your script, regardless of the operating system that the script is running on. Occasionally, though, backslashes are necessary. In this situation, you need to use two backslashes in a row, because PHP interprets a backslash as escaping the following character:

```
"C:\\MyDocs\\data\\data.txt"
```

# Getting Information on Files

PHP provides functions that enable you to access useful information. For example, you can use file_exists() to discover whether a file exists before attempting to open it:

```
file_exists("/home/chris/my-file.txt")
```

file_exists() returns true if the file at the specified path, or false otherwise.

In a similar fashion, you can use the filesize() to determine the size of a file on the hard disk. Just as with file_exists(), this function takes a filename as an argument:

```
filesize("/home/chris/my-file.txt")
```

This returns the size of the specified file in bytes, or false upon error.