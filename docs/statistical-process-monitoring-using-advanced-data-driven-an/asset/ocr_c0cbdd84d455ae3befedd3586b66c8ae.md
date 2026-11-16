![](bbox=[0.16, 0.1, 0.87, 0.28])

FIGURE 8.24 Comparison of the performance of DBN-OCSVM with other algorithms in terms of AUC at different levels of bias (Case A).

![](bbox=[0.16, 0.36, 0.87, 0.54])

FIGURE 8.25 Comparison of the performance of the DBN-based detection algorithms in terms of AUC at different levels of bias (Case A).

This method outperformed the RBM-, DBN2-, and DSA-OCSVM methods, as well as the shallow OCSVM algorithm, which was applied directly to the ozone measurements without including the feature extraction steps. The results demonstrate that the method with a deeper network (DBN3-OCSVM) achieved better detection results than RBM-OCSVM or DBN2-OCSVM. This demonstrates the benefits of deep learning methods over shallow OCSVM, such as the ability to reveal information that is more useful for detecting abnormalities in ozone data. In addition, it was found that the DBN model extracted more informative features for anomaly detection than the DSA model.

The second comparison was conducted between DBN-OCSVM and the DBN-based EM, k-means, and BIRCH algorithms. The results are presented in Fig. 8.25. In this experiment, the clustering algorithms use the features extracted from the last layer of the DBN model. It was found that combining DBN with OCSVM resulted in a significantly greater detection ability than when DBN was combined with the other clustering algorithm (i.e., EM, k-means, and BIRCH). OCSVM is an assumption-free algorithm that, unlike the EM algorithm, does