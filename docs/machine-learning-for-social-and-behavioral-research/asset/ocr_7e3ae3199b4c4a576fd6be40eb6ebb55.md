# Disadvantages:

+   * Instability.
* Collinearity presents problems.
* Relatively lower predictive performance.

Just as researchers need to understand the assumptions of linear models, and in what situations these models may not be appropriate, we urge them to not just turn a blind eye and believe decision trees represent a panacea. As we have noted, there are some research contexts for which tree structures are appropriate, and there are underlying assumptions that can be violated. Decision trees should be viewed as complementary to the use of linear models, and in most cases we recommend using both methods to compare and contrast the different theoretical conclusions that they results.

# 5.6.1 Further Reading

+   * For further discussion on the instability of decision trees and how to assess them, see Philipp, Rusch, Hornik, and Strobl (2018).
* A number of tutorials have been written on the use of decision trees for various disciplines. Two that we recommend include King and Resik (2014) and McArdle (2012).
* One topic that was not discussed was the use of decision trees in a number of applications as for imputing data and for creating propensity scores. See Lee, Lesser, and Stuart (2010) for an evaluation of the use of trees for creating propensity scores, and Carrig et al. (2015) for imputing datasets are to be integrated.

# 5.6.2 Computational Time and Resources

Relative to the algorithms that comprise the following chapter, decision trees are relatively quick to fit, even when paired with cross-validation or the assessment of stability. Similarly to regularized regression, decision trees often take on the order of seconds or a few minutes to fit. The runtime is mainly influenced by the number of predictors, and number of possible cutpoints on each predictor. Predictors that are continuous and contain a large number of unique values, along with predictors coded as nominal (requiring one vs.), drastically increase the runtime.