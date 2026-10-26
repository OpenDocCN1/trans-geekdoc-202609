# 2.8 Summary of learning algorithms

It is natural to ask which learning algorithm is best, but the answer depends on what characteristics are important to the problem you are trying to solve.

**Naïve Bayes** *Pros:* easy to implement; estimation is fast, requiring only a single pass over the data; assigns probabilities to predicted labels; controls overfitting with smoothing parameter. *Cons:* often has poor accuracy, especially with correlated features.

**Perceptron** *Pros:* easy to implement; online; error-driven learning means that accuracy is typically high, especially after averaging. *Cons:* not probabilistic; hard to know when to stop learning; lack of margin can lead to overfitting.

**Support vector machine** *Pros:* optimizes an error-based metric, usually resulting in high accuracy; overfitting is controlled by a regularization parameter. *Cons:* not probabilistic.

**Logistic regression** *Pros:* error-driven and probabilistic; overfitting is controlled by a regularization parameter. *Cons:* batch learning requires black-box optimization; logistic loss can “overtrain” on correctly labeled examples.

One of the main distinctions is whether the learning algorithm offers a probability over labels. This is useful in modular architectures, where the output of one classifier is the input for some other system. In cases where probability is not necessary, the support vector machine is usually the right choice, since it is no more difficult to implement than the perceptron, and is often more accurate. When probability is necessary, logistic regression is usually more accurate than Naïve Bayes.

# Additional resources

A machine learning textbook will offer more classifiers and more details (e.g., Murphy, 2012), although the notation will differ slightly from what is typical in natural language processing. Probabilistic methods are surveyed by Hastie et al. (2009), and Mohri et al. (2012) emphasize theoretical considerations. Bottou et al. (2016) surveys the rapidly moving field of online learning, and Kummerfeld et al. (2015) empirically review several optimization algorithms for large-margin learning. The python toolkit SCikit-learn includes implementations of all of the algorithms described in this chapter (Pedregosa et al., 2011).

Appendix B describes an alternative large-margin classifier, called **passive-aggressive**. Passive-aggressive is an online learner that seeks to make the smallest update that satisfies the margin constraint at the current instance. It is closely related to MIRA, which was used widely in NLP in the 2000s (Crammer and Singer, 2003).