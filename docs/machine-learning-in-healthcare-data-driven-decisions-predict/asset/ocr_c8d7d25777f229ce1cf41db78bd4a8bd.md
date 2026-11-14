well-generalized linear boundary, which is advantageous in high-dimensional or noisy biomedical data.

The third learner is naïve Bayes, specifically with Laplace (add-one) smoothing, that addresses the zero probabilities problem of categorical features never occurring in any class. For example, some CKD predictors like pus cell clumps or bacteria might never occur in normal patients, causing sparsity in training data. Laplace smoothing guarantees that such rare but clinically important events receive nonzero predictive probabilities, maintaining predictive integrity. These three classifiers work together to make sure that the ensemble is robust against noise, feature correlation, and sparse data while capturing both linear and nonlinear patterns. In order to ensure that misclassified samples are given more weight in the subsequent round, each base learner contributes to the HRAB ensemble proportionate to its own classification error (adaptive boosting concept).

Together with learner diversity, this error-focused re-weighting creates a potent ensemble that can produce high accuracy (e.g., > 98% in internal validation) while preserving efficiency and interpretability. HRAB successfully overcomes the difficulties presented by clinical data, including noise, small sample size, and associated characteristics by including a varied collection of regularized base learners. In addition to improving prediction performance, the strategic design provides a dependable and expandable method for early CKD identification.

# 3.4 Integration of Regularization in Boosting

HRAB’s framework uses regularization penalties during the boosting, bringing an added control over normal AdaBoost that solely adjusts weights by classification error. In clinical use cases such as CKD prediction early, where overfitting and learner instability will heavily damage generalizability as well as clinician trust, this modification is needed. Each boosting step in HRAB considers both the basic learner’s misclassification rate and an instance-specific regularization penalty that accounts for the model complexity and error profile.

The core mechanism of HRAB involves computing a penalty score (§§) for each base learner at iteration i, which is defined as a function of two key components:

+   1. Error rate (εᵢ) – the weighted classification error of the base learner.
+   2. Complexity index (Cᵢ) – a structural measure that varies depending on the learner type. For example:
+      - For decision trees: depth or total number of leaf nodes.
+      - For logistic regression: number of nonzero coefficients (sparsity).
+      - For naïve Bayes: variance in probability estimates.