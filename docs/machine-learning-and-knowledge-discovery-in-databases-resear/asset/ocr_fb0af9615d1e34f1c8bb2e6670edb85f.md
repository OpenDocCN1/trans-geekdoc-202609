![](bbox=[0.09, 0.08, 0.87, 0.18])

**Fig. 7.** Two MNIST images matching the logical formula \(\psi\) extracted by PUTPUT from a learned probabilistic circuit.

**Table 1.** Results of experiment 1 after the first step of PUTPUT, showing the average F1-score and circuit size (and standard deviations) in relation to \(\mathcal{E}_{HPR}\). The abbreviation gen. sign. refers to the generic significance method.

| Function | F1-score | Circuit size (# nodes) |
|---|---|---|
| no pruning | | 3086 ± 1163 |
| circuit flows | 0.313 ± 0.23 | 1812 ± 812 |
| gen. sign. | 0.285 ± 0.24 | 2281 ± 904 |

_Experiment 2: Effect of PUTPUT's Step 2._ The second step of PUTPUT prunes the input nodes to further lower the aggregated entropy. Table 2 shows the results of PUTPUT applied on the open-source benchmarks. We conclude for the second research question, that the second step significantly decreased the aggregated entropy. Furthermore, it also increased the F1-score and recall.

_Experiment 3: evaluation of PUTPUT._ For all datasets, we evaluate using the ground truth labels rather than \(\mathcal{E}_{HPR}\). To the best of our knowledge, the only other work that operates in a PU learning scenario and produces an interpretable model that is convertible into a database query, is the work by Goyal et al. [15]. They learn a decision tree (_DT_) by first enhancing the dataset with negative examples, via either the Rocchio (_r_) or Likelihood (_l_) method [3]. In addition to replicating their work, we also extend their idea by considering inductive logic programming (_ILP_): instead of learning a decision tree, we learn logical rules using RIPPER [9]. Because those methods are not easily convertible into CNF, but are easily convertible into DNF, we apply them on the reliable negatives as the positive class, converting the resulting DNF into CNF by negation. Afterwards, we compare the CNF to the one produced by our method, PUT-

**Table 2.** Results of experiment 2, showing average and standard deviation for various metrics, in relation to examples \(\mathcal{E}_{HPR}\), after PUTPUT step 1 and 2.

| Step | F1-score | Aggregated entropy | Precision | Recall | PC size (# nodes) | LC size (# nodes) |
|---|---|---|---|---|---|---|
| 1 | 0.313 ± 0.23 | 10168 ± 45798 | 0.341 ± 0.25 | 0.363 ± 0.27 | 1812 ± 812 | 1168 ± 1242 |
| 2 | 0.362 ± 0.23 | 287 ± 454 | 0.341 ± 0.26 | 0.381 ± 0.26 | 523 ± 294 | 92 ± 73 |