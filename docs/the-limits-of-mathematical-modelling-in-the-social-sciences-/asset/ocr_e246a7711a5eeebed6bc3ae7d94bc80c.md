# The Limits of Mathematical Modeling in the Social Sciences

quoted after they were published; however, their applications were until recently restricted to computer science, to set computational bounds for techniques onwards in algebraic computation.

From here onward, we suppose that our formal constructions are made within a first-order axiomatic theory $T$, which can be thought to include Zermelo-Fraenkel (ZF) theory plus at least portion of the Axiom of Choice.

In our version, the Richardson functor starts out of a polynomial $p$ in $q$ indeterminates over the integers Z. Richardson tells us how to explicitly and algorithmically construct two expressions of that $p$:

+   First, an expression for a $q$-variable function $f(p)$, which includes polynomial terms, sine functions, and the number $\pi$ satisfies the following conditions:

1. The Diophantine equation $p=0$ has no solutions over the integers if and only if, for all values of its variables, $f(p) > 1$.
2. $p=0$ has a solution over the integers if and only if $f(p)$ dips beyond 1 and has zero values.

+   Second, an expression for a 1-variable function, which can be explicit constructed with elementary functions and which has a similar behavior according to the existence of roots in $p=0$.

The idea in Richardson's transform is that there is a kind of strip of finite width, which is never crossed by the values of $f(p)$ if the Diophantine equation $p=0$ has no solutions. If it does solutions, that strip will be crossed at points depending on the Diophantine roots. If we now add an expression for the absolute value function $|\dots|$ to our language, we can obtain a new function $c(f)$ with the following behavior:

+   $c(f)=0$ if and only if $p=0$ has no solutions as a Diophantine equation.
$c(f)>0$ somewhere if and only if $p=0$ has integer solutions.

Richardson's interest seems to have been restricted to the construction of a few unsolvable problems in analysis. However, we realized that his two maps amounted to a true-blue functor from