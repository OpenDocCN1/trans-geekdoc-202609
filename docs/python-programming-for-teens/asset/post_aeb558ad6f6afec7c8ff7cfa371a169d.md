
```
# Determine whether to make a turn first.
if probability < .01:    # Probability too small to take the turn
    return
if probability < 1:    # Maybe not take the turn
    if not choice(range(100)) in range(0, int(probability * 100)):
        return

# A turn will be made, so the # of degrees is either random or given
if not upper:    # Upper absent, so use lower
    degrees = lower
else:    # Choose a random amount of degrees
    degrees = randint(lower, upper)

if randint(1, 2) == 1:    # Turn left or right with equal prob.
    left(degrees)
else:
    right(degrees)
```

Whew! There is a saying that nothing good comes cheaply, and this function is a case in point. Whenever there is complex logic, you try to handle the easiest cases first. So, here are the cases in this function:

- 1. The probability is less than .01, so you just quit the function.
- 2. The probability is less than 1, so you use it to determine whether to continue. You pick a random number from 0 through 99 and then see if that number is in the range of numbers from 0 through 100 times the probability. If it’s not in that range, you quit the function.
- 3. If you get this far, you’ll be turning the turtle. If the value of upper is not present, the number of degrees will be the value of lower. Otherwise, the number of degrees is a random number from lower through upper.
- 4. Finally, you choose whether to turn left or right, with equal probability.

Note that the function also imports the random function choice for later use in its code.

Even though you have expended a lot of effort on several new function definitions, this effort will be well rewarded. Your top-level code will be simpler and easier to read and manage. Moreover, other programmers will find your code useful, should you decide to share it with them.

## Another Version of the Random Walk

The random walk program halts when the turtle crosses an edge of the window. But animals don’t typically stop when they encounter obstacles; they either climb over them or turn to try another route.

Another version of a random walk allows the turtle to turn back into the enclosed area of the window when it encounters an edge. In this version, the main loop runs a definite number of times—perhaps long enough to allow the turtle several “rebounds” off the edges of its window. When the turtle crosses an edge, it turns its back to that edge and proceeds from there. Otherwise, it takes a random turn, as before. The program also allows the user to specify the number of iterations via a command-line argument. This value is 1000 by default.

Here is the code for the new version of the program:

```
from turtle import *
from random import randint
import sys

# New function definitions will go here

def main():
    if len(sys.argv) > 1:
        iterations = int(sys.argv[1])
    else:
        iterations = 1000
    reset()
    for count in range(iterations):
        randomForward(1, 3)      # Move 1, 2, or 3 units
        if atTopEdge():
            setheading(270)      # Go south
        elif atBottomEdge():
            setheading(90)       # Go north
        elif atLeftEdge():
            setheading(0)        # Go east
        elif atRightEdge():
            setheading(180)      # Go west
        else:
            randomTurn(45, 135, .05) # Turn 1/20 of the time by default
```

As you can see, the functions you developed in this section have come in quite handy. You will have many more occasions to structure your code with functions in the rest of this book.

## SUMMARY

- A function definition consists of a heading and a set of statements.
- A function heading contains the function’s name and a parenthesized list of argument names.
- A function’s docstring is located between the function’s heading and its statements.
- A default argument appears as an assignment of a default value to the argument’s name in a function heading.
- If an argument has a default value, you can omit that argument when the function is called.
- Arguments can be passed with keywords when a function is called. The keyword is the argument’s name, which is followed by the assignment operator and its value. A keyword argument may appear in a different position than its position in the function definition’s heading.
- An argument without a keyword must appear in the same position in both the call and the definition of the function.
- An argument without a default value must appear before any of the arguments with defaults in the function definition’s heading.
- An argument without a default value is required; you cannot omit it when the function is called.
- The `return` statement returns the value of an expression to the function’s caller. When the expression is omitted or the function has no `return` statement, that function returns the value `None`.
- A function may be passed as an argument to another function.
- The `lambda` expression creates an anonymous function.

## EXERCISES

Launch the IDLE shell, open a file window, and complete the following exercises. You should run each program within IDLE and, when it is completed, in the terminal window.

- 1. The Pythagorean Theorem defines the relationship between the hypotenuse of a right triangle and its other two sides. It states that the square of the hypotenuse is equal to the sum of the squares of the other two sides. Define a function named `hypo`

that expects the lengths of other two sides of a right triangle as arguments. This function returns the triangle’s hypotenuse. Include this function in a tester program that exercises its capabilities.

- 2. Try to use the `regularPolygon` function to draw circles. Note what happens when you vary the length. Then define a new function named `myCircle`, which expects the radius of the circle as an argument. This function should call `regularPolygon` with the appropriate arguments to draw a circle with the given radius. Include this function in a tester program that exercises its capabilities. Hint: determine the radius of a circle that is a regular polygon with a length of 1 and 360 sides. Then use that information to determine the length to be used for any given radius.

This page intentionally left blank

## CHAPTER 6

### User Interaction with the Mouse and the Keyboard

![](img/4dc3f6307b32ff815a6d58ec1c84708c_143_0.png)

In the previous two chapters, you wrote programs that drew shapes in a turtle graphics window. However, many other programs take information as input from people. This information might be text (like a username and password) or numbers (like your age or income tax paid). Text and numbers are entered from the keyboard. People might also interact with a program by moving a mouse, clicking it, or dragging it. Many programs, especially computer games, would be unthinkable without such input capabilities. In this chapter, you explore various ways of allowing users to interact with your turtle graphics programs.

### Using Dialog-Based Input

In Chapter 4, “Composing, Saving, and Running Programs,” you learned how some programs obtain input via command-line arguments. For example, when you run the command

```
examplepattern.py 6 blue pink
```

the program draws a radial pattern of hexagons with a blue pen color and a pink fill color. This way of taking input into a program is fine for some applications, but it has two shortcomings:

- Most people don’t run programs from a terminal window.
- When they do, it may not be clear to them what role the input plays in the program. In this program, which color is the pen color, and which color is the fill color? And what does the 6 mean?

Most people are used to receiving an informative prompt for a computer input; such a prompt describes the type of value that’s requested. In terminal-based Python programs, Python’s input function serves this purpose, but again, most people don’t run programs from a terminal window. Moreover, even when you do run a turtle graphics program from a terminal, your program code can no longer access the terminal window for input values.

The primary way in which window-based applications receive input is via labeled entry fields within a window. As you know from filling in forms on the web, you place the mouse cursor in a box and type in the number or text requested. The request or prompt is a label that appears next to the field. You then click a Submit or OK button to inform the program that the input is ready, or you click a Cancel button to back out of the input operation altogether. Turtle graphics supports this strategy for input with input dialogs, which form the subject of this section.

### Input Dialogs in Turtle Graphics

An input dialog is a small window that pops up for input. The window contains a message about the kind of data requested and a field for the user to enter this information via the keyboard. Command buttons are available to submit or cancel the input.

Assume that the pattern drawing program of the previous two chapters takes three inputs from input dialogs. At program start-up, the user is presented with a sequence of three dialogs, shown in Figure 6.1.

![](img/4dc3f6307b32ff815a6d58ec1c84708c_144_0.png)

Figure 6.1
Three input dialogs.
© 2014 Python Software Foundation.

When the user closes each dialog, the next one pops up, until all the input has been submitted or canceled. If input is canceled, the program uses a default value, as before.

Turtle graphics dialogs come in two flavors: one for accepting numbers, and the other for accepting strings. The two functions for input dialogs are named textinput and numinput. Now you’ll examine these functions more closely.
