# # Setting the include path

To find the file that you include (or require), you must either put the file in the same directory as the file doing the including, or provide a full path to the file, as in /home/jezebel/html_ files/myphpstuff.php. However, if you move your site to a different host with a differently organized file system, coding an absolute path can be a problem.

```
include_path = ".:/php/includes"
```

Or look like this for Windows:

```
include_path = ".;c:\php\includes"
```

For the Linux/Unix one, add your path inside the string, separating the items with a colon, like so:

```
include_path = ".:/php/includes:/home/ jezebel/html_files"
```

A better way than coding absolute paths into your files is to use the PHP system include path. PHP maintains a set of directories that it looks in for the included files. If you add your directory to this path, you don’t need to use any paths in the names of the files you include. How do you set this secret wonder known as an include path? You can do it two ways. If you have access to the php.ini file (which you might not if you’re using a third-party hosting service), you can set it in the php.ini file. Open the php.ini file and search for a line that starts with include_path = . (It might start with a semicolon, which means it’s commented out. Remove the semicolon.) The line might look like this for Linux/Unix:

For Windows, separate the items with a semicolon and use backslashes:

```
include_path = ".;c:\php\includes;c:\ phpfiles\jezebel"
```

(Notice that you don’t double up the backslashes.)

Finally, if you don’t have access to the php.ini file, you can add a line to your .php file that sets the include path, like so:

```
ini_set('include_path','/home/ jezebel/ html_files ');
```

You can also use variable names in your require and include statements:

```
$headerfile = "myfunctions.php";
require $headerfile;
```

This means that if you’re really brave and writing some seriously complex code, you can construct different filenames based on different situations. For example, say that you’re writing a set of “helper” functions that do some database work for you, and you write different forms of these functions for different database systems. You can construct the name of the correct file to include or require on the fly, store the name in a variable, and then require or include the file using the variable name. Or, you can conditionally include or require your files, as I discuss in the section “Conditionally requiring and including,” later in this chapter.