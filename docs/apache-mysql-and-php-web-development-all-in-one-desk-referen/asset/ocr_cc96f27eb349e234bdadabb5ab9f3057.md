# # Running Types of Applications

The idea of dynamic content opens a world of possibilities. No longer do you have to type in every last HTML page and say, "That's it! This is what you get!" Instead, you can build Web pages on the fly, customized for the current situation. In the sections that follow, I provide a general idea of just a few of the many things you can do with PHP.

# ## Creating math and engineering applications

The PHP language includes a set of functions serving mathematical purposes. These functions include the BCMath category of functions, which provide arbitrary-precision mathematics. If you're a scientist or an engineer, or if you work with such people, you can appreciate the importance of this. Normally when you use a computer to perform math, you end up with size limitations. For example, an integer has a limit on how big it can be, and floating point numbers (which are numbers containing a decimal point) have a limit on how many significant digits they can contain. But using the BCMath library, you have unlimited precision. (Well, okay, theoretically you could have a number with so many millions of digits that you eat up all the memory in the computer, but for most work, you shouldn't have any problems or limitations.)

![](bbox=[0.045, 0.495, 0.135, 0.545])

You can find out more about the BCMath library by visiting www.php.net/bc.

PHP includes a set of more traditional mathematical functions in its Math category. This category includes too many functions for me to list here, but these functions include such familiar items as cos (cosine), sin (sine), sinh (hyperbolic sine — those elusive things that most calc classes skip), log (natural logarithm), min and max (for minimum and maximum), rand (for random numbers), and so on.

![](bbox=[0.045, 0.66, 0.135, 0.71])

You can explore the traditional math routines by visiting www.php.net/math.

For scientific and engineering (and other) applications, you also have a library of graphics routines that I mention earlier in this chapter. In addition, you have access to various third-party libraries (some free, some not) that provide additional mathematical features. For example, one free library called PEAR (which is standard on many PHP installations) includes a library that handles complex numbers.