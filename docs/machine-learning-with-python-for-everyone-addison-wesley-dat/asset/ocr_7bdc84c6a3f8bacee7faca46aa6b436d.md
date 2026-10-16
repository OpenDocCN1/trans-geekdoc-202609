# 8.2.3 Bias and Variance in Decision Trees

If we start with a wide open, no-depth-limit tree, we’ll have a model that is very flexible and can capture any finite pattern that doesn’t have coin-flipping randomness built into it. While that might seem ideal, you’ve learned enough to know that there is a tradeoff. If we use unconstrained trees, we will likely overfit, and when we try to generalize, we’ll have poor test performance. If you need a reminder about that tradeoff, see Section 5.6. So, how can we bias our trees or place limits on them to prevent overfitting? We can take several steps.

+   1. We can limit the depth of the trees. We allow fewer questions before categorizing.
+   2. We can require more examples at leaves. This constraint forces us to group together examples that might be different. Since we aren’t allowed to separate them them, it effectively smoothes out some of our boundaries.
+   3. We can limit the number of features we consider when we ask questions of the examples. This constraint has the added benefit of speeding up our learning process.

# 8.3 Support Vector Classifiers

In a few minutes, we’ll see a great oddity of logistic regression classifiers: the underlying mathematics fail with perfectly separable data. If drawing a line between the Xs and Os on paper is as simple as possible, the mathematics simply fall apart. It’s a case of being in a desert and drowning in fresh water. Let’s take a closer look at the perfectly separable case. What would you do with all the data points falling neatly on either side of a set of tracks? Here are three possible lines:

In [9]:

```
fig, ax = plt.subplots(1,1,figsize=(4,3))

# fancy way to get cross product of points
left = np.mgrid[1:4.0, 1:10].reshape(2, -1).T
right = np.mgrid[6:9.0, 1:10].reshape(2, -1).T

# data points
ax.scatter(left[:,0], left[:,1], c='b', marker='x')
ax.scatter(right[:,0], right[:,1], c='r', marker='o')

# separating lines
ax.plot([3.5, 5.5], [1,9], 'y', label='A')
ax.plot([4.5, 4.5], [1,9], 'k', label='B')
ax.plot([3.5, 5.5], [9,1], 'g', label='C')
ax.legend(loc='lower center');
```