The logic of the animation is buried in the two callback functions, `rebound` and `twirl`. You saw the logic of both of these types of movement in earlier examples. You can easily change this logic to get the turtles to do other things during the animation.

The `pauseOrResume` function is triggered on a screen click. The logic in this function is similar to what you saw earlier. In this case, however, the logic is applied to a list of animated turtles.

When you run this program, you should be able to pause or resume the animation by clicking in the window. Be careful to pause before trying to resize the window.

# CREATING CUSTOM TURTLE SHAPES

There are several built-in shapes to choose from in turtle graphics, and as you learned in Chapter 2, “Getting Started with Turtle Graphics,” you can load a shape from an image file on disk. As you write more sophisticated animations, however, you’ll want to create some shapes of your own under program control. In this section, you explore how to create custom shapes in turtle graphics.

# Creating Simple Shapes

A quick way to create a simple shape is to get the system turtle to do the work for you. To do so, you use the functions `begin_poly`, `end_poly`, and `get_poly` to create a polygon. These functions are described in Table 9.3.

Table 9.3 Functions to Create a Polygon

| Method | What It Does |
|---|---|
| `begin_poly()` | Starts to record the turtle’s movements. |
| `end_poly()` | Ends the recording of the turtle’s movements. |
| `get_poly()` | Returns a tuple containing the vertices of a polygon created by the turtle’s movements. |

The first two functions operate much like the functions `begin_fill` and `end_fill` do for filling a shape. But instead of filling a shape, `begin_poly` and `end_poly` “record” the turtle’s movements in a set of vertices, which you can obtain after ending the recording. After calling `begin_poly`, you run some code that draws a polygon, with the pen up. You then