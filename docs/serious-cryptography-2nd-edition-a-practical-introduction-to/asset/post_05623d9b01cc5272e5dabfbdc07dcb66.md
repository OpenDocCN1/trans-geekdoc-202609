
otherwise will do the same thing at the same cost, whatever the integer’s length.

To see the difference between linear, quadratic, and exponential time complexities, look at how complexity grows for $O(n)$ (linear) versus $O(n^2)$ (quadratic) versus $O(2^n)$ (exponential) in Figure 9-1.

![](img/ace4de942d037de8ea5835bc9fbe57cd_207_0.png)

*Figure 9-1: The growth of exponential, quadratic, and linear complexities, from the fastest to the slowest growing*

Exponential complexity means the problem is practically impossible to solve, and linear complexity means the solution is feasible, whereas quadratic complexity is somewhere between the two.

## Polynomial vs. Superpolynomial Time

The quadratic $O(n^2)$ complexity (the middle curve in Figure 9-1) is a special case of the broader class of polynomial complexities, or $O(n^k)$, where $k$ is some fixed number such as 3, 2.373, 7/10, or the square root of 17. Polynomial-time algorithms are eminently important in complexity theory and in cryptography because they’re the very definition of practically feasible. When an algorithm runs in *polynomial time*, or *polytime* for short, it completes in a decent amount of time even if the input is large. That’s why polynomial time is synonymous with “efficient” for complexity theorists and cryptographers.

In contrast, you can view algorithms running in *superpolynomial time*—that is, in $O(f(n))$, where $f(n)$ is any function that grows faster than any polynomial—as impractical. I’m saying superpolynomial, and not just exponential, because there are complexities in between polynomial and the well-known exponential complexity O(2^n), such as O(n^{log(n)}), as Figure 9-2 shows.

![](img/ace4de942d037de8ea5835bc9fbe57cd_208_0.png)

Figure 9-2: The growth of the 2^n, n^{log[n]}, and n^2 functions, from the fastest to the slowest growing

O(n^2) or O(n^3) may be efficient, but O(n^{99,999,999,999}) obviously isn't. In other words, polytime is fast in practice as long as the exponent isn't too large. Fortunately, all polynomial-time algorithms found to solve actual problems have small exponents. For example, O(n^{2.373}) is the time complexity of the best known algorithm for multiplying two n × n matrices in theory, as this algorithm is never used in practice. The 2002 breakthrough polynomial-time deterministic algorithm for identifying n-bit prime numbers initially had a complexity O(n^12), but it was later improved to O(n^6). Polynomial time thus may not be the perfect definition of a practical time for an algorithm, but it's the best we have.

By extension, you can consider a problem that can't be solved by a polynomial-time algorithm impractical, or hard. As an example, for a straightforward key search, there's no way to beat the O(2^n) complexity unless the cipher is somehow broken.

NOTE Exponential complexity O(2^n) is not the worst you can get. Some complexities grow even faster and thus characterize algorithms even slower to compute—for example, the complexity O(n^n) or the exponential factorial O(n^{f(n-1)}), where for any x, the function f is here recursively defined as f(x) = x^{f(x-1)}. In practice, you'll never encounter algorithms with such preposterous complexities.

You know that there’s no way to beat the $O(2^n)$ complexity of a brute-force key search (as long as the cipher is secure), but you won’t always know the fastest way to solve a computational problem in general. A large portion of the research in complexity theory is about proving complexity *bounds* on the running time of algorithms solving a given problem. To make their job easier, complexity theorists have categorized computational problems in different groups, or *classes*, according to the effort needed to solve them.

## Complexity Classes

In mathematics, a *class* is a group of objects with some similar attribute. For example, all computational problems solvable in time $O(n^2)$, which complexity theorists simply denote **TIME**($n^2$), are one class. Likewise, **TIME**($n^3$) is the class of problems solvable in time $O(n^3)$, **TIME**($2^n$) is the class of problems solvable in time $O(2^n)$, and so on. For the same reason that a supercomputer can compute whatever a laptop can compute, any problem solvable in $O(n^2)$ is also solvable in $O(n^3)$. Hence, any problem in the class **TIME**($n^2$) also belongs to the class **TIME**($n^3$), which also both belong to the class **TIME**($n^4$), and so on. The union of all the classes **TIME**($n^k$), for all constants $k$, is **P**, which stands for polynomial time.

If you’ve programmed a computer, you’ll know that seemingly fast algorithms may still crash your system by eating all its memory resources. When selecting an algorithm, you should consider not only its time complexity but also how much memory it uses, or its *space complexity*. This is especially important because a single memory access is usually orders of magnitude slower than a basic arithmetic operation in a CPU.

Formally, you define an algorithm’s memory consumption as a function of its input length, $n$, in the same way you defined time complexity. The class of problems solvable using $f(n)$ bits of memory is **SPACE**($f(n)$). For example, **SPACE**($n^3$) is the class of problems solvable using on the order of $n^3$ bits of memory. Just as you had **P** as the union of all **TIME**($n^k$), the union of all **SPACE**($n^k$) problems is **PSPACE**.

While the lower the memory the better, a polynomial amount of memory doesn’t necessarily imply that an algorithm is practical. Take, for example, a brute-force key search, which takes negligible memory but is slow as hell. More generally, an algorithm can take forever, even if it uses just a few bytes of memory.

Any problem solvable in time $f(n)$ needs at most $f(n)$ memory, so **TIME**($f(n)$) is included in **SPACE**($f(n)$). In time $f(n)$, you can write up to $f(n)$ bits, and no more, because writing (or reading) 1 bit is assumed to take one unit of time; therefore, any problem in **TIME**($f(n)$) can’t use more than $f(n)$ space. As a consequence, **P** is a subset of **PSPACE**.

## Nondeterministic Polynomial Time

**NP**, *nondeterministic polynomial time*, is the second most important complexity class, after the class **P** of all polynomial-time algorithms.

**NP** is the class of decision problems for which you can verify a solution in polynomial time—that is, efficiently—even though the solution may be hard to find. By *verified*, I mean that given a potential solution, you can run some polynomial-time algorithm that checks whether you’ve found an actual solution. For example, the problem of deciding whether there exists a key K such that C = **E**(K, P) given P and C for a symmetric cryptosystem **E** is in **NP**. This is because given a candidate key K₀, you can check that K₀ is the correct key by verifying that **E**(K₀, P) equals C. You can’t find a potential key (the solution), if it exists, in polynomial time, but you can check whether a key is correct.

Now for a counterexample: What about known-ciphertext attacks? This time, you get only some **E**(K, P) values for random unknown plaintext Pₛ. If you don’t know what the Pₛ are, then there’s no way to verify whether a potential key, K₀, is the right one. In other words, the key-recovery problem under known-ciphertext attacks is not in **NP** (let alone in **P**), as you can’t express it as a decision problem.

Another example of a problem not in **NP** is that of verifying the *absence* of a solution to a problem. Verifying that a solution is correct boils down to computing some algorithm with the candidate solution as an input and then checking the return value. However, to verify that *no* solution exists, you may need to go through all possible inputs. If there’s an exponential number of inputs, you won’t be able to efficiently prove that no solution exists. The absence of a solution is hard to show for the hardest problems in the class **NP**—the so-called **NP**-complete problems.

### NP-Complete Problems

**NP**-complete problems are the hardest decision problems in the class **NP**; you won’t know how to solve the worst-case instances of these problems in polynomial time. As complexity theorists discovered in the 1970s when they developed the theory of **NP**-completeness, **NP**’s hardest problems are all fundamentally equally hard. This was proven by showing that you can turn any efficient solution to any of the **NP**-complete problems into an efficient solution for any of the other **NP**-complete problems. In other words, if you can solve any **NP**-complete problem efficiently, you can solve all of them, as well as all problems in **NP**. How can this be?

**NP**-complete problems come in different guises, but they’re fundamentally similar from a mathematical perspective. In fact, you can reduce any **NP**-complete problem to any other **NP**-complete problem such that the capability to solve the second implies the capability to solve the first. Remember that **NP** contains decision problems, not search problems. You can efficiently transform an algorithm able to solve a search problem into an algorithm able to solve the corresponding decision problem, though the converse direction is not always possible. Fortunately, this is the case for **NP**-complete problems, which explains why people often mix up the two.
