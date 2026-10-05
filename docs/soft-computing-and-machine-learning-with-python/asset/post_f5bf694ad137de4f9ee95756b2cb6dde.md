
# Soft Computing and Machine Learning with Python

```python
variable = sequence [0]
block
variable = sequence [1]
block
variable = sequence [-1]
block
```

- The sequence can be any expression that evaluates to a sequence value, such as a list or tuple. The range() function is often used here to generate a sequence of integers.
- For each value in the sequence in turn, the variable is set to that value, and the block is executed.

As with the if statement, the block consists of one or more statements, indented the same amount relative to the if keyword.

This example prints the cubes of all numbers from 1 through 5.

```python
>>> for n in range(1,6):
    print "The cube of {0} is {1}".format(n, n**3)
The cube of 1 is 1
The cube of 2 is 8
The cube of 3 is 27
The cube of 4 is 64
The cube of 5 is 125
```

You may put the body of the loop—that is, the statements that will be executed for each item in the sequence—on the same line as the "for" if you like. If there are multiple statements in the body, separate them with semicolons.

```python
>>> for n in range(1,6): print "{0}**={1}".format(n, n**3),
```

...

```python
1**3=1 2**3=8 3**3=27 4**3=64 5**3=125
```

```python
>>> if 1 > 0: print "Yes";print "One is still greater than zero"
...
Yes
One is still greater than zero
Here is another example of iteration over a list of specific values.
>>> for s in ('a', 'e', 'i', 'o', 'u'):
...
    word = "st" + s + "ck"
...
    print "Pick up the"
...
Pick up the stack
Pick up the steck
Pick up the stick
Pick up the steck
Pick up the stuck
```

# The while Statement

Use this statement when you want to perform a block B as long as a condition C is true:

```python
while C:
    B
...
```

![](img/e1ab17402154bec3fa9a7873fe3ee232_232_0.png)

Here is how a while statement is executed.

- Evaluate C. If the result is true, go to step 2. If it is false, the loop is done, and control passes to the statement after the end of B.
- Execute block B.
- Go back to step 1.

Here is an example of a simple while loop.

```python
>>> i = 1
>>> while i < 100:
... print i,
... i=i* 2
...
```

1 2 4 8 16 32 64

This construct has the potential to turn into an infinite loop, that is, one that never terminates. Be sure that the body of the loop does something that will eventually make the loop terminate.

# Special Branch Statements: break and continue

Sometimes you need to exit a for or while loop without waiting for the normal termination. There are two special Python branch statements that do this:

- If you execute a break statement anywhere inside a for or while loop, control passes out of the loop and on to the statement after the end of the loop.
- A continue statement inside a for loop transfers control back to the top of the loop, and the variable is set to the next value from the sequence if there is. (If the loop was already using the sequence, the effect of continue is the same as break.)

Here are examples of those statements.

```python
>>> i = 0
>>> while i < 100:
... i = i + 3
... if (i % 5 ) == 0:
... break
... print i,
...
```

3 6 9 12

In the example above, when the value of i reaches 15, which has remainder 0 when divided by 5, the break statement exits the loop.

```python
>>> for i in range(50, -1, -1):
... if (i % 100) != 0:
... continue
... print i,
......
```

# HOW TO WRITE A SELF-EXECUTING SCRIPT

So far we have used Python’s mode to demonstrate all features. Now it’s time to learn how to write a complete program. Your program will live in a file called script. To create your script, use your favorite text editor (emacs, vi, whatever), and just type Python statements into it.

How you make it executable depends on your operating system.

- On Windows platforms, be sure to give your script file name that ends in ".py". If Python is installed, double-clicking any script with this ending will use Python to run the script.
- Under Linux and MacOS, the first line of your script must look like this:
  `#!/usr/bin/python`

The path tells the operating system where to find Python. This path will usually be "/usr/local/bin/python", but you can use the "which" command to find path on your computer:

```bash
$ which python
/usr/local/bin/python
```

Once you have created your script, you must also use this command to make it executable: `chmod +x script-name`

Here is a complete script, set up for a typical Linux installation. This script, `powersof2`, prints a table showing the values of 2^n and 2^-n for n in range(1, 2, ..., 12).

```python
#!/usr/local/bin/python

print "Table of powers two"
for n in range(13):
    print "{0:>10d} {1:>15f}".format(n, 2**-n)
```

We use the invocation of this script under the bash shell, and the output:

```bash
./powersof2

# Table of powers two

| n | 2^-n |
| :--- | :--- |
| 0 | 1.00000000000000 |
| 1 | 0.50000000000000 |
| 2 | 0.25000000000000 |
| 3 | 0.12500000000000 |
| 4 | 0.06250000000000 |
| 5 | 0.03125000000000 |
| 6 | 0.01562500000000 |
| 7 | 0.00781250000000 |
| 8 | 0.00390625000000 |
| 9 | 0.00195312500000 |
| 10 | 0.00097656250000 |
| 11 | 0.00048828125000 |
| 12 | 0.00024414062500 |

# def: DEFINING FUNCTIONS

You can define your own functions in Python with the `def` statement.

- Python functions can act like mathematical functions such as `len(s)`, which computes the length of s. In this example, values like s passed to the function are called parameters to the function.
- However, more generally, a Python function is just a container for some Python statements that do some task. A function can take any number of parameters, even zero.

Here is the general form of a Python function definition. It consists of a `def` statement, followed by an indented block called the body of the function.

```python
def name(arg_i, arg_j, ...):
    block
```

The parameters that a function expects are called arguments inside the body of the function.

Here is an example of a function that takes no arguments at all, and does nothing but print some text.

```python
>>> pirateNoises():
    for arrCount in range(7):
        print "Arr!"
...
```

To call this function:

```python
>>> pirateNoises()
Arr! Arr! Arr! Arr! Arr!
```

To call a function in general, use an expression of this form: `name(param_i, param_j, ...)`

Here's a simple example showing argument substitution.

```python
>>> def grocer(nFruits, fruitKind):
    print "Stock: {0} cases of {1}".format(nFruits, fruitKind)
...
```

```python
>>> grocer(37, 'kale')
Stock: 37 cases of kale
>>> grocer(0, "bananas")
```

# Returning Values from a Function

Stock: 0 cases of bananas

So far we have seen some simple functions that take arguments or don't take arguments. How do we define functions like `len()` that return a value?

Anywhere in the body of your function, you can write a return statement that terminates execution of the function and returns to the statement where it was called.

Here is the general form of this statement:

```python
return expression
```

The expression is evaluated, and its value is returned to the caller.

Here is an example of a function that returns a value:

```python
>>> def square(x):
    return x**2
>>> square(9)
81
>>> square(2.5)
6.25
```

- You can omit the expression, and just use a statement of this form:
  * return

In this case, the special placeholder value None is returned.
- If Python executes your function body and never encounters a return statement, the effect is the same as return with no value: the special value None is returned.

Here is another example of a function that returns a value. This function computes the factorial of a positive integer:

The factorial of n, denoted n!, is defined as the product of all integers from 1 to n inclusive.

For example, 4! = 1×2×3×4 = 24.

We define the factorial recursively like this:

- If n is 0 or 1, n! is 1.
- If n is greater than 1, n! = n × (n-1).

And here is a recursive Python function that computes the factorial, and a few examples of its use:

```python
>>> def fact(n):
    if n <= 1:
```
