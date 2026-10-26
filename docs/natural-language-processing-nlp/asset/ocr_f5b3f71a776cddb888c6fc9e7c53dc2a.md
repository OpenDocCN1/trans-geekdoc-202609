|  |  | ψ(·) | exp ψ(·) |
|---|---|---|---|
| S | → NP VP | 0 | 1 |
| NP | → NP PP | -1 | 1/2 |
|  | → we | -2 | 1/4 |
|  | → sushi | -3 | 1/8 |
|  | → chopsticks | -3 | 1/8 |
| PP | → IN NP | 0 | 1 |
| IN | → with | 0 | 1 |
| VP | → V NP | -1 | 1/2 |
|  | → VP PP | -2 | 1/4 |
|  | → MD V | -2 | 1/4 |
| V | → eat | 0 | 1 |

Table 10.2: An example weighted context-free grammar (WCFG). The weights are chosen so that exp ψ(·) sums to one over right-hand sides for each non-terminal; this is required by probabilistic context-free grammars, but not by WCFGs in general.

which are computed independently. In a weighted context-free grammar (WCFG), the score of each anchored production X → (α, (i, j, k)) is simply ψ(X → α), ignoring the anchor (i, j, k). In other parsing models, the anchors can be used to access features of the input, while still permitting efficient bottom-up parsing.

# Example

Consider the weighted grammar shown in Table 10.2, and the analysis in Figure 10.2b.

Ψ(τ) = ψ(S → NP VP) + ψ(VP → VP PP) + ψ(VP → V NP) + ψ(PP → IN NP)
      + ψ(NP → We) + ψ(V → eat) + ψ(NP → sushi) + ψ(IN → with) + ψ(NP → chopsticks) [10.6]
      = 0 − 2 − 1 + 0 − 2 + 0 − 3 + 0 − 3 = −11. [10.7]

In the alternative parse in Figure 10.2a, the production VP → VP PP (with score −2) is replaced with the production NP → NP PP (with score −1); all other productions are the same. As a result, the score for this parse is −10. This example hints at a problem with WCFG parsing on non-terminals such as NP, VP, and PP: a WCFG will always prefer either VP or NP attachment, regardless of what is being attached! Solutions to this issue are discussed in § 10.5.