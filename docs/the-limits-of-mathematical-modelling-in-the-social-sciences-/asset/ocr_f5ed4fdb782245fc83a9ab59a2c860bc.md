Axiomatics, the Social Sciences, and the Gödel Phenomenon: A Toolkit

# 2. Axiom systems: mathematics

We will restrict here our attention to two axiom systems for mathematics, Peano Arithmetic (PA) and Zermelo-Fraenkel set theory with the Axiom of Choice (ZFC). PA will be mainly used when we are dealing with the cost of computation and its consequences; and we will require ZFC in order to axiomatize the kind of mathematics that is used by professional mathematicians. However our arguments are valid for recursive extensions of these theories, that is, extensions whose theorems are also recursively enumerable.

Axiomatic systems like Zermelo-Fraenkel set theory, or Peano arithmetic, can be formulated as computer programs that list (ie., recursively enumerate) all theorems of the theory. These theories are machines that produce the sentences which are valid in the theory. So, suppose that $S$ is one such axiomatic theory. Suppose that $S$ is able to talk about computer programs, that is, we can talk about partial recursive functions in the language of $S$. We are interested in the recursive functions that are total, that is, which are defined for all natural numbers 0, 1, 2,. . .

Then we listing (i.e., we try to recursively enumerate) all $S$-total recursive functions, that is, recursive functions that $S$ can recognize as total, or better, which $S$ can prove to be total. This is the starting point of our argument, which stems from Kleene (1936):

+   - We need two preliminary suppositions: axiomatic system $S$ is supposed to be consistent (i.e., it doesn't prove a contradiction such as, e.g., $0 \neq 0$). Also, $S$ must be sound, that is, $S$ doesn't prove sentences that are false in the standard interpretation for arithmetic.
- Start the program that lists the theorems of $S$.
- Pick those theorems that say: "function $f$ is total and computable."
- Out of that, we can build another list, $f_0, f_1, f_2, \dots$, of $S$-total computable functions (functions that are proved as such in $S$),