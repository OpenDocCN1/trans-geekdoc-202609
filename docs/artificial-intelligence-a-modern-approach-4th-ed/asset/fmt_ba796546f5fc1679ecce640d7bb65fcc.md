
## 6.3.1 Evaluation Function

In practice, this kind of analysis requires too many categories and hence too much experience to estimate all the probabilities. Instead, most evaluation functions compute separate numerical contributions from each feature and then combine them to find the total value. For centuries, chess players have developed ways of judging the value of a position using just this idea. For example, introductory chess books give an approximate material value for each piece: each pawn is worth 1, a knight or bishop is worth 3, a rook 5, and the queen 9. Other features such as “good pawn structure” and “king safety” might be worth half a pawn, say. These feature values are then simply added up to obtain the evaluation of the position.

> **Material value**

Mathematically, this kind of evaluation function is called a weighted linear function because it can be expressed as

$\\text{EVAL}\\,\\text{(}s\\text{)~=~}w\_{\\text{1}}\\ f\_{\\text{1}}\\text{(}s\\text{)}\\,\\text{+}\\, w\_{\\text{2}}\\ f\_{\\text{2}}\\text{~(}s\\text{)~+}\\ldots\\text{+~}w\_{n}\\ f\_{n}\\,\\text{(}s\\text{)~=}{\\sum\\limits\_{i = 1}^{n}{w\_{i}\\ f\_{i}\\,\\text{(}s\\text{)~,}}}$

where each `fi` is a feature of the position (such as “number of white bishops”) and each `wi` is a weight (saying how important that feature is). The weights should be normalized so that the sum is always within the range of a loss (0) to a win (+1). A secure advantage equivalent to a pawn gives a substantial likelihood of winning, and a secure advantage equivalent to three pawns should give almost certain victory, as illustrated in [Figure 6.8(a)](#Chapter06-03.xhtml#fig6-8). We said that the evaluation function should be strongly correlated with the actual chances of winning, but it need not be linearly correlated: if state `s` is twice as likely to win as state `s'` we don’t require that `EVAL(S)` be twice `EVAL(S')`; all we require is that `EVAL(S)` > `EVAL(S')`.

> **Weighted linear function**

Description

The graph consists of six nodes labeled "A", B, C, D, E, and F. Figure (“a”): Node B is connected to node "A" on the upper left, node C on the lower left, and node D on the right. Node D is connected to node E on the upper right and node F on the lower right. Figure (b): Node "A" is connected to node B on the right. Node B is connected to nodes C and D on the right. Node D is connected to nodes E, and F on the right.

×![](images/Fig-92.jpg)

Figure 6.8 Two chess positions that differ only in the position of the rook at lower right. In (a), Black has an advantage of a knight and two pawns, which should be enough to win the game. In (b), White will capture the queen, giving it an advantage that should be strong enough to win.

Adding up the values of features seems like a reasonable thing to do, but in fact it involves a strong assumption: that the contribution of each feature is independent of the values of the other features. For this reason, current programs for chess and other games also use nonlinear combinations of features. For example, a pair of bishops might be worth more than twice the value of a single bishop, and a bishop is worth more in the endgame than earlier—when the move number feature is high or the number of remaining pieces feature is low.

Where do the features and weights come from? They’re not part of the rules of chess, but they are part of the culture of human chess-playing experience. In games where this kind of experience is not available, the weights of the evaluation function can be estimated by the machine learning techniques of [Chapter 23](#Chapter23-00.xhtml). Applying these techniques to chess has confirmed that a bishop is indeed worth about three pawns, and it appears that centuries of human experience can be replicated in just a few hours of machine learning.

## 6.3.2 Cutting off search

The next step is to modify `ALPHA-BETA-SEARCH` so that it will call the heuristic `EVAL` function when it is appropriate to cut off the search. We replace the two lines in [Figure 6.7](#Chapter06-02.xhtml#fig6-7) that mention `IS-TERMINAL` with the following line:

```
if game.IS-CUTOFF(state, depth) then return game.EVAL(state, player), null
```

We also must arrange for some bookkeeping so that the current depth is incremented on each recursive call. The most straightforward approach to controlling the amount of search is to set a fixed depth limit so that `IS-CUTOFF(state, depth)` returns true for all depth greater than some fixed depth `d` (as well as for all terminal states). The depth `d` is chosen so that a move is selected within the allocated time. A more robust approach is to apply iterative deepening. (See [Chapter 3](#Chapter03-00.xhtml).) When time runs out, the program returns the move selected by the deepest completed search. As a bonus, if in each round of iterative deepening we keep entries in the transposition table, subsequent rounds will be faster, and we can use the evaluations to improve move ordering.

These simple approaches can lead to errors due to the approximate nature of the evaluation function. Consider again the simple evaluation function for chess based on material advantage. Suppose the program searches to the depth limit, reaching the position in [Figure 6.8(b)](#Chapter06-03.xhtml#fig6-8), where Black is ahead by a knight and two pawns. It would report this as the heuristic value of the state, thereby declaring that the state is a probable win by Black. But White’s next move captures Black’s queen with no compensation. Hence, the position is actually favorable for White, but this can be seen only by looking ahead.

The evaluation function should be applied only to positions that are quiescent—that is, positions in which there is no pending move (such as a capturing the queen) that would wildly swing the evaluation. For nonquiescent positions the `IS-CUTOFF` returns false, and the search continues until quiescent positions are reached. This extra quiescence search is sometimes restricted to consider only certain types of moves, such as capture moves, that will quickly resolve the uncertainties in the position.

> **Quiescence**
> **Quiescence search**

The horizon effect is more difficult to eliminate. It arises when the program is facing an opponent’s move that causes serious damage and is ultimately unavoidable, but can be temporarily avoided by the use of delaying tactics. Consider the chess position in [Figure 6.9](#Chapter06-03.xhtml#fig6-9). It is clear that there is no way for the black bishop to escape. For example, the white rook can capture it by moving to h1, then a1, then a2; a capture at depth 6 ply.

Description

The graph consists of seven nodes labeled S "A", W "A", N T, Q, N S W, V, and T. Node T remains isolated from the other nodes. Node S "A" is at the center and connects the remaining nodes as follows. S "A" node is connected to node W "A" on the left, node N T above, node Q on the upper right, node N S W on the right, and node V on the lower right. Node W "A" is connected to node N T. Node N T is connected to node Q. Node Q is connected to node N S W. Node N S W is connected to node V.

×![](images/Fig-93.jpg)

Figure 6.9 The horizon effect. With Black to move, the black bishop is surely doomed. But Black can forestall that event by checking the white king with its pawns, encouraging the king to capture the pawns. This pushes the inevitable loss of the bishop over the horizon, and thus the pawn sacrifices are seen by the search algorithm as good moves rather than bad ones.

> **Horizon effect**
