
# CHAPTER 6

## Ensemble Models

In the previous chapter, we understood that models built using Decision Tree algorithm
tend to overfit. Like Decision Tree algorithm, all algorithms have some
weaknesses. One way to overcome this problem is to make a prediction using multiple
models and then decide based on the collective intelligence of all models. When
have numerous models working together to make decisions, we call such models Ensemble models.

In this chapter, we will explore different types of Ensemble models:
![](img/1af2c47dddfed008516c06df_178_0.png) 

## Structure

In this chapter, we will discuss the following topics:
- Ensemble Models
- The Intuition Behind Ensemble Models
- Different Types of Ensemble Models
- Ensemble implementation in Scikit-Learn
- VotingClassifier
- BaggingClassifier
- StackingClassifier
- Building Ensemble Model Using Bagging
- About the Data Set
- Librosa library
- Building Ensemble Model

## Objectives

After reading this chapter, the nuances of Ensemble model will be clear. Also,
you will learn how to use implementation of different Ensemble models from
Scikit-Learn library. Lastly, by the end of this chapter, you will learn how to
solve classification problem for extracting emotions using Bagging as well.

## Ensemble models

When faced with very complex question, we can pose the question to one expert and
get an opinion. Here we will depend on intelligence of the expert. Every individual
has some biases. So the expert contacted answer based on their preferences. It is
likely that the solution could have limited chance of being accurate. Suppose
we change our approach and pose the question to several experts. Then, we collate
the answers from all experts and choose the solution that most experts agree with.
In most cases, such conclusion could be more accurate than one expert’s opinion.

The idea of ensembles is to ask several experts about a given problem. In simple ensemble models, we provide the data to several models and get the answers from each
model. Then, if it is a regression problem, we take the average of answers obtained
from all models as the solution. If it is a classification problem, we take the answers
from all the models, and the answer provided by the maximum number of models is taken
the answer.

To understand this more clearly, suppose we have a classification problem to determine
whether it is spam (that is, we need to classify it into two classes – SPAM and NOT SPAM).
We will provide our labeled data to several algorithms and create all models. When
we want to predict data instance, we will pose the question to all models. Some of
models may classify the case as SPAM, and some of the models may classify the case as
SPAM. We will count how many models predicted SPAM and how many predicted NOT SPAM.
If the count of prediction as SPAM is greater than the count of predictions NOT SPAM,
we will conclude that the case is SPAM; else, we need not always create models with
multiple algorithms. Generally, we take a single algorithm like Decision Tree.
We know that Decision Tree tends to divert. Overfitting means the algorithm learns
the data too well; thus, when new data is provided, the model tends to make mistakes.
So, what we do is to create subsets of the data. For simplicity to understand, suppose
we have 1,000 data points. We create subsets of 100 data points by randomly
picking them from the original data set of 1,000. Now, we provide each of the subsets
of 100 data points to create ten separate models using the Decision Tree algorithm.
Now, each model sees only part of the data, and none of the models can see the
complete data set. When the ten models make the predictions, we take our prediction
as the decision made by the maximum number of models. We will always consider
the prediction based on the predictions of all the models.

Such a technique of creating a model is called the ensemble technique, and such
models are called Ensemble models.

## The intuition behind Ensemble models

Suppose we have a biased coin with a probability of obtaining a head being 51% (and
the probability of obtaining a tail is 49%). If we toss this coin once, the chance of
getting a head or a tail will be equally likely. However, if we toss this coin
100 times, the chance is that we obtain heads 51 and tails 49 times. However,
if we toss this coin 10,000 times, the chance of getting heads is 5,100 times,
the chance of obtaining tails is 4,900 times. Notice that our conclusion is clearly
distinguished as we increase the number of times we toss the coin.

Ensembles work in the same way. Suppose we have several classifiers that produce
better results than the random guess. Then, when we create ensembles with sufficient
data points using these classifiers and take the majority from the results, the
ensembles generally provide more than 75% accuracy. The critical point to note is
that we need to have sufficient data points. In statistics, this is called the Law
of large numbers.

## Different types of Ensemble models

There are many types of ensemble models. We will focus on four types of ensemble
models, that is, Voting, Bagging, Boosting, and Stacking.

## Voting ensemble models

In the Voting ensemble model, we subject the same data to several models built
using different algorithms. Then, we make predictions from each model separately
and take the decision provided by the maximum number of models.

In Figure 6.2, we see how Voting ensemble models work. We can build 3 models on
the input:
![](img/1af2c47dddfed008516c06df_181_0.png)

> "Class A" got 2 votes and "Class B" got 1 vote and thus choose "Class A" as our decision.

Figure 6.2: Simplified example of Voting

As shown in Figure 6.2, we built the three models using Nave Bayes, KNN, and
Decision Tree algorithms. Then, when we have a data instance for which need to make
prediction, we will subject the data to each of the three models and take the
prediction from each. The prediction made by the maximum number of models is
considered the final prediction.

> Note: As we are discussing the classification algorithm, we will consider the
decision as the class. If the problem was for regression, we would take the
output from each of models.

> Note: In the illustration in Figure 6.1, we have considered three models. This is
for example. We could use as many numbers of models as we desire.

## Bagging ensemble model

In Bagging ensemble models, we use the same algorithm to create multiple models.
However, we provide a different subset of the data for each model. So, none of the
models sees the complete data set. To provide different subsets of the data to each
model, we create random subsets of the original data set. Then, we train each of
models on one of the subsets of the data set.
