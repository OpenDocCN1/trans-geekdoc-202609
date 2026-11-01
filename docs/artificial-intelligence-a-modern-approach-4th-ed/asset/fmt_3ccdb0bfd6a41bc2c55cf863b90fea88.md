
Typically, we assume that the empty set of players achieves nothing (`v({}) = 0`), and that the function is nonnegative (`v(C) ≥ 0` for all `C`). In some games we make the further assumption that players achieve nothing by working alone: `v({i}) = 0` for all `i ∈ N`.

## 17.3.1 Coalition structures and outcomes

It is conventional to refer to a subset of players `C` as a coalition. In everyday use the term “coalition” implies a collection of people with some common cause (such as the Coalition to Stop Gun Violence), but we will refer to any subset of players as a coalition. The set of all players `N` is known as the grand coalition.

In our model, every player must choose to join exactly one coalition (which could be a coalition of just the single player alone). Thus, the coalitions form a partition of the set of players. We call the partition a coalition structure. Formally, a coalition structure over a set of players `N` is a set of coalitions `{C1,...,Ck}` such that:

```
\begin{array}{l}
{C_{i} \neq {\{ \}}}
{C_{i} \subseteq N}
{C_{i} \cap C_{j} = {\{ \}} \text{~for~all~} i \neq j \in N}
{C_{1} \cup \cdots \cup C_{k} = N.}
\end{array}
```

For example, if we have `N = {1,2,3}`, then there are seven possible coalitions:

`{1}`, `{2}`, `{3}`, `{1,2}`, `{2,3}`, `{3,1}`, and `{1,2,3}`

and five possible coalition structures:

`{{1}, {2}, {3}}`, `{{1}, {2,3}}`, `{{2},{1,3}}`, `{{3}, {1,2}}`, and `{{1,2,3}}`.

We use the notation `CS(N)` to denote the set of all coalition structures over player set `N`, and `CS(i)` to denote the coalition that player `i` belongs to.

The outcome of a game is defined by the choices the players make, in deciding which coalitions to form, and in choosing how to divide up the `v(C)` value that each coalition receives. Formally, given a cooperative game defined by (`N`,`v`), the outcome is a pair (`CS`, `x`) consisting of a coalition structure and a payoff vector `x = (x1,...,xn)` where `xi` is the value that goes to player `i`. The payoff must satisfy the constraint that each coalition `C` splits up all of its value `v(C)` among its members:

```
\begin{matrix}
{\sum\limits_{i \in C}{x_{i} = v(C)}} & {\text{for~all~}C \in CS}
\end{matrix}
```

For example, given the game (`{1,2,3}`, `v`) where `v({1}) = 4` and `v({2,3}) = 10`, a possible outcome is:

`({{1},{2,3}}, (4,5,5))`.

That is, player 1 stays alone and accepts a value of 4, while players 2 and 3 team up to receive a value of 10, which they choose to split evenly.

Some cooperative games have the feature that when two coalitions merge together, they do no worse than if they had stayed apart. This property is called superadditivity. Formally, a game is superadditive if its characteristic function satisfies the following condition:

```
\begin{matrix}
{v(C \cup D) \geq v(C) + v(D)} & {\text{for~all~}C,D \subseteq N}
\end{matrix}
```

If a game is superadditive, then the grand coalition receives a value that is at least as high as or higher than the total received by any other coalition structure. However, as we will see shortly, superadditive games do not always end up with a grand coalition, for much the same reason that the players do not always arrive at a collectively desirable Pareto–optimal outcome in the prisoner’s dilemma.

## 17.3.2 Strategy in cooperative games

The basic assumption in cooperative game theory is that players will make strategic decisions about who they will cooperate with. Intuitively, players will not desire to work with unproductive players—they will naturally seek out players that collectively yield a high coalitional value. But these sought-after players will be doing their own strategic reasoning. Before we can describe this reasoning, we need some further definitions.

An imputation for a cooperative game (`N`, `v`) is a payoff vector that satisfies the following two conditions:

```
\begin{array}{l}
{\sum_{i = 1}^{n}x_{i} = v(N)}
{x_{i} \geq v(\{i\})~for~all~i \in N.}
\end{array}
```

The first condition says that an imputation must distribute the total value of the grand coalition; the second condition, known as individual rationality, says that each player is at least as well off as if it had worked alone.

Given an imputation `x = (x1,...,xn)` and a coalition `C ⊆ N`, we define `x(C)` to be the sum `∑[i ∈ C] x[i]`—the total amount disbursed to `C` by the imputation `x`.

Next, we define the core of a game (`N`, `v`) as the set of all imputations `x` that satisfy the condition `x(C) ≥ v(C)` for every possible coalition `C ⊂ N`. Thus, if an imputation `x` is not in the core, then there exists some coalition `C ⊂ N` such that `v(C) > x(C)`. The players in `C` would refuse to join the grand coalition because they would be better off sticking with `C`.

The core of a game therefore consists of all the possible payoff vectors that no coalition could object to on the grounds that they could do better by not joining the grand coalition. Thus, if the core is empty, then the grand coalition cannot form, because no matter how the grand coalition divided its payoff, some smaller coalition would refuse to join. The main computational questions around the core relate to whether or not it is empty, and whether a particular payoff distribution is in the core.

The definition of the core naturally leads to a system of linear inequalities, as follows (the unknowns are variables `x1,..., xn`, and the values `v(C)` are constants):

```
\begin{array}{l}
{x_{i} \geq v(\{i\})}
{\sum_{i \in N} x_{i} = v(N)}
{\sum_{i \in C} x_{i} \geq v(N)}
\end{array}
\begin{array}{l}
{\text{for~all~}i \in N}
{\text{for~all~}C \subseteq N}
\end{array}
```

Any solution to these inequalities will define an imputation in the core. We can formulate the inequalities as a linear program by using a dummy objective function (for example, maximizing `∑[i ∈ N] x[i]`), which will allow us to compute imputations in time polynomial in the number of inequalities. The difficulty is that this gives an exponential number of inequalities (one for each of the `2n` possible coalitions). Thus, this approach yields an algorithm for checking non-emptiness of the core that runs in exponential time. Whether we can do better than this depends on the game being studied: for many classes of cooperative game, the problem of checking non-emptiness of the core is co-NP-complete. We give an example below.

Before proceeding, let’s see an example of a superadditive game with an empty core. The game has three players `N = {1,2,3}`, and has a characteristic function defined as follows:

```
v(C) = \left\{ \begin{array}{l}
{\text{1~if~|}C\text{|~} \geq \text{~2}}
{\text{0~otherwise}.}
\end{array} \right.
```

Now consider any imputation (`x1`, `x2`, `x3`) for this game. Since `v(N) = 1`, it must be the case that at least one player `i` has `xi > 0`, and the other two get a total payoff less than 1. Those two could benefit by forming a coalition without player `i` and sharing the value 1 among themselves. But since this holds for all imputations, the core must be empty.

The core formalizes the idea of the grand coalition being stable, in the sense that no coalition can profitably defect from it. However, the core may contain imputations that are unreasonable, in the sense that one or more players might feel they were unfair. Suppose `N = {1,2}`, and we have a characteristic function `v` defined as follows:
