```
}
for ($i=0; $i < count($fileArray); $i++) {
    printf("%s<br>", $fileArray[$i]);
}
?>
</body>
</html>
```

# Writing to Files

The functions fputs() and fwrite() can be used for writing to files. These two functions are identical:

```
int fputs(int fp, string stringtoWrite [,int length]);
int fwrite(int fp, string stringtoWrite [,int length]);
```

The first argument fp is the file handle of the file to be written to. The second argument stringToWrite is the string to be written to the file. The third optional argument is the number of characters from the string to write. If this last parameter is not included then the entire string will be written. The return value is true on success, or false on failure.

# Navigating within Files

When reading from a file, the current position indicator within the file moves to the next unread character. PHP provides a set of functions for changing the current position indicator within the file:

```
int rewind(int fp)
```

The rewind() function sets the current position indicator to the beginning of the file. The argument fp is the file pointer of the file. The function returns true on success, or false on failure:

```
int fseek(int fp, int offset [, int whence])
```

The fseek() function can be used to set the current position indicator to any position in the file. The argument fp is the file handle of the file. The third argument whence can be any one of the following:

+   - SEEK_SET
+     Sets position indicator to offset bytes.
+   - SEEK_CUR
+     Sets position indicator to current location plus offset.
+   - SEEK_END
+     Sets position indicator to end-of-file plus offset. Note that a negative value can be specified as offset.

The default value of the whence argument is SEEK_SET. The fseek() function returns true on success, false on failure:

```
int ftell(int fp)
```