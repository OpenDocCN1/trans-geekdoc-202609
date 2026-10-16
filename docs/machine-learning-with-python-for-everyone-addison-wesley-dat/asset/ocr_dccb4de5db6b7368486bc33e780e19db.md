line in 2D. One way to reduce the model is to pick some ws—say, w1 and w0—and set them to zero. That gives us y = w2x2 which effectively says that we don’t care about the value of x1 and we are content with an intercept of zero. Completely blanking out values seems a bit heavy-handed. Are there more gradual alternatives? Yes, I’m glad you asked.

Instead of introducing zeros, we can ask that the total size of the weights be relatively small. Of course, this constraint brings up problems—or, perhaps, opportunities. We must define total size and relatively small. Fortunately, total hints that we need to add several things up with sum. Unfortunately, we have to pick what we feed to sum.

We want the sum to represent an amount and we want things far away from zero to be counted equally—just as we have done with errors. We’d like 9 and −9 to be counted equally. We’ve dealt with this by (1) squaring values or (2) taking absolute values. As it turns out, we can reasonably use either here.

In [2]:

```
weights = np.array([3.5, -2.1, .7])
print(np.sum(np.abs(weights)),
      np.sum(weights**2))
```

6.3 17.15

Now we have to define some criteria for relatively small. Let’s return to our goal: we want to simplify our model to move from overfitting and towards just right. Our just-right values cannot operate on their own, in a vacuum. They must be connected to how well we are fitting the data—we just want to tone down the over part of overfitting. Let’s return to the way we account for the quality of our fit. To investigate, let’s create a bit of data where we specifically control the errors in it:

In [3]:

```
x_1 = np.arange(10)
m, b = 3, 2
w = np.array([m,b])
x = np.c_[x_1, np.repeat(1.0, 10)] # the plus-one trick
errors = np.tile(np.array([0.0, 1.0, 1.0, .5, .5]), 2)
print(errors * errors)
print(np.dot(errors, errors))
y_true = rdot(w,x)
y_msr = y_true + errors
D = (x,y_msr)
```

[0.  1.  1.  0.25 0.25 0.  1.  1.  0.25 0.25]

5.0