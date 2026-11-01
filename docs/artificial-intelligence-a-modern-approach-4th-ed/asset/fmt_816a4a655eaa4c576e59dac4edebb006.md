
# Normal Form Games

The first game model we will look at is one in which all players take action simultaneously and the result of the game is based on the profile of actions that are selected in this way. (Actually, it is not crucial that the actions take place at the same time; what matters is that no player has knowledge of the other players’ choices.) These games are called normal form games. A normal form game is defined by three components:

Normal form game

## Components

• Players or agents who will be making decisions. Two-player games have received the most attention, although `n`-player games for `n` > 2 are also common. We give players capitalized names, like `Ali` and `Bo` or `O` and `E`.

Player

• Actions that the players can choose. We will give actions lowercase names, like `one` or `testify`. The players may or may not have the same set of actions available.

• A payoff function that gives the utility to each player for each combination of actions by all the players. For two-player games, the payoff function for a player can be represented by a matrix in which there is a row for each possible action of one player, and a column for each possible choice of the other player: a chosen row and a chosen column define a matrix cell, which is labeled with the payoff for the relevant player. In the two-player case, it is conventional to combine the two matrices into a single payoff matrix, in which each cell is labeled with payoffs for both players.

Payoff function
Payoff matrix

## Example: Two-Finger Morra

To illustrate these ideas, let’s look at an example game, called two-finger Morra. In this game, two players, `O` and `E`, simultaneously display `one` or `two` fingers. Let the total number of fingers displayed be `f`. If `f` is odd, `O` collects `f` dollars from `E`; and if `f` is even, `E` collects `f` dollars from `O`. The payoff matrix for two-finger Morra is as follows:

|  || `O`: `one` || `O`: `two` |
| --- | --- | --- |
| `E`: `one` || `E` = +2, `O` = –2 || `E` = –3, `O` = +3 |
| `E`: `two` || `E` = –3, `O` = +3 || `E` = +4, `O` = –4 |

We say that `E` is the row player and `O` is the column player. So, for example, the lower-right corner shows that when player `O` chooses action `two` and `E` also chooses `two`, the payoff is +4 for `E` and –4 for `O`.

Row player
Column player

Before analyzing two-finger Morra, it is worth considering why game-theoretic ideas are needed at all: why can’t we tackle the challenge facing (say) player `E` using the apparatus of decision theory and utility maximization that we’ve been using elsewhere in the book? To see why something else is needed, let’s suppose `E` is trying to find the best action to perform. The alternatives are `one` or `two`. If `E` chooses `one`, then the payoff will be either +2 or –3. Which payoff `E` will actually receive, however, will depend on the choice made by `O`: the most that `E` can do, as the row player, is to force the outcome of the game to be in a particular row. Similarly, `O` chooses only the column.

To choose optimally between these possibilities, `E` must take into account how `O` will act as a rational decision maker. But `O`, in turn, should take into account the fact that `E` is a rational decision maker. Thus, decision making in multiagent settings is quite different in character to decision making in single-agent settings, because the players need to take each other’s reasoning into account. The role of solution concepts in game theory is to try to make this kind of reasoning precise.

Solution concept

## Strategies

The term strategy is used in game theory to denote what we have previously called a policy. A pure strategy is a deterministic policy; for a single-move game, a pure strategy is just a single action. As we will see below, for many games an agent can do better with a mixed strategy, which is a randomized policy that selects actions according to a probability distribution. The mixed strategy that chooses action `a` with probability `p` and action `b` otherwise is written `p: a; (1 – p): b`. For example, a mixed strategy for two-finger Morra might be `0.5: one;0.5: two`. A strategy profile is an assignment of a strategy to each player; given the strategy profile, the game’s outcome is a numeric value for each player—if players use mixed strategies, then we must use expected utility.

Strategy
Pure strategy
Mixed strategy
Strategy profile

So, how should agents decide act in games like Morra? Game theory provides a range of solution concepts that attempt to define rational action with respect to an agent’s beliefs about the other agent’s beliefs. Unfortunately, there is no one perfect solution concept: it is problematic to define what “rational” means when each agent chooses only part of the strategy profile that determines the outcome.

## Prisoner’s Dilemma

We introduce our first solution concept through what is probably the most famous game in the game theory canon—the prisoner’s dilemma. This game is motivated by the following story: Two alleged burglars, `Ali` and `Bo`, are caught red-handed near the scene of a burglary and are interrogated separately. A prosecutor offers each a deal: if you testify against your partner as the leader of a burglary ring, you’ll go free for being the cooperative one, while your partner will serve 10 years in prison. However, if you both testify against each other, you’ll both get 5 years. `Ali` and `Bo` also know that if both refuse to testify they will serve only 1 year each for the lesser charge of possessing stolen property. Now `Ali` and `Bo` face the so-called prisoner’s dilemma: should they testify or refuse? Being rational agents, `Ali` and `Bo` each want to maximize their own expected utility, which means minimizing the number of years in prison—each is indifferent about the welfare of the other player. The prisoner’s dilemma is captured in the following payoff matrix:

Prisoner’s dilemma

|   || `Ali`: `testify` || `Ali`: `refuse` |
| --- | --- | --- |
| `Bo`: `testify` || `A` = –5, `B` = –5 || `A` = –10, `B` = 0 |
| `Bo`: `refuse` || `A` = 0, `B` = –10 || `A` = –1, `B` = –1 |

Now, put yourself in `Ali`’s place. She can analyze the payoff matrix as follows:

• Suppose `Bo` plays `testify`. Then I get 5 years if I testify and 10 years if I don’t, so in that case testifying is better.
• On the other hand, if `Bo` plays `refuse`, then I go free if I testify and I get 1 year if I refuse, so testifying is also better in that case.
• So no matter what `Bo` chooses to do, it would be better for me to testify.

`Ali` has discovered that `testify` is a dominant strategy for the game. We say that a strategy `s` for player `p` strongly dominates strategy `s'` if the outcome for `s` is better for `p` than the outcome for `s'`, for every choice of strategies by the other player(s). Strategy `s` weakly dominates `s'` if `s` is better than `s'` on at least one strategy profile and no worse on any other. A dominant strategy is a strategy that dominates all others. A common assumption in game theory is that a rational player will always choose a dominant strategy and avoid a dominated strategy. Being rational—or at least not wishing to be thought irrational—`Ali` chooses the dominant strategy.

Dominant strategy
Strong domination
Weak domination

It is not hard to see that `Bo`’s reasoning will be identical: he will also conclude that `testify` is a dominant strategy for him, and will choose to play it. The solution of the game, according to dominant strategy analysis, will be that both players choose `testify`, and as a consequence both will serve 5 years in prison.
