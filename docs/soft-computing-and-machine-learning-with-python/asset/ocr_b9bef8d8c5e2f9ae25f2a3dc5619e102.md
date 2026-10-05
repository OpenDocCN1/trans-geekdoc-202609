Note that the newline characters ('\n') are included in the return value. You can use the string.rstrip() method to remove trailing newlines, but beware: it also removes any other trailing whitespace.

```
>>> 'alligator juniper\n'.rstrip()
'alligator juniper'
```

```
>>> 'eat all my trailing spaces    \n'.rstrip()
'eat all my trailing spaces'
```

To read all the lines in a file at once, use the .readlines() method. This returns a list whose elements are strings, one per line.

```
>>> treeFile=open("trees")
>>> treeFile.readlines()
['yew\n', 'oak\n', 'alligator juniper\n']
```

A general method for reading files is the .read() method. Used without arguments, it reads the entire file and returns it to you as one string.

```
>>> treeFile = open("trees")
>>> treeFile.read()
'yew\noak\nalligator juniper\n'
```

To read exactly N characters from a file F, use the method F.read(N). If N characters remain in the file, you will get them back as an N-character string. If fewer than N characters remain, you will get the remaining characters in the file (if any).

```
>>> treeFile = open ("trees")
>>> treeFile.read(1)
'y'
>>> treeFile.read(5)
'ew\noa'
>>> treeFile.read(50)
'k\nalligator juniper\n'
>>> treeFile.read(80)
```

One of the easiest ways to read the lines from a file is to use a for statement. Here is an example: