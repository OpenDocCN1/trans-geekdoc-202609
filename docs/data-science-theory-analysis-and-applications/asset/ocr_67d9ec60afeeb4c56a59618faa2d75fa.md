data type specifications were performed. The loaded data contained 100,005 ratings, with timestamp, genre, and tags as the only variables. The tag variable was the only variable used in learning and classification. The tags were categorized into positive and negative followed by being appended to each other in accordance and stored into already-created empty lists. The modeling scheme designated 75% of data to a training set and the rest to validation.

# 13.4.3 Evaluation Measures

The performance metrics used to evaluate the two algorithms were based on the classical confusion matrix experiment and computations. The matrix presented in Table 13.3 contains counts of sentiment instances correctly classified and misclassified. The performance of the models was evaluated based on TP, True Negative (TN), False Positive (FP), and False Negative (FN). The TP is the count of the number of correctly predicted sentiments [43]. That is, the model predicts the actual positive sentiments correctly. The number of actual positive sentiments predicted as negative constitute the FN measure, while the number of negative sentiments predicted or classified as positive sentiments constitute the FP measure [43]. Finally, the number of negative sentiments correctly predicted is the TN measure.

From the confusion matrix table, metrics such as precision, recall, F-measure, and accuracy can be computed. The definition and computational formula for each of the metrics are discussed as follows.

**Precision:** It refers to the ratio between the number of correctly predicted positive sentiments to the sum of correctly predicted positive sentiments and the negative sentiments predicted as positive sentiment [43]. The computation equation is shown as follows.

Precision = TP / (TP + FP)  (13.6)

**Recall:** It is a measure of sensitivity, because it refers to the ratio between correctly classified positive sentiments and the sum of positively classified sentiments and positive sentiments incorrectly classified as negative sentiments [43]. The computation equation is shown as follows.

Recall = TP / (TP + FN)  (13.7)

TABLE 13.3
Confusion Matrix and Model Sentiment Prediction Elements

Predicted Sentiment Class
Positive    Negative
Actual Sentiment Class
Positive    TP      FN
Negative    FP      TN