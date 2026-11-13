```
; ShotWorld -> Image
(define (to-image w)
 (cond
  [(empty? w) ...]
  [else
   (... (first w) ... (to-image (rest w)) ...)]))
```

The template for data definitions for lists is so familiar now that it doesn't need much explanation. If you have any doubts, read over the questions in figure 52 and design the template on your own.

From here it is straightforward to define the function. The key is to combine the examples with the template and to answer the questions from figure 53. Following those, you start with the base case of an empty list of shots, and, from the examples, you know that the expected answer is BACKGROUND. Next you formulate what the template expressions in the second cond compute:

+   • (first w) extracts the first coordinate from the list;

+   • (rest w) is the rest of the coordinates; and

+   • (to-image (rest w)) adds each shot on (rest w) to the background image, according to the purpose statement of to-image.

In other words, (to-image (rest w)) renders the rest of the list as an image and thus performs almost all the work. What is missing is the first shot, (first w). If you now apply the purpose statement to these two expressions, you get the desired expression for the second cond clause:

```
(place-image SHOT XSHOTS (first w)
           (to-image (rest w)))
```

The added icon is the standard image for a shot; the two coordinates are spelled out in the purpose statement; and the last argument to place-image is the image constructed from the rest of the list.

Figure 61 displays the complete function definition for to-image and indeed the rest of the program, too. The design of tock is just like the design of to-image, and you should work through it for yourself. The signature of the keyh