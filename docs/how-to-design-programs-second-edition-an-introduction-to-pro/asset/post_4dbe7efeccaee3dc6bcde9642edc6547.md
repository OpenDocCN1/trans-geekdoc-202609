
Just in case you have not taken geometry courses or in case you forgot the formula that you encountered there, the point (x,y) has the distance

$\sqrt{x^2 + y^2}$

from the origin. After all, we are teaching you how to design programs, not how to be a geometer.

To develop the desired expression, it is best to click RUN and to experiment in the interactions area. The RUN action tells DrRacket what the current values of x and y are so that you can experiment with expressions that involve x and y:

```
> x
3
> y
4
> (+ x 10)
13
> (* x y)
12
```

Once you have the expression that produces the correct result, copy it from the interactions area to the definitions area.

To confirm that the expression works properly, change x to 12 and y to 5, then click RUN. The result should be 13.

Your mathematics teacher would say that you computed the distance formula. To use the formula on alternative inputs, you need to open DrRacket, edit the definitions of x and y so they represent the desired coordinates, and click RUN. But this way of reusing the distance formula is cumbersome and naive. We will soon show you a way to define functions, which makes reusing formulas straightforward. For now, we use this kind of exercise to call attention to the idea of functions and to prepare you for programming with them.

## 1.2 The Arithmetic of Strings

A widespread prejudice about computers concerns their innards. Many believe that it is all about bits and bytes—whatever those are—and possibly numbers because everyone knows that computers can calculate. While it is true that electrical engineers must understand and study the computer as just such an object, beginning programmers and everyone else need never (ever) succumb to this thinking.

Programming languages are about computing with information, and information comes in all shapes and forms. For example, a program may deal with colors, names, business letters, or conversations between people. Even though we could encode this kind of information as numbers, it would be a horrible idea. Just imagine remembering large tables of codes, such as 0 means “red” and 1 means “hello,” and the like.

Instead, most programming languages provide at least one kind of data that deals with such symbolic information. For now, we use BSL’s strings. Generally speaking, a String is a sequence of the characters that you can enter on the keyboard, plus a few others, about which we aren’t concerned just yet, enclosed in double quotes. In the Prologue, we have seen a number of BSL strings: "hello", "world", "blue", "red", and others. The first two are words that may show up in a conversation or in a letter; the others are names of colors that we may wish to use.

Note We use 1String to refer to the keyboard characters that make up a String. For example, "red" consists of three such 1Strings: "r", "e", "d". As it turns out, there is a bit more to the definition of 1String, but for now thinking of them as Strings of length 1 is fine. End

BSL includes only one operation that exclusively consumes and produces strings: string-append, which, as we have seen in the Prologue, concatenates two given strings into one. Think of string-append as an operation that is just like +. While the latter consumes two (or more) numbers and produces a new number, the former consumes two or more strings and produces a new string:

```
> (string-append "what a " "lovely " "day" " 4 BSL")
"what a lovely day 4 BSL"
```

Nothing about the given numbers changes when + adds them up, and nothing about the given strings changes when string-append concatenates them into one big string. If you wish to evaluate such expressions, you just need to think that the obvious laws hold for string-append, similar to those for +:

```
(+ 1 1) == 2   (string-append "a" "b") == "ab"
(+ 1 2) == 3   (string-append "ab" "c") == "abc"
(+ 2 2) == 4   (string-append "a" " " ) == "a "
...   ...
```

### Exercise 2. Add the following two lines to the definitions area:

```
(define prefix "hello")
(define suffix "world")
```

Then use string primitives to create an expression that concatenates prefix and suffix and adds "_" between them. When you run this program, you will see "hello_world" in the interactions area.

See exercise 1 for how to create expressions using DrRacket.

## 1.3 Mixing It Up

All other operations (in BSL) concerning strings consume or produce data other than strings. Here are some examples:

- string-length consumes a string and produces a number;
- string-ith consumes a string s together with a number i and extracts the 1String located at the ith position (counting from 0); and
- number->string consumes a number and produces a string.

Also look up substring and find out what it does.

If the documentation in HelpDesk appears confusing, experiment with the functions in the interactions area. Give them appropriate arguments, and find out what they compute. Also use inappropriate arguments for some operations just to find out how BSL reacts:

```
> (string-length 42)
string-length:expects a string, given 42
```

As you can see, BSL reports an error. The first part “string-length” informs you about the operation that is misapplied; the second half states what is wrong with the arguments. In this specific example, string-length is supposed to be applied to a string but is given a number, specifically 42.

Naturally, it is possible to nest operations that consume and produce different kinds of data as long as you keep track of what is proper and what is not. Consider this expression from the Prologue:

```
(+ (string-length "hello world") 20)
```

The inner expression applies string-length to "hello world", our favorite string. The outer expression has + consume the result of the inner expression and 20.

Let’s determine the result of this expression in a step-by-step fashion:

```
(+ (string-length "hello world") 20)
==
(+ 11 20)
==
31
```

Not surprisingly, computing with such nested expressions that deal with a mix of data is no different from computing with numeric expressions. Here is another example:

```
(+ (string-length (number->string 42)) 2)
==
(+ (string-length "42") 2)
==
(+ 2 2)
==
4
```

Before you go on, construct some nested expressions that mix data in the **wrong** way, say,

```
(+ (string-length 42) 1)
```

Run them in DrRacket. Study the red error message but also watch what DrRacket highlights in the definitions area.

### Exercise 3. Add the following two lines to the definitions area:

```
(define str "helloworld")
(define i 5)
```

Then create an expression using string primitives that adds "_" at position i. In general this means the resulting string is longer than the original one; here the expected result is "hello_world".

_Position_ means _i_ characters from the left of the string, but programmers start counting at 0. Thus, the 5th letter in this example is "w", because the 0th letter is "h". **Hint** When you encounter such “counting problems” you may wish to add a string of digits below str to help with counting:

```
(define str "helloworld")
(define ind "0123456789")
(define i 5)
```

See exercise 1 for how to create expressions in DrRacket.

### Exercise 4. Use the same setup as in exercise 3 to create an expression that deletes the ith position from str. Clearly this expression creates a shorter string than the given one. Which values for i are legitimate?

## 1.4 The Arithmetic of Images

An Image is a visual, rectangular piece of data, for example, a photo or a geometric figure and its frame. You can insert images in DrRacket wherever you can write down an expression because images are values, just like numbers and strings.

> Remember to require the 2htdp/image library in a new tab.

Your programs can also manipulate images with primitive operations. These primitive operations come in three flavors. The first kind concerns the creation of basic images:

- circle produces a circle image from a radius, a mode string, and a color string;
- ellipse produces an ellipse from two radii, a mode string, and a color string;
- line produces a line from two points and a color string;
- rectangle produces a rectangle from a width, a height, a mode string, and a color string;
- text produces a text image from a string, a font size, and a color string; and
- triangle produces an upward-pointing equilateral triangle from a size, a mode string, and a color string.

The names of these operations mostly explain what kind of image they create. All you must know is that mode strings means "solid" or "outline", and color strings are strings such as "orange", "black", and so on.

Play with these operations in the interactions window:
