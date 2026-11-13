# MOVE_UPLOADED_FILE()

```
bool move_uploaded_file ( string filename, string destination)
```

This function incorporates the functionality of is_uploaded_file(). It first checks whether the argument file name was uploaded via HTTP POST, and, if so, moves it to the destination location. If it is not an uploaded file, the function returns FALSE.

# BASENAME()

```
string basename (string path [, string suffix])
```

Given a file path, this function will cut off all elements of the path except the base file name. If a suffix is given as an optional argument, that suffix will also be cut off of the file name. For example:

```
$path = "/www/htdocs/testfile.txt";
echo basename($path, ".txt");
```

will output

testfile

# REALPATH()

```
string realpath (string path)
```

Given a pathname containing symbolic links or ../ shortcuts, realpath() will return an absolute pathname with none of these components.

# FILE SYSTEM FUNCTIONS NOT USED IN THIS BOOK

File system functions are an important topic, and one you should spend some time learning about. Most of the more popular file system commands are available through PHP, and many commands are available for opening, reading, writing, and displaying files. But, as this book deals with a relational database for data storage, we will not cover them here.

# Script Control functions

This is a group of functions and language constructs that can be used to control the execution of PHP scripts.