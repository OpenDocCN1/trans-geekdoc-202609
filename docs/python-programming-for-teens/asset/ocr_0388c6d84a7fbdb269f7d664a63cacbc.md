turns left and moves forward by small increments until it completes a circuit. Now you can schedule these actions with a timer.

In the first experiment, you instruct the turtle to turn left and move forward, after a delay of a given number of milliseconds. You then repeat this process, forever. The turtle appears to rotate in a circular pattern (without drawing the circle). To quit the program, you click the mouse in the turtle graphics window.

Here is the code for this program, in the file animate1.py.

```
```python
"""
animate1.py
Animates the turtle using the ontimer function.
"""

from turtle import *

def act():
    """Move forward and turn a bit, forever."""
    left(2)
    forward(2)
    ontimer(act, 1)

def main():
    """Start the timer with the move function.
    The user's click exits the program."""
    reset()
    shape("turtle")
    speed(0)
    up()
    exitonclick()      # Quit the program when the user clicks the mouse
    listen()
    ontimer(act, 1)
    return "Done!"

if __name__ == '__main__':
    msg = main()
    print(msg)
    mainloop()
```
```

The act function turns the turtle left, moves it forward, and calls ontimer with the act function and a delay of 1 millisecond as arguments. This looks a bit like a recursive function, but it's indirect—ontimer calls act, which calls ontimer again. This recursion is also infinite, because there is no check for a base case condition and no return.