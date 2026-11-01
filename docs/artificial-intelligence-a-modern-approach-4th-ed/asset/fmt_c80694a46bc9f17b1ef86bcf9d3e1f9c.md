
Up and down triangles represent `MAX` and `MIN` nodes, respectively. The first level of the game tree is labeled `MAX` and the `MAX` node is labeled "`A`". Node "`A`" is marked 3 and has three child nodes. The second level is labeled `MIN` and the three child nodes are `MIN` nodes that are labeled `B`, `C`, and `D`. An arrow labeled "`a₁`" from node "`a`" points to node `B`. Paths labeled "`a₂`" and "`a₃`" from node "`a`" connect to nodes `C` and `D`, respectively. The three nodes each have three child nodes that are `MAX` nodes. Node `B` is marked 3, `C` is marked 2, and `D` is marked 2. The three child nodes of `B` are marked 3, 12, and 8. Paths labeled `b₁`, `b₂`, and `b₃` connect node `B` to nodes 3, 12, and 8, respectively. The three child nodes of `C` are marked 2, 4, and 6. Paths labeled `c₁`, `c₂`, and `c₃` connect node `C` to nodes 2, 4, and 6, respectively. The three child nodes of `D` are marked 14, 5, and 2. Paths labeled `d₁`, `d₂`, and `d₃` connect node `D` to nodes 14, 5, and 2, respectively.

×![](images/Fig-73.jpg)

Figure 5.2 (a) A cryptarithmetic problem. Each letter stands for a distinct digit; the aim is to find a substitution of digits for letters such that the resulting sum is arithmetically correct, with the added restriction that no leading zeroes are allowed. (b) The constraint hypergraph for the cryptarithmetic problem, showing the `Alldiff` constraint (square box at the top) as well as the column addition constraints (four square boxes in the middle). The variables `C1`, `C2`, and `C3` represent the carry digits for the three columns from right to left.

Cryptarithmetic

$\\begin{array}{l} {O\\,\\text{+}\\, O\\text{~=~}R\\,\\text{+}\\,\\text{10} \\cdot C\_{\\text{1}}} \\\\ {C\_{1}\\,\\text{+}\\, W\\text{~+}\\, W\\text{~=~}U\\text{~+10} \\cdot C\_{\\text{2}}} \\\\ {C\_{\\text{2}}\\text{+}\\, T\\text{~+}\\, T\\text{~=~}O\\,\\text{+}\\,\\text{10} \\cdot C\_{\\text{3}}} \\\\ {C\_{3}\\text{~=~}F\\ \\text{,}} \\\\ \\end{array}$

where `C1`, `C2`, and `C3` are auxiliary variables representing the digit carried over into the tens, hundreds, or thousands column. These constraints can be represented in a constraint hypergraph, such as the one shown in [Figure 5.2(b)](#Chapter05-01.xhtml#fig5-2). A hypergraph consists of ordinary nodes (the circles in the figure) and hypernodes (the squares), which represent n\-ary constraints—constraints involving n variables.

Constraint hypergraph

Alternatively, as Exercise 5.NARY asks you to prove, every finite-domain constraint can be reduced to a set of binary constraints if enough auxiliary variables are introduced. This means that we could transform any `CSP` into one with only binary constraints—which certainly makes the life of the algorithm designer simpler. Another way to convert an n\-ary `CSP` to a binary one is the dual graph transformation: create a new graph in which there will be one variable for each constraint in the original graph, and one binary constraint for each pair of constraints in the original graph that share variables.

Dual graph

For example, consider a `CSP` with the variables `χ = {X, Y, Z}`, each with the domain `{1,2,3,4,5}`, and with the two constraints `C1: 〈(X ,Y, Z), X + Y = Z〉` and `C2: 〈(X, Y), X +1 = Y〉`. Then the dual graph would have the variables `χ = {C1, C2}`, where the domain of the `C1` variable in the dual graph is the set of `{(xi, yj, zk)}` tuples from the `C1` constraint in the original problem, and similarly the domain of `C2` is the set of `{(xi, yj)}` tuples. The dual graph has the binary constraint `〈(C1, C2), R1〉`, where `R1` is a new relation that defines the constraint between `C1` and `C2`; in this case it would be `R1 = {((1,2,3), (1,2)), ((2,3,5), (2,3))}`.

There are however two reasons why we might prefer a global constraint such as `Alldiff` rather than a set of binary constraints. First, it is easier and less error-prone to write the problem description using `Alldiff`. Second, it is possible to design special-purpose inference algorithms for global constraints that are more efficient than operating with primitive constraints. We describe these inference algorithms in [Section 5.2.5](#Chapter05-02.xhtml#sec5-2-5).

The constraints we have described so far have all been absolute constraints, violation of which rules out a potential solution. Many real-world `CSP`s include preference constraints indicating which solutions are preferred. For example, in a university class-scheduling problem there are absolute constraints that no professor can teach two classes at the same time. But we also may allow preference constraints: Prof. R might prefer teaching in the morning, whereas Prof. N prefers teaching in the afternoon. A schedule that has Prof. R teaching at 2 p.m. would still be an allowable solution (unless Prof. R happens to be the department chair) but would not be an optimal one.

Preference constraints

Preference constraints can often be encoded as costs on individual variable assignments—for example, assigning an afternoon slot for Prof. R costs 2 points against the overall objective function, whereas a morning slot costs 1. With this formulation, `CSP`s with preferences can be solved with optimization search methods, either path-based or local. We call such a problem a constrained optimization problem, or `COP`. Linear programs are one class of `COP`s.

Constrained optimization problem

## 5.2 Constraint Propagation: Inference in CSPs

An atomic state-space search algorithm makes progress in only one way: by expanding a node to visit the successors. A `CSP` algorithm has choices. It can generate successors by choosing a new variable assignment, or it can do a specific type of inference called constraint propagation: using the constraints to reduce the number of legal values for a variable, which in turn can reduce the legal values for another variable, and so on. The idea is that this will leave fewer choices to consider when we make the next choice of a variable assignment. Constraint propagation may be intertwined with search, or it may be done as a preprocessing step, before search starts. Sometimes this preprocessing can solve the whole problem, so no search is required at all.

Constraint propagation

The key idea is local consistency. If we treat each variable as a node in a graph (see [Figure 5.1(b)](#Chapter05-01.xhtml#fig5-1)) and each binary constraint as an edge, then the process of enforcing local consistency in each part of the graph causes inconsistent values to be eliminated throughout the graph. There are different types of local consistency, which we now cover in turn.

Local consistency

## 5.2.1 Node consistency

A single variable (corresponding to a node in the `CSP` graph) is node-consistent if all the values in the variable’s domain satisfy the variable’s unary constraints. For example, in the variant of the Australia map-coloring problem ([Figure 5.1](#Chapter05-01.xhtml#fig5-1)) where South Australians dislike green, the variable `SA` starts with domain `{red,green,blue}`, and we can make it node consistent by eliminating green, leaving `SA` with the reduced domain `{red, blue}`. We say that a graph is node-consistent if every variable in the graph is node-consistent.

Node consistency

It is easy to eliminate all the unary constraints in a `CSP` by reducing the domain of variables with unary constraints at the start of the solving process. As mentioned earlier, it is also possible to transform all n\-ary constraints into binary ones. Because of this, some `CSP` solvers work with only binary constraints, expecting the user to eliminate the other constraints ahead of time. We make that assumption for the rest of this chapter, except where noted.

## 5.2.2 Arc consistency
