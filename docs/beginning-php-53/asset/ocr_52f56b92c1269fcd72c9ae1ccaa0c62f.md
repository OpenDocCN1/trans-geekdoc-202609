```
echo "I can write to myfile.txt";
}
if ( is_executable( "myfile.txt" ) {
    echo "I can execute myfile.txt";
}
```

You can also use the fileperms() function to return an integer representing the permissions that are set on a file or directory. For example, to print the octal value of the permissions on a file you might use:

```
chmod( "myfile.txt", 0644 );
echo substr( sprintf( "%o", fileperms( "myfile.txt" ) ), -4 ); // Displays
"0644"
```

(The call to substr() is used to return just the last four digits, because the other octal digits in the returned value aren't relevant.)

# Copying, Renaming, and Deleting Files

PHP also lets you copy, rename, and delete files. The functions to perform these operations are copy(), rename(), and unlink(), respectively.

The copy() function takes two string arguments: the first argument is the path to the file to copy, and the second argument is the path to copy it to. It returns true if the file was successfully copied, or false if there was a problem copying the file. The following example copies the source file copyme.txt to the destination file copied.txt in the same folder:

```
copy( "./copyme.txt", "./copied.txt" );
```

The rename() function is used to rename (or move) a file. It works in much the same way as copy(). For example, to rename a file within a folder you could use:

```
rename( "./address.dat", "./address.backup" );
```

To move a file to a different folder, you might use:

```
rename( "/home/joe/myfile.txt", "/home/joe/archives/myfile.txt" );
```

The unlink() function lets you delete files from the server. To use it, pass the filename of the file you want to delete. For example, if you wanted to say adiós to the file trash.txt in the current directory, you could write:

```
unlink( "./trash.txt" );
```

copy(), rename(), and unlink() raise warning-level errors if the file or directory in question can't be found. Make sure the file or directory exists first (for example, by using file_exists()) to avoid such errors.