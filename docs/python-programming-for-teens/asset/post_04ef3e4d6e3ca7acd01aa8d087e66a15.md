
If __name__ is set to the value "__main__". So you can see that the logic of the one-way if statement makes the right thing happen, no matter what. If __name__ is "__main__", the program calls the main function to run the program. Otherwise, the program does nothing further but has already loaded the other pieces of code that belong to this module.

### The mainloop Function

Now it’s time to look more closely at the last three lines of code in the example program. The first line calls the main function, which pops up the turtle graphics window and draws the pattern. At that point, main returns the string "Done!" The program then outputs this string either to the IDLE shell or to the terminal window, depending on the launch method. The last line of code calls the mainloop() function. This function causes the turtle graphics window to stay open when the program is run from a terminal window. If you are running the program from an IDLE file window, you cannot return to the shell until you close the turtle graphics window.

## RUNNING A PROGRAM

By now you will be eager to run the example program. This section explores a couple of ways to do this. But first you need a quick reminder about using a turtle graphics configuration file.

### Using a Turtle Graphics Configuration File

As mentioned in Chapter 2, “Getting Started with Turtle Graphics,” a turtle graphics configuration file can provide the same initial settings for several programs. For example, you might want a smaller initial turtle graphics window and the full RGB color mode. Many of the example programs in the rest of this book use a configuration file with the following settings:

```
width = 400
height = 300
canvwidth = 1200
canvheight = 900
using_IDLE = True
colormode = 255
title = Python Turtle Graphics
```

This file is named turtle.cfg and should sit in the same directory as your Python program file. Of course, you are free to modify any of these settings from within your program after it launches.

### Running a Program from an IDLE Window

Now, at long last, you are ready to run a Python program. The easiest way to do so in IDLE is to place your mouse cursor in the program file window and press the Fn + F5 or F5 key. If the program has not yet been saved, Python stops you with a request to do that. Then, if the program has not yet been compiled, Python does that. If there are no syntax errors, Python loads the resulting code into its runtime system and runs the program. In the case of the example program, you should now see three windows: the shell window, the file window, and the turtle graphics window, as shown in Figure 4.2.

![](img/4dc3f6307b32ff815a6d58ec1c84708c_110_0.png)

![](img/4dc3f6307b32ff815a6d58ec1c84708c_110_1.png)

```python
"""
samplepattern.py
Draw a pattern using a hexagon.
"""

from turtle import *

def main():
    reset()
    speed(0)
    pensize(2)
    hideturtle()
    color("blue", "yellow")    # Blue outline, yellow fill
    begin_fill()
    for count in range(10):    # Draw 10 hexagons
        for count in range(6): # Draw each hexagon
            forward(70)
            left(60)
        left(36)               # Rotate them evenly
    end_fill()
    return "Done!"

if __name__ == "__main__":
    msg = main()
    print(msg)
    mainloop()
```

![](img/4dc3f6307b32ff815a6d58ec1c84708c_110_2.png)

Figure 4.2
Running a program in IDLE.
© 2014 Python Software Foundation.

Note that if there are any runtime errors in the program (but there should be none in this example), the error messages appear in red, as always, in the shell window.

To quit your running program, close the turtle graphics window. At that point, control returns to the shell, and you can make any desired changes to the program in the file window.

When you develop programs in the rest of this book, you’ll be working with windows of this sort in IDLE. Learn where the F5 key is!

### Running a Program from a Terminal Window

If you want to give a finished Python program to others, note that they will likely run it from a terminal window. To try this yourself, open a terminal window and navigate to the directory that contains the file samplepattern.py. Then enter the command

```
python3 samplepattern.py
```

in the terminal window. The turtle graphics window should pop up and display the pattern. When you close this window, the program quits and returns control to the terminal window. Note that the message "Done!" should be displayed in that window. If you don’t want extra output like this from your program, you can delete the output statement in the penultimate line of code.

Most computer systems provide a way to set the action that is triggered when you launch a file by double-clicking on its icon. In Windows systems, this action runs the Python program. In Mac OS, this action opens an IDLE file window. Also, in either system, you must make sure that Python 3.0 or higher is installed.

### Using the sys Module and Command-Line Arguments

When you run a program from a terminal window, you can usually provide optional command-line arguments. For example, the idle3 command pops up a shell window, but you can instead run idle3 filename to open a file window. Likewise, when you run python3 filename, you are launching a Python program, but when you run just python3, a shell opens (in the terminal window itself, not in an IDLE window).

Python lets you distribute programs that you can run with additional command-line arguments. For example, suppose you want the example program that draws a pattern with hexagons to use pentagons or octagons instead. Your program could accept an additional command-line argument that represents the number of sides in the figure. The default
number would still be 6 if the user does not supply the extra argument. Here are three examples of how to use this feature in the terminal window:

```
Madison:~ ken$ python3 samplepattern.py
Done!
Madison:~ ken$ python3 samplepattern.py 5
Done!
Madison:~ ken$ python3 samplepattern.py 8
Done!
```

When a Python program is run in the terminal window, the system places each optional argument in a list of strings. The first string in this list is the program’s filename. To access this list in your Python program, you import the sys module. The variable sys.argv is the name of the list.

To experiment with command-line arguments before you actually use them, try printing them at the beginning of the main function. Here are the changes to the example program to accomplish this, followed by the terminal outputs:

```
"""
samplepattern.py
Draws a pattern using a hexagon.
"""

from turtle import *
import sys

def main():
    print(sys.argv)
# The rest of the program would go here
```

Program output from two runs:

```
Madison:~ ken$ python3 samplepattern.py
['samplepattern']
Done!
Madison:~ ken$ python3 samplepattern.py 5
['samplepattern', '5']
Done!
```

Now you’ll modify the program so that it handles the extra command-line argument, if there is one. Here is the relevant code, followed by an explanation.

```python
from turtle import *
import sys

def main():
    if len(sys.argv) == 2:
        numSides = int(sys.argv[1])
        if numSides < 3:
            return "Error: number of sides must be > 2"
    else:
        numSides = 6
    angle = 360 / numSides        # Compute interior angle for polygon
    reset()
    speed(0)
    width(2)
    hideturtle()
    color("blue", "yellow")       # Blue outline, yellow fill
    begin_fill()
    for count in range(10):       # Draw 10 polygons
        for count in range(numSides):  # Draw each polygon
            forward(70)
            left(angle)
        left(36)                  # Rotate them evenly
    end_fill()
    return "Done!"
```

The main function now uses the variable numSides to refer to the number of sides in the shape, and it uses the variable angle to refer to the interior angle between sides in the shape. Note how these variables are initialized and then used in the loop.

The rest of the new code at the beginning of main deals with the possibility of the extra command-line argument. If the extra command-line argument is not present, the number of sides in the figure is 6, as before. Otherwise, this argument is converted to an int and checked for an error before being used to establish the number of sides and the angle.

Note the use of the nested if and return statements to handle the error.

## LOOKING BEHIND THE SCENES: How Python Runs Programs

Whether you are running Python code as a program or interactively in a shell, Python does a great deal of work to carry out the instructions in your program. Think for a moment about bridging the huge gap between the instructions that you write in Python
