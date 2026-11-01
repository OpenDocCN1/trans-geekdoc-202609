
$\\begin{array}{r} \\chi \\\\ \\\\ \\end{array}\\,\\,\\begin{matrix} = \\\\ \\\\ \\end{matrix}\\,\\,\\begin{array}{l} {\\text{\\{}Axle\_{F}\\text{,~}Axle\_{B}\\text{,~}Wheel\_{RF}\\text{,~}Wheel\_{LF}\\text{,~}Wheel\_{RB}\\text{,~}Wheel\_{LB}\\text{,~}Nuts\_{RF}\\text{,}} \\\\ {Nuts\_{LF}\\text{,~}Nuts\_{RB}\\text{,~}Nuts\_{LB}\\text{,~}Cap\_{RF}\\text{,~}Cap\_{LF}\\text{,~}Cap\_{RB}\\text{,~}Cap\_{LB}\\text{,~}Inspect\\text{\\}}\\text{.}} \\\\ \\end{array}$

Next, we represent precedence constraints between individual tasks. Whenever a task `T1` must occur before task `T2`, and task `T1` takes duration `d1` to complete, we add an arithmetic constraint of the form

`T[1] + d[1] ≤ T[2]` :

<p class="sidebar">Precedence constraint</p>

In our example, the axles have to be in place before the wheels are put on, and it takes 10 minutes to install an axle, so we write

$\\begin{array}{l} {Axle\_{F}\\text{~+~10~} \\leq \\ Wheel\_{RF}\\text{;~}\\,\\,\\, Axle\_{F}\\text{~+~10~} \\leq \\ Wheel\_{LF}\\text{;}} \\\\ {Axle\_{B}\\text{~+~10~} \\leq \\ Wheel\_{RB}\\text{;~}\\,\\, Axle\_{B}\\text{~+~10~} \\leq \\ Wheel\_{LB}\\ \\text{.}} \\\\ \\end{array}$

Next we say that for each wheel, we must affix the wheel (which takes 1 minute), then tighten the nuts (2 minutes), and finally attach the hubcap (1 minute, but not represented yet):

$\\begin{array}{l} {Wheel\_{RF}\\text{~+}\\,\\text{1~} \\leq \\ Nuts\_{RF}\\text{;~}Nuts\_{RF}\\text{~+}\\,\\text{2~} \\leq \\ Cap\_{RF}\\text{;}} \\\\ {Wheel\_{LF}\\text{~+}\\,\\text{1~} \\leq \\ Nuts\_{LF}\\text{;~}Nuts\_{LF}\\text{~+}\\,\\text{2~} \\leq \\ Cap\_{LF}\\text{;}} \\\\ {Wheel\_{RB}\\,\\text{+}\\,\\text{1~} \\leq \\ Nuts\_{RB}\\text{;~}Nuts\_{RB}\\,\\,\\text{+}\\,\\text{2~} \\leq \\ Cap\_{RB}\\text{;}} \\\\ {Wheel\_{LB}\\,\\,\\text{+}\\,\\text{1~} \\leq \\ Nuts\_{LB}\\text{;~}Nuts\_{LB}\\,\\,\\text{+}\\,\\text{2~} \\leq \\ Cap\_{LB}\\ \\text{.}} \\\\ \\end{array}$

Suppose we have four workers to install wheels, but they have to share one tool that helps put the axle in place. We need a disjunctive constraint to say that `AxleF` and `AxleB` must not overlap in time; either one comes first or the other does:

`(Axle[F] + 10 ≤ Axle[B]) or (Axle[B] + 10 ≤ Axle[F])`.

<p class="sidebar">Disjunctive constraint</p>

This looks like a more complicated constraint, combining arithmetic and logic. But it still reduces to a set of pairs of values that `AxleF` and `AxleB` can take on.

We also need to assert that the inspection comes last and takes 3 minutes. For every variable except `Inspect` we add a constraint of the form `X + dX ≤ Inspect`. Finally, suppose there is a requirement to get the whole assembly done in 30 minutes. We can achieve that by limiting the domain of all variables:

`D[i] = {0,1,2,3,…,30}`.

This particular problem is trivial to solve, but CSPs have been successfully applied to jobshop scheduling problems like this with thousands of variables.

## 5.1.3 Variations on the CSP formalism

The simplest kind of CSP involves variables that have discrete, finite domains. Map-coloring problems and scheduling with time limits are both of this kind. The 8-queens problem ([Figure 4.3](#Chapter04-01.xhtml#fig4-3)) can also be viewed as a finite-domain CSP, where the variables `Q1,...,Q8` correspond to the queens in columns 1 to 8, and the domain of each variable specifies the possible row numbers for the queen in that column, `Di = {1,2,3,4,5,6,7,8}`. The constraints say that no two queens can be in the same row or diagonal.

<p class="sidebar">Discrete domain</p> <p class="sidebar">Finite domain</p>

A discrete domain can be infinite, such as the set of integers or strings. (If we didn’t put a deadline on the job-scheduling problem, there would be an infinite number of start times for each variable.) With infinite domains, we must use implicit constraints like `T1 + d1 ≤ T2` rather than explicit tuples of values. Special solution algorithms (which we do not discuss here) exist for linear constraints on integer variables—that is, constraints, such as the one just given, in which each variable appears only in linear form. It can be shown that no algorithm exists for solving general nonlinear constraints on integer variables—the problem is undecidable.

<p class="sidebar">Infinite</p> <p class="sidebar">Linear constraints</p> <p class="sidebar">Nonlinear constraints</p> <p class="sidebar">Continuous domains</p>

Constraint satisfaction problems with continuous domains are common in the real world and are widely studied in the field of operations research. For example, the scheduling of experiments on the Hubble Space Telescope requires very precise timing of observations; the start and finish of each observation and maneuver are continuous-valued variables that must obey a variety of astronomical, precedence, and power constraints. The best-known category of continuous-domain CSPs is that of linear programming problems, where constraints must be linear equalities or inequalities. Linear programming problems can be solved in time polynomial in the number of variables. Problems with different types of constraints and objective functions have also been studied—quadratic programming, second-order conic programming, and so on. These problems constitute an important area of applied mathematics.

In addition to examining the types of variables that can appear in CSPs, it is useful to look at the types of constraints. The simplest type is the unary constraint, which restricts the value of a single variable. For example, in the map-coloring problem it could be the case that South Australians won’t tolerate the color green; we can express that with the unary constraint `〈(SA), SA ≠ green〉`. (The initial specification of the domain of a variable can also be seen as a unary constraint.)

<p class="sidebar">Unary constraint</p>

A binary constraint relates two variables. For example, `SA ≠ NSW` is a binary constraint. A binary CSP is one with only unary and binary constraints; it can be represented as a constraint graph, as in [Figure 5.1(b)](#Chapter05-01.xhtml#fig5-1).

<p class="sidebar">Binary constraint</p> <p class="sidebar">Binary CSP</p>

We can also define higher-order constraints. The ternary constraint `Between(X, Y, Z)`, for example, can be defined as `〈(X, Y, Z), X < Y < Z or X > Y > Z〉`.

A constraint involving an arbitrary number of variables is called a global constraint. (The name is traditional but confusing because a global constraint need not involve all the variables in a problem). One of the most common global constraints is `Alldiff`, which says that all of the variables involved in the constraint must have different values. In Sudoku problems (see [Section 5.2.6](#Chapter05-02.xhtml#sec5-2-6)), all variables in a row, column, or 3 × 3 box must satisfy an `Alldiff` constraint.

<p class="sidebar">Global constraint</p>

Another example is provided by cryptarithmetic puzzles ([Figure 5.2(a)](#Chapter05-01.xhtml#fig5-2)). Each letter in a cryptarithmetic puzzle represents a different digit. For the case in [Figure 5.2(a)](#Chapter05-01.xhtml#fig5-2), this would be represented as the global constraint `Alldiff (F, T, U, W, R, O)`. The addition constraints on the four columns of the puzzle can be written as the following n-ary constraints:

Description
