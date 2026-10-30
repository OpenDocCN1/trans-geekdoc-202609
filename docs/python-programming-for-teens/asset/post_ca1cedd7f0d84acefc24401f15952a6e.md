
```
>>> for row in range(3):
    for column in range(3):
        print(grid[row][column], end = " ")
        index = index + 1
    print()

0 1 2
3 4 5
6 7 8
>>>
```

In the discussion that follows, you use a list structure to hold a grid’s data.

## Defining a Class for a Tic-Tac-Toe Grid

Each square in Tic-Tac-Toe is either empty or contains a letter. When a player clicks on an empty square, that player’s letter is inserted and displayed there. Thus, a square is complex enough to warrant its own class definition. You call this new class TicTacToeSquare and define it in the module tictactoesquare.py.

When you decide to define a new class, the first question you should ask yourself is, “Can I get some data and behavior for free by subclassing an existing class?” By now, you do not want to write all your code from scratch. You have seen two examples of subclassing in this chapter already: Square is a subclass of RegularPolygon, and MenuItem is a subclass of Turtle. Because you want a Tic-Tac-Toe square to respond to mouse clicks, subclassing the Turtle class looks like a wise move.

In addition to its turtle-like attributes (shape, pen color, fill color, position, and a callback function), a Tic-Tac-Toe square contains two other data values. The first data value is a single-character string. This string will be empty when a square is created and will be either X or O after a player makes a successful move. The second data value is the integer index of the square in the grid. (Remember that you will use a list to contain the squares.) These data are initialized when you create the square.

In addition to the __init__ method, the TicTacToeSquare class includes a text method. This method is the getter and setter for the letter that appears within a grid square. The Tic-Tac-Toe game uses this method to examine the letter within a square and to place a letter in it if it’s empty.

Here is the code for the complete definition of the TicTacToeSquare class:

```python
"""
File: tictactoesquare.py
Defines the TicTacToeSquare class.
"""

from turtle import Turtle

class TicTacToeSquare(Turtle):
    """Represents a Tic-Tac-Toe square."""

    FONT = ("Arial", 12, "bold")

    def __init__(self, index, grid, length, xPos, yPos,
                outlineColor = "black", fillColor = "white", text = ""):
        """Sets the initial state of the Tic-Tac-Toe square."""
        Turtle.__init__(self, shape = "square", visible = False)
        self.speed(0)
        self.color(outlineColor, fillColor)
        self.up()
        self.goto(xPos, yPos)
        self.resizemode("user")
        self.shapesize(length / 20, length / 20)
        self._text = text
        self._index = index
        self._grid = grid
        self.onclick(lambda x, y: self._grid.makeMove(self._index))
        self.showturtle()

    def text(self, text = None):
        """Getter and setter for text."""
        if not text is None:
            self._text = text
            self.write(text, align = "center", font = TicTacToeSquare.FONT)
        return self._text
```

## Using Class Variables

There is a new type of variable in the TicTacToeSquare class that you have not seen before. The variable FONT is initialized between the class header and the first method definition. This makes it a class variable. Unlike an instance variable, which always begins with the prefix self and refers to data that belong to a single object, a class variable refers to data that the entire class of objects shares in common. Because the letters in all the grid squares
are displayed with the same font, it is not necessary to keep this font in a separate storage area belonging to each square. That’s why you put the font in a class variable, where all the squares can see it and use it. Because class variables usually behave like constants, you spell them in caps.

Note also that the text method, which uses the FONT variable to write the text to the window, must use the class name as a prefix with this variable, as in TicTacToeSquare.FONT.

## Stretching the Shape of a Turtle

You decided to subclass the Turtle class rather than the Square class for TicTacToeSquare because grid squares can get more useful behavior from turtles than from squares. However, the turtle’s “square” shape is not automatically the same size as your grid square’s shape. You don’t want the turtle to have to draw a separate square to compensate for that; the square’s shape should be exactly the turtle’s shape in the window. More importantly, when the user clicks anywhere within the space of a square, the square/turtle should detect and respond to that click.

To get the turtle’s shape to be the same size as the length of a square, you have to stretch the size of the turtle’s shape with the shapesize method. The two arguments you need in this context are the stretch width and the stretch height factors. For this application, each of these factors should be the length of the square divided by 20. Before running shapesize, you must run resizemode("user").

## Making a Move

One of the arguments to the __init__ method of TicTacToeSquare is its grid, and another is its index in that grid. The square needs this information to run the appropriate method when the user clicks in the square. The following three lines of code set up the callback function, which accomplishes this task:

```
self._index = index
self._grid = grid
self.onclick(lambda x, y: self._grid.makeMove(self._index))
```

When the user clicks in this square, the grid’s makeMove method is called with the square’s index as an argument. From there, it is the grid’s responsibility to make the move and update the window.

You can now turn your attention to the grid class.

## Defining a Class for the Grid

The grid class is named TicTacToeGrid, and it appears in the module tictactoe_grid.py. This class is responsible for creating the grid squares, laying them out in the window, and managing the game logic. Here is the code for the imports and the class header:

```python
"""
File: tictactoe_grid.py
Defines the TicTacToeGrid class.
"""

from tictactoesquare import TicTacToeSquare
from turtle import goto, tracer, up, update, write
class TicTacToeGrid(object):
    """Represents a Tic-Tac-Toe grid."""
```

Note that you import just the functions you need from the turtle module, not everything.

## Laying Out the Grid

The two main attributes of the grid are a list that contains the grid squares and a string that represents the current player’s letter. The creator of a grid can specify the size of a square, the position of the grid, the outline and fill colors of the squares, and the current player’s letter. As usual, these attributes are initialized in the __init__ method. This method also lays out the squares in the grid. Here is the code for the __init__ method:

```python
def __init__(self, length, xPos, yPos,
            outlineColor="black", fillColor="white",
            letter="X"):
    """Sets the initial state of the Tic-Tac-Toe grid."""
    self._letter = letter
    self._grid = list()
    index = 0
    y = yPos
    tracer(False)
    for row in range(3):
        x = xPos
        for column in range(3):
            square = TicTacToeSquare(index, self, length, x, y,
                                    outlineColor, fillColor)
            self._grid.append(square)
            x += length
            index += 1
        y -= length
    update()
    tracer(True)
```

Nothing is unusual here; by now, you should be familiar with the nested loop pattern used to process a grid. The index that identifies each grid square is passed along with self, the grid, to each square as it is created. That information is used in the game logic of the other methods in this class. Note that you call the tracer and update functions to speed up the display of the grid at program start-up.

## Defining Methods for the Game Logic

The other methods in the TicTacToeGrid class are concerned with the game logic. The method makeMove, which you passed to each grid square when it was created, is triggered when the user clicks in a square. This method receives the index of the target square as an argument.

The method obtains the square where the click occurred and examines the text contained there. If the text is the empty string, the grid’s current letter is put into the square and then set to the other player’s letter. The method then checks the grid to see if there is a winner and, if so, announces the outcome. Instead of writing the complex code for checking for a winner here, you pass the buck onto another method, to be defined later. (Remember: passing the buck is a programming virtue.)

Here is the code for the makeMove method:

```
def makeMove(self, index):
    """Responds to a user's click in a square."""
    square = self._grid[index]
    if square.text() == "":
        square.text(self._letter)
        if self._letter == "X":
            self._letter = "O"
        else:
            self._letter = "X"
    winner = self._hasWinner()
    if winner:
        up()
        hideturtle()
        goto(-40, 110)
        write(winner + " wins!", font = ("Arial", 24, "bold"))
```

The _hasWinner method examines the grid and, if there is a winner, returns that player’s letter; otherwise, the method returns the empty string. The method must check each row, each column, and each diagonal to see if one of them contains three Xs or three Os.
