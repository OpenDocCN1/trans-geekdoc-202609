```
rightX = 60
up()
goto(leftX, y)
down()
goto(leftX - offset, y + offset)
up()
goto(leftX - offset, y - offset)
down()
goto(leftX, y)
goto(rightX, y)
goto(rightX + offset, y + offset)
goto(rightX, y)
goto(rightX + offset, y - offset)

y = -40
up()
goto(leftX, y)
down()
goto(leftX + offset, y + offset)
up()
goto(leftX + offset, y - offset)
down()
goto(leftX, y)
goto(rightX, y)
goto(rightX - offset, y + offset)
goto(rightX, y)
goto(rightX - offset, y - offset)
hideturtle()
```

# Exercise 2

```
from turtle import *
speed(0)
hideturtle()
length = 40
angle = 90
forward(length)
left(angle)
forward(length)
left(angle)
forward(length)
left(angle)
forward(length)
left(angle)
```