
# Break

`break` ends execution of the current `for`, `foreach`, `while`, `do-while` or `switch` structure.

`break` accepts an optional numeric argument which tells it how many nested enclosing structures are to be broken out of.

Here is an example of how the `break` command works with the optional argument:

![](images/00066.jpeg)

# Continue

The `continue` command is similar to the `break` command, but it does not break out of the loop. Instead it continues to the next iteration of the loop. This command can be used inside of `switch` statements as well, but the results of that would be the same using a `break`. You can think of it this way:

`continue` takes you to just before the last closing curly bracket of your structure. If it is a loop, you will go to the next iteration of the loop. For a `switch` statement, when the execution is taken to just before the closing curly bracket, you are essentially being taken to the end of the `switch` statement.

In contrast, `break` will take you to just outside the last closing curly bracket of your code. For a loop that means that you have broken out of the loop. For a `switch` statement, that means that you break out of the `switch` statement and do not go through any of the cases.

As with the `break` statement, `continue` takes an optional argument that tells PHP how many levels of enclosing loops it should skip.

# Return

The `return` command returns program control to the calling module. Execution resumes at the statement following the called module’s invocation.

If you use `return` from within a function, the `return` statement immediately ends execution of the current function, and returns the argument of the `return` as the value of the function call.

Try to abstain from using `return` inside of a file that is included in another file as this is bad practice.

# Include

Files are included based on the file path given or, if none is given, the `include_path` specified. If the file isn't found in the `include_path`, `include` will finally check in the calling script's own directory and the current working directory before failing. The `include` construct will emit a warning if it cannot find a file; this is different behavior from `require`, which will emit a fatal error.

If a path is defined — whether absolute (starting with a drive letter or `\` on Windows, or `/` on Unix/Linux systems) or relative to the current directory (starting with `.` or `..`) — the `include_path` will be ignored altogether. For example, if a filename begins with `../`, the parser will look in the parent directory to find the requested file.

For more information on how PHP handles including files and the include path, see the documentation for `include_path`.

When a file is included, the code it contains inherits the variable scope of the line on which the `include` occurs. Any variables available at that line in the calling file will be available within the called file, from that point forward. However, all functions and classes defined in the included file have the global scope.

# Require

`require` is identical to `include`, except that upon failure, it will return an error and execution of the script will stop.

# Require_once

This is similar to `require`, except `require_once` will check whether the file has been included up to that point. If it has, it will not include it again. Hence, it will require the file to be included only once.

# Include_once

Works exactly like `require_once`, except it will not produce an error.

# Conclusion

This is probably one of the most important chapters in the book. With the concepts and techniques you learned in this chapter you should be able to fully utilize your PHP skills to create amazing applications. The control structures introduced here are the basis of each PHP script you will write and encounter. Combine these with the next chapters about functions and database connections and usage and you will be well on your way to creating advanced and complicated web applications.

## Exercise 1

In this PHP exercise, you will use a conditional statement to determine what gets printed to the browser. Write a script that gets the current month and prints one of the following responses, depending on whether it's August or not:

* It's August, so it's really hot.
* Not August, so at least not in the peak of the heat.

Hint: the function to get the current month is `date('F', time())` for the month's full name.

## Exercise 2

In this PHP exercise, you will put all the loops through their paces. Write a script that will print the following to the browser:

```text
abc abc abc abc abc abc abc abc abc
xyz xyz xyz xyz xyz xyz xyz xyz xyz
1 2 3 4 5 6 7 8 9
1. Item A
2. Item B
3. Item C
4. Item D
5. Item E
6. Item F
```

Create the 'abc' row with a `while` loop, the 'xyz' row with a `do-while` loop, and the last two sections with `for` loops. Remember to include HTML and source code line breaks in your output. No arrays allowed in this solution.

## Exercise 3

Loops are very useful in creating lists and tables. In this PHP exercise, you will use a loop to create a list of equations for squares.

Using a `for` loop, write a script that will send to the browser a list of squares for the numbers 1-12.

Use the format, "1 * 1 = 1", and be sure to include code to print each formula on a different line.

# Chapter Five – Functions

## Introduction

Functions in PHP, like in many other languages, give you the power to create extremely versatile and reusable code. Imagine the following situations. You are writing a script and you want to perform a certain set of actions. Later on, you need to perform the same set of actions, but you have to change a variable to another variable, for example. Wouldn’t it be convenient to be able to separate those actions out, and just replace the variable as needed? This is where functions come in.

In PHP, functions are broken up into user defined functions and pre-defined functions. User defined functions are custom functions that you create inside of your code. Pre-defined functions are the functions that PHP comes with.

## User Defined Functions

A function is basically a block of statements that can be used repeatedly in a program that will only be executed when you call it. Functions can take parameters that you predefine or they can have no parameters. Let’s look at the syntax for a function in PHP.

![](images/00067.jpeg)

The function name is defined by you. It is a good idea to give the function a name that reflects what the function will do. The naming convention for functions is pretty much the same as the naming convention for variables (functions can start with letters or underscores but not numbers). An important thing to note is that function names are not case-sensitive. Therefore, the following code will produce an error:

![](images/00068.jpeg)

If you want to call the function you created, you just write the name of the function followed by a pair of parentheses. If your function takes parameters, you put the corresponding variable or variables in between the parentheses.

![](images/00069.jpeg)

### Function Arguments

Information can be passed to functions through arguments. An argument is just like a variable.

Arguments are specified after the function name, inside the parentheses. You can add as many arguments as you want, just separate them with a comma. Let’s modify the previous example to include a name:

![](images/00070.jpeg)

Function arguments can take default values. For example, if you call the function without specifying an argument, the function will assume the default argument value;

![](images/00071.jpeg)

### Return values

Often times, you want the function to return a specific value. To do this, you use the `return` statement:

![](images/00072.jpeg)

### Variable Scope

When dealing with variables, it is important to know what their scope is (or the context in which they are defined). For example:

![](images/00073.jpeg)
