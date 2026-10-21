
Furthermore, to investigate if the algorithm is stable and if the overfitting problem exists, we calculate the cross-validation score. We further split the 70% training set into ten subsets, and fit the algorithm using nine of these subsets being the training data, and one set being the testing data. Rotating which set is the testing set, the average of these ten prediction accuracies is the cross-validation score.

Our selection rule for optimal tuning parameters goes as follows. We first plot the testing and cross-validation scores for various combinations of tuning parameters. The optimal tuning parameters are the simplest to achieve the highest testing scores, whereas the cross-validation scores are later used to check if the overfitting problem exists.

The above procedures give a simple rule to select the optimal tuning parameters. We remark that there are other alternatives to select the optimal tuning parameters. For instance, the optimal combination of tuning parameters are selected to maximize the performance measure (such as the F1-score or AUC).

Figure 101.6 compares testing and cross-validation scores against various combinations of tuning parameters: k ranging from 1, 21, 41, ..., 81, and two weighting schemes (uniform weight and distance weight). Testing scores with uniform and distance weighting are about the same, which are also close.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_3729_0.png)

Figure 101.6: Validation curves of the k-nearest neighbors against k with uniform weight and distance weight using training data and cross-validation of the credit card dataset.

### Validation Curve with Boosting

![](img/31ee7e6fa5107b22bbf7960ec96106a1_3731_0.png)

Figure 101.8: Validation curves of boosting against a number of estimators with tree maximum depths of one and two using training data and cross-validation of the credit card dataset.

### Validation Curve with SVM

![](img/31ee7e6fa5107b22bbf7960ec96106a1_3731_1.png)

Figure 101.9: Validation curves of the support vector machine against maximum iterations with polynomial and RBF functions using training data and cross-validation of the credit card data set.

instance is an anomaly and the algorithm fails to compare it to other similar instances. We decide to use a maximum tree depth of one since it is more general and does not perform worse than a maximum depth of 2, and 10 estimators because it gives better performance and this data set does not benefit from having more estimators.

Figure 101.9 compares the testing and cross-validation scores with the SVM using both the polynomial and RBF kernels with maximum iterations ranging from 1100, 1600, 2100, and 2600. Our experiments suggest to use the RBF kernel because it performs much better than the polynomial kernel, and it also runs faster than the polynomial kernel. In addition, we use a maximum iterations value of 2100, as no more improvements on the testing scores can be found with larger maximum iterations value.

We use the ReLU function as the activation function. For neural network, we decide to test the number of hidden layers and number of neurons in each hidden layer. Figure 101.10 compares the testing and cross-validation scores of neural network. The upper panel varies the number of hidden layers, and suggests us to select the number of hidden layers to be three. With three hidden layers, the lower panel varies the number of hidden neurons in each layer, which suggests us to have 15 neurons as a suitable size in each layer.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_3733_0.png)

Figure 101.11: Learning curves against number of examples with decision tree, neural network, boosting, support vector machine, and k-nearest neighbors, for the credit card dataset.

### 101.4.3 Learning curves

Figure 101.11 compares the accuracy with these five machine learning methods against the number of examples (the size of training set) with the optimal tuning parameters obtained in Section 101.4.2 to see if the accuracy appears to be stable as the number of examples increases. It is shown that KNN, decision tree, and boosting perform consistently as the number of examples increases. But SVM performs worse as the number of examples increases. As a conclusion, for the credit card data set, the decision tree algorithm performs the best. Not only does it yield the highest accuracy, but it runs the quickest.

## 101.5 Conclusions

### 101.5.1 Summary

In this chapter, we introduce five machine learning methods: k-nearest neighbors, decision tree, boosting, support vector machine, and neural network, to predict the default of credit card holders. For illustration, we conduct data analysis using a data set of 29,999 instances with 23 features and provide Python scripts for implementation. It is shown in our study that the decision tree performs best in predicting the default of credit card holders in terms of learning curves.

### 101.5.2 Limitations and future work

As the risk management for personal debt is of considerable importance, it is worthy of studying the following directions for future research. One limitation in this paper is that we only use one data set. According to Butaru et al. (2016), multiple data sets should be used to illustrate the robustness of a machine learning algorithm, and pairwise-comparisons should be conducted to verify which machine learning algorithm outperforms the others (Demšar, 2006; García and Herrera, 2008).

This chapter only uses accuracy as a measure to compare different machine learning methods. Indeed, in addition to the standard measures, such as precision, recall, F1-score, and AUC, it is interesting to consider cost-sensitive framework or profit measures to compare different machine learning algorithms as in Verbraken et al. (2014), Bahnsen et al. (2015), and Garrido et al. (2018).

Along with the availability of voluminous data in recent days, Moeyersoms and Martens (2015) solve high-cardinality attributes in churn prediction in the energy sector. In addition, it is also interesting to predict for longer-horizon or the default time (using survival analysis). Last but not least, it is of considerable importance to develop a method for extremely rare event. All the above mentioned issues are worthy of future studies and will be investigated in separate papers.

## Funding

The first author, Huei-Wen Teng, gratefully acknowledges the support by the Ministry of Science and Technology of Taiwan, ROC, under grant MOST 108-2118-M-009-001-MY2 and grant MOST 108-2634-F-163-001 through Pervasive Artificial Intelligence Research Labs, and the support under the Higher Education Sprout Project by the Ministry of Education of Taiwan, ROC.

## Bibliography

- Abdou, H., Pointon, J. and Masry, A.E. (2008). Neural Nets Versus Conventional Techniques in Credit Scoring in Egyptian Banking. Expert Systems with Applications 35(2), 1275-1292.
- Abu-Mostafa, Y.S., Magdon-Ismail, M. and Lin, H.-T. (2012). Learning from Data: A Short Course. AMLBook.
- Addo, P.M., Guegan, D. and Hassani, B. (2018). Credit Risk Analysis Using Machine and Deep Learning Models. Risks 6(2), 38.
- Bahnsen, A.C., Aouada, D. and Ottersten, B. (2015). A Novel Cost-sensitive Framework for Customer Churn Predictive Modeling. Decision Analytics 2(5), 1-15.
- Borovykh, A., Bothe, S. and Oosterlee, C. (2018). Conditional Time Series Forecasting with Convolutional Neural Networks. https://arxiv.org/abs/1703.04691v4 (retrieved June 15, 2018).
- Butaru, F., Chen, Q., Clark, B., Das, S., Lo, A.W. and Siddique, A. (2016). Risk and Risk Management in the Credit Card Industry. Journal of Banking and Finance 72, 218-239.
- Bzdok, D., Altman, N. and Krzywinski, M. (2018). Statistics Versus Machine Learning. Nature Methods 15(4), 233-234.
- Desai, V.S., Crook, J.N. and Overstreet, G.A. (1996). A Comparison of Neural Networks and Linear Scoring Models in the Credit Union Environment. European Journal of Operational Research 95(1), 24-47.
- Demšar, J. (2006). Statistical Comparisons of Classifiers Over Multiple Data Sets. Journal of Machine Learning Research 7, 1-30.
- Fernandes, G.B. and Artes, R. (2016). Spatial Dependence in Credit Risk and its Improvement in Credit Scoring. European Journal of Operational Research 249, 517-524.
- García, S. and Herrera, F. (2008). An Extension on “Statistical Comparisons of Classifiers over Multiple Data Sets” for all Pairwise Comparisons. Journal of Machine Learning Research 9, 2677-2694.
