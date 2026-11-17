# Control statements and loops

Python has several types of control statements and loops. Let’s look at them.

# if...else

The if statement executes a block of code if the specified condition is true. Whereas, the else statement executes a block of code if the specified condition is false. Furthermore, you can use the elif (else if) statement to check the new condition if the first condition is false.

Syntax:

```
if condition1:
    Code to be executed
elif condition2:
    Code to be executed
else:
    Code to be executed
```

# Example: 1.8 If...else control statement

```
1. x = 26
2. y = 17
3.
4. if(x > y):
5.     print('x is greater than y')
6. elif(x == y):
7.     print('x and y are equal')
8. else:
9.     print('y is greater than x')
10.
11.x is greater than y
```

# for loop

It is used when you want to iterate over a sequence or iterable such as a string, list, dictionary, or tuple. It will execute a block of code a certain number of times.

Syntax: