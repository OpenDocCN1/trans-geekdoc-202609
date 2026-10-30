
The insert method always inserts an item before the given index, after shifting some items to the right by one position. The pop method removes the item at the given index, before shifting some items to the left by one position. Note that when you omit the index, the pop method removes the last item in the list.

Other list methods are content based, meaning that they are given or targeted at an item rather than a position in the list. For example, the append method adds a given item to the end of a list, whereas the remove method removes the first instance of a given item from a list. The following shell session demonstrates these operations:

```
>>> fruits
['oranges', 'bananas', 'apples']
>>> fruits.append("grapes")
>>> fruits
['oranges', 'bananas', 'apples', 'grapes']
>>> fruits.remove("bananas")
>>> fruits
['oranges', 'apples', 'grapes']
```

Note that the item given to the remove method must already be in the list.

Although the items in a list are always ordered by position, they may not be in alphabetical order (if they are strings) or in ascending or descending order (if they are numbers). Rearranging list items into this kind of order is called sorting. Sorting is a complex process, but the list method sort makes that easy, as shown here:

```
>>> fruits
['oranges', 'peaches', 'cherries', 'apples']
>>> fruits.sort()
>>> fruits
['apples', 'cherries', 'oranges', 'peaches']
>>> grades
[77, 100, 85, 92]
>>> grades.sort()
>>> grades
[77, 85, 92, 100]
>>> grades.reverse()
>>> grades
[100, 92, 85, 77]
```

Note that the methods sort and reverse are used in sequence to place list items in descending order.

Table 1.4 summarizes some commonly used list operations, where the variable L refers to a list.

Table 1.4 Some Commonly Used List Operations

| List Operation | What It Does |
|---|---|
| `len(L)` | Returns the number of items currently in the list. |
| `L[index]` | Returns the item at the integer position `index` in the list. Note: do not use an `index` that is less than 0 or greater than or equal to the length of the list. |
| `L[index] = item` | Replaces the item at the integer position `index` in the list with `item`. Note: do not use an `index` that is less than 0 or greater than or equal to the length of the list. |
| `L.append(item)` | Adds `item` to the end of the list. |
| `L.count(item)` | Returns the number of instances of `item` in the list. |
| `L.index(item)` | Returns the position of the first instance of `item` in the list, or raises an exception if `item` is not present. |
| `L.insert(index, item)` | Inserts `item` at position `index`, shifting other items to the right by one position if necessary. |
| `L.pop(index)` | Removes the item at position `index`, shifting other items to the left by one position if necessary. If `index` is not provided, removes the item at the end of the list. |
| `L.remove(item)` | Removes the first instance of `item` in the list, or raises an exception if `item` is not present. |

## Lists from Other Sequences

Sometimes you'll want to build a new list from another sequence, such as a string or another list. The easiest way to do this is to supply that sequence as an argument to the list function, as follows:

```
>>> characters = list("Ken Lambert")
>>> characters
['K', 'e', 'n', ' ', 'L', 'a', 'm', 'b', 'e', 'r', 't']
>>> myCopy = list(characters)
>>> myCopy
['K', 'e', 'n', ' ', 'L', 'a', 'm', 'b', 'e', 'r', 't']
```

The first assignment creates a list of the characters in a string. The second assignment creates a copy of that list.

Another common way to build a list from a string is to use the string method split. This method returns a list of the words in the string, where the space character is the separator between the words. The original string can be reconstructed by running the string method join with the list of words as an argument. Here is an example:

```
>>> words = "Ken Lambert".split()
>>> words
['Ken', 'Lambert']
>>> " ".join(words)
'Ken Lambert'
```

Finally, to create a list from a range of numbers, you use Python’s range function to create the range and pass this result to the list function.

Here are some examples:

```
>>> numbers = list(range(15))
>>> numbers
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
>>> oneThroughFifteen = list(range(1, 16))
>>> oneThroughFifteen
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]
>>> fifteenThroughOne = list(range(15, 0, -1))
>>> fifteenThroughOne
[15, 14, 13, 12, 11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
```

When range gets a single integer argument, it returns a range of numbers from 0 to this integer minus one. When range gets two integer arguments, it returns a range from the first integer to the second integer minus one. When range gets three integer arguments, it returns a range from the first integer to the second integer minus one, but the value of the third integer is used to count the interval between the integers in the range. Thus, to count down rather than up, as in the example, the first integer must be greater than the second one, and the third integer must be negative.

## Lists and the random Module

The set of integers is also a sequence, which allows you to treat other sets, such as the set of characters and the set of positions in a list or string, as sequences. You have seen that even when the items in a list or string are in a sequence, they may otherwise be in a random (unsorted) order. In many applications, you might want to arrange a set of items in a list in random order or perhaps select an item from a random position. (Think of shuffling a new deck of cards or picking a random ping pong ball from a bowl of such balls.) Python’s random module includes some functions that allow you to perform these tasks with lists. The two most commonly used functions are random.shuffle and random.choice. Here are some uses of these two functions:

```
>>> import random
>>> numbers = list(range(1, 16))
>>> numbers
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]
>>> random.shuffle(numbers)
>>> numbers
[6, 11, 1, 12, 3, 10, 13, 4, 5, 15, 2, 7, 9, 8, 14]
>>> random.choice(numbers)
13
>>> random.choice(numbers)
8
>>> coin = ["heads", "tails"]
>>> random.choice(coin)
'heads'
>>> random.choice(coin)
'heads'
>>> random.choice(coin)
'tails'
```

## Tuples as Immutable Lists

You saw earlier that a string is immutable, meaning that its contents and structure cannot change after it is created. You also saw that lists are mutable, meaning that you can alter their contents and structure with replacements, insertions, and removals. Although lists are mutable, occasionally you want to create sequences of items that are list-like but also immutable. In Python, a data structure called a tuple fills this bill.

A tuple looks just like a list but uses parentheses rather than square brackets to enclose its items. Tuples are created by mentioning them as literals (with possibly embedded variables) or by running the tuple function on another sequence, such as a list, a string, or a range of numbers. The usual operators have the expected results, but a tuple with a subscript cannot appear on the left side of an assignment. The next shell session shows some examples:

```
>>> pair = (1, 2)
>>> triple = (3, 4, 5)
>>> len(triple)
3
>>> triple[2]
5
>>> triple[1:]
(4, 5)
>>> pair + triple
(1, 2, 3, 4, 5)
>>> tuple(range(15))
(0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14)
>>> tuple("Ken Lambert".split())
('Ken', 'Lambert')
```

## WORKING WITH DICTIONARIES

Lists and tuples are sequences. They are well suited for applications in which items must be ordered by position. Another type of data structure, called the dictionary, does not order its items by position. Instead, a dictionary associates each item with a unique value called a key. For example, when you hear the words mother and father, it’s likely that images of your mother and father immediately come to mind. In a crude sense, your mind or memory is like a big dictionary, in which each item or idea is associated with a unique key that allows you to access it. In this section, you explore the use of Python dictionaries to model this type of memory storage.

## Dictionary Literals

A dictionary is a set of key/value pairs. In a Python dictionary, the keys must be unique, but the values can be repeated. A key must be an immutable value, such as a number or a string. A value can be any Python data object or even a function or method.

A dictionary literal consists of curly braces {}, which enclose a sequence of key/value pairs. Commas separate the pairs. Within each pair, a colon appears between the key and the value. The next shell session shows some example dictionaries:

```
>>> {}
{}
>>> kenInfo = {"name":"Ken", "hair-color":"gray", "age":63}
```
