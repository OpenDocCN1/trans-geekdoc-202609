```
(define (picture-of-rocket height)

(place-image 🚀 50 height (empty-scene 100 60))))
```

# Figure 4: Landing a rocket (version 1)

Try this out in the definitions area or the interactions area; both create the expected scenes.

In BSL, you can use all kinds of characters in names, including “-” and “.”.

The second goal requires knowledge about one additional primitive operation from the 2htdp/universe library: animate. So, click RUN and enter the following expression:

```
> (animate picture-of-rocket)
```

Stop and note that the argument expression is a function. Don’t worry for now about using functions as arguments; it works well with animate, but don’t try to define functions like animate at home just yet.

Don’t forget to add the 2htdp/universe library to your definitions area.

As soon as you hit the “return” key, DrRacket evaluates the expression; but it does not display a result, not even a prompt. It opens another window—a canvas—and starts a clock that ticks 28 times per second. Every time the clock ticks, DrRacket applies picture-of-rocket to the number of ticks passed since this function call. The results of these function calls are displayed in the canvas, and it produces the effect of an animated movie. The simulation runs until you close the window. At that point, animate returns the number of ticks that have passed.

The question is where the images on the window come from. The short explanation is that animate runs its operand on the numbers 0, 1, 2, and so on, and displays the resulting images. The long explanation is this:

+   • animate starts a clock and counts the number of ticks;