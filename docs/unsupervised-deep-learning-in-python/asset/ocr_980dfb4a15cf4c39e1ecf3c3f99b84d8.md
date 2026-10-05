# Chapter 2: t-SNE

In this lecture we are going to talk about another dimensionality reduction and visualization method called t-SNE. The t means we are going to incorporate the t-distribution and SNE stands for “stochastic neighbor embedding”.

One big advantage of t-SNE is that it's a nonlinear method, so it is more expressive than PCA.

Why study t-SNE?

2 reasons:

+   1) t-SNE was jointly developed by Geoffrey Hinton, who as you know, is one of the main figures of deep learning.

+   2) by doing t-SNE, we are seeing how the limitations of PCA can be overcome by using a more complex mathematical model.

One key difference between PCA and t-SNE, other than the fact that t-SNE is non-linear, is that there is no transformation model with t-SNE.

Instead, t-SNE just modifies the outputs directly in order to minimize the cost function.

What this means is that, you won’t have any train and test sets, and you can’t transform data after fitting on some other data.

The way that t-SNE works is essentially it tries to preserve the distances between each input vector.

We will start with symmetric SME since it intuitively makes more sense.

On the original data X, we define a joint probability distribution p(i,j) which is equal to: