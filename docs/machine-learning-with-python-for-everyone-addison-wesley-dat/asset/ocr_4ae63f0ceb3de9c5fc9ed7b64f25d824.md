DA methods are very interesting for at least three reasons:

+   1. They have a wonderfully clear mathematical connection with Naive Bayes on continuous features (Gaussian Naive Bayes, GNB).
+   2. Like GNB, discriminant analysis methods model the features and the target together.
+   3. DA methods arise from particularly simple—or perhaps mathematically convenient—assumptions about the data. The different DA methods make slightly different assumptions.

Without going into great mathematical detail, we will discuss four different DA methods. I won’t introduce them by name, yet. Each of these methods works by making assumptions about the true nature of the data. Those assumptions could be wrong! Every method we use makes assumptions of one kind or another. However, DA methods make a specific set of stronger and stronger assumptions about the relationships between the features and their relationship to the target. We’ll talk about these as a group of friends. Suppose there are three friends: Feature One, Feature Two, and Class. They don’t always talk to each other as much as they’d like to, so they don’t know as much about each other as they’d like. Here are the sorts of assumptions these methods make:

+   1. Features One and Two talk to each other. They care what Class has to say.
+   2. Features One and Two talk to each other. They don’t care what Class has to say.
+   3. Feature One doesn’t talk to Feature Two directly. Anything Feature One knows comes from talking to Class. That knowledge, in turn, might give some information—gossip—about Feature Two.
+   4. We can combine 2 and 3: Feature One doesn’t talk directly to Feature Two nor does it care what Class has to say.

In fact, these assumptions aren’t just about the communication between Feature One and Feature Two. They are about the communication between all pairs of features: {Ftr_i, Ftr_j}.

These assumptions lead to different models. Make no mistake: we can assume any of these scenarios and build a model of our data that relies on its assumptions. It might work out; it might not. We might have perfect knowledge that leads us to choose one of these sets of assumptions correctly. If so, we’d expect it to work better than the others. Short of omniscience, we can try each set of assumptions. Practically, that means we fit several different DA models, cross-validate, and see which performs the best. Then we assess on a hold-out set to make sure we haven’t misled ourselves.

# 8.5.1 Covariance

To understand the differences between the DA methods, you need to know about covariance. Covariance describes one way in which the features are related—or not—to each other. For example, if we are looking at physiological data on medical patients, our models might make good use of the fact that height and weight have a strong relationship. The covariance encodes the different ways features may metaphorically communicate with each other.