Note that the int function does not round a floating-point number to the nearest integer but instead truncates or removes its fractional part.

# Input and Output Functions

Computer programs typically take input data, process them, and output the results. In the program fragments you have seen thus far, the inputs are operands in expressions or arguments to functions, and the outputs are the values returned. When a program is not run from the Python shell but from a system terminal, separate input and output operations are needed to supply data to the program and display its results. For text-based terminal programs, Python provides two functions, named input and print, for this purpose. Although you will write very few such programs in this book, it’s still a good idea to experiment with Python’s input and print functions here, in “sandbox mode.”

# Output with the print Function

The print function expects zero or more arguments. It evaluates these arguments and converts their values to strings, builds a new string from them with single spaces between them, and displays this string as a single line of text. A line break is automatically displayed as well. The next shell session shows some examples of the use of the print function:

```
>>> print()
>>> print("Hello there!")
Hello there!
>>> print("Text followed by a blank line\n")
Text followed by a blank line
>>> print("Four uses the digit", 4)
Four uses the digit 4
```

Note that print has the effect of stripping off the quotes enclosing each string.

# Input with the input Function

The input function expects an optional string as an argument. If the string is provided, the function displays it as a prompt for an input value and waits for the user to enter some keystrokes. When the user presses the Return or Enter key, the function builds and