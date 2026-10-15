The first parameter is the file handle; the second one is the desired kind of locking to be used. The following options are available:

+   - LOCK_EX—Exclusive lock for writing
+   - LOCK_NB—Nonblocking lock
+   - LOCK_SH—Shared lock for reading
+   - LOCK_UN—Releasing a lock

The preceding code contains an updated version of the custom file_put_contents() function from the previous phrase, this time using an exclusive lock.

# Using Relative Paths
for File Access

```
dirname(__FILE__);
basename(__FILE__);
```

Usually, files are opened (or searched) relative to the path of the document. If you are using PHP as an ISAPI module under Windows, the location of php4ts.dll or php5ts.dll may be relevant. To be sure that you are searching to the current scripts’ path, you can use a two-step approach:

+   - The constant __FILE__ contains the full path of the current script
+   - The function dirname() determines the directory name portion of a path