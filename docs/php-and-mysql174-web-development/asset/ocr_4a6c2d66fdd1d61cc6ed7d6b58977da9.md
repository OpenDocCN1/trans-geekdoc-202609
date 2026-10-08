Chapter 2 Storing and Retrieving Data

# fopen() to Open a File

Assume that you want to write a customer order to Bob's order file. You can open this file for writing with the following:

```
$fp = fopen("document_root/../orders/orders.txt", 'w');
```

When fopen() is called, it expects two, three, or four parameters. Usually, you use two, as shown in this code line.

The first parameter should be the file you want to open. You can specify a path to this file, as in the preceding code; here, the orders.txt file is in the orders directory. We used the PHP built-in variable $_SERVER['DOCUMENT_ROOT'] but with the cumbersome full names for form variables, we assigned a shorter name.

This variable points at the base of the document tree on our web server. This directory is the document tree, for security reasons. In this case, we do not want this file to be accessible except through the interface that we provide. This path is called a *relative path* because it describes a position in the file system relative to the document root.

With the short names given for variable, you need the following line at the start of your script

```
$document_root = $_SERVER['DOCUMENT_ROOT'];
```

to copy the contents of the long-style variable to the short-style name.

You could also specify an *absolute path* to the file. This is the path from the root directory (/ on a Unix system and c:\ on a Windows system). Our path could be something like /data/orders. If no path is specified, the file will be created or looked for in the same directory as the script itself. The directory used will vary if you are running PHP through some kind of CGI wrapper and depends on your server configuration.

In a Unix environment, use forward slashes (/) in directory paths. If you are using a Windows platform, you can use forward (/) or backslashes (\). If you use backslashes, they must be escaped (as a special character) for fopen() to understand them properly. To escape a character, you simply add an additional backslash in front of it, as shown in the following:

```
$fp = fopen("document_root\\orders\\orders.txt", 'w');
```

Very few people use paths within PHP because it makes the code work only in Windows environments. If you use forward slashes, you can often move your code between Windows and Unix without alteration.

The second fopen() parameter is the file mode, which should be a string. This string specifies what you want to do with the file. In this case, we are passing 'w' to fopen(); this means "open the file for writing." A summary of file modes is shown in Table 2.1.