
each other, there are no more items to examine, and the target item is not present. So, as long as

```
left <= right
```

the search must continue.

Your new version of the myIn function keeps its header and defines a recursive helper function named binaryIn. This function takes the left and right endpoints of the list as arguments. Their initial values are 0 and the length of the list minus one, respectively. Here is the complete code for the new version of myIn:

```
def myIn(targetItem, lyst):
    def binaryIn(left, right):
        if left <= right:
            midPoint = (left + right) // 2
            if lyst[midPoint] == targetItem:
                return True
            elif targetItem < lyst[midPoint]:
                return binaryIn(left, midPoint - 1)
            else:
                return binaryIn(midPoint + 1, right)
        else:
            return False
    return binaryIn(0, len(lyst) - 1)
```

Recall that the sequential search function must examine every item in the worst case, when the target item is not present. Thus, in this case, if there are 16 items, the sequential search function must make 16 recursive calls. Just how much faster is the binary search function? The binary search discards half of the remaining list items before each recursive call. So, how many recursive calls must be made before you discover that a target item is not in a list? That number is equal to the number of times that you can divide the length of the list by 2 before you reach a list segment whose length is 0. For example, for a list of length 16, the recursive calls examine list segments of lengths 8, 4, 2, 1, and 0. That’s a maximum of 5 calls, whereas the sequential search requires a maximum of 16 calls. Put mathematically, the binary search has a logarithmic running time (5 equals 1 + log₂ of 16, where the log₂ of a number is the exponent used with 2 to obtain that number). This means that the running time grows only logarithmically with the size of the list. That is, when the size of the list doubles, the amount of work that the binary search performs does not double, but increases by just 1 recursive call!

## RECURSIVE PATTERNS IN ART: ABSTRACT PAINTING

The twentieth century Dutch artist Piet Mondrian developed a style of abstract painting that exhibited simple recursive patterns. To generate such a pattern with a computer, you begin with a rectangle drawn in a random color and then repeatedly draw two unequal subdivisions with random colors. Several sample drawings are shown in Figure 7.3 (actual colors not shown).

![](img/4dc3f6307b32ff815a6d58ec1c84708c_175_0.png)

![](img/4dc3f6307b32ff815a6d58ec1c84708c_175_1.png)

![](img/4dc3f6307b32ff815a6d58ec1c84708c_175_2.png)

![](img/4dc3f6307b32ff815a6d58ec1c84708c_175_3.png)

Figure 7.3
Generating simple recursive patterns in the style of Piet Mondrian.
© 2014 Python Software Foundation.

As you can see, the program continues the process of subdivision until an “aesthetically right moment” is reached. In this version, the program divides the current rectangle into portions representing one-third and two-thirds of its area and randomly alternates these subdivisions along the horizontal and vertical axes. The user of the program specifies the
level of detail in the drawing. In Figure 7.3, you see, from left to right, a level-1 drawing, a level-3 drawing, a level-4 drawing, and a level-8 drawing.

In this section, you develop the parts of a program to create drawings like the ones in Figure 7.3. The exercises give you an opportunity to add embellishments.

## Design of the Program

Your art-drawing program appears in a single module file named `mondrian.py`. As usual, the program consists of a `main` function and several supporting functions. Because you are drawing in random colors, you can use the `randomColor` function discussed in Chapter 5. Also, because you might be drawing many rectangles, you will define a `drawRectangle` function. Finally, you will define a function to draw a complete artwork. This function's name is, appropriately, `mondrian`. Figure 7.4 shows the call diagram for the programmer-defined functions.

![](img/4dc3f6307b32ff815a6d58ec1c84708c_176_0.png)

Figure 7.4

The call diagram for the mondrian program.

As you can see, the `main` function makes a single call to the `mondrian` function. This function then makes a call to the `drawRectangle` function and calls itself (recursively) twice. You will learn in a moment how to stop these recursive calls.

## Performance Tracking

Just for fun, you can maintain some statistics on the performance of the program. These data include the number of rectangles drawn and the number of calls of the `mondrian` function. You keep these values in a dictionary named `stats`, which is set up as a module
variable. This variable is initialized near the beginning of the module, and its data are reset to 0 at the beginning of the main function. Here is the code to initialize stats:

```
# Data to track performance
stats = {"calls":0, "rectangles":0}
```

You increment the number of calls each time that mondrian is called, and you increment the number of rectangles each time that drawRectangle is called. You will use these statistics to analyze the program’s behavior shortly.

## The drawRectangle Function

Unlike the functions you developed for drawing geometric shapes in Chapter 5, the drawRectangle function expects the coordinates of two corner points—the upper-left corner and the lower-right corner—as arguments. In this case, you can draw the rectangle’s line segments by calling the goto function. Before these line segments are drawn, you must obtain a random color, set the pen to that color, pick up the pen to move a corner point, and place the pen down. The remaining steps, which draw the four line segments with goto, require you to figure out the correct coordinates for the other two corner points. Here is the code for the drawRectangle function:

```
def drawRectangle(x1, y1, x2, y2):
    """Draws a rectangle with the given corner points
    using a random color."""
    stats["rectangles"] = stats["rectangles"] + 1
    (red, green, blue) = randomColor()
    pencolor(red, green, blue)
    up()
    goto(x1, y1)
    down()
    goto(x2, y1)
    goto(x2, y2)
    goto(x1, y2)
    goto(x1, y1)
```

## The mondrian Function

The mondrian function expects the coordinates of two corner points of a rectangle and a level number as arguments. The function draws a complete artwork for that level. Now, what does that last sentence really mean?

Suppose the function receives a level of 3 on its top-level call. A level-3 drawing consists of two rectangles, each of which is a level-2 drawing. Each of these, in turn, consists of two rectangles, each of which is a level-1 drawing. A level-1 drawing is a simple rectangle containing no smaller rectangles.

The main point here is that you use the same mondrian function to create all these drawings, as long as their levels are greater than or equal to 1. Each one is drawn on either the top-level call or a recursive call of mondrian.

When does the recursion stop? When the level becomes 0. In that case, the function simply returns and does nothing. Here is a pseudocode design for this recursive process:

```
Function mondrian(x1, y1, x2, y2, level)
    If level > 0
        Call drawRectangle(x1, y1, x2, y2)
        Compute the corner points of two smaller rectangles
        Call mondrian with one set of corner points and level - 1
        Call mondrian with the other set of corner points and level - 1
```

As you can see, because the level decreases by 1 on each recursive call, it will eventually reach 0, and the recursion will stop.

The most complicated part of the mondrian function is the computation of the corner points of the two new rectangles. There are many options here. The simplest strategy would be to locate the corner points of the two rectangles given by a vertical line through the middle of the current rectangle. However, if you do this every time, you'll see a boring series of evenly spaced vertical lines in the drawing.

A better alternative is to subdivide the current rectangle either vertically or horizontally, with equal probability. In addition, you can split the current rectangle into unequal areas, perhaps using fractions of 1/3 and 2/3 of the current rectangle’s size.

The following Python code for the mondrian function uses this strategy. You will have an opportunity to refine it in the exercises.

```
def mondrian(x1, y1, x2, y2, level):
    """Draws a Mondrian-like painting at the given level."""
    stats["calls"] = stats["calls"] + 1
    if level > 0:
        drawRectangle(x1, y1, x2, y2)
        vertical = randint(1, 2)
        if vertical == 1: # Vertical split
            mondrian(x1, y1, (x2 - x1) / 3 + x1, y2,
                     level - 1)
```
