# Table 8.3 Metrics used for causal discovery analysis [28, 29].

| Metric | Description |
| :--- | :--- |
| Missing or extra edges | Number of edges that are missing or present in the original model but not in the generated one. |
| Incorrect adjacencies | Number of undirected edges that are present in the generated model but not in the original one. |
| Incorrect and correct directed edges | Number of directed edges that are missing are present in the generated model that were correctly directed. |
| Structural hamming distance | Sum of missing edges, extra edges, and incorrectly directed edges. |
| Adjacency precision | Correctly predicted adjacencies/predicted adjacencies. |
| Adjacency recall | Correctly predicted adjacencies/true adjacencies. |
| Arrowhead precision | Correctly predicted arrowheads/predicted arrowheads. |
| Arrowhead recall | Correctly predicted arrowheads/true arrowheads. |
| Area-above-curve | AOC = 1 – AUC, where AUC (area-under-curve) measures the area below the graph of false positive rate and true positive rate. |

That is not the only quantity that we can infer. In fact, there are additional causal effects, such as the conditional average treatment effect (CATE)89 and the Average Treatment Effect on Treated (ATT),90 as well as the Individual Treatment Effect of unit (ITE),91 etc.

To find the ATT, it is only logical to only examine the beams in Group B.

To continue our example in order to estimate ATT, we would want to go back to Group B only. Then, ATT would be the E[Y1 - Y0] | T = 1 92.

There are a number of ML packages that can be used in causal inference investigations. These are listed in Table 8.4.

# 8.4.10 Causal Approach

In the following pages, I will be presenting an approach to causal discovery and causal inference that I will be adopting in the following examples pertaining to this chapter.

Let us start by presenting the approach.93

It is only natural for the proposed causal approach to comprise three steps. Causal discovery [to uncover the underlying structure through a causal graph, say a DAG94], causal inference [to infer how would the observed phenomenon/output change by intervening95], and, when possible, examine causal findings against a companion or independent analysis (say, from ML, statistical analysis, domain knowledge, etc.). Figure 8.9 demonstrates the proposed approach in more detail.

+   89 Simply, an ATE conditioned on a subset of the population.
+   90 Which answers the following question, what is the expected causal effect of the treatment for individuals in the treatment group?
+   91 Which answers the following question, what is the expected causal effect of the treatment on the outcome of a specific unit? It is obvious that ITE may not be easily hor possibly estimated from this example since we can only test each exact beam once. A workaround would be to estimate the difference in expectation between each identical beam to get a close estimate of ITE.
+   92 The PO approach extends to cover a wide range of applications and conditions (i.e., propensity scoring, confoundingness, missing data, matching, etc.). Please feel free to review [19].
+   93 Or, mental map!
+   94 We will leverage domain knowledge too!
+   95 Remember that an intervention equates to setting X = x as opposed to observing X = x. The former relates to causation (what is the fire resistance of a RC slab if its thickness is increased to 200 mm?) and the latter to prediction (what is the fire resistance of the same slab given it has a width of 200 mm)?