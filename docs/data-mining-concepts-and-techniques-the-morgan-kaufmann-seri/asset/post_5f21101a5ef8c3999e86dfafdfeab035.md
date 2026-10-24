
**FIGURE 7.6** Here we see just two possible separating hyperplanes and their associated margins. Which one is better? The one with the larger margin (b) should have greater generalization accuracy.

The weights can be adjusted so that the hyperplanes defining the “sides” of the margin can be written as

```
H₁ : b + w₁x₁ + w₂x₂ ≥ 1   for yᵢ = +1,   (7.11)
H₂ : b + w₁x₁ + w₂x₂ ≤ -1   for yᵢ = -1.   (7.12)
```

That is, any tuple that falls on or above H₁ belongs to class +1, and any tuple that falls on or below H₂ belongs to class -1. Combining the two inequalities of Eqs. (7.11) and (7.12), we get

```
yᵢ(b + w₁x₁ + w₂x₂) ≥ 1, ∀i.   (7.13)
```

Any training tuples that fall on hyperplanes H₁ or H₂ (i.e., yᵢ(b + w₁x₁ + w₂x₂) = 1) are called **support vectors**. That is, they are equally close to the (separating) MMH. In Fig. 7.7, the support vectors are shown encircled with a thicker border. Essentially, the support vectors are the most difficult tuples to classify and give the most information regarding classification.

From this, we can obtain a formula for the size of the maximal margin. The distance from the separating hyperplane to any point on H₁ is 1/||W||, where ||W|| is the Euclidean norm of W, that is,

\(\sqrt{\mathbf{W} \cdot \mathbf{W}}\).<sup>3</sup> By definition, this is equal to the distance from any point on H₂ to the separating hyperplane. Therefore the maximal margin is \(\frac{2}{\|\mathbf{W}\|}\). This suggests that we should minimize \(\|\mathbf{W}\|^2\) in order to make the margin as large as possible. Notice that if the tuples are in \(n\) dimensional space, Eq. (7.13) becomes \(y_i(\mathbf{W}'\mathbf{X}_i + b) \ge 1\). Putting it together, we have the following mathematical formulation of SVM:

```
min \(\|\mathbf{W}\|^2\),
s.t. \(y_i(\mathbf{W}'\mathbf{X}_i + b) \ge 1, \forall i.\)
(7.14)
```

The intuition of the above formulation is that we want to find a linear classifier (i.e., hyperplane), such that (1) its margin is as large as possible (i.e., min \(\|\mathbf{W}\|^2\)), and (2) each training tuple is correctly classified (i.e., \(y_i(\mathbf{W}'\mathbf{X}_i + b) \ge 1, \forall i\)). The corresponding classifier is often called *hard-margin linear SVM*.

“So, how does an SVM find the MMH and the support vectors?” Using some “fancy math tricks,” we can rewrite Eq. (7.14) so that it becomes what is known as a (convex) quadratic programming problem. Such fancy math tricks are beyond the scope of this book. Advanced readers may be interested to note that the tricks involve rewriting Eq. (7.14) as its dual form using Lagrangian formulation and then solving for the solution using Karush-Kuhn-Tucker (KKT) conditions. Details can be found in the bibliographic notes at the end of this chapter (Section 7.10).

If the data are relatively small (say, with a few thousand training tuples), any optimization software package for solving convex quadratic programming problems can then be used to find the support vectors and MMH. For larger data, special and more efficient algorithms for training SVMs can be used instead, the details of which exceed the scope of this book.<sup>3</sup>

<sup>3</sup> If \(\mathbf{W} = \{w_1, w_2, \dots, w_n\}\), then \(\sqrt{\mathbf{W} \cdot \mathbf{W}} = \sqrt{w_1^2 + w_2^2 + \dots + w_n^2}\).

Once we've found the support vectors and MMH (note that the support vectors define the MMH!), we have a trained support vector machine. The MMH is a linear class boundary, and so the corresponding SVM can be used to classify linearly separable data.

> "Once I've got a trained support vector machine, how do I use it to classify test (i.e., new) tuples?"

Based on the Lagrangian formulation mentioned before, the MMH can be rewritten as the decision boundary

```
d(X) = \sum_{i=1}^{l} y_i \alpha_i X' X_i + b, \quad (7.15)
```

where \( y_i \) is the class label of support vector \( X_i \); \( X \) is a test tuple and \('\) denotes the transpose of a vector; \( \alpha_i \) and \( b \) are numeric support parameters that were determined automatically by the SVM algorithm noted before; and \( l \) is the number of support vectors, which is often much smaller than the total number of training tuples. Interested readers may note that the \( \alpha_i \) are Lagrangian multipliers. For linearly separable data, the support vectors are a subset of the actual training tuples. Slight twist regarding this when dealing with nonlinearly separable data, as we shall see in the following.

Given a test tuple, \( X \), we plug it into Eq. (7.15), and then check to see the sign of the result. This tells us on which side of the hyperplane the test tuple falls. If the sign is positive, then \( X \) falls above the MMH, and so the SVM predicts that \( X \) belongs to class +1 (representing buys_computer = yes, in our case). If the sign is negative, then \( X \) falls below the MMH and the class prediction is -1 (representing buys_computer = no).

Notice that the Lagrangian formulation of our problem Eq. (7.15) contains a dot product between support vector \( X_i \) and test tuple \( X \). This will prove very useful for finding the MMH and support vectors of a nonlinear SVM when the given data are linearly inseparable, as described further in the next section. However, before that, let's briefly introduce how we can modify the formulation of hard-margin linear SVM (Eq. (7.14)) for the nonlinear case. That is, we still wish to find a linear classifier (i.e. a hyperplane) when the training tuples are linearly inseparable. Here, the trick is that we allow some training tuples to be mis-classified. To be specific, we can introduce a nonnegative slack variable \( \xi_i \ge 0 \) for each training tuple, \( X_i \). If \( \xi_i = 0 \), it means that the corresponding tuple \( X_i \) is correctly classified by the hyperplane (i.e., \( y_i(W'X_i + b) \ge 1 \)). In other words, a training example with \( \xi_i = 0 \) is just like the one in the hard-margin linear SVM. However, if \( \xi_i > 0 \), it means that the tuple \( X_i \) is incorrectly classified by the hyperplane and its magnitude \( |\xi| \) indicates how far the training tuple is away from its corresponding side (i.e., \( H_1 \) for a positive training example, and \( H_2 \) for a negative training example). See Fig. 7.8(a) for an illustration.

Then we have the following alternative mathematical formulation of SVM. The corresponding classifier is often called soft-margin linear SVM. Different from hard-margin linear SVM, our new objective function has two terms, including (1) \( \|W\|^2 \), which measures the size of margin (i.e., the smaller \( \|W\|^2 \), the larger margin), and (2) the sum of all slack variables \( \sum_{i=1}^{N} \xi_i \), which measures the (approximate) number of incorrectly classified training tuples (i.e., the training error). In Eq. (7.16), \( N \) is the total number of training tuples and \( C > 0 \) is a user-tuned parameter that balances the size of margin and the training error. Note that we can use the same optimization technique (i.e., convex quadratic programming) to solve Eq. (7.16) as for hard-margin linear SVM. Likewise, the resulting soft-margin linear classifier uses the same equation (Eq. (7.15)) to classify a test tuple.

FIGURE 7.8 A simple 2-D case showing linearly inseparable data, where each tuple is represented by two attributes (x1 and x2). Unlike the linearly separable data of Fig. 7.5, here it is not possible to draw a straight line to perfectly separate the two classes. We could use a soft-margin linear SVM, with the help of slack variables (ε1 and ε2), to produce a linear decision boundary at the expense of two training tuples being mis-classified (a). Alternatively, we could seek for a nonlinear decision boundary (b).

```
min ||W||^2 + C \sum_{i=1}^N \xi_i,

s.t. y_i(W'X_i + b) \ge 1 - \xi_i, \forall i.   (7.16)
```

We end this section with two important things to note. The complexity of the learned classifier is characterized by the number of support vectors rather than the dimensionality of the data. Hence SVMs tend to be less prone to overfitting than some other methods. The support vectors are the essential or critical training tuples—they lie closest to the decision boundary (MMH). If all other training tuples were removed and training were repeated, the same separating hyperplane would be found. Furthermore, the number of support vectors found can be used to compute an (upper) bound on the expected error rate of the SVM classifier, which is independent of the data dimensionality. An SVM with a small number of support vectors can have good generalization, even when the dimensionality of the data is high.

### 7.3.2 Nonlinear support vector machines

In Section 7.3.1, we learned about hard-margin linear SVMs for classifying linearly separable data. We also learned about soft-margin linear SVMs when the training data are linearly inseparable, by allowing
