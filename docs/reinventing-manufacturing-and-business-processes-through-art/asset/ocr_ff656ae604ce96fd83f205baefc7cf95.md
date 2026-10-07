# Reinventing Processes Through AI

$Precision = \frac{TP}{TP + FP}$

+   - F-measure: A measure that integrates recall value and precision value. It is said to be the harmonic mean of recall and precision values.

$F - measure = 2 \times \frac{Precision \times Recall}{Precision + Recall}$

+   - mRHR: A metric used to evaluate the ranking of the recommended product by the model when there exist multiple preferences for the customer.

$mRHR = \frac{1}{preferences} \times \frac{\sum_{i=1}^N hit}{rank}$

Where hit is if the customer prefers the predicted product by the model. Rank is the position of the preferred product.

To achieve experimental results, this survey analyzes the customer behavior of data using various techniques that include machine learning as logical regression, naive Bayes, SVM, decision tree, random Forest and neural networks using a predictive model to segment customers and forecast the shopping menu. The comparison of the ML algorithms is made using performance evaluation factors such as F-measure and mRHR. Table 5.1 shows that SVM gives the best result with 0.345 of F-measure and 0.120 of mRHR in an individual-level approach. LR exhibited the best result in the segment-level approach, with an F-measure of 0.355 and

# TABLE 5.1
Comparison of Customer Behavior Modeling Using Various ML Algorithms

| Individual-Level Approach |
| ML Algorithm | F-measure Value | mRHR Value |
| Logistic regression | 0.328 | 0.100 |
| Decision tree | 0.329 | 0.107 |
| Random forest | 0.337 | 0.112 |
| Support vector machine | 0.345 | 0.120 |
| Neural network | 0.314 | 0.102 |

| Segment-Level Approach |
| ML Algorithm | F-measure Value | mRHR Value |
| Logistic regression | 0.355 | 0.124 |
| Decision tree | 0.33 | 0.112 |
| Random forest | 0.315 | 0.109 |
| Support vector machine | 0.322 | 0.113 |
| Neural network | 0.293 | 0.092 |