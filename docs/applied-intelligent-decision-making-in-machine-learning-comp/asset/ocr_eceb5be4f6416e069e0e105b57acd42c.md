# Applied Intelligent Decision Making in Machine Learning

# TABLE 2.3

The LDA Model Evaluation Confusion Matrix and Performance Parameters for Identification of Soybean Aphids, Exoskeletons, and Leaf Spots Using Test Data

| Actual/Predicted | Aphids | Exoskeletons | Leaf Spots |
| --- | --- | --- | --- |
| Aphids | 25 | 0 | 1 |
| Exoskeletons | 0 | 14 | 1 |
| Leaf spots | 3 | 0 | 17 |

| Performance | Aphids | Exoskeletons | Leaf Spots | Macro-Average | Weighted Average |
| --- | --- | --- | --- | --- | --- |
| Support* | 28 | 14 | 19 | 61 | 61 |
| Precision | 0.89 | 1.0 | 0.90 | 0.93 | 0.92 |
| Recall | 0.96 | 0.93 | 0.85 | 0.91 | 0.92 |
| F-score | 0.92 | 0.96 | 0.87 | 0.92 | 0.91 |
| Accuracy | 92% | | | | | |

Note: Refer to Figure 2.8 for details.
* Support is the number of samples in each class.

# Problem

![](bbox=[0.148, 0.483, 0.283, 0.555])

How to classify soybean aphid from exoskeleton and leafspot that have similar color and size?

![](bbox=[0.483, 0.545, 0.853, 0.765])

# Solution

+   * Input features (test data)
* Roundness
* Solidity
* Circularity

![](bbox=[0.318, 0.646, 0.433, 0.712])

FIGURE 2.8 The LDA classification of soybean aphids, exoskeletons, and leaf spots using the dimensionless shape features, such as solidity, roundness, and circularity.

differentiate aphids from the exoskeletons and leaf spots (Sunoj et al., 2017). Another study developed and based on color and size features to classify soybean aphids achieved an aphid count misclassification from -57% (underestimation) to 142% (overestimation) among different cameras and two lighting conditions (Maharloei et al., 2017).