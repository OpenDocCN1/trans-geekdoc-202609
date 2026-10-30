# Exercise 2

```
```
"""
drawcircle.py
Draws a circle whose center point is the position of the first mouse click and whose circumference contains the position of the second mouse click.
"""

from turtle import *
# Used to store the position of the first mouse click.
positionHistory = []

def respondToClick(x, y):
    """Responds to consecutive mouse clicks by using their positions to draw a circle.
Arguments: the coordinates of the mouse click."""
    if len(positionHistory) == 1:
        # This is the second click, so get the center point from the history,
        # compute the radius, and draw the circle.
        (centerX, centerY) = positionHistory.pop()
        up()
        goto(centerX, centerY)
        radius = distance(x, y)
        setheading(270)
        forward(radius)
        setheading(0)
        down()
        circle(radius)
    else:
        # This is the first click, so save the position.
        positionHistory.append((x, y))

def main():
    reset()
    speed(0)
    pensize(2)
    hideturtle()
    onscreenclick(respondToClick)
    listen()
    return "Done!"

if __name__ == "__main__":
    msg = main()
    print(msg)
    mainloop()
```
```