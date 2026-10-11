
# 2.2.3 Steepest Descent Method

It is known from computer mathematics that methods of this type have a significant disadvantage: sometimes local minima and plateaus can occur when searching for a solution, which are generally difficult to recognize and require very complex calculations. Once in a local minimum, the steepest descent method will stop there without finding a solution. Once on a plateau, the method results in aimless random walks across the plateau.

The method of steepest descent works well when the estimator is unimodal, i.e., when it has a single global minimum and no plateau. But in order to choose a unimodal scoring function, one needs to know the properties of the search space fully, and they are usually unknown.

Consider an example. In a game of eight, we take the evaluation function `F`—this is the number of stones that are not in place. As a result, the search graph for this game looks like this (Fig. 19).

![](Images/image00341.jpeg)

**Figure 19.** Scoring function `F`: Number of stones out of place

Here the nodes of the graph represent the states of the database and the numbers in the nodes are the value of the evaluation function in the given state.

In this case, the rating function proved to be very successful—the fastest search method quickly found a solution. But there is an element of luck here: from a node with a score of 3, the search went north instead of west, simply because the north rule ended up before the west rule in our rules list.

# 2.2.4 Reverse Search (Backtracking)

Irreversible search implies that if an inappropriate rule is applied, the solution will either become fundamentally impossible, or the search process will be significantly slowed down. You can base the search algorithm on the following idea: If it is clear from the current state of the database that if you continue with the solution you have started, either no solution can be found or this search promises to take too long, then you can try to go back and try another way.

A search strategy that involves backtracking and applying a different rule when applying the rule is inappropriate is called backtracking [[41]](#part0005.xhtml#_ftn41).

Consider the backtracking procedure (Algorithm 5).

**Algorithm 5.** Backtracking search method for the product system.

```
proc Backtracking(d, R, t)
    if t(d) then return (OK) end if
    if Deadend(d) then return (fail) end if
    R' := SelectAll(d, R)
    für r ∈ R' tun
        if Backtracking(rf(d), R, t) = OK then return (OK) end if
    end for
    return (error)
end process
```

The idea of the backtracking search method is very simple and consists of the following. If any of the termination conditions are met, work must stop and the result returned. Otherwise, you should determine the set of rules in effect in that state (conflict set, see Section 0) using the `SelectAll` function. Next, the same backtracked search procedure is recursively referred to in a loop according to the applicable rules, but using the state obtained after applying the selected rule as the database state.

It is advisable to include the `Deadend` function in this process—breaking up "dead" paths (dead ends), otherwise the program may loop.

The `Deadend` procedure can check a variety of conditions, for example:

- Correspondence of the current state of the database `D` with that previously created;
- Search depth limit, etc.

An example of a reverse search for the wolf, goat, and cabbage problem is shown in Fig. 20. In this figure, the nodes from which the return is made are marked in gray because they are identical to the nodes already built. We should also mention node `0001` separately; this is a dead end node—it is impossible to continue the search from there. Fortunately, there is no need to continue, because at this point, the algorithm finds the destination node `1111`.

![](Images/image00342.jpeg)

**Figure 20.** Tracing for the wolf, goat and cabbage problem

Here the `Deadend` function is used to check if the new state of the database matches what was previously created on this path.

Various modifications of reverse search are known. For example, if not all are saved during the search, but only the most important states of the database, and the return is not one step, but several steps back to the last saved state.

When searching with backtracking, the tree is traversed and not the entire tree is saved, only the currently constructed path in this tree. Moving down the tree corresponds to recursive calls. Upward movements correspond to yields. On Fig. 21 shows a fragment of a search tree with returns for the knight move problem.

![](Images/image00343.jpeg)

**Figure 21.** Fragment of a backtracking search tree for the knight's move problem

We place the knight on any square of the board. In this case the angular field `a1` is taken as the first field. We alternately arrange the knight on different squares, looking for one where the horse was not before. If there are no such fields at all, we return to the previous field and so on.

Note that the actual structure of the rules involves storing information about the squares of the board that the knight has already visited (see Section 0). Therefore, here in the `Deadend` function there is no need to check whether the new state of the database matches what was previously created along this path. At the expense of storing some additional information in the database, the computational load of the backtracking procedure can be reduced.

# 2.2.5 Graph Search

Graph search belongs to the group of informed strategies that store all available previously obtained information. A so-called search graph is created for this purpose.

The search graph is a directed graph `G(V,E)` in which the set of vertices `V` is the set [[42]](#part0005.xhtml#_ftn42) of database states and the set of arcs `E` is the set of rule applications.

This graph has an initial node `d0` and a set (possibly empty) of terminal nodes `T = { d ∈ D | t(d) }`. The elements of the set of terminal nodes are denoted by `dt`, `dt ∈ T`. An arc from node `d1` to node `d2` is executed if and only if there is a rule that is applicable in state `d1` and, because of its application, transitions the basis to state `d2`.

```
d1 → d2 ∈ E ⇔ ∃ r ∈ R ( rp(d1) & rf(d1) = d2 )
```

In the general case, the search graph can contain cycles, loops, multiple arcs. It may not be related etc.

To search in a graph, the following two main methods are used, which are specified in the algorithms: Algorithm 6 and Algorithm 7.

**Algorithm 6.** The main search method in the graph.

```
proc GraphSearch(d, R, t)
    O := {d} { list of "open" nodes }
    C := ∅ { list of "closed" nodes }
    while ¬t(d) do
        d := select(O)
        if d = zero then return (fail) end if
        Open(d, R)
    end while
    return (OK)
end proc
```

**Algorithm 7.** Node Disclosure Procedures.

```
proc Open(d, R)
    for r ∈ R do
        if rp(d) then
            if rf(d) ∉ O & rf(d) ∉ C then
                O := O + rf(d)
            end if
        end if
    end for
    O := O - {d}
    C := C + {d}
end proc
```

Here the `+` sign means adding an item to the list, and the `-` sign means removing an item from the list.
