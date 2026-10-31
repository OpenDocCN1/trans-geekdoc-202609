![](bbox=[0.23, 0.11, 0.78, 0.37])

**FIGURE 1.2:** Non-overlapping balls centered at codewords

**1.7 Definition.** A binary code $(n, M, d)_2$ is a set of $M$ bitstrings in $\mathbb{F}_2^n$ such that any two different elements of the code (codewords) are at distance $\ge d$. We call $n$ the **length** and $d$ the **minimum distance** of the code.

A code of minimum distance 5 can correct 2 errors, minimum distance 7 can correct 3 errors and so on. A fundamental problem of coding theory is the following: Given $n$ and $d$, find the largest $M$ such that there is a code $(n, M, d)_2$.

+   1. A binary code $(n, M, d)_2$ is a collection of $M$ bitstrings of length $n$ such that any two different of these codewords are at Hamming distance at least $d$.
+   2. A basic problem of coding theory: determine the maximum $M$ such that an $(n, M, d)_2$-code exists.
+   3. A code can correct $e$ errors provided its minimum distance is $d \ge 2e + 1$.
+   4. We saw a $(6, 8, 3)_2$–code.

# Exercises 1.3

**1.3.1.** If we want to correct 8 bit errors, what would the minimum distance of the code have to be?