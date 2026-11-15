# "include_path"

There is a second interesting setting in php.ini: Under include_path, you can define any paths in which include() and require() statements are automatically looked up. Multiple paths are separated with a colon in Linux and with a semicolon in Windows. Here you can see the Linux version:

```
include_path = ".:/php/includes"
```

And here is the Windows version:

```
include_path = ";c:\php\includes"
```

The PATH_SEPARATOR constant contains the separator depending on the operating system. This means that you do not have to worry about this detail, but simply write the following:

```
include_path = "." . PATH_SEPARATOR . "c:\php\includes"
```

You can also change the include_path setting for the current script. There are two different ways to do this:

+   ■ The set_include_path()function :
+   set_include_path("/includes");
+   
+   ■ The ini_set()function to change any setting in php.ini:
+   ini_set("include_path", "/includes");

# 4.2 Output with PHP

To really get started with PHP, you need to be able to test how the syntax and programming constructs work. To do this, you should be able to output data. PHP has two language constructs12 for output:

+   ■ The echo statement:
+   
+   <?php
+   echo "output";
+   ?>

+   ■ The print statement:
+   
+   <?php
+   print "Output";
+   ?>

12 A language construct (statement) is a PHP instruction. In this book, we distinguish between language constructs (synonymous: statements, language instructions) and functions. More on this follows in Chapter 6.