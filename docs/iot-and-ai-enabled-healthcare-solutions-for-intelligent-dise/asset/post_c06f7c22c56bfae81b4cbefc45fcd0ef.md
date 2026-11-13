
![](img/a797255277085a0fa8aa2736cb720e31_50_0.png)

Fig. 3. Correlation between features and target variable.

studying features, and area information to build strong predictive models. Properly deciphering and using correlation can significantly enhance the effectiveness of facts-driven decision-making strategies. Figure 3 represents the relation among all the features with each other.

### 1.3.1.2 K-Nearest Neighbor

From many Machine Learning Algorithms, KNeighbors Classifier is used to classify the data, giving us maximum accuracy. It is a machine learning algorithm provided by the sci-kit-learn library in Python, used for classification tasks. It is based on the k-nearest neighbors algorithm (k-NN), which is a type of instance-based learning.

The K-Nearest Neighbors (kNN) algorithm is a fundamental and intuitive machine learning technique used for both classification and regression tasks. It operates on the principle that data points with comparable traits tend to be near each other within the feature space. During prediction, kNN calculates the distance among the new instance and all the instances in the training dataset by using the designated distance metric such as Euclidean distance. It then identifies the closest neighbors and makes a prediction primarily based on their majority class (for classification) or average value (for regression). The simplicity and effectiveness of kNN make it a popular choice for numerous applications, which include image classification, recommendation systems, and predicting continuous outcomes like house prices.

However, kNN has a few challenges and considerations that need to be addressed for optimal performance. The choice of k is important: a small k may cause noisy predictions, while a large k might overlook local patterns. Cross-validation can help determine the optimal k value. Additionally, kNN is computationally intensive, particularly with large datasets, because it requires distance calculations for every example in the training set. Feature scaling is also crucial because kNN is based on distance metrics, and features with larger scales can disproportionately influence the results. Despite those challenges, with proper tuning and preprocessing, kNN may be a powerful tool for many machine learning tasks. In this research, I have applied the KNN algorithm to achieve nearly accurate results.

After data preprocessing, the minimum error for a certain number of neighbors is calculated. Finding the correct neighbors in the K-Nearest Neighbors (KNN) algorithm is critical because the algorithm’s predictions are based on these neighbors’ characteristics. Correct neighbor identification directly impacts the model’s classification or regression accuracy as the prediction is based on these neighbors’ majority class or average values. Misidentifying neighbors can lead to wrong predictions and badly impact the performance of the model. Distance metric and proper feature scaling are important to get meaningful distance calculation, which determines the correct neighbors.

In Fig. 4, K is the number of neighbors required to give the minimum error. From the graph we can see the first minimum is at k = 3.

Minimum error: 0.02666666666666667 at K = 3

![](img/a797255277085a0fa8aa2736cb720e31_51_0.png)

Fig. 4. Error at different values.

### 1.3.1.3 Measuring Accuracy

A confusion matrix is a key tool to evaluate a classification model. It gives you a breakdown of the model’s predictions so you can see the accuracy, precision, recall and other metrics in detail in Table 5.

- **True Positives (TP):** Where it finds out the exact position of class.
- **True Negatives (TN):** Where it finds out the negative nature of class.
- **False Positives (FP):** Where it finds out the negative class as positive.
- **False Negatives (FN):** Where it finds out the positive class as negative.

The Confusion Matrix has the following metrics in the classification report: accuracy, precision, recall, F1-score, and specificity. Accuracy is the percentage of values that were expected. Precision is the percentage of positive values that were correctly predicted. The recall can be described as the proportion of true positives and all positively forecasted cases while precision is the percentage of perfect positive forecasts among all positively anticipated instances. F1-Score is the Harmonic mean of precision and recall. The specificity represents the proportion of truly recognized negatives to actual negatives.

**Table 5. Structure of confusion matrix.**

| | Positive Prediction | Negative Prediction |
|---|---|---|
| Actually Positive | TP = 48 | FN = 0 |
| Actually Negative | FP = 2 | TN = 25 |

### 1.3.1.4 Classification Report

The Classification report is crucial for evaluating the effectiveness of a classification model across different classes. It helps to identify which classes the model is performing well on and which classes it struggles with, guiding further enhancements and tuning of the model. For instance, high precision but low recall is considered for a class suggests the model is conservative in predicting class, likely lacking some actual positives. Conversely, note that low precision suggests the model captures most positives but also includes many false positives. By inspecting these metrics, data scientists can gain a deeper understanding of their model’s strengths and weaknesses, ensuring better decision-making in model selection and optimization. In Table 6, there is a classification report corresponding to the dataset after applying the K-Nearest Neighbor Algorithm to the Cardiovascular disease dataset.

This algorithm has an accuracy score of 97% which is a significant value, making it outperform other classification algorithms.

**Table 6. Classification report.**

| | Precision | Recall | F1-score | Support |
|---|---|---|---|---|
| 0 | 0.96 | 1.00 | 0.98 | 48 |
| 1 | 1.00 | 0.93 | 0.96 | 27 |
| Accuracy | | | 0.97 | 75 |
| Macro avg | 0.98 | 0.96 | 0.97 | 75 |
| Weighted avg | 0.97 | 0.97 | 0.97 | 75 |

## 1.4 Conclusion

Machine Learning is revolutionizing the field of cardiovascular diseases by permitting early detection, customized remedies, and improved risk stratification. Advanced ML algorithms can examine tremendous quantities of data from electronic health records, imaging, and genetic profiles, identifying patterns that might not be discernible through traditional methods. This functionality permits the identification of early symptoms of diseases, facilitating timely intervention and potentially improving patient outcomes. Moreover, ML–driven predictive analytics can tailor remedy plans to individual patients’ unique risk factors, thereby improving the effectiveness of interventions and reducing detrimental consequences. Machine learning techniques applied to identify cardiovascular disease offer a great deal in improving patient outcomes and reducing mortality rates. By understanding different relevant risk factors and patterns in patients’ data through algorithms, doctors can have more accurate and timely diagnoses, thus making it easier for better treatment plans to be employed resulting in improved outcomes for patients with cardiovascular diseases. According to this research, the K-Nearest neighbor algorithm can predict the presence of cardiovascular illness with high accuracy. This could completely change cardiovascular care by leading to personalized therapies, and earlier detection by machine learning algorithms for clinical practice in the future.

Despite its capacity, the combination of Machine Learning algorithms with cardiovascular diseases comes with significant challenges. Ensuring the quality and variety of datasets while preserving patient privacy and data security is vital. Additionally, the interpretability of machine learning models is essential for gaining the trust of both healthcare professionals and patients. Seamless integration into clinical workflows and addressing ethical concerns, which include biases in Machine Learning models and equitable access to innovations, are also vital for the considerable adoption of ML in cardiology. Moving forward, interdisciplinary collaboration, advancements in algorithms, and clear regulatory frameworks might be key to harnessing the total potential of ML in improving cardiovascular health outcomes.
