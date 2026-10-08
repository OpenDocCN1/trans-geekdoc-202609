# Core PHP Programming

The getlastmod function returns the date the executing script was last modified. The date is returned as a number of seconds since January 1, 1970. This is the same as calling filetime on the current file.

```
<?php
printf("This script was last modified %s",
    date("m/d/y", getlastmod()));
?>
```

# integer getmyinode()

The getmyinode function returns the inode of the executing script. Under Windows, zero is always returned. You can get the inode of any file using fileinode.

```
<?php
print(getmyinode());
?>
```

# integer getmypid()

The getmypid function returns the process identifier of the PHP engine. It may not return anything under Windows 98.

```
<?php
print(getmypid());
?>
```

# integer getmyuid()

The getmyuid function returns the user identifier of the owner of the script.

```
<?php
    print(getmyuid());
?>
```

# array getrusage(integer children)

The getrusage function is a wrapper for the C function of the same name. It reports information about the resources used by the calling process. If thechildren argument is I,