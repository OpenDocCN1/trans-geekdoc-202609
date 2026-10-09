# **9.6.4.2 Covariance characteristics in handwriting recognition**

Similar to Section 9.6.4, Handwriting 1 and Handwriting 9 are classified in this section. The covariance sample set $C_R$ constructed from (9.75)–(9.78) is classified by Algorithm 9.4 and Algorithm 9.5, and the measure between the covariance samples in Algorithm 9.5 is given by (9.79). First, from the training set, randomly select 100 training samples of two types, and from the test set, randomly select 100 test samples of two types. The covariance matrix is constructed using (9.75)–(9.78) and then run 10 times for each case. In the experiment, the mean of Algorithm 9.5 is calculated by the log-Euclidean, i.e., (9.25), and Algorithm 9.4 does not change. The results obtained are shown in Figure 9.13.

From the experimental results in Figure 9.13, it can be clearly seen that Algorithm 9.4 has high classification accuracy in most cases by using (9.75), while Algorithm 9.5 and the matrix-based FLDA algorithm are essentially flat using (9.77). However, when using (9.76) and (9.78), the classification accuracy of the two Lie–Fisher algorithms is slightly lower than that of the FLDA algorithm, indicating that the sample distribution at this time is basically linearly separable. When mapping the mean of the sample and Lie group-Lie algebra, the accuracies of the two Lie–Fisher algorithms are reduced, resulting in a decrease in classification accuracy. In Figure 9.13(b), compared to (a), because the first-order gradient vector length operator is used, Algorithm 9.5 becomes very unstable with low classification accuracy, whereas the FLDA algorithm and Algorithm 9.4 are relatively stable with high accuracy. This

![](bbox=[0.08, 0.51, 0.48, 0.66])

![](bbox=[0.49, 0.51, 0.83, 0.66])

![](bbox=[0.08, 0.67, 0.48, 0.82])

![](bbox=[0.49, 0.67, 0.83, 0.82])

**Fig. 9.13:** Using the experimental results of (9.47)–(9.50), where the number of iterations is abscissa and the classification accuracy is ordinate.