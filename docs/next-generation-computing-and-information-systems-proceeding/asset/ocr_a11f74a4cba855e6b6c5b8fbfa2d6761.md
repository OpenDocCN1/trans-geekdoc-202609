So, Logistic Regression formula is given by:

ln ( P / 1 - P ) = b₀ + b₁x  (7)
=> P = e^(b₀+b₁x) / 1 + e^(b₀+b₁x)  (8)

# 4.8 Naïve Bayes algorithm

The Naïve Bayes technique is a probabilistic classification approach frequently used in machine learning for classification difficulties, such as text categorization, spam detection, sentiment analysis, and others (Rincy and Gupta 2020). Bayes's Theorem may be expressed in a straightforward mathematical manner as follows:

P(A|B) = P(B|A) * P(A) / P(B)  (9)

The marginal probability of an occurrence, P(A), is termed the prior, and the probability we're interested in, P(A|B), is called the posterior.

# 4.9 Soft voting ensemble

The decisions of numerous classifiers are combined using the multiple classifiers voting technique. It involves creating a classifier for each of the smaller, equal subsets of the training dataset that are created. Soft voting has been used in which the individual models' predictions are weighted based on their confidence scores, and the final prediction is made by considering these weighted contributions. The accuracy of these classifiers has been improved when voting is applied to classification algorithms(Rincy and Gupta 2020).

# 5 RESULT AND DISCUSSION

We used the Ensemble Learning approach, where we used multiple models for classifying glasses according to their categories. As a result of this study, we found an accuracy of 95.29% using the Ensemble method for the glass dataset.

Multiple studies show that using multiple classifiers on a dataset yields far better results. Therefore, the classification decision is based on the combined outputs of numerous models, making it more accurate than using a single classifier to identify the glass type.

Using data on the glass's elemental composition and refractive index, we trained several machine learning algorithms to make an identification. We used five different machine learning methods.

Table 2 below details the precision of the various machine-learning models used in the ensemble method. Random Forest was the best model for making predictions in this data set, achieving an accuracy of 96.92%. Ensemble voting yielded an accuracy of 95.29 percent.

Table 2. Classification accuracy details in glass dataset.

| Model | Accuracy | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- | :--- |
| K-Nearest-Neighbor | 89.23% | 86% | 86% | 85% |
| Support Vector Machine | 83.85% | 98% | 95% | 96% |
| Gaussian Naïve Bayes | 72.31% | 78% | 72% | 72% |
| Logistic Regression | 93.85% | 96% | 94% | 95% |
| **Random Forest** | **96.92%** | **99%** | **98%** | **99%** |
| Ensemble Voting | 95.29% | 96% | 95% | 96% |