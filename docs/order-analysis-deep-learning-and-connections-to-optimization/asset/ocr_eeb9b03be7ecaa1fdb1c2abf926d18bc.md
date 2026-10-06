# 3.1 Optimality Conditions for a Unique Minimal Solution

```
= \delta\left(\alpha l_0 + \sum_{k \in J(\bar{x})} \beta_k l_k + \sum_{k \in J(\bar{x})} \gamma_k l_k\right)(x - \bar{x})\n= 0 .
```

Following the lines of Remark 3.2 (c), we then apply Theorem 3.1 (a), and we conclude that $\bar{x}$ is a unique minimal solution of the optimization problem

```
min f(x)\nsubject to the constraints\ng_1(x) \le 0\n:\ng_m(x) \le 0\ng_k(x) - g_k(\bar{x}) \le 0$ for all $k \in J(\bar{x})$\n$x \in \hat{S}$ . .
```

Next, we show that the inequality constraints in problem (3.10) defined by the index set $J(\bar{x})$ are redundant, i.e.,

```
$S = \{x \in S \mid g_k(x) - g_k(\bar{x}) \le 0$ for all $k \in J(\bar{x})\}$. .
```

It is obvious that the right-hand side in (3.11) is a subset of $S$. For the proof of the converse inclusion, choose an arbitrary $x \in S$, and we obtain with the definition in (3.8)

```
$g_k(x) - g_k(\bar{x}) \le 0$ for all $k \in J(\bar{x})$. . .
```

Hence, the Eq.(3.11) is shown, and the inequalities (3.12) can be dropped in problem (3.10). Consequently, the vector $\bar{x}$ is a unique minimal solution of the optimization problem $\min f(x)$. $x \in S$

Remark 3.3 ([35, Remark 3.15, (c) and (d)]

+   (a) The optimality conditions in Theorem 3.2 are an extension of the standard Fritz John conditions [80].
(b) The index set $J(\bar{x})$ is needed in Theorem 3.2 because the notion of active inequality constraints is too strict in discrete optimization. We have to incorporate inequality constraints, which are “nearly active.” The involvement of the index set $J(\bar{x})$ in the optimality condition (3.9) is one possibility to handle discrete-continuous problems. The following example illustrates this point: