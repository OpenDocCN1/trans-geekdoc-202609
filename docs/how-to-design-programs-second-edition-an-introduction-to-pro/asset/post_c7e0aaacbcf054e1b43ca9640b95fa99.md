
## Figure 5: Landing a rocket (version 2)

And here is the second one:

```
> (picture-of-rocket.v2 5555)
```

![](img/19fbe4068996ced0ce42cec7fb82a834_54_0.png)

No matter what number you give to picture-of-rocket.v2, if it is over 60, you get the same scene. In particular, when you run

```
> (animate picture-of-rocket.v2)
```

the rocket descends and sinks halfway into the ground before it stops.

Stop! What do you think we want to see?

Landing the rocket this far down is ugly. Then again, you know how to fix this aspect of the program. As you have seen, BSL knows an arithmetic of images. When place-image adds an image to a scene, it uses its center point as if it were the whole image, even though the image has a real height and a real width. As you may recall, you can measure the height of an image with the operation image-height. This function comes in handy here because you really want to fly the rocket only until its bottom touches the ground.

Putting one and one together you can now figure out that

```
(- 60 (/ (image-height 🚀) 2))
```

is the point at which you want the rocket to stop its descent. You could figure this out by playing with the program directly, or you can experiment in the interactions area with your image arithmetic.

Here is a first attempt:

```
(place-image
 50 (- 60 (image-height 🚀))
(empty-scene 100 60))
```

Now replace the third argument in the above application with

```
(- 60 (/ (image-height 🚀) 2))
```

Stop! Conduct the experiments. Which result do you like better?

When you think and experiment along these lines, you eventually get to the program in figure 6. Given some number, which represents the height of the rocket, it first tests whether the rocket's bottom is above the ground. If it is, it places the rocket into the scene as before. If it isn't, it places the rocket's image so that its bottom touches the ground.

```
(define (picture-of-rocket.v3 height)
(cond
[ (<= height (- 60 (/ (image-height 🚀) 2)))
(place-image
 50 height
(empty-scene 100 60))]
[ (> height (- 60 (/ (image-height 🚀) 2)))
(place-image
 50 (- 60 (/ (image-height 🚀) 2))
(empty-scene 100 60))])
```

Figure 6: Landing a rocket (version 3)

## One Program, Many Definitions

Now suppose your friends watch the animation but don't like the size of your canvas. They might request a version that uses 200-by-400 scenes. This simple request forces you to replace 100 with 400 in five places in the program and 60 with 200 in two other places—not to speak of the occurrences of 50, which really means “middle of the canvas.”

Stop! Before you read on, try to do just that so that you get an idea of how difficult it is to execute this request for a five-line program. As you read on, keep in mind that programs in the world consist of 50,000 or 500,000 or even 5,000,000 or more lines of program code.

In the ideal program, a small request, such as changing the sizes of the canvas, should require an equally small change. The tool to achieve this simplicity with BSL is define. In addition to defining functions, you can also introduce constant definitions, which assign some name to a constant. The general shape of a constant definition is straightforward:

```
(define Name Expression)
```

Thus, for example, if you write down

```
(define HEIGHT 60)
```

in your program, you are saying that HEIGHT always represents the number 60. The meaning of such a definition is what you expect. Whenever DrRacket encounters HEIGHT during its calculations, it uses 60 instead.

Now take a look at the code in figure 7, which implements this simple change and also names the image of the rocket. Copy the program into DrRacket; and after clicking RUN, evaluate the following interaction:

```
> (animate picture-of-rocket.v4)
```

Confirm that the program still functions as before.

```
(define (picture-of-rocket.v4 h)
  (cond
    [(<= h (- HEIGHT (/ (image-height ROCKET) 2)))
     (place-image ROCKET 50 h (empty-scene WIDTH HEIGHT))]
    [(> h (- HEIGHT (/ (image-height ROCKET) 2)))
     (place-image ROCKET 50 (- HEIGHT (/ (image-height ROCKET) 2))
                    (empty-scene WIDTH HEIGHT))])

(define WIDTH 100)
(define HEIGHT 60)
(define ROCKET 🚀)
```

## Figure 7: Landing a rocket (version 4)

The program in figure 7 consists of four definitions: one function definition and three constant definitions. The numbers 100 and 60 occur only twice—once as the value of WIDTH and once as the value of HEIGHT. You may also have noticed that it uses h instead of height for the function parameter of picture-of-rocket.v4. Strictly speaking, this change isn’t necessary because DrRacket doesn’t confuse height with HEIGHT, but we did it to avoid confusing **you**.

When DrRacket evaluates `(animate picture-of-rocket.v4)`, it replaces HEIGHT with 60, WIDTH with 100, and ROCKET with the image every time it encounters these names. To experience the joys of real programmers, change the 60 next to HEIGHT into a 400 and click RUN. You see a rocket descending and landing in a 100 by 400 scene. One small change did it all.

In modern parlance, you have just experienced your first _program refactoring_. Every time you reorganize your program to prepare yourself for likely future change requests, you refactor your program. Put it on your resume. It sounds good, and your future employer probably enjoys reading such buzzwords, even if it doesn’t make you a good programmer. What a good programmer would never live with, however, is having a program contain the same expression three times:

```
(- HEIGHT (/ (image-height ROCKET) 2))
```

Every time your friends and colleagues read this program, they need to understand what this expression computes, namely, the distance between the top of the canvas and the center point of a rocket resting on the ground. Every time DrRacket computes the value of the expressions, it has to perform three steps: (1) determine the height of the image; (2) divide it by 2; and (3) subtract the result from HEIGHT. And, every time, it comes up with the same number.

This observation calls for the introduction of one more definition:

```
(define ROCKET-CENTER-TO-TOP
 (- HEIGHT (/ (image-height ROCKET) 2)))
```

Now substitute ROCKET-CENTER-TO-TOP for the expression `(- HEIGHT (/ (image-height ROCKET) 2))` in the rest of the program. You may be wondering whether this definition should be placed above or below the definition for HEIGHT. More generally, you should be wondering whether the ordering of definitions matters. The answer is that for constant definitions, the order matters; and for function definitions, it doesn't. As soon as DrRacket encounters a constant definition, it determines the value of the expression and then associates the name with this value. For example,

```
(define HEIGHT (* 2 CENTER))
(define CENTER 100)
```

causes DrRacket to complain that “CENTER is used before its definition,” when it encounters the definition for HEIGHT. In contrast,

```
(define CENTER 100)
(define HEIGHT (* 2 CENTER))
```

works as expected. First, DrRacket associates CENTER with 100. Second, it evaluates (* 2 CENTER), which yields 200. Finally, DrRacket associates 200 with HEIGHT.

While the order of constant definitions matters, it does not matter where you place constant definitions relative to function definitions. Indeed, if your program consists of many function definitions, their order doesn’t matter either, though it is good to introduce all constant definitions first, followed by the definitions of functions in decreasing order of importance. When you start writing your own multi-definition programs, you will see why this ordering matters.

> The program also contains two line comments, introduced with semicolons (“;”). While DrRacket ignores such comments, people who read programs should not because comments are intended for human readers. It is a “back channel” of communication between the author of the program and all of its future readers to convey information about the program.

Once you eliminate all repeated expressions, you get the program in figure 8. It consists of one function definition and five constant definitions. Beyond the placement of the rocket’s center, these constant definitions also factor out the image itself as well as the creation of the empty scene.
