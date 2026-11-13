# Example no. 3 discovering causal structure for an unknown DGP (Python)

The following case study will attempt to uncover the unknown DGP of fire resistance of RC columns but using the Python library, CausalNex [42]106. CausalNex is a Python library that depicts the causal relationship between variables via DAGs. To overcome the search space of multiple variables, CausalNex employs an optimized structure learning algorithm, NOTEARS [43], to find the variables that have the most influence on the target. This makes CausalNex an ideal tool for causal discovery.

I will use the same database we used in an earlier chapter to predict fire resistance of RC columns (as well as in unsupervised/clustering analysis) herein too. As you have seen, this database has 144 full scale fire-exposed RC columns, each of which has the following parameters: 1) column width, W, 2) steel reinforcement ratio, r, 3) column length, L, 4) concrete compressive strength, fc, 5) column effective length factor, K, 6) concrete cover to steel reinforcement, C, 7) the magnitude of applied loading, P, and 8) fire resistance time, FR.

At this point in time, CausalNex does not accommodate continuous data (due to its Bayesian Network nature). As such, the database was discretized via the Decision Tree Supervised discrimination method within CausalNex [44]. The thresholds for discretizing all features are listed in Table 8.5.

![](bbox=[0.095, 0.37, 0.385, 0.595])

Once the data is discretized, the Bayesian network interface within CausalNex is trained to create a DAG. This DAG is created by learning the joint probability distribution of all the variables from the data. Then, the DAG is examined to check its predictive accuracy. Since the data was discretized, then a classification analysis was followed. In this study, the database was split into two sets as 70/30 for the training and testing of the model107. The classification was performed using the Bayesian Network Classifier (see Table 8.6) and achieved an accuracy, precision, and recall of 0.86/0.86, 0.90/0.89, and 0.910.86 for training/testing, respectively.

Following the above classification, the discretized data regressed to evaluate its explanatory power. In this regression, the Random Forest ML model is applied and achieves an R2 score of 0.85 and 0.811 on the training and test data. This implies that the created DAG in Figure 8.10 is suitable for an inference analysis. Let us examine this DAG. As you can see, the majority of the causal links could be justified by our domain knowledge. For instance, there is a direct link from W to C, and this link can be explained by the fact that the concrete cover is often a function of the width of the column.108 Another link from W to P may explain that the magnitude of applied load a column can carry is tied to the capacity of the same column, which also include W as a main parameter. However, some links are much harder to justify. For example, the link from C to fc and fc to K.109

Figure 8.10 Causal model for fire resistance RC columns [from CausalNex].

| Variables | Threshold values |
|---|---|
| C (mm) | 27.5, 39, 44.5 |
| K | 0.59, 0.85 |
| L (m) | 2.4, 3.9, 4.3 |
| P (kN) | 538, 975.5, 1174 |
| W (mm) | 201.5, 302.5, 431.5 |
| fc (MPa) | 26.5, 33.5, 34.5 |
| R (%) | 0.95, 1.18, 1.9 |
| FR (min) | 60, 120, and 180 |

106 We will use the arrived at DGP to infer the effect of intervention in the next section using the Python library DoWhy in Example no. 4.
107 Please note that CausalNex does not incorporate cross-validation training at the moment.
108 A quick look into ACI 216.1 shows a couple of tables where FR is governed by C and W!
109 What to do? Well, we continue testing! For now, we will simplify this DAG.