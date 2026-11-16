
resumes with the next statement after the `try` statement. Again, that's the end of the loop, so execution resumes with the next loop iteration.

### Flow of Control for a Successful Division

Now let's consider the flow of control, based on the last three lines of the sample output:

- First, the user enters 100 for the numerator in response to line 7 in the `try` suite.
- Next, the user enters 7 for the denominator in response to line 8 in the `try` suite.
- At this point, we have two valid integer values and the denominator is not 0, so line 9 successfully divides 100 by 7.

When no exceptions occur in the `try` suite, program execution resumes with the `else` clause (if there is one); otherwise, program execution resumes with the next statement after the `try` statement. In this example's `else` clause, we display the division result, then terminate the loop, and the program terminates.

## 9.8.3 Catching Multiple Exceptions in One `except` Clause

It's relatively common for a `try` clause to be followed by several `except` clauses to handle various types of exceptions. If several `except` suites are identical, you can catch those exception types by specifying them as a tuple in a single `except` handler, as in:

```
except (type1, type2, ...) as variable_name:
```

The `as` clause is optional. Typically, programs do not need to reference the caught exception object directly. If you do, you can use the variable in the `as` clause to reference the exception object in the `except` suite.

## 9.8.4 What Exceptions Does a Function or Method Raise?

Exceptions may surface via statements in a `try` suite, via functions or methods called directly or indirectly from a `try` suite, or via the Python interpreter as it executes the code (for example, `ZeroDivisionError`).

Before using any function or method, read its online API documentation, which specifies what exceptions are thrown (if any) by the function or method and indicates reasons why such exceptions may occur. Next, read the online API documentation for each exception type to see potential reasons why such an exception occurs.

## 9.8.5 What Code Should Be Placed in a try suite?

Place in a try suite a significant logical section of a program in which several statements can raise exceptions, rather than wrapping a separate try statement around every statement that raises an exception. However, for proper exception-handling granularity, each try statement should enclose a section of code small enough that, when an exception occurs, the specific context is known and the except handlers can process the exception properly. If many statements in a try suite raise the same exception types, multiple try statements may be required to determine each exception's context.

## 9.9 FINALLY CLAUSE

Operating systems typically can prevent more than one program from manipulating a file at once. When a program finishes processing a file, the program should close it to release the resource so other programs can access it. Closing the file helps prevent a resource leak.

### The finally Clause of the try Statement

A try statement may have a finally clause after any except clauses or the else clause. The finally clause is guaranteed to execute. 8 In other languages that have finally, this makes the finally suite an ideal location to place resource-deallocation code for resources acquired in the corresponding try suite. In Python, we prefer the with statement for this purpose and place other kinds of “clean up” code in the finally suite.

8 The only reason a finally suite will not execute if program control enters the corresponding try suite is if the application terminates first, for example by calling the sys module's exit function.

### Example

The following IPython session demonstrates that the finally clause always executes, regardless of whether an exception occurs in the corresponding try suite. First, let’s consider a try statement in which no exceptions occur in the try suite:

Click here to view code image

```
In [1]: try:
....     print('try suite with no exceptions raised')
....     except:
....     print('this will not execute')
....     else:
....     print('else executes because no exceptions in the try suite')
....     finally:
....     print('finally always executes')
....

try suite with no exceptions raised
else executes because no exceptions in the try suite
finally always executes

In [2]:
```

The preceding `try` suite displays a message but does not raise any exceptions. When program control successfully reaches the end of the `try` suite, the `except` clause is skipped, the `else` clause executes and the `finally` clause displays a message showing that it always executes. When the `finally` clause terminates, program control continues with the next statement after the `try` statement. In an IPython session, the next `In []` prompt appears.

Now let's consider a `try` statement in which an exception occurs in the `try` suite:

Click here to view code image

```
In [2]: try:
....     print('try suite that raises an exception')
....     int('hello')
....     print('this will not execute')
....     except ValueError:
....     print('a ValueError occurred')
....     else:
....     print('else will not execute because an exception occurred')
....     finally:
....     print('finally always executes')
....

try suite that raises an exception
a ValueError occurred
finally always executes

In [3]:
```

This `try` suite begins by displaying a message. The second statement attempts to convert the string 'hello' to an integer, which causes the `int` function to raise a ValueError. The try suite immediately terminates, skipping its last print statement. The except clause catches the ValueError exception and displays a message. The else clause does not execute because an exception occurred. Then, the finally clause displays a message showing that it always executes. When the finally clause terminates, program control continues with the next statement after the try statement. In an IPython session, the next In [] prompt appears.

### Combining with Statements and try except Statements

Most resources that require explicit release, such as files, network connections and database connections, have potential exceptions associated with processing those resources. For example, a program that processes a file might raise IOErrors. For this reason, robust file-processing code normally appears in a try suite containing a with statement to guarantee that the resource gets released. The code is in a try suite, so you can catch in except handlers any exceptions that occur and you do not need a finally clause because the with statement handles resource deallocation.

To demonstrate this, first let's assume you're asking the user to supply the name of a file and they provide that name incorrectly, such as gradez.txt rather than the file we created earlier grades.txt. In this case, the open call raises a FileNotFoundError by attempting to open a non-existent file:

Click here to view code image

```
In [3]: open('gradez.txt')
------------------------------------------------------------
FileNotFoundError                        Traceback (most recent call last)
ipython-input-3-b7f41b2d5969> in <module>()
----> 1 open('gradez.txt')

FileNotFoundError: [Errno 2] No such file or directory: 'gradez.txt'
```

To catch exceptions like FileNotFoundError that occur when you try to open a file for reading, wrap the with statement in a try suite, as in:

Click here to view code image

```
In [4]: try:
    ...:     with open('gradez.txt', 'r') as accounts:
    ...:         print(f'{"ID":<3}{"Name":<7}{"Grade"}')
    ...:         for record in accounts:
    ...:             student_id, name, grade = record.split()
    ...:             print(f'{student_id:<3}{name:<7}{grade}')
    ...: except FileNotFoundError:
    ...:     print('The file name you specified does not exist')
    ...:
The file name you specified does not exist
```

## 9.10 EXPLICITLY RAISING AN EXCEPTION

You've seen various exceptions raised by your Python code. Sometimes you might need to write functions that raise exceptions to inform callers of errors that occur. The raise statement explicitly raises an exception. The simplest form of the raise statement is

```
raise ExceptionClassName
```

The raise statement creates an object of the specified exception class. Optionally, the exception class name may be followed by parentheses containing arguments to initialize the exception object—typically to provide a custom error message string. Code that raises an exception first should release any resources acquired before the exception occurred. In the next section, we'll show an example of raising an exception.

In most cases, when you need to raise an exception, it's recommended that you use one of Python's many built-in exception types 9 listed at:

9 You may be tempted to create custom exception classes that are specific to your application. We'll say more about custom exceptions in the next chapter.

https://docs.python.org/3/library/exceptions.html

## 9.11 (OPTIONAL) STACK UNWINDING AND TRACEBACKS

Each exception object stores information indicating the precise series of function calls that led to the exception. This is helpful when debugging your code. Consider the following function definitions—function1 calls function2 and function2 raises an Exception:

Click here to view code image

```
In [1]: def function1():
...:     function2()
```
