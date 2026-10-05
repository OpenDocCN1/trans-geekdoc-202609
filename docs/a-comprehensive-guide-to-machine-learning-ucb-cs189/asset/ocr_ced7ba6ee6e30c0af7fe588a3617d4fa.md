# Chapter 8

# Decision Tree Learning

#  8.1 Decision Trees

A decision tree is a type of classifier which classifies things by repeatedly posing questions of the form, "Is $x_i$ greater than value $v$?" You can visualize such a thing as a tree, where each node consists of a split-feature, split-value pair $(x_i, v)$ and the leaves are possible classes. Here's a picture:

![](bbox=[0.344, 0.467, 0.653, 0.683])

Note that a class may appear multiple times at the leaves of the decision tree. Picking a split-feature, split-value pair essentially carves up the feature space into chunks, and you can imagine having enough of these pairs lets you create an arbitrarily complex classifier that can perfectly fit any training set (unless two points of different classes coincide).

When we consider the task of building this tree, we want to ask ourselves a couple of things:

+   - How do we pick the split-feature, split-value pairs?
- How do we know to stop growing the tree?

Let's address the first point. Intuitively, when we pick a feature to split on, we want to choose the one that maximizes how sure we are of the classes of the two resulting chunks. If we had a bunch