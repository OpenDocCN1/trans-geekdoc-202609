
**Table 20.1: Basic information of three credit datasets.**

| Datasets | ACD | GCD | AMCD |
|---|---|---|---|
| No. of Total Instances | 690 | 1000 | 5000 |
| No. of Good Instances | 383 | 700 | 4185 |
| No. of Bad Instances | 307 | 300 | 815 |
| No. of Attributes | 14 | 24 | 65 |
| No. of Classes | 2 | 2 | 2 |

Different models’ performance in the given space and time. Notable examples include Australian credit dataset (ACD) and German credit dataset (GCD), which we could download from the UCI Machine Learning Repository (http://archive.ics.uci.edu/ml). ACD has 690 total instances, which is composed of 383 good instances and 307 bad instances. GCD has 1,000 total instances, which is composed of 700 good instances and 300 bad instances. The number of attributes of ACD and GCD are 14 and 24, respectively, which is far less than the number of instances. Obviously, these two datasets are balanced datasets, in which the positive and negative samples are basically the same size. In addition, we also utilized a real-life credit dataset of a US commercial bank (AMCD) to compare the classification ability of different models. Particularly, AMCD has 5,000 total instances, which is composed of 4,185 good instances and 815 bad instances. It’s worth noting that the proportion of bad instances in AMCD is relatively lower, at only 16.3%. Thus, AMCD is a typical unbalanced dataset and more like the actual situation. These three datasets we used in the experiment are described in Table 20.1.

### 20.3.2 SVM-based methodology

In order to classify the good and bad borrowers utilizing SVM-based methods, the whole framework should be constructed as shown in Figure 20.1.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_849_0.png)

**Figure 20.1:** The flow chart of utilizing SVM-based methods in credit risk analysis.

As shown in Figure 20.1, the specific algorithm steps for the classification problem are as follows:

- **1. Data collection and collation:** In this step, all the values of different attributes should be normalized, that is, map all the values to [0, 1]. When numerical levels vary considerably between different attributes, if we directly analyze with the original data, the model would largely be influenced by those attributes with higher levels. Therefore, in order to ensure the reliability of the results, it is necessary to normalize the original data. This could effectively avoid the errors from the values with different dimension. In general, min–max normalization method is a commonly used method, and the specific computational process could be found in Appendix 20A.

- **2. Choose appropriate feature extraction method for SVM:** In our research, we mainly focus on the regularization method which has the penalty on the model complexity. Hence, during this step, we would choose an appropriate regularization method to extract important and effective features for the SVM model. In detail, we could choose a certain regularization method from $L_1$, $L_2$ and adaptive $L_q$.

- **3. Choose appropriate kernel functions:** Based on the intrinsic structure of data, we could choose different kernel functions introduced in Section 20.2.3. In general, if the number of features is much larger than the sample size, or both number of features and the sample size are large, then the linear kernel function would be better. In addition, the Gauss kernel function is generally used in cases where the number of features is much less than the sample size.

- **4. Choose appropriate hyper-parameter optimization method:** Facing a certain kind of combination of penalty and kernel function which we determine before, GS, PSO, SA or ES method could be used to implement the hyper-parameter optimization process. Generally speaking, different hyper-parameter optimization methods themselves have different number of parameters which should be determined in advance; therefore, we should choose an appropriate method considering the present dataset structure.

- **5. Training and predicting process:** For the purpose of obtaining an independent test set, we randomly divided the whole dataset into two parts, and the corresponding proportion is 80% and 20%, respectively. After partitioning the training set and test set randomly for several times, SVM model's training and predicting would be implemented for many times, until we obtain the satisfactory accuracy. In other words, using the SVM model constructed through the combination of the above (2), (3) and (4) steps, we could implement the model training and predicting.

In total, we could utilize SVM-based methodology to classify the credit dataset through the above five steps. For every combination of different feature extraction method, kernel function and hyper-parameter optimization method, there is a certain SVM-based algorithm. For example, we could use GS-$L_1$G-SVM to stand for the algorithm which is composed of $L_1$ regularization method, Gauss kernel function and GS hyper-parameter optimization method.

Specifically speaking, the detailed procedure of the whole algorithm could be found in Appendix 20B of this chapter.

## 20.4 Experiment Results

To guarantee valid results for making predictions, the dataset was randomly partitioned into training sets and independent test sets, and the corresponding proportions are 80% and 20%. For a certain SVM-based method, which is a certain combination of feature extraction method, kernel function and hyper-parameter optimization method, 5-fold cross-validation is used in our experiments when training SVM models for choosing the hyper-parameters for the binary-class datasets. With 5-fold cross-validation, each sample is used for validating the model trained with the other samples in the training sets. Then we use this model with the optimal parameters in the test sets to make classification. Therefore, we could acquire the corresponding average validation accuracy and avoid overfitting. We used Matlab R2015b to perform all the computation.

The performance is measured by Type 1 accuracy (T1), Type 2 accuracy (T2) and Total accuracy (T). They stand for the percent of correctly classified good samples, the percent of correctly classified bad samples and the percent of correctly classified in total, respectively. The formulas are as follows (e.g., see Chen et al., 2011; Li et al., 2012):

$$\text{Total Accuracy (T)} = \frac{TP + TN}{TP + FN + TN + FP},$$

$$\text{Type 1 Accuracy (T1)} = \frac{TP}{TP + FN},$$

$$\text{Type 2 Accuracy (T2)} = \frac{TN}{TN + FP},$$

where TP is the number of good credit samples that are correctly classified; TN is the number of bad instances correctly classified; FN is the number of good credit samples that are misclassified, and FP is the number of the misclassified bad samples.

### 20.4.1 Experiment results — Different SVM-based models

Firstly, we compare the results of several different SVM-based models derived from the framework we constructed before, which are combinations of different penalty form ($L_1$, $L_2$ and adaptive $L_q$), different kernel functions (linear, polynomial, Gauss and Sigmoid) and different hyper-parameter optimization methods (GS, PSO, SA, ES). In total, there are 48 different kinds of methods under our computational framework theoretically. However, actually speaking, many kinds of methods are obviously not suitable for the credit dataset. For example, linear kernel function may not be suitable for the nonlinear classification tasks. Finally, after comparison and selection, results of those experiments with relatively high precision on the three credit datasets (ACD, GCD and AMCD) with SVM-based models are shown in Table 20.2.

The experiment results show that Gauss kernel-based SVM models show better accuracy than models with linear and polynomial kernel functions, and the classification accuracy of $L_q$-based methods is generally better than or equal to $L_1$- and $L_2$-based methods. As for hyper-parameter optimization method, ES-based methods and GS-based methods generally outperform the other methods, such as PSO and SA.
