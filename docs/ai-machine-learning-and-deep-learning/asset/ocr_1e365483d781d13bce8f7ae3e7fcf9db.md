the data was used as a test, set and 70% was used as a training set. Table 19.1 provides an overview of the different samples used:

# TABLE 19.1 Data Used for Analysis

|  | TOTAL | PERCENTAGE |
|---|---|---|
| Whole data set | 18,305 | 100.00% |
| Phishing emails | 3,416 | 18.66% |
| Spam emails | 14,889 | 81.34% |
| Training set | 12,813 | 70.00% |
| Test set | 5,492 | 30.00% |

# 19.4 UNDERSTANDING THE DECISION BEHAVIOR OF MACHINE LEARNING MODELS

Since it has been shown that even the best DL/ML phishing detectors should be complemented by attentive email users to improve the detection rate, two different frameworks for interpreting ML classification models are presented.

# 19.4.1 Interpreter for Machine Learning Algorithms

In the paper “‘Why Should I Trust You?’ Explaining the Predictions of Any Classifier,” Ribeiro et al. [44] introduced methods to explain the decision behavior of ML models. People encounter ML in their daily lives, for example, for unlocking their smartphone by face recognition. Without knowledge about how these tools and applications work, it is difficult to trust their behavior and decisions [10], especially when they behave in unexpected ways, such as not recognizing the face or providing unusual recommendations. People do not use applications they do not trust, and they do not trust applications they do not understand [44]. To solve this problem in classification tasks, Ribeiro et al. [44] developed local interpretable model-agnostic explanations (LIME) and anchor explanations to provide easily understandable representations of the decision behavior of any classifier [44, 42].