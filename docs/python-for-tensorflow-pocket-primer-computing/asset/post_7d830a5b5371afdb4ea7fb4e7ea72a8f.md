
If you have reached the limits of what you have learned here and want to get further technical depth regarding TensorFlow 1.x, consider the recommended book that is mentioned earlier in this Preface, as well as an upcoming book about TensorFlow 2.

# COMPANION FILES

Code samples and figures appearing in the book may be obtained by writing to the publisher at info@merclearning.com.

# INTRODUCTION TO PYTHON

This chapter provides a fast-paced introduction to Python, along with tools for installing Python modules, and examples of how to work with some data types in Python. This chapter does not contain any historical information about Python, nor topics such as creating Python class, inheritance, threads, or any other topics that are beyond introductory material. The reason is simple: the purpose of this chapter is to familiarize you with enough Python so that you can learn the material in subsequent chapters.

The first part of this chapter covers the installation of Python, some Python environment variables, and how to use the Python interpreter. You will see Python code samples and also how to save Python code in text files that you can launch from the command line. The second part of this chapter shows you how to work with simple data types, such as numbers, fractions, and strings. The final part of this chapter discusses exceptions and how to use them in Python scripts.

If you like to read documentation, one of the best third party documentation publications is pymotw (“Python Module of the Week”) by Doug Hellman, and his home page is:

http://pymotw.com/2/

> NOTE The Python scripts in this book are for Python 2.7.5 and although most of them are probably compatible with Python 2.6, these scripts require a modest degree of conversion (e.g., the syntax of the print() command) in order to be compatible with Python 3.

# TOOLS FOR PYTHON

The Anaconda Python distribution is available for Windows, Linux, and Mac, and it is downloadable here:
http://continuum.io/downloads

Anaconda is well suited for modules such as NumPy and SciPy (discussed in Chapter 2 and Chapter 4), and if you are a Windows user, Anaconda appears to be a better alternative.

# easy_install and pip

Both easy_install and pip are very easy to use when you need to install Python modules.

Whenever you need to install a Python module (and there are many in this book), use easy_install or pip with the following syntax:

```
easy_install <module-name>
pip install <module-name>
```

> **NOTE** Python-based modules are easier to install, whereas modules with code written in C are usually faster but more difficult in terms of installation.

# virtualenv

The virtualenv tool enables you to create isolated Python environments, and its home page is here:
http://virtualenv.org/en/latest/virtualenv.html
virtualenv addresses the problem of preserving the correct dependencies and versions (and indirectly, permissions) for different applications. If you are a Python novice you might not need virtualenv right now, but keep this tool in mind.

# IPython

Another very good tool is IPython (which won a Jolt award), and its home page is here:

http://ipy.org/install.html
Two very nice features of IPython are tab expansion and “?”
and an example of tab expansion is shown here:

```python
Python 2.7.5 -- Anaconda 1.6.1 (x86_64) -- (default, Jun 28
              2013, 22:20:13)
Type "copyright", "credits" or "license" for more
Information.
```

```
IPython 0.13.2 -- An enhanced Interactive Python.
? -> Introduction and overview of IPython's features.
%quickref -> IPython's own help system.
help
object? -> Details about 'object', use 'object??' for
              extra details.
```

```
[1] di divmod
%dirs dir divmod
```

In the preceding session, if you type the characters di, IPython
ponds with the following line that contains all the functions that
start with the letters di:

```
%dirs dict divmod
```

If you enter a question mark (“?”), ipython provides textual assistance, the first part of which is here:

# IPython -- An enhanced Interactive Python
==================================

IPython offers a combination of convenient shell
features, special commands and a history mechanism
for both input (command history) and output
(results caching, similar to Mathematica). It is
intended to be a fully compatible replacement for
the standard Python interpreter, while offering
vastly improved functionality and flexibility.

The next section shows you how to check whether or not Python is installed on your machine, and also where you can download Python.

# PYTHON INSTALLATION

Before you download anything, check if you have Python already installed on your machine (which is likely if you have a Macbook or a Linux machine) by typing the following command in a command shell:

```
python -V
```

The output for the Macbook used in this book is here:

Python 2.7.5 :: Anaconda 1.6.1 (x86_64)

> **NOTE** Install Python 2.7.5 (or as close as possible to this version) on your machine so that you will have the same version of Python that was used to test the Python scripts in this book.

If you need to install Python on your machine, navigate to the Python home page and select the download link or navigate directly to this website:

http://www.python.org/

Use any text editor to create, edit, and save Python scripts as text files.

# SETTING THE PATH ENVIRONMENT (WINDOWS)

The PATH variable specifies a list of directories that are searched whenever you specify an executable.

# LAUNCHING PYTHON ON MACHINE

There are three different ways to launch Python:

- Use the Python Interpreter
- Launch Python scripts from the command line
- Use an IDE

# Python Interactive Interpreter

Launch the Python interpreter by opening a command shell and typing the following:

```
Python 2.7.5 :: Anaconda 1.6.1 (x86_64) -- (default, Jun 28
              2013, 22:20:13)
Type "copyright", "credits" or "license" for more
Information.
```

Now type the expression 2 + 7 at the prompt:

```
>>> 2 + 7
9
```

Press ctrl-d to exit the shell. You can launch any Python script from the command line by preceding it with the word "python". For example, if you have a Python script myscript.py, launch it as:

```
python myscript.py
```

As a simple illustration, suppose that the Python script myscript.py contains the following code:

```
print 'Hello World from Python'
print '2 + 7 = ', 2+7
```

When you launch the preceding Python script you will see the following output:

```
Hello World from Python
2 + 7 = 9
```

# PYTHON IDENTIFIERS

A Python identifier is the name of a variable, function, class, module, or other Python object, and a valid identifier conforms to the following rules:

- starts with a letter A to Z, or to a z, or an underscore (_)
- zero or more letters, underscores, and digits (0 to 9)

**NOTE** Python identifiers cannot contain characters such as @, $, and %.

Python is a case-sensitive language, so Ab and abc are different identifiers in Python. In addition, Python has the following naming convention:

- Class names start with an uppercase letter and all other identifiers with a lowercase letter
- an initial underscore is used for private identifiers
- two initial underscores are used for strongly private identifiers

A Python identifier with two initial underscore and two trailing underscore characters indicates a language-defined special name.

# LINES, INDENTATION, AND MULTI-LINES

Unlike other languages (such as Java or Objective-C), Python uses indentation instead of curly braces for code blocks. Indentation must be consistent in a code block, as shown here:

```
if True:
    print "ABC"
    print "DEF"

else:
    print "ABC"
    print "GHJ"
```
