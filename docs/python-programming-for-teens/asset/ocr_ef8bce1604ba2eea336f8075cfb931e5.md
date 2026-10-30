When you run this program, you can grow or shrink the window’s width with your mouse, and the turtle will continue to bounce merrily on its way. Note that the distance of each move is 4, which gives the turtle a fairly quick pace but still allows its movement to appear smooth.

# ANIMATING MANY TURTLES

The design pattern just used in animating a turtle works well for the single system turtle, but if you want to animate several turtles, you have to resort to a pattern of objects and classes, as discussed in Chapter 8, “Objects and Classes.” In this section, you develop a new class, named AnimatedTurtle, that supports the animation of many turtles at once.

# What Is an Animated Turtle?

The AnimatedTurtle class is a subclass of the Turtle class. Thus, an animated turtle has all the features of a regular turtle. In addition, an animated turtle has three attributes that support its animation:

+   - **Time interval**—This is the number of milliseconds that elapse between each action performed during the animation process. The default value is 1 millisecond.
+   - **Animated**—This is a Boolean flag that determines whether to pause or continue the turtle’s animation. A value of False pauses the animation; a value of True continues it. The default value is True.
+   - **Callback**—This is a function of one argument. This function is called when the delay on the turtle’s timer expires. When called, this function is passed the turtle as its argument. The default value is a function that returns False.

To create an animated turtle, you run the AnimatedTurtle function with the optional/keyword arguments shown in Table 9.1.

Table 9.1 Optional Initial Arguments for AnimatedTurtle

| Keyword | Default Value |
|---|---|
| shape | "turtle" |
| xPos | 0 |
| yPos | 0 |

(Continued)