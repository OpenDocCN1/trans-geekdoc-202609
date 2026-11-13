
```
> (circle 10 "solid" "green")

> (rectangle 10 20 "solid" "blue")

> (star 12 "solid" "gray")
```

Stop! The above uses a previously unmentioned operation. Look up its documentation and find out how many more such operations the 2htdp/image library comes with. Experiment with the operations you find.

The second kind of functions on images concern image properties:

- image-width determines the width of an image in terms of pixels;
- image-height determines the height of an image;

They extract the kind of values from images that you expect:

```
> (image-width (circle 10 "solid" "red"))
20
> (image-height (rectangle 10 20 "solid" "blue"))
20
```

Stop! Explain how DrRacket determines the value of this expression:

```
(+ (image-width (circle 10 "solid" "red"))
(image-height (rectangle 10 20 "solid" "blue")))
```

A proper understanding of the third kind of image-composing primitives requires the introduction of one new idea: the *anchor point*. An image isn’t just a single pixel, it consists of many pixels. Specifically, each image is like a photograph, that is, a rectangle of pixels. One of these pixels is an implicit anchor point. When you use an image primitive to compose two images, the composition happens with respect to the anchor points, unless you specify some other point explicitly:

- overlay places all the images to which it is applied on top of each other, using the center as anchor point;
- overlay/xy is like overlay but accepts two numbers—x and y—between two image arguments. It shifts the second image by x pixels to the right and y pixels down—all with respect to the first image's top-left corner; unsurprisingly, a negative x shifts the image to the left and a negative y up; and
- overlay/align is like overlay but accepts two strings that shift the anchor point(s) to other parts of the rectangles. There are nine different positions overall; experiment with all possibilities!

The 2htdp/image library comes with many other primitive functions for combining images. As you get familiar with image processing, you will want to read up on those. For now, we introduce three more because they are important for creating animated scenes and images for games:

- empty-scene creates a rectangle of some given width and height;
- place-image places an image into a scene at a specified position. If the image doesn't fit into the given scene, it is appropriately cropped;
- scene+line consumes a scene, four numbers, and a color to draw a line into the given image. Experiment with it to see how it works.

The laws of arithmetic for images are analogous to those for numbers; see figure 10 for some examples and a comparison with numeric arithmetic. Again, no image gets destroyed or changed. Like +, these primitives just make up new images that combine the given ones in some manner.

## Figure 10: Laws of image creation

| arithmetic of numbers | arithmetic of images |
| :--- | :--- |
| `(+ 1 1) == 2` | `(overlay (square 4 "solid" "orange") (circle 6 "solid" "yellow"))` |
| `(+ 1 2) == 3` | `(underlay (circle 6 "solid" "yellow") (square 4 "solid" "orange"))` |
| `(+ 2 2) == 4` | `(place-image (circle 6 "solid" "yellow") 10 10 (empty-scene 20 20))` |

### Exercise 5. Use the 2htdp/image library to create the image of a simple boat or tree. Make sure you can easily change the scale of the entire image.

*Copy and paste the image into your DrRacket.*

### Exercise 6. Add the following line to the definitions area:

![](img/19fbe4068996ced0ce42cec7fb82a834_81_0.png)

```
(define cat )
```

Create an expression that counts the number of pixels in the image.

## 1.5 The Arithmetic of Booleans

We need one last kind of primitive data before we can design programs: Boolean values. There are only two kinds of Boolean values: #true and #false. Programs use Boolean values for representing decisions or the status of switches.

Computing with Boolean values is simple, too. In particular, BSL programs get away with three operations: or, and, and not. These operations are kind of like addition, multiplication, and negation for numbers. Of course, because there are only two Boolean values, it is actually possible to demonstrate how these functions work in all possible situations:

- or checks whether any of the given Boolean values is #true:

```
> (or #true #true)
#true
> (or #true #false)
#true
> (or #false #true)
#true
> (or #false #false)
#false
```

- and checks whether all of the given Boolean values are #true:

```
> (and #true #true)
#true
> (and #true #false)
#false
> (and #false #true)
#false
> (and #false #false)
#false
```

- not always picks the Boolean that isn't given:

```
> (not #true)
#false
```

Unsurprisingly, or and and may be used with more than two expressions. Finally, there is more to or and and than these explanations suggest, but to explain the extra bit requires a second look at nested expressions.

### Exercise 7. Boolean expressions can express some everyday problems.

Suppose you want to decide whether today is an appropriate day to go to the mall. You go to the mall either if it is not sunny or if today is Friday (because that is when stores post new sales items).

*Nadeem Hamid suggested this formulation of the exercise.*

Here is how you could go about it using your new knowledge about Booleans. First add these two lines to the definitions area of DrRacket:

```
(define sunny #true)
(define friday #false)
```

Now create an expression that computes whether sunny is false or friday is true. So in this particular case, the answer is #false. (Why?)
See exercise 1 for how to create expressions in DrRacket. How many combinations of Booleans can you associate with sunny and friday?

## 1.6 Mixing It Up with Booleans

One important use of Boolean values concerns calculations with different kinds of data. We know from the Prologue that BSL programs may name values via definitions. For example, we could start a program with

```
(define x 2)
```

and then compute its inverse:

```
(define inverse-of-x (/ 1 x))
```

This works fine, as long as we don't edit the program and change x to 0.

This is where Boolean values come in, in particular conditional calculations. First, the primitive function = determines whether two (or more) numbers are equal. If so, it produces #true, otherwise #false. Second, there is a kind of BSL expression that we haven’t mentioned so far: the if expression. It uses the word “if” as if it were a primitive function; it isn’t. The word “if” is followed by three expressions, separated by blank spaces (that includes tabs, line breaks, etc.). Naturally the entire expression is enclosed in parentheses. Here is an example:

```
(if (= x 0) 0 (/ 1 x))
```

This if expression contains (= x 0), 0, and (/ 1 x), three so-called sub-expressions. The evaluation of this expression proceeds in two steps:

1. The first expression is always evaluated. Its result must be a Boolean.
2. If the result of the first expression is #true, then the second expression is evaluated; otherwise the third one is. Whatever their results are, they are also the result of the entire if expression.

Right-click on the result and choose a different representation.

Given the definition of x above, you can experiment with if expressions in the interactions area:

```
> (if (= x 0) 0 (/ 1 x))
0.5
```

Using the laws of arithmetic, you can figure out the result yourself:

```
(if (= x 0) 0 (/ 1 x))
== ; because x stands for 2
(if (= 2 0) 0 (/ 1 2))
== ; 2 is not equal to 0, (= 2 0) is #false
(if #false 0 (/ 1 x))
(/ 1 2)
== ; normalize this to its decimal representation
0.5
```

In other words, DrRacket knows that x stands for 2 and that the latter is not equal to 0. Hence, (= x 0) produces the result #false, meaning if picks its third sub-expression to be evaluated.

Stop! Imagine you edit the definition so that it looks like this:

```
(define x 0)
```

What do you think

```
(if (= x 0) 0 (/ 1 x))
```

evaluates to in this context? Why? Show your calculation.

In addition to =, BSL provides a host of other comparison primitives. Explain what the following four comparison primitives determine about numbers: <, <=, >, >=.

Strings aren't compared with = and its relatives. Instead, you must use string=? or string<=? or string>=? if you ever need to compare strings. While it is obvious that string=? checks whether the two given strings are equal, the other two primitives are open to interpretation. Look up their documentation. Or, experiment, guess a general law, and then check in the documentation whether you guessed right.

You may wonder why it is ever necessary to compare strings with each other. So imagine a program that deals with traffic lights. It may use the strings
