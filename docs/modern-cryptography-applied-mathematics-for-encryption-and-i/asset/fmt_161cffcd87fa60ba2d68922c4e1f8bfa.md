
Designing an algorithm is a formal process that provides a systematic way of solving a problem. Therefore, it should be no surprise that there are systematic ways of designing algorithms. In this section we will examine a few of these methods.

The “divide-and-conquer” approach to algorithm design is a commonly used approach. In fact, it could be argued that it is the most commonly used approach. It works by recursively breaking down a problem into sub-problems of the same type until these sub-problems become simple enough to be solved directly. Once the sub-problems are solved, the solutions are combined to provide a solution to the original problem. In short, you keep subdividing the problem until you find manageable portions that you can solve, and after solving those smaller, more manageable portions, you combine those solutions to solve the original problem.

When you’re approaching difficult problems, such as the classic Tower of Hanoi puzzle, the divide-and-conquer method often offers the only workable way to find a solution. The divide-and-conquer method often leads to algorithms that are not only effective, but also efficient.

The efficiency of the divide-and-conquer method can be examined by considering the number of sub-problems being generated. If the work of splitting the problem and combining the partial solutions is proportional to the problem’s size n, then there are a finite number p of sub-problems of size ~ n/p at each stage. Furthermore, if the base cases require O (that is, constant-bounded) time, then the divide-and-conquer algorithm will have O(n log n) complexity. This is often used in sorting problems to reduce the complexity from O(n^2). An O of n log n is fairly good for most sorting algorithms.

In addition to allowing you to devise efficient algorithms for solving complex problems, the divide-and-conquer approach is well suited for execution in multi-processor machines. The sub-problems can be assigned to different processors to allow each processor to work on a different sub-problem. This leads to sub-problems being solved simultaneously, thus increasing the overall efficacy of the process.

The second method is the *greedy approach.* The textbook *An Introduction to Algorithms*, by Thomas Cormen, Charles Leiserson, Ronald Rivest, and Clifford Stein (MIT Press, 2009), defines *greedy algorithm*s as algorithms that select what appears to be the most optimal solution in a given situation. In other words, a solution is selected that is ideal for a specific situation, but it might not be the most effective solution for the broader class of problems. The greedy approach is used with optimization problems. To provide a precise description of the greedy paradigm, we must first consider a more detailed description of the environment in which most optimization problems occur. Most optimization problems include the following:

![image](Images/image00484.jpeg) A collection of candidates—a set, a list, an array, or another data structure. How the collection is stored in memory is irrelevant.

![image](Images/image00484.jpeg) A set of candidates that have previously been used.

![image](Images/image00484.jpeg) A predicate solution that is used to test whether or not a given set of candidates provides an efficient solution. This does not check to determine whether those candidates provide an optimal solution, just whether or not they provide a working solution.

![image](Images/image00484.jpeg) Another predicate solution (feasible) to test whether a set of candidates can be extended to a solution.

![image](Images/image00484.jpeg) A selection function, which chooses some candidate that has not yet been used.

![image](Images/image00484.jpeg) A function that assigns a value to a solution.

Essentially, an optimization problem involves finding a subset S from a collection of candidates C, where that subset satisfies some specified criteria. For example, the criteria may be “a solution such that the function is optimized by S.” Optimization may denote any number of factors, such as minimized or maximized. Greedy methods are distinguished by the fact that the selection function assigns a numerical value to each candidate C and chooses that candidate for which

`SELECT( C )` is largest

or

`SELECT( C )` is smallest

All greedy algorithms have this same general form. A greedy algorithm for a particular problem is specified by describing the predicates and the selection function. Consequently, greedy algorithms are often very easy to design for optimization problems.

The general form of a greedy algorithm is as follows:

function `select` (C : candidate_set) returncandidate;

function `solution` (S : candidate_set) returnboolean;

function `feasible` (S : candidate_set) returnboolean;

**Tip**

*An Introduction to Algorithms* is an excellent source for learning about algorithms. It is often used as a textbook in university courses. If you are looking for a thorough discussion of algorithms, I recommend this book.

##### P vs. NP

You have probably heard this issue bandied about quite a bit, even if you don’t have a rigorous mathematical background. It was even featured in an episode of the television drama *Elementary*. It involves a question that has significant implications for cryptography.

Many problems in mathematics are solvable via some *polynomial* equation, though not all problems are solvable in this fashion. Those that are not solvable are referred to as *NP*, or *not polynomial* (also known as *nondeterministic polynomial time* or *not solvable in polynomial time*). In complexity theory, *NP-complete* (NP-C) problems are the most difficult problems to solve because there are no polynomial equations for their solutions. That concept should be simple enough. *P* is *polynomial*, or more exactly, *problems solvable in polynomial time*. So what is the question that “P versus NP” addresses?

The question has to do with the fact that, to date, no one has proven that there is no polynomial solution for any NP-complete problem. If someone could provide a polynomial solution for *any* NP-complete problem, this would prove that *all* NP-complete problems *do* have a polynomial solution (in short, it would prove that there is no such thing as an NP-complete problem). In other words, as far as we know, there might be some polynomial time solution to these NP problems, but no one has proven that they cannot be solved in polynomial time.

**Tip**

When I say “proven” I mean provided with a mathematical proof.

There are essentially three classes of problems: *P* problems can be solved in polynomial time. *NP* problems cannot be solved in polynomial time, but they can be verified that a given solution is correct. *NP-C* problems simply cannot be addressed in any fashion in polynomial time.

One example of an NP-C problem is the subset sum problem, which can be summarized as follows: Given a finite set of integers, determine whether any non-empty subset of them sums to zero. A proposed answer is easy to verify for correctness; however, to date, no one has produced a faster way to solve the problem than simply to try each and every single possible subset. This is very inefficient.

At present, all known algorithms for NP-C problems require time that is super-polynomial in the input size. In other words, there is no polynomial solution for any NP-C problem. Therefore, to solve an NP-C problem, one of the following approaches is used:

![image](Images/image00484.jpeg) **Approximation** An algorithm is used that quickly finds a suboptimal solution that is within a certain known range of the optimal one. In other words, an approximate solution is found.

![image](Images/image00484.jpeg) **Probabilistic** An algorithm is used that provably yields good average runtime behavior for a given distribution of the problem instances.
