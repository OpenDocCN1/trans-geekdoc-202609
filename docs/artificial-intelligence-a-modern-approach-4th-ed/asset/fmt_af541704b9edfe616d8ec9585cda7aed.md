
Of course, Sudoku would soon lose its appeal if every puzzle could be solved by a mechanical application of `AC-3`, and indeed `AC-3` works only for the easiest Sudoku puzzles. Slightly harder ones can be solved by `PC-2`, but at a greater computational cost: there are 255,960 different path constraints to consider in a Sudoku puzzle. To solve the hardest puzzles and to make efficient progress, we will have to be more clever.

Indeed, the appeal of Sudoku puzzles for the human solver is the need to be resourceful in applying more complex inference strategies. Aficionados give them colorful names, such as “naked triples.” That strategy works as follows: in any unit (row, column or box), find three squares that each have a domain that contains the same three numbers or a subset of those numbers. For example, the three domains might be `{1,8}`, `{3,8}`, and `{1,3,8}`. From that we don’t know which square contains 1, 3, or 8, but we do know that the three numbers must be distributed among the three squares. Therefore we can remove 1, 3, and 8 from the domains of every other square in the unit.

It is interesting to note how far we can go without saying much that is specific to Sudoku. We do of course have to say that there are 81 variables, that their domains are the digits 1 to 9, and that there are 27 `Alldiff` constraints. But beyond that, all the strategies—arc consistency, path consistency, and so on—apply generally to all CSPs, not just to Sudoku problems. Even naked triples is really a strategy for enforcing consistency of `Alldiff` constraints and is not specific to Sudoku per se. This is the power of the CSP formalism: for each new problem area, we only need to define the problem in terms of constraints; then the general constraintsolving mechanisms can take over.

## 5.3 Backtracking Search for CSPs

Sometimes we can finish the constraint propagation process and still have variables with multiple possible values. In that case we have to search for a solution. In this section we cover backtracking search algorithms that work on partial assignments; in the next section we look at local search algorithms over complete assignments.

Consider how a standard depth-limited search (from [Chapter 3](#Chapter03-00.xhtml)) could solve CSPs. A state would be a partial assignment, and an action would extend the assignment, adding, say, `NSW = red` or `SA = blue` for the Australia map-coloring problem. For a CSP with `n` variables of domain size `d` we would end up with a search tree where all the complete assignments (and thus all the solutions) are leaf nodes at depth `n`. But notice that the branching factor at the top level would be `n d` because any of `d` values can be assigned to any of `n` variables. At the next level, the branching factor is `(n – 1)d`, and so on for `n` levels. So the tree has `n! · d^n` leaves, even though there are only `d^n` possible complete assignments!

We can get back that factor of `n!` by recognizing a crucial property of CSPs: commutativity. A problem is commutative if the order of application of any given set of actions does not matter. In CSPs, it makes no difference if we first assign `NSW = red` and then `SA = blue`,or the other way around. Therefore, we need only consider a single variable at each node in the search tree. At the root we might make a choice between `SA = red`, `SA = green`, and `SA = blue`, but we would never choose between `NSW = red` and `SA = blue`. With this restriction, the number of leaves is `d^n`, as we would hope. At each level of the tree we do have to choose which variable we will deal with, but we never have to backtrack over that choice.

<p class="sidebar">Commutativity</p>

[Figure 5.5](#Chapter05-03.xhtml#fig5-5) shows a backtracking search procedure for CSPs. It repeatedly chooses an unassigned variable, and then tries all values in the domain of that variable in turn, trying to extend each one into a solution via a recursive call. If the call succeeds, the solution is returned, and if it fails, the assignment is restored to the previous state, and we try the next value. If no value works then we return failure. Part of the search tree for the Australia problem is shown in [Figure 5.6](#Chapter05-03.xhtml#fig5-6), where we have assigned variables in the order `WA`, `NT`, `Q`,.... 

 Description 

Part (“a”): The blacks are in the following positions. King, e 8. Queen, g 2. Rooks, "a" 8 and h 8. Bishop, c 8. Knights d 4 and g 8. Pawns, "a" 7, b 7, c 7, d 6, e 5, f 7, g 7, and h 7. The whites are in the following positions. King, e 1. Queen, d 1. Rooks, "a" 1 and h 1. Bishop, c 4. Knight c3. Pawns, "a" 2, b 2, c 2, e 4, f 2, and h 2. Part (b): All the pieces are in the same positions as in part (“a”), except the white rook at h 1 moves to g 1.

×![](images/Fig-76.jpg)

Figure 5.5 A simple backtracking algorithm for constraint satisfaction problems. The algorithm is modeled on the recursive depth-first search of [Chapter 3](#Chapter03-00.xhtml). The functions `SELECT-UNASSIGNED-VARIABLE` and `ORDER-DOMAIN-VALUES` implement the generalpurpose heuristics discussed in [Section 5.3.1](#Chapter05-03.xhtml#sec5-3-1). The `INFERENCE` function can optionally impose arc-, path-, or k-consistency, as desired. If a value choice leads to failure (noticed either by `INFERENCE` or by `BACKTRACK`), then value assignments (including those made by `INFERENCE`) are retracted and a new value is tried.

 Description 

The blacks are in the following positions. King, g 7. Bishop, "a" 2. Pawns, g 6, f 5, e 4, and b 4. The whites are in the following positions. King, d 2. Rook, h 2. Pawns, c 2 and b 3.

×![](images/Fig-77.jpg)

Figure 5.6 Part of the search tree for the map-coloring problem in [Figure 5.1](#Chapter05-01.xhtml#fig5-1).

Notice that `BACKTRACKING-SEARCH` keeps only a single representation of a state (assignment) and alters that representation rather than creating new ones (see [page 98](#Chapter03-04.xhtml#page_98)).

Whereas the uninformed search algorithms of [Chapter 3](#Chapter03-00.xhtml) could be improved only by supplying them with domain-specific heuristics, it turns out that backtracking search can be improved using domain-independent heuristics that take advantage of the factored representation of CSPs. In the following four sections we show how this is done:

•(5.3.1) Which variable should be assigned next (`SELECT-UNASSIGNED-VARIABLE`), and in what order should its values be tried (`ORDER-DOMAIN-VALUES`)?

•(5.3.2) What inferences should be performed at each step in the search (`INFERENCE`)?

•(5.3.3) Can we `BACKTRACK` more than one step when appropriate?

•(5.3.4) Can we save and reuse partial results from the search?

### 5.3.1 Variable and value ordering

The backtracking algorithm contains the line

```
var ← SELECT-UNASSIGNED-VARIABLE(csp, assignment)
```

The simplest strategy for `SELECT-UNASSIGNED-VARIABLE` is static ordering: choose the variables in order, `{X1,X2,...}`. The next simplest is to choose randomly. Neither strategy is optimal. For example, after the assignments for `WA = red` and `NT = green` in [Figure 5.6](#Chapter05-03.xhtml#fig5-6), there is only one possible value for `SA`, so it makes sense to assign `SA = blue` next rather than assigning `Q`. in fact, after `SA` is assigned, the choices for `Q`, `NSW`, and `V` are all forced.

This intuitive idea—choosing the variable with the fewest “legal” values—is called the minimum-remaining-values (`MRV`) heuristic. It also has been called the “most constrained variable” or “fail-first” heuristic, the latter because it picks a variable that is most likely to cause a failure soon, thereby pruning the search tree. If some variable `X` has no legal values left, the `MRV` heuristic will select `X` and failure will be detected immediately—avoiding pointless searches through other variables. The `MRV` heuristic usually performs better than a random or static ordering, sometimes by orders of magnitude, although the results vary depending on the problem.

<p class="sidebar">Minimum-remaining-values</p>
