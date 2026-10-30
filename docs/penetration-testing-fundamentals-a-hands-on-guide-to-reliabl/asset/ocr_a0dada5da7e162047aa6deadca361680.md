You may have noticed that in Ruby, unlike many other languages (C, C++, Java, C#, etc.), each statement does not need to end with a semicolon.

Variables can also be arrays. Arrays are simple to create in Ruby. Consider the following two array declarations:

```
a = [ 1, 2, 3, 5, 8, 13, 21 ]
b = [ 'tom', 'juan', 'fares' ]
```

The first declares an array named a. That array contains the first few numbers of the famed Fibonacci sequence. The second contains male first names, named b. As you can see, it is fairly easy to create an array of either numbers or strings.

# Operators

Ruby, like all programming and scripting languages, supports the basic mathematical operations of +, -, *, / (add, subtract, multiply, and divide).

There are also additional operators supported by Ruby, and summarized here:

+   - % is the modulus operator and simply means to divide two numbers and only report the remainder. Yes, this is an oversimplification of modulus mathematics, but is sufficient for programming.
+   - ** is how Ruby performs exponents. So, if you have a variable a, and type a**3, that means “a cubed” or a³.
+   - == compares two variables to determine if they are the same. Like many other programming/scripting languages, the single = assigns, and the double == evaluates.
+   - != checks to see if two values are not equal.
+   - < is the traditional less-than operator. And of course, > means greater than, <= means less than or equal to, and >= means greater than or equal to.

You can also combine operators. For example, += means to add two numbers and produce the output. Here is what that looks like:

```
a += 2
```

This is a shorthand way of writing a = a+2.

Here is a basic Ruby script that will perform some essential math operations:

```
# demo basic variables and math

#a global variable initialized to 0
anumber=0

# prompt the user to enter a number
```