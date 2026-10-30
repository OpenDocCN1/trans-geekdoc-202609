
```
def callback(self, fun=None):
    """Getter and setter for the callback function. If flag is True,
    also starts or resumes the animation."""
    if not fun is None:
        self.__callback = fun
    return self.__callback

def act(self):
    """Performs the next callback action if the turtle is animated."""
    if not self.animated():
        return
    self.__callback(self)
    ontimer(lambda: self.act(), self._timeInterval)
```

There are two things to note about this code:

The __init__ method calls the act method in its last step because the default state of this type of turtle is to be animated. Thus, by default, the animation begins as soon as the turtle is created.

If the animated state is False, the act method simply returns. This logic allows you to pause or resume the animation by calling the animated method with an argument of False or True, respectively. You can also create a turtle whose animation is initially off by overriding the default value of the animated attribute.

The act method implements the logic of the timer that you saw in earlier examples. In this logic, an action is performed, and then ontimer waits for a given time interval before performing that action again. In AnimatedTurtle.act, the callback function is called with self (the turtle) as an argument. This function can perform whatever actions you want. A call of the act method is then bundled in a function that is passed to ontimer for the next cycle of the animation.

## Sleepy and Speedy as Animated Turtles

Your last experiment recasts sleepy and speedy as animated turtles. In this short program, sleepy bounces back and forth in the window, while speedy revolves in a circular pattern. Here is the code for the program:

```
"""
File: animate3.py
Creates two animated turtles. One bounces back and forth, while
the other revolves in a circular pattern.
"""
```

```
from animatedturtle import AnimatedTurtle
from turtle import hideturtle, listen, mainloop, onscreenclick
from turtle import window_height, window_width
from random import randint

def pauseOrResume(turtles):
    """Pauses or resumes the animation."""
    for t in turtles:
        t.animated(not t.animated())

def rebound(aTurtle):
    """Callback function that fires on each timer event.
    Moves forward until an edge is encountered, then turns
    about face."""
    if window_height() // 2 - 20 <= abs(aTurtle.ycor()) or \
        window_width() // 2 - 20 <= abs(aTurtle.xcor()):
        aTurtle.left(180)
    aTurtle.forward(4)

def twirl(aTurtle):
    """Callback function that fires on each timer event.
    Turns and moves forward, as in a circle."""
    aTurtle.left(8)
    aTurtle.forward(8)

def randomColor():
    """Returns a random RGB value."""
    return (randint(0, 255), randint(0, 255), randint(0, 255))

def main():
    hideturtle()
    sleepy = AnimatedTurtle(heading = 0, fillColor = randomColor(),
                            callback = rebound)
    speedy = AnimatedTurtle(heading = 90, fillColor = randomColor(),
                            callback = twirl)
    turtles = (sleepy, speedy)
    onscreenclick(lambda x, y: pauseOrResume(turtles))
    listen()
    return "Done!"

if __name__ == '__main__':
    msg = main()
    print(msg)
    mainloop()
```

The logic of the animation is buried in the two callback functions, `rebound` and `twirl`. You saw the logic of both of these types of movement in earlier examples. You can easily change this logic to get the turtles to do other things during the animation.

The `pauseOrResume` function is triggered on a screen click. The logic in this function is similar to what you saw earlier. In this case, however, the logic is applied to a list of animated turtles.

When you run this program, you should be able to pause or resume the animation by clicking in the window. Be careful to pause before trying to resize the window.

## CREATING CUSTOM TURTLE SHAPES

There are several built-in shapes to choose from in turtle graphics, and as you learned in Chapter 2, “Getting Started with Turtle Graphics,” you can load a shape from an image file on disk. As you write more sophisticated animations, however, you’ll want to create some shapes of your own under program control. In this section, you explore how to create custom shapes in turtle graphics.

### Creating Simple Shapes

A quick way to create a simple shape is to get the system turtle to do the work for you. To do so, you use the functions `begin_poly`, `end_poly`, and `get_poly` to create a polygon. These functions are described in Table 9.3.

Table 9.3 Functions to Create a Polygon

| Method | What It Does |
|---|---|
| `begin_poly()` | Starts to record the turtle’s movements. |
| `end_poly()` | Ends the recording of the turtle’s movements. |
| `get_poly()` | Returns a tuple containing the vertices of a polygon created by the turtle’s movements. |

The first two functions operate much like the functions `begin_fill` and `end_fill` do for filling a shape. But instead of filling a shape, `begin_poly` and `end_poly` “record” the turtle’s movements in a set of vertices, which you can obtain after ending the recording. After calling `begin_poly`, you run some code that draws a polygon, with the pen up. You then call end_poly to finish the recording. At that point, you can call get_poly to retrieve the set of the vertices. The next session shows these functions in action:

```
>>> from turtle import *
>>> hideturtle()
>>> up()
>>> begin_poly()
>>> for count in range(5):    # Record the vertices of a pentagon
    forward(20)
    left(360 / 5)

>>> end_poly()
>>> get_poly()
((0.00,0.00), (20.00,0.00), (26.18,19.02), (10.00,30.78), (-6.18,19.02), (0.00,0.00))
```

At this point, you can use the set of vertices to register a new shape and then create a turtle with it, as follows:

```
>>> addshape("pentagon", get_poly())
>>> sleepy = Turtle(shape = "pentagon")
```

The result is shown in Figure 9.1.

![](img/4dc3f6307b32ff815a6d58ec1c84708c_228_0.png)

Figure 9.1
Creating a new turtle shape with a polygon.
© 2014 Python Software Foundation.

Note that the pentagon seems a bit off-kilter from the pentagons you drew in Chapters 3 through 5 (the bottom side should be parallel to the x-axis). To correct this problem, you can rotate the turtle’s shape without altering its heading by calling the tilt method, as follows:

```
>>> sleepy.tilt(90)
```

The next example is a short tester program that defines a function to create shapes that are regular polygons. This function, named makeShape, expects the length, number of sides, and shape name as arguments. It calls the regularPolygon function to draw the shape while recording it, and then it registers the new shape under its name. The main function creates two turtles with different shapes and allows the user to drag them around with the mouse. Here is the code (in the file testpoly.py):

```python
"""
testpoly.py
Illustrates the use of begin_poly, end_poly, and get_poly to
create custom turtle shapes.
"""

from turtle import *

def regularPolygon(length, numSides):
    """Draws a regular polygon.
    Arguments: the length and number of sides."""
    interiorAngle = 360 / numSides
    for count in range(numSides):
        forward(length)
        left(interiorAngle)

def makeShape(length, numSides, shapeName):
    """Creates and registers a new turtle shape with the given name.
    The shape is a regular polygon with the given length and number
    of sides.
    Arguments: the length, number of sides, and shape name."""
    up()
    goto(0, 0)
    setheading(0)
    begin_poly()
    regularPolygon(length, numSides)
    end_poly()
    shape = get_poly()
    addshape(shapeName, shape)

def main():
    """Creates two turtles with custom shapes and allows you
    to drag them around the window."""
    hideturtle()
    speed(0)
    makeShape(40, 5, "pentagon")
    makeShape(20, 8, "octagon")
    sleepy = Turtle(shape = "pentagon")
    sleepy.color("brown", "green")
    sleepy.up()
    sleepy.goto(100, 50)
    sleepy.tilt(90)
    happy = Turtle(shape = "octagon")
    happy.color("blue", "pink")
    happy.up()
    sleepy.ondrag(lambda x, y: sleepy.goto(x, y))
    happy.ondrag(lambda x, y: happy.goto(x, y))
    listen()
    return "Done!"

if __name__ == '__main__':
    msg = main()
    print(msg)
    mainloop()
```

### Creating Compound Shapes

Sometimes a simple polygon won’t do for a turtle’s shape. Consider the shape of even just a simple rocket. It has a rectangular fuselage in the middle, a triangular nose cone at one end, and two tail fins at the other end, as shown in Figure 9.2.

![](img/4dc3f6307b32ff815a6d58ec1c84708c_230_0.png)

Figure 9.2
A simple rocket shape.
© 2014 Python Software Foundation.
