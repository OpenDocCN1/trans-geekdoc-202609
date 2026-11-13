
construction step.

Design the function add-savannah. The function consumes an image and four numbers: (1) the x-coordinate of a line’s base point, (2) the y-coordinate of a line’s base point, (3) the length of the line, and (4) the angle of the line. It adds a fractal Savannah tree to the given image.

Unless the line is too short, the function adds the specified line to the image. It then divides the line into three segments. It recursively uses the two intermediate points as the new starting points for two lines. The lengths and the angles of the two branches change in a fixed manner, but independently of each other. Use constants to define these changes and work with them until you like your tree well enough.

**Hint** Experiment with shortening each left branch by at least one third and rotating it left by at least 0.15 degrees. For each right branch, shorten it by at least 20% and rotate it by 0.2 degrees in the opposite direction.

Géraldine Morin suggested this exercise.

## Exercise 528. Graphics programmers often need to connect two points with a smooth curve where “smooth” is relative to some perspective. Here are two sketches:

![](img/19fbe4068996ced0ce42cec7fb82a834_953_0.png)

![](img/19fbe4068996ced0ce42cec7fb82a834_953_1.png)

The left one shows a smooth curve, connecting points A and C; the right one supplies the perspective point, B, and the angle of an observer.

One method for drawing such curves is due to Bézier. It is a prime example of generative recursion, and the following sequence explains the eureka! behind the algorithm:

![](img/19fbe4068996ced0ce42cec7fb82a834_954_0.png)

![](img/19fbe4068996ced0ce42cec7fb82a834_954_1.png)

![](img/19fbe4068996ced0ce42cec7fb82a834_954_2.png)

Consider the image on the left. It reminds you that the three given points determine a triangle and that the connection from A to C is the focal point of the algorithm. The goal is to pull the line from A to C toward B so that it turns into a smooth curve.

Now turn to the image in the middle. It explains the essential idea of the generative step. The algorithm determines the midpoint on the two observer lines, A-B and B-C, as well as their midpoint, A-B-C.

Finally, the right-most image shows how these three new points generate two distinct recursive calls: one deals with the new triangle on the left and the other one with the triangle on the right. More precisely, A-B and B-C become the new observer points and the lines from A to A-B-C and from C to A-B-C become the foci of the two recursive calls.

When the triangle is small enough, we have a trivially solvable case. The algorithm just draws the triangle, and it appears as a point on the given image. As you implement this algorithm, you need to experiment with the notion of “small enough” to make the curve look smooth.

## 34 Summary

This last part is about designing with accumulators, a mechanism for collecting knowledge during a data structure traversal. Adding an accumulator can fix performance flaws and eliminate termination problems. Your takeaway from this part are two and a half design lessons:

- 1. The first step is to recognize the need for introducing an accumulator. Traversals “forget” pieces of the argument when they step from one piece to the next. If you discover that such knowledge could simplify the function’s design, consider introducing an accumulator. The first step is to switch to the **accumulator template**.

- 2. The key step is to formulate an accumulator statement. The latter must express **what knowledge** the accumulator gathers **as what kind of data**. In most cases, the accumulator statement describes the difference between the original argument and the current one.

- 3. The third step, a minor one, is to deduce from the accumulator statement (a) what the initial accumulator value is, (b) how to maintain it during traversal steps, and (c) how to exploit its knowledge.

The idea of accumulating knowledge is ubiquitous, and it appears in many different forms and shapes. It is widely used in so-called functional languages like ISL+. Programmers using imperative languages encounter accumulators in a different way, mostly via assignment statements in primitive looping constructs because the latter cannot return values. Designing such imperative accumulator programs proceeds just like the design of accumulator functions here, but the details are beyond the scope of this first book on systematic program design.

![](img/19fbe4068996ced0ce42cec7fb82a834_956_0.png)

## EPILOGUE: MOVING ON

You have reached the end of this introduction to computing and programming, or program design, as we say here. While there is more to learn about both subjects, this is a good point to stop, summarize, and look ahead.

## Computing

In elementary school, you learned to calculate with numbers. At first, you used numbers to count real things: three apples, five friends, twelve bagels. A bit later, you encountered addition, subtraction, multiplication, and even division; then came fractions. Eventually, you found out about variables and functions, which your teachers called algebra. Variables represented numbers, and functions related numbers to numbers.

Because you used numbers throughout this process, you didn’t think much of numbers as a means to represent information about the real world. Yes, you had started with three bears, five wolves, and twelve horses; but by high school, nobody reminded you of this relationship.

When you move from mathematical calculations to computing, the step from information to data and back becomes central. Nowadays, programs process representations of music, videos, molecules, chemical compounds, business case studies, electrical diagrams, and blueprints. Fortunately, you don’t need to encode all this information with numbers or, worse, just 0 and 1; if you had to, life would be unimaginably tedious. Instead, computing generalizes arithmetic and algebra so that when you program, you can code—and your programs can compute—with strings, Booleans, characters, structures, lists, functions, and many more kinds of data.

Classes of data and their functions come with equational laws that explain their meaning, just like the laws for numbers and their functions. While these equational laws are as simple as “(+ 1 1) evaluates to 2” and “(not #true) equals #false,” you can use them to predict the behavior of entire programs. When you run a program, you actually just apply one of its many functions, an act that you can explain with the beta rule first mentioned in intermezzo 1. Once the variables are replaced with values, the laws of data take over until you have either only a value or another function application. But yes, that's all there is to computing.

## Program Design

A typical software development project requires the collaboration of many programmers, and the result consists of thousands of functions. Over the life span of such a project, programmers come and go. Hence, the design structure of programs is really a means of communication among programmers across time. When you approach code that someone else wrote some time ago, the program ought to express its purpose and its relationships to other pieces—because that other person might not be around anymore.

In such a dynamic context, programmers must create programs in a disciplined manner if they wish to work reasonable numbers of hours or produce high-quality products. Following a systematic design method guarantees that the program organization is comprehensible. Others can then easily understand the pieces and the whole, and then fix bugs or add new pieces of functionality.

The design process of this book is one of these methods, and you ought to follow it whenever you create programs you might care about. You start with an analysis of the world of information and a description of the data that represents the information. Then you make a plan, a work list of functions needed. If this list is large, you refine the process in an iterative manner. You start with a subset of functions that quickly yields a product with which a client can interact. As you observe these interactions, you will quickly figure out which elements of your work list to tackle next.

Designing a program, or only a function, requires a rigorous understanding of what it computes. Unless you can describe the purpose of a piece of code with a concise statement, you cannot produce anything useful for future programmers. Make up, and work through, examples. Turn these examples into a suite of tests. This test suite is even more important when it comes to future modifications of the program. Anyone who changes the code can rerun these tests and reconfirm that the program still works for the basic examples.

Eventually your program will also fail. Other programmers may use it in an unanticipated manner. Real-world users may find differences between expected
