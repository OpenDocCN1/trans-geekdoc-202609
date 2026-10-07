Axiomatics, the Social Sciences, and the Gödel Phenomenon: A Toolkit 83

+   • We use a binary coding for the Turing machines, which is also monotonic on the length of their tables, linearly arranged, that is, a 3-line table s1, s2, s3, becomes the line s1s2s3.
We call such monotonic codings *standard codings*.

+   • We consider the set of all Boolean expressions in cnf, including those that are unsatisfiable, or totally false. We give it the usual coding, which is one-to-one and onto ω.

+   • Consider the poly Turing machine V(x, s), where V(x, s) = 1 if and only the line of truth values s satisfies the Boolean cnf expression x, and V(x, s) = 0 if s does not satisfy x.

+   • Consider the enumeration of the BGS (see Baker *et al.*, 1975) machines, P0, P1, P2,...¹¹⁸

We start from x, the binary code for a Boolean expression in cnf form:

+   • Consider x to P0, P1, P2,... up to the first Pj so that Pj(x) = sj and sj satisfies x (that is, for the verifying machine V(x, sj) = 1).

+   • Notice that there is a bound ≤ j = f⁻¹(x).

This requires some elaboration. Eventually a poly machine (in the BGS sequence) will produce a satisfying line for x as its output given as input. The upper bound for the machine with that ability is given by the first BGS index that the code for x is smaller than the value at index of the counterexample function.
That means: we arrive at a machine Mn, which outputs a correct line up to x as an input, and then begins to output wrong solutions.

+   • Alternatively check for V(x,0), V(x,1)... up to — if it happens — some s so that V(x,s) = 1; or,

¹⁷Conjunctive normal form.
¹⁸Have in mind that the BGS machine set is a set of time-polynomial Turing machines, which includes algorithms that mimic all time-polynomial Turing machines. See above and check (see Baker *et al.*, 1975).