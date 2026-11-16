# ### 3.3 Data splitting

We divided the dataset into training and testing sets using a 70–30% split, where 70% of the data was allocated for training the models and 30% for testing their performance. The splitting of data into these subsets allowed us to evaluate the models’ ability to generalize to new, unseen data. Out of total 1010 records, 707 were given to train the model and the remaining 303 were used for testing.

# ### 3.4 Attribute scaling

To speed up the calculation of the algorithm and to scale the data in a particular range, Standard Scaling is performed. After splitting data, we standardized the numerical attributes using StandardScaler from Scikit-Learn.

# ### 3.5 Machine learning regression models for training

Subsequently, we applied a comprehensive set of regression models to predict Asthma Control Test (ACT) scores based on the preprocessed dataset. These model-specific experiments allow us to provide a broad understanding of each model’s behavior and the impact of hyperparameter tuning on their predictive performance. The K-Nearest Neighbors (KNN) algorithm was examined with a range of neighbor values, making it particularly valuable for applications where nearby data points significantly impact the prediction. Logistic Regression is a widely-used linear model. It offers simplicity and interpretability, which make it an excellent choice for scenarios where the model’s inner workings need to be transparent. Decision Trees, through the adjustment of tree depths and the application of the Gini impurity method, proved to be robust and intuitive, showcasing suitability in contexts where decision-making processes should be easily interpretable. Support Vector Machine (SVM) Regression gives its flexibility in kernel selection, is well-suited for complex, non-linear relationships between attributes. Random Forest (RF) emerged as a robust choice for mitigating overfitting, and is ideal when the prediction requires resistance to noise and variability. Deep Neural Network (DNN) provides valuable insights into complex, data-driven patterns, making it a compelling option for applications where intricate relationships in the data need to be captured. ADA Boost’s ensemble approach combines multiple weak learners and form a strong predictor. That is beneficial when predictive accuracy is utmost. Finally, XGBoost, known for its efficiency, offered a compelling solution for cases where model accuracy is crucial, combining both predictive power and computational speed. This thorough examination allowed us to showcase strengths of each model, enabling more informed choices in real-world applications.

# ### 3.6 Model evaluation

To evaluate the performance of these machine learning regression models, we used a range of evaluation metrics. Each metric provides predictive capabilities of the models, and we used them to compare and evaluate the performance of each algorithm. Table 1 represents various performance metrics we have considered for this research. In the formulas, n represents the total number of samples, Y i represents the actual value of the i-th sample, and Ŷ i represents the predicted value for the i-th sample.

# ## 4 RESULTS

In this section, we present the outcomes of our experiments in predicting Asthma Control Test (ACT) scores using a range of machine learning regression models. These results are illustrated through Tables 2 to 10, that highlight the performance of the models. Our research aims to provide a detailed analysis of the model’s predictive capabilities and their effectiveness in estimating ACT scores.