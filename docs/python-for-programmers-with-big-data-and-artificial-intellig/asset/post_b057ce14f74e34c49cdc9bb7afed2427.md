
be redundant, and `a_singleton_tuple` would simply refer to the string 'red' rather than a tuple.

## Accessing Tuple Elements

A tuple's elements, though related, are often of multiple types. Usually, you do not iterate over them. Rather, you access each individually. Like list indices, tuple indices start at 0. The following code creates `time_tuple` representing an hour, minute and second, displays the tuple, then uses its elements to calculate the number of seconds since midnight—note that we perform a *different* operation with each value in the tuple:

click here to view code image

```
In [11]: time_tuple = (9, 16, 1)

In [12]: time_tuple
Out[12]: (9, 16, 1)

In [13]: time_tuple[0] * 3600 + time_tuple[1] * 60 + time_tuple[2]
Out[13]: 33361
```

Assigning a value to a tuple element causes a TypeError.

## Adding Items to a String or Tuple

As with lists, the += augmented assignment statement can be used with strings and tuples, even though they're *immutable*. In the following code, after the two assignments, `tuple1` and `tuple2` refer to the *same* tuple object:

```
In [14]: tuple1 = (10, 20, 30)

In [15]: tuple2 = tuple1

In [16]: tuple2
Out[16]: (10, 20, 30)
```

Concatenating the tuple (40, 50) to `tuple1` creates a *new* tuple, then assigns a reference to it to the variable `tuple1`—`tuple2` still refers to the original tuple:

click here to view code image

```
In [17]: tuple1 += (40, 50)

In [18]: tuple1
Out[18]: (10, 20, 30, 40, 50)

In [19]: tuple2
Out[19]: (10, 20, 30)
```

For a string or tuple, the item to the right of += must be a string or tuple, respectively—mixing types causes a TypeError.

## Appending Tuples to Lists

You can use += to append a tuple to a list:

click here to view code image

```
In [20]: numbers = [1, 2, 3, 4, 5]

In [21]: numbers += (6, 7)

In [22]: numbers
Out[22]: [1, 2, 3, 4, 5, 6, 7]
```

## Tuples May Contain Mutable Objects

Let’s create a student_tuple with a first name, last name and list of grades:

click here to view code image

```
In [23]: student_tuple = ('Amanda', 'Blue', [98, 75, 87])
```

Even though the tuple is immutable, its list element is mutable:

click here to view code image

```
In [24]: student_tuple[2][1] = 85

In [25]: student_tuple
Out[25]: ('Amanda', 'Blue', [98, 85, 87])
```

In the double-subscribed name student_tuple[2][1], Python views student_tuple[2] as the element of the tuple containing the list [98, 75, 87], then uses [1] to access the list element containing 75. The assignment in snippet [24] replaces that grade with 85.

## 5.4 UNPACKING SEQUENCES

The previous chapter introduced tuple unpacking. You can unpack any sequence’s elements by assigning the sequence to a comma-separated list of variables. A `ValueError` occurs if the number of variables to the left of the assignment symbol is not identical to the number of elements in the sequence on the right:

click here to view code image

```python
In [1]: student_tuple = ('Amanda',   [98, 85, 87])
In [2]: first_name, grades = student_tuple
In [3]: first_name
Out[3]: 'Amanda'
In [4]: grades
Out[4]: [98, 85, 87]
```

The following code unpacks a string, a list and a sequence produced by `range`:

click here to view code image

```python
In [5]: first, second = 'hi'
In [6]: print(f'{first}   {second}')
h i
In [7]: number1, number2, number3 = [2,   3, 5]
In [8]: print(f'{number1}   {number2}   {number3}')
2 3 5
In [9]: number1, number2, number3 = range(10, 40, 10)
In [10]: print(f'{number1}   {number2}   {number3}')
10 20 30
```

### Swapping Values Via Packing and Unpacking

You can swap two variables’ values using sequence packing and unpacking:

click here to view code image

```
In [11]: number1 = 99
In [12]: number2 = 22
In [13]: number1, number2 = (number2, number1)
In [14]: print(f'number1 = {number1}; number2 = {number2}')
number1 = 22; number2 = 99
```

### Accessing Indices and Values Safely with Built-in Function enumerate

Earlier, we called range to produce a sequence of index values, then accessed list elements in a for loop using the index values and the subscription operator ([ ]). This is error-prone because you could pass the wrong arguments to range. If any value produced by range is an out-of-bounds index, using it as an index causes an IndexError.

The preferred mechanism for accessing an element's index and value is the built-in function enumerate. This function receives an iterable and creates an iterator that, for each element, returns a tuple containing the element's index and value. The following code uses the built-in function list to create a list containing enumerate's results:

![](img/34b7fc2f1ee27beb73bca14927d42340_181_0.png)

```
In [15]: colors = ['red', 'orange', 'yellow']
In [16]: list(enumerate(colors))
Out[16]: [(0, 'red'), (1, 'orange'), (2, 'yellow')]
```

Similarly the built-in function tuple creates a tuple from a sequence:

![](img/34b7fc2f1ee27beb73bca14927d42340_181_1.png)

```
In [17]: tuple(enumerate(colors))
Out[17]: ((0, 'red'), (1, 'orange'), (2, 'yellow'))
```

The following for loop unpacks each tuple returned by enumerate into the variables index and value and displays them:

![](img/34b7fc2f1ee27beb73bca14927d42340_181_2.png)

```
In [18]: for index, value in enumerate(colors):
...:     print(f'{index}: {value}')
...:
0: red
1: orange
2: yellow
```

### Creating a Primitive Bar Chart

The following script creates a primitive bar chart where each bar's length is made of asterisks (*) and is proportional to the list's corresponding element value. We use the function enumerate to access the list's indices and values safely. To run this example, change to this chapter's ch05 examples folder, then enter:

```
ipython fig05_01.py
```

or, if you're in IPython already, use the command:

```
run fig05_01.py
```

click here to view code image

```
1 # fig05_01.py
2 """Displaying a bar chart"""
3
4 numbers = [19, 3, 15, 7, 11]
5
6 print('\nCreating a bar chart from numbers:')
7 print(f'Index{"Value":>8}   Bar')
8
9 for index, value in enumerate(numbers):
10     print(f'{index:>5}{value:>8}   {"*" * value}')
```

click here to view code image

```
Creating a bar chart from numbers:
Index   Value   Bar
0       19      *******************
1       3       ***
2       15      *******************
3       7       *******
4       11      ***********
```

The for statement uses enumerate to get each element's index and value, then displays a formatted line containing the index, the element value and the corresponding bar of asterisks. The expression

```
"*" * value
```

creates a string consisting of `value` asterisks. When used with a sequence, the multiplication operator (*) *repeats* the sequence—in this case, the string "*"—`value` times. Later in this chapter, we'll use the open-source Seaborn and Matplotlib libraries to display a publication–quality bar chart visualization.

## 5.5 SEQUENCE SLICING

You can *slice* sequences to create new sequences of the same type containing *subsets* of the original elements. Slice operations can modify mutable sequences—those that do *not* modify a sequence work identically for lists, tuples and strings.

### Specifying a Slice with Starting and Ending Indices

Let's create a slice consisting of the elements at indices 2 through 5 of a list:

click here to view code image

```
In [1]: numbers = [2, 3, 5, 7, 11, 13, 17, 19]
In [2]: numbers[2:6]
Out[2]: [5, 7, 11, 13]
```

The slice *copies* elements from the *starting index* to the left of the colon (2) up to, but not including, the *ending index* to the right of the colon (6). The original list is not modified.

### Specifying a Slice with Only an Ending Index

If you omit the starting index, 0 is assumed. So, the slice `numbers[:6]` is equivalent to the slice `numbers[0:6]`:

click here to view code image

```
In [3]: numbers[:6]
Out[3]: [2, 3, 5, 7, 11, 13]
In [4]: numbers[0:6]
Out[4]: [2, 3, 5, 7, 11, 13]
```

### Specifying a Slice with Only a Starting Index

If you omit the ending index, Python assumes the sequence’s length (8 here), so snippet [5]’s slice contains the elements of numbers at indices 6 and 7:

click here to view code image

```
In [5]: numbers[6:]
Out[5]: [17, 19]

In [6]: numbers[6:len(numbers)]
Out[6]: [17, 19]
```

### Specifying a Slice with No Indices

Omitting both the start and end indices copies the entire sequence:

click here to view code image

```
In [7]: numbers[:]
Out[7]: [2, 3, 5, 7, 11, 13, 17, 19]
```

Though slices create new objects, slices make shallow copies of the elements—that is, they copy the elements’ references but not the objects they point to. So, in the snippet above, the new list’s elements refer to the same objects as the original list’s elements, rather than to separate copies. In the “Array-Oriented Programming with NumPy” chapter, we’ll explain deep copying, which actually copies the referenced objects themselves, and we’ll point out when deep copying is preferred.

### Slicing with Steps

The following code uses a step of 2 to create a slice with every other element of numbers:

```
In [8]: numbers[::2]
Out[8]: [2, 5, 11, 17]
```

We omitted the start and end indices, so 0 and len(numbers) are assumed, respectively.
