# CHAPTER 11 TOOLS OF THE TRADE: PYTHON AND R

Note that both Python and R record a variable's data type based on the value assigned to it. So if you have assigned a variable the value of 7, Python and R will track it as an int until it's reassigned to something else.

# Python

Python has all the basic data types plus two similar list types (called a list and a tuple, respectively) and the map (called a dict, short for dictionary). Lists and tuples are indexed starting at 0, so the first element is at position 0, the second at 1, and so on. Python has only one integer data type, int, in the current popular version (earlier versions had a larger integer long). It also has only one decimal type, float (int used to have a larger decimal type called double). The current int and float are as large as the previous long and double, which is there's no need for them in modern code. The Boolean type is called bool and the complex type is called complex. Strings are stored in the str data type. You can find out the type by calling the type() function and putting the variable name inside the parentheses.

# R

R also has one of each of all the basic data types. It has two similar list types, vector and list indexed starting with 1, unlike Python. The integer data type is called integer and the decimal type is called numeric. The complex type is simply called complex. Strings are built with the character data type. Finally, the Boolean type is called logical. You can check the type of any value by calling the class() function with the variable name inside the parentheses.

# Operations

Operations are just the instructions on the action to take in programming languages. For instance, if you want to do mathematical operations in code, you'd use the operators seen in Table 11-2. These all work identically