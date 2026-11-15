> “if a man will begin with certainties, he shall end in doubts; but if he will be content to begin with doubts, he shall end in certainties.” – Sir Francis Bacon

¹S. F. Bacon, *The Advancement of Learning*. 1605, vol. 8. (This quote of Sir Francis Bacon may describe a recursive function, wherein its self-reference occurs only until there is doubt.) ¶

Processing data structures, such as lists, entails a repetition of operations. Rather than tediously hand-coding these operations over and over, we can invoke a function that repeats them. This can be accomplished with either iterative loops or recursive functions.

A non-recursive algorithm that repeats is commonly referred to as *iterative*. Iterative algorithms use loops for repetition instead of recursive calls to themselves.

Requirements for a recursive function:

+   - An input value.
+   - Evaluation of the input, leading to either a recursive call or to an end of the recursion.
+   - The solution is found in the final state of the input.

Consider the function f as it is controlled by the following function that repeats eight times:

```
f 8 REPEAT
```

Alternatively, we can effectively repeat the operations by having them inside a function definition that also refers to itself. That is, have the function f invoke the function f, such as: