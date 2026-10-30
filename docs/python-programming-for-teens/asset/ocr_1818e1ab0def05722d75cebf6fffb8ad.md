```
self._fillColor = fillColor
self._fillOn = fillOn
self._isVisible = isVisible
if isVisible:            # Display the polygon if it's
    self.show()          # visible

def _draw(self):
    """Draws a regular polygon with the given turtle,
    length and number of sides."""
    interiorAngle = 360 / self._sides
    self._turtle.up()
    self._turtle.setheading(self.heading())
    self._turtle.color(self._outlineColor, self._fillColor)
    self._turtle.goto(self._xPos, self._yPos)
    self._turtle.down()
    if self.fillOn():
        self._turtle.begin_fill()
    for count in range(self._sides):
        self._turtle.forward(self._length)
        self._turtle.left(interiorAngle)
    if self.fillOn():
        self._turtle.end_fill()

def show(self):
    """Displays the polygon."""
    self._draw()
    self._isVisible = True

def hide(self):
    """Erases the polygon."""
    oldOutline = self.outlineColor()      # Save the current colors
    oldFill = self.fillColor()
    erasingColor = bgcolor()
    self._outlineColor = erasingColor     # Prepare to erase
    self._fillColor = erasingColor
    self._turtle.width(3)                 # Make sure outline goes away
    self._draw()
    self._outlineColor = oldOutline       # Restore the current colors
    self._fillColor = oldFill
    self._turtle.width(1)
    self._isVisible = False

def outlineColor(self, value = None):
    """Getter and setter for the outline color."""
    if value:
        self._outlineColor = value
```