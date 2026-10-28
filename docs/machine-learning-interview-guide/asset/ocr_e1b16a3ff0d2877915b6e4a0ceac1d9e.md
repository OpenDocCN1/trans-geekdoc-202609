weighted sum for each class, which is then passed through the softmax function to convert these sums into probabilities.

+   - **Softmax function**: The softmax function converts the weighted sum into probabilities and the probabilities of each class of examples sum to 1. The probability of each class is stored in the vector at the specific position as the index of the class.
+   - **Prediction**: The class with the maximum probability is considered as the output for the given set of features.
+   - **Training**: The preceding model is learnt in a manner such as maximum likelihood estimation. In particular, the purpose of the training is the optimization of weights and biases to match the class label likelihood of training data.

Multinomial logistics regression is common in cases of classification problems with more classes like image recognition, natural language processing, and medical diagnosis. It extends binary logistic regression to allow for classification into multiple classes.

# Question 11: Describe softmax regression and its role in multiclass classification.

Answer: Softmax regression, also called multinomial logistic regression, is an extension of the binary logistic regression in which the output is a probability of any of the k classes instead of one class. Most often, it is utilized in multiclass classification, a problem in which the main purpose is to estimate the probability of the occurrence of each class for the given input.

Here is a brief overview of softmax regression and its role in multiclass classification: