
chdir() returns true if PHP managed to change to the specified directory, or false if there was an error (such as the directory not being found).

The current directory is the directory where PHP first looks for files. If you specify a path that isn’t an absolute or relative path, PHP looks for the file inside the current directory. So the following code

```
chdir( "/home/matt/myfolder" );
$handle = fopen( "myfile.txt" );
```

opens the same myfile.txt file as:

```
$handle = fopen( "/home/matt/myfolder/myfile.txt" );
```

The current directory is also used as the base directory for relative file paths. For example:

```
chdir( "/home/joe/images" );
$handle = fopen( "../myfile.txt" ); // Looks for myfile.txt in /home/joe
```

Usually the current directory defaults to the directory containing the running script. You can retrieve the current directory by calling getcwd():

```
chdir( "/home/matt/newfolder" );
echo getcwd(); // Displays "/home/matt/newfolder"
```

## Creating Directories

To create a new directory, call the mkdir() function, passing in the path of the directory you want to create:

```
mkdir( "/home/matt/newfolder" );
```

Note that the parent directory has to exist already ( "/home/matt" in the example just shown) for the function to work. mkdir() returns true if the directory was created, or false if there was a problem.

You can also set permissions for the directory at the time you create it by passing the mode as the second argument. This works much like using chmod() — see the “Changing Permissions” section earlier in the chapter for details. For example, the following code creates a directory with read, write, and execute permissions granted to all users:

```
mkdir( "/home/matt/newfolder", 0777 );
```

File and directory modes only work on UNIX systems such as Linux and Mac OS; they have no effect when used on Windows machines.

## Deleting Directories

The rmdir() function removes a given directory. The directory must be empty, and you need appropriate permissions to remove it. For example:

```
rmdir( "/home/matt/myfolder" );
```

If PHP can’t remove the directory — for example, because it’s not empty — rmdir() returns false; otherwise it returns true.

## Getting the Directory Path

The dirname() function returns the directory part of a given path. It complements the basename() function, which returns the filename portion of a given path (see the section "Retrieving a Filename from a Path" earlier in the chapter).

For example:

```
$path = "/home/james/docs/index.html";
$directoryPath = dirname( $path );
$filename = basename( $path );
```

After running this code, $directoryPath contains "/home/james/docs", and $filename holds "index.html".

## Working with Directory Objects

PHP offers an alternative object-oriented mechanism for working with directories: the Directory class. To use it, first create a Directory object by calling the dir() function with the name of the directory you want to work with, as follows:

```
$dir = dir( "/home/james/docs" );
```

The Directory object provides two properties: handle and path. These refer to the directory handle and the path to the directory, respectively:

```
echo $dir->handle . "<br />"; // Displays the directory handle
echo $dir->path . "<br />"; // Displays "/home/james/docs"
```

You can use the handle property with other directory functions such as readdir(), rewinddir(), and closedir(), just as if you were using a regular directory handle.

The Directory object supports three methods — read(), rewind(), and close() — which are functionally equivalent to readdir(), rewinddir(), and closedir(), respectively. For example, you can rewrite the dir_list.php script from earlier in the chapter using a Directory object:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Listing the contents of a directory</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Listing the contents of a directory</h1>

<?php

$dirPath = "/home/matt/images";
$dir = dir( $dirPath );

?>

<?php echo $dirPath ?> contains the following files and folders:</p>
<ul>
<?php
while ( $file = $dir->read() ) {
    if ( $file != "." && $file != ".." ) echo "<li>$file</li>";
}
$dir->close();
?>
</ul>
</body>
</html>
```

## Telling a File from a Directory

Often you need to know whether a particular file is a regular file or a directory. For example, suppose you want to write some code that travels down through a tree of folders. You'd need to detect when a file was actually a folder, so you could enter the folder and continue working through the tree. By the same token, if you want to display the files in a folder, you'd need to detect when a file is in fact a regular file.

*Remember: both directories and regular files are all essentially files, but directories are a special kind of file.*

PHP has two functions to help you test for a file or a directory:

- `is_dir()` — Returns true if the given filename refers to a directory
- `is_file()` — Returns true if the given filename refers to a regular file

Here's a simple example that determines if a file called myfile is a file or a directory:

```
$filename = "myfile";

if ( is_dir( $filename ) ) {
    echo "$filename is a directory.";
} elseif ( is_file( $filename ) ) {
    echo "$filename is a file.";
} else {
    echo "$filename is neither a directory nor a file.";
}
```

## Traversing a Directory Hierarchy

As you learned in Chapter 7, recursion is particularly useful when a script has to perform repetitive operations over a set of data of unknown size, and traversing a directory hierarchy is a very good example.

A directory may hold subdirectories as well as files. If you want to create a script that lists all the files and subdirectories under a given directory — including subdirectories of subdirectories, and so on — you need to write a recursive function, as follows:

- 1. Read the entries in the current directory.
- 2. If the next entry is a file, display its name.
- 3. If the next entry is a subdirectory, display its name, then call the function recursively to read the entries inside it.

As you can see, the third step repeats the whole process by itself, when necessary. The recursion continues until there are no more subdirectories left to traverse.

To try out this technique, first save the following script as directory_tree.php. Now change the $dirPath variable at the top of the script to point to a folder on your Web server's hard drive, and open the script's URL in your Web browser. You should see a page similar to Figure 11-3.

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <title>Listing the contents of a directory</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
  <h1>Listing the contents of a directory</h1>

<?php

$dirPath = "/home/matt/images";

function traverseDir( $dir ) {
  echo "<h2>Listing $dir ...</h2>";
  if ( ! ( $handle = opendir( $dir ) ) ) die( "Cannot open $dir." );

$files = array();

while ( $file = readdir( $handle ) ) {
  if ( $file != "." && $file != ".." ) {
    if ( is_dir( $dir . "/" . $file ) ) $file .= "/";
    $files[] = $file;
  }
}

sort( $files );
echo "<ul>";
foreach ( $files as $file ) echo "<li>$file</li>";
echo "</ul>";

foreach ( $files as $file ) {
    if ( substr( $file, -1 ) == "/" ) traverseDir( "$dir/" . substr( $file,
0, -1 ) );
}

closedir( $handle );
}

traverseDir( $dirPath );

?>
</body>
</html>
```

![](img/1ddec54918a4802eb9b4febec3d4e7f6_360_0.png)

## Figure 11-3

## How It Works

The traverseDir() recursive function traverses the whole directory hierarchy under a specified directory. First, the function displays the path of the directory it is currently exploring. Then, it opens the directory with opendir():

```
if ( ! $handle = opendir( $dir ) ) die( "Cannot open $dir." );
```

Next the function sets up a $files array to hold the list of filenames within the directory, then uses readdir() with a while loop to move through each entry in the directory, adding each filename to the array as it goes ("." and ".." are skipped). If a particular filename is a directory, a slash (/) is added to the end of the filename to indicate to the user (and the rest of the function) that the file is in fact a directory:

```
$files = array();

while ( $file = readdir( $handle ) ) {
    if ( $file != "." && $file != ".." ) {
        if ( is_dir( $dir . "/" . $file ) ) $file .= "/";
        $files[] = $file;
    }
}
```

Now the array of filenames is sorted alphabetically to aid readability, and the filenames are displayed in an unordered list:

```
sort( $files );
echo "<ul>";
foreach ( $files as $file ) echo "<li>$file</li>";
echo "</ul>";
```

The last part of the function loops through the array again, looking for any directories (where the filename ends in a slash). If it finds a directory, the function calls itself with the directory path (minus the trailing slash) to explore the contents of the directory:

```
foreach ( $files as $file ) {
    if ( substr( $file, -1 ) == "/" ) traverseDir( "$dir/" . substr( $file,
0, -1 ) );
}
```

Finally, the directory handle is closed:

```
closedir( $handle );
```

The last line of code in the script kicks off the directory traversal, starting with the path to the initial, topmost directory:

```
traverseDir( $dirPath );
```
