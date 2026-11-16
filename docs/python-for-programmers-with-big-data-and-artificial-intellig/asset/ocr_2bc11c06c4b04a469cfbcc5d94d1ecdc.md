nteger a string (like 'hello') that does not represent a number:

lick here to view code image

```
In [2]: value = int(input('Enter an integer: '))
Enter an integer: hello
-------------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
ipython-input-2-b521605464d6> in <module>()
----> 1 value = int(input('Enter an integer: '))

ValueError: invalid literal for int() with base 10: 'hello'

In [3]:
```

# 9.8.2 try Statements

Now let's see how to handle these exceptions so that you can enable code to continue processing. Consider the following script and sample execution. Its loop attempts to read two integers from the user, then display the first number divided by the second. The script uses exception handling to catch and handle (i.e., deal with) any ZeroDivisionErrors and ValueErrors that arise—in this case, allowing the user to re-enter the input.

lick here to view code image

```
1 # dividebyzero.py
2 """Simple exception handling example."""
3
4 while True:
5     # attempt to convert and divide values
6     try:
7         number1 = int(input('Enter numerator: '))
8         number2 = int(input('Enter denominator: '))
9         result = number1 / number2
10    except ValueError: # tried to convert non-numeric value to int
11        print('You must enter two integers\n')
12    except ZeroDivisionError: # denominator was 0
13        print('Attempted to divide by zero\n')
14    else: # executes only if no exceptions occur
15        print(f'{number1:.3f} / {number2:.3f} = {result:.3f}')
16        break # terminate the loop
```

lick here to view code image