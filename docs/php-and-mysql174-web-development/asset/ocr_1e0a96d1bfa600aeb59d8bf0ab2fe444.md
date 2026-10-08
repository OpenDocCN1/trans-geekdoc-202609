# Chapter 5 Reusing Code and Writing Functions

You can provide values for optional parameters, or you can choose to ignore them and the default value will be used. Note, however, that a function with more than one optional parameter, you can only leave out parameters from the right. For example, when using fopen(), you can leave out context or you leave out use_include_path and context; however, you cannot leave out use_include_path but provide context.

After reading the prototype for this function, you know that the following code fragment is a valid call to fopen():

```
$name = 'myfile.txt';
$fopenmode = 'r';
$fp = fopen($name, $fopenmode);
```

This code calls the function named fopen(). The value returned by the function will be stored in the variable $fp. For this example, we chose to pass the function to the variable $name containing a string representing the file we want to open and a variable $fopenmode containing a string representing the mode in which we want to open the file.
We chose not to provide the third and fourth parameters.

# Calling an Undefined Function

If you attempt to call a function that does not exist, you will get an error message, as shown in Figure 5.3.

![](bbox=[0.118, 0.513, 0.603, 0.77])

Figure 5.3 This error message is the result of calling a function that does not exist

The error messages that PHP gives are usually useful. The one in the figure tells you exactly which file the error occurred, in which line of the script it occurred, and the name of the function you attempted to call. This information should make it fairly easy to find and correct the problem.