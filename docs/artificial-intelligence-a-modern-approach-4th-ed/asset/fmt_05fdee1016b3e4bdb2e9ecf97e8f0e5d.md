
Backward chaining is a kind of AND/OR search—the OR part because the `goal` query can be proved by any rule in the knowledge base, and the AND part because all the conjuncts in the `lhs` of a clause must be proved. `FOL-BC-OR` works by fetching all clauses that might unify with the `goal`, standardizing the variables in the clause to be brand-new variables, and then, if the `rhs` of the clause does indeed unify with the `goal`, proving every conjunct in the `lhs`, using `FOL-BC-AND`. That function works by proving each of the conjuncts in turn, keeping track of the accumulated substitution as it goes. [Figure 9.7](#Chapter09-04.xhtml#fig9-7) is the proof tree for deriving `Criminal(West)` from sentences (9.3) through (9.10).

Description

The horizontal axis is labeled Number of trials and ranges from 0 to 100 in increments of 20 units. The vertical axis is labeled utility estimates and ranges from 0.6 to 2.2 in increments of 0.2 units. The graph consists of five curves. All the curves start at (10, 1.95), and drops linearly downward. The solid curve labeled (3, 3) deviates to a horizontal path at (12, 1) and ends at (100, 1). The dashed curve labeled (3, 2) deviates to a horizontal path at (12, 0.96) and ends at (100, 0.96). The dashed curve labeled (2,1) deviates to a horizontal path at (12, 0.9) and ends at (100, 0.9). The dashed curve labeled (1, 3) deviates to a horizontal path at (15, 0.83) and ends at (100, 0.83). The dashed (1, 1) curve deviates to a horizontal path at (15, 0.8) and ends at (100, 0.8). Data are approximated.

×![](images/Fig-135.jpg)

Figure 9.7 Proof tree constructed by backward chaining to prove that West is a criminal. The tree should be read depth first, left to right. To prove `Criminal(West)`, we have to prove the four conjuncts below it. Some of these are in the knowledge base, and others require further backward chaining. Bindings for each successful unification are shown next to the corresponding subgoal. Note that once one subgoal in a conjunction succeeds, its substitution is applied to subsequent subgoals. Thus, by the time `FOL-BC-ASK` gets to the last conjunct, originally `Hostile(z)`, `z` is already bound to `Nono`.

Backward chaining, as we have written it, is clearly a depth-first search algorithm. This means that its space requirements are linear in the size of the proof. It also means that backward chaining (unlike forward chaining) suffers from problems with repeated states and incompleteness. Despite these limitations, backward chaining has proven to be popular and effective in logic programming languages.

## 9.4.2 Logic programming

Logic programming is a technology that comes close to embodying the declarative ideal described in [Chapter 7](#Chapter07-00.xhtml): that systems should be constructed by expressing knowledge in a formal language and that problems should be solved by running inference processes on that knowledge. The ideal is summed up in Robert Kowalski’s equation,

`Algorithm = Logic + Control`.

Prolog is the most widely used logic programming language. It is used primarily as a rapid prototyping language and for symbol-manipulation tasks such as writing compilers (Van Roy, 1990) and parsing natural language (Pereira and Warren, 1980). Many expert systems have been written in Prolog for legal, medical, financial, and other domains.

Prolog

Prolog programs are sets of definite clauses written in a notation somewhat different from standard first-order logic. Prolog uses uppercase letters for variables and lowercase for constants—the opposite of our convention for logic. Commas separate conjuncts in a clause, and the clause is written “backwards” from what we are used to; instead of `A ∧ B ⇒ C` in Prolog we have `C :- A, B`. Here is a typical example:

```
criminal(X) :- american(X), weapon(Y), sells(X,Y,Z), hostile(Z).
```

In Prolog the notation `[E|L]` denotes a list whose first element is `E` and whose rest is `L`. Here is a Prolog program for `append(X,Y,Z)`, which succeeds if list `Z` is the result of appending lists `X` and `Y`:

```
append([], Y, Y).
append([A|X], Y, [A|Z]) :- append(X, Y, Z).
```

In English, we can read these clauses as (1) appending the empty list and the list `Y` produces the same list `Y`, and (2) `[A|Z]` is the result of appending `[A|X]` and `Y`, provided that `Z` is the result of appending `X` and `Y`. In most high-level languages we can write a similar recursive function that describes how to append two lists. The Prolog definition is actually more powerful, however, because it describes a relation that holds among three arguments, rather than a function computed from two arguments. For example, we can ask the query `append(X,Y,[1,2,3])`: what two lists can be appended to give `[1,2,3]`? Prolog gives us back the solutions

```
X = []
X = [1]
X = [1,2]
X = [1,2,3]
```

```
Y = [1,2,3];
Y = [2,3];
Y = [3];
Y = []
```

The execution of Prolog programs is done through depth-first backward chaining, where clauses are tried in the order in which they are written in the knowledge base. Prolog’s design represents a compromise between declarativeness and execution efficiency. Some aspects of Prolog fall outside standard logical inference:

• Prolog uses the database semantics of [Section 8.2.8](#Chapter08-02.xhtml#sec8-2-8) rather than first-order semantics, and this is apparent in its treatment of equality and negation (see [Section 9.4.4](#Chapter09-04.xhtml#sec9-4-4)).

• There is a set of built-in functions for arithmetic. Literals using these function symbols are “proved” by executing code rather than doing further inference. For example, the goal `X is 4+3` succeeds with `X` bound to `7`. On the other hand, the goal `5 is X+Y` fails, because the built-in functions do not do arbitrary equation solving.

• There are built-in predicates that have side effects when executed. These include inputoutput predicates and the `assert/retract` predicates for modifying the knowledge base. Such predicates have no counterpart in logic and can produce confusing results— for example, if facts are asserted in a branch of the proof tree that eventually fails.

• The occur check is omitted from Prolog’s unification algorithm. This means that some unsound inferences can be made; these are almost never a problem in practice.

• Prolog uses depth-first backward-chaining search with no checks for infinite recursion. This makes for a usable programming language that is very fast when used properly, but it means that some programs that look like valid logic will fail to terminate.

## 9.4.3 Redundant inference and infinite loops

We now turn to the Achilles heel of Prolog: the mismatch between depth-first search and search trees that include repeated states and infinite paths. Consider the following logic program that decides if a path exists between two points on a directed graph:

```
path(X, Z) :- link(X, Z).
path(X, Z) :- path(X,Y), link(Y, Z).
```

A simple three-node graph, described by the facts `link(a,b)` and `link(b,c)`, is shown in [Figure 9.8(a)](#Chapter09-04.xhtml#fig9-8). With this program, the query `path(a,c)` generates the proof tree shown in [Figure 9.9(a)](#Chapter09-04.xhtml#fig9-9). On the other hand, if we put the two clauses in the order

×![](images/Fig-136.jpg)

Figure 9.8(a) Finding a path from A to C can lead Prolog into an infinite loop. (b) A graph in which each node is connected to two random successors in the next layer. Finding a path from A1 to J4 requires 877 inferences.

Description
