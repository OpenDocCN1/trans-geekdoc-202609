
### Using lists

The Python specification defines a list as a kind of sequence. `Sequences` simply provide some means of allowing multiple data items to exist together in a single storage unit, but as separate entities. Think about one of those large mail holders you see in apartment buildings. A single mail holder contains a number of small mailboxes, each of which can contain mail. Python supports other kinds of sequences as well:

*   `Tuples:` A `tuple` is a collection used to create complex list-like sequences. An advantage of tuples is that you can nest the content of a tuple. This feature lets you create structures that can hold employee records or x-y coordinate pairs.

*   `Dictionaries:` As with the real dictionaries, you create key/value pairs when using the dictionary collection (think of a word and its associated definition). A dictionary provides incredibly fast search times and makes ordering data significantly easier.

*   `Stacks:` Most programming languages support stacks directly. However, Python doesn't support the stack, although there’s a workaround for that. A stack is a last in/first out (LIFO) sequence. Think of a pile of pancakes: You can add new pancakes to the top and also take them off of the top. A stack is an important collection that you can simulate in Python using a list.

*   `Queues:` A queue is a first in/first out (FIFO) collection. You use it to track items that need to be processed in some way. Think of a queue as a line at the bank. You go into the line, wait your turn, and are eventually called to talk with a teller.

*   `Deques:` A double-ended queue (deque, pronounced `deck`) is a queue-like structure that lets you add or remove items from either end, but not from the middle. You can use a deque as a queue or a stack or any other kind of collection to which you’re adding and from which you’re removing items in an orderly manner (in contrast to lists, tuples, and dictionaries, which allow randomized access and management).

Of all the sequences, lists are the easiest to understand and are the most directly related to a real-world object. Working with lists helps you become better able to work with other kinds of sequences that provide greater functionality and improved flexibility. The point is that the data is stored in a list much as you would write it on a piece of paper — one item comes after another. The following sections help you understand lists better.

#### Defining a list

The list has a beginning, a middle, and an end. The items are numbered. (Even if you might not normally number them in real life, Python always numbers the items for you.) To see how you can work with lists, open the Anaconda Prompt, type `python` and press Enter, and type the following code:

```
ListA = [0, 1, 2, 3]
ListB = [4, 5, 6, 7]
ListA.extend(ListB)
ListA
```

When you type the last line of code, you see the output of `[0, 1, 2, 3, 4, 5, 6, 7]`. The `extend()` function adds the members of `ListB` to `ListA`. Beside extending lists, you can also add to them using the `append()` function. Type `ListA.append(-5)` and press Enter. When you type `ListA` and press Enter again, you see that Python has added –5 to the end of the list. You may find that you need to remove items again and you do that using the `remove()` function. For example, type `ListA.remove(-5)` and press Enter. When you list `ListA` again, you see that the added entry is gone.

#### Combining lists using concatenation

Lists support concatenation using the plus (`+`) sign. For example, if you type `ListX = ListA + ListB` and press Enter, you find that the newly created `ListX` contains both `ListA` and `ListB` in it with the elements of `ListA` coming first.

#### Constructing lists using comprehensions

List comprehensions provide an elegant and simple method of creating lists with specific content. A comprehension appears in square brackets after the list name assignment and includes three elements: an expression, an individual item upon which to act, and a list of items to work with. For example, the following list comprehension would place the individual letters of the string `"Hello"` into the list `Letters` after converting them to uppercase:

```
Letters = [letter.upper() for letter in "Hello"]
print(Letters)
```

The output would contain `['H', 'E', 'L', 'L', 'O']`. Normally, to create a list like this, you'd need a `for` loop and several lines of code. The list comprehension does it in just one line, and it’s easy to read.

#### Slicing and dicing lists

You have access to a broad range of list methods and techniques for acting on only part of a list. The following list provides some of the most common techniques for interacting with lists. You see a number of other methods in the book examples.

*   `MyList.append(x):` Adds an element to the end of the list.

*   `MyList.insert(index, value):` Adds an element, `value`, to the location specified by `index` to the list.

    ![Tip](images/tip.png)The first item in a list is numbered `0`, rather than `1`, as you might think. So, when adding the number `4` to the front of `MyList`, you use `MyList.insert(0, 4)`.

*   `MyList.remove(x):` Removes the first occurrence of x from the list.

*   `MyList.extend(ListB):` Appends the elements in `ListB` to the end of `MyList`.

*   `MyList[a:b]:` Returns just the part of the list expressed by the beginning point, `a`, and the ending point, `b`. You may optionally add a third element, a step, that tells how many elements to skip between outputs.

*   `MyList.index(value):` Returns the index of the first occurrence of `value` in the list.

*   `MyList.sort():` Sorts the list in order. You may specify `reverse=True` to sort the list in reverse order. In addition, you can provide a special function to define the sort order.

*   `len(MyList):` Displays the list length.

*   `max(MyList):` Obtains the maximum value in the list.

*   `min(MyList):` Obtains the minimum value in the list.

### Creating and using tuples

A `tuple` is a collection used to create complex lists, in which you can embed one tuple within another. This embedding lets you create hierarchies with tuples. A hierarchy could be something as simple as the directory listing of your hard drive or an organizational chart for your company. The idea is that you can create complex data structures using a tuple.

![Remember](images/remember.png)Tuples are `immutable`, which means that you can't change them. You can create a new tuple with the same name and modify it in some way, but you can’t modify an existing tuple. Lists are mutable, which means that you can change them. So, a tuple can seem at first to be at a disadvantage, but immutability has all sorts of advantages, such as being more secure as well as faster. In addition, immutable objects are easier to use with multiple processors. To see how you can work with tuples, open the Anaconda Prompt, type `python` and press Enter, and type the following code:

```
MyTuple = (1, 2, 3, (4, 5, 6, (7, 8, 9)))
```

`MyTuple` is nested three levels deep. The first level consists of the values 1, 2, 3, and a tuple. The second level consists of the values 4, 5, 6, and yet another tuple. The third level consists of the values 7, 8, and 9. To see how nesting works, type the following code into the python console:

```
for Value1 in MyTuple: if type(Value1) == int: print(Value1) else: for Value2 in Value1: if type(Value2) == int: print("\t", Value2) else: for Value3 in Value2: print("\t\t", Value3)
```

When you run this code, you find that the values really are at three different levels. You can see the indentations showing the level:

```
123 4 5 6 7 8 9
```
