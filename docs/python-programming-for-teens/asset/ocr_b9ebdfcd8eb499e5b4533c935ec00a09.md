processors on your particular system. The Format menu includes some commands for formatting Python code and cleaning up indentation problems.

To save a program to a file, select the Save option from the File menu, or use the control key sequence on your particular system (Command+S on a Mac, and Ctrl+S on other systems). Python program files have a .py extension. If you don’t provide that when you save a file for the first time, Python adds it for you.

# Program Structure

As you saw in Chapter 3, some Python statements, such as loops and selection statements, have a structure. Python follows this structure to run the statements, just as you follow it to understand what they mean.

A complete Python program also has a structure—one that you employ in each program you write. Here is an example turtle graphics program that draws a pattern of hexagon shapes similar to the one you saw in Chapter 3. You can find this program in the file named samplepattern.py on the companion website (www.cengageptr.com/downloads). The next few subsections explain each part of the program’s structure.

```
```python
"""
samplepattern.py
Draws a pattern using a hexagon.
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
        for count in range(6):  # Draw each hexagon
            forward(70)
            left(60)
        left(36)                # Rotate them evenly
    end_fill()
    return "Done!"
```
```