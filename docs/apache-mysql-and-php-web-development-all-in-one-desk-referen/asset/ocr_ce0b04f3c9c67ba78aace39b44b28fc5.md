The `cd` command takes as a single parameter the directory you want to switch to. (On both Linux and Windows, you can use the forward slash, as usual.) The `pwd` command returns a string representing the current directory; it doesn’t actually print out the string. To print out the string, put the `pwd` command in quotes and print it with `puts`. Or save it to a variable like this:

```
set mydir [pwd]
```

In interactive mode (but not in a program), you can also use many of the usual shell commands, depending on your operating system. Here are some examples:

+   ♦ dir: This command displays a directory listing. (Windows)
+   ♦ ls: This command displays a directory listing. (Linux)
+   ♦ copy: This command copies a file. (Windows)
+   ♦ cp: This command copies a file. (Linux)

![](bbox=[0.12, 0.42, 0.22, 0.49])

You can include all the usual options, such as `dir /s` on Windows or `ls -ltr` on Linux. Because all these commands are present, you can use `tclsh` as your shell, rather than the usual shell, if you prefer.

# Creating File Links

![](bbox=[0.11, 0.56, 0.22, 0.64])

For you advanced users, Tcl includes a `link` command that lets you inspect or create a symbolic or hard link. This is something most Linux users are aware of; however, most people don’t realize that links also exist on Windows 2000 and XP. But on these Windows operating systems, you can have only symbolic links for directories and hard links for files.

On Linux, to create a link called `file2` to an existing file called `file1`, use this line:

```
file link file2 file1
```

This results in a symbolic link, where the new file effectively points to the original file. The default is to create a symbolic link; however, you can be redundant and specify `-symbolic` as an option like so:

```
file link -symbolic file2 file1
```

Or, you can create a hard link, whereby you have two separate filenames aliased to the same file structure on the disk, like so:

```
file link -hard test2.txt test.txt
```