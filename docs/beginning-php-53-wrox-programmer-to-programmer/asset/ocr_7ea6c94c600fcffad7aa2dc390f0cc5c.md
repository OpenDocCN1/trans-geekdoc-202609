```
sin(30) = 0.5
cos(30) = 0.866025403784
tan(30) = 0.57735026919
```

In the real world, variable function is often used to dynamically select a function to execute on the fly, depending on, for example, user input or other external factors. You can also use it to write code that calls user-created callback functions or event handler functions. (You create functions in Chapter 15 and some event handlers in Chapter 19.)

# Writing Your Own Functions

If you've learned that functions are useful beasts that let you encapsulate and reuse code, and you've explored how to call functions in PHP. Here's where the fun really begins, the fun as you get to create your functions.

Defining a function is really easy — just use the following syntax:

```
function myFunc() {
  // (do stuff here)
}
```

In other words, you write the word function, followed by the name of the function you want to create, followed by parentheses. Next, put your function's code between curly brackets ({}).

Here's a trivial example:

```
function hello() {
  echo "Hello, world!<br/>";
}
```

```
// Displays "Hello, world!"
hello();
```

As you can see, this script defines a function, hello(), that displays the string "Hello, world!" After the function definition, the script calls the hello() function to display the output.

> Note that the code within the hello() is only run when the function is called, not when the function itself is called. Simply creating a function does not run the code within the function; you have to explicitly call the function in order to run its code.

# Defining Parameters

As you know, functions can optionally accept one or more arguments, which are passed to the function. To tell PHP that you want your function to accept arguments, you specify one or more corresponding parameters when you define your function. A parameter is a variable that holds the value passed to it when the function is called.