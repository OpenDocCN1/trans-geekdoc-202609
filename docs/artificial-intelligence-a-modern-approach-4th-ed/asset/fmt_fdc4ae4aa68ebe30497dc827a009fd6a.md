
## 9.2.1 Unification Algorithm

An algorithm for computing most general unifiers is shown in [Figure 9.1](#Chapter09-02.xhtml#fig9-1). The process is simple: recursively explore the two expressions simultaneously “side by side,” building up a unifier along the way, but failing if two corresponding points in the structures do not match. There is one expensive step: when matching a variable against a complex term, one must check whether the variable itself occurs inside the term; if it does, the match fails because no consistent unifier can be constructed. For example, `S(x)` can’t unify with `S(S(x))`. This so-called occur check makes the complexity of the entire algorithm quadratic in the size of the expressions being unified. Some systems, including many logic programming systems, simply omit the occur check and put the onus on the user to avoid making unsound inferences as a result. Other systems use more complex unification algorithms with lineartime complexity.

Description
A grid with four columns and three rows is shown. The columns are numbered 1 to 4 from left to right. The rows are labeled 1 to 3 from bottom to top. Each cell depicts a state. The actions inside each state are as follows. State (1, 1): Upward arrow. State (1, 2): Upward arrow. State (1, 3): Right-headed arrow. State (2, 1): left-headed arrow. State (2, 2): Highlighted in blue. State (2, 3): Right-headed arrow. State (3, 1): left-headed arrow and an upward arrow. State (3, 2): upward arrow. State (3, 3): Right-headed arrow. State (4, 1): left-headed arrow. State (4, 2): A block labeled negative 1. State (4, 3): A block labeled positive 1.

×![](images/Fig-129.jpg)

Figure 9.1 The unification algorithm. The arguments `x` and `y` can be any expression: a constant or variable, or a compound expression such as a complex sentence or term, or a list of expressions. The argument `θ` is a substitution, initially the empty substitution, but with `{var / val}` pairs added to it as we recurse through the inputs, comparing the expressions element by element. In a compound expression such as `F(A,B)`, `OP(x)` field picks out the function symbol `F` and `ARGS(x)` field picks out the argument list `(A, B)`.

*Occur check*

## 9.2.2 Storage and retrieval

Underlying the `TELL`, `ASK`, and `ASKVARS` functions used to inform and interrogate a knowledge base are the more primitive `STORE` and `FETCH` functions. `STORE(s)` stores a sentence `s` into the knowledge base and `FETCH(q)` returns all unifiers such that the query `q` unifies with some sentence in the knowledge base. The problem we used to illustrate unification—finding all facts that unify with `Knows(John, x)`—is an instance of `FETCH`ing.

The simplest way to implement `STORE` and `FETCH` is to keep all the facts in one long list and unify each query against every element of the list. Such a process is inefficient, but it works. The remainder of this section outlines ways to make retrieval more efficient.

We can make `FETCH` more efficient by ensuring that unifications are attempted only with sentences that have some chance of unifying. For example, there is no point in trying to unify `Knows(John, x)` with `Brother(Richard, John)`. We can avoid such unifications by indexing the facts in the knowledge base. A simple scheme called predicate indexing puts all the

*Indexing*
*Predicate indexing*

`Knows` facts in one bucket and all the `Brother` facts in another. The buckets can be stored in a hash table for efficient access.

Predicate indexing is useful when there are many predicate symbols but only a few clauses for each symbol. Sometimes, however, a predicate has many clauses. For example, suppose that the tax authorities want to keep track of who employs whom, using a predicate `Employs(x,y)`. This would be a very large bucket with perhaps millions of employers and tens of millions of employees. Answering a query such as `Employs(x, Richard)` with predicate indexing would require scanning the entire bucket.

For this particular query, it would help if facts were indexed both by predicate and by second argument, perhaps using a combined hash table key. Then we could simply construct the key from the query and retrieve exactly those facts that unify with the query. For other queries, such as `Employs(IBM, y)`, we would need to have indexed the facts by combining the predicate with the first argument. Therefore, facts can be stored under multiple index keys, rendering them instantly accessible to various queries that they might unify with.

Given a sentence to be stored, it is possible to construct indices for all possible queries that unify with it. For the fact `Employs(IBM, Richard)`, the queries are

$\\begin{array}{l} {Employs(IBM,Richard)} \\\\ {Employs(x,Richard)} \\\\ {Employs(IBM,y)} \\\\ {Employs(x,y)} \\\\ \\end{array}\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\begin{array}{l} \\text{Does~IBM~employ~Richard?} \\\\ \\text{Who~employs~Richard?} \\\\ \\text{Whom~does~IBM~employ?} \\\\ \\text{Who~employs~whom?} \\\\ \\end{array}$

*Subsumption lattice*

These queries form a subsumption lattice, as shown in [Figure 9.2(a)](#Chapter09-02.xhtml#fig9-2). The lattice has some

Description
The horizontal axis is labeled number of trials, and ranges from 0 to 100 in increments of 20 units. The vertical axis is labeled utility estimates and ranges from 0.5 to 1 in increments of 0.1 units. Five dashed curves are plotted on the graph. The first dashed curve labeled (3, 3) starts at (0, 1) and ends at (100, 1) with no significant change. The second curve labeled (3, 2) starts at (24, 0), rises vertically until (24, 0.95), then remains horizontally constant until (60, 0.95), then drops to a point (65, 0.93) and remains horizontally constant and ends at (100, 0.095). The third curve labeled (1, 3) starts at (0, 0.8), rises a little, and forms a small peak at (4, 0.86). The curve further drops to a point (5, 0.83) and then moves toward the right and ends at (100, 0.88). The fourth curve labeled (1, 1) starts at (0, 0.72), rises to form a peak at (3, 0.76). The curve further then moves without a significant change toward the right and ends at (100, 0.75). The fifth curve labeled (2, 1) starts at (17, 0), rises vertically until (17, 0.72), then rises toward the right and forms a peak at (18, 0.73). The curve then drops to a point (20, 0.69) and progresses linearly to end at (100, 0.72).

×![](images/Fig-130.jpg)

Figure 9.2(a) The subsumption lattice whose lowest node is `Employs(IBM, Richard)`. (b) The subsumption lattice for the sentence `Employs(John, John)`.

interesting properties. The child of any node in the lattice is obtained from its parent by a single substitution; and the “highest” common descendant of any two nodes is the result of applying their most general unifier. A sentence with repeated constants has a slightly different lattice, as shown in [Figure 9.2(b)](#Chapter09-02.xhtml#fig9-2). Although function symbols are not shown in the figure, they too can be incorporated into the lattice structure.

For predicates with a small number of arguments, it is a good tradeoff to create an index for every point in the subsumption lattice. That requires a little more work at storage time, but speeds up retrieval time. However, for a predicate with `n` arguments, the lattice contains `O(2n)` nodes. If function symbols are allowed, the number of nodes is also exponential in the size of the terms in the sentence to be stored. This can lead to a huge number of indices.
