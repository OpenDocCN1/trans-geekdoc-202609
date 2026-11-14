

```
% cat > hello.py
print 'Hello, world!'
^D   # This is simple CTRL+D being pressed to break out
% python hello.py
Hello, world!
```

Starting in Python 3, print is no longer a dedicated statement and is a true function.2 This was a necessary change and requires the use of parentheses as with normal function calls. The following is “Hello, world!” in Python 3.0:

```
% python
>>> print ("Hello, world!")
Hello, world!
```

## Python Objects

The main thing you need to understand really well is the different types of objects that Python can use to hold data and how it manipulates that data. We’ll cover the big five data types: strings, numbers, lists, dictionaries, and files. After that, we’ll cover some basic syntax and the bare minimum on networking.

## Strings

You already used one string object in the section “Hello, World!” in Python.” Strings are used in Python to hold text. The best way to show how easy it is to use and manipulate strings is to demonstrate the technique. The following works with both Python 2.7 or Python 3:

```
% python
>>> string1 = 'Dilbert'
>>> string2 = 'Dogbert'
>>> string1 + string2
'DilbertDogbert'
>>> string1 + " Asok " + string2
'Dilbert Asok Dogbert'
>>> string3 = string1 + string2 + "Wally"
>>> string3
'DilbertDogbertWally'
```

```
>>> string3[2:10] # string 3 from index 2 (0-based) to 10
'lbertDog'
>>> string3[0]
'D'
>>> len(string3)
19
>>> string3[14:] # string3 from index 14 (0-based) to end
'Wally'
>>> string3[-5:] # Start 5 from the end and print the rest
'Wally'
>>> string3.find('Wally') # index (0-based) where string starts
14
>>> string3.find('Alice') # -1 if not found
-1
>>> string3.replace('Dogbert','Alice') # Replace Dogbert with Alice
'DilbertAliceWally'
>>> print('AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA') # 30 A's the hard way
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
>>> print ('A' * 30) # 30 A's the easy way
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
```

These are the basic string-manipulation functions you'll use when working with simple strings. The syntax is simple and straightforward, just as you'll come to expect from Python. One important distinction to make right away is that each of those strings (we named them string1, string2, and string3) is simply a pointer—for those familiar with C—or a label for a blob of data out in memory someplace. One concept that sometimes trips up new programmers is the idea of one label (or pointer) pointing to another label. The following code and Figure 2-1 demonstrate this concept:

![](img/5f597c6a70133069118d9e804ace3775_74_0.png)

Figure 2-1 Two labels pointing at the same string in memory

```
>>> label1 = 'Dilbert'
>>> label2 = label1
```

At this point, we have a blob of memory somewhere with the Python string 'Dilbert' stored. We also have two labels pointing at that blob of memory. If we then change label1's assignment, label2 does not change:

```
... continued from above
>>> label1 = 'Dogbert'
>>> label2
'Dilbert'
```

As you see next in Figure 2-2, label2 is not pointing to label1, per se. Rather, it’s pointing to the same thing label1 was pointing to until label1 was reassigned.

![](img/5f597c6a70133069118d9e804ace3775_75_0.png)

Figure 2-2 Label1 is reassigned to point to a different string.

## Numbers

Similar to Python strings, numbers point to an object that can contain any kind of number. It will hold small numbers, big numbers, complex numbers, negative numbers, and any other kind of number you can dream up. The syntax is just as you’d expect:

```
>>> n1=5   # Create a Number object with value 5 and label it n1
>>> n2=3
>>> n1 * n2
15
>>> n1 ** n2      # n1 to the power of n2 (5^3)
125
>>> 5 / 3, 5 % 3      # Divide 5 by 3, then 5 modulus 3
(1.6666666666666667, 2)
# In Python 2.7, the above 5 / 3 calculation would not result in a float without
# specifying at least one value as a float.
>>> n3 = 1        # n3 = 0001 (binary)
>>> n3 << 3       # Shift left three times: 1000 binary = 8
8
>>> 5 + 3 * 2      # The order of operations is correct
11
```

Now that you’ve seen how numbers work, we can start combining objects. What happens when we evaluate a string plus a number?

```
>>> s1 = 'abc'
>>> n1 = 12
>>> s1 + n1
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: Can't convert 'int' object to str implicitly
```

Error! We need to help Python understand what we want to happen. In this case, the only way to combine ‘abc’ and 12 is to turn 12 into a string. We can do that on the fly:

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

## Lists

The next type of built-in object we'll cover is the list. You can throw any kind of object into a list. Lists are usually created by adding [ and ] around an object or a group of objects. You can do the same kind of clever “slicing” as with strings. Slicing refers to our string example of returning only a subset of the object's values—for example, from the fifth value to the tenth with label1[5:10]. Let's look at how the list type works:

```
>>> mylist = [1,2,3]
>>> len(mylist)
3
>>> mylist*4      # Display mylist, mylist, mylist, mylist
[1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3]
>>> 1 in mylist    # Check for existence of an object
True
>>> 4 in mylist
False
>>> mylist[1:]     # Return slice of list from index 1 and on
[2, 3]
>>> biglist = [['Dilbert', 'Dogbert', 'Catbert'],
...  ['Wally', 'Alice', 'Asok']]   # Set up a two-dimensional list
>>> biglist[1][0]
'Wally'
>>> biglist[0][2]
'Catbert'
>>> biglist[1] = 'Ratbert'       # Replace the second row with 'Ratbert'
>>> biglist
[['Dilbert', 'Dogbert', 'Catbert'], 'Ratbert']
>>> stacklist = biglist[0]       # Set another list = to the first row
>>> stacklist
['Dilbert', 'Dogbert', 'Catbert']
>>> stacklist = stacklist + ['The Boss']
>>> stacklist
['Dilbert', 'Dogbert', 'Catbert', 'The Boss']
>>> stacklist.pop()              # Return and remove the last element
'The Boss'
>>> stacklist.pop()
'Catbert'
>>> stacklist.pop()
'Dogbert'
>>> stacklist
['Dilbert']
>>> stacklist.extend(['Alice', 'Carol', 'Tina'])
>>> stacklist
['Dilbert', 'Alice', 'Carol', 'Tina']
>>> stacklist.reverse()
>>> stacklist
['Tina', 'Carol', 'Alice', 'Dilbert']
>>> del stacklist[1]             # Remove the element at index 1
>>> stacklist
['Tina', 'Alice', 'Dilbert']
```

Next, we’ll take a quick look at dictionaries and then files, and then we’ll put all the elements together.

## Dictionaries

Dictionaries are similar to lists, except that an object stored in a dictionary is referenced by a key, not by the index of the object. This turns out to be a very convenient mechanism for storing and retrieving data. Dictionaries are created by adding { and } around a key-value pair, like this:

```
>>> d = { 'hero' : 'Dilbert' }
>>> d['hero']
'Dilbert'
>>> 'hero' in d
True
>>> 'Dilbert' in d   # Dictionaries are indexed by key, not value
False
>>> d.keys()    # keys() returns a list of all objects used as keys
dict_keys([['hero']])
>>> d.values()  # values() returns a list of all objects used as values
dict_keys([['Dilbert']])
>>> d['hero'] = 'Dogbert'
>>> d
{'hero': 'Dogbert'}
>>> d['buddy'] = 'Wally'
>>> d['pets'] = 2      # You can store any type of object, not just strings
>>> d
{'hero': 'Dogbert', 'buddy': 'Wally', 'pets': 2}
```

We'll use dictionaries more in the next section as well. Dictionaries are a great way to store any values that you can associate with a key, where the key is a more useful way to fetch the value than a list's index.

## Files with Python

File access is as easy as the rest of Python’s language. Files can be opened (for reading or for writing), written to, read from, and closed. Let’s put together an example using several different data types discussed here, including files. This example assumes that we start with a file named targets and that we transfer the file contents into individual vulnerability target files. (We can hear you saying, “Finally, an end to the Dilbert examples!”) Note the required indentation being used within blocks.

