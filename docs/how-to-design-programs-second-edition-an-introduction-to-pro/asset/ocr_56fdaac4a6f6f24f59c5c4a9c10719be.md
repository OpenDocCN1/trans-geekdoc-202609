data definition. Since our data definitions are really just English descriptions of classes, you may indeed define the class of temperatures in a much more accurate manner than shown here. In this book, we use a stylized form of English for such data definitions, and the next chapter introduces the style for imposing constraints such as “larger than –274.”

So far, you have encountered the names of four classes of data: Number, String, Image, and Boolean. With that, formulating a new data definition means nothing more than introducing a new name for an existing form of data, say, “temperature” for numbers. Even this limited knowledge, though, suffices to explain the outline of our design process.

> At this point, you may wish to reread the section on Systematic Program Design in the Preface, especially figure 1.

# The Design Process

Once you understand how to represent input information as data and to interpret output data as information, the design of an individual function proceeds according to a straightforward process:

+   1. Express how you wish to represent information as data. A one-line comment suffices:

```
; We use numbers to represent centimeters.
```

Formulate data definitions, like the one for Temperature, for the classes of data you consider critical for the success of your program.

+   2. Write down a signature, a statement of purpose, and a function header.

A function signature is a comment that tells the readers of your design how many inputs your function consumes, from which classes they are drawn, and what kind of data it produces. Here are three examples for functions that respectively

+   • consume one String and produce a Number:

```
; String -> Number
```

+   • consume a Temperature and produce a String: