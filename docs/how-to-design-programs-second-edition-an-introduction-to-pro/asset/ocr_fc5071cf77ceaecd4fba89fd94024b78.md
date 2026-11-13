To this end, it comes with one required sub-expression, whose value becomes the *initial state* of the program. Otherwise big-bang consists of one required clause and many optional clauses. The required to-draw clause tells DrRacket how to render the state of the program, including the initial one. Each of the other, optional clauses tells the operating system that a certain function takes care of a certain event. Taking care of an event in BSL means that the function consumes the state of the program and a description of the event, and that it produces the next state of the program. We therefore speak of the *current state* of the program.

**Terminology** In a sense, a big-bang expression describes how a program connects with a small segment of the world. This world might be a game that the program's users play, an animation that the user watches, or a text editor that the user employs to manipulate some notes. Programming language researchers therefore often say that big-bang is a description of a small world: its initial state, how states are transformed, how states are rendered, and how big-bang may determine other attributes of the current state. In this spirit, we also speak of the *state of the world* and even call big-bang programs *world programs*. **End**

Let's study this idea step-by-step, starting with this definition:

```
(define (number->square s)
(square s "solid" "red"))
```

The function consumes a positive number and produces a solid red square of that size. After clicking *RUN*, experiment with the function, like this:

+   - `> (number->square 5)`
+   - `> (number->square 10)`
+   - `> (number->square 20)`

![](bbox=[0.13, 0.67, 0.16, 0.69])

![](bbox=[0.13, 0.7, 0.17, 0.73])

![](bbox=[0.13, 0.75, 0.18, 0.78])

It behaves like a batch program, consuming a number and producing an image, which DrRacket renders for you.

Now try the following big-bang expression in the interactions area: