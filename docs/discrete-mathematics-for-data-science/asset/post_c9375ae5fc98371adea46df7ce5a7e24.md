
For example, in the recursive count-down function below, recursion terminates when n becomes zero.

The base and general cases can be expressed as:

Base case: t(0) = 0

General case: t(n) = 1 + t(n - 1) for n > 0

Given those conditional cases with n = 3, the recurrence relation of a countdown function could be solved as:

t(3) = 1 + t(2) = 1 + 2 = 3
t(2) = 1 + t(1) = 1 + 1 = 2
t(1) = 1 + t(0) = 1 + 0 = 1

As you can see, t(n) = n for all n > 0. This is still true if we substitute n - 1 for t(n - 1), for all n > 0. That is, by inductive reasoning we accept as true that t(n) = base case + general case.

## 11.5 TRACKING RECURSION USING A STACK

To execute a recursive function, a programming language is generally expected to first generate one or more stack data structures in memory that consist of operations and data. The area of the stack for a particular function call is termed a stack frame or activation record. Once this stack is loaded into memory, it is then executed.

TABLE 11.1 Function calls structured as a stack in memory

| Function | Counter | Address |
|---|---|---|
| countDown | 9 | 82994EE80 |
| countDown | 8 | 82994EF00 |
| countDown | 7 | 82994EF80 |
| countDown | 6 | 829948100 |
| countDown | 5 | 829948180 |
| countDown | 4 | 829948200 |
| countDown | 3 | 829948280 |
| countDown | 2 | 829948300 |
| countDown | 1 | 829948380 |

Each recursive call generates an activation record until the counter is 1. Generating activation records as such entails more memory than an iterative or non-recursive function.

Unlike an iterative algorithm, which re-executes its statements within each cycle, recursion generally puts the operational elements from all successive recursive calls on the stack, ahead of their eventual combined execution. Hence, if there are too many recursive calls relative to available memory, then recursion may lead to the infamous *stack overflow* and a crash.

The implementation of a recursive count down function:

```forth
{ DUP. CR i- DUP countDown ? } countDown WORD
9 countDown
9
8
7
...
```

To demonstrate how recursion is expanded on the stack before execution, here is a countDown version that emulates stack frame generation and execution.

```forth
{ DUP. CR i- DUP } countDown2 WORD
{ countDown2 ' } 9 LREPEAT
```

Here is how that program appears on the stack:

| Value | index | address |
| --- | --- | --- |
| countDown2 | 8 | 82AAFDE00 |
| countDown2 | 7 | 82AAFDE80 |
| countDown2 | 6 | 82AAF7180 |
| ... | | |

Note how the stack data structure ensures a certain data order, as last-in-first-out (LIFO). This order is an important consideration in the design of the algorithm.

The next step is to process the instructions and data that was put on the stack.

```forth
{ SWAP EXEC runit ? } runit WORD
GSC runit
9
8
7
...
```

Consider for example this recursive function that sums a list of integers:

```forth
{ 1 3 5 7 9 } nums LIST
{ + GSC 1 > sum ? } sum WORD
nums sum ( → 25)
```

The following code uses that same sum function to generate a mini program on the stack, emulating sum as it might appear in memory:

```forth
0 nums DS2RS
{{ R > R > sum ' } GRC 2 / LREPEAT } build WORD
{ EXEC GSC 1 > runit ? } runit WORD
build runit finalsum !
```

Here is how that program appears on the stack:

| Value | index | address |
| :--- | :--- | :--- |
| sum | 8 | 82A668B00 |
| 9 | 7 | 82A668B80 |
| 7 | 6 | 82A664680 |
| sum | 5 | 82A664700 |
| 5 | 4 | 82A664780 |
| 3 | 3 | 82A664800 |
| sum | 2 | 82A664880 |
| 1 | 1 | 82A664900 |
| 0 | 0 | 82A664980 |

No accumulator variable was used during the process of computing the sum, as each intermediate result is put on the stack to be added to the next number. With the stack assembled, its operations are then invoked with the final value assigned to a variable, in this case called finalsum. This process relates to the programming concept of lazy evaluation in that the evaluation of an expression is delayed until it is needed, avoiding evaluation in the interim.

The operation sequence of building and processing a stack may also be emulated in a non-recursive step-by-step manner as follows:

```forth
{ 1 3 5 7 9 } nums LIST
nums HEAD > R
nums TAIL HEAD > R
nums TAIL TAIL HEAD > R
nums TAIL TAIL TAIL HEAD > R
0 { R > + } GRC i- LREPEAT ( → 25)
```

The above code redirects output to the return stack via the >R operator. The expression “{ R > + }” retrieves the top number from the return stack via the R> operator and then adds it to the top number on the data stack. This occurs repeatedly until the return stack is empty.

## 11.6 WHEN TO USE RECURSION

Generally, solutions that require multiple recursive function calls (branches) in the same cycle and have a large number of input values are not suitable for recursion. This is because recursive algorithms generally require more memory than iterative algorithms, as discussed above.

What do you do with an elegant recursive algorithm that runs too slow? Perhaps relegate it to prototyping and then use a less elegant and better performing iterative algorithm in production.

Recursion is generally a suitable solution if:

- The problem is related to the principle of mathematical induction.
- Recursion allows for simpler or less syntax.
- Using recursion means better overall algorithm efficiency.
- There are few elements to process.
- The variables involved are immutable (can only be assigned once).

In some programming contexts, variables may not actually be variable, as they are defined as constant or immutable. This may lead to errors when an immutable variable is used in repetition and we attempt to mutate an immutable variable. In such cases a copy of the variable may actually be generated, unbeknownst to the programmer.

Immutability is the default state for non-reference variables in some functional programming languages, as well as in distributed programming environments where immutability protects variables against unintended results.

For example, to compute the sum of a series of numbers, consider that an accumulator variable named _sum_ is defined as immutable. Therefore, _sum_ cannot be used repetitiously, such as:

sum = sum + input

Or

sum @input + sum !

However, by using recursion we accommodate immutable accumulator variables because assignment only occurs once, after the enclosing function's stack was fully generated and then executed.

## 11.7 ADDITIONAL EXAMPLES OF RECURSIVE ALGORITHMS

Two popular functions in functional programming are called _map_ and _reduce_. Map takes a unary function as an argument and applies it separately to each element of a list. Reduce takes a binary function as an argument and applies it pairwise to list elements to produce a single aggregate result.

Map and reduce functionality can be combined into a single function. For example:

```forth
{ var @ EXEC >> GSC 0 > mapReduce ? } mapReduce WORD
```

An iterative alternative might look as follows:

```forth
{ var ! { var @ EXEC >> } GSC LREPEAT } mapReduce WORD
```

Here is the map usage, mapping a unary i+ operation across a list, storing the i+ operation in variable var:

```forth
i+ ' var !
alist mapReduce
```

Here is the reduce usage, reducing to a single result the aggregate of binary + operations to the values of alist, storing the + operation in variable var which is used internally by this version of mapReduce:

```forth
+ ' var !
alist mapReduce
```

Separate map and reduce functions can alternatively be defined, without the need of the prior host-guest function dependency. Consider the following code that computes the factorial of a number. First, a recursive version of each:

```forth
{ DUP i- DUP 1 > map ? } map WORD
{ * GSC 1 > reduce ? } reduce WORD
```

Here are iterative versions of each:

```forth
{ DUP i- { DUP i- } LREPEAT } map WORD
{ { * } GSC i- LREPEAT } reduce WORD
