of that class from all the other classes. The class having the highest probability from all the classifiers is chosen.

+   - **One-vs.-one (OvO)**: Uses a binary classifier for every pair of classes, each of which gives its vote for the class that they are looking for. In the case of all the classifiers, the class that received the highest votes is chosen.

+   - **Multinomial Naïve Bayes**: Built for the scheme of multiclass classification, particularly for use with textual data. As a probability estimator, it estimates the probability of occurrence of each feature (word or token) in each class and uses the multinomial distribution to compute class probabilities.

Although Naïve Bayes is not nearly as complex as some other multiclass classification algorithms, it can be adequate once more; this is the case when the features are well-separated by class to a high degree or when computational time is a critical factor.

# **Question 9**: What are the advantages and limitations of Naïve Bayes in NLP?

Answer: The advantages and limitations of Naïve Bayes in NLP are:

+   **Advantages**:
+   - **Simplicity**: Naïve Bayes is simple and fast to implement and comprehend for any developer or data scientist, also the training and testing phase is simpler.

+   - **Efficiency**: Due to the fact that this approach is computationally efficient, it is ideal for large datasets or processes that need to take place in real time.