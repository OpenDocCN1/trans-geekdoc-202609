![](bbox=[0.2, 0.13, 0.8, 0.58])

Conceptually, LinearSVC, SVC(linear), and SVC(poly=1) should all be the same; practically there are some mathematical and implementation differences between the three. LinearSVC uses a slightly different loss function and it treats its constant term—the plus-one trick—differently than SVC. Regardless, each of the linear options has boundaries defined by lines. There's no curve or bend to the borders. Notice that the SVC(poly=3) example has some deep curvature to its boundaries. The rbf examples have increasingly deep curves and a bit of waviness to their boundaries.

# 13.2.5 Take-Home Notes on SVM and an Example

Although this book is largely about explaining concepts, not giving recipes, people often need specific advice. SVMs have lots of options. What are you supposed to do when you want to use them? Fortunately, the authors of the most popular SVM implementation, libsvm (used under the hood by scikit-learn), have some simple advice:

+   - Scale the data.
+   - Use an rbf kernel.
+   - Pick kernel parameters using cross-validation.