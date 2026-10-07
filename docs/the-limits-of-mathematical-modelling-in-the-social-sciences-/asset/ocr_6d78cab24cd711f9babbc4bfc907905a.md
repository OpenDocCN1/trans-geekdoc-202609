# Quasi-trivial machines: intuitions

The counterexample function is highly oscillating. Since it collects the counterexamples for a problem in the class $NP$, out of a natural listing of the poly machines, there will be cases where the counterexample takes a long time to reveal itself, while the very next poly machine outputs a counterexample in the first trials. So the idea here is to construct a family of poly machines, which produce counterexamples that can be seen as part of a fast-growing functions; a function which grows as fast as one wishes.

So, we construct a family of poly machines that fits our purpose:

+   - Consider an exponential algorithm for the problem we are dealing with — it will settle all instances of the question, albeit in exponential time. Call it E.
- Build the following algorithm A:
  $A = E$ for any input up to instance $k$.
  $A = 0$ for all inputs $> k$.
- $A$ is a poly machine, and the value of the counterexample at (the Gödel number of) $A$ is $k+1$.
- Now make $k$ as large as one wishes.

Notice that $k$ requires about $\log k$ bits to be described. As such, a value must be coded in our machine’s Gödel number, which will be very large for large $k$. However, we need a kind of controlled growth in Gödel numbers for the A-machines family. So, instead of explicitly encoding $k$ as a numerical, we use it as the value of a function; we put $k=g(i)$, for a fast-growing function $g$. For the $s-m-n$ theorem comes handy and ensures that the modified $A$’s Gödel numbers will always grow as a primitive recursive function, but not beyond it.

# Quasi-trivial machines: formal treatment

Recall the operation time of a Turing machine is given as follows: given that $x$ is the Turing machine’s input (in binary form) and $|x|$ is its length, if M stops over an input $x$, then we have the following definition.