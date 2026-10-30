The functions in Table A.7 are used to show or hide the turtle.

Table A.7 Visibility

| Method | What It Does |
|---|---|
| hideturtle() | Makes the turtle invisible. |
| isvisible() | Returns True if the turtle is visible, or False otherwise. |
| showturtle() | Makes the turtle visible. |

# Event Handling

The functions in Table A.8 register functions that handle events on the turtle.

Table A.8 Functions to Register Event-Handling Functions

| Method | What It Does |
|---|---|
| onclick(fun, btn=1, add=None) | Registers fun as a function to be triggered when the mouse is clicked on the turtle's shape. fun should be a function of two arguments: the x and y coordinates of the mouse click. Optional btn values are 1 (left button) and 2 (right button). When add is True, the existing event-handling functions are not removed. |
| ondrag(fun, btn=1, add=None) | Registers fun as a function to be triggered when the mouse is dragged on the turtle's shape. fun should be a function of two arguments: the x and y coordinates of the mouse click. Optional btn values are 1 (left button) and 2 (right button). When add is True, the existing event-handling functions are not removed. |
| onrelease(fun, btn=1, add=None) | Registers fun as a function to be triggered when the mouse button is released on the turtle's shape. fun should be a function of two arguments: the x and y coordinates of the mouse click. Optional btn values are 1 (left button) and 2 (right button). When add is True, the existing event-handling functions are not removed. |