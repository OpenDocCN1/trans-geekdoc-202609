+   - **Large number of features with limited samples**: SVMs can handle situations with a large number of features, but feature selection may still be necessary.
+   - **Ease of use and flexibility**: If one wants a fast solution in terms of the development of a prototype or simply better usability, then this is where logistic regression or decision tree models would be better.
+   - **Online learning**: SVMs cannot be used to continuously update the model by incorporating new data; for online learning we have stochastic gradient descent, etc.

# Model evaluation

Model evaluation for classification is the generally used statistical measure to determine the number of correct classification made by the classification models. It is performed using the validity evaluation metrics such as accuracy, precision, recall, F1 score, and the AUC on the unseen data. The evaluation of models is vital because of its ability to determine the general performance of the model and not only the performance when operated on the training set. This knowledge is crucial in ML to make an informed choice of the selection and tuning of models, as well as, deciding whether to deploy a new, a modified, or the existing model to avoid unreliable or weak predictive systems.

# Question 1: What is overfitting in supervised learning, and how can it be prevented?

**Answer:** Overfitting is a situation where a given model performs well on the training data and is poor on the testing data. This states that the model is not anymore a general model but specifically influenced by the training data it tries to mimic an outcome while predicting.