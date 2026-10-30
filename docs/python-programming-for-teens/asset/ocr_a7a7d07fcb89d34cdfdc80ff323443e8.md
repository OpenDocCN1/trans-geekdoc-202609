```
up()
goto(x1, y1)
down()
goto(x2, y1)
goto(x2, y2)
goto(x1, y2)
goto(x1, y1)
end_fill()

def mondrian(x1, y1, x2, y2, level):
    """Draws a Mondrian-like painting at the given level."""
    if level > 0:
        drawRectangle(x1, y1, x2, y2)
        vertical = randint(1, 2)
        splitFactor = randint(1, 2)
        if vertical == 1:          # Vertical split
            if splitFactor == 1:   # Do 1/3 and 2/3
                mondrian(x1, y1, (x2 - x1) / 3 + x1, y2,
                         level - 1)
                mondrian((x2 - x1) / 3 + x1, y1, x2, y2,
                         level - 1)
            else:                  # Do 2/3 and 1/3
                mondrian(x1, y1, 2 * (x2 - x1) / 3 + x1, y2,
                         level - 1)
                mondrian(2 * (x2 - x1) / 3 + x1, y1, x2, y2,
                         level - 1)
        elif splitFactor == 1:  # Horizontal split with 1/3 and 2/3
            mondrian(x1, y1, x2, y1 - (y1 - y2) / 3,
                     level - 1)
            mondrian(x1, y1 - (y1 - y2) / 3, x2, y2,
                     level - 1)
        else:                   # Do 2/3 and 1/3
            mondrian(x1, y1, x2, y1 - 2 * (y1 - y2) / 3,
                     level - 1)
            mondrian(x1, y1 - 2 * (y1 - y2) / 3, x2, y2,
                     level - 1)

def main():
    # Obtain the level from the user.
    level = numinput("Input Dialog", "Enter the level",
                     default = 1, minval = 1)
    if not level:
        level = 1
```