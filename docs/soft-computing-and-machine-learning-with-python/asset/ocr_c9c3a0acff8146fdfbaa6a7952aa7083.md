# Documenting Function Interfaces

Python has a preferred way to document the purpose and usage of your functions. If the first line of a function body is a string constant, that string constant is saved along with the function as the documentation string. This string can be retrieved by using an expression of the form f.__doc__, where f is the function name.

Here's an example of a function with a documentation string.

```
>>> pythag(a, b):
    """Returns the hypotenuse of a right triangle with sides a and b.
    """
    return (a*a + b*b)**0.5
...
>>> pythag(3,4)
5.0
>>> pythag(1,1)
1.414213562730951
>>> print pythag.__doc__
    Returns the hypotenuse of a right triangle with sides a and b.
```

# USING PYTHON MODULES

Once you start building programs that are more than a few lines long, it's critical to apply this overarching principle to programming design:

# Important

Divide and conquer.

In other words, rather than build your program as one large blob of Python statements, divide it into logical pieces, and divide the pieces into smaller pieces, until the pieces are small enough to understand.

Python has many tools to help you divide and conquer. In Section 8, "def: Defining functions", we learned how to package up a group of statements into a function, and how to call that function and retrieve the result.