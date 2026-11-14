
12. To verify the installation, navigate to the directory where you installed Python and double click on the python.exe file.

## MACINTOSH

1. From the official Python website, click on the “Downloads” icon and select Mac.
2. Click on the “Download Python 3.8.0” button to view all the downloadable files.
3. On the subsequent screen, select the Python version you would like to download. In this book, we will be using the Python 3 version under “Stable Releases.” So scroll down the page and click on the “Download macOS 64-bit installer” link under Python 3.8.0, as shown in the picture below.

![](img/fe3427740784586362e0a35d3200b425_131_0.png)

4. A pop up window titled “python-3.8.0-macosx10.9.pkg” will be shown.
5. Click “Save File” to start downloading the file.
6. Once the download has completed, double click the saved file icon, and an “Install Python” pop window will be shown.
7. Click “Continue” to proceed, and the terms and conditions pop up window will appear.
8. Click Agree and then click “Install.”
9. A notification requesting administrator permission and password will be shown. Enter your system password to start installation.
10. Once the installation has finished, an “Installation was successful” message will appear. Click on the Close button, and you are all set.
11. To verify the installation, navigate to the directory where you installed Python and double click on the python launcher icon that will take you to the Python Terminal.

## LINUX

- For Red Hat, CentOS, or Fedora, install the python3 and python3-devel packages.
- For Debian or Ubuntu, install the python3.x and python3.x-dev packages.
- For Gentoo, install the '=python-3.x.*' ebuild (you may have to unmask it first).

1. From the official Python website, click on the “Downloads” icon and select Linux/UNIX.
2. Click on the “Download Python 3.8.0” button to view all the downloadable files.
3. On subsequent screen, select the Python version you would like to download. In this book, we will be using the Python 3 version under “Stable Releases.” So scroll down the page and click on the “Download Gzipped source tarball” link under Python 3.8.0, as shown in the picture below.
4. A pop up window titled “python-3.7.5.tgz” will be shown.
5. Click “Save File” to begin downloading the file.
6. Once the download has finished, double click the saved file icon, and an “Install Python” pop window will appear.
7. Follow the prompts on the screen to complete the installation process.

![](img/fe3427740784586362e0a35d3200b425_132_0.png)

## Getting Started

With the Python terminal installed on your computer, you can now start writing and executing the Python code. All Python codes are written in a text editor as (.py) files and executed on the Python interpreter command line as shown in the code below, where “nineplanets.py” is the name of the Python file:

```
`"C: \Users\Your Name\python nineplanets.py"`
```

You will be able to test a small code without writing it in a file and simply executing it as a command line itself by typing the code below on the Mac, Windows or Linux command line, as shown below:

```
"C:\\Users\\Your Name\\python"
```

In case the command above does not work, use the code below instead:

```
"C:\\Users\\Your Name\\py"
```

### Indentation

The importance of indentation, which is the number of spaces preceding the code, is fundamental to the Python coding structure. In most programming languages, indentation is added to enhance the readability of the code. However, in Python, the indentation is used to indicate execution of a subset of the code, as shown in the code below:

```
if 7 > 2:
    print('Seven is greater than two')
```

Indentation precedes the second line of code with the print command. If the indentation is skipped and the code was written as below, an error will be triggered:

```
if 7 > 2:
print('Seven is greater than two')
```

The number of spaces can be modified but is required to have at least one space. For example, you can execute the code below with higher indentation, but for a specific set of code same number of spaces must be used, or you will receive an error.

```
if 7 > 2:
    print('Seven is greater than two')
```

### Adding Comments

In Python, comments can be added to the code by starting the code comment lines with a “#,” as shown in the example below:

```
#Any relevant comments will be added here
print('Nine planets')
```

Comments serve as a description of the code and will not be executed by the Python terminal. Make sure to remember that any comments at the end of the code line will lead to the entire code line being skipped by the Python terminal, as shown in the code below. Comments can be very useful in case you need to stop the execution when you are testing the code.

```python
print('Nine Planets') #Comments added here
```

Multiple lines of comments can be added by starting each code line with "#," as shown below:

```python
#Comments added here
#Supplementing the comments here
#Further adding the comments here
print('Nine Planets')
```

## Python Variables

In Python, variables are primarily utilized to save data values without executing a command for it. A variable can be created by simply assigning the desired value to it, as shown in the example below:

```python
A = 999
B = 'Patricia'
print(A)
print(B)
```

A variable could be declared without a specific data type. The data type of a variable can also be modified after it's an initial declaration, as shown in the example below:

```python
A = 999 # A has data type set as int
A = 'Patricia' # A now has data type str
print(A)
```

Some of the rules applied to the Python variable names are as follows:

1. Variable names could be as short as single alphabets or more descriptive words like height, weight, and more.
2. Variable names could only be started with an underscore character or a letter.
3. Variable names must not start with numbers.
4. Variable names can contain underscores or alpha numeric characters. No other special characters are allowed.
5. Variable names are case sensitive. For example, ‘weight,’ ‘Weight,’ and ‘WEIGHT’ will be accounted as 3 separate variables.

## Assigning Value to Variables

In Python, multiple variables can be assigned DISTINCT values in a single code line, as shown in the example below:

```python
A, B, C = 'violet', 'maroon', 'teal'
print(A)
print(B)
print(C)
```

OR multiple variables can be assigned SAME value in a single code line, as shown in the example below:

```python
A, B, C = 'violet'
print(A)
print(B)
print(C)
```

## Python Data Types

Python supports a variety of data types, as listed below. To build a solid understanding of the concept of variables, you must learn all the Python data types.

| Category | Data Type | Example Syntax |
|---|---|---|
| Text | "str" | 'Nine Planets' "Nine Planets" """Nine Planets""" |
| Boolean | "bool" | 'True' 'False' |
| Mapping (mixed data types, associative array of key and value pairs) | "dict" | {'key8': 8.0, 5: True} |
| Sequence (may contain mixed data types) | "list" | [8.0, 'character', True] |
| Sequence (may contain mixed data types) | "tuple" | (8.0, 'character', True) |
| Sequence (may contain mixed data types) | "range" | range(11, 51) range(110, 51, 11, -11, -51, -110) |
| Binary | "bytes" | b'byte sequences' b'byte sequences' bytes([121, 91, 75, 110]) |
| Binary | "bytearray" | bytearray(b'byte sequences') bytearray(b'byte sequences') bytearray([121, 91, 75, 110]) |
| Binary | "memoryview" | |
| Set | "set" | {8.0, 'character', True} |
| (unordered, no duplicates, mixed data types) | "frozenset" | frozenset([8.0, 'character', True]) |
| Numeric | "int" | 35 |
| | "float" | 155e3 |
| | "complex" | 155 + 2.1j |
| Ellipsis (index in NumPy arrays) | "ellipsis" | ... 'Ellipsis' |

To view the data type of any object, you can use the “type()” function as shown in the example below:

```python
A = 'Violet'
print(type(A))
```

## Assigning the Data Type to Variables

A new variable can be created by simply declaring a value for it. This set data value will in turn assign the data type to the variable.

To assign a specific data type to a variable, the constructor functions listed below are used:

| Constructor Functions | Data Type |
|---|---|
| A = str('Nine Planets') | str |
| A = int(55) | Int (Must be a whole number, positive or negative with no decimals, no length restrictions) |
| A = float(14e6) | Float (Floating point number must be positive or negative number with one or more decimals; maybe scientific |
