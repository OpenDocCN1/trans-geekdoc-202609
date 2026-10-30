
## Functions as Arguments

Consider the code that draws a radial pattern of 10 squares:

```
for count in range(10):
    square(70)
    left(36)
```

As you saw in Chapter 4, you can use code such as this to draw a pattern that uses triangles, hexagons, or other regular polygons. At this point, you should be asking yourself this: what must change in this pattern of code to use a different type of polygon in the drawing? Obviously, it’s just the name of the function, which in this particular instance happens to be square. If you substitute the name hexagon, the code calls the function to draw hexagons instead.

Unfortunately, you must rewrite the same loop each time you want to draw the pattern. You would like to capture this common pattern of code in a single function. The only thing that would vary from call to call of this function would be the name of the function used to draw the particular type of polygon. If you could pass this function as an argument to a pattern-drawing function, you’d be all set.

Assume that your new pattern-drawing function is named radialPattern. You could call it to draw a square-based pattern and a hexagon-based pattern in the following manner:

```
radialPattern(square)
radialPattern(hexagon)
```

Fortunately, Python is one of the few programming languages that allow you to do this. Here is the code for the definition of the radialPattern function:

```
def radialPattern(polygonFunction):
    """Draws a series of polygons by rotating around a center point."""
    for count in range(10):
        polygonFunction(70)
        left(36)
```

Note that the argument name, polygonFunction in this definition, refers to the function that the caller passes. This function can be square, hexagon, or any function of one argument that draws a polygon.

By now, you should be thinking to yourself, “Hey, this radialPattern function is still not general enough. It always draws a pattern with 10 polygons of length 70. I want to provide a function that can draw any number of polygons of any length.” You’d be right to think that, and in the exercises, you’ll have an opportunity to act on that thought.

## Building Functions with lambda Expressions

After you get over the shock of learning that you can pass functions as arguments to other functions, you need to learn another related idea.

You saw earlier that you can define any function to draw a particular type of regular polygon by calling the more general function regularPolygon. The arguments to this function are the length of a side and the number of sides. When you want to draw a new type of polygon, you just define a function for it in this manner and call that function.

However, there are lots of regular polygons besides the standard ones with three, four, five, six, and eight sides. Defining a new function for each one can get rather tedious, when you could simply call the regularPolygon function to perform the desired task. But you can’t pass this function as an argument to the radialPattern function. That’s because regularPolygon expects two arguments, whereas radialPattern’s function argument expects only one argument—the length of a side—when it is called.

Fortunately, Python provides a nice way around this problem. When you defined the square function, you essentially “wrapped” a call of regularPolygon with two arguments inside of a function, square, that expects one argument. Python includes a special form called a lambda expression that allows you to do just that, without going to the trouble of defining a named function. The form of a Python lambda expression follows:

```
lambda arguments: expression
```

Suppose, for example, that you want to draw a 16-sided figure. The following lambda expression builds a new function that would do the trick:

```
>>> lambda length: regularPolygon(length, 16)
<function <lambda> at 0x102b69ef0>
```

This lambda expression is evaluated in a shell session to show you that a function is built and returned. This is an anonymous function of one argument, the length, which is just what you need for radialPattern. When your new function is eventually called, it calls regularPolygon to draw a regular polygon with 16 sides. Here is a sample call of your new function, which draws a 16-sided polygon of length 70:

```
>>> (lambda length: regularPolygon(length, 16))(70)
```

Pass this lambda expression as an argument to the radialPattern function to draw the pattern with a 16-sided polygon:

```
>>> radialPattern(lambda length: regularPolygon(length, 16))
```

To change the particular type of polygon, you only have to change the number of sides.

## MODULES AS LIBRARIES OF FUNCTIONS

By now you will have written several related functions for drawing geometric shapes and perhaps a few patterns that use these shapes. You should continue to test your functions in short tester programs. But as the number of functions grows, you need a better place to keep them, where you can access them just like you access Python’s library functions `math.sqrt` and `random.randint`.

After you test each function and verify that it’s working as expected, you should place it in an appropriate module or library file. Call your first module `mygeometry`. You create this file by opening a new file window in IDLE. Immediately save this file with the name `mygeometry.py`. Then add a docstring at the top of the file that summarizes the purpose of this module. At that point, you can start to paste in each function definition as it becomes available.

Every so often, you should import your new module into one of the tester programs you’ve used and run your functions as module functions. If you use the form

```
moduleName.functionName(argumentList)
```

when calling your functions, you can be sure that they will be available for any programmers who eventually use your module.

## MATH TOPIC: GRAPHING FUNCTIONS

In this section, you learn how you can use functions in a Python program to express functions as understood in mathematics.

### Functions in Mathematics

There are several ways to express a function in mathematics. In algebra, a function $f$ expresses a relationship between two variables, $x$ and $y$. In shorthand, this relationship is stated as the equation

$y = f(x)$

In this equation, $f$ is the function, $y$ is the *dependent variable*, and $x$ is the *independent variable*. This means that, for the function $f$, as you change the value of $x$, the value of $y$ also changes. The set of all values that $x$ can take on is called the function’s *domain*, and the set of all values that $y$ can take on is called the function’s *range*.

A function f expresses a rule for mapping the values of its domain into the corresponding values in its range. For example, take the function that expresses the square of a given number x, also known as x². Subsets of this function’s domain and range are shown in Table 5.1.

Table 5.1 A Subset of the Domain and Range of y = x²

| x (Domain) | y (Range) |
|---|---|
|1|1|
|2|4|
|3|9|
|4|16|

In each row of this table, you can see that the value of y is the square of the value of x.

To state the rule for a function f, you must expand this function into an expression that uses x to compute the corresponding value of y. This expression can consist of operators and applications of other functions to the value of x. For example, you can expand the function f(x) to the expression x * x or x ** 2 to state the rule for expressing the square of x. Thus, for this case, the equation y = f(x) expands to the equation y = x * x (or y = x ** 2, if you use the exponentiation operator).

Another way to express a function is to draw a graph that plots a given subset of its domain. Each point (x, y) on this plot represents the solution to the equation y = f(x) for a given value of x. The values of x are plotted along the x-axis, and the values of y are plotted along the y-axis. Figure 5.1 shows the graphs of two equations, y = 2 * x + 10 and y = x ** 2 - 10 * x + 3. The first equation is also called a linear equation, and the second equation is also called a quadratic equation.
