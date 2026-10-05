
# A Python 2.7 Programming Tutorial 213

```
... return 1
... else:
... return fact(n-1)
...
>>> for i in range(5):
... print i, fact(i)
```

```
0 1
1 1
2 2
3 6
4 24
```

```
>>> fact(44)
26582175174884476804362581101146158903196385280000000
```

# Function Argument List Features

The general form of a def shown in Section 8, “def: Defining functions” is over-simplified. In general, the argument list of a function is a sequence of four kinds of arguments:

- 1. If the argument is just a name, it is called a positional argument. There can be any number of positional arguments, including zero.
- 2. You can supply a default value for the argument using the form “name=value”. Such arguments are called keyword arguments. See Section 8.3, “Keyword arguments”. A function can have any number of keyword arguments, including zero.

All keyword arguments must follow any positional arguments in the argument list.

- 3. Sometimes it is convenient to write a function that can accept any number of positional arguments. To this, use an argument of the form:
- 4. * name
A function may have only one such argument, and it must follow any positional or keyword arguments. For more information about this feature, see Section 8.4, “Extra positional arguments”.
- 5. Sometimes it is also convenient to write a function that can accept any number of keyword arguments, not just the specific keyword arguments. To this, use an argument of this form:
- 6. ** name
If a function has an argument of this form, it must be the last item in the argument list. For more information about this feature, see Section 8.5, “Extra keyword arguments”.

# Keyword Arguments

If you want to make some of the arguments to your function optional, you must supply a default value. In the argument list, this looks like “name=value”.

Here’s an example of a function with one argument that has a default value. If you call it with no arguments, the name has the string value ‘bleah’ inside the function. If you call it with an argument, the name has the value you supply.

```
>>> def report(mood='bleah'):
...     print("My mood today is", mood)
... 
>>> report()
My mood today is bleah
>>> report('hyper')
My mood today is hyper
```

If your function has multiple arguments, and the caller supplies multiple parameters, here is how they are matched up:

- The function must supply at least as many parameters as the function has positional arguments.
- If the caller supplies more positional parameters than the function has positional arguments, parameters are matched with keyword arguments according to their position.
- Here are some examples showing how this works.

```
>>> def f(a, b="green", c=3.5):
...     print a, b, c
... 
>>> f()
Traceback (most recent call last):
  File "stdin>", line 1, in ?
TypeError: f() takes at least 1 argument (0 given)
>>> f(47)
47 green 3.5
>>> f(47, 48)
```

```
47 48 3.5
>>> f(47, 48, 29)
47 48 29
>>> f(47, 48, 49, 50)
Traceback (most recent call last):
File "stdin>", line 1, in =
TypeError: f() takes at most 3 arguments (4)
>>>
```

Here is another feature: the caller of a function can supply what are called keyword parameters of the form "name=value". If the function has an argument with a matching keyword, that argument will be set to value.

- If the caller's caller supplies both positional and keyword parameters, all positional parameters must precede all keyword parameters.
- Keyword parameters may occur in any order.
- Here are some examples of calling a function with keyword parameters.

```
>>> g(p0, p1, k0="K-0", k1="K-1")
...    print p0, p1, k0
>>> g(33,44)
33 44 K-0 K-1
>>> g(33,44,"K-9","beep")
33 44 K-9 beep
>>> g(55,66,k1="whirr")
55 66 K-0 whirr
>>> g(7,8,k0="click",k1="clank")
7 8 clank clank
>>>
```

# Extra Positional Arguments

You can declare your function in such a way that it will accept any of positional parameters. To do this, use an argument of the form "*name" in your argument list.

- If you use this special argument, it must follow all the positional and keyword parameters in the list.
- When the function is called, this name will be bound to a tuple containing any positional parameters that the caller supplied, and over above parameters that corresponded to other parameters.

Here is an example of such a function.

```
>>> def h(i, j=-99, *extras):
... print i, j, extras
...
>>> h(0)
0 -99 ()
>>> h(1,2)
1 2 ()
>>> h(3,4,5,6,7,8,9)
3 4 (5, 6, 7, 8, 9)
>>>
```

# Extra Keyword Arguments

You can declare your function in such a way that it can accept any number of keyword parameters, in addition to any keyword arguments you declare.

To do this, place an argument of the form “**name” last in your argument list.

When the function is called, that name is bound to a dictionary that contains any keyword-type parameters that are passed in that have names that don't match your function’s keyword-type arguments. In that dictionary, the keys are the names used by the caller, and the values are the values that the caller passed.

Here’s an example.

```
>>> def k(p0, p1, nickname='Noman', *extras, **extraKeys):
... print p0, p1, nickname, extras, extraKeys
>>> k(1,2,3)
1 2 3 () {}
>>> k(4,5)
4 5 Noman () {}
>>> k(6, 7, hobby='sleeping', nickname='Sleepy', hatColor='green')
6 7 Sleepy () {'hatColor': 'green', 'hobby': 'sleeping'}
>>> k(33, 44, 55, 66, 77, hometown='McDonald', eyes='purple')
33 44 55 (66, 77) {'hometown': 'McDonald', 'eyes': 'purple'}
>>>
```

# Documenting Function Interfaces

Python has a preferred way to document the purpose and usage of your functions. If the first line of a function body is a string constant, that string constant is saved along with the function as the documentation string. This string can be retrieved by using an expression of the form f.__doc__, where f is the function name.

Here's an example of a function with a documentation string.

```python
>>> pythag(a, b):
    """Returns the hypotenuse of a right triangle with sides a and b.
    """
    return (a*a + b*b)**0.5
...
>>> pythag(3,4)
5.0
>>> pythag(1,1)
1.4142135623730951
>>> pythag.__doc__
    'Returns the hypotenuse of a right triangle with sides a and b.'
```

# USING MODULES

Once you start building programs that are more than a few long, it's critical to apply this overarching principle to programming design:

Divide and conquer. In other words, rather than build your program as one large blob of statements, divide it into logical pieces, and divide the pieces into smaller pieces, until the pieces are small enough to understand.

Python has many tools to help you divide and conquer. In Section 8, "def: Defining functions", we learned how to package up a group of statements into a function, and how to call that function and retrieve the result.

Soft Computing and Machine Learning with Python

Way back in Section 2.3, “More mathematical operations”, we got our first look at another important tool, Python’s module system. Python does not have a built-in function to compute square roots, but there is a built-in module math that includes a function sqrt() that computes square roots.

In general, a module is a package of functions and variables that you can import and use in your programs. Python comes with a large variety of modules, and you can also create your own. Let’s look at Python’s module system in detail.

- In Section 9.1, “Importing items from modules”, we learn to import items from existing modules.
- Section 9.2, “Import entire modules” shows another way to use items from modules.
- Section 9.4, “Build your own modules”.

# Import Items from Modules

Back in Section 2.2, “the assignment statement”, we learned that there is an area called the “global namespace,” where Python keeps the names and values of the variables you define.

The Python dir() function returns a list of all the names that are currently defined in the global namespace. Here is a conversational example; suppose you have just started Python in conversational mode.

```python
>>> dir()
['__builtins__', '__doc__', '__name__']
>>> frankness = 0.79
>>> dir()
['__builtins__', '__doc__', '__name__', 'frankness']
>>> def oi():
    ...
    print "Oi!"

>>> dir()
['__builtins__', '__doc__', '__name__', 'frankness', 'oi']
>>> type(frankness)
<type 'float'>
```
