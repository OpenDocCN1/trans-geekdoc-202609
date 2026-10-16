
![](img/d94e4cd766940d79abed0bc6ba4e4344_183_0.png)

We see that we have a lot of similar outcomes. 5-NN appears to win on three folds, while GNB wins on one. The others are visual ties. We would be unable to do this sort of “who won” comparison on stripplots or from calculated means. The stripplot loses the connection to the fold and the mean compresses all the comparative information in the individual folds.

## 5.9 EOC

### 5.9.1 Summary

We have become more sophisticated in the machinery we use to compare different learners: instead of single train-test splits, we make multiple splits. That’s good. We also dove into one of the fundamental theoretical issues in learning: the bias-variance tradeoff. Lastly, we’ve looked at two graphical methods learning curves, complexity curves, and comparing learners across several folds of cross-validation. However, we’re still using only a small toolbox of methods and we’re not really selecting hyperparameters for those methods in a structured way. More to come!

### 5.9.2 Notes

### External Issues in Evaluation

When we build a bridge, we want to make certain that it is safe. We want to ensure that it can handle the weight and wind—the Tacoma Narrows!—that it will experience. Yet, before we even start construction, someone needs

There are many different ways to resample data for evaluation purposes. We discussed cross-validation and repeated train-test splitting (RTTS). RTTS is also called *Monte Carlo cross-validation*. When you see Monte Carlo (a famous gambling town) in a learning or statistical phrase, feel free to substitute the phrase “repeated random rolls.” Here, Monte Carlo refers to the repeated randomness of selecting train-test splits—as opposed to the one-and-done randomness of standard cross-validation. Each of the resampling evaluators is making an estimate of a target quantity. Mind-blowingly enough, this means they themselves have a *bias* and a *variance*. Oh dear, we’ve slipped into the meta world again! If you’d like to learn more, you can start with this mathematically dense paper by Kohavi, “A study of cross-validation and bootstrap for accuracy estimation and model selection.”

There are other, related resampling methods called the *jackknife* and the *bootstrap*. The jackknife is very similar to leave-one-out style evaluation. We’ll discuss bootstrapping in a slightly different context—essentially using repeated sampling *with replacement* to build models—in Section 12.3.1. When we want to account for hyperparameters, we need another level of cross-validation: *nested cross-validation*. We’ll discuss it in Section 11.3.

The quote from *Elements of Statistical Learning* (ESL) is from the first edition, page 196. Likewise, if you’d like to see the details that were swept under the carpet in the bias-variance equation, ESL has those details starting on that same page. Funny, that. Be warned, it is not easy reading. A nice answer on *Cross Validated*—an online statistics and machine learning community—has some useful discussion also: https://stats.stackexchange.com/a/164391/1704.

If you’re wondering why I took the time to hack through using *tsplot*, you can check out the *sklearn* docs example for making a learning curve: http://scikit-learn.org/stable/auto_examples/model_selection/plot_learning_curve.html. Drawing the graph by hand just didn’t interest me for some reason.

### 5.9.3 Exercises

We’ve introduced a number of evaluation techniques. We never compared them directly to each other. Can you directly compare leave-one-out with two-, three-, five-, and ten-fold cross-validation on a learning problem? Do you see any patterns as the number of folds increases?

A quick example of the variance in model estimates is the difference in training (calculating) a mean and a median from a random sample of a larger dataset. Make a small dataset with 20 random values in it. Randomly select 10 of those values and compute the mean and median of the 10 values. Repeat randomly selecting 10 values five times and compute the mean and median. How different are the 5 means? How different are the 5 medians? How do those values compare to the mean and median of the original 20 values?

This page intentionally left blank

## Evaluating Classifiers

```
In [1]:
# setup
from mlwpy import *
%matplotlib inline

iris = datasets.load_iris()

tts = skms.train_test_split(iris.data, iris.target,
    test_size=.33, random_state=21)

(iris_train_ftrs, iris_test_ftrs,
 iris_train_tgt, iris_test_tgt) = tts
```

In the previous chapter, we discussed evaluation issues that pertain to both classifiers and regressors. Now, I’m going to turn our attention to evaluation techniques that are appropriate for classifiers. We’ll start by examining baseline models as a standard of comparison. We will then progress to different metrics that help identify different types of mistakes that classifiers make. We’ll also look at some graphical methods for evaluating and comparing classifiers. Last, we’ll apply these evaluations on a new dataset.

### 6.1 Baseline Classifiers

I’ve emphasized—and the entire previous chapter reinforces—the notion that we must not lie to ourselves when we evaluate our learning systems. We discussed fair evaluation of single models and comparing two or more alternative models. These steps are great. Unfortunately, they miss an important point—it’s an easy one to miss.

Once we’ve invested time in making a fancy—new and improved, folks!—learning system, we are going to feel some obligation to use it. That obligation may be to our boss, or our investors who paid for it, or to ourselves for the time and creativity we invested in it. However, rolling a learner into production use presumes that the shiny, new, improved system is needed. It might not be. Sometimes, simple old-fashioned technology is more effective, and more cost-effective, than a fancy new product.

How do we know whether we need a campfire or an industrial stovetop? We figure that out by comparing against the simplest ideas we can come up with: baseline methods. sklearn calls these dummy methods.

We can imagine four levels of learning systems:

- 1. Baseline methods—prediction based on simple statistics or random guesses,
- 2. Simple off-the-shelf learning methods—predictors that are generally less resource-intensive,
- 3. Complex off-the-shelf learning methods—predictors that are generally more resource-intensive, and
- 4. Customized, boutique learning methods.

Most of the methods in this book fall into the second category. They are simple, off-the-shelf systems. We’ll glance at more complex systems in Chapter 15. If you need boutique solutions, you should hire someone who has taken a deeper dive into the world of machine learning and statistics—like your humble author. The most basic, baseline systems help us decide if we need a complicated system and if that system is better than something primitive. If our fancy systems are no better than the baseline, we may need to revisit some of our fundamental assumptions. We may need to gather more data or change how we are representing our data. We’ll talk about adjusting our representation in Chapters 10 and 13.

In sklearn, there are four baseline classification methods. We’ll actually show code for five, but two are duplicates. Each of the methods makes a prediction when given a test example. Two baseline methods are random; they flip coins to make a prediction for the example. Two methods return a constant value; they always predict the same thing. The random methods are (1) uniform: choose evenly among the target classes based on the number of classes and (2) stratified: choose evenly among the target classes based on frequency of those classes. The two constant methods are (1) constant (surprise?): return one target class that we’ve picked out and (2) most_frequent: return the single most likely class. most_frequent is also available under the name prior.

The two random methods will behave differently when a dataset has rare occurrences, like a rare disease. Then, with two classes—plentiful healthy people and rare sick people—the uniform method picks evenly, 50%–50%, between sick and healthy. It ends up picking way more sick people than there are in reality. For the stratified method, we pick in a manner similar to stratified sampling. It picks healthy or sick as the target based on the percents of healthy and sick people in the data. If there are 5% of sick people, it would pick sick around 5% of the time and healthy 95% of the time.

Here’s a simple use of a most_frequent baseline method:

```
In [2]:

# normal usage: build-fit-predict-evaluate
baseline = dummy.DummyClassifier(strategy="most_frequent")
baseline.fit(iris_train_ftrs, iris_train_tgt)
base_preds = baseline.predict(iris_test_ftrs)
```
