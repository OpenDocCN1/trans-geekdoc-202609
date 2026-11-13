# 9.5 Lists and World

With lists and self-referential data definitions in general, you can design and run many more interesting world programs than with finite data. Just imagine you can now create a version of the space invader program from chapter 6 that allows the player to fire as many shots from the tank as desired. Let’s start with a simplistic version of this problem:

> **Sample Problem** Design a world program that simulates firing shots. Every time the “player” hits the space bar, the program adds a shot to the bottom of the canvas. These shots rise vertically at the rate of one pixel per tick.

> If you haven’t designed a world program in a while, reread chapter 3.6.

Designing a world program starts with a separation of information into constants and elements of the ever-changing state of the world. For the former we introduce physical and graphical constants; for the latter we need to develop a data representation for world states. While the sample problem is relatively vague about the specifics, it clearly assumes a rectangular scenery with shots painted along a vertical line. Obviously the locations of the shots change with every clock tick, but the size of the scenery and x-coordinate of the line of shots remain the same:

```
(define HEIGHT 80) ; distances in terms of pixels
(define WIDTH 100)
(define XSHOTS (/ WIDTH 2))

; graphical constants
(define BACKGROUND (empty-scene WIDTH HEIGHT))
(define SHOT (triangle 3 "solid" "red"))
```

Nothing in the problem statement demands these particular choices, but as long as they are easy to change—meaning changing by editing a single definition— we have achieved our goal.

As for those aspects of the “world” that change, the problem statement