○ Scalability: Naïve Bayes also does not clutter feature space and is capable of handling a large number of independent variables or features, or in other words, a giant list of words as in text classification.

○ Robustness to noise: It performs well with noisy data and irrelevant features, minimizing the risk of overfitting.

# • Limitations:

○ Assumption of conditional independence: Although feature independence assumption is always assumed in most of the NLP tasks, it can actually cause more harm than good because it rarely holds true in most of the cases.

○ Sensitivity to feature dependencies: Naïve Bayes may fail to model feature dependencies, hence has poor relation between features which hampers performance of tasks that involve high degree of feature interdependencies.

○ Limited expressiveness: However, Naïve Bayes has a relatively low complexity, and thus it may not find complex dependencies and patterns in data as good as more complicated algorithms, which may affect the model’s performance in the tasks that require high precision/ recall.

Overall, Naïve Bayes is easy to implement, is computationally efficient and can work well in large-scale problems of NLP, but sometimes due to its assumption of independence of features, it may not perform that well in problems where there are interactions between these features.

# Question 10: How does Naïve Bayes perform in comparison to other classification algorithms in NLP?