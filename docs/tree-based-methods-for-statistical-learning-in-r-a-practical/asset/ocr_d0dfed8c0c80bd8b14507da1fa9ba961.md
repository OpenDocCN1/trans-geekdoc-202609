![](bbox=[0.13, 0.1, 0.86, 0.4])

FIGURE 2.9: Regression tree diagram (left) and corresponding regression surface (right) for the air quality data. These are the same splits shown in Figure 2.1.

$x$ into two mutually disjoint groups. For example, if $x$ took on the categories $\{a,b,c\}$, then we could form a total three splits:

+   - $x \in \{a\}$ vs. $x \in \{b,c\}$;
+   - $x \in \{b\}$ vs. $x \in \{a,c\}$;
+   - $x \in \{c\}$ vs. $x \in \{a,b\}$.

For a nominal predictor with $J$ categories

In short, the optimal split for a nominal predictor $x$ at some node $A$ can be found by first ordering the individual categories of $x$ by their average response value—for example, the proportion of successes in the binary outcome case—and then finding the best split using this new ordinal variable.$^\mathsection$ This reduces