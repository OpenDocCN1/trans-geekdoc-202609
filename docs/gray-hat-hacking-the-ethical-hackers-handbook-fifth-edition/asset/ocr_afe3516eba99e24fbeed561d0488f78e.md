```
>>> s1 + str(n1)
'abc12'
>>> s1.replace('c', str(n1))
'ab12'
```

When it makes sense, different types can be used together:

```
>>> s1*n1  # Display 'abc' 12 times
'abcabcabcabcabcabcabcabcabcabcabcabc'
```

And one more note about objects—simply operating on an object often does not change the object. The object itself (number, string, or otherwise) is usually changed only when you explicitly set the object's label (or pointer) to the new value, as follows:

```
>>> n1 = 5
>>> n1 ** 2        # Display value of 5^2
25
>>> n1           # n1, however is still set to 5
5
>>> n1 = n1 ** 2  # Set n1 = 5^2
>>> n1          # Now n1 is set to 25
25
```

# Lists

The next type of built-in object we'll cover is the list. You can throw any kind of object into a list. Lists are usually created by adding [ and ] around an object or a group of objects. You can do the same kind of clever “slicing” as with strings. Slicing refers to our string example of returning only a subset of the object's values—for example, from the fifth value to the tenth with label1[5:10]. Let's look at how the list type works: