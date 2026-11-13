
introductory books still commingle them. Thus, working with BSL and DrRacket allows you to focus on the design of the core of programs, and, when you have enough experience with that, you can learn to design the information-data translation parts.

Here we use two preinstalled teachpacks to demonstrate the separation of data and information: 2htdp/batch-io and 2htdp/universe. Starting with this chapter, we develop design recipes for **batch** and **interactive** programs to give you an idea of how complete programs are designed. Do keep in mind that the libraries of full-fledged programming languages offer many more contexts for complete programs, and that you will need to adapt the design recipes appropriately.

Given the central role of information and data, program design must start with the connection between them. Specifically, we, the programmers, must decide how to use our chosen programming language to *represent* the relevant pieces of information as data and how we should *interpret* data as information. Figure 15 explains this idea with an abstract diagram.

![](img/19fbe4068996ced0ce42cec7fb82a834_127_0.png)

Figure 15: From information to data, and back

To make this idea concrete, let’s work through some examples. Suppose you are designing a program that consumes and produces information in the form of numbers. While choosing a representation is easy, an interpretation requires explaining what a number such as 42 denotes in the domain:

- 42 may refer to the number of pixels from the top margin in the domain of images;
- 42 may denote the number of pixels per clock tick that a simulation or game object moves;
- 42 may mean a temperature, on the Fahrenheit, Celsius, or Kelvin scale for the domain of physics;
- 42 may specify the size of some table if the domain of the program is a furniture catalog; or
- 42 could just count the number of characters in a string.

The key is to know how to go from numbers as information to numbers as data and vice versa.

Since this knowledge is so important for everyone who reads the program, we often write it down in the form of comments, which we call *data definitions*. A data definition serves two purposes. First, it names a collection of data—a *class*—using a meaningful word. Second, it informs readers how to create elements of this class and how to decide whether some arbitrary piece of data belongs to the collection.

> Computing scientists use “class” to mean something like a “mathematical set.”

Here is a data definition for one of the above examples:

```
; A Temperature is a Number.
; **interpretation** represents Celsius degrees
```

The first line introduces the name of the data collection, Temperature, and tells us that the class consists of all Numbers. So, for example, if we ask whether 102 is a temperature, you can respond with “yes” because 102 is a number and all numbers are temperatures. Similarly, if we ask whether "cold" is a Temperature, you will say “no” because no string belongs to Temperature. And, if we asked you to make up a sample Temperature, you might come up with something like -400.

If you happen to know that the lowest possible temperature is approximately -274° C, you may wonder whether it is possible to express this knowledge in a data definition. Since our data definitions are really just English descriptions of classes, you may indeed define the class of temperatures in a much more accurate manner than shown here. In this book, we use a stylized form of English for such data definitions, and the next chapter introduces the style for imposing constraints such as “larger than -274.”

So far, you have encountered the names of four classes of data: Number, String, Image, and Boolean. With that, formulating a new data definition means nothing more than introducing a new name for an existing form of data, say, “temperature” for numbers. Even this limited knowledge, though, suffices to explain the outline of our design process.

> At this point, you may wish to reread the section on Systematic Program Design in the Preface, especially figure 1.

## The Design Process

Once you understand how to represent input information as data and to interpret output data as information, the design of an individual function proceeds according to a straightforward process:

- 1. Express how you wish to represent information as data. A one-line comment suffices:

```
; We use numbers to represent centimeters.
```

Formulate data definitions, like the one for Temperature, for the classes of data you consider critical for the success of your program.

- 2. Write down a signature, a statement of purpose, and a function header.

A function signature is a comment that tells the readers of your design how many inputs your function consumes, from which classes they are drawn, and what kind of data it produces. Here are three examples for functions that respectively

- consume one String and produce a Number:

```
; String -> Number
```

- consume a Temperature and produce a String:

```
; Temperature -> String
```

As this signature points out, introducing a data definition as an alias for an existing form of data makes it easy to read the intention behind signatures.

Nevertheless, we recommend that you stay away from aliasing data definitions for now. A proliferation of such names can cause quite a lot of confusion. It takes practice to balance the need for new names and the readability of programs, and there are more important ideas to understand right now.

- consume a Number, a String, and an Image:

```
; Number String Image -> Image
```

Stop! What does this function produce?

A *purpose statement* is a BSL comment that summarizes the purpose of the function in a single line. If you are ever in doubt about a purpose statement, write down the shortest possible answer to the question

*what does the function compute?*

Every reader of your program should understand what your functions compute **without** having to read the function itself.

A multi-function program should also come with a purpose statement. Indeed, good programmers write two purpose statements: one for the reader who may have to modify the code and another one for the person who wishes to use the program but not read it.

Finally, a *header* is a simplistic function definition, also called a *stub*. Pick one variable name for each class of input in the signature; the body of the function can be any piece of data from the output class. These three function headers match the above three signatures:

- (define (f a-string) 0)
- (define (g n) "a")
- (define (h num str img) (empty-scene 100 100))

Our parameter names reflect what kind of data the parameter represents. Sometimes, you may wish to use names that suggest the purpose of the parameter.

When you formulate a purpose statement, it is often useful to employ the parameter names to clarify what is computed. For example,

```
; Number String Image -> Image
; adds s to img,
; y pixels from the top and 10 from the left
(define (add-image y s img)
  (empty-scene 100 100))
```

At this point, you can click the RUN button and experiment with the function. Of course, the result is always the same value, which makes these experiments quite boring.

- 3. Illustrate the signature and the purpose statement with some functional examples. To construct a functional example, pick one piece of data from each input class from the signature and determine what you expect back.

Suppose you are designing a function that computes the area of a square. Clearly this function consumes the length of the square's side, and that is best represented with a (positive) number. Assuming you have done the first process step according to the recipe, you add the examples between the purpose statement and the header and get this:

```
; Number -> Number
; computes the area of a square with side len
; given: 2, expect: 4
; given: 7, expect: 49
(define (area-of-square len) 0)
```

- 4. The next step is to take inventory, to understand what are the givens and what we need to compute. For the simple functions we are considering right now, we know that they are given data via parameters. While
