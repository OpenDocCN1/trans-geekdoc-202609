
```
for i in range(numTurtles):
    t = Turtle(shape = "turtle")
    t.color(randomColor())
    turtles.append(t)

# Make them wander around for a fixed number of iterations
for i in range(iterations):
    for t in turtles:
        t.left((random() - .5) * 180)
        t.forward(int((random() - .5) * 100))

if __name__ == "__main__":
    main()
```

Note that the random number of degrees and the distance are generated a bit differently than they were in Chapter 3. For this new program, you use a random distance between –50 and 50. (A negative distance indicates a backward move.) You also use a random number of degrees between –90 and 90. (A negative number of degrees indicates a right turn.) To accomplish this, you use the function random.random, which returns a floating-point number from 0 through 1. The expression ((random.random() - .5) * 180) multiplies 180 by a random number between –0.5 and 0.5 to produce a random number between –90 and 90. The expression int((random.random() - .5) * 100) produces a random integer between –50 and 50.

Note also that the main function allows you to adjust the number of iterations and the number of turtles on different runs of the program.

## A New Class: RegularPolygon

Just as you can define new functions when the built-in functions won’t do, you can define new classes when the need arises. Classes can represent almost any types of objects you can think of, such as geometric shapes, houses, books, or living things. All you need to think of when you model a type of object with a class is the set of attributes it needs and the behavior it exhibits. In the next two sections, you develop two new classes: a regular polygon class and a menu item class.

You can draw regular polygons rather nicely with the function developed earlier, but you can also think of regular polygons as objects in their own right. They may have other attributes and behavior than their length and their capacity to draw themselves. A regular polygon can be filled or not, can have two colors (a fill and an outline), and can have an area and a perimeter. A regular polygon also has a position and a heading in the turtle graphics coordinate system and can be hidden or shown. Finally, a regular polygon can be translated (moved given x and y distances from its current position), scaled (have its size reduced or increased by a given factor), and rotated (turned left or right by a given angle). Although you can define functions to represent most of this behavior, it is much more convenient to bundle an object’s attributes and behavior in a class. You name this new class RegularPolygon and then begin its design.

## Design: Determine the Attributes

You begin by listing the attributes of a regular polygon and their default values (see Table 8.1). The attributes of an object are usually named with nouns (such as length) or adjectives (such as isVisible). The default values are ones these attributes have when a new polygon is created if the programmer creating it does not provide them. Typically, the programmer can override most of these defaults when a polygon is created.

Table 8.1 The Attributes of Regular Polygons

| Attribute | Default Value |
|---|---|
| turtle | A new turtle |
| length | None; the programmer must provide it |
| xPos | None; the programmer must provide it |
| yPos | None; the programmer must provide it |
| heading | None; the programmer must provide it |
| sides | 3 |
| outlineColor | "black" |
| fillColor | "black" |
| fillOn | False |
| isVisible | True |

Note that four of the attributes—the length, the coordinates of the polygon’s position, and the heading—have no defaults. This means that the programmer is required to provide her values when a new RegularPolygon object is created. Note also that the attributes include a turtle object, which is used to draw or hide the polygon in the turtle graphics window. The turtle object is created within the regular polygon object when it is created.

Before you consider the behavior of a regular polygon, you’ll see how a couple of them might be created. You create a regular polygon by using its class name to call a function. The required arguments are the attributes with no defaults listed in Table 8.1. You can also provide any or all of the other attributes as optional arguments. For clarity, you should use the keyword notation when supplying arguments in this situation. In the next session, you create a square and a hexagon with the given attributes:

```
>>> from regularpolygon import RegularPolygon
>>> square = RegularPolygon(length = 70, xPos = 0, yPos = 0,
    heading = 45, sides = 4, outlineColor = "blue")
>>> hexagon = RegularPolygon(length = 50, xPos = 80, yPos = 80, sides = 6,
    heading = 0, outlineColor = "red",
    fillOn = True)
```

Because the default value of the isVisible attribute is True, both of these polygons appear in the turtle graphics window as soon as they are created.

## Design: Determine the Behavior

The behavior of an object consists of the actions it performs when you run its methods. Taking a cue from your experience with a turtle object, two basic behaviors immediately come to mind: showing and hiding the object. Other behaviors relate directly to the polygon object’s attributes, such as examining or modifying its colors or changing its fillOn attribute. Behavior also includes what happens when you create a new object. Thus, creating a regular polygon whose isVisible attribute is True immediately draws it in the turtle graphics window. Table 8.2 lists a reasonable set of methods that capture the behavior of RegularPolygon objects.

Table 8.2 The Methods of Regular Polygons

| Method | Description |
|---|---|
| show() | Displays the polygon and sets its visibility to True. |
| hide() | Hides the polygon and sets its visibility to False. |
| fillOn(value = None) | If value (a Boolean) is provided, resets the fillOn attribute to this value. Returns its current value. |
| outlineColor(value = None) | If value (a color) is provided, resets the outlineColor attribute to this value and redraws the polygon if it’s visible. Returns its current value. |
| fillColor(value = None) | If value (a color) is provided, resets the fillColor attribute to this value and redraws the polygon if it's visible. Returns its current value. |
| isVisible() | Returns True if the polygon is shown, or False if it's hidden. |
| position() | Returns a tuple (x, y) representing the coordinates of the current position. |
| heading() | Returns the current heading in degrees. |
| translate(xDist, yDist) | Moves the polygon the given distance and redraws it if it's visible. |
| scale(factor) | Grows or shrinks the polygon by the given factor and redraws it if it's visible. |
| rotate(degrees) | Rotates the polygon by the given degrees and redraws it if it's visible. Positive degrees rotate to the left, and negative degrees rotate to the right. |

Note that the methods fillOn, outlineColor, and fillColor work in a similar manner to some of the turtle methods. That is, when you supply no argument, the method returns the value of the current setting; when you supply an argument, the method uses it to establish a new setting and redraws the polygon if it's visible.

The next session shows some of these methods in action with a hexagon. The RegularPolygon class is located in a new module named regularpolygon.

```
>>> from regularpolygon import RegularPolygon
>>> hexagon = RegularPolygon(length = 50, xPos = 80, yPos = 80, sides = 6,
    outlineColor = "red", fillOn = True)
>>> hexagon.translate(100, 0)      # Move 100 pixels to the right
>>> hexagon.scale(1.5)             # Increase the size by half
>>> hexagon.rotate(45)             # Spin 45 degrees to the left
>>> hexagon.outlineColor()
"red"
>>> hexagon.outlineColor("blue")  # Redraw outline in blue
```

When each of these methods runs, you should see a change in the turtle graphics window, according to the rules of behavior specified in Table 8.2.
