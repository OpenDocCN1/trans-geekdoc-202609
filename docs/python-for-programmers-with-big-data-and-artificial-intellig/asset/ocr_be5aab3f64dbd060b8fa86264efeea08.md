```
return number ** 2
```

first squares number, then terminates the function and gives the result back to the
caller. In this example, the first caller is in snippet [2], so IPython displays the result
in Out[2]. The second caller is in snippet [3], so IPython displays the result in
Out[3].

Function calls also can be embedded in expressions. The following code calls square
first, then print displays the result:

lick here to view code image

```
In [4]: print('The square of 7 is', square(7))
The square of 7 is 49
```

There are two other ways to return control from a function to its caller:

+   Executing a return statement without an expression terminates the function and
+   implicitly returns the value None to the caller. The Python documentation states
+   that None represents the absence of a value. None evaluates to False in conditions.

+   When there's no return statement in a function, it implicitly returns the value
+   None after executing the last statement in the function's block.

# Local Variables

Though we did not define variables in square's block, it is possible to do so. A
function's parameters and variables defined in its block are all local variables—they
can be used only inside the function and exist only while the function is executing.
Trying to access a local variable outside its function's block causes a NameError,
indicating that the variable is not defined.

# Accessing a Function's Docstring via IPython's Help Mechanism

IPython can help you learn about the modules and functions you intend to use in your
code, as well as IPython itself. For example, to view a function's docstring to learn how
to use the function, type the function's name followed by a question mark (?):

lick here to view code image