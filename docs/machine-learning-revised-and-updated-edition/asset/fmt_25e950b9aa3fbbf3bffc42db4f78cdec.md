
# Decision Trees

Each path from the root to a leaf corresponds to a conjunction of test conditions in the decision nodes on the path and such a path can be written as an if-then rule. That is one of the advantages of the decision tree: that a tree can be converted to a rule base of if-then rules and that those rules are easy to interpret. The tree is trained with a given training data where splits are placed to delimit regions that have the highest “purity,” in the sense that each region contains instances that are similar in terms of their output.

Decision tree learning is nonparametric—we do not have a model where the structure is assumed a priori and we only update the parameters of that fixed structure; a decision tree grows as needed and its size depends on the complexity of the problem underlying the data; for a simple task, the tree is small, whereas a difficult task grows a large tree.

There are different decision tree models and learning algorithms depending on the splitting test used in the decision nodes and the interpolation done at the leaves; one very popular current approach is the `random forest`, where we train many decision trees on randomly chosen different subsets of the training data and we combine their predictions by taking a vote.

Trees are used successfully in various machine learning applications, and together with the linear model, the decision tree should be taken as one of the basic benchmark methods before any more complex learning algorithm is tried.

## Active Learning

In learning, it is critical that the learner also knows what it knows and what it does not know. When a trained model makes a prediction, it is helpful if it can also indicate its certainty in that prediction.

One easy way to do this is by `resampling`.

Let us say that we want to be able to predict the price of a used car and we have a data set of 100 examples. Let us choose randomly 80 examples from that data and using those we train our first model. Then we can choose another random subset of 80 examples from the original data set and train a second model. The two data sets will be similar but not the same, and so the two fitted models will be similar in their predictions but not the same.

We can do this for example ten times and get ten models. Later on, when we are given a new car, we can give its mileage as input to all ten models and get ten predictions. They will be slightly different because each one has been trained on a slightly different data set. We can then use the average of those ten values as our point estimate; we can also sort those ten estimates from the smallest to the largest and define an interval, the so-called `confidence interval`, from the minimum to the maximum (in practice, it is better to discard the two extreme values at either end and use the interval from the second to the ninth). The size of that interval is a measure of our predictive uncertainty; if it is large we understand that our prediction is very much affected by slight changes in the data and hence is not too reliable.

The important point here is that data points are not created equal and our data may not be uniform all over the input space. For example, we may have a lot of cars in the training set with mileage less than 100K but not many cars with more.

In the case of estimation, in regions of the input space where we have a lot of data, we will have many training examples which means that all ten sets will have instances from there, which in turn implies that we would expect the ten models to make similar predictions in there and hence the confidence interval for any input there will be small. Where we have few data in the input space, it may be possible that there will not be examples in the training data of all of the ten models, and hence the predictions of the ten models can be expected to vary more and we will have a larger confidence interval.

So where the confidence interval is large, the uncertainty is understood to be large, and the model can actively ask the supervisor to provide training examples in there. This is called `active learning`. The model generates inquiries by synthesizing new inputs and asks for them to be supplied, rather like a student asking a question during a lecture.

For example, very early on in artificial intelligence, it was realized that in classification the most informative examples are those that lie closest to the current estimate of the class boundary: a `near miss` is an instance that looks very much like a positive example but is actually a negative example (Winston 1975).

A related research area in machine learning is called `computational learning theory`, where work is done to find theoretical bounds for learning algorithms that hold in general, independent of the particular learning task. For example, for a given model and learning algorithm, we may want to know the minimum number of training instances needed to guarantee at most a certain error with high enough probability—this is called `probably approximately correct learning` (Valiant 1984).

## Learning to Rank

`Ranking` is an application area of machine learning that is different from regression or classification, and that is sort of between the two. In classification and regression, for each instance, we have a desired absolute value for the output; in ranking we train on pairs of instances and are asked to have the outputs for the two in the correct order.

Let us say we want to learn a `recommendation model` for movies. For this task, the input is composed of the attributes of the movie. The output is a numeric score that is a measure of how much we believe that a particular customer will enjoy a particular movie. To train such a model, we use past ratings by that customer. If we know that the customer liked movie `A` more than movie `B` in the past, we do our training such that for that customer the estimated score for `A` is indeed a higher value than the estimated score for `B`. Then, later on when we use that model to make a recommendation based on the highest scores, we expect to choose a movie that is more similar to `A` than to `B`.

There is no required numeric value for the score, as we have for the price of a used car, for example. The scores can be in any range as long as the ordering is correct. The training data is not given in terms of absolute values but in terms of such rank constraints (Liu 2011).

We can note here the advantage and difference of a ranker over a classifier or a regressor. If users rate the movies they have seen as enjoyed versus not enjoyed, this will be a two-class classification problem and a classifier can be used, but taste is nuanced, and a binary rating is hard to come by. On the other hand, if people rate their enjoyment of each movie on a scale of, say, from 1 to 10, this will be a regression problem, but such values are difficult to assign. It is more natural and easier for people to say of the two movies they watched which one they enjoyed more. After the ranker is trained with all such pairs, it is expected to generate numeric scores satisfying all these constraints.

Ranking has many applications. In search engines, we want to retrieve the most relevant documents when given a query. When we retrieve and display the current top ten candidates, if the user clicks the third one skipping the first two, we understand that the third should have been ranked higher than the first and the second. Such `click logs` are used to train rankers.

## Bayesian Methods
