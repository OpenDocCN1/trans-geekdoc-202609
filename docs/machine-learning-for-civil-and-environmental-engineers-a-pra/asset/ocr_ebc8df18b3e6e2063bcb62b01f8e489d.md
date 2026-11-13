![](bbox=[0.095, 0.09, 0.66, 0.435])

Figure 4.1 A snippet of notable ML algorithms [1, 2].6 "Decision trees (DT) and gradient boosted trees (GBTs).

fall under supervised learning can accommodate regression and classification problems. On the other hand, algorithms belonging to unsupervised learning are traditionally reserved for this particular type of learning, and these too are presented in the second half of this chapter.

# 4.1.1 Supervised Learning

As you remember, ML problems comprising datasets with labeled7 targets fall under supervised learning. These problems encompass the majority of the ML realm and our domain.8 Let us go over some of the most notable algorithms that fall under supervised learning and work well for regression and classification problems.

# 4.1.1.1 Adaptive Neuro-fuzzy Interface System (ANFIS)

The adaptive neuro-fuzzy interface system (ANFIS) is a multilayer adaptive network-based fuzzy inference system. This system contains a number of nodes connected through directional links. Each node is identified by a function with a fixed or adjustable parameter.

The ANFIS system can accommodate numerical, verbal, logical, or conditional terms of “if-then” rules to capture imprecise knowledge of fuzzy variables9 [3]. This process involves mapping through membership functions to numerically define the partial belonging (i.e., fuzziness) of a statement by assigning values on a scale between zero and unity.

# How does ANFIS work?

One approach to apply ANFIS is via the first order Takagi-Sugeno model [4], which includes two inputs, x and y (see Figure 4.2). This model is set with two if-then rules, as shown by the following formulations, and yields a weighted average of each output rule:

6 This chapter builds on my group’s two review papers [1, 2].
7 Please remember that semi-supervised learning is applied when the labels are only available for a small percentage of targets.
8 This makes sense! Especially when we recognize that we heavily use ML to predict phenomena (which implies that we know the target and we can label it).
9 A fuzzy variable is one that can be an adjective, i.e., strong and weak, hot and cold. It is worth noting that fuzzy logic was created by Prof. Lotfi Zadeh. Fuzzy variables can be attractive to capture the uncertainty of features.