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

# Python Objects

The main thing you need to understand really well is the different types of objects that Python can use to hold data and how it manipulates that data. We’ll cover the big five data types: strings, numbers, lists, dictionaries, and files. After that, we’ll cover some basic syntax and the bare minimum on networking.

# Strings

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