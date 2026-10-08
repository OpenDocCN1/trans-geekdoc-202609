# Lists

Perhaps the most important data structure in Python language is the list. A list can be defined as an ordered collection. Lists in python share a lot of features with lists in other languages.
To check for list membership in Python, you use the in operator as shown below:

```
1 in [1, 2, 3] # True
0 in [1, 2, 3] # False
```

It’s a straightforward process to concatenate lists:

```
x = [1, 2, 3]
x.extend([4, 5, 6]) # x is now [1,2,3,4,5,6]
```

Still, you have the option to use x,
If you don't want to alter x, you can use list addition.

```
x = [1, 2, 3]
y = x + [4, 5, 6] # y is unchanged
```

Most of the time, you’ll append lists to a single item at a time.
It is effective to unpack lists if you already understand the total number of elements they can store. However, if the number of elements on both sides isn’t the same, you will see a value.
It’s common to write the underscore for a value you want to throw away:

```
_, y = [1, 2] # now y == 2, didn't care about the first element
```

# Dictionaries

The dictionary, also referred to as a hashtable, is one of the most robust data structures Python has available to apply. Fortunately, because it’s built into the Python language, you don’t need to run it yourself.
The dictionary is a useful data structure that features a ‘key’ and a ‘value.’