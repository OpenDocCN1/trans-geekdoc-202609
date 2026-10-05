# Generalization 227

+   Navigating a drone to a safe landing zone while avoiding obstacles. The state space is the location of the drone in three spatial dimensions (perhaps surrounded by a bounding box) and the action space is the direction taken with a remote controller. The reward might be the negative straight-line distance to the landing zone (i.e., moving closer to the landing zone is better). The epoch can terminate if the drone strikes an obstacle.

This sketch should provide an idea of the reinforcement learning approach, and how it is different from supervised and unsupervised learning. This is a very active research area that has led to fruitful results. A deeper discussion of RL is outside the scope of this introductory text on data science. For learning more, please see [37].

# 12.6 Generalization

We will focus on our modeling attention on the supervised learning approach. A critical assumption in SL is that the patterns learned from the training set will generalize to additional data. The additional data might be a separate segment of data that has already been collected, or data yet to be collected.

One of the greatest fears of a data scientist is that a model is trained on some data, it fits the data, it is deployed, and fails to work as well in production. This would mean the model learned relationships between the predictors and target from the training set, but those relationships were not present in production data. This can happen, and when it does, it is a major disappointment.

How can we avoid this lack of generalization? Unfortunately, it can't be eliminated with certainty, but there are steps a data scientist can take to improve the chances of generalization. First, it is important to distinguish between two cases:

+   1. The model fails out of the gate.
2. The model works in production for some time and later fails

In the first case, the problem is caused by overfitting. As an example, imagine cramming for an exam by taking practice tests. If we learn the practice exams perfectly, the real exam only if it matches the practice questions. Suppose there are some quirky practice questions that don't test the core concepts. We might learn those and have a false sense of confidence that we know the material. It is unlikely, however, that these questions will be recycled on the real exam.

Model overfitting can have the same effect as cramming the quirky questions. While the model is learning some patterns, it is also memorizing idiosyncyn