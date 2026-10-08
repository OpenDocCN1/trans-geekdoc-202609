Core PHP Programming

```
{
  print("log.txt not changed to editors group");
}?>
```

# boolean chmod(string filename, integer mode)

The chmod function sets the UNIX permissions for the given file based on the mode supplied. The mode is interpreted like the UNIX shell command, except that it is not converted to octal. Unless prefixed with a 0, mode is treated as a decimal number.

Under UNIX, three octal numbers specify privileges for owner, group, and others, respectively. The modes may be added in order to combine different privileges. For example, to make a file readable and executable, use mode 5. Refer to Table 8.3. You may also wish to refer to the man page for chmod on UNIX system.

Under Windows, chmod has limited use. The modes described in Table 8.4 are defined by Microsoft. They may be combined with the bitwise-or (|), but in practice only write permissions have any meaning. All files in Windows are readable and the file extension determines determines whether the file will execute.

Table 8.3. File Modes

| Mode | Description |
|---|---|
| 0 | No access |
| 1 | Execute |
| 2 | Write |
| 4 | Read |

Table 8.4. Windows File Modes

| Mode | Description |
|---|---|
| 0000400 | read permission, owner |
| 0000200 | write permission, owner |
| 0000100 | execute/search permission, owner |

This function is part of a group of three functions that share similar information about files. The other two are chgrp chown. The fileperms function will tell you the file's current modes.

```
<?
/
 ** allow everyone to read and write to file
 ** when running PHP under UNIX
 */
```

IT-SC book

129