
Luck isn’t what’s behind the result — it’s simply the *law of large numbers* in action (see more at [`https://en.wikipedia.org/wiki/Law_of_large_numbers`](https://en.wikipedia.org/wiki/Law_of_large_numbers)). Even though an individual has a slightly more than 50 percent chance of getting the right answer, the guess is better than a random choice. By cumulating more and more guesses, the overall distribution of answers will finally resemble that slim chance of getting the right answer (you get a prevalence of correct answers), which is enough to obtain the right prediction if you pick the most frequent choice or average them. You can employ such an apparently incredible fact (yet founded on solid statistical theory) in many practical ways, such as for consensus forecasts in economics and political sciences. It also applies in machine learning, where it powers effective learning ensembles such as the Random Forests algorithm.

![Remember](images/remember.png)You don’t have to type the source code for this chapter manually. In fact, using the downloadable source is a lot easier. You can find the source for this chapter in the `ML4D2E` folder of the downloadable source for Python code and the `ML4D2ER` folder of the downloadable source for the R code. The example files for this chapter will begin with `ML4D2E; 16;` (for Python) or `ML4D2E_R; 16;` (for R). See the Introduction for details on how to find these source files.

## Leveraging Decision Trees

Ensembles are based on a recent idea (formulated around 1990), but they leverage older tools, such as decision trees, which have been part of machine learning since 1950. As covered in [Chapter 10](#c10.xhtml), decision trees at first looked quite promising and appealing to practitioners because of their ease of use and understanding. After all, a decision tree can easily do the following:

*   Handle mixed types of target variables and predictors, with very little or no feature preprocessing (missing values are handled almost automatically if you replace them with an unusually high or low value)

*   Ignore redundant features and select only the relevant features

*   Work out-of-the box, with no complex hyper-parameters to fix and tune

*   Visualize the prediction process as a set of recursive rules arranged in a tree with branches and leaves, thus offering ease of interpretation

Given the range of positive characteristics, you may wonder why practitioners slowly started distrusting this algorithm after a few years. The main reason is that the resulting models often have high variance in the estimates.

To grasp the critical problem of decision trees better, you can consider the problem visually. Think of the tricky situation of the bull's-eye problem that requires a machine learning algorithm to approximate nonlinear functions (as neural networks do) or to transform the feature space (as when using linear model with polynomial expansion or kernel functions in support vector machines). [Figure 16-1](#c16.xhtml#c16-fig-0001) shows the squared decision boundary of a single decision tree (on the left) as compared to an ensemble of decision trees (on the right).

![FIGURE 16-1: Comparing a single decision tree output (left) to an ensemble of decision trees (right).](images/9781119724018-fg1601.png)

[FIGURE 16-1:](#c16.xhtml#rc16-fig-0001) Comparing a single decision tree output (left) to an ensemble of decision trees (right).

Decision trees partition the feature space into delimited areas and then use such areas for classification or regression purposes. When the decision boundary that separates classes in a bull’s-eye problem is an ellipse, decision trees can approximate it by combining a certain number of areas.

Even if a decision tree performs fine in separating two classes, it may be easily at fault on the test set at the boundaries between the two classes. In fact, in proximity of the boundary, things are often quite different from how they appear in the training set. The decision boundary of the decision tree is very imprecise and its shape is extremely rough and squared. The issue is clearly visible on bidimensional problems. Bidimensionality leads to imprecise estimates and overfitting, which decisively worsen as feature dimensions increase and in the presence of noisy observations (observations that are somehow randomly scattered around the feature space). But you can improve decision trees using some interesting heuristics that stabilize results from trees:

*   Keep only the correctly predicted cases to retrain the algorithm

*   Build separate trees for misclassified examples

*   Simplify trees by pruning the less effective rules

Apart from these heuristics, the best trick is to build multiple trees using different samples, then compare and average their results. The example in [Figure 16-1](#c16.xhtml#c16-fig-0001), shown previously, indicates that the benefit is immediately visible. As you build an ensemble of more trees, the decision boundary gets smoother, slowly resembling the hypothetical target shape of the class separator.

### Growing a forest of trees

Improving a decision tree by replicating it many times and averaging results to get a more general solution sounded like such a good idea that it spread, and both academics and practitioners derived various solutions. When the problem is a regression, the technique averages results from the ensemble. However, when the trees deal with a classification task, the technique can use the ensemble as a voting system, choosing the most frequent response class as an output for all its replications. The following sections discuss how using trees for an ensemble creates a superior solution.

#### Creating the Random Forests ensemble

![Tip](images/tip.png)When using an ensemble for regression, the standard deviation, calculated from all the ensemble’s estimates for an example, can provide you with an estimate of how confident you can be about the prediction. The standard deviation shows how good the mean of the estimates is. For classification problems, the percentage of trees predicting a certain class is indicative of the level of confidence in the prediction, but you can’t use it as a probability estimate because it’s the outcome of a voting system.

Deciding on how to compute the solution of an ensemble happened quickly; finding the best way to replicate the trees in an ensemble required more research and reflection. The first solution is *pasting,* that is, sampling a portion of your training set. Initially proposed by Leo Breiman, pasting reduces the number of training examples, which can become a problem for learning from complex data because you get fewer examples to feed to the learning algorithm. It shows its usefulness by reducing the learning sample noise (sampling fewer examples reduces the number of outliers and anomalous cases). After pasting, Professor Breiman also tested the effects of *bootstrap sampling* (sampling with replacement), which not only leaves out some noise (when you bootstrap, on average you leave out 37 percent of your initial example set) but also, thanks to sampling repetition, creates more variation in the ensembles, improving the results. This technique is called *bagging* (also known as *bootstrap aggregation*).

![Remember](images/remember.png)Bootstrapping appears in [Chapter 9](#c09.xhtml) as part of validation alternatives. In bootstrapping, you sample the examples from a set to create a new set, allowing the code to sample the examples multiple times. Therefore, in a bootstrapped sample, you can find the same example repeated from one to many times.

Breiman noticed that results of an ensemble of trees improved when the trees differ significantly from each other (statistically, we say that they’re *uncorrelated*), which leads to the last technique of *transformation* — the creation of mostly uncorrelated ensembles of trees using different subsets of features.
