
## The while Loop

Python provides a control structure called a while loop for when you can’t predict how many times the loop will iterate. Its form is quite simple:

```
while BooleanExpression:
    Statements
```

This form looks a bit like that of the one-way if statement discussed earlier. The behavior is similar, too. The difference is that the loop repeatedly tests the Boolean expression until it becomes False. Whenever the expression returns True, the statements in the body of the loop are run; otherwise, the body of the loop is skipped, and computation continues after the loop. Thus, the statements in the one-way if statement are run once or not at all, whereas the statements in the while loop are run zero or more times. Figure 3.4 shows the flow of control in this type of loop.

![](img/4dc3f6307b32ff815a6d58ec1c84708c_97_0.png)

Figure 3.4
The flow of control in a while loop.

A while loop can be used like a for loop, to move through a sequence of values, as shown in the next shell session:

```
>>> number = 0
>>> while number < 5:
    print(number)
    number = number + 1

>>>
0
1
2
3
4
```

However, the while loop really comes into its own when the number of iterations is unpredictable. For example, consider Euclid’s method for computing the greatest common divisor of two integers. The greatest common divisor of two integers is the largest integer by which both numbers can be evenly divided (with a remainder of 0). For instance, the greatest common divisor of 120 and 32 is 8. Euclid’s method starts with the two numbers A and B and assumes A >= B and B >= 0. You repeatedly replace B with the remainder of dividing A by B and replace A with B. You stop when B equals 0; at that point, A is the answer. Here is a pseudocode design for this method:

```
While B > 0
    C = A remainder B
    A = B
    B = C
```

When A = 128 and B = 32, the loop sets A to 32 and B to 24 on the first pass. On the second pass, A becomes 24 and B becomes 8. On the third and final pass, A becomes 8 and B becomes 0. You can confirm that this is how Euclid’s method works with Python code in the following shell session:

```
>>> a = 120
>>> b = 32
>>> while b > 0:
    c = a % b
    a = b
    b = c
    print(a, b)
```

32 24
24 8
8 0
>>> a
8

As you can see, it’s impossible to anticipate the number of iterations required for any given values of A and B. Therefore, the while loop is the appropriate loop control structure to use for Euclid’s method.

## Random Walks in Turtle Graphics

In the turtle graphics examples seen thus far, your turtle has moved in quite rigid and regular ways to draw geometric shapes. But consider the movements of animals, such as

insects, in their natural environment. Their movements might be determined by the nearness of food or potential predators. Other movements might appear to be quite random; they seem to just wander around.

To simulate this type of random movement, you can make the turtle take a *random walk*. One way to do this is to move the turtle a random distance and then turn a random number of degrees to the left or right. You repeat this process a given number of times. You use Python’s function `random.randint` to obtain a random integer within a given range. The following shell session produces the random walk shown in Figure 3.5.

```
>>> from random import randint
>>> reset()
>>> for count in range(30):
    distance = randint(10, 60)
    forward(distance)
    degrees = randint(45, 135)
    if randint(1, 2) == 1:
        left(degrees)
    else:
        right(degrees)
```

![](img/4dc3f6307b32ff815a6d58ec1c84708c_99_0.png)

Figure 3.5
A random walk.
© 2014 Python Software Foundation.

Note that the turtle might walk beneath the edge of the window for a bit and then return to the visible area of the canvas.

A more interesting scenario has the turtle stopping when it encounters a piece of food or an obstacle that it can’t get around. This type of process calls for an indefinite loop that continues while such an encounter has not occurred. The next shell session directs the turtle to move around until it encounters one of the edges of its window. Figure 3.6 shows a result.

```
>>> reset()
>>> width = window_width()
>>> height = window_height()
>>> (minX, maxX) = (-(width / 2), width / 2)
>>> (minY, maxY) = (-(height / 2), height / 2)
>>> (x, y) = position()
>>> while x > minX and y > minY and x < maxX and y < maxY:
    distance = randint(10, 60)
    forward(distance)
    degrees = randint(45, 135)
    if randint(1, 2) == 1:
        left(degrees)
    else:
        right(degrees)
    (x, y) = position()
```

![](img/4dc3f6307b32ff815a6d58ec1c84708c_100_0.png)

Figure 3.6
A random walk to a boundary.
© 2014 Python Software Foundation.

Because the distances and headings are random, and the user may alter the size of the window at runtime, the number of paths that the turtle takes on any given walk is unpredictable. That's why you must use a `while` loop in this case.

## SUMMARY

- The basic control structures in programming are sequencing, selection, and iteration.
- A sequence of statements consists of one statement written after another. The computer runs them in the order in which they appear.
- A selection statement tests at least one condition. If the condition is `True`, the computer runs the sequence of statements. Otherwise, the computer skips this sequence and runs the code following it.
- A one-way `if` statement contains one test of a condition, followed by a sequence of statements. A two-way `if` statement contains one test of a condition, followed by two alternative sequences of statements. A multiway `if` statement contains two or more tests of conditions, each of which is followed by an alternative sequence of statements.
- The two Boolean values are `True` and `False`.
- A condition is a Boolean expression. A Boolean expression returns `True` or `False`.
- The comparison operators `==`, `!=`, `<`, `>`, `<=`, and `>=` can compare integers, floating-point numbers, or strings. Comparisons return `True` or `False`.
- The logical operators `and`, `or`, and `not` take Boolean expressions as operands. Logical operations return `True` or `False`.
- The rules for logical operations are described in truth tables.
- A `for` loop is used to repeat a sequence of statements a definite number of times.
- A `for` loop uses the `range` function to count through a sequence of integers.
- A `for` loop can visit the characters in a string, the items in a list or tuple, and the keys in a dictionary.
- A `while` loop is used to repeat a sequence of statements zero or more times. The loop is governed by the test of a condition, which must be `True` for the loop to continue running the sequence of statements.

## EXERCISES

Launch the IDLE shell and complete the following exercises. You should write your code interactively in the IDLE shell.

+   1. You have drawn various geometric shapes by moving the turtle forward and then turning left. Write a code fragment that draws a circle in a similar manner. Hint: the turtle turns 1 degree to the left. How do you increase or decrease the size of your circles?
+   
+   2. You can modify your code from Exercise 1 to draw a spiral. Start by calling `left` with a larger number of degrees, say, 4, and observe what happens. Then clear the drawing and set a new variable named `distance` to 1. Use this variable as the argument to move forward within the loop, and increment the variable by a small amount, say, .05, on each pass through the loop. How do you increase or decrease the number of rotations and the distance between them?

## CHAPTER 4

## COMPOSING, SAVING, AND RUNNING PROGRAMS

![](img/4dc3f6307b32ff815a6d58ec1c84708c_103_0.png)

Thus far in this book, you have been entering short Python code fragments into the IDLE shell and viewing the results. This method works well for experimenting with the basic elements of Python, including the turtle graphics operations. However, as the things you want to do with your code get more complicated, so does your code. At that point, entering lots of small pieces of code into the shell becomes unwieldy and inconvenient. When you put related code fragments together, you really have what counts as a *computer program*. What you need now is an editor for composing programs, a means of saving them to files for later use, and a means of running them. The programming process and its supporting tools are the topics of this chapter.

## EXPLORING THE PROGRAM DEVELOPMENT PROCESS

A *program* is a sequence of statements or instructions that solves a problem. Programs can be as short as a single line of code or can consist of millions of lines of code. Software companies may employ many teams of programmers to work on a single large program. Each team is responsible for working on a solution to a piece of the overall problem (for example, the spell checker, file manager, and editor in a word processing program). Each team in turn may be composed of smaller teams who work on different stages of the programming process. These stages include the following, which are also shown in the flow diagram of Figure 4.1:

+   1. **Analysis**—In this stage, you determine exactly what counts as a solution to a problem. For example, a spell checker should check the spelling of words in a text file
