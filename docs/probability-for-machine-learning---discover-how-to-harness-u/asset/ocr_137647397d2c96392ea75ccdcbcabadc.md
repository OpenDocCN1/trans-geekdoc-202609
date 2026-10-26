Any system that classifies new instances according to [the equation] is called a Bayes optimal classifier, or Bayes optimal learner. No other classification method using the same hypothesis space and same prior knowledge can outperform this method on average.

— Page 175, *Machine Learning*, 1997.

We have to let that sink in. It is a big deal. It means that any other algorithm that operates on the same data, the same set of hypotheses and same prior probabilities cannot outperform this approach, on average. Hence the name *optimal classifier*. Although the classifier makes optimal predictions, it is not perfect, given the uncertainty in the training data and incomplete coverage of the problem domain and hypothesis space. As such the model will make errors. This error are often referred to as Bayes error.

The Bayes classifier produces the lowest possible test error rate, called the Bayes error rate. [...] The Bayes error rate is analogous to the irreducible error ...

— Page 38, *An Introduction to Statistical Learning with Applications in R*, 2017.

Because the Bayes classifier is optimal, the Bayes error is the minimum possible error that can be made on a dataset.

+   - **Bayes Error**: The minimum possible error that can be made when making predictions.

Further, the model is often described in terms of classification, e.g. the *Bayes Classifier*. Nevertheless, the principal applies just as well to regression, that is predictive modeling problems where a numerical value is predicted instead of a class label. It is a theoretical model, but it is held up as an ideal that we may wish to pursue.

In theory we would always like to predict qualitative responses using the Bayes classifier. But for real data, we do not know the conditional distribution of Y given X, and so computing the Bayes classifier is impossible. Therefore, the Bayes classifier serves as an unattainable gold standard against which to compare other methods.

— Page 39, *An Introduction to Statistical Learning with Applications in R*, 2017.

Because of the computational cost of this optimal strategy, we instead can work with direct simplifications of the approach. Two of the most commonly used approaches are using a sampling algorithm for hypotheses such as Gibbs sampling, or to use the simplifying assumptions of the Naive Bayes classifier.

+   - **Gibbs Algorithm**. Randomly sample hypotheses biased on their posterior probability.
+   - **Naive Bayes**. Assume that variables in the input data are conditionally independent.

Nevertheless, many nonlinear machine learning algorithms are able to make predictions are that are close approximations of the Bayes classifier in practice.

Despite the fact that it is a very simple approach, KNN can often produce classifiers that are surprisingly close to the optimal Bayes classifier.

— Page 39, *An Introduction to Statistical Learning with Applications in R*, 2017.