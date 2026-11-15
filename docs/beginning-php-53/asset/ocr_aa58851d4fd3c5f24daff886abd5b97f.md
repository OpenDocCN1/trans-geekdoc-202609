To use `fseek()`, pass the handle of the open file, and an integer offset. The file pointer moves to the specified number of characters from the start of the file (use zero to move the pointer to the first character). For example, the following code moves the pointer to the eighth character in the file (that is, seven characters after the first character) and displays the next five characters from that point:

```
// hello_world.txt contains the characters "Hello, world!"
$handle = fopen( "hello_world.txt", "r" );
fseek( $handle, 7 );
echo fread( $handle, 5 ); // Displays "world"
fclose( $handle );
```

To specify how the offset is calculated, you can add a third optional argument containing one of the following constants:

+   - SEEK_SET — Sets the pointer to the beginning of the file plus the specified offset (the default setting)
+   - SEEK_CUR — Sets the pointer to the current position plus the specified offset
+   - SEEK_END — Sets the pointer to the end of the file plus the specified offset (use with a negative offset)

fseek() returns 0 if the pointer was successfully positioned, or -1 if there was a problem.

> You can't use this function with files on remote hosts opened via HTTP or FTP (for example, fopen( "http://www.example.com/" )).

If you want to move the pointer back to the start of the file (a common occurrence), a handy shortcut is the rewind() function. The following two lines of code both do the same thing:

```
fseek( $handle, 0 );
rewind( $handle );
```

The ftell() function takes a file handle and returns the current offset (in characters) of the corresponding file pointer from the start of the file. For example:

```
$offset = ftell( $handle );
```

As you saw earlier, the fpassthru() function outputs file data from the current file position onward. If you have already read data from an open file but want to output the file's entire contents, call rewind() first.

# Working with File Permissions

File system permissions determine what different users can do with each file and directory in the file system. For example, whereas one user might have permission to read and write to a file, another user may only be allowed to read the file. A third user might not even be allowed to do that.