Most file system calls, which return the details of the file, are very expensive. To avoid this performance overhead, PHP caches the details of the file. This cache can be cleared by calling the clearstatcache() function.

There is a set of functions which indicate the type of the file. These are:

```
boolean is_dir(string filename)
boolean is_executable(string filename)
boolean is_file(string filename)
boolean is_link(string filename)
```

These functions return true if the named file is a directory, an executable file, a regular file, or a symbolic link, respectively:

```
boolean is_readable(string filename)
boolean is_writable(string filename)
```

The functions is_readable() and is_writable() can be used to find if the PHP script has permissions to read from or write to the named file.

We use some of these functions in the Online Storage Application, later in the chapter.

# Directories

Apart from manipulating individual files, PHP provides functions for handling directories. PHP's directory APIs can be used to create and delete new directories, and to read the contents of a directory:

```
int chdir(string directory)
```

The current directory of the PHP process can be set by the chdir() function. If you are accessing a number of files in a directory, then you may want to change the current directory to point to the directory containing these files:

```
string getcwd()
```

You can get the current directory using the getcwd() function. It returns the current working directory:

```
int opendir(string path)
```

For reading the contents of a directory, you first need to open the directory. The opendir() function opens the directory specified by path. It returns a directory handle on success, which can be used to refer to the open directory in subsequent function calls:

```
string readdir(int dir)
```