examples of text files.

A binary file stores the data in the same manner as stored in the memory. The mp3 files, word documents are some of the examples of binary files. You cannot read a binary file using a text editor.

In Python language, file processing takes the following steps.

+   - Open a file that returns a filehandle.
- Use the handle to read or write action.
- Close the filehandle.

Before you perform a read or write operation to a file in Python, you must open it first. And as the read/write transaction finishes, you should close it to free the resources connected with the file.

Let's now look at each step in detail.

**Access_mode:** This is represented with an integer e.g read, write, and append. The default setting is the read-only <r>.

**Buffering:** The default value for buffering is 0. A zero value shows that buffering will not happen. If the value is 1, then the line buffering will happen when accessing the file. If it's more than 1, then the buffering action will proceed based on the size.

**File_name:** This is a string that represents the name of the file you want to access.

# File open modes in Python language

```
<r>
<rb+>
<rb>
<w+>
<wb+>
<r+>
<w>
<wb>
```

# Python File Object Properties

Once you call the Python () function, it returns an object, which is the filehandle. Additionally, you need to understand that Python files have different features. And you can take advantage of the filehandle to list the features of a file it belongs.

# Close a File in Python

It is good always to close a file when you finish your work. However, Python