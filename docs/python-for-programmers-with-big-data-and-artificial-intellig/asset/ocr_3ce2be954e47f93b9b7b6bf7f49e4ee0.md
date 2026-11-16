exception classes from the Python Standard Library. However, using the inheritance techniques presented earlier in this chapter, you can create your own custom exception classes that derive directly or indirectly from class Exception. Generally, that's discouraged, especially among novice programmers. Before creating custom exception classes, look for an appropriate existing exception class in the Python exception hierarchy. Define new exception classes only if you need to catch and handle the exceptions differently from other existing exception types. That should be rare.

# 10.12 NAMED TUPLES

You've used tuples to aggregate several data attributes into a single object. The Python Standard Library's collections module also provides named tuples that enable you to reference a tuple's members by name rather than by index number.

Let's create a simple named tuple that might be used to represent a card in a deck of cards. First, import function namedtuple:

lick here to view code image

```
In [1]: from collections import namedtuple
```

Function namedtuple creates a subclass of the built-in tuple type. The function's first argument is your new type's name and the second is a list of strings representing the identifiers you'll use to reference the new type's members:

lick here to view code image

```
In [2]: Card = namedtuple('Card', ['face', 'suit'])
```

We now have a new tuple type named Card that we can use anywhere a tuple can be used. Let's create a Card object, access its members by name and display its string representation:

lick here to view code image

```
In [3]: card = Card(face='Ace', suit='Spades')

In [4]: card.face
Out[4]: 'Ace'

In [5]: card.suit
Out[5]: 'Spades'

In [6]: card
Out[6]: Card(face='Ace', suit='Spades')
```

# Other Named Tuple Features