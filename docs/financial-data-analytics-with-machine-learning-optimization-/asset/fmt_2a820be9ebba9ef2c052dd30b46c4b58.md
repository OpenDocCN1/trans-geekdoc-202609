
Notice that the max‐min inequality ([11.28](#c11.xhtml#c11-disp-0064)) holds for any function `f` regardless of whether `f` possesses any convexity or concavity property, and regardless of the topological structure of `X` and `Y`.

As a side discussion, von Neumann's minimax theorem is actually closely related to the vitally important concept of the `Nash equilibrium` in Economics, which is central to `noncooperative game theory`. Define a joint satisfaction function when playing a game between two players by `J(x, y)`, where `x ∈ X` and `y ∈ Y` are the respective strategies independently adopted by Players 1 and 2. We say a pair of strategies `(x*, y*) ∈ X × Y` is a `Nash equilibrium` if

```
max_{x∈X} J(x, y*) = J(x*, y*) and max_{y∈Y} J(x*, y) = J(x*, y*).
```

By definition, the Nash equilibrium represents a stable solution of the game in that if the players play in this way, either player has no incentive to unilaterally change to another strategy because each player's strategy is the best response to the strategy adopted by his opponent. A fundamental result in game theory states that Nash equilibrium always exists for every such game, under the following assumptions:

1. **(A1)** both `X` and `Y` are nonempty compact and convex subsets of finite dimensional spaces;

2. **(A2)** `J(x, y)` is concave in `x` for each `y ∈ Y`, and is also concave in `y` for each `x ∈ X`;

3. **(A3)** `J(x, y)` is jointly continuous.

To establish its validity, the following argument is essentially the same as discussed above for von Neumann's minimax theorem. To ease the discussion here, we first assume that `J` is indeed strictly concave in both `x` and `y`, such that both maps below are well‐defined and continuous:
