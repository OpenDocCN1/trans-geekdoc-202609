
## Additional exercise 6.3

As the NA values in `votesTib` include abstention, recode these values into the value `"a"` and cross-validate a naive Bayes model including these values. Does this improve performance?

## Additional exercise 6.4

Perform another random search for the best SVM hyperparameters using nested cross-validation. This time, limit your search to the linear kernel (so no need to tune degree or gamma), search over the range 0.1 and 100 for the cost hyperparameter, and increase the number of iterations to 100. WARNING: This took nearly 12 minutes to complete on my machine!

## 6.8 Summary

- The naive Bayes and support vector machine (SVM) algorithms are supervised learners for classification problems
- Naive Bayes uses Bayes' rule (defined in chapter 5) to estimate the probability of new data belonging to each of the possible output classes
- The SVM algorithm finds a hyperplane (a surface with one fewer dimensions than there are predictors) which best separates the classes
- While naive Bayes can handle both continuous and categorical predictor variables, the SVM algorithm can only handle continuous predictors
- Naive Bayes is computationally cheap, while the SVM algorithm is one of the most expensive algorithms
- The SVM algorithm can use kernel functions to add an extra dimension to the data that helps find a linear decision boundary
- The SVM algorithm is sensitive to the values of its hyperparameters, which must be tuned to maximize performance
- The mlr package allows parallelization of intensive processes, such as hyperparameter tuning, by using the parallelMap package

## 6.9 Solutions to exercises

1. Use the `map_dbl()` function to count the number of "y" values in each column of `votesTib`

    ```r
    map_dbl(votesTib, ~ length(which(. == "y")))
    ```

2. Extract the prior probabilities and likelihoods from your naive Bayes model

    ```r
    getLearnerModel(bayesModel)

    # the prior probabilities are 0.61 for democrat and 0.39 for republican (at the time these data were collected)

    # the likelihoods are shown in 2x2 tables for each vote
    ```

3. Recode the NA values from the `votesTib` tibble and cross-validate a model including these values.

    ```r
    votesTib[] <- map(votesTib, as.character)

    votesTib[is.na(votesTib)] <- "a"

    votesTib[] <- map(votesTib, as.factor)

    votesTask <- makeClassifTask(data = votesTib, target = "Class")

    bayes <- makeLearner("classif.naiveBayes")

    kFold <- makeResampleDesc(method = "RepCV", folds = 10, reps = 50,
                               stratify = TRUE)

    bayesCV <- resample(learner = bayes, task = votesTask, resampling = kFold,
                        measures = list(mmce, acc, fpr, fnr))

    bayesCV$aggr

    # only a very slight increase in accuracy
    ```

4. Perform a random search, restricted to the linear kernel, tuning over a larger range of values for the cost hyperparameter.

    ```r
    svmParamSpace <- makeParamSet(
      makeDiscreteParam("kernel", values = "linear"),
      makeNumericParam("cost", lower = 0.1, upper = 100))

    randSearch <- makeTuneControlRandom(maxit = 100)

    cvForTuning <- makeResampleDesc("Holdout", split = 2/3)

    outer <- makeResampleDesc("CV", iters = 3)

    svmWrapper <- makeTuneWrapper("classif.svm", resampling = cvForTuning,
                                  par.set = svmParamSpace,
                                  control = randSearch)

    parallelStartSocket(cpus = detectCores())

    cvWithTuning <- resample(svmWrapper, spamTask, resampling = outer) # ~12 min

    parallelStop()

    cvWithTuning
    ```

- What are decision trees?
- Using the recursive partitioning algorithm to predict animal classes
- An important weakness of decision trees

There's nothing like the great outdoors. I live in the countryside, and when I walk my dog in the woods I’m reminded just how much we rely on trees. Trees produce the atmosphere we breathe, create habitats for wildlife, provide us with food, and are surprisingly good at making predictions. Yes, you read that right: trees are good at making predictions. But before you go asking the birch in your back garden for next week’s lottery numbers, I should clarify that I’m referring to several supervised learning algorithms that use a branching tree structure. This family of algorithms can be used to solve both classification and regression tasks, can handle continuous and categorical predictors, and are naturally suited to solving multi-class classification problems.

> Remember that a predictor variable is a variable we believe may contain information about the value of our outcome variable. Continuous predictors can have any numeric value on their measurement scale, while categorical variables can have only finite, discrete values/categories.

The basic premise of all tree-based classification algorithms is that they learn a sequence of questions that separates cases in different classes. Each question has a binary answer, and cases will be sent down the left or right branch, depending on which criteria they meet. There can be branches within branches, and once the model is learned, it can be graphically represented as a tree. Have you ever played the game 20 Questions where you have to guess what object someone

![](img/a22105d68c35e8d5bd3c7bafb4644881_177_0.png)

This all seems simple so far. But in the simplistic example above, we could have constructed this ourselves by hand (in fact, I did!). So tree-based models aren’t necessarily learned by machine learning. A decision tree could be a decided-upon HR process for dealing with disciplinary action, for example. You could have a tree-based approach to deciding which flights to buy (is the price above your budget, is the airline reliable, is the food terrible, and so on). So how can we learn the structure of a decision tree automatically for complex datasets with many features? Enter the rpart algorithm.

> Tree-based models can be used for both classification and regression tasks, so you may see them described as classification and regression trees (CART). However, CART is a trademarked algorithm whose code is proprietary. The rpart algorithm is simply an open source implementation of CART. You’ll learn how to use trees for regression tasks in chapter 12.

At each stage of the tree-building process the rpart algorithm considers all of the predictor variables and selects the predictor that does the best job of discriminating the classes. It starts at the root, and then at each branch looks again for the next feature that will best discriminate the classes of the cases that took that branch. But how does rpart decide on the best feature at each split? There are a few different ways this can be done, and rpart offers you two approaches: the difference in entropy (called the information gain) and the difference in Gini index (called the Gini gain). The two methods usually give very similar results, but the Gini index (named after the sociologist and statistician Corrado Gini) is slightly faster to compute and so we’ll focus on this.

> The Gini index is the default method rpart uses to decide how to split the tree. If you're concerned you're missing the best-performing model, you can always compare Gini index and entropy during hyperparameter tuning.

In this section, I'll show you how Gini gain is calculated to find the best split for a particular node when growing a decision tree. Entropy and the Gini index are two ways of trying to measure the same thing: impurity. Impurity is a measure of how heterogenous the classes are within a node.

> If a node contains only a single class (which would make it a leaf), it would be said to be pure.

By estimating the impurity (with whichever method you choose) that would result from using each predictor variable for the next split, the algorithm can choose the feature that will result in the smallest impurity. Put another way, the algorithm chooses the feature that will result in subsequent nodes that are as homogenous as possible.

So what does the Gini index look like? Have a look at the example split in figure 7.2. We have 20 cases in a parent node belonging to two classes, A and B. We split the node into two leaves based on some criterion. In the left leaf we have 11 cases from class A and 3 from class B. In the right leaf we have 5 from class B and 1 from class A.

![](img/a22105d68c35e8d5bd3c7bafb4644881_178_0.png)

We want to know what the Gini gain of this split is. The Gini gain is the difference between the Gini index of the parent node, and the Gini index of the split. Looking at our example in figure 7.2, the Gini index for any node is calculated as:

```
Gini index = 1 - (p(A)^2 + p(B)^2)
```
