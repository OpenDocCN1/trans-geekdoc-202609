# A Python 2.7 Programming Tutorial 227

```
1L
>>> treeFile.read(5)
'ew\noa'
>>> treeFile.tell()
6L
>>> treeFile.seek(1, 1)
>>> treeFile.tell()
7L
>>> treeFile.seek(-3, 1)
>>> treeFile.tell()
4L
>>> treeFile.seek(0, 2)
>>> treeFile.tell()
26L
>>> treeFile.seek(-3, 2)
>>> treeFile.tell()
23L
>>> treeFile.read()
'er\n'
```

# Writing Files

To create a disk file, open the file using a statement of this general form:

```
F = open (filename, “w")
```

The second argument, "w", specifies write access. If possible, Python will create an empty file by that name. If there is an existing file by that name, and if you have write permission to it, the existing file will be deleted.

To write some content to the file you are creating, use this method:

```
F.write(s)
```

where s is any string expression.

# Warning

The data you have sent to a file with the .write() method may not actually appear in the disk file until you close it by calling the .close() method on the file.

This is due to a mechanism called buffering. Python accumulates the data you have sent to the file, until a certain amount is present, and then it