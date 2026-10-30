The process starts in the main function, where ontimer is called with the act function and a delay of 1 millisecond and continues forever. Fortunately, before this process starts, the exitonclick function is called to let turtle graphics know to quit when the user clicks in the window.

As you can see, the pattern for running code with a timer is a bit like registering a function to handle a mouse or keyboard event. In the case of a timer, the act function is the event handler for a single timing event: the tick of the system clock after a given delay. The call of ontimer within the act function allows the process to go on indefinitely.

The next example uses this pattern to produce a more interesting animation. In this program, the turtle bounces back and forth between the edges of the window until the user clicks the mouse to exit. Here is the code:

```
```
"""
animate2.py
The turtle turns 180 degrees when it reaches the window edges.
"""
from turtle import *

def act():
    """Bounce back and forth, forever."""
    if window_height() // 2 - 20 <= abs(ycor()) or \
        window_width() // 2 - 20 <= abs(xcor()):
        left(180)
    forward(4)
    ontimer(act, 1)

def main():
    """Start the timer with the move function.
    A user click exits the program."""
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