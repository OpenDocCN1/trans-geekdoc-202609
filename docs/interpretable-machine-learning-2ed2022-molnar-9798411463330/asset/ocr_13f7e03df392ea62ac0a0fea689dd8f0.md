# CHAPTER 7 GLOBAL MODEL-AGNOSTIC METHODS

![](bbox=[0.163, 0.122, 0.758, 0.448])

Figure 7.32: Evaluations of the witness function at different points.

reducing the overall MMD2, we are looking for points that maximize a cost function that includes the witness function and a regularizer term. The additional term in the optimization enforces diversity in the points, which is needed so that the points come from different clusters.

This second step is independent of how the prototypes are formed. I could also have handpicked some prototypes and use the procedure described here to learn criticisms. Or the prototypes could come from any clustering procedure, like k-medoids.

That is it with the important parts of MMD-critic theory. One question: **How can MMD-critic be used for interpretable machine learning?**

MMD-critic can add interpretability in three ways: By helping to better understand the data distribution; by building an interpretable model; by making a black box model interpretable.

If you apply MMD-critic to your data to find prototypes and criticisms, it will improve your understanding of the data, especially if you have a complex data distribution with edge cases. But with MMD-critic you can achieve more!

For example, you can create an interpretable prediction model: a so-called "nearest prototype model". The prediction function is defined as:

```
$\hat{f}(x) = argmax_{i \in S} k(x, x_i)$
```