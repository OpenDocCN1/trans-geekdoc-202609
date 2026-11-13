# # File processing in Python

To process files in Python, use the following functions:

+   - open()
+   - read()
+   - readline()
+   - write()
+   - close()

The open() function takes two parameters: the name of the file and the mode the file should open in. There are several modes available in Python:

+   - "w" – write mode: The file is opened for writing text to it:
+     - If the file does not exist, it creates a new file with the given name.
+     - When adding text in write mode, the new text added will overwrite the previous text.
+   - "a" – append mode: The file is opened for adding text at the end of the file:
+     - If the file does not exist, it creates a new file with the given name.
+     - When adding text in append mode, the new text is added at the end of the file, so the previous text is not overwritten.
+   - "r" – read mode: The file is opened for reading data from it:
+     - If the file does not exist, it will throw an error.

The default mode is the read mode. Therefore, writing `f = open("numbers.txt")` is the same as writing `f = open("numbers.txt", "r")`.

```
```python
f = open("numbers.txt", "w")
f.write("First line")
f.close()
```
```

The code above will create a file called `numbers.txt` in case it does not exist on the disk, and it will write the given text to it. Once this is done, the file is closed. If the program is run again with a different line of text, the existing text in the file will be overwritten.

```
```python
f = open("numbers.txt", "w")
f.write("First line")
f.close()
f = open("numbers.txt", "r")
print(f.read())
f.close()
```
```

The code above opens the file, writes the given text to the file and closes it. Afterwards, the file is open in read mode, the line is read and displayed, and then the file is closed.
read() will read the entire content of the file so, if the file contains several lines, as shown below, they will all be displayed. Although this might seem an inefficient method, it can be