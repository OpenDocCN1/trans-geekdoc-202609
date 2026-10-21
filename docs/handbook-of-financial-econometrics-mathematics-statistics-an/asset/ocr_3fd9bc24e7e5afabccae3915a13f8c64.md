![](bbox=[0.1, 0.08, 0.9, 0.68])

Figure 20.1: The flow chart of utilizing SVM-based methods in credit risk analysis.

original data. This could effectively avoid the errors from the values with different dimension. In general, min–max normalization method is a commonly used method, and the specific computational process could be found in Appendix 20A.

(2) Choose appropriate feature extraction method for SVM: In our research, we mainly focus on the regularization method which has the penalty on the model complexity. Hence, during this step, we would choose an appropriate regularization method to extract important and effective features for the SVM model. In detail, we could choose a certain regularization method from L1, L2 and adaptive Lq.

(3) Choose appropriate kernel functions: Based on the intrinsic structure of data, we could choose different kernel functions introduced in Section 20.2.3. In general, if the number of features is much larger than the sample size, or both number of features and the sample size are large, then the linear kernel function would be better. In addition, the Gauss kernel function is generally used in cases where the number of features is much less than the sample size.