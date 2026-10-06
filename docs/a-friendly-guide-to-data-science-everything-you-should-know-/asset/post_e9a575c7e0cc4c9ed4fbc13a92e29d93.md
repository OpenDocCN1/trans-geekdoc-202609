
## CHAPTER 15 NOT A CRYSTAL BALL: MACHINE LEARNING

But our dataset has more features than total years of education. We can add age to the chart and create a standard two-dimensional scatterplot, as you can see in Figure 15-22. As soon as we do this, we can see two points very far away from all the others and from each other.

![](img/df37a23523ff92247f9125691b1edea2_583_0.png)

Figure 15-22. The impact of increasing dimensions in data from one dimension to two

These points on Figure 15-22 are so far away that it would be difficult to include these in the model without other problems, like overfitting. Also, these distant points happen to be the lowest and highest values in the whole dataset. It looks like if we used age in a model, it wouldn't know what to do—is being older with a high or low level of education? And what's going on in all that space between the bulk of the points are and the two distant ones? We have no idea because we don't have enough data for this number of dimensions. If data can spread out with just a single dimension increase, imagine what can happen with 10 dimensions or 50 or even more. The more features we have, the more data we need to represent the real variety among each feature and how it relates to other features.

As seen in the chart, overfitting is another problem that the dimensionality brings, which comes about largely from sparsity. A fourth problem is that “distance” tends to get fuzzy the more features you have. So some of the typical metrics we use to measure distance stop working when we get into higher-dimensional data.

Two other problems relate to the amount of computation that has to be done as the number of features increase. It starts to use more and more compute resources and takes longer and longer to run. Depending on the number of features, this can reach a point of being completely impractical (or way too expensive) to run.

## Data Leakage

Data leakage comes from one of the easiest mistakes to make in modeling—accidentally including data in the train set that shouldn’t be there. This could be from your test set (easy to do) or any other information about your target that won’t be available when running real forecasts.

Another thing that’s easy to do, especially when you’re new, is accidentally including features that are there in your train (and test) set but won’t be there when you’re running your model on unseen/future data. For instance, imagine you’re predicting daily pizza sales at a restaurant for the next week, Monday through Sunday. You create a bunch of great features, including things like previous day’s sales and previous week’s sales. That works in your test set because you are able to calculate all of those since you have complete data. When it comes to running true forecasts for the upcoming week, you may have sales all the way through Sunday night, and then you’re going to run the feature update for the coming week and then the forecasts early on Monday morning. No problem there because you have previous day’s sales. What about Tuesday? You don’t have Monday’s sales yet because it’s early Monday morning and the restaurant hasn’t even opened. Most likely your feature generation or forecasts would simply fail if you tried to run it on this data because it would be missing that, but even worse would be your model just takes the null value and uses it (to unknown impact, but not good).

Data science requires attention to detail and always thinking about what you're doing. If you're getting very high accuracies or performance scores, you probably have data leakage. Any time you have surprisingly good performance on your test set, check for that there is no overlap in your train and test sets. Then check for unreasonable features. Additionally, if you're testing time-based data, you almost always want to make your test set chronologically at the very end of your data and the train before that. This is a requirement if you've included features that rely on previous values, such as the previous month's sales.

## Key Takeaways and Next Up

In this chapter, we covered a lot of machine learning topics. We first focused on defining the three key types of machine learning, supervised, unsupervised, and reinforcement, and also addressed semi-supervised learning and ensemble learning, both of which add a lot to the field. We then looked at several supervised learning algorithms, some in depth, including time series analysis, generalized linear models, trees, naïve Bayes, neural networks, k-nearest neighbors, and support vector machines. We then talked about the two unsupervised learning techniques, clustering and association rule mining, touching on both types of clustering, k-means and hierarchical. I talked about model explainers that can help explain forecasts from black box models and of the practical aspects of doing machine learning in code. I addressed some of the major challenges we face when doing machine learning modeling. These included overfitting and underfitting, by the model either won't generalize well or misses important patterns. Then I discussed imbalanced data, when the counts of different labels are very different, and the curse of dimensionality, which describes some of the problems that come from having a large number of features in a model. Finally, I explained data leakage, when information gets into your trained model that shouldn't be there.

In the next chapter, we'll be looking at how to see how well your models have done after you've trained them. We'll talk about several metrics that can be used for measuring the performance of models in classification tasks and models in regression tasks, because they can be quite different. I'll also look at some metrics that we use to measure the performance of clustering algorithms.

## PRACTITIONER PROFILE: JEFF ELMORE

**Name:** Jeff Elmore

**Current Title:** Senior principal data scientist

**Current Industry:** Energy, also worked in education tech, literacy research, and writing

**Years of Experience:** 20 in tech, 13 of that in data science

**Education:**

- BS Applied Mathematics

> *The opinions expressed here are Jeff's and not any of his employers, past or present.*

## Background

Jeff fell in love with computers when he was 12, and that has never waived. He started working as a programmer after high school and enjoyed it, but eventually decided to get a degree. He started as a computer engineering major, but after taking calculus, he realized he loved the math more and switched his major to applied math. He loves how you can have a problem that's really hard and just apply a mathematical transformation to it, and suddenly it's easy. He learned about machine learning from both college and his experienced boss.

## Work

His first major project at his company was working with a researcher on improving one of their products, a tool that analyzed books to assign a difficulty-like score to, which could be used to match kids to the right books. He needed to understand how kids learn to read, and he realized he didn't have the domain knowledge, so he started learning but it was a slow process. Ultimately, he and the researcher came up with a product that solved the problem. He was really proud of this work, but unfortunately nothing came out of it because the company didn't understand it or how to market it. He founded a company with a couple of people he knew, and they created a product designed to help writers write novels. This venture didn't work out and it was really disappointing. But it also shifted his perspective to valuing the life part of the work/life balance more. He found a new job that he likes but doesn't take over his life, so he's happy. He's still interested in finding ways to use AI to help people, but he feels like an AI hobbyist at his point.
