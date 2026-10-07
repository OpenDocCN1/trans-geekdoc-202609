means that you can write unit tests for your code as well.
Listing 1.14 displays the contents of Hello.py that shows you how to use sys.argv to check the number of command line parameters.

# LISTING 1.14 Hello.py

```
import sys

def main():
    if len(sys.argv) >= 2:
        name = sys.argv[1]
    else:
        name = 'World'
    print 'Hello', name

# Standard boilerplate to invoke the main()
function
if __name__ == '__main__':
    main()
```

Listing 1.14 defines the main() function that checks the number of command-line parameters: if this value is at least 2, then the variable name is assigned the value of the second parameter (the first parameter is Hello.py), otherwise name is assigned the value Hello. The print statement then prints the value of the variable name.

The final portion of Listing 1.14 uses conditional logic to determine whether or not to execute the main() function.

# SUMMARY

This chapter showed you how to work with numbers and perform arithmetic operations on numbers, and then you learned how to work with strings and string operations.