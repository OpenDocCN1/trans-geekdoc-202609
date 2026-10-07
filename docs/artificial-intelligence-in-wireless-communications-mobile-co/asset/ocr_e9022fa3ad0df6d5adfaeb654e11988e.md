# Decision Making with Case-Based Learning 99

better reflect the environment to help make better choices. This technique is similar to an expert system, but one that learns autonomously.

A similarity function defines how similar two cases are and represented by (6.1). The similarity function is any that provides measure of how close these problems are to each other 0 represents no similarity and 1 represents a perfect match.

```
$s : P \times P \rightarrow [0, 1]$
```

The utility analysis of the past cases is represented in (6.2), which is any function that produces some real-valued result measuring the utility of the action.

```
$u : R \rightarrow \mathfrak{R}$
```

Case analysis comes down to which case is both most similar to the new problem as well how successful the action was in the past. The decision maker then uses a final decision to decide which case to use. The simplest implementation is a similarity-weighted decision function as shown in (6.3). A particular problem may be very similar to previous problems in the case base, but the solution to the previous problem might have performed poorly in the past. In this situation, a less similar but better performing case is selected instead.

```
$U(a) = s(p, q)u(r) \quad (q, a, r) \in M$
```

This equation is only one function used to make the decision. The challenge of this technique is to create effective similarity, utility, and decision functions that best represent the types of information received through the sensors. We develop this concept further throughout this chapter.

# 6.2 Cognitive Engine Architecture with CBDT

The cognitive engine uses case-based decision theory to augment the optimization process. Instead of relying on pure optimization alone, the case base helps prime and direct the optimization with learned experience. Likewise, instead of basing all decisions on past actions from the case base, the optimization process allows online learning work together to enable learning and adaptation in the cognitive engine.

The case base holds past cases, actions, and results of the actions. In the cognitive radio, the case represents some model of the environment, such as a