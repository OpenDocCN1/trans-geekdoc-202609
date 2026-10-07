For example, let's show examples of 3s and 5s (the plot_digits() function) just uses
Matplotlib's show() function; see this Jupyter notebook for details:

```
cl_a, cl_b = 3, 5
X_aa = X_train[y_train == cl_a] & (y_train_pred == cl_a)
X_ab = X_train[y_train == cl_a] & (y_train_pred == cl_b)
X_ba = X_train[y_train == cl_b] & (y_train_pred == cl_a)
X_bb = X_train[y_train == cl_b] & (y_train_pred == cl_b)

plt.figure(figsize=(8,8))
plt.subplot(221); plot_digits(X_aa[:25], images_row=5)
plt.subplot(222); plot_digits(X_ab[:25], images_row=5)
plt.subplot(223); plot_digits(X_ba[:25], images_row=5)
plt.subplot(224); plot_digits(X_bb[:25], images_row=5)
plt.show()
```

![](bbox=[0.331, 0.332, 0.666, 0.574])

The 5x5 blocks on the left show digits classified as 3s, and the two 5x5 blocks on
right show images classified as 5s. Some of the digits that the classifier gets wrong
(i.e., in the bottom-left and top-right blocks) are so badly written that even human
would trouble classifying them (e.g., the 5 on the 1st row and 2nd column truly
looks like a badly written 3). However, misclassified images seem like obvious
errors, and it's hard to understand why the classifier makes the mistakes it.
The reason is that we used a simple 5GDCCClassifier, which is a linear model. All
it assigns a weight per class to each pixel, and when it sees a new image it just
sums the weighted intensities to get a score for each class. Since 3s and 5s
differ only by a few pixels, this model will easily confuse them.

> But remember that our brain is a fantastic pattern recognition system, and our visual system does a lot of
complex preprocessing before any information reaches our consciousness, so fact that it feels simply
not mean that it is.