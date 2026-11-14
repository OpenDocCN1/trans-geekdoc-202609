

The function returns a tuple of two values. In the first instruction of the main body of the program these values are assigned to the tuple with the variables a and b. Each of these variables is of the integer type and, for argument 10 of the function, they receive the values 11 and 9, respectively. These values are shown by the first print(). The second print() directly shows the tuple that the function returns.

```
>>>
11 9
(21, 19)
```

## Functions with an arbitrary number of parameters, using tuples

In the previous topic, we analyzed functions with keywords arguments. There is the option to define a function with an arbitrary (variable) number of parameters using the * operator before the parameter name. Let's look at the function of the following example and its different calls.

```
def average(*pair):
    sum = 0
    for elem in pair:
        sum = sum + elem
    return sum / len(pair)
print(average(3, 4))
print(average(10.2, 14, 12, 9.5, 13.4, 8, 9.2))
print(average(2))
```

```
>>>
3.5
10.9
2.0
```

The function calculates the average value of the sequence of numbers that is sent as an argument to the input parameter, which expects to receive a tuple. The function can be improved to avoid dividing by 0, in case of entering an empty tuple.

## Tuple Methods

As in the strings, there are methods associated with tuple type objects and lists. But only the methods: s.index(x) and s.count(x). You can also use the internal functions max and min when the tuples (or lists) are of numerical values. If the elements are strings, calculate the major or minor element, according to the position in the ASCII table of the first character. Let’s see some examples,

```
a = (2, 3, 4, 5, 79, -8, 5, -4)
>>> a.index(5) # index of the first occurrence of 5 in a
3
>>> a.count(5) # total occurrences of 5 in a
2
```

```
>>> max(a)
79
>>> min(a)
-8
>>> b = ('az', 'b', 'x')
>>> max(b)
'x'
>>> min(b)
'az'
```

## Zip function

It is an iterator that operates on several iterable ones and creates tuples by adding elements of the iterable sequences (string, tuples, lists, etc.). Example,

```
def AccountElemsSamePosition(s1, s2):
    """Tell how many equal letters are in the same position in 2
    S1 and S2 words. You can use lists or tuples
    >>> AccountElemsSamePosition('Hello', 'Casting')
    3
    """
    counter = 0
    for c1, c2 in zip(s1, s2):
        if c1 == c2:
            counter += 1
    return counter
```

```
>>> AccountElemsSamePosition('Hello', 'Goodbye')
0
>>> AccountElemsSamePosition('Hello', 'Casting')
3
```

## Frozen sets (Frozenset)

In Python, there is another group of heterogeneous structured data that try to keep a certain relationship with set theory. This data is the Set and Frozenset sets. The first ones are presented in the following section of structured mutable or dynamic data.

A frozen set (Frozenset) is a collection of unordered items that are unique and immutable. That is, it can contain numbers, string, tuples, but not lists. That they are unique elements means that they are not repeated. The Set and Frozenset are not sequences of data.

Frozen sets are immutable because they cannot be changed or removed or added. Examples of frozen data:

```
>>> FS1 = frozenset({25, 4, 'a', 2, 25, 'house', 'a'})
>>> FS1
frozenset({2, 'a', 4, 'house', 25})
>>> type(FS1)
<class 'frozenset'>
>>> len(FS1)
5
```

The repeated elements (25 and 'a') that we included in the frozen set were discarded.

## Types of structured mutable (dynamic) data

Unlike the frozen strings, tuples and sets, the structured mutable data, also called dynamic, are characterized in that their elements can change in value and elements can be added or deleted.

In Python, we have as mutable structured data the lists, the sets (Set) and the dictionaries. The lists and sets (Set) can be considered as the mutable equivalents to the frozen tuples and sets (Frozenset), respectively.

## Lists

The lists, as well as tuples and strings, are formed by a sequence of data. But unlike tuples, its elements can be modified, eliminated or increased. The elements of the lists can be simple data (numerical or Boolean), strings, tuples or other lists. Elements are indexed the same as tuples and string, through an integer. The syntax of the lists is a sequence of comma-separated values enclosed in square brackets. Examples:

```
>>> v1 = [2, 4, 6, 8, 10]
>>> type(v1)
<class 'list'>
>>> v2 = [7, 8.5, 'a', 'Hello', (2, 3), [11, 12]]
>>> v2
[7, 8.5, 'a', 'Hello', (2, 3), [11, 12]]
>>> games = ['tennis', 'baseball', 'football', 'volleyball', 'swimming']
>>> games
['tennis', 'baseball', 'football', 'volleyball', 'swimming']
```

The v1 list consists of integers, while v2 includes integers, reals, strings, tuples and a list as its last element. The variable games refer to a list object with 5 elements of type string. It is similar to the previously defined tuple, but its elements can be modifiable. It is a dynamic structure.

We can generate a list with a sequence of integers with the data type range(), of the form,

```
>>> v = list(range(1, 11))
>>> v
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

In Python versions 2.x, range() is a function that directly generates a list. However, in versions 3.x, being range() a type of data range, we have to convert it to a list with the function list(). This function also serves to convert iterable data types, such as strings or tuples to list type. You can also create an empty list. Examples:

```
>>> t = (1, 2, 3)
>>> list(t)
[1, 2, 3]
>>> s = 'Hello'
>>> list(s)
['H', 'e', 'l', 'l', 'o']
>>> e = list() # empty list
>>> e = [] # empty list
```

## Indexing, trimming and other list operations

In the lists, access to its elements, the extraction of elements and operations are carried out in the same way as in strings and tuples. The slice operators [n: m] are also used in the lists. Let's look at several examples:

```
>>> v2 = [7, 8, 'a', 'Hello', (2, 3), [11, 12]]
>>> v2[0]
7
>>> v2[-1]
[11, 12]
>>> v2[-2]
(2, 3)
>>> v2[0: 3]
[7, 8, 'a']
>>> t = ['las', 'lists', 'are', 'mutables']
>>> t[3] = 'dynamic'
>>> t
['las', 'lists', 'are', 'dynamic']
>>> len(t)
4
```

The mutability of the lists can be observed. Lists can be concatenated and repeated with the + and * operators, respectively, such as strings and tuples,

```
>>> v1 = [2, 4, 6, 8, 10]
>>> v3 = [3, 5, 7]
>>> v1 + v3
[2, 4, 6, 8, 10, 3, 5, 7]
>>> 3 * v3
[3, 5, 7, 3, 5, 7, 3, 5, 7]
```

The iterative Python for - in composition has already been used with lists in the subject of iterative compositions. With the previously defined games list, we get:

```
>>> for sport in games:
...     print(sport)
tennis
baseball
football
volleyball
swimming
```

In addition, as in the string and tuple sequences, the lists can be concatenated with the + operator and repeated with the * operator. Boolean operators in and not in, as in strings and tuples, evaluate whether or not an element belongs to a sequence (string, tuple or list). Examples

```
>>> v2 = [7, 8, 'a', 'Hello', (2, 3), [11, 12]]
>>> 8 in v2
True
>>> 'Hello' in v2
True
>>> 'HELLO' not in v2
True
```

## Objects, values and references

The operator is available in Python that indicates whether two variables are referred to the same object or not. If we execute the instructions.

```
>>> a = 'house'
>>> b = 'house'
>>> id(a)
123917904
>>> id(b)
123917904
>>> a is b
True
```

![](img/6308792a7b2c124d01547ee394b31561_59_0.png)

You can see that both variables a and b are referred to the same object, which has a 'house' value and occupies the memory position 123917904 (this position is arbitrary). The instruction a is b is true.

In string data types, being immutable, Python creates only one object per memory economy and both variables are referred to the same object. However, with the lists, being mutable, although two lists with the same values are formed, Python creates two objects, which occupy different memory locations:

```
>>> a = [1, 2, 3]
>>> b = [1, 2, 3]
>>> id(a)
123921992
>>> id(b)
123923656
>>> a is b
False
```

![](img/6308792a7b2c124d01547ee394b31561_59_1.png)

The lists assigned to variables a and b, although with the same value, are different objects. But you have to be careful with the variable assignments to the

