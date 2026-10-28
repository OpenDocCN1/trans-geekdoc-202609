+   ○ Express words in fixed-sized vectors in a high-dimensional continuous space.
+   ○ Records the relationship between words on semantics so as to translate the text data into more detailed forms.

These representations transform the raw textual data into numerical feature vectors which could be used by the Naïve Bayes classifier for its training and prediction. The vectors correspond to documents, the values of the features stand for information about specific words or word sequences presence, frequency, or significance within the document.

# Question 6: How are probabilities estimated in Naïve Bayes classifiers?

Answer: Naïve Bayes classifiers rely on using probabilities to classify documents - these probabilities are calculated using Bayes’ theorem, whereby by giving a set of features, it is aimed at estimating the probability of a class. Here is a quick explanation of how probabilities are estimated:

+   - **Prior probability (P(class))**: The prior probabilities, used commonly to compute at the start of the learning algorithm, is the simple relative frequency of each class label in the training data.
+   - **Likelihood probability (P(features|class))**: They are used to quantify the likelihood of registering the features when a given class has been hypothesized, based upon the assumption that the features are conditionally independent of each other when the class is known.
+   - **Posterior probability (P(class|features))**: The new likelihood of classes with highlighted features uses Bayes formula of modifying prior probability of the class with the likelihood probability of the features of the classes.