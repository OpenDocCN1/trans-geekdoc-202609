These interactions with DrRacket don’t draw anything at all; they really just measure their width.

Two more operations matter: empty-scene and place-image. The first creates a scene, a special kind of rectangle. The second places an image into such a scene:

```
(place-image (circle 5 "solid" "green")
50 80
(empty-scene 100 100))
```

and you get this:

![](bbox=[0.142, 0.358, 0.253, 0.453])

> Not quite. The image comes without a grid. We superimpose the grid on the empty scene so that you can see where exactly the green dot is placed.

As you can see from this image, the origin (or (0,0)) is in the upper-left corner. Unlike in mathematics, the y-coordinate is measured downward, not upward. Otherwise, the image shows what you should have expected: a solid green disk at the coordinates (50,80) in a 100 by 100 empty rectangle.

Let’s summarize again. To program is to write down an arithmetic expression, but you’re no longer restricted to boring numbers. In BSL, arithmetic is the arithmetic of numbers, strings, Booleans, and even images. To compute, though, still means to determine the value of an expression—except that this value can be a string, a number, a Boolean, or an image.

And now you’re ready to write programs that make rockets fly.

# # Inputs and Output

The programs you have written so far are pretty boring. You write down an expression or several expressions; you click RUN; you see some results. If you click RUN again, you see the exact same results. As a matter of fact, you can