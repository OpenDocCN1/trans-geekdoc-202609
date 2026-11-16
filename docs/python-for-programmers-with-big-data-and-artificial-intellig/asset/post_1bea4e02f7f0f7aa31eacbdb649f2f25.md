
We'll continue our pandas discussion in the next chapter's Intro to Data Science section, and we'll use pandas in several later chapters.

### 8.14 WRAP-UP

In this chapter, we presented various string formatting and processing capabilities. You formatted data in f-strings and with the string method format. We showed the augmented assignments for concatenating and repeating strings. You used string methods to remove whitespace from the beginning and end of strings and to change their case. We discussed additional methods for splitting strings and for joining iterables of strings. We introduced various character-testing methods.

We showed raw strings that treat backslashes (\) as literal characters rather than the beginning of escape sequences. These were particularly useful for defining regular expressions, which often contain many backslashes.

Next, we introduced the powerful pattern-matching capabilities of regular expressions with functions from the re module. We used the fullmatch function to ensure that an entire string matched a pattern, which is useful for validating data. We showed how to use the replace function to search for and replace substrings. We used the split function to tokenize strings based on delimiters that match a regular expression pattern. Then we showed various ways to search for patterns in strings and to access the resulting matches.

In the Intro to Data Science section, we introduced the synonyms data munging and data wrangling and showed a sample data munging operation, namely transforming data. We continued our discussion of pandas Series and DataFrames by using regular expressions to validate and munge data.

In the next chapter, we'll continue using various string-processing capabilities as we introduce reading text from files and writing text to files. We'll use the csv module for manipulating comma-separated value (CSV) files. We'll also introduce exception handling so we can process exceptions as they occur, rather than displaying a traceback.

## 9 Files and Exceptions

### Objectives

In this chapter, you'll:

- Understand the notions of files and persistent data.
- Read, write and update files.
- Read and write CSV files, a common format for machine-learning datasets.
- Serialize objects into the JSON data-interchange format—commonly used to transmit over the Internet—and deserialize JSON into objects.
- Use the `with` statement to ensure that resources are properly released, avoiding “resource leaks”.
- Use the `try` statement to delimit code in which exceptions may occur and handle those exceptions with associated `except` clauses.
- Use the `try` statement’s `else` clause to execute code when no exceptions occur in the `try` suite.
- Use the `try` statement’s `finally` clause to execute code regardless of whether an exception occurs in the `try`.
- `raise` exceptions to indicate runtime problems.
- Understand the traceback of functions and methods that led to an exception.
- Use pandas to load into a `DataFrame` and process the Titanic Disaster CSV dataset.

### Outline

- .1 Introduction
- .2 Files
- .3 Text-File Processing
- .3.1 Writing to a Text File: Introducing the with Statement
- .3.2 Reading Data from a Text File
- .4 Updating Text Files
- .5 Serialization with JSON
- .6 Focus on Security: pickle Serialization and Deserialization
- .7 Additional Notes Regarding Files
- .8 Handling Exceptions
- .8.1 Division by Zero and Invalid Input
- .8.2 try Statements
- .8.3 Catching Multiple Exceptions in One except Clause
- .8.4 What Exceptions Does a Function or Method Raise?
- .8.5 What Code Should Be Placed in a try Suite?
- .9 finally Clause
- .10 Explicitly Raising an Exception
- .11 (Optional) Stack Unwinding and Tracebacks
- .12 Intro to Data Science: Working with CSV Files
- .12.1 Python Standard Library Module csv
- .12.2 Reading CSV Files into Pandas DataFrames
- .12.3 Reading the Titanic Disaster Dataset

### 9.1 INTRODUCTION

Variables, lists, tuples, dictionaries, sets, arrays, pandas Series and pandas DataFrames offer only *temporary* data storage. The data is lost when a local variable “goes out of scope” or when the program terminates. **Files** provide long-term retention of typically large amounts of data, even after the program that created the data terminates, so data maintained in files is persistent. Computers store files on secondary storage devices, including solid-state drives, hard disks and more. In this chapter, we explain how Python programs create, update and process data files.

We consider text files in several popular formats—plain text, JSON (JavaScript Object Notation) and CSV (comma-separated values). We’ll use JSON to serialize and deserialize objects to facilitate saving those objects to secondary storage and transmitting them over the Internet. Be sure to read this chapter’s Intro to Data Science section in which we’ll use both the Python Standard Library’s `csv` module and pandas to load and manipulate CSV data. In particular, we’ll look at the CSV version of the Titanic disaster dataset. We’ll use many popular datasets in upcoming data-science case-study chapters on natural language processing, data mining Twitter, IBM Watson, machine learning, deep learning and big data.

As part of our continuing emphasis on Python security, we’ll discuss the security vulnerabilities of serializing and deserializing data with the Python Standard Library’s `pickle` module. We recommend JSON serialization in preference to `pickle`.

We also introduce **exception handling**. An exception indicates an execution-time problem. You’ve seen exceptions of types `ZeroDivisionError`, `NameError`, `ValueError`, `StatisticsError`, `TypeError`, `IndexError`, `KeyError` and `RuntimeError`. We’ll show how to deal with exceptions as they occur by using `try` statements and associated `except` clauses to *handle* exceptions. We’ll also discuss the `try` statement’s `else` and `finally` clauses. The features presented here help you write *robust, fault-tolerant* programs that can deal with problems and continue executing or *terminate gracefully*.

### 9.2 FILES

Programs typically request and release resources (such as files) during program execution. Often, these are in limited supply or can be used only by one program at a time. We show how to guarantee that after a program uses a resource, it's released for use by other programs, even if an exception has occurred. You'll use the with statement for this purpose.

Python views a text file as a sequence of characters and a binary file (for images, videos and more) as a sequence of bytes. As in lists and arrays, the first character in a text file and byte in a binary file is located at position 0, so in a file of n characters or bytes, the highest position number is n – 1. The diagram below shows a conceptual view of a file:

![](img/34b7fc2f1ee27beb73bca14927d42340_348_0.png)

For each file you open, Python creates a file object that you'll use to interact with the file.

### End of File

Every operating system provides a mechanism to denote the end of a file. Some represent it with an end-of-file marker (as in the preceding figure), while others might maintain a count of the total characters or bytes in the file. Programming languages generally hide these operating-system details from you.

### Standard File Objects

When a Python program begins execution, it creates three standard file objects:

- sys.stdin—the standard input file object
- sys.stdout—the standard output file object, and
- sys.stderr—the standard error file object.

Though these are considered file objects, they do not read from or write to files by default. The input function implicitly uses sys.stdin to get user input from the keyboard. Function print implicitly outputs to sys.stdout, which appears in the command line. Python implicitly outputs program errors and tracebacks to
