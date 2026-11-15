![](bbox=[0.165, 0.115, 0.775, 0.235])

# **FIGURE 3.3**

The comparison of the computational efficiency of P-DVR and GT-CDGD [26] algorithms.

![](bbox=[0.165, 0.32, 0.775, 0.435])

# **FIGURE 3.4**

The comparison of the accuracy of P-DVR and GT-SAGA [19] algorithms.

across various datasets, the findings are exhibited in Fig. 3.2. The near parallelism of the two trends in Fig. 3.2 signifies that the projection operator maintains GT-SAGA’s linear convergence attribute during the resolution of the constraint issue. The reason the P-DVR algorithm appears beneath the GT-SAGA curve is due to the projection operator’s ability to swiftly direct the decision vector towards the optimal solution during initial iterations, thereby positioning the state of the P-DVR algorithm, denoted as $x_k$, nearer to the optimal solution $x^*$ at each $k$th iteration.

(ii) The computational efficiency of P-DVR: Fig. 3.3 clearly demonstrates the remarkable computational efficiency achieved through the application of the variance-reduction method. The principle behind this technique indicates that when there are $n$ data points per node, the number of component gradient computations required per iteration for an algorithm employing variance-reduction is just $\frac{1}{n}$ of those needed for an algorithm without it. Based on the experimental setup, it is evident that each node contains 400 COVTYPE data entries, 50 MNIST data entries, and 22 BREAST data entries. Fig. 3.3 precisely showcases that, on these three datasets, the P-DVR algorithm enhanced with variance-reduction offers a computational efficiency that is approximately 400 times, 50 times, and 22 times greater than the GT-CDGD algorithm without variance-reduction, respectively.

(iii) The effectiveness (accuracy) of the P-DVR algorithm: When evaluating the precision of binary classification, our emphasis is on contrasting the precision achieved by the P-DVR algorithm with a well-known algorithm operating under