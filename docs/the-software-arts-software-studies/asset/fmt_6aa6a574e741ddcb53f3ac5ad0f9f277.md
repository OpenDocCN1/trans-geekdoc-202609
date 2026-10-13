
# Beyond the Algorithm

As discussed in chapter 2, Turing demonstrated the equivalence between his automatic machines—now called Turing machines—and Alonzo Church’s lambda-calculus. Church’s student Stephen Kleene coined the phrase the “Church-Turing thesis” to refer to this equivalence. Also in chapter 2, we examined how the Church-Turing thesis has been popularized and expanded to the fantastical idea that Turing’s 1936 paper shows that machines of any sort—whether or not they have been rendered as a Turing machine or in the lambda-calculus—can be simulated by a Turing machine. But neither Turing nor Church proved that *all* machines could be rendered in their formalisms. What can be written in their formalisms is any procedure that meets the definition of an algorithm. Nevertheless, this hyperbolic popularization of the Church-Turing thesis is repeated again and again—even today.

Computer scientist Edward Lee has written a technically precise but easily accessible refutation of this popularization of the Church-Turing thesis. Lee writes, “Turing and Church considered only machines that operate on digital data, and only machines that compute algorithmically, via a step-by-step process. We routinely build machines that satisfy neither of these properties, such as my dishwasher.”^([17](#chapter_8.xhtml#chapter8-17)) This quotation is from the beginning of Lee’s discussion. In the rest, he leads us through some of the technical literature of computer science that refutes the notion that a universal Turing machine (UTM) is more than just a programmable Turing machine. Imagine if a UTM were really universal: we could download an app on our smartphones to wash dishes, function as a bicycle, or mow the lawn!

But what about self-driving cars? What about robots? Can’t a robot be designed to wash the dishes? Probably. But the point is that while such a robot would likely incorporate many algorithms that could be modeled as functions, the design of the whole thing—all of the interacting parts of the software systems of such a robot—cannot be modeled as a mathematical function.

## Outside the Algorithm

### Beyond Algorithms: Case 1, Milner’s Calculus for Concurrent Systems

To understand the gap that lies between mathematical functions and most software, we can read the works of Robin Milner, who extended the lambda-calculus to try to bridge this gap. In his Turing Award lecture, “Elements of Interaction,”^([18](#chapter_8.xhtml#chapter8-18)) Milner explains why the lambda-calculus needed to be extended: “For the much smaller world of sequential computation, a common semantic framework is founded on the central notion of a mathematical function and is formally expressed in a functional calculus—of which Alonzo Church’s `λ-calculus` is the famous prototype. Functions are an essential ingredient of the air we breathe, so to speak, when we discuss the semantics of sequential programming. But for concurrent programming and interactive systems in general, we have nothing comparable.”^([19](#chapter_8.xhtml#chapter8-19)) Milner called his extension to the lambda-calculus a Calculus for Concurrent Systems (CCS).

Milner continues his comparison like this: “In the `λ-calculus`, all computation comes down to just one thing, called *reduction*—the act of passing an argument to a function; we may call this the *atom of behavior* of the `λ-calculus`. In just the same way, an *interaction*—the passage of a single datum between processes—is the atom of behavior in CCS.”^([20](#chapter_8.xhtml#chapter8-20))

Robots incorporate multiple concurrent processes, as does any other system that includes software and interacts with the world—even interfaces as simple as keyboards that asynchronously capture our keystrokes as we type. The `λ-calculus` (and therefore algorithms and Turing’s automatic machines) are inadequate for modeling such concurrent systems, because they exclude, by definition, any form of interaction.

Turing machines are automatic machines that have input and output but do not stop to interact with a user, an “external operator.” Functions of the `λ-calculus` work by substituting variables and reducing the body of the function without stopping to interact. These formalisms are imagined to work instantaneously. For example, substituting the value of `y` into the variable `x` is supposed to be “atomic” in the sense that interrupting substitution *in medias res* is not addressed in the notation: `(λx.x)y = [y/x]x`, but what if, in the midst of the substitution, something changes the value of `y`?

Milner illustrates this possibility with three simple programs, each of which includes one or two assignment statements. Recall from chapter 2 that an assignment statement in an ALGOL-like language can be written like this: `y := 1`, meaning that after the assignment statement has executed, the variable `y` contains the value 1. Here are Milner’s three example programs:

```
P1: y := 1; y := y + 1;
P2: y := 2;
P3: y := 3.
```

P1 and P2, if run without any interference, both give the variable `y` the value 2. In P1, it takes two assignment statements to accomplish this: first `y` gets the value 1, and then it gets the value 1 + 1 or 2. So, in a functional notation, P1 and P2 are equivalent, because they both assign the variable `y` the value 2.

However, if we run either P1 or P2 concurrently with P3, P1 and P2 will not be equivalent. Assume that assignment statements take about the same amount of time to execute; that is, to move the value into the memory location designated by the variable. Then, run concurrently, P2 and P3 will result in `y` having the value of either 2 or 3 (depending on which assignment statement finishes last). By comparison, when P1 and P3 are executed concurrently, `y` will be 2, 3, or 4—again depending on which assignment statement finishes last.

Let us use the notation `Q | R` to mean that the programs Q and R are executed concurrently—in parallel—and let us denote the possible results of execution as a set in which the elements are the possible value(s) of the variable `y`: `P1 = {2}`, `P2 = {2}`, `P1 | P3 = {2, 3}`, and `P2 | P3 = {2, 3, 4}`.

The point of Milner’s example is that even though `P1 = P2`, when run concurrently with P3, they are different. Specifically, if we use sets to denote the range of the “functions,” P1 and P2 cease to be the same when they are combined with a third “function.”

Milner’s little example poses a big problem for any effort to model software as a Turing machine, as an algorithm, or as a function of the `λ-calculus`, because the composition of mathematical functions is not supposed to change the definitions of the functions being composed. Yet, composing functions with the `|` operator is quite unlike composing functions by using addition, subtraction, multiplication, or division. Imagine what arithmetic would be like if `1 + 1 = 2`, 3, or 4, depending on whether and when other operations of arithmetic are under way!

Why is this a big problem for mathematicians? The short answer is simply that computer programs are not mathematical functions, or at least not simply mathematical functions. The longer answer is that in actual systems that connect with other systems and that are used by people, timing and interaction are crucial, and Turing, as noted, ruled out interaction right from the start by limiting his formalism to automatic machines akin to mathematical functions and subsequently known as algorithms.

### Beyond Algorithms: Case 2, Wegner’s Interaction Machines
