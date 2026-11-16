sections we derive a linear formulation depending on the chosen machine learning model for the value function \(\tilde{v}_i(x)\). We are going to present solutions for two different models, a linear model and a fully-connected multi-layer neural network.

# Solution for Linear Model

We first treat the case where the machine learning model is a simple linear model and call this approach **GALO** (linear).

In the linear model the estimated value function is of the form \(\tilde{v}_i(x) = w^Tx + w_0\), where \(w = (w_1, ..., w_m) \in \mathbb{R}^m\) and \(w_0 \in \mathbb{R}\). The function is obviously linear caused by the Euclidean norm. The nonlinearity is only caused by the Euclidean norm.

Let \(C\) be a large constant. The following ILP erases the nonlinearity while staying equivalent to (2.12).

```
arg max \ r \\
s.t. \\
y - \tilde{v}_i(x) \le r \\
\tilde{v}_i(x) - y \le r \\
y' - \tilde{v}_i(x) + C \cdot b_{y'} \ge r \\
\tilde{v}_i(x) - y' + C \cdot (1 - b_{y'}) \ge r \quad \forall y' \in Y \\
b_{y'} \in \{0, 1\} \quad \forall y' \in Y \\
r \in \mathbb{R}
```

Before we can proof Theorem 2.12, we introduce Lemma 2.11 which will be helpful for the equivalence proof.

**Lemma 2.11.** Let \(b_{y'} \in \{0, 1\}\). Let further \(C\) be a large enough constant. Then it holds that \(|y' - \tilde{v}_i(x)| \ge r\), if and only if \(y' - \tilde{v}_i(x) + C \cdot b_{y'} \ge r\) and \(\tilde{v}_i(x) - y' + C \cdot (1 - b_{y'}) \ge r\).

*Proof of Lemma 2.11.* We make a case distinction.