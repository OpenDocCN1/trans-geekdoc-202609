
# Chapter 5 – Variables and Data Types of Python

The real deal about Python programming is surfacing now. The previous chapter has laid the foundation for coding by explaining the nitty-gritty of Python syntax; the rule guiding the stringing of words together for instruction and interpretation. In this chapter, we will examine variables, their definition, syntax, etc. and the types of data found in Python.

Within Python is a container; more like a memory card that can store values; called the **variables**. It can be accessed or changed depending on the kind of information stored therein. Variables are like ways of pinpointing a specific location used by a program while coding. In a way, variables are used to track the particular place programs coded are stored for further usage like exporting to other platforms, merging, among others. For Python, variables can instruct (give statements) the computer to save or retrieve data to and from this same memory location.

In dealing with variables and data types, Python works significantly different from other related languages like Java, C, etc. This is chiefly because while they declare and bind a variable to a specific data type, Python binds with different data – it can only store a unique data type. To put it in simple terms, if the variable to be stored is of integer type, you will only be able to save integers in that variable when running your program. In short, in dealing with variables, there is no rigid way of handling them in Python; peradventure you wish to use a variable, think of a name, declare it through value assignment which can be changed as well during the execution of the program if need be.

## How do you declare a variable through a value assignment?

To answer this, examine the illustration given below:

```
my_variable = 20
```

Note that you are equating the variable `my_variable` as 20 in actuality rather than the variable is just set to 20.

If you want to increase the value of the variable, enter this statement on the command line:

```
>>> my_variable = my_variable + 5
```

In order to know the way Python will respond to this command, invoke the `print` command with:

```
>>> print(my_variable)
```

This will be the result on the next line:

```
25
```

If you wish to use `my_variable` to store a literal string “violet”, simply set the variable to “violet” in this way:

```
>>> my_variable = "violet"
```

In order to know the current store in `my_variable`, use the `print` command:

```
>>> print(my_variable)
```

On the next line, you’ll see:

```
Violet
```

These are just simple ways of handling variables in Python, make sure you follow practically.

At this point, the journey to variables will be on hold as we turn to the data types found in Python programming.

## Data Types in Python

Python has different data types in order to enhance the importance of it to application developers and programmers as enough effective data are supplied. The data types are numbers, date, Strings, time, Booleans, and lists.

### The Numbers Data Types

Python can differentiate numeric types without you declaring them; this is one of the greatest advantages of using Python. With its in-built functions, Python knows for itself one data from the other when you are running your statement. These in-built functions for numeric values are four, namely: floating, complex, integer, and long integer numbers. It is pertinent to note that the type of Python you are using will determine the number of active in-built numeric functions. For Python 3, however, only three (floating, integer, and complex) types are supported.

#### The Floating numbers

These are real numbers. They are known as floats too. Also known as floats, floating-point numbers signify real numbers. Significantly, when you want to write floats, put a decimal in them to differentiate them from fractional numbers. In another way, you can write floats using scientific notations; upper and lower cases; where the letter ‘e’ will be equivalent to the power of 10th. The illustration is:

```
>>> 7.4e2
7400.0
>>> 7.4e2
742
```

You can try it more with other number sequences too to enhance flexibility with floats.

#### The Integer (int) numbers

Integers, unlike floats, are not written with decimal points. They are whole positive or negative numbers. Integers in Python are numerous but few will be given below as a guide to how others will be treated;

**Base 2 integers**

In order to write binary integers, use either `0b` or `0B` as prefix (it is zero and not `o`). As an illustration, see:

```
>>> a = 0b3200
>>> print(a)
3200
```

**Regular integers**

They are just normal numbers whether positive or negative polar. Examples are 243, -110, 3, etc.

**Base 16 integers**

They are also known as hexadecimal. In order to write the base 16 integers, use the prefix `0X` or `0x` (zero eks). To illustrate see below:

```
>>> hex_lit = 0xA0B
>>> print(hex_lit)
238
```

**Base 8**

This like others, too, is represented by using `0o` or `0O` as prefix too. Example:

```
>>> c = 0O29
>>> print(c)
29
```

#### Complex numbers

They are like the real numbers in that they are real numbers, though they always in pairs. Additionally, complex numbers are also sets of imaginary numbers. In their combination, they take the form of a float and real number in this way: `c + bJ` where `c` is a float, `b` a float too and `J` square root of the imaginary number. See the examples below:

```
>>> x = 5 + 6j
>>> y = 8 - 2j
>>> z = x + y
>>> print(z)
(13+4j)
```

Note that complex numbers are restricted in usage in Python.

### The Strings Data Types

Strings are special data as they are Unicode character with letters, symbols and numbers combinations. In their definition, while coding, enclose strings in ‘matching single or double quotations’. Check the examples below:

```
>>> stringA = "The best student is Python."
>>> stringB = "The best student is Python."
```

Peradventure you are dealing with literal string enclosed in single quotes which contains a single quote as well, place a backslash (`\`) before the single quote within the string to escape the character. For example:

```
>>> stringC = 'It is good to be smart.'
```

To print `stringC`:

```
>>> print(stringC)
It is good to be smart.
```

If the quote had been enclosed in the normal double quote, the coding would have been straightforward in this manner:

```
>>> stringC = "It is good to be smart"
```

In the same vein, whenever your quote is enclosed in another double quote, place a backslash before the embedded quote. Check this example:

```
>>> doc = "The programmer reiterated: \"You will always choose Python programming language as the best among others.\""
>>> print(doc)
The programmer reiterated: "You will always choose Python programming language as the best among others"
```

There are ways in which strings treat indexed or subscripted numbers. Bear in mind that Python indexing starts from 0 (zero) instead of 1. Therefore, the first character of any string must start from zero. To illustrate how to string indexing works in Python, define the string "Hello Python" on the command line:

```
>>> s = "Hello everyone, it is Python"
```

This is how Python would index the string:

```
-12 -11 -10 -9 -8 -6 -6 -5 -4 -3 -2 -1
H  e  l  l  o     e  v  e  r  y  o  n  e  ,     i  t     i  s     P  y  t  h  o  n
( write from 0- infinity)
```

In order to check for the first character of the string, type and enter the variable name `s` and the index 0 within square brackets like this:

```
>>> s[0]
```

You’ll get this output:

```
'H'
```

Note that it is easier to check for this because you know that its index number is zero. Interestingly, you do not have this privilege when you want to access the last character on the same string. How do you do it then? In order to check for the last character, use this expression:

```
>>> s[len(s)-1]
```

You’ll get the output:

```
'n'
```

The expression introduces you to the `len()` function. There is actually an easier way to access the last item on the string:

```
>>> s[-1]
'n'
```

To access the penultimate character:

```
>>> s[-2]
'o'
```

Apart from using the index, you can use other functions and mathematical operators on a string.

### Date and Time Data Types

The fact that a good number of applications works effectively with date and time information is true of Python programming. To use the function of time and date, use this command: `datetime.now()`. This will generate the current date and time as it communicates the in-built Python code to execute the function. You can access time and date right from Python by encoding the following on the command prompt:

```
>>> from datetime import datetime
>>> datetime.now()
datetime.datetime(2019, 4, 20, 4, 17, 19, 60352)
```

You will notice that the format of the numbers is not really readable and you’d love to work with something readable, therefore, use the command `strftime` to make it possible. Check the format given below:

```
>>> from time import strftime
>>> strftime("%Y-%m-%d %H:%M:%S")
'2019-04-20 05:35:03'
```

Note that the `strftime` commands acronym are: Y (year), M (month), D (day), M (month), and S (seconds).

### The Boolean Data Types

Basically, the data types that are used to generate positive and negative responses in Python are Booleans. The responses are typically true or false. For example, create several variables to store Boolean values and print the result in this way:

```
bool_a = 7 == 2*3
bool_b = 9 < 2 * 2**3
bool_c = 7 > 2 * 4 + 1
print(bool_a)
print(bool_b)
print(bool_c)
```

The Python Shell will display these results:

```
False
True
False
```

### The Lists Data Types

Simply put; lists are data types that can be used to store any type and number of variables a piece of information. In order to define your lists, you must assign item types to them in this way:

```
my_list = [item_1, item_2, item_3]
```

Perhaps you want to create empty list, it is permitted in Python also in this way:

```
my_list = []
```

For better understanding, let’s create a list of animals:

```
animals = ["goat", "cow", "pig", "dog", "duck", "lizard"]
```

Do you remember how indexing is treated in Python? Good, this is an indexed list with the first item on animals has zero as its index. To access the first item on the list, you can print the animal with the command:

```
>>> print(animals[0])
goat
```

To use the print command to get the name of the third color on the list, you can enter:

```
>>> print(animals[4])
dog
```

You can try it with other animal types too. In order to ascertain the number of animals in the list given use the `len()` function:

```
>>> len(animals)
6
```

There are only six animals on your list in all. If peradventure you included an odd item in your list and you want to remove it, use the function `remove()` method – this is most applicable where the odd items are many. To illustrate this check:

```
>>> animals.remove("goat")
```

See the updated list with this print command:

```
>>> print(animals)
['cow', 'pig', 'dog', 'duck', 'lizard']
```

In the same vein, if you wish to add to your list, use the `append()` command in this way:

```
>>> animals.append("dog")
```

Now access the updated list with this print command:

```
>>> print(animals)
['cow', 'pig', 'dog', 'duck', 'lizard', 'dog']
```

The animal ‘dog’ was added to the end of the list. Also, if you wish to insert the list in between the item you have listed use Python’s `insert()` method with the syntax:

```
list.insert(index, obj)
```

The index and object are the basic parameters needed here. Meanwhile, index here means the particular position for the new item while the object is the item itself. Applying the syntax rules to the example given above, this is the command:

```
>>> animals.insert(4, "cat")
```

To see the new list:

```
>>> print(animals)
['cow', 'pig', 'dog', 'duck', 'cat', 'lizard', 'dog']
```

### The Dictionary Data Type

As noted from the beginning of this book, the variables and data types of Python provide a list of unique keys. The dictionary is important while coding as lots of accesses to values are assured. Simply put, a dictionary is more like a list that uses unique keys that are immutable to the data type instead of creating access to values only. To separate a key, use a colon and enclose it in a curly bracket. Check the dictionary structure below:

```
x = {key_1: c, key_2: d, key_3: cd}
```

Meanwhile, an empty dictionary will have this format:

```
x = {}
```

One of the amazing facts of the dictionary is that it can be used to store and manipulate the values of the key that are in pairs like the ones in directory, menu, log in data, or phone books. Also, it is very possible to modify the data on the dictionary. In order to understand the structure of a dictionary and how it works, consider creating a menu on drums parts with their prices in pairs as in:

```
menu = {"base": 14.40, "snare": 30, "cymbals": 20}
```

For the key-value pairs and how they are stored in the dictionary, use the `len()` function as in:

```
>>> len(menu)
3
```

Using the print command to get the current entries in the menu dictionary:

```
>>> print(menu)
{'cymbals': 20, 'snare': 30, 'base': 14.40}
```

If you wish to input new entry in the menu dictionary, you can use this format:

```
d[key_4] = b
```

Applying this structure to the menu dictionary, you can add the drum parts kick: 7 with this format:

```
menu["kick"] = 7
```

In order to get the updated menu, use the print command:

```
>>> print(menu)
```

You should get this string from the outset:

```
{"base": 14.40, "kick": 7, "snare": 30, "cymbals": 20}
```

If you would love to delete any item out of your list using the `del` command in this way: (using the “base” as an example)

```
>>> del menu["base"]
```

To see the modified list after deleting spam: This is the list you will see obviously:

```
{"kick": 7, "snare": 30, "cymbals": 20}
```

If it is that you want to change the values of any of the key, assign a new value to it using the command below (using the key “snare” as an example which you are changing from 30 to 25):

```
>>> menu["snare"] = 25
```

Access the print command once more to see the updated menu:

```
>>> print(menu)
```

This will show as list:

```
{"kick": 7, "snare": 25, "cymbals": 20}
```

If you want to remove all entries in the dictionary in order to store others, use the function `dict.clear()`. This is the command:

```
>>> dict.clear(menu)
```

To see what happened to the menu dictionary, print as in:

```
>>> print(menu)
{}
```

This will enable you to store the new data into the dictionary by repeating the steps given above on the dictionary.

## Conclusion

In conclusion, we have treated the variables, data types and even a dictionary of Python successfully in this chapter. If anything is seeming absurd, which shouldn't, repeat the steps. The next chapter explores some basic operators on Python. Alongside their functionality, the operators work in different ways for different purposes. The understanding of these operators will give you better chances of applying their functions to other related languages. Join me in the next chapter; finger crossed!
